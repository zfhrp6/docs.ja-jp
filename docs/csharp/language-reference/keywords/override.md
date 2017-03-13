---
title: "override (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "override"
  - "override_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "override キーワード [C#]"
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# override (C# リファレンス)
`override` 修飾子は、継承したメソッド、プロパティ、インデクサー、またはイベントの抽象実装や仮想実装を拡張したり修飾したりする際に必要です。  
  
## 使用例  
 この例では、`Square` クラスが `Area` のオーバーライド実装を提供する必要があります。これは、`Area` が抽象 `ShapesClass` から継承されているためです。  
  
 [!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 `override` メソッドは、基本クラスから継承されたメンバーの新しい実装を提供します。  `override` 宣言によってオーバーライドされたメソッドを、オーバーライドされた基本メソッドと言います。  オーバーライドされた基本メソッドは、`override` メソッドと同じシグネチャを持つ必要があります。  継承の詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。  
  
 非仮想メソッドまたは静的メソッドのオーバーライドはできません。  オーバーライドされる基本メソッドは、`virtual`、`abstract`、または `override` のいずれかである必要があります。  
  
 `override` 宣言は、`virtual` メソッドのアクセシビリティを変更できません。  `override` メソッドと `virtual` メソッドは、同じ[アクセス レベル修飾子](../../../csharp/language-reference/keywords/access-modifiers.md)を持つ必要があります。  
  
 `override` メソッドの修飾に、修飾子 `new`、`static`、または `virtual` は使用できません。  
  
 オーバーライドのプロパティ宣言では、継承されるプロパティと正確に同じアクセス修飾子、型、および名前を指定する必要があります。オーバーライドされるプロパティは、`virtual`、`abstract`、または `override` である必要があります。  
  
 `override` キーワードの使い方の詳細については、「[Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)」および「[Override キーワードと New キーワードを使用する場合について \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」を参照してください。  
  
## 使用例  
 この例では、`Employee` という基本クラスと、`SalesEmployee` という派生クラスを定義します。  `SalesEmployee` クラスには追加のプロパティ `salesbonus` があり、このプロパティを処理に含めるために、`CalculatePay` メソッドをオーバーライドします。  
  
 [!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)