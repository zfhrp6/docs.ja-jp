---
title: "データ型 (Visual Basic) のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
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
- Char data type, converting
- Decimal data type, conversions
- data types [Visual Basic], troubleshooting
- literals, default types
- type characters, literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types
- floating-point numbers, precision
- Boolean data type, converting
- literal types
- literal type characters
- floating-point numbers, imprecision
- String data type, converting
- floating-point numbers, comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: 29
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
ms.openlocfilehash: cfb8fc77d3e0d85ef795a94fc95ab61a8f68ff39
ms.lasthandoff: 03/13/2017

---
# <a name="troubleshooting-data-types-visual-basic"></a>データ型のトラブルシューティング (Visual Basic)
ここでは、組み込みデータ型の操作を実行するときに発生する一般的な問題について説明します。  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>浮動小数点式が等しいと評価比較されません。  
 浮動小数点数を扱うとき ([Single データ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)と[Double データ型](../../../../visual-basic/language-reference/data-types/double-data-type.md))、バイナリの分数として格納されることに注意してください。 つまりがない場合、2 進数の正確な表現を保持することはできません (k 形式の/(2 ^ n)、k と n は整数)。 たとえば、0.5 (= 1/2) や 0.3125 (= 5/16) 保持できる正確な値を (= 1/5) 0.2 と 0.3 (3/10 =) 近似値のみであることができます。  
  
 このため、誤差に依存できない正確な結果浮動小数点値を操作するときにします。 具体的には、理論上は同じである&2; つの値には、若干異なる表現があります。  
  
| 浮動小数点の値を比較するには | 
|---| 
|1.使用して差の絶対値を計算、<xref:System.Math.Abs%2A>のメソッド、<xref:System.Math>クラス、<xref:System>名前空間</xref:System></xref:System.Math></xref:System.Math.Abs%2A>。<br />2.許容される最大の誤差を決めますが等しい場合の実用的な目的の場合はその違いは、サイズは、2 つの数を検討することができます。<br />3.許容可能な差までの差の絶対値を比較します。|  
  
 次の例では、2 つの正しくないと、正しい比較`Double`値。  
  
 [!code-vb[VbVbalrDataTypes&#10;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 前の例を使用して、<xref:System.Double.ToString%2A>のメソッド、<xref:System.Double>より精度の高いことを指定できるように構造化、`CStr`キーワードを使用しています</xref:System.Double></xref:System.Double.ToString%2A>。 既定値は 15 桁が、"G17"書式が 17 桁に拡張します。  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod 演算子は正確な結果を返しません。  
 浮動小数点数のストレージでの誤差のため、 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)が浮動小数点型のオペランドの少なくとも&1; つと、予期しない結果を返すことができます。  
  
 [Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)浮動小数点表現を使用しません。 正確で数`Single`と`Double`で正確では`Decimal`(0.2 と 0.3 など)。 演算で低速`Decimal`よりもに、浮動小数点とよいでしょう、パフォーマンスを低下させるための正確性が向上します。  
  
|浮動小数点数の整数の剰余を検索するには|  
|---|  
|1.として変数を宣言`Decimal`します。<br />2.リテラルの型文字を使用して`D`にリテラルを強制的に`Decimal`、その値が大きすぎる場合に、`Long`データ型。|  
  
 次の例では、浮動小数点のオペランドの誤差の可能性を示します。  
  
 [!code-vb[VbVbalrDataTypes&#11;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 前の例を使用して、<xref:System.Double.ToString%2A>のメソッド、<xref:System.Double>より精度の高いことを指定できるように構造化、`CStr`キーワードを使用しています</xref:System.Double></xref:System.Double.ToString%2A>。 既定値は 15 桁が、"G17"書式が 17 桁に拡張します。  
  
 `zeroPointTwo`は`Double`0.2 用の値は 0.20000000000000001 として格納されている値を持つ場合は、無限に繰り返されるバイナリ分数。 この数量 2.0 で除算には、0.19999999999999991 となりますの残りの部分と 9.9999999999999995 が生成されます。  
  
 式で`decimalRemainder`、リテラルの型文字`D`強制的にオペランドは両方とも`Decimal`は正確に表現します。 したがって、`Mod`演算子が 0.0 の予想される残りの部分を生成します。  
  
 宣言するだけで十分ではないことに注意してください`decimalRemainder`として`Decimal`します。 リテラルを強制することも必要があります。 `Decimal`、または使用している`Double`既定では、`decimalRemainder`と同じ不正確な値を受け取る`doubleRemainder`します。  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>ブール型で正確な数値型に変換されません。  
 [ブール型のデータ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)値は、数値として格納されず、格納される値は番号に相当するものでありません。 以前のバージョンとの互換性のため[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]変換キーワードは、([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)、 `CBool`、`CInt`など) 間で変換を`Boolean`と数値型。 ただし、他の言語も変換を実行これらのように、異なる、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]メソッドです。  
  
 数値と等価の値に依存するコードを記述する必要がありますしない`True`と`False`です。 使用を制限する必要があります可能であれば、`Boolean`変数を論理値に設計されています。 組み合わせる必要がある場合`Boolean`し、数値を選択する変換メソッドを理解しておくことを確認します。  
  
### <a name="conversion-in-visual-basic"></a>Visual Basic での変換  
 使用すると、`CType`または`CBool`数値データ型に変換する変換キーワード`Boolean`、0 になります`False`され、その他のすべての値になる`True`します。 変換する際に`Boolean`値を変換キーワードを使用して、数値型に`False`が 0 になると`True`-1 になります。  
  
### <a name="conversion-in-the-framework"></a>フレームワークでの変換  
 <xref:System.Convert.ToInt32%2A>のメソッド、<xref:System.Convert>クラス、<xref:System>名前空間に変換`True`+1 にします</xref:System></xref:System.Convert></xref:System.Convert.ToInt32%2A>。  
  
 変換が必要である場合、`Boolean`値、数値データ型をご注意くださいを使用する変換メソッド。  
  
## <a name="character-literal-generates-compiler-error"></a>文字リテラルには、コンパイラ エラーが生成されます。  
 任意の種類の文字がない場合[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]リテラルのデータ型の既定値を想定しています。 文字リテラルに既定の種類-引用符で囲む (`" "`) — は`String`です。  
  
 `String`にデータ型が変換されない、 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)します。 つまり、リテラルを代入する場合、`Char`変数、する必要がありますか、縮小変換を行うか、リテラルを`Char`型です。  

|Char 型の変数または定数に割り当てるリテラルを作成するには|
|---|  
|1.変数または定数として宣言`Char`します。<br />2.文字の値を引用符で囲みます (`" "`)。<br />3.次のリテラルの型文字と終わりの二重引用符`C`にリテラルを強制的に`Char`します。 これは型チェック スイッチの場合必要 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`とはどのような場合に適切です。|  
  
 次の例は、リテラルを成功、失敗の割り当て、`Char`変数です。  
  
 [!code-vb[VbVbalrDataTypes&#12;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 リスクがある常に縮小変換を使用しているため、実行時に失敗したことができます。 変換など`String`に`Char`失敗する場合、`String`値には、1 つ以上の文字が含まれています。 そのため、それを使用するプログラミングがより、`C`文字を入力します。  
  
## <a name="string-conversion-fails-at-run-time"></a>文字列の変換は実行時に失敗します。  
 [文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)がごくわずかの拡大変換に参加します。 `String`自体にのみ拡大変換と`Object`とのみ`Char`と`Char()`(、`Char`配列) に拡大変換`String`します。 これは、ため`String`変数および定数が他のデータ型を含むことができない値を含めることができます。  
  
 型チェックを切り替える場合 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`コンパイラは、すべての暗黙的な縮小変換を許可しません。 関連するものが含まれます`String`します。 コードもなどを使用変換キーワード`CStr`と[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)、どのダイレクト、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]変換を試みます。  
  
> [!NOTE]
>  内の要素からの変換の縮小変換エラーは出力されず、`For Each…Next`ループ制御変数のコレクション。 詳細と例については、「縮小変換」セクションを参照して[ごとにしています.次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)です。  
  
### <a name="narrowing-conversion-protection"></a>縮小変換の保護  
 縮小変換の欠点では、それらが実行時に失敗することができます。 たとえば場合、`String`変数が含まれるもの以外の"True"または"False"に変換できない`Boolean`します。 区切り文字を含んでいる場合は、任意の数値型への変換が失敗します。 わかっていない限り、`String`変数変換先の型が受け入れられる値を常に保持する、実行、変換しないでください。  
  
 変換する必要がある場合`String`最も安全なプロシージャが実行しようとした変換を囲むを別のデータ型、[しようとしています.キャッチしてください.Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。 これにより、実行時エラーに対処することができます。  
  
### <a name="character-arrays"></a>文字配列  
 単一の`Char`と配列の`Char`要素の両方に拡大変換する`String`です。 ただし、`String`に拡大変換されない`Char()`します。 変換する、`String`値を`Char`配列、<xref:System.String.ToCharArray%2A><xref:System.String?displayProperty=fullName>クラス</xref:System.String?displayProperty=fullName>のメソッド</xref:System.String.ToCharArray%2A>を使用することができます  
  
### <a name="meaningless-values"></a>意味のない値  
 一般に、`String`値は、他のデータ型で意味がわかりませんし、変換が危険なです。 使用を制限する必要があります可能であれば、`String`変数を文字のシーケンスに設計されています。 その他の種類に対応する値に依存するコードを書かないようにしてください。  
  
## <a name="see-also"></a>関連項目  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [データ型の有効な使用方法](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
