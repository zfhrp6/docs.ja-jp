---
title: UInteger 型
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1c734578abd55270dd6feb9060d02691a6aaf8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591339"
---
# <a name="uinteger-data-type"></a>UInteger データ型

保持符号なし 32 ビット (4 バイト) 0 ~ 整数 4,294,967,295 です。  
  
## <a name="remarks"></a>コメント

 `UInteger`データ型は、最も効率的なデータの幅の最大の符号なしの値を提供します。  
  
 `UInteger` の既定値は 0 です。  
  
## <a name="literal-assignments"></a>リテラルの割り当て

宣言して初期化することができます、`UInteger`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。 整数リテラルが `UInteger` の範囲外にある場合 (つまり、<xref:System.UInt32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 3,000,000,000 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`UInteger` 値に割り当てられています。
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。 例えば:

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

数値リテラルを含めることも、`UI`または`ui`[文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`UInteger`データ型は、次の例のようにします。

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a>プログラミングのヒント

 `UInteger`と`Integer`できないために、データ型が、32 ビットのプロセッサで最適なパフォーマンスを提供小さい整数型 (`UShort`、 `Short`、 `Byte`、および`SByte`) 少量のビットを使用する場合でも、時間がかかります読み込み、格納、およびフェッチします。  
  
-   **負の数。** `UInteger`符号なしの型は、負の数を表すことはできません。 単項マイナスを使用する場合 (`-`) 型に評価される式で演算子`UInteger`、Visual Basic の式を変換する`Long`最初。  
  
-   **CLS 準拠しています。** `UInteger`データ型がの一部、[共通言語仕様](http://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)、CLS 準拠コードがそれを使用するコンポーネントを使用できないようにします。
  
-   **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合などの型を注意して`uint`他の環境で別のデータ幅 (16 ビット) を持つことができます。 このようなコンポーネントに 16 ビットの引数を渡す場合として宣言`UShort`の代わりに`UInteger`マネージ コードを Visual Basic でします。  
  
-   **拡大します。** `UInteger`拡大変換後のデータ型`Long`、 `ULong`、 `Decimal`、 `Single`、および`Double`です。 つまり、変換することができます`UInteger`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。  
  
-   **型宣言文字。** リテラルの型文字を付加`UI`リテラルにリテラルを`UInteger`データ型。 `UInteger` 識別子の型文字がありません。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.UInt32?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.UInt32>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
