---
title: "データの種類の演算子の結果 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types
- operator result data types
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
caps.latest.revision: 27
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
ms.openlocfilehash: 577be6330cb76da436470c383841a717dd6e3200
ms.lasthandoff: 03/13/2017

---
# <a name="data-types-of-operator-results-visual-basic"></a>演算子の結果のデータ型 (Visual Basic)
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]オペランドのデータ型に基づく操作の結果のデータ型を決定します。 場合によっては、データ型のいずれかのオペランドよりも広い範囲でこれがあります。  
  
## <a name="data-type-ranges"></a>データ型の範囲  
 最小から最大値、順序で、該当するデータ型の範囲は次のとおりです。  
  
-   [ブール](../../../visual-basic/language-reference/data-types/boolean-data-type.md)-2 つの値  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[バイト](../../../visual-basic/language-reference/data-types/byte-data-type.md)— 256 の整数値  
  
-   [短い](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65,536 (6.5. E + 4) 使用可能な整数値  
  
-   [整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)、 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4,294,967,296 (4.2. E + 9) 使用可能な整数値  
  
-   [長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18,446,744,073,709,551,615 (1.8. E + 19) 使用可能な整数値  
  
-   [10 進](../../../visual-basic/language-reference/data-types/decimal-data-type.md)— 1.5. E + 29 可能な整数値、最大の範囲は 7.9. E + 28 (絶対値)  
  
-   [単一](../../../visual-basic/language-reference/data-types/single-data-type.md)-最大範囲 3.4 E + 38 (絶対値)  
  
-   [二重](../../../visual-basic/language-reference/data-types/double-data-type.md)-最大範囲 1.7 E + 308 (絶対値)  
  
 詳細については[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データ型を参照してください[データ型](../../../visual-basic/language-reference/data-types/data-type-summary.md)します。  
  
 オペランドが評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]算術演算子が&0; として処理します。  
  
## <a name="decimal-arithmetic"></a>10 進数の算術演算子  
 なお、 [10 進数](../../../visual-basic/language-reference/data-types/decimal-data-type.md)データ型は、どちらも浮動小数点も整数。  
  
 場合のいずれかのオペランド、 `+`、 `–`、 `*`、 `/`、または`Mod`操作が`Decimal`がないと`Single`または`Double`、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]をもう一方のオペランドは拡大し、`Decimal`です。 操作を実行`Decimal`、結果のデータ型は`Decimal`です。  
  
## <a name="floating-point-arithmetic"></a>浮動小数点数演算  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ほとんどの浮動小数点演算を実行[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)、これは最も効率的なデータなどの操作を入力します。 ただし、1 つのオペランドが場合[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)がないと`Double`、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]で操作を実行`Single`します。 各オペランドは、操作の前に適切なデータ型を必要に応じて、拡大変換し、結果がそのデータ型を持ちます。  
  
### <a name="-and--operators"></a>/、^ 演算子  
 `/`演算子に対してのみ定義されます、 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)、および[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)データ型。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]そのデータ型を操作と、結果がある前に各オペランドは、適切なデータ型を必要に応じて幅が広がります。  
  
 次の表は、結果のデータ型、`/`演算子。 このテーブルは、対称; ことに注意してください。オペランドのデータ型の特定の組み合わせについては、結果のデータ型は、オペランドの順序に関係なく同じです。  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|任意の整数型|  
|`Decimal`|Decimal (10 進数型)|Single|倍精度浮動小数点型|Decimal (10 進数型)|  
|`Single`|Single|Single|倍精度浮動小数点型|Single|  
|`Double`|倍精度浮動小数点型|Double (倍精度浮動小数点型)|Double (倍精度浮動小数点型)|倍精度浮動小数点型|  
|任意の整数型|Decimal (10 進数型)|Single|倍精度浮動小数点型|倍精度浮動小数点型|  
  
 `^`演算子は定義のみ、`Double`データ型。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]拡大変換後の各オペランドを必要に応じて`Double`、操作すると、結果のデータ型は常に`Double`します。  
  
## <a name="integer-arithmetic"></a>整数の算術演算子  
 整数演算の結果のデータ型は、オペランドのデータ型に依存します。 一般に、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]結果のデータ型を決定するため、次のポリシーを使用します。  
  
-   二項演算子の両方のオペランドが同じであるかどうかは結果データ型、そのデータ型を持ちます。 例外は、 `Boolean`、これが強制的に`Short`します。  
  
-   符号なしのオペランドが符号付きのオペランドで参加すると場合、結果は符号付きの型と、最低範囲いずれかのオペランドとして。  
  
-   それ以外の場合、結果通常は&2; つのオペランドのデータ型のうち、大きい方。  
  
 結果のデータ型ができないこと、オペランドのデータ型と同じに注意してください。  
  
> [!NOTE]
>  結果のデータ型は常に、操作によって発生したすべての可能な値を保持するのに十分ではないです。 <xref:System.OverflowException>結果のデータ型の値が大きすぎる場合に、例外が発生することができます</xref:System.OverflowException>。  
  
### <a name="unary--and--operators"></a>単項 + と ~ 演算子  
 次の表は、2 つの単項演算子の結果のデータ型を示します`+`と`–`です。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|単項`+`|Short|SByte|Byte|Short|UShort|整数|UInteger|Long|ULong|  
|単項`–`|Short|SByte|Short|Short|整数|整数|Long|Long|Decimal (10 進数型)|  
  
### <a name="-and--operators"></a><\<>> 演算子  
 次の表は、2 つのビット シフト演算子の結果のデータ型を示します`<<`と`>>`です。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]各ビット シフト演算子を単項演算子の左側のオペランド (をシフトするビット パターン) として扱われます。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|整数|UInteger|Long|ULong|  
  
 左側のオペランドがの場合`Decimal`、 `Single`、 `Double`、または`String`、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]に変換しようとしています。 `Long` 、操作すると、結果のデータ型は`Long`です。 右側のオペランド (シフトするビット位置の数) である必要があります`Integer`またはに拡大変換できる型`Integer`します。  
  
### <a name="binary----and-mod-operators"></a>バイナリ +、-、*、および Mod 演算子  
 次の表は、結果のバイナリのデータ型を示しています`+`と`–`演算子および`*`と`Mod`演算子。 このテーブルは、対称; ことに注意してください。オペランドのデータ型の特定の組み合わせについては、結果のデータ型は、オペランドの順序に関係なく同じです。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整数|整数|Long|Long|Decimal (10 進数型)|  
|`SByte`|SByte|SByte|Short|Short|整数|整数|Long|Long|Decimal (10 進数型)|  
|`Byte`|Short|Short|Byte|Short|UShort|整数|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整数|整数|Long|Long|Decimal (10 進数型)|  
|`UShort`|整数型|整数|UShort|整数|UShort|整数|UInteger|Long|ULong|  
|`Integer`|整数型|整数|整数|整数|整数|整数|Long|Long|Decimal (10 進数型)|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal (10 進数型)|  
|`ULong`|Decimal (10 進数型)|Decimal (10 進数型)|ULong|Decimal (10 進数型)|ULong|Decimal (10 進数型)|ULong|Decimal (10 進数型)|ULong|  
  
### <a name="-operator"></a>\ 演算子  
 次の表は、結果のデータ型、`\`演算子。 このテーブルは、対称; ことに注意してください。オペランドのデータ型の特定の組み合わせについては、結果のデータ型は、オペランドの順序に関係なく同じです。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整数|整数|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整数|整数|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|整数|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整数|整数|Long|Long|Long|  
|`UShort`|整数型|整数|UShort|整数|UShort|整数|UInteger|Long|ULong|  
|`Integer`|整数型|整数|整数|整数|整数|整数|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 場合のいずれかのオペランド、`\`演算子は[10 進](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)、または[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]に変換しようとしています。[長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、操作すると、結果のデータ型は`Long`です。  
  
## <a name="relational-and-bitwise-comparisons"></a>リレーショナルとビットごとの比較  
 リレーショナル操作の結果のデータ型 (`=`、 `<>`、 `<`、 `>`、 `<=`、 `>=`) は常に`Boolean`[ブール データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)します。 論理操作の場合も同様です (`And`、 `AndAlso`、 `Not`、 `Or`、 `OrElse`、 `Xor`) で`Boolean`オペランド。  
  
 ビットごとの論理演算の結果のデータ型は、オペランドのデータ型に依存します。 注意してください`AndAlso`と`OrElse`に対してのみ定義`Boolean`、および[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を必要に応じて、各オペランドを変換`Boolean`操作を実行する前にします。  
  
### <a name="-----and--operators"></a>=, <>, \<, >, \<=, and >= Operators  
 両方のオペランドが場合`Boolean`、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]考慮`True`するより小さい`False`します。 数値型を比較する場合、 `String`、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]に変換しようと、`String`に`Double`操作の前にします。 A`Char`または`Date`オペランドが同じデータ型のオペランドとのみ比較できます。 結果のデータ型は常に`Boolean`します。  
  
### <a name="bitwise-not-operator"></a>ビットごとの Not 演算子  
 次の表は、結果のビットごとのデータ型を示しています`Not`演算子。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|ブール型|SByte|Byte|Short|UShort|整数|UInteger|Long|ULong|  
  
 場合は、オペランドが`Decimal`、 `Single`、 `Double`、または`String`、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]に変換しようとしています。 `Long` 、操作すると、結果のデータ型は`Long`です。  
  
### <a name="bitwise-and-or-and-xor-operators"></a>ビットごと、または、および Xor 演算子  
 次の表は、結果のビットごとのデータ型を示しています`And`、 `Or`、および`Xor`演算子。 このテーブルは、対称; ことに注意してください。オペランドのデータ型の特定の組み合わせについては、結果のデータ型は、オペランドの順序に関係なく同じです。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|ブール型|SByte|Short|Short|整数|整数|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整数|整数|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|整数|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整数|整数|Long|Long|Long|  
|`UShort`|整数型|整数|UShort|整数|UShort|整数|UInteger|Long|ULong|  
|`Integer`|整数型|整数|整数|整数|整数|整数|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 オペランドは場合`Decimal`、 `Single`、 `Double`、または`String`、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]に変換しようとしています。 `Long` 、操作すると、結果のデータ型は、場合と同じにそのオペランドが既に`Long`します。  
  
## <a name="miscellaneous-operators"></a>その他の演算子  
 `&`演算子は連結したものに対してのみ定義`String`オペランド。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]各オペランドを必要に応じて変換`String`、操作すると、結果のデータ型は常に`String`します。 ため、`&`演算子、すべての変換に`String`拡大変換と見なされる場合でも`Option Strict`は`On`です。  
  
 `Is`と`IsNot`演算子がオペランドは両方とも参照型である必要があります。 The `TypeOf`...`Is`式は、参照型である&1; 番目のオペランドと&2; 番目のオペランドのデータ型の名前にする必要があります。 これらすべての場合、結果のデータ型は`Boolean`です。  
  
 `Like`のパターンに一致する場合にのみこの演算子が定義された`String`オペランド。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]必要に応じて各オペランドを変換しようと`String`操作の前にします。 結果のデータ型は常に`Boolean`します。  
  
## <a name="see-also"></a>関連項目  
 [データ型](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [演算子よぶ式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Visual Basic における比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [演算子](../../../visual-basic/language-reference/operators/index.md)   
 [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
