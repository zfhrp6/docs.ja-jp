---
title: "MustInherit (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "MustInherit"
  - "vb.MustInherit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic], abstract"
  - "MustInherit classes, MustInherit keyword"
  - "abstract classes, MustInherit class"
  - "MustInherit keyword"
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# MustInherit (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

クラスが基本クラスとしてのみ使用でき、オブジェクトを直接作成できないことを示します。  
  
## 解説  
 *基本クラス* \(*抽象クラス* とも呼ばれます\) の目的は、ここから派生したすべてのクラスに共通した機能を定義することです。  これにより、派生クラスが共通の要素を再定義する必要がなくなります。  有用なオブジェクトを作成するために、この共通の機能では十分でない場合は、派生クラスがそれぞれ足りない機能を定義します。  この場合、使用する側のコードでは、派生クラスからのみオブジェクトを作成できるようにすると便利です。  これを実現するには、基本クラスで `MustInherit` を使用します。  
  
 また、`MustInherit` クラスを使用して、変数を関連するクラスのみに制限できます。  基本クラスを定義し、これらの関連するクラスをすべてここから派生させます。  基本クラスでは、すべての派生クラスに共通の機能を定義する必要はなく、変数に値を割り当てる際のフィルターとして機能させることができます。  使用する側のコードで、変数を基本クラスとして宣言すると、その変数には、いずれかの派生クラスのオブジェクトだけを割り当てることができるようになります。  
  
 .NET Framework では、いくつかの `MustInherit` クラスが定義されています。たとえば、<xref:System.Array>、<xref:System.Enum>、<xref:System.ValueType> などです。  <xref:System.ValueType> は、変数を制限する基本クラスの 1 つです。  すべての値型は <xref:System.ValueType> から派生します。  変数を <xref:System.ValueType> として宣言すると、その変数には値型のみを割り当てられます。  
  
## 規則  
  
-   **宣言コンテキスト。** `MustInherit` は、`Class` ステートメントでのみ使用できます。  
  
-   **結合された修飾子。**同じ変数宣言で `MustInherit` と `NotInheritable` を同時に指定することはできません。  
  
## 使用例  
 次の例では、強制的な継承と強制的なオーバーライドを示します。  基本クラス `shape` は、変数 `acrossLine` を定義します。  `circle` クラスと `square` クラスは、`shape` から継承されます。  これらのクラスは、`acrossLine` の定義を継承しますが、図形の種類によって計算が異なるため、`area` 関数を定義する必要があります。  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/visualbasic/mustinherit_1.vb)]  
  
 `shape1` と `shape2` は、`shape` 型として定義できます。  ただし、`shape` からオブジェクトを作成することはできません。`area` 関数の機能がないことと、`MustInherit` とマークされているためです。  
  
 クラスが `shape` として宣言されているので、変数 `shape1` と `shape2` は派生クラス `circle` および `square` のオブジェクトに限定されます。  Visual Basic では、高いレベルのタイプ セーフを実現するために、その他のオブジェクトをこれらの変数に割り当てることはできません。  
  
## 使用方法  
 `MustInherit` 修飾子は、次の場合に使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## 参照  
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)