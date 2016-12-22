---
title: "\ Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.\"
  - "\"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "division operator, integer"
  - "integer division operator"
  - "zero, division by zero"
  - "arithmetic operators, division"
  - "division, by zero"
  - "backslash (\) [Visual Basic]"
  - "\ operator [Visual Basic]"
  - "integer quotient"
  - "math operators"
  - "quotients, integer"
  - "truncation, integer division"
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# \ Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

2 つの数値の商を計算し、結果を整数で返します。  
  
## 構文  
  
```  
  
expression1 \ expression2  
```  
  
## 指定項目  
 `expression1`  
 必ず指定します。  任意の数式を指定します。  
  
 `expression2`  
 必ず指定します。  任意の数式を指定します。  
  
## サポートされている型  
 unsigned 型と浮動小数点型を含むすべての数値型、および 10 進型 \(`Decimal`\)。  
  
## 結果  
 結果は `expression1` を `expression2` で割った整数の商です。余りはすべて破棄し、整数部分だけが保持されます。  これを*切り捨て*と呼びます。  
  
 結果のデータ型は、`expression1` と `expression2` のデータ型に適した数値型です。  「[Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「整数演算」の表を参照してください。  
  
 [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) は、余りを小数部分に保持する完全な商を返します。  
  
## 解説  
 Visual Basic では、除算を実行する前に、すべての浮動小数点型の数式が長整数型 \(`Long`\) の式に変換されます。  `Option Strict` が `On` であれば、コンパイル エラーが発生します。  `Option Strict` が `Off` の場合でも、値が [Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md) の範囲を超えていれば <xref:System.OverflowException> が発生します。  長整数型 \(`Long`\) への変換でも、*銀行型丸め*が行われます。  詳細については、「[Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)」の「小数部分」を参照してください。  
  
 `expression1` または `expression2` が [Nothing](../../../visual-basic/language-reference/nothing.md) に評価される場合は、式が 0 として扱われます。  
  
## 0 による除算  
 `expression2` が 0 に評価される場合、`\` 演算子は <xref:System.DivideByZeroException> 例外をスローします。  これは、オペランドのデータ型がどの数値型であっても同じです。  
  
> [!NOTE]
>  `\` 演算子は*オーバーロード*できます。つまり、オペランドがクラスや構造体を型として持つ場合に、演算子の動作をそのクラスや構造体で再定義できるという意味です。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `\` 演算子を使って整数の除算を実行する例を次に示します。  結果は、2 つのオペランドの商の整数部分を表す整数です。余りは破棄されます。  
  
 [!CODE [VbVbalrOperators#18](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrOperators#18)]  
  
 この例の式は、2、3、33、および \-22 の値をそれぞれ返します。  
  
## 参照  
 [\\\= Operator](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Arithmetic Operators](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)