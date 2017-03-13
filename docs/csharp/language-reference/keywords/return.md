---
title: "return (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "return_CSharpKeyword"
  - "return"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "return キーワード [C#]"
  - "return ステートメント [C#]"
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# return (C# リファレンス)
`return` ステートメントは、メソッドの実行を終了し、呼び出し側のメソッドに制御を戻します。  省略可能な値を返すこともできます。  メソッドの型が `void` 型の場合、`return` ステートメントは省略できます。  
  
 return ステートメントが `try` ブロック内にある場合は、制御が呼び出し側のメソッドに返される前に、`finally` ブロック \(存在する場合\) が実行されます。  
  
## 使用例  
 次の例では、メソッド `A()` が変数 `Area` を [double](../../../csharp/language-reference/keywords/double.md) 値として返します。  
  
 [!code-cs[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [return ステートメント](/visual-cpp/cpp/return-statement-cpp)   
 [ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md)