---
title: "/演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./
dev_langs:
- VB
helpviewer_keywords:
- division operator, floating point
- floating-point numbers, division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators, division
- division, by zero
- operators [Visual Basic], division
- division operator, syntax
- / operator [Visual Basic]
- math operators
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 71b4f64f6deeb334412c87131ccd9480620f284f
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>/ 演算子 (Visual Basic)
2 つの数値を除算して、浮動小数点の結果を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
expression1 / expression2  
```  
  
## <a name="parts"></a>指定項目  
 `expression1`  
 必須です。 任意の数式。  
  
 `expression2`  
 必須です。 任意の数式。  
  
## <a name="supported-types"></a>サポートされている型  
 署名なしで、浮動小数点型を含むすべての数値型と`Decimal`です。  
  
## <a name="result"></a>結果  
 結果は、すべての商`expression1`で割った値`expression2`、小数部分を含みます。  
  
 [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)残りの部分を削除する整数の商を返します。  
  
## <a name="remarks"></a>コメント  
 結果のデータ型は、オペランドの型によって異なります。 次の表では、結果のデータ型を決定する方法を示します。  
  
|オペランドのデータ型|結果のデータ型|  
|------------------------|----------------------|  
|両方の式が整数データ型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[バイト](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[短い](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)、 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|1 つの式は、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)データ型と、その他は、[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|1 つの式は、 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)データ型とその他のではありません、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)または[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|いずれかの式、[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)データ型|`Double`|  
  
 整数の数式に拡大変換除算を実行する前に`Double`します。 Visual Basic がから結果を変換しようとした場合は、結果を整数データ型を割り当てると、`Double`その型にします。 結果がその型に収まらない場合は、例外がスローすることができます。 具体的には、このページで「0 による除算」を参照してください。  
  
 場合`expression1`または`expression2`に評価[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。  
  
## <a name="attempted-division-by-zero"></a>0 による除算  
 場合`expression2`をゼロに評価される、`/`演算子がオペランドのデータ型の動作とは異なります。 次の表は、それぞれの動作を示します。  
  
|オペランドのデータ型|動作場合`expression2`ゼロ|  
|------------------------|---------------------------------------|  
|浮動小数点 (`Single`または`Double`)|無限大が返されます (<xref:System.Double.PositiveInfinity>または<xref:System.Double.NegativeInfinity>)、または<xref:System.Double.NaN>(非数) 場合`expression1`も&0; である</xref:System.Double.NaN></xref:System.Double.NegativeInfinity></xref:System.Double.PositiveInfinity>|  
|`Decimal`|スローされます。<xref:System.DivideByZeroException></xref:System.DivideByZeroException>|  
|整数 (符号付きまたは符号なし)|整数型への変換を試行<xref:System.OverflowException>整数型を受け入れることはできませんので<xref:System.Double.PositiveInfinity>、 <xref:System.Double.NegativeInfinity>、または<xref:System.Double.NaN></xref:System.Double.NaN></xref:System.Double.NegativeInfinity></xref:System.Double.PositiveInfinity></xref:System.OverflowException>|  
  
> [!NOTE]
>  `/`演算子を指定できます*オーバー ロードされた*、つまり、クラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合です。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義される動作を確認ください。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。  
  
## <a name="example"></a>例  
 この例では、`/`浮動小数点除算を実行する演算子です。 結果は、2 つのオペランドの商です。  
  
 [!code-vb[VbVbalrOperators&#16;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 前の例の式では、2.5 と 3.333333 の値を返します。 結果が常に浮動小数点型ことに注意してください (`Double`) 場合でも、両方のオペランドが整数の定数、します。  
  
## <a name="see-also"></a>関連項目  
 [/= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)   
 [演算子の結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)   
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)

