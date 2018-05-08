---
title: データ型のトラブルシューティング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
ms.openlocfilehash: c5ff9d097c0660956a9751a23511d8273766227c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-data-types-visual-basic"></a>データ型のトラブルシューティング (Visual Basic)
このページには、組み込みのデータ型に対する操作を実行するときに発生する可能性がある一般的な問題が一覧表示されます。  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a>浮動小数点式が等しいかどうかと比較されません。  
 浮動小数点数を操作する際に ([Single データ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)と[Double データ型](../../../../visual-basic/language-reference/data-types/double-data-type.md))、バイナリの分数として格納されることに注意してください。 つまり、バイナリの分数ではない任意の数量の正確な表現を保持することはできません (k 形式の/(2 ^ n)、k と n は整数)。 たとえば、0.5 (= 1/2) と 0.3125 (= 5/16) 保持できる正確な値は、近似値のみであることができます (= 1/5) 0.2、0.3 (= 3/10)。  
  
 このため、不正確さに依存できない正確な結果浮動小数点値を操作するときにします。 具体的には、理論的に等しい 2 つの値には、若干異なる表現があります。  
  
| 浮動小数点の値を比較するには | 
|---| 
|1.使用して、差の絶対値を計算、<xref:System.Math.Abs%2A>のメソッド、<xref:System.Math>クラス内で、<xref:System>名前空間。<br />2.2 つの数量と等しくなります扱いの違いが大きい場合は不要にすることもできます、許容される最大の違いを決めます。<br />3.許容される相違点に差の絶対値を比較します。|  
  
 次の例では、2 つの正しくないと、正しい比較`Double`値。  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 前の例では、<xref:System.Double.ToString%2A>のメソッド、<xref:System.Double>より精度の高いを指定できるように構造体、`CStr`キーワードを使用します。 既定値は、15 桁の数字が、"G17"書式が 17 桁に拡張します。  
  
## <a name="mod-operator-does-not-return-accurate-result"></a>Mod 演算子には、正確な結果は返しません。  
 浮動小数点の記憶域の不正確さのため、 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)が浮動小数点型には、少なくとも 1 つのオペランドのときに、予期しない結果を返すことができます。  
  
 [Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)浮動小数点表現を使用しません。 正確である数値`Single`と`Double`で正確では`Decimal`(0.2、0.3 など)。 演算で低速`Decimal`よりで浮動小数点、価値があるかもしれません正確性が向上を実現するために、パフォーマンスが低下します。  
  
|浮動小数点数の整数の剰余を検索するには|  
|---|  
|1.として変数を宣言`Decimal`です。<br />2.リテラルの型文字を使用して`D`にリテラルを強制的に`Decimal`場合に、その値が大きすぎて、`Long`データ型。|  
  
 次の例では、浮動小数点のオペランドの不正確さの可能性を示します。  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 前の例では、<xref:System.Double.ToString%2A>のメソッド、<xref:System.Double>より精度の高いを指定できるように構造体、`CStr`キーワードを使用します。 既定値は、15 桁の数字が、"G17"書式が 17 桁に拡張します。  
  
 `zeroPointTwo`は`Double`0.2 用の値は、無限に繰り返されるバイナリ分数 0.20000000000000001 として格納されている値でします。 この数量除算 2.0 には、0.19999999999999991 となりますの残りの部分と 9.9999999999999995 が生成されます。  
  
 式で`decimalRemainder`、リテラルの型文字`D`強制的にオペランドは両方とも`Decimal`は正確に表現します。 したがって、`Mod`演算子は 0.0 の予想される残りの部分を生成します。  
  
 なっていないことを宣言するだけで十分に注意してください`decimalRemainder`として`Decimal`です。 リテラルを強制することも必要があります。 `Decimal`、または使用している`Double`既定と`decimalRemainder`として同じ不正確な値を受け取る`doubleRemainder`です。  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a>ブール型で正確な数値型に変換されません。  
 [Boolean データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)値は、数値として格納されず、格納された値が数値に相当するものではありません。 以前のバージョンと互換性のため、Visual Basic では変換キーワード ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)、 `CBool`、`CInt`など) の間で変換する`Boolean`と数値型。 ただし、他の言語も実行これらの変換と同様に、異なる、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メソッドです。  
  
 数値と等価の値に依存するコードを記述する必要がありますしない`True`と`False`です。 使用を制限する必要があります、可能な限り`Boolean`仕様で定められている論理値変数。 組み合わせる必要がある場合`Boolean`し、数値を選択した変換方法を理解することを確認します。  
  
### <a name="conversion-in-visual-basic"></a>Visual Basic での変換  
 使用すると、`CType`または`CBool`数値データ型に変換する変換キーワード`Boolean`、0 になります`False`になり、その他のすべての値`True`です。 変換する際に`Boolean`値を変換のキーワードを使用して、数値型に`False`が 0 になると`True`-1 になります。  
  
### <a name="conversion-in-the-framework"></a>フレームワークでの変換  
 <xref:System.Convert.ToInt32%2A>のメソッド、<xref:System.Convert>クラス内で、<xref:System>名前空間に変換します`True`+1 にします。  
  
 変換する必要があります場合、`Boolean`値、数値データ型を注意を使用する変換メソッド。  
  
## <a name="character-literal-generates-compiler-error"></a>文字リテラルには、コンパイラ エラーが生成されます。  
 任意の型文字がない場合は、Visual Basic では既定リテラルのデータ型します。 文字リテラルの既定の型: 引用符で囲む (`" "`) — は`String`します。  
  
 `String`データ型に拡大変換されない、 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)です。 つまり、リテラルを代入する場合、`Char`変数、する必要がありますか、縮小変換または強制的にリテラル、`Char`型です。  

|Char 型の変数または定数に割り当てるリテラルを作成するには|
|---|  
|1.変数または定数として宣言`Char`です。<br />2.文字の値を引用符で囲みます (`" "`)。<br />3.次のリテラルの型文字と終わりの二重引用符`C`にリテラルを強制的に`Char`です。 これは型チェック スイッチの場合必要 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`、いずれの場合も必要があるとします。|  
  
 次の例は、リテラルを成功、失敗の割り当て、`Char`変数。  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 常にリスクが縮小変換を使用して実行時にそれらが失敗する可能性です。 変換など、`String`に`Char`失敗する場合、`String`値には、1 つ以上の文字が含まれています。 そのため、これはよりプログラミングを使用する、`C`文字を入力します。  
  
## <a name="string-conversion-fails-at-run-time"></a>実行時に文字列変換に失敗します。  
 [文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)拡大変換がごくわずかに関与します。 `String` 自体にのみ拡大変換と`Object`、のみと`Char`と`Char()`(、`Char`配列) に拡大変換`String`です。 これは、ため`String`変数および定数が他のデータ型を含めることはできませんの値を含めることができます。  
  
 ときに、型チェック スイッチの ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`On`コンパイラには、すべての暗黙的な縮小変換が許可されていません。 関連するものが含まれます`String`です。 コードも使える変換キーワードなど`CStr`と[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)、どのダイレクト、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]変換を試みます。  
  
> [!NOTE]
>  内の要素からの変換の縮小変換エラーは出力されず、`For Each…Next`ループ コントロール変数のコレクション。 詳細と例については、「縮小変換」セクションを参照して[ごとにしています.次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。  
  
### <a name="narrowing-conversion-protection"></a>縮小変換の保護  
 縮小変換の欠点は、実行時に失敗することです。 たとえば場合、`String`変数が含まれるもの"True"または"False"に変換できない場合を除いて`Boolean`です。 区切り文字が含まれている場合は、任意の数値型への変換が失敗します。 わかっている場合を除き、`String`変数は、常に、変換先の型で許容される値を保持、実行、変換しないでください。  
  
 変換する必要がある場合`String`最も安全なプロシージャが実行しようとした変換を囲むを別のデータ型、[を再試行してください.キャッチしてください.Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)です。 これにより、実行時エラーに対処できます。  
  
### <a name="character-arrays"></a>文字配列  
 1 つ`Char`と配列の`Char`に拡大変換する両方の要素`String`です。 ただし、`String`に拡大変換されない`Char()`です。 変換する、`String`値を`Char`使用することができます、配列、<xref:System.String.ToCharArray%2A>のメソッド、<xref:System.String?displayProperty=nameWithType>クラスです。  
  
### <a name="meaningless-values"></a>意味のない値  
 一般に、`String`値は他のデータ型で意味がないので、変換は危険なです。 使用を制限する必要があります、可能な限り`String`仕様で定められている文字のシーケンスの変数です。 その他の型と同じ値に依存するコードを記述する必要があることはありません。  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [データ型の有効な使用方法](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
