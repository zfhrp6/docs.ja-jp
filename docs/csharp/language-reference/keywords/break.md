---
title: "break (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "break"
  - "break_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "break キーワード [C#]"
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# break (C# リファレンス)
`break` ステートメントは、これを囲むループまたは [switch](../../../csharp/language-reference/keywords/switch.md) ステートメントのうち、最も内側のものを終了させます。  終了したステートメントの次にステートメントがある場合は、そこに制御が移動します。  
  
## 使用例  
 次の例には、条件付きステートメントに 1 から 100 までをカウントするカウンターがあります。ただし、`break` ステートメントによってループは 4 回で終了します。  
  
 [!code-cs[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## 使用例  
 この例では、`break` ステートメントを使用して入れ子になった内側のループから抜け出し、外側のループに制御を戻します。  
  
 [!code-cs[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## 使用例  
 [switch](../../../csharp/language-reference/keywords/switch.md) ステートメント内での `break` の使用例を次に示します。  
  
 [!code-cs[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 `4` を入力すると、出力は次のようになります。  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [switch](../../../csharp/language-reference/keywords/switch.md)   
 [ジャンプ ステートメント](../../../csharp/language-reference/keywords/jump-statements.md)   
 [繰り返しステートメント](../../../csharp/language-reference/keywords/iteration-statements.md)