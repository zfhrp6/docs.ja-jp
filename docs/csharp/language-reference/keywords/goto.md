---
title: "goto (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "goto_CSharpKeyword"
  - "goto"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "goto キーワード [C#]"
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# goto (C# リファレンス)
`goto` ステートメントは、プログラムの制御をラベル付きステートメントに直接移動します。  
  
 通常、`goto` は `switch` ステートメントの特定の switch\-case ラベルまたは default ラベルに制御を移動するのに使用します。  
  
 `goto` ステートメントは、階層の深い入れ子のループから抜ける際にも便利です。  
  
## 使用例  
 次の例は、[switch](../../../csharp/language-reference/keywords/switch.md) ステートメントでの `goto` の使用方法を示しています。  
  
 [!code-cs[csrefKeywordsJump#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_1.cs)]  
  
## 使用例  
 入れ子のループから `goto` で抜け出す例を次に示します。  
  
 [!code-cs[csrefKeywordsJump#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/goto_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [goto ステートメント](/visual-cpp/cpp/goto-statement-cpp)   
 [ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md)