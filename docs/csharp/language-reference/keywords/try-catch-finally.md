---
title: "try-catch-finally (C# リファレンス) | Microsoft Docs"
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
  - "catch-finally_CSharpKeyword"
  - "catch-finally"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "finally ブロック [C#]"
  - "try-catch ステートメント [C#]"
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# try-catch-finally (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

通常、`catch` および `finally` は、`try` ブロックのリソースを取得して使用する場合に、対で記述されます。`catch` ブロックで例外的な状況を処理し、`finally` ブロックでリソースを解放します。  
  
 例外の再スローの詳細および例については、「[try\-catch](../../../csharp/language-reference/keywords/try-catch.md)」および「[例外のスロー](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)」を参照してください。  `finally` ブロックに関する詳細については、 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)を参照してください。  
  
## 使用例  
 [!code-cs[csrefKeywordsExceptions#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch-finally_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [try、throw、および catch ステートメント \(C\+\+\)](/visual-cpp/cpp/try-throw-and-catch-statements-cpp)   
 [例外処理ステートメント](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [方法 : 例外を明示的にスローする](../Topic/How%20to:%20Explicitly%20Throw%20Exceptions.md)   
 [using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)