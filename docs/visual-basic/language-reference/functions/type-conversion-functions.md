---
title: データ型変換関数 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: c9222bdb31f4fd7c792d5a50c100067e29e9d537
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605083"
---
# <a name="type-conversion-functions-visual-basic"></a>データ型変換関数 (Visual Basic)
これらの関数は、コンパイルされたインラインで、変換コードは、式を評価するコードの一部を意味します。 場合によってパフォーマンスを向上させると、変換を行うプロシージャへの呼び出しはありません。 各関数は、式を特定のデータ型を変換します。  
  
## <a name="syntax"></a>構文  
  
```  
CBool(expression)  
CByte(expression)  
CChar(expression)  
CDate(expression)  
CDbl(expression)  
CDec(expression)  
CInt(expression)  
CLng(expression)  
CObj(expression)  
CSByte(expression)  
CShort(expression)  
CSng(expression)  
CStr(expression)  
CUInt(expression)  
CULng(expression)  
CUShort(expression)  
```  
  
## <a name="part"></a>パーツ  
 `expression`  
 必須。 ソースのデータ型の任意の式。  
  
## <a name="return-value-data-type"></a>戻り値のデータ型  
 関数名は、次の表に示すように、返されると、値のデータ型を決定します。  
  
|関数名|戻り値のデータ型|範囲`expression`引数|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Boolean データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任意の有効な`Char`または`String`または数値式です。|  
|`CByte`|[Byte データ型](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 ~ 255 (符号なし)。小数部は丸められます。<sup>1</sup>|  
|`CChar`|[Char データ型](../../../visual-basic/language-reference/data-types/char-data-type.md)|任意の有効な`Char`または`String`式以外の最初の文字のみの場合は、`String`に変換されます。 値は 0 ~ 65535 (符号なし) を指定できます。|  
|`CDate`|[Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)|任意の有効な日付と時刻の表現。|  
|`CDbl`|[Double 型](../../../visual-basic/language-reference/data-types/double-data-type.md)|-- を 4.94065645841246544E-(負の値)。4.94065645841246544E-324 正の値の 1.79769313486231570 e + 308 ~ です。|  
|`CDec`|[Decimal データ型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|数値のゼロ拡張 79,228,162,514,264,337,593,543,950,335、+/-小数点以下の桁数番号は、します。 小数点以下桁数が 28 数値の場合は、範囲は、7.9228162514264337593543950335 です。 可能な 0 以外の最小値は、(1 e ~ 28) +/-0.0000000000000000000000000001 です。|  
|`CInt`|[整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md)|-2,147, 483,648 ~ 2,147, 483,647 です。小数部は丸められます。<sup>1</sup>|  
|`CLng`|[Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)|9,223,372,036,854,775,807; を通じて-9,223,372,036,854,775,808小数部は丸められます。<sup>1</sup>|  
|`CObj`|[Object 型](../../../visual-basic/language-reference/data-types/object-data-type.md)|任意の有効な式。|  
|`CSByte`|[SByte データ型](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|-128 ~ 127 です。小数部は丸められます。<sup>1</sup>|  
|`CShort`|[Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)|-32,768 ~ 32,767 です。小数部は丸められます。<sup>1</sup>|  
|`CSng`|[Single データ型](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823 e + 38 ~ - 1.401298E-45 負の値です。1.401298E-45 正の値の 3.402823 e + 38 ~ です。|  
|`CStr`|[String データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)|返します`CStr`によって異なります、`expression`引数。 参照してください[CStr 関数の戻り値](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)です。|  
|`CUInt`|[UInteger データ型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|0 ~ 4,294,967,295 (符号なし)。小数部は丸められます。<sup>1</sup>|  
|`CULng`|[ULong データ型](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|0 ~ 18,446,744,073,709,551,615 (符号なし)。小数部は丸められます。<sup>1</sup>|  
|`CUShort`|[UShort データ型](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|0 ~ 65,535 (符号なし)。小数部は丸められます。<sup>1</sup>|  
  
 <sup>1</sup>小数部分は、特殊な丸めと呼ばれるを受けることができます*銀行型丸め*です。 詳細については、「解説」を参照してください。  
  
## <a name="remarks"></a>コメント  
 原則として、する必要があります、Visual Basic 型変換関数を使用、.NET Framework のメソッドよりもなど`ToString()`か、上、<xref:System.Convert>クラスまたは個々 の型の構造体またはクラス。 Visual Basic の関数は最適な Visual Basic コード、対話するために設計されていてもソース コードできるだけ短く、また読みやすくします。 さらに、.NET Framework 変換メソッドは、常に生成しない変換する場合の例については、Visual Basic の関数と同じ結果`Boolean`に`Integer`です。 詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。  
  
## <a name="behavior"></a>動作  
  
-   **強制型変換です。** 一般に、データ型変換関数を使用して、既定のデータ型ではなく、特定のデータ型を操作の結果を強制することができます。 たとえば、使用して`CDec`場合の単精度、倍精度、または整数算術演算は通常を行う場所の 10 進数の演算を強制的にします。  
  
-   **変換の失敗。** 場合、`expression`関数に渡されるが範囲外のデータ型の変換するのには、先に<xref:System.OverflowException>に発生します。  
  
-   **小数部分。** 整数以外の値を整数に変換すると、型、整数の変換関数 (`CByte`、 `CInt`、 `CLng`、 `CSByte`、 `CShort`、 `CUInt`、 `CULng`、および`CUShort`) を削除します小数部分し、を最も近い整数値を丸めます。  
  
     場合は、小数部分が正確には 0.5、整数の変換関数に丸める、近い偶数の整数。 たとえば、0.5 は、0、および 1.5 2.5 は 2 にどちらに切り上げられます。 これとも呼ばれます*銀行型丸めが*、その目的は、このような多くの数値をまとめて追加するときに蓄積する偏りを調整するとします。  
  
     `CInt` `CLng`は異なる、<xref:Microsoft.VisualBasic.Conversion.Int%2A>と<xref:Microsoft.VisualBasic.Conversion.Fix%2A>切り上げるには、数値の小数部ではなく、切り捨て関数。 また、`Fix`と`Int`を渡すと、同じデータ型の値を常に返します。  
  
-   **日付/時刻の変換。** 使用して、<xref:Microsoft.VisualBasic.Information.IsDate%2A>値を日付と時刻に変換できるかどうかを判断する関数。 `CDate` リテラルの日付と時刻リテラルが数値以外の値を認識します。 Visual Basic 6.0 を変換する`Date`値を`Date`Visual Basic 2005 での値またはそれ以降のバージョンでは、使用できます、<xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>メソッドです。  
  
-   **ニュートラル日付/時刻値。** [Date データ型](../../../visual-basic/language-reference/data-types/date-data-type.md)常に日付と時刻の両方の情報が含まれます。 型変換のため、Visual Basic 1/1/0001 (1 年 1 月、1) であると見なす、*ニュートラル値*日付、および 00時 00分: 00 (午前 0 時) に依存しない値であることにします。 変換する場合、`Date`値を文字列に`CStr`結果の文字列に中立的な値は含まれません。 変換する場合など、`#January 1, 0001 9:30:00#`文字列に、結果は"9時 30分: 00 AM"以外の場合は、日付情報は表示されません。 ただし、日付情報は、元にまだ存在している`Date`値し、などの関数で回復できる<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>関数。  
  
-   **カルチャと小文字の区別します。** 文字列に関係するデータ型変換関数は、アプリケーションの現在のカルチャ設定に基づく変換を実行します。 たとえば、`CDate`システムのロケール設定に従って日付形式を認識します。 日、月、および使用されるロケールの正しい順序で年を指定するか、日付が正しく解釈されない可能性があります。 長い日付形式は、「水曜日」などの曜日の文字列が含まれている場合に認識されません。  
  
     または現在のロケールで指定された 1 つは異なる形式で値の文字列形式からに変換する必要がある場合は、Visual Basic の型変換関数を使用することはできません。 これを行うを使用して、`ToString(IFormatProvider)`と`Parse(String, IFormatProvider)`値の型のメソッドです。 たとえば、使用<xref:System.Double.Parse%2A?displayProperty=nameWithType>を文字列に変換するときに、`Double`を使用して<xref:System.Double.ToString%2A?displayProperty=nameWithType>型の値を変換するときに`Double`を文字列にします。  
  
## <a name="ctype-function"></a>CType Function  
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)2 番目の引数を受け取り`typename`、強制`expression`に`typename`ここで、`typename`任意のデータ型、構造体、クラス、または有効な変換が存在するインターフェイスを指定できます。  
  
 比較について`CType`他の型変換のキーワードと、次を参照してください。 [DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)と[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)です。  
  
## <a name="cbool-example"></a>CBool 例  
 次の例では、`CBool`関数を式に変換する`Boolean`値。 0 以外の値に式が評価された場合`CBool`を返します`True`、それ以外を返します`False`です。  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a>CByte 例  
 次の例では、`CByte`関数を式に変換する、`Byte`です。  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a>Cchar 関数の例  
 次の例では、`CChar`関数の最初の文字に変換する、`String`式、`Char`型です。  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 入力引数`CChar`データ型でなければなりません`Char`または`String`です。 使用することはできません`CChar`に変換する数値、文字、ため`CChar`数値データ型を受け入れることはできません。 次の例では、コード ポイント (文字コード) を表す数値を取得し、対応する文字に変換します。 使用して、 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> 、桁の数字の文字列を取得する関数`CInt`を入力文字列に変換する`Integer`、および`ChrW`を入力する数値を変換する`Char`です。  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a>Cdate 関数の例  
 次の例では、`CDate`関数への文字列に変換する`Date`値。 一般に、ハードコーディングされた日付と時刻文字列としてのこの例に示す) は推奨されません。 日付リテラルと #Feb 12、1969 # など、時刻のリテラルを使用し、# 4時 45分: 23 PM #、代わりにします。  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a>CDbl 例  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a>CDec 例  
 次の例では、`CDec`関数を数値に変換する`Decimal`です。  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a>CInt 例  
 次の例では、`CInt`値を変換する関数`Integer`です。  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a>CLng 例  
 次の例では、`CLng`値に変換する関数`Long`です。  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a>CObj 例  
 次の例では、`CObj`関数を数値に変換する`Object`です。 `Object`変数自体を指す 4 バイト ポインターのみが含まれています、`Double`値を割り当てます。  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a>CSByte 例  
 次の例では、`CSByte`関数を数値に変換する`SByte`です。  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a>CShort 例  
 次の例では、`CShort`関数を数値に変換する`Short`です。  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a>CSng 例  
 次の例では、`CSng`値に変換する関数`Single`です。  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a>Cstr 関数の例  
 次の例では、`CStr`関数を数値に変換する`String`です。  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 次の例では、`CStr`関数に変換する`Date`値`String`値。  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 `CStr` 常に表示、`Date`現在のロケールのたとえば、標準の短い形式の値"2003 年 6 月 15/4時 35分: 47 PM"です。 ただし、`CStr`抑制、*ニュートラル値*の日付と時刻の 00時 00分: 00 の 1/1/0001 です。  
  
 によって返される値の詳細については`CStr`を参照してください[CStr 関数の戻り値](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)です。  
  
## <a name="cuint-example"></a>CUInt 例  
 次の例では、`CUInt`関数を数値に変換する`UInteger`です。  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a>CULng 例  
 次の例では、`CULng`関数を数値に変換する`ULong`です。  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a>CUShort 例  
 次の例では、`CUShort`関数を数値に変換する`UShort`です。  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 <xref:Microsoft.VisualBasic.Strings.Format%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [変換関数](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [Visual Basic での型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
