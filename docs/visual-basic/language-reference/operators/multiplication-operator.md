---
title: "* Operator (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.*"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arithmetic operators, multiplication"
  - "operators [Visual Basic], multiplication"
  - "* operator [Visual Basic]"
  - "multiplication operator, syntax"
  - "math operators"
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# * Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

2 つの数値の積を返します。  
  
## 構文  
  
```  
  
number1 * number2  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`number1`|必ず指定します。  任意の数式を指定します。|  
|`number2`|必ず指定します。  任意の数式を指定します。|  
  
## 結果  
 結果は、引数 `number1` と引数 `number2` の積です。  
  
## サポートされている型  
 unsigned 型と浮動小数点型を含むすべての数値型、および 10 進型 \(`Decimal`\)。  
  
## 解説  
 結果のデータ型は、オペランドの型によって決まります。  オペランドの型と結果のデータ型の関係を次の表に示します。  
  
|||  
|-|-|  
|オペランドのデータ型|結果のデータ型|  
|両方の式が整数型 \([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)\) の場合|`number1` と `number2` のデータ型に対して適切な数値データ型。  「[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「整数演算」の表を参照してください。|  
|両方の式が 10 進型 \([Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)\)|`Decimal`|  
|両方の式が単精度浮動小数点型 \([Single](../../../visual-basic/language-reference/data-types/single-data-type.md)\)|`Single`|  
|どちらか一方の式が浮動小数点型 \(`Single` または [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)\) だが、両方が `Single` ではない場合 \(`Decimal` は浮動小数点型ではありません\)|`Double`|  
  
 [Nothing](../../../visual-basic/language-reference/nothing.md) に評価される式は、0 として扱われます。  
  
## オーバーロード  
 `*` 演算子は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `*` 演算子を使って 2 つの数値を乗算する例を次に示します。  結果は、2 つのオペランドの積です。  
  
 [!CODE [VbVbalrOperators#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#4)]  
  
## 参照  
 [\*\= Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [Arithmetic Operators](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)