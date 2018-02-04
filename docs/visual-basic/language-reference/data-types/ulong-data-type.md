---
title: "ULong 型 (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 606e0ef87b209bb2e75e28223f27d081713c1b7e
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="ulong-data-type-visual-basic"></a>ULong データ型 (Visual Basic)

18,446,744,073,709,551,615 ~ 0 の値で範囲の符号なし 64 ビット (8 バイト) 整数 (1.84 倍以上の 10 ^19)。  
  
## <a name="remarks"></a>コメント

使用して、`ULong`データ型に対して大きすぎますバイナリ データを格納する`UInteger`、最大の可能な符号なし整数値またはします。  
  
`ULong` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラルの割り当て

宣言して初期化することができます、`ULong`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。 整数リテラルが `ULong` の範囲外にある場合 (つまり、<xref:System.UInt64.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt64.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 7,934,076,125 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`ULong` 値に割り当てられています。
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。 例:

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

数値リテラルを含めることも、`UL`または`ul`[文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`ULong`データ型は、次の例のようにします。

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a>プログラミングのヒント
  
-   **負の数。** `ULong`符号なしの型は、負の数を表すことはできません。 単項マイナスを使用する場合 (`-`) 型に評価される式で演算子`ULong`、Visual Basic の式を変換する`Decimal`最初。  
  
-   **CLS 準拠しています。** `ULong`データ型がの一部、[共通言語仕様](http://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)、CLS 準拠コードがそれを使用するコンポーネントを使用できないようにします。  
  
-   **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合などの型を注意して`ulong`他の環境で別のデータ幅 (32 ビット) を持つことができます。 このようなコンポーネントに 32 ビットの引数を渡す場合として宣言`UInteger`の代わりに`ULong`マネージ コードを Visual Basic でします。  
  
     さらに、Windows 95、Windows 98、Windows ME、または Windows 2000 では 64 ビット整数の自動化はできません。 Visual Basic を渡すことはできません`ULong`これらのプラットフォームでのオートメーション コンポーネントへの引数。  
  
-   **拡大します。** `ULong`拡大変換後のデータ型`Decimal`、 `Single`、および`Double`です。 つまり、変換することができます`ULong`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。  
  
-   **型宣言文字。** リテラルの型文字を付加`UL`リテラルにリテラルを`ULong`データ型。 `ULong`識別子の型文字がありません。
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.UInt64?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

 <xref:System.UInt64>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
