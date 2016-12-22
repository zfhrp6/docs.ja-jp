---
title: "/ Operator (Visual Basic) | Microsoft Docs"
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
  - "vb./"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "division operator, floating point"
  - "floating-point numbers, division operator"
  - "slash (/) operator"
  - "zero, division by zero"
  - "operators [Visual Basic], arithmetic"
  - "arithmetic operators, division"
  - "division, by zero"
  - "operators [Visual Basic], division"
  - "division operator, syntax"
  - "/ operator [Visual Basic]"
  - "math operators"
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# / Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

2 つの数値の商を計算し、結果を浮動小数点で返します。  
  
## 構文  
  
```  
  
expression1 / expression2  
```  
  
## 指定項目  
 `expression1`  
 必ず指定します。  任意の数式を指定します。  
  
 `expression2`  
 必ず指定します。  任意の数式を指定します。  
  
## サポートされている型  
 unsigned 型と浮動小数点型を含むすべての数値型、および 10 進型 \(`Decimal`\)。  
  
## 結果  
 結果は `expression1` を `expression2` で割った、剰余を含む完全な商です。  
  
 The [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md) は整数の商を返します。剰余は破棄します。  
  
## 解説  
 結果のデータ型は、オペランドの型によって決まります。  オペランドの型と結果のデータ型の関係を次の表に示します。  
  
|オペランドのデータ型|結果のデータ型|  
|----------------|-------------|  
|両方の式が整数型 \([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)\) の場合|`Double`|  
|一方の式が [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) データ型でもう一方が [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) でない場合|`Single`|  
|一方の式が [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) データ型でもう一方が [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) でも [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) でもない場合|`Decimal`|  
|どちらかの式が [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) データ型の場合|`Double`|  
  
 除算を実行する前に、整数の数式は必ず `Double` 型に拡大変換されます。  結果を整数型に代入する場合は、結果が `Double` からその型に変換されます。  このとき、結果がその型に合わなければ、例外がスローされます。  詳細は、このヘルプ ページの「0 による除算」を参照してください。  
  
 `expression1` または `expression2` が [Nothing](../../../visual-basic/language-reference/nothing.md) に評価される場合は、式が 0 として扱われます。  
  
## 0 による除算  
 `expression2` が 0 に評価される場合、`/` 演算子はオペランドのデータ型の違いに応じて異なる動作をします。  次の表に、それぞれの動作を示します。  
  
|オペランドのデータ型|`expression2` が 0 の場合の動作|  
|----------------|------------------------------|  
|浮動小数点型 \(`Single` または `Double`\)|無限大 \(<xref:System.Double.PositiveInfinity> または <xref:System.Double.NegativeInfinity>\) を返すか、`expression1` も 0 であれば <xref:System.Double.NaN> \(非数値\) を返します|  
|`Decimal`|<xref:System.DivideByZeroException> をスローします|  
|整数 \(符号付きまたは符号なし\)|整数型に変換して戻そうとすると、整数型が <xref:System.Double.PositiveInfinity>、<xref:System.Double.NegativeInfinity>、または <xref:System.Double.NaN> を処理できないため <xref:System.OverflowException> がスローされます。|  
  
> [!NOTE]
>  `/` 演算子は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `/` 演算子を使って浮動小数点の除算を実行する例を次に示します。  結果は、2 つのオペランドの商です。  
  
 [!CODE [VbVbalrOperators#16](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#16)]  
  
 この例の式は、2.5 と 3.333333 の値を返します。  たとえ両方のオペランドが整数定数であっても、結果が必ず浮動小数点 \(`Double`\) になっていることに注意してください。  
  
## 参照  
 [\/\= Operator](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)   
 [Arithmetic Operators](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)