---
title: "方法: foreach を使用してコマンド ライン引数にアクセスする (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "コマンド ライン引数 [C#]"
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 方法: foreach を使用してコマンド ライン引数にアクセスする (C# プログラミング ガイド)
配列の反復処理には、この例で示すように [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを使用する方法もあります。  `foreach` ステートメントは、配列、.NET Framework コレクション クラス、または <xref:System.Collections.IEnumerable> インターフェイスを実装する任意のクラスや構造体の反復処理に使用できます。  
  
> [!NOTE]
>  Visual Studio でアプリケーションを実行する場合、「[\[デバッグ\] ページ \(プロジェクト デザイナー\)](/visual-studio/ide/reference/debug-page-project-designer)」のコマンド ライン引数を指定できます。  
  
## 使用例  
 この例では、`foreach` を使用したコマンド ライン引数の出力方法を示します。  
  
 [!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/how-to-access-command-li_1.cs)]  
  
 [!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/how-to-access-command-li_2.cs)]  
  
## 参照  
 <xref:System.Array>   
 <xref:System.Collections>   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Main\(\) とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [方法: コマンド ライン引数を表示する](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Main\(\) の戻り値](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)