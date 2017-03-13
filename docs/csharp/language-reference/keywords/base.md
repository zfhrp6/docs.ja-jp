---
title: "base (C# リファレンス) | Microsoft Docs"
description: base keyword (C#)
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "base"
  - "BaseClass.BaseClass"
  - "base_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "base キーワード [C#]"
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# base (C# リファレンス)
`base` キーワードは、派生クラス内で基本クラスのメンバーにアクセスするために使用されます。  
  
-   他のメソッドによってオーバーライドされた基本クラスのメソッドを呼び出します。  
  
-   派生クラスのインスタンスを作成するときに呼び出される基本クラスのコンストラクターを指定します。  
  
 基本クラスにアクセスできるのは、コンストラクター内、インスタンスのメソッド内、またはインスタンスのプロパティ アクセサー内だけです。  
  
 静的メソッド内で `base` キーワードを使用するのはエラーです。  
  
 アクセスされる基本クラスは、クラス宣言で指定された基本クラスです。  たとえば、`class ClassB : ClassA` を指定すると、ClassA のメンバーは、ClassA の基本クラスに関係なく、ClassB からアクセスされます。  
  
## 使用例  
 この例では、基本クラス `Person` および派生クラス `Employee` の両方に、`Getinfo` という名前のメソッドがあります。  `base` キーワードを使用すると、基本クラスの `Getinfo` メソッドを派生クラス内で呼び出すことができます。  
  
 [!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]  
  
 その他の例については、「[new](../../../csharp/language-reference/keywords/new.md)」、「[virtual](../../../csharp/language-reference/keywords/virtual.md)」、および「[override](../../../csharp/language-reference/keywords/override.md)」を参照してください。  
  
## 使用例  
 この例では、派生クラスのインスタンスを作成するときに呼び出される、基本クラスのコンストラクターを指定する方法を示します。  
  
 [!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [this](../../../csharp/language-reference/keywords/this.md)