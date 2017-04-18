---
title: "スタック領域が不足 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
dev_langs:
- VB
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6343767da28ea4e02f9443006b222640755f7882
ms.lasthandoff: 03/13/2017

---
# <a name="out-of-stack-space-visual-basic"></a>スタック領域が不足しています。(Visual Basic)
スタックは、実行しているプログラムの要求で動的に拡大または縮小するメモリの作業領域です。 限界を超えました。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  プロシージャが深すぎます。 入れ子にしないように確認してください。  
  
2.  再帰プロシージャが正常に終了することを確認します。  
  
3.  ローカル変数では、複数領域がある必要がある場合は、モジュール レベルでいくつかの変数を宣言してください。 宣言することも、手順のすべての変数静的より前で、 `Property`、 `Sub`、または`Function`キーワード`Static`します。 使用することも、`Static`プロシージャ内で個別に静的変数を宣言するステートメントです。  
  
4.  固定長文字列可変長文字列よりも多いスタック領域を使用すると、可変長の文字列として、固定長文字列の一部を再定義します。 スタック領域必要ありません、モジュール レベルで文字列を定義することもできます。  
  
5.  数を確認して入れ子になった`DoEvents`関数を使用して呼び出し、`Calls`ダイアログ ボックスで、スタック上でアクティブなプロシージャ ビューをします。  
  
6.  スタックに既にイベント プロシージャを呼び出すイベントをトリガーすることによって、「イベントの連鎖」を発生しないことを確認します。 イベント cascade は、終端文字なし再帰プロシージャの呼び出しに似ていますが、によって呼び出されるためにわかりにくく、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]のコード内の明示的な呼び出しではなく。 使用して、 `Calls` ダイアログ ボックス プロシージャが、スタック上でアクティブなビューにします。  
  
## <a name="see-also"></a>関連項目  
 [[メモリ] ウィンドウ](https://docs.microsoft.com/visualstudio/debugger/memory-windows)
