---
title: "Composite Data Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic], composite data types"
  - "composite types"
  - "composite data types"
  - "data types [Visual Basic], composite"
  - "arrays [Visual Basic], composite data types"
  - "structures, composite data types"
  - "classes [Visual Basic], composite types"
  - "types [Visual Basic], composite"
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Composite Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] に用意されている基本データ型以外にも、異なる型のアイテムを組み合わせて、構造体、配列、クラスなどの*複合データ型*を作成できます。  基本型および他の複合型から複合データ型を作成できます。  たとえば、構造体要素の配列や配列メンバーを持つ構造体を定義できます。  
  
## データ型  
 複合型は、その構成要素のデータ型とは異なります。  たとえば、整数型 \(`Integer`\) の要素の配列は整数型 \(`Integer`\) ではありません。  
  
 配列データ型は通常、要素の型、かっこ、および必要に応じてコンマを使用して表されます。  たとえば、`String` 型の要素を持つ 1 次元配列は、`String()` として表され、`Boolean` 型の要素を持つ 2 次元配列は、`Boolean(,)` として表されます。  
  
## 構造体型  
 すべての構造体を包括する 1 つのデータ型はありません。  逆に、すべての構造体定義はそれぞれ異なるデータ型を表します。たとえば、まったく同じ要素が同じ順番で定義されている 2 つの構造体があっても、それらは同じデータ型と見なされません。  ただし、同じ構造体の複数のインスタンスを作成した場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はそれらを同じデータ型と見なします。  
  
## 配列型  
 すべての配列を包括する 1 つのデータ型はありません。  配列の特定のインスタンスのデータ型は、次の事項によって決まります。  
  
-   配列であること。  
  
-   配列のランク \(次元数\)。  
  
-   配列の要素型。  
  
 特に、次元の長さはインスタンスのデータ型に含まれません。  次に例を示します。  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 この例では、配列変数 `arrayA` と `arrayB` は異なる長さに初期化されますが、データ型は同じ `Byte()` であると見なされます。  変数 `arrayB` と `arrayC` は、要素型が異なるため同じデータ型ではありません。  変数 `arrayC` と `arrayD` は、ランクが異なるため同じデータ型ではありません。  変数 `arrayD` と変数 `arrayE` は、`arrayD` がまだ初期化されていませんが、ランクも要素型も同じなので、同じ `Short(,)` 型です。  
  
 配列の詳細については、「[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)」を参照してください。  
  
## クラス型  
 すべてのクラスを包括する 1 つのデータ型はありません。  あるクラスが別のクラスを継承することはできますが、それらは別のデータ型です。  同じクラスの複数のインスタンスは、同じデータ型です。  あるクラス インスタンス変数を別のクラス インスタンス変数に代入すると、それらの変数はデータ型が同じであるだけでなく、メモリ内の同じクラス インスタンスを指すことになります。  
  
 クラスの詳細については、「[Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)」を参照してください。  
  
## 参照  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Hold More Than One Value in a Variable](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)