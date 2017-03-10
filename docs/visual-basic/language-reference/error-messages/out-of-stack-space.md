---
title: "Out of stack space (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID28"
dev_langs: 
  - "VB"
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Out of stack space (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

スタックとはメモリ内にある作業領域のことで、スタックのサイズは、実行しているプログラムの要求に応じて動的に増減します。  スタックの制限を超えました。  
  
### このエラーを解決するには  
  
1.  プロシージャをあまり多くのレベルにわたって入れ子にしないようにします。  
  
2.  再帰的に呼び出し可能なプロシージャが正常に終了していることを確認します。  
  
3.  ローカル変数に必要な領域が足りない場合は、一部の変数をモジュール レベルで宣言してみてください。  また、`Property`、`Sub`、または `Function` の各キーワードの前に `Static` を付けて、プロシージャのすべての変数を静的変数として宣言することもできます。  この他、`Static` ステートメントを使ってプロシージャ内で個別に静的変数を宣言することもできます。  
  
4.  固定長文字列のいくつかを可変長文字列で定義し直します。固定長文字列では、可変長文字列よりもスタック領域が多く消費されます。  スタック領域を必要としないモジュール レベルで文字列を定義することもできます。  
  
5.  `Calls` ダイアログ ボックスを使ってスタック上でアクティブなプロシージャを表示し、入れ子になった `DoEvents` 関数呼び出しの数を確認します。  
  
6.  既にスタック上にあるイベント プロシージャを呼び出すイベントを発生させることによって、"イベント連鎖" が発生していないことを確認します。  イベント連鎖は、終了しない再帰プロシージャ呼び出しに似ていますが、コードで明示的に呼び出されるのではなく [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] によって呼び出されるため、再帰プロシージャ呼び出しに比べてわかりにくくなります。  `Calls` ダイアログ ボックスを使って、スタック上でアクティブなプロシージャを確認します。  
  
## 参照  
 [\[メモリ\] ウィンドウ](/visual-studio/debugger/memory-windows)