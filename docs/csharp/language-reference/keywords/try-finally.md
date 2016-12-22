---
title: "try-finally (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "finally"
  - "finally_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "finally キーワード [C#]"
  - "try-finally ステートメント [C#]"
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# try-finally (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`finally` ブロックを使用すると、[try](../../../csharp/language-reference/keywords/try-catch.md) ブロックで割り当てられたリソースをクリーンアップし、`try` ブロックで例外が発生してもコードを実行することができます。  通常、制御が `try` ステートメントを離れると、`finally` ブロックのステートメントが実行されます。  制御の移動は、`break` ステートメント、`continue` ステートメント、`goto` ステートメント、`return` またはステートメントの正常な実行の結果や、`try` ステートメントで生じた例外の反映の結果として生じます。  
  
 ハンドルされている例外では、関連する `finally` ブロックの実行が保証されます。  ただし、例外がハンドルされていない場合、`finally` ブロックの実行は、例外のアンワインド操作のトリガー方法に依存します。  つまり、コンピューターの設定に依存するということでもあります。  詳細については、「[CLR のハンドルされない例外の処理](http://go.microsoft.com/fwlink/?LinkId=128371)」を参照してください。  
  
 通常、ハンドルされていない例外によってアプリケーションが終了した場合、`finally` ブロックが実行されるかどうかは重要ではありません。  ただし、このような状況でも実行する必要のあるステートメントが `finally` ブロックにある場合は、`try`\-`finally` ステートメントに `catch` ブロックを追加するという方法があります。  または、`try`\-`finally` ステートメントの `try` ブロックでスローされた例外があれば、コール スタックの上の方でキャッチすることもできます。  つまり、`try`\-`finally` ステートメントが含まれているメソッドを呼び出すメソッド内でも、そのメソッドを呼び出すメソッド内でも、コール スタック内の任意のメソッド内でも、例外をキャッチできるということです。  例外がキャッチされない場合、`finally` ブロックの実行は、例外のアンワインド操作がオペレーティング システムによってトリガーされるかどうかに依存します。  
  
## 使用例  
 次の例では、無効な変換ステートメントによって `System.InvalidCastException` 例外が発生しています。  この例外はハンドルされていません。  
  
 [!code-cs[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 次の例では、コール スタックのずっと上の方のメソッド内で `TryCast` メソッドからの例外がキャッチされます。  
  
 [!code-cs[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 `finally` の詳細については、「[try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)」を参照してください。  
  
 C\# には、<xref:System.IDisposable> オブジェクトに対して同様の機能を便利な構文で提供する [using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)も含まれています。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [try、throw、および catch ステートメント \(C\+\+\)](/visual-cpp/cpp/try-throw-and-catch-statements-cpp)   
 [例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [方法 : 例外を明示的にスローする](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)