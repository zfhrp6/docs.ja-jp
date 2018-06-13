---
title: 文字型 (Char) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: e672402535215ca30d19cc480e39b42b0364f137
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590816"
---
# <a name="char-data-type-visual-basic"></a>文字型 (Char) (Visual Basic)
0 から 65535 まで符号なし 16 ビット (2 バイト) コード ポイントを保持します。 各*コード ポイントが*、または文字コードを 1 つの Unicode 文字を表します。  
  
## <a name="remarks"></a>コメント  
 使用して、`Char`データ型の 1 つのみを保持するために必要なときのオーバーヘッドが不要および文字`String`です。 使用することができる場合によっては`Char()`、配列の`Char`要素、複数の文字を保持するためにします。  
  
 既定値の`Char`が 0 のコード ポイントを使用して文字です。  
  
## <a name="unicode-characters"></a>Unicode 文字  
 Unicode の最初の 128 個のコード ポイント (0 ~ 127) は、文字および記号の標準的な US キーボード上に対応します。 これらの最初の 128 個のコード ポイントと同じ、ASCII 文字セットを定義します。 2 番目の 128 個のコード ポイント (128 ~ 255) では、ラテン語系のアルファベット文字、アクセント記号、通貨記号、および分数などの特殊文字を表します。 Unicode は、さまざまな記号、世界中のテキスト文字、分音文字、数学と技術的な記号などの他のコード ポイント (256 ~ 65535) を使用します。  
  
 などのメソッドを使用する<xref:System.Char.IsDigit%2A>と<xref:System.Char.IsPunctuation%2A>上、`Char`の Unicode の分類を決定する変数。  
  
## <a name="type-conversions"></a>型変換  
 Visual Basic では間で直接変換されません`Char`と数値の型。 使用することができます、<xref:Microsoft.VisualBasic.Strings.Asc%2A>または<xref:Microsoft.VisualBasic.Strings.AscW%2A>に変換する関数、`Char`値を`Integer`コード ポイントを表すです。 使用することができます、<xref:Microsoft.VisualBasic.Strings.Chr%2A>または<xref:Microsoft.VisualBasic.Strings.ChrW%2A>に変換する関数、`Integer`値を`Char`そのコード ポイントを保持します。  
  
 型チェック スイッチの場合 ([Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)) は、リテラルとして識別するために 1 文字の文字列にリテラルの型文字を追加する必要があります、`Char`データ型。 次に例を示します。  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **負の数。** `Char` 符号なしの型は、負の値を表すことはできません。 いずれの場合は、使用しないで`Char`数値の値を保持します。  
  
-   **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントを使用する場合、他の環境では文字型の別のデータ幅 (8 ビット) ことに注意してください。 このようなコンポーネントを 8 ビットの引数を渡す場合として宣言`Byte`の代わりに`Char`新しい Visual Basic コードでします。  
  
-   **拡大します。** `Char`拡大変換後のデータ型`String`です。 つまり、変換することができます`Char`に`String`は発生しないと、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。  
  
-   **型宣言文字。** リテラルの型文字を付加する`C`1 文字の文字列にリテラルを強制的に、`Char`データ型。 `Char` 識別子の型文字がありません。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.Char?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [String データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
