---
title: "Mod 演算子 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Mod"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "剰余 (Mod 演算子)"
  - "除算演算子、Mod 演算子"
  - "剰余演算子、Visual Basic"
  - "Mod 演算子 [Visual Basic]"
  - "演算子 [Visual Basic]、除算"
  - "算術演算子、Mod"
  - "数値演算子"
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Mod 演算子 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

2 つの数字を除算して剰余のみを返します。  
  
## 構文  
  
```  
  
number1 Mod number2  
```  
  
## 指定項目  
 `number1`  
 必須です。  任意の数式を指定します。  
  
 `number2`  
 必須です。  任意の数式を指定します。  
  
## サポートされている型  
 すべての数値型。  これには、符号なし、浮動小数点、`Decimal` が含まれます。  
  
## 結果  
 結果は `number1` を `number2` で割った後の剰余になります。  たとえば、"`14 Mod 4`" という式は 2 に評価されます。  
  
## 解説  
 `number1` または `number2` が浮動小数点値であった場合、浮動小数点の剰余が返されます。  結果のデータ型は、`number1` と `number2` のデータ型で除算を行った結果として想定される、あらゆる値の格納が可能なデータ型の中で、最も小さい型になります。  
  
 `number1` または `number2` が [Nothing](../../../visual-basic/language-reference/nothing.md) に評価される場合は、式が 0 として扱われます。  
  
 関連する演算子としては、次のものが挙げられます。  
  
-   [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md) は、除算の結果として得られる整数の商を返します。  たとえば、"`14 \ 4`" という式は 3 に評価されます。  
  
-   [\/ Operator](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) は、剰余を含む完全な商を、浮動小数点数として返します。  たとえば、"`14 / 4`" という式は 3.5 に評価されます。  
  
## 0 による除算  
 `number2` が 0 である場合、`Mod` 演算子の動作はオペランドのデータ型に応じて異なります。  整数を 0 で除算すると <xref:System.DivideByZeroException> 例外がスローされます。  浮動小数点数を 0 で除算すると、<xref:System.Double.NaN> が返されます。  
  
## 等価な数式  
 次の数式は、いずれも "`a Mod b`" と同じ意味になります。  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## 浮動小数点の不正確性  
 浮動小数点数を扱う場合、これらの値がメモリ内で常に正確に表現されているわけではないことに注意してください。  このため、値の比較や `Mod` 演算子など、特定の処理で予期しない結果が返される可能性があります。  詳細については、「[Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。  
  
## オーバーロード  
 `Mod` 演算子の動作は、クラスまたは構造体で再定義できます。これを演算子の*オーバーロード*といいます。  このようなオーバーロードを含むクラスまたは構造体のインスタンスに `Mod` を適用する場合は、再定義された動作を十分に理解しておく必要があります。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `Mod` 演算子を使って、2 つの数値の除算を行い、その剰余を取得する例を次に示します。  どちらかの数値が浮動小数点数の場合、結果は剰余を表す浮動小数点数になります。  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## 使用例  
 浮動小数点数のオペランドによって誤差が生じる例を次に示します。  最初のステートメントのオペランドは、どちらも倍精度浮動小数点型 \(`Double`\) であり、無限に繰り返されるバイナリ分数である 0.2 が、値 0.20000000000000001 として格納されています。  2 つ目のステートメントでは、リテラルの型文字 `D` が指定されているため、2 つのオペランドが 10 進型 \(`Decimal`\) になり、0.2 が正確に表現されています。  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>   
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [\\ Operator](../../../visual-basic/language-reference/operators/integer-division-operator.md)