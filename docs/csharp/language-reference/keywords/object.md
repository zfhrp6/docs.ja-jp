---
title: "object (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "object_CSharpKeyword"
  - "object"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "object キーワード [C#]"
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# object (C# リファレンス)
`object` 型は、.NET Framework の <xref:System.Object> のエイリアスです。  C\# の統一型システムでは、定義済みの型やユーザー定義の型、参照型や値型など、すべての型が、<xref:System.Object> から直接的または間接的に継承されます。  任意の型の値を `object` 型の変数に代入できます。  値型の変数をオブジェクトに変換することを "*ボックス化*" と言います。  型オブジェクトの変数を値型に変換することを "*ボックス化解除*" と言います。  詳細については、「[ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)」を参照してください。  
  
## 使用例  
 次の例では、`object` 型の変数が任意のデータ型の値を受け取る方法、および `object` 型の変数が .NET Framework からの <xref:System.Object> のメソッドを使用する方法を示しています。  
  
 [!code-cs[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [参照型](../../../csharp/language-reference/keywords/reference-types.md)   
 [値型](../../../csharp/language-reference/keywords/value-types.md)