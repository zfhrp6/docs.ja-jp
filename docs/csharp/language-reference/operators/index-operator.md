---
title: "演算子 (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "[]_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "添字演算子 [C#]"
  - "角かっこ [ ] 演算子 [C#]"
  - "[] 演算子 [C#]"
  - "添字演算子 [C#]"
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# 演算子 (C# リファレンス)
角かっこ \(`[]`\) は、配列、インデクサー、および属性で使用します。  角かっこは、ポインターでも使用できます。  
  
## 解説  
 配列型は、型名の後に `[]` が続きます。  
  
 [!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#43)]  
  
 配列の要素にアクセスするには、目的の要素の添字を角かっこで囲みます。  
  
 [!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#44)]  
  
 配列の添字が範囲外の場合は、例外がスローされます。  
  
 配列の添字演算子は、オーバーロードできません。ただし、型ではインデクサーおよび 1 つ以上のパラメーターをとるプロパティを定義できます。  インデクサーのパラメーターは配列の添字と同じように角かっこで囲みますが、整数でなければならない配列の添字とは異なり、インデクサーのパラメーターは任意の型として宣言できます。  
  
 たとえば、.NET Framework では任意の型のキーと値を関連付ける `Hashtable` 型を定義しています。  
  
 [!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#45)]  
  
 角かっこは、[属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)を指定するためにも使用します。  
  
 [!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#46)]  
  
 角かっこを使用して、ポインターにインデックスを作成できます。  
  
 [!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/csharp/csrefOperators/csrefOperators.cs#47)]  
  
 添字の範囲チェックは行われません。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)   
 [配列](../../../csharp/programming-guide/arrays/index.md)   
 [インデクサー](../../../csharp/programming-guide/indexers/index.md)   
 [安全でない](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)