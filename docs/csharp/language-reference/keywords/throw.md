---
title: "throw (C# リファレンス) | Microsoft Docs"
ms.date: "2015-03-02"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "throw"
  - "throw_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "throw キーワード [C#]"
  - "throw ステートメント [C#]"
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
caps.handback.revision: 22
---
# throw (C# リファレンス)
`throw` ステートメントは、プログラムの実行中に例外という異常事態が発生したことを通知するために使用します。  
  
## 解説  
 スローされる例外は、クラスが <xref:System.Exception?displayProperty=fullName> から派生したオブジェクトです。例を次に示します。  
  
```  
class MyException : System.Exception {}  
// ...  
throw new MyException();  
```  
  
 `throw` ステートメントは、`try-catch` ステートメントまたは `try-finally` ステートメントと共に使用するのが一般的です。`catch` ブロックでキャッチされた例外を再びスローするために、`catch` ブロックでは [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントを使用できます。この場合、[throw](../../../csharp/language-reference/keywords/throw.md) ステートメントは例外オペランドを使用しません。使用例を含む詳細については、「[try\-catch](../../../csharp/language-reference/keywords/try-catch.md)」および「[方法 : 例外を明示的にスローする](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)」を参照してください。  
  
## 使用例  
 `throw` ステートメントで例外をスローする例を次に示します。  
  
 [!code-cs[csrefKeywordsExceptions#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/throw_1.cs)]  
  
## コード例  
 「[try\-catch](../../../csharp/language-reference/keywords/try-catch.md)」および「[方法 : 例外を明示的にスローする](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)」の例を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [The try, catch, and throw Statements in C\+\+ \(C\+\+ の try、catch、throw ステートメント\)](../../../csharp/language-reference/keywords/try-catch.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [方法 : 例外を明示的にスローする](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)