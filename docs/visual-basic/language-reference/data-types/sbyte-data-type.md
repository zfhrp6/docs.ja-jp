---
title: "SByte 型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bcd00665ec5b8651089811a61212bfa302fe95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-data-type-visual-basic"></a>SByte データ型 (Visual Basic)

符号付き 8 ビット (1 バイト) 整数-128 から 127 までさまざまです。  
  
## <a name="remarks"></a>コメント

使用して、`SByte`データ型の完全なデータの幅を必要としない整数値を含む`Integer`のデータの半分の幅も`Short`します。 場合によっては、共通言語ランタイムがパックすることがあります、`SByte`変数密接に関連しておよびメモリの消費量を保存します。

`SByte` の既定値は 0 です。

## <a name="literal-assignments"></a>リテラルの割り当て
  
宣言して初期化することができます、`SByte`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。

次の例では、整数と等しい 16 進数、10 進数として表される-102 およびに割り当てられているバイナリ リテラル`SByte`値。 この例では、使用してコンパイルする必要があります、`/removeintchecks`コンパイラ スイッチ。

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

整数リテラルが `SByte` の範囲外にある場合 (つまり、<xref:System.SByte.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.SByte.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。 整数リテラルには、サフィックスがあるない場合に、[整数](integer-data-type.md)推論されます。 整数リテラルは、範囲の場合、`Integer`型、[長い](long-data-type.md)推論されます。 つまり、前の例では、数値リテラルで`0x9A`と`0b10011010`が 32 ビット符号付き整数を超える 156 の値として解釈される<xref:System.SByte.MaxValue?displayProperty=nameWithType>です。 正常にコンパイルする 10 進数以外の整数を代入するこのようなコードを`SByte`次のいずれかを行うことができます。

- コンパイルすると整数の範囲チェックを無効にする、`/removeintchecks`コンパイラ スイッチ。

- 使用して、[文字入力](../../programming-guide\language-features\data-types/type-characters.md)に割り当てるリテラルの値を明示的に定義する、`SByte`です。 次の例では、負の値のリテラル`Short`値を`SByte`です。 なお、負の値、数値リテラルの上位ワードの上位ビットを設定する必要があります。 このビットの場合はこの例では、リテラルの 15`Short`値。

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a>プログラミングのヒント
  
-   **CLS 準拠しています。** `SByte`データ型がの一部、[共通言語仕様](http://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)、CLS 準拠コードがそれを使用するコンポーネントを使用できないようにします。

-   **拡大します。** `SByte`拡大変換後のデータ型`Short`、 `Integer`、 `Long`、 `Decimal`、 `Single`、および`Double`です。 つまり、変換することができます`SByte`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。
  
-   **型宣言文字。** `SByte`リテラルの型文字または識別子の型文字がありません。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.SByte?displayProperty=nameWithType> 構造体です。
  
## <a name="see-also"></a>関連項目

 <xref:System.SByte?displayProperty=nameWithType>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
