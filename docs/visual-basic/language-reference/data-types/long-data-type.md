---
title: Long 型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 687c235be76ef522758658fd1c5fe0cb1dbeb414
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591367"
---
# <a name="long-data-type-visual-basic"></a>長い形式のデータ型 (Visual Basic)

符号付き 64 ビット (8 バイト) の整数 9,223,372,036,854,775,807 を通じて-9,223,372,036,854,775,808 から値の範囲 (9.2... E + 18) です。  
  
## <a name="remarks"></a>コメント

 使用して、`Long`が大きすぎてに収まるように整数値を格納するデータ型、`Integer`データ型。  
  
 `Long` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラルの割り当て 

宣言して初期化することができます、`Long`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。 整数リテラルが `Long` の範囲外にある場合 (つまり、<xref:System.Int64.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int64.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 4,294,967,296 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Long` 値に割り当てられています。
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。 例えば:

```vb
Dim number As Long = &H_0FAC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

数値リテラルを含めることも、 `L` [文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`Long`データ型は、次の例のようにします。

```vb
Dim number = &H_0FAC_0326_1489_D68CL
```

## <a name="programming-tips"></a>プログラミングのヒント

-   **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合の点に注意`Long`が他の環境で別のデータ幅 (32 ビット) を持ちます。 このようなコンポーネントに 32 ビットの引数を渡す場合として宣言`Integer`の代わりに`Long`新しい Visual Basic コードでします。  
  
-   **拡大します。** `Long`拡大変換後のデータ型`Decimal`、 `Single`、または`Double`です。 これは、`Long` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
-   **型宣言文字。** あるリテラルにリテラルの型文字 `L` を付けると、そのリテラルは `Long` に変換されます。 ある識別子に識別子の型文字 `&` を付けると、その識別子は整数型 (`Long`) に変換されます。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.Int64?displayProperty=nameWithType> 構造体です。  

## <a name="see-also"></a>関連項目

<xref:System.Int64>
[データ型](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
[整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
[Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)   
[型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
[変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
[データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
