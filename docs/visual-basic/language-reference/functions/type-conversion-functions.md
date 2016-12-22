---
title: "Type Conversion Functions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.CUShort"
  - "vb.csng"
  - "vb.CDate"
  - "CByte"
  - "CSng"
  - "vb.CDec"
  - "CBool"
  - "CStr"
  - "vb.CULng"
  - "CDec"
  - "CVErr"
  - "CDbl"
  - "CShort"
  - "vb.CObj"
  - "vb.CVErr"
  - "CULng"
  - "vb.cdbl"
  - "vb.cbool"
  - "CObj"
  - "CDate"
  - "CLng"
  - "vb.cstr"
  - "vb.cbyte"
  - "vb.clng"
  - "vb.CChar"
  - "CUShort"
  - "vb.CUInt"
  - "vb.cint"
  - "vb.CShort"
  - "CInt"
  - "CUInt"
  - "CChar"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "CDate function"
  - "CByte function"
  - "Integer data type, converting"
  - "string conversion, conversion functions"
  - "fractions"
  - "data types [Visual Basic], converting"
  - "text, converting"
  - "CDec function"
  - "Char data type, converting"
  - "type conversion, functions for"
  - "Single data type, converting"
  - "numbers, rounding"
  - "rounding numbers, type conversion"
  - "CUShort function"
  - "Long data type, converting"
  - "return values, data types"
  - "single-precision numbers, converting"
  - "data type conversion, functions for"
  - "CStr function"
  - "times, converting"
  - "CSng function"
  - "conversions, type conversion functions"
  - "CBool function"
  - "CDbl function"
  - "CUInt function"
  - "Currency data type, conversion functions"
  - "numbers, converting"
  - "Double data type, converting"
  - "CLng function"
  - "CSByte function"
  - "double-precision numbers"
  - "Decimal data type, converting"
  - "Boolean data type, converting"
  - "integers, type conversion functions"
  - "dates, converting"
  - "CULng function"
  - "CInt function"
  - "Date data type, converting"
  - "Byte data type, converting"
  - "String data type, converting"
  - "CChar function"
  - "banker's rounding"
  - "Short data type, converting"
  - "rounding numbers, banker's rounding"
  - "type conversion, Visual Basic vs. .NET Framework"
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type Conversion Functions (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

データ型変換関数は、インラインでコンパイルされます。つまり、変換コードは、式を評価するコードに含まれます。  変換を実行するためにプロシージャへの呼び出しを行わないようにすると、パフォーマンスが向上することがあります。  各関数は式を特定のデータ型に変換します。  
  
## 構文  
  
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
  
## 指定項目  
 `expression`  
 必ず指定します。  変換前のデータ型の任意の式です。  
  
## 戻り値のデータ型  
 返される値のデータ型は、次に示すように、関数名によって異なります。  
  
|関数名|戻り値の型|引数 `expression` の範囲|  
|---------|-----------|-------------------------|  
|`CBool`|[Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任意の有効な `Char`、`String`、または数式。|  
|`CByte`|[Byte Data Type](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 から 255 \(符号なし\)。小数部分は丸められます<sup>1</sup>。|  
|`CChar`|[Char Data Type](../../../visual-basic/language-reference/data-types/char-data-type.md)|任意の有効な `Char` または `String` 式。`String` の最初の文字だけが変換されます。値は 0 から 65535 \(符号なし\)。|  
|`CDate`|[Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md)|任意の有効な日付と時刻の表現。|  
|`CDbl`|[Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md)|\-1.79769313486231570E\+308 ～ \-4.94065645841246544E\-324 \(負の値\)。4.94065645841246544E\-324 ～ 1.79769313486231570E\+308 \(正の値\)。|  
|`CDec`|[Decimal Data Type](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|小数点以下が 0 桁 \(小数部分を持たない数値\) の場合、\-79,228,162,514,264,337,593,543,950,335 ～ 79,228,162,514,264,337,593,543,950,335。  小数点以下 28 桁の数値の場合、 \-7.9228162514264337593543950335 ～ 7.9228162514264337593543950335。  絶対値の最小値は 0 を除いた場合、0.0000000000000000000000000001 \(\+\/\-1E\-28\) です。|  
|`CInt`|[Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)|\-2,147,483,648 から 2,147,483,647。小数部分は丸められます<sup>1</sup>。|  
|`CLng`|[Long Data Type](../../../visual-basic/language-reference/data-types/long-data-type.md)|\-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807。小数部分は丸められます<sup>1</sup>。|  
|`CObj`|[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)|任意の有効な式。|  
|`CSByte`|[SByte Data Type](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|\-128 から 127。小数部分は丸められます<sup>1</sup>。|  
|`CShort`|[Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)|\-32,768 から 32,767。小数部分は丸められます<sup>1</sup>。|  
|`CSng`|[Single Data Type](../../../visual-basic/language-reference/data-types/single-data-type.md)|\-3.402823E\+38 ～ \-1.401298E\-45 \(負の値\)。1.401298E\-45 ～ 3.402823E\+38 \(正の値\)。|  
|`CStr`|[String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)|`CStr` 関数の戻り値は引数 `expression` により異なります。  [Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md) を参照してください。|  
|`CUInt`|[UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|0 から 4,294,967,295 \(符号なし\)。小数部分は丸められます<sup>1</sup>。|  
|`CULng`|[ULong Data Type](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|0 から 18,446,744,073,709,551,615 \(符号なし\)。小数部分は丸められます<sup>1</sup>。|  
|`CUShort`|[UShort Data Type](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|0 から 65,535 \(符号なし\)。小数部分は丸められます<sup>1</sup>。|  
  
 <sup>1</sup> 小数部分は、*銀行型丸め*と呼ばれる特別な丸めの対象になります。  詳細については、「解説」を参照してください。  
  
## 解説  
 規則として、Visual Basic の型変換関数は、<xref:System.Convert> クラスと個々の型構造体またはクラスの両方で `ToString()` などの .NET Framework メソッドよりも優先して使用します。  Visual Basic 関数は、Visual Basic コードへの対応に最適化されており、ソース コードをより短く、より読みやすくします。  さらに、`Boolean` を `Integer` に変換する場合など、.NET Framework の変換メソッドは Visual Basic 関数と同じ結果を生成するとは限りません。  詳細については、「[Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。  
  
## \[動作\]  
  
-   **強制型変換。**一般に、ある操作結果を既定のデータ型ではなく特定のデータ型に強制的に変換する場合は、データ型変換関数を使用します。  たとえば、単精度、倍精度、または整数で計算を行うような場合に、`CDec` 関数を使用して 10 進の演算を強制的に行います。  
  
-   **変換の失敗。**関数に渡された引数 `expression` の値が変換されるデータ型の範囲を超えている場合、<xref:System.OverflowException> が発生します。  
  
-   **小数部分。**非整数型の値を整数型に変換する場合、整数変換関数 \(`CByte`、`CInt`、`CLng`、`CSByte`、`CShort`、`CUInt`、`CULng`、`CUShort`\) は、最も近い整数に値を丸めて小数部分を取り除きます。  
  
     小数部分がちょうど 0.5 のとき、整数変換関数はこれを最も近い偶数に丸めます。  たとえば、0.5 は 0 に、1.5 と 2.5 はどちらも 2 になります。  これは*銀行型丸め*とも呼ばれ、このような数値を大量に加算するときに蓄積する偏りを調整する目的で使用されます。  
  
     <xref:Microsoft.VisualBasic.Conversion.Int%2A> および <xref:Microsoft.VisualBasic.Conversion.Fix%2A> 関数は小数部分を丸めるのではなく切り捨てるので、`CInt` および `CLng` とは異なります。  また、`Fix` 関数および `Int` 関数は引き渡された値と同じデータ型で常に値を返します。  
  
-   **日付\/時刻の変換。**値を日付と時刻に変換できるかどうかを確認するには、<xref:Microsoft.VisualBasic.Information.IsDate%2A> 関数を使用します。  `CDate` は日付リテラルと時刻リテラルを認識しますが、数値は認識しません。  Visual Basic 6.0 の `Date` 値を Visual Basic 2005 以降のバージョンの  `Date` 値に変換するには、<xref:System.DateTime.FromOADate%2A?displayProperty=fullName> メソッドを使用します。  
  
-   **日付\/時刻の基準値。** [Date Data Type](../../../visual-basic/language-reference/data-types/date-data-type.md) には、常に日付と時刻の両方の情報が含まれます。  型変換のために、Visual Basic は 1\/1\/0001 \(西暦 1 年 1 月 1 日\) を日付の基準値と見なし、00:00:00 \(午前 0 時\) を時刻の*基準値*と見なします。  日付型 \(`Date`\) の値を文字列に変換する場合、`CStr` は結果の文字列に基準値を含めません。  たとえば、`#January 1, 0001 9:30:00#` を文字列に変換すると、結果は "9:30:00 AM" となり、日付情報が省略されます。  ただし、元の日付型 \(`Date`\) の値には日付情報が残っており、<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> などの関数を使って復元できます。  
  
-   **カルチャの区別。**文字列を扱う型変換関数は、アプリケーションの現在のカルチャ設定に基づいて変換を実行します。  たとえば、`CDate` は、システムのロケール情報に基づいて日付の形式を認識します。  日、月、および年は、ロケールに対応した正しい順序で指定する必要があります。そうしないと、日付が正しく解釈されない場合があります。  日付の形式が、曜日文字列 \("Wednesday" など\) を含む長い形式の場合も認識できません。  
  
     ロケールで指定されているもの以外の書式の、値の文字列形式を扱った変換では、Visual Basic の型変換関数は使用できません。  この変換では、その値の型の `ToString(IFormatProvider)` および `Parse(String, IFormatProvider)` メソッドを使用します。  たとえば、文字列を `Double` に変換するには <xref:System.Double.Parse%2A?displayProperty=fullName> を使用します。`Double` 型の値を文字列に変換するには <xref:System.Double.ToString%2A?displayProperty=fullName> を使用します。  
  
## CType 関数  
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md) は、2 番目の引数として `typename` を取り、`expression` を強制的に `typename` に変換します \(`typename` は、有効な変換が可能な任意のデータ型、構造体、クラス、インターフェイス\)。  
  
 `CType` とその他の型変換キーワードとの比較については、「[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md)」および「[TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md)」を参照してください。  
  
## CBool の例  
 `CBool` 関数を使って式をブール型 \(`Boolean`\) の値に変換する例を次に示します。  式が 0 でない値のときは、`CBool` 関数は `True` を返します。それ以外は `False` を返します。  
  
 [!CODE [VbVbalrFunctions#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#1)]  
  
## CByte の例  
 `CByte` 関数を使って式を \(`Byte`\) に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#2](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#2)]  
  
## CChar の例  
 `CChar` 関数を使って、文字列型 \(`String`\) の式の最初の文字を char 型 \(`Char`\) に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#3](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#3)]  
  
 `CChar` の入力引数は `Char` または `String` データ型である必要があります。  `CChar` には数値データ型を入力できないため、`CChar` を使って数値を文字に変換することはできません。  次の例では、コード ポイント \(文字コード\) を表す数値を取得し、それを対応する文字に変換します。  ここでは、<xref:Microsoft.VisualBasic.Interaction.InputBox%2A> 関数を使って数字の文字列を取得し、`CInt` を使って文字列を整数型 \(`Integer`\) に変換し、`ChrW` を使ってその数値を `Char` に変換しています。  
  
 [!CODE [VbVbalrFunctions#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#4)]  
  
## CDate の例  
 `CDate` 関数を使って文字列を日付型 \(`Date`\) の値に変換する例を次に示します。  一般的には、この例のように文字列で日付\/時刻を表すことはお勧めできません。  文字列の代わりに、日付リテラルや時刻リテラル \(\#Feb 12, 1969\# や \#4:45:23 PM\# など\) を使ってください。  
  
 [!CODE [VbVbalrFunctions#5](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#5)]  
  
## CDbl の例  
 [!CODE [VbVbalrFunctions#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#6)]  
  
## CDec の例  
 `CDec` 関数を使って数値を `Decimal` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#7](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#7)]  
  
## CInt の例  
 `CInt` 関数を使って値を `Integer` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#8](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#8)]  
  
## CLng の例  
 `CLng` 関数を使って値を `Long` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#9](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#9)]  
  
## CObj の例  
 `CObj` 関数を使って数値を `Object` に変換する例を次に示します。  オブジェクト型 \(`Object`\) の変数自体には、4 バイトのポインターだけが含まれます。このポインターは、変数に代入された倍精度浮動小数点数型 \(`Double`\) の値を指しています。  
  
 [!CODE [VbVbalrFunctions#10](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#10)]  
  
## CSByte の例  
 `CSByte` 関数を使って数値を `SByte` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#11](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#11)]  
  
## CShort の例  
 `CShort` 関数を使って数値を `Short` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#12](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#12)]  
  
## CSng の例  
 `CSng` 関数を使って値を `Single` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#13](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#13)]  
  
## CStr の例  
 `CStr` 関数を使って数値を `String` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#14](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#14)]  
  
 `CStr` 関数を使って `Date` の値を `String` の値に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#15](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#15)]  
  
 `CStr` は常に、現在のロケールに対する標準の短い形式 \("6\/15\/2003 4:35:47 PM " など\) で日付型 \(`Date`\) の値を表示します。  しかし、`CStr` は 1\/1\/0001 \(日付\) および 00:00:00 \(時刻\) の*基準値*を表示しません。  
  
 `CStr` が返す値の詳細については、「[Return Values for the CStr Function](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md)」を参照してください。  
  
## CUInt の例  
 `CUInt` 関数を使って数値を `UInteger` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#16](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#16)]  
  
## CULng の例  
 `CULng` 関数を使って数値を `ULong` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#17](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#17)]  
  
## CUShort の例  
 `CUShort` 関数を使って数値を `UShort` に変換する例を次に示します。  
  
 [!CODE [VbVbalrFunctions#18](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrFunctions#18)]  
  
## 参照  
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
 [Conversion Functions](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)