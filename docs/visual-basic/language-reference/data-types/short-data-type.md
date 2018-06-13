---
title: Short 型 (Visual Basic)
ms.date: 01/31/2018
author: rpetrusha
ms.author: ronpet
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: ef99743828d8d80844486b651178622ff45fd554
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590713"
---
# <a name="short-data-type-visual-basic"></a>Short データ型 (Visual Basic)
符号付き 16 ビット (2 バイト) 整数-32,768 からの値の範囲は、32,767 までです。  
  
## <a name="remarks"></a>コメント  
 使用して、`Short`データ型の完全なデータの幅を必要としない整数値を含む`Integer`です。 場合によっては、共通言語ランタイムがパックことができます、`Short`変数密接に関連しておよびメモリの消費量を保存します。  
  
 `Short` の既定値は 0 です。  
  
## <a name="literal-assignments"></a>リテラルの割り当て

宣言して初期化することができます、`Short`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。 整数リテラルが `Short` の範囲外にある場合 (つまり、<xref:System.Int16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数と等しい 16 進数、10 進数として表される 1,034 およびからバイナリ リテラルを暗黙的に変換[整数](integer-data-type.md)に`Short`値。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。 例えば:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

数値リテラルを含めることも、 `S` [文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`Short`データ型は、次の例のようにします。

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>プログラミングのヒント

-   **拡大します。** `Short`拡大変換後のデータ型`Integer`、 `Long`、 `Decimal`、 `Single`、または`Double`です。 これは、`Short` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
-   **型宣言文字。** あるリテラルにリテラルの型文字 `S` を付けると、そのリテラルは `Short` に変換されます。 `Short` 識別子の型文字がありません。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.Int16?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

 <xref:System.Int16?displayProperty=nameWithType>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
