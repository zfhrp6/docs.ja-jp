---
title: 文字列型 (String) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 894638bbe50dad2cae1f74a2f7b7fe006f029d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592120"
---
# <a name="string-data-type-visual-basic"></a>文字列型 (String) (Visual Basic)
0 ~ 65535 の値の符号なし 16 ビット (2 バイト) コード ポイントのシーケンスの範囲を保持します。 各*コード ポイントが*、または文字コードを 1 つの Unicode 文字を表します。 文字列は、0 からおよそ 20億を含めることができます (2 ^31) の Unicode 文字。  
  
## <a name="remarks"></a>コメント  
 使用して、`String`の配列の管理オーバーヘッドがなく、複数の文字を格納するデータ型`Char()`、配列の`Char`要素。  
  
 既定値の`String`は`Nothing`(null 参照)。 これはいない空の文字列と同じ (値`""`)。  
  
## <a name="unicode-characters"></a>Unicode 文字  
 Unicode の最初の 128 個のコード ポイント (0 ~ 127) は、文字および記号の標準的な US キーボード上に対応します。 これらの最初の 128 個のコード ポイントと同じ、ASCII 文字セットを定義します。 2 番目の 128 個のコード ポイント (128 ~ 255) では、ラテン語系のアルファベット文字、アクセント記号、通貨記号、および分数などの特殊文字を表します。 Unicode は、さまざまなシンボルを他のコード ポイント (256 ~ 65535) を使用します。 これには、世界中のテキスト文字、分音文字、および数学と技術的な記号が含まれます。  
  
 などのメソッドを使用することができます<xref:System.Char.IsDigit%2A>と<xref:System.Char.IsPunctuation%2A>で個々 の文字で、`String`の Unicode の分類を決定する変数。  
  
## <a name="format-requirements"></a>書式の要件  
 囲む必要があります、`String`引用符で囲まれたリテラル (`" "`)。 2 つの連続する引用符を使用する場合は、文字列内の文字の 1 つとして、引用符を含める必要があります、(`""`)。 次に例を示します。  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 表す文字列の引用符、二重引用符は作業を開始および終了すると、引用符に依存しないことに注意してください、`String`リテラルです。  
  
## <a name="string-manipulations"></a>文字列操作  
 文字列を代入すると、`String`変数、その文字列は*不変*長さや内容を変更することができることはできません。 任意の方法で文字列を変更するときに、Visual Basic は新しい文字列を作成し、前の 1 つを破棄します。 `String`変数は、新しい文字列を指します。  
  
 内容を操作することができます、`String`さまざまな文字列関数を使用して変数。 次の例を示しています、<xref:Microsoft.VisualBasic.Strings.Left%2A>関数  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 別のコンポーネントによって作成される文字列は、先頭または末尾の空白が埋め込まれている可能性があります。 このような文字列を受信する場合を使用できます、 <xref:Microsoft.VisualBasic.Strings.Trim%2A>、 <xref:Microsoft.VisualBasic.Strings.LTrim%2A>、および<xref:Microsoft.VisualBasic.Strings.RTrim%2A>をこれらのスペースを削除する関数。  
  
 文字列操作の詳細については、次を参照してください。[文字列](../../../visual-basic/programming-guide/language-features/strings/index.md)です。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **負の数。** 文字が保持していることに注意してください`String`署名されていないと、負の値を表すことはできません。 いずれの場合は、使用しないで`String`数値の値を保持します。  
  
-   **相互運用の考慮事項。** オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合、他の環境では文字列の文字の別のデータ幅 (8 ビット) ことに注意してください。 このようなコンポーネントを 8 ビット文字の文字列引数を渡す場合として宣言`Byte()`、配列の`Byte`要素の代わりに`String`新しい Visual Basic コードでします。  
  
-   **型宣言文字。** 識別子の型文字を付加`$`任意の識別子を強制的に、`String`データ型。 `String` リテラルの型文字がありません。 ただし、コンパイラに引用符で囲まれたリテラル (`" "`) として`String`です。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.String?displayProperty=nameWithType>クラスです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.String?displayProperty=nameWithType>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Char データ型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
