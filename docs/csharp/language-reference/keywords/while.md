---
title: "while (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "while_CSharpKeyword"
  - "while"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "while キーワード [C#]"
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# while (C# リファレンス)
`while` ステートメントは、指定した式が `false` になるまでステートメントまたはステートメントのブロックを実行します。  
  
## 使用例  
 [!code-cs[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/csharp/while_1.cs)]  
  
## 使用例  
 [!code-cs[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/csharp/while_2.cs)]  
  
## 使用例  
 `while` 式が評価されてからループが実行されるので、`while` ループは 0 回以上実行されます。  [do](../../../csharp/language-reference/keywords/do.md) ループは、これと異なり、1 回以上実行されます。  
  
 `while` ループは、[break](../../../csharp/language-reference/keywords/break.md)、[goto](../../../csharp/language-reference/keywords/goto.md)、[return](../../../csharp/language-reference/keywords/return.md)、または [throw](../../../csharp/language-reference/keywords/throw.md) ステートメントがループの外部に制御を移動すると終了できます。  ループを終了せずに制御を次の繰り返しに渡すには、[continue](../../../csharp/language-reference/keywords/continue.md) ステートメントを使用します。  上記の 3 つの例での出力は、`int n` がインクリメントされる位置によって異なる点に注意してください。  次の例では出力は生成されません。  
  
 [!code-cs[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/csharp/while_3.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [while ステートメント \(C\+\+\)](/visual-cpp/cpp/while-statement-cpp)   
 [繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)