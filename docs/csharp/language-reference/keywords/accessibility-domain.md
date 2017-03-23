---
title: "アクセシビリティ ドメイン (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "アクセシビリティ ドメイン [C#]"
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# アクセシビリティ ドメイン (C# リファレンス)
メンバーのアクセシビリティ ドメインは、プログラムのセクション内で、メンバーを参照できる場所を指定します。  メンバーが他の型の入れ子になっている場合、そのメンバーのアクセシビリティ ドメインは、メンバーの[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)と、それを含む型のアクセシビリティ ドメインによって決定されます。  
  
 トップレベルの型のアクセシビリティ ドメインは、少なくとも、その型が宣言されているプロジェクトのプログラム テキストです。  つまり、ドメインには、このプロジェクトのすべてのソース ファイルが含まれていることになります。  入れ子にされた型のアクセシビリティ ドメインは、少なくとも、入れ子にされた型が宣言されている型のプログラム テキストです。  つまり、ドメインは、入れ子にされたすべての型を含む、型の本体です。  入れ子にされた型のアクセシビリティ ドメインは、含んでいる側の型のアクセシビリティ ドメインの外には決して出ません。  これらの概念を次の例で説明します。  
  
## 使用例  
 この例には、トップ レベルの型 `T1` と、2 つの入れ子にされたクラス `M1` および `M2` があります。  クラスには、異なる種類の宣言されたアクセシビリティを持つフィールドがあります。  `Main` メソッドでは、各ステートメントに続くコメントが、各メンバーのアクセシビリティ ドメインを示しています。  アクセス不可のメンバーを参照しようとするステートメントがコメントになっている点に注意してください。  アクセス不可のメンバーを参照したために発生したコンパイラ エラーを見るには、コメントを一度に 1 つずつ解除してください。  
  
 [!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [アクセシビリティ レベルの使用に関する制限事項](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [private](../../../csharp/language-reference/keywords/private.md)   
 [protected](../../../csharp/language-reference/keywords/protected.md)   
 [internal](../../../csharp/language-reference/keywords/internal.md)