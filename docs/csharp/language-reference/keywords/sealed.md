---
title: "sealed (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sealed"
  - "sealed_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "sealed キーワード [C#]"
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# sealed (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`sealed` 修飾子をクラスに適用すると、それ以外のクラスは継承できなくなります。  次の例では、`B` クラスは `A` クラスを継承しますが、どのクラスも `B` クラスを継承できません。  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 `sealed` 修飾子は、基本クラスの仮想メソッドまたはプロパティをオーバーライドするメソッドまたはプロパティで使用することもできます。  これにより、クラスの派生が行えるようになります。また、クラスによって特定のメソッドまたはプロパティがオーバーライドされないようにします。  
  
## 使用例  
 次の例では、`Z` は `Y` から継承します。しかし `Z` は仮想関数 `F` をオーバーライドできません。この仮想関数は `X` で宣言されており、`Y` でシールされています。  
  
 [!code-cs[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 新しいメソッドまたはプロパティをクラスで定義するときに、[virtual](../../../csharp/language-reference/keywords/virtual.md) として宣言しないようにすると、派生クラスによるオーバーライドを防ぐことができます。  
  
 [abstract](../../../csharp/language-reference/keywords/abstract.md) 修飾子をシール クラスで使用するとエラーになります。抽象メソッドまたは抽象プロパティを実装するクラスでは、抽象クラスを継承する必要があるからです。  
  
 メソッドまたはプロパティに適用する場合、`sealed` 修飾子は常に [override](../../../csharp/language-reference/keywords/override.md) と共に使用される必要があります。  
  
 構造体は暗黙にシールされるため、構造体の継承はできません。  
  
 詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。  
  
 その他の例については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
## 使用例  
 [!code-cs[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 上記の例で、次のステートメントを使用してシール クラスからの継承を試みたとします。  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 次のエラー メッセージが表示されることになります。  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 解説  
 クラス、メソッド、またはプロパティをシールするかどうかを判断するには通常、次の 2 つの点を検討する必要があります。  
  
-   クラスをカスタマイズすることで派生クラスに生じ得るメリット。  
  
-   派生クラスがクラスを変更することによって、正しくまたは期待通り機能しなくなる可能性。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
 [アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [修飾子](../../../csharp/language-reference/keywords/modifiers.md)   
 [オーバーライド](../../../csharp/language-reference/keywords/override.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)