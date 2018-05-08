---
title: バイト型 (Byte) (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28189ab4ab1a9be9265d1cca020039b5302fb5d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="byte-data-type-visual-basic"></a>Byte データ型 (Visual Basic)
0 から 255 までの範囲の 8 ビット (1 バイト) の符号なし整数を保持します。

## <a name="remarks"></a>コメント

使用して、`Byte`バイナリ データを格納するデータ型。  
  
`Byte` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラルの割り当て

宣言して初期化することができます、`Byte`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。 整数リテラルは、範囲の場合、 `Byte` (である場合より小さい<xref:System.Byte.MinValue?displayProperty=nameWithType>以上<xref:System.Byte.MaxValue?displayProperty=nameWithType>)、コンパイル エラーが発生します。

次の例では、整数と等しい 16 進数、10 進数として表される 201 とからバイナリ リテラルを暗黙的に変換[整数](integer-data-type.md)に`byte`値。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。 例えば:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>プログラミングのヒント

-   **負の数。** `Byte`符号なしの型は、負の数を表すことはできません。 単項マイナスを使用する場合 (`-`) 型に評価される式で演算子`Byte`、Visual Basic の式を変換する`Short`最初。
  
-   **形式を変換します。** Visual Basic の読み取りまたは書き込みをファイルまたは Dll、メソッド、およびプロパティを呼び出すとき、データ形式間で自動的に変換できます。 格納されているバイナリ データ`Byte`変数および配列はこのような形式の変換中に保持されます。 使用しないで、 `String` ANSI、Unicode 形式の間で変換中にその内容が破損する可能性があるため、バイナリ データの変数です。

-   **拡大します。** `Byte`拡大変換後のデータ型`Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、 `ULong`、 `Decimal`、 `Single`、または`Double`です。 つまり、変換することができます`Byte`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。
  
-   **型宣言文字。** `Byte` リテラルの型文字または識別子の型文字がありません。

-   **Framework の型。** .NET Framework において対応する型は、<xref:System.Byte?displayProperty=nameWithType> 構造体です。

## <a name="example"></a>例

 次の例では、`b`は、`Byte`変数。 ステートメントでは、変数の範囲およびにビット シフト演算子の適用を示しています。

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>関連項目

 <xref:System.Byte?displayProperty=nameWithType>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
