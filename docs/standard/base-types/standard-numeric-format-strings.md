---
title: "標準の数値書式指定文字列"
ms.date: 09/10/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- standard format strings, numeric
- format strings
- numbers [.NET Framework], formatting
- format specifiers, numeric
- standard numeric format strings
- formatting numbers [.NET Framework]
- format specifiers, standard numeric format strings
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 81547bbcdbae5b4cc8dc1f20e829dfb5ede08963
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="standard-numeric-format-strings"></a>標準の数値書式指定文字列
一般的な数値型を書式設定するには、標準の数値書式指定文字列を使用します。 標準の数値書式指定文字列の形式は `Axx` です。  
  
-   `A` は *書式指定子* です。これは 1 文字の英文字です。 空白を含む複数の英文字で構成される数値書式指定文字列は、カスタム数値書式指定文字列として解釈されます。 詳細については、「[カスタム数値書式指定文字列](../../../docs/standard/base-types/custom-numeric-format-strings.md)」をご覧ください。  
  
-   `xx` は *精度指定子* です。これは省略可能な整数値です。 精度指定子は 0 ～ 99 の範囲で指定され、結果の桁数に影響します。 精度指定子は、文字列形式の数値の桁数を制御することに注意してください。 精度指定子では、数値を丸めません。 丸め操作を実行するには、<xref:System.Math.Ceiling%2A?displayProperty=nameWithType>、<xref:System.Math.Floor%2A?displayProperty=nameWithType>、または <xref:System.Math.Round%2A?displayProperty=nameWithType> の各メソッドを使用します。  
  
     ときに*精度指定子*数を制御結果の文字列の小数部桁数は、結果文字列はゼロから離れる方向に丸められる数を反映して (使用して、 <xref:System.MidpointRounding.AwayFromZero?displayProperty=nameWithType>)。  
  
    > [!NOTE]
    >  精度指定子は、結果文字列の桁数を決定します。 結果文字列に先頭または末尾のスペースを埋め込むには、[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)機能を使用して、書式指定項目に *alignment コンポーネント*を定義します。  
  
標準の数値書式指定文字列でサポートされます。

- 一部のオーバー ロード、`ToString`すべての数値型のメソッドです。 たとえば、数値書式指定文字列を指定できます、<xref:System.Int32.ToString%28System.String%29?displayProperty=nameWithType>と<xref:System.Int32.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>メソッドです。 
 
- .NET[複合書式指定機能](../../../docs/standard/base-types/composite-formatting.md)、によって使用される`Write`と`WriteLine`のメソッド、<xref:System.Console>と<xref:System.IO.StreamWriter>、クラス、<xref:System.String.Format%2A?displayProperty=nameWithType>メソッド、および<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>メソッド。 複合書式指定機能により、複数のデータ項目の文字列表現を 1 つの文字列にまとめ、フィールド幅を指定し、フィールドの数値の位置を揃えることができます。 詳細については、「[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)」をご覧ください。  

- [文字列の補間](../../csharp/language-reference/keywords/interpolated-strings.md)c# および Visual Basic の場合でを複合書式指定文字列と比較すると、簡略化された構文を提供します。
 
> [!TIP]
>  [書式指定ユーティリティ](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)をダウンロードできます。このアプリケーションを使用すると、書式指定文字列を数値または日付と時刻の値に適用して、結果の文字列を表示できます。  
  
<a name="table"></a>次の表に、標準数値書式指定子の説明および書式指定子ごとのサンプル出力を示します。 標準の数値書式指定文字列の使用方法については、「[メモ](#NotesStandardFormatting)」をご覧ください。それらを使用する包括的な例については、「[例](#example)」をご覧ください。  
  
|書式指定子|名前|説明|例|  
|----------------------|----------|-----------------|--------------|  
|"C" または "c"|通貨|結果: 通貨値。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: <xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> によって定義されます。<br /><br /> 詳細については、「[通貨 ("C") 書式指定子](#CFormatString)」を参照してください。|123.456 ("C", en-US) -> $123.46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en-US) -> ($123.456)<br /><br /> -123.456 ("C3", fr-FR) -> -123,456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|  
|"D" または "d"|Decimal (10 進数型)|結果: 必要に応じて負の符号が付く整数。<br /><br /> サポート: 整数型のみ。<br /><br /> 精度指定子: 最小桁数。<br /><br /> 既定の精度指定子: 必要な最小桁数。<br /><br /> 詳細については、「[10 進数 ("D") 書式指定子](#DFormatString)」を参照してください。|1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|  
|"E" または "e"|指数|結果: 指数表記。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: 6。<br /><br /> 詳細については、「[指数 ("E") 書式指定子](#EFormatString)」を参照してください。|1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1,052033e+003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr_FR) -> -1,05E+003|  
|"F" または "f"|固定小数点|結果: 必要に応じて負の符号が付く整数と小数。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> によって定義されます。<br /><br /> 詳細については、「[固定小数点 ("F") 書式指定子](#FFormatString)」を参照してください。|1234.567 ("F", en-US) -> 1234.57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en-US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en-US) -> -1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> -1234,5600|  
|"G" または "g"|全般|結果: 固定小数点表記または指数表記のいずれかのより簡潔な形式。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 有効桁数。<br /><br /> 既定の精度指定子: 数値型によって異なります。<br /><br /> 詳細については、「[一般 ("G") 書式指定子](#GFormatString)」を参照してください。|-123.456 ("G", en-US) -> -123.456<br /><br /> -123.456 ("G", sv-SE) -> -123,456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|  
|"N" または "n"|Number|結果: 必要に応じて負の符号が付く整数と小数、桁区切り記号、および小数点記号。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> によって定義されます。<br /><br /> 詳細については、「[数値 ("N") 書式指定子](#NFormatString)」を参照してください。|1234.567 ("N", en-US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en-US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3", en-US) -> -1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> -1 234,560|  
|"P" または "p"|パーセント|結果: 数値に 100 を掛けて、パーセント記号を付けて表示します。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: によって定義された<xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A?displayProperty=nameWithType>です。<br /><br /> 詳細については、「[パーセント ("P") 書式指定子](#PFormatString)」を参照してください。|1 ("P", en-US) -> 100.00 %<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0.39678 ("P1", en-US) -> -39.7 %<br /><br /> -0.39678 ("P1", fr-FR) -> -39,7 %|  
|"R" または "r"|ラウンドトリップ|結果: 同じ数値にラウンドトリップできる文字列。<br /><br /> サポート: <xref:System.Single>、<xref:System.Double>、および <xref:System.Numerics.BigInteger>。<br /><br /> 注: 推奨、<xref:System.Numerics.BigInteger>のみを入力します。 <xref:System.Double>の種類、"G17"を使用して;<xref:System.Single>の種類が"G9"を使用します。 </br> 精度指定子: 無視されます。<br /><br /> 詳細については、「[ラウンドトリップ ("R") 書式指定子](#RFormatString)」を参照してください。|123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|  
|"X" または "x"|16 進数|結果: 16 進数文字列。<br /><br /> サポート: 整数型のみ。<br /><br /> 精度指定子: 結果文字列の桁数。<br /><br /> 詳細については、「[16 進数 ("X") 書式指定子](#XFormatString)」を参照してください。|255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|  
|その他の 1 文字|未定義の指定子|結果: 実行時に <xref:System.FormatException> をスローします。||  
  
<a name="Using"></a>   
## <a name="using-standard-numeric-format-strings"></a>標準の数値書式指定文字列の使用  
 標準の数値書式指定文字列を使用すると、次のいずれかの方法で数値の書式を定義できます。  
  
-   `ToString` パラメーターを持つ `format` メソッドのオーバーロードに渡す。 次の例では、(ここでは、EN-US カルチャ)、現在のカルチャの通貨文字列として数値を書式設定します。  
  
     [!code-cpp[Formatting.Numeric.Standard#10](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#10)]
     [!code-csharp[Formatting.Numeric.Standard#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#10)]
     [!code-vb[Formatting.Numeric.Standard#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#10)]  
  
-   として指定できます、`formatString`などのメソッドで使用される書式指定項目で引数<xref:System.String.Format%2A?displayProperty=nameWithType>、 <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>、および<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>です。 詳細については、「[複合書式指定](../../../docs/standard/base-types/composite-formatting.md)」をご覧ください。 次の例では、書式指定項目を使用して文字列に通貨値を挿入しています。  
  
     [!code-cpp[Formatting.Numeric.Standard#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#11)]
     [!code-csharp[Formatting.Numeric.Standard#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#11)]
     [!code-vb[Formatting.Numeric.Standard#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#11)]  
  
     必要に応じて、指定することができます、`alignment`数値フィールド、およびその値が右揃えまたは左揃えの幅を指定する引数。 次の例では、通貨の値が 28 文字フィールドでは左揃えになっており、14 文字フィールドでは右揃えになっています。  
  
     [!code-cpp[Formatting.Numeric.Standard#12](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/standardusage1.cpp#12)]
     [!code-csharp[Formatting.Numeric.Standard#12](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/standardusage1.cs#12)]
     [!code-vb[Formatting.Numeric.Standard#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/standardusage1.vb#12)]  
  
 以降では、それぞれの標準の数値書式指定文字列について詳しく説明します。  
  
<a name="CFormatString"></a>   
## <a name="the-currency-c-format-specifier"></a>通貨 ("C") 書式指定子  
 "C" (通貨) 書式指定子は、金額を表す文字列に数値を変換します。 精度指定子は、結果文字列の小数部の桁数を示します。 精度指定子を省略すると、<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A?displayProperty=nameWithType> プロパティによって既定の桁数が定義されます。  
  
 書式指定される値が指定または既定の小数部の桁数を超えている場合、小数値は結果文字列で丸められます。 指定した小数部の桁数の右側にある値が 5 以上の場合、結果文字列の最後の桁はゼロから離れる方向に丸められます。  
  
 結果文字列は、現在の <xref:System.Globalization.NumberFormatInfo> オブジェクトの書式情報に影響されます。 返される文字列の書式を制御する <xref:System.Globalization.NumberFormatInfo> のプロパティの一覧を次の表に示します。  
  
|NumberFormatInfo のプロパティ|説明|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern%2A>|正の値の通貨記号の位置を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>|負の値の通貨記号の位置を定義し、かっこと <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> プロパティのどちらによって負の符号が表されるかを指定します。|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|場合に使用される負符号を定義<xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern%2A>かっこを使用しないことを示します。|  
|<xref:System.Globalization.NumberFormatInfo.CurrencySymbol%2A>|通貨記号を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits%2A>|通貨値の既定の小数点以下桁数を定義します。 この値は、精度指定子を使用してオーバーライドできます。|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator%2A>|整数部と小数部を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator%2A>|整数の桁を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes%2A>|桁を何桁ごとに区切るかを定義します。|  
  
 次の例では、通貨書式指定子を使って <xref:System.Double> 値の書式を設定します。  
  
 [!code-cpp[Formatting.Numeric.Standard#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#1)]
 [!code-csharp[Formatting.Numeric.Standard#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#1)]
 [!code-vb[Formatting.Numeric.Standard#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#1)]  
  
 [表のトップへ](#table)  
  
<a name="DFormatString"></a>   
## <a name="the-decimal-d-format-specifier"></a>10 進数 ("D") 書式指定子  
 "D" (10 進数) 書式指定子は、0 ～ 9 の数字から成る文字列に数値を変換します。負の数値の場合は、文字列の先頭にマイナス記号が挿入されます。 この書式指定は整数型でだけサポートされています。  
  
 精度指定子は、変換後の文字列の最小桁数を示します。 必要に応じて、精度指定子によって指定された桁数に達するまで、数値の左側にゼロが埋め込まれます。 精度指定子が指定されていない場合の既定値は、先行するゼロを含めずに整数を表すために必要な最小値です。  
  
 結果文字列は、現在の <xref:System.Globalization.NumberFormatInfo> オブジェクトの書式情報に影響されます。 次の表に示すように、結果文字列の書式に影響を与えるプロパティは 1 つです。  
  
|NumberFormatInfo のプロパティ|説明|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|数値が負であることを示す文字列を定義します。|  
  
 次の例では、10 進数の書式指定子を使って <xref:System.Int32> 値の書式を設定します。  
  
 [!code-cpp[Formatting.Numeric.Standard#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#2)]
 [!code-csharp[Formatting.Numeric.Standard#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#2)]
 [!code-vb[Formatting.Numeric.Standard#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#2)]  
  
 [表のトップへ](#table)  
  
<a name="EFormatString"></a>   
## <a name="the-exponential-e-format-specifier"></a>指数 ("E") 書式指定子  
 指数 ("E") 書式指定子は、"-d.ddd…E+ddd" または "-d.ddd…e+ddd" という形式の文字列に数値を変換します。この "d" は 0 ～ 9 の 1 桁の数字を示します。 負の数値の場合、変換後の文字列の先頭にマイナス記号が挿入されます。 小数点の前には 1 桁の数字が必ず示されます。  
  
 精度指定子は、小数部の桁数を示します。 精度指定子を省略すると、小数部の桁数として既定の 6 桁が使用されます。  
  
 書式指定子が大文字の場合は指数部の前に "E" が挿入され、小文字の場合は "e" が挿入されます。 指数部は常に、プラス記号またはマイナス記号のいずれかと、3 桁以上の桁で構成されます。 指数部の桁数が最小桁数の 3 桁よりも少ない場合には、3 桁になるようにゼロが埋め込まれます。  
  
 結果文字列は、現在の <xref:System.Globalization.NumberFormatInfo> オブジェクトの書式情報に影響されます。 返される文字列の書式を制御する <xref:System.Globalization.NumberFormatInfo> のプロパティの一覧を次の表に示します。  
  
|NumberFormatInfo のプロパティ|説明|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|係数と指数部の両方で数値が負であることを示す文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|係数の整数部と小数部を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|指数部が正であることを示す文字列を定義します。|  
  
 次の例では、指数書式指定子を使って <xref:System.Double> 値の書式を設定します。  
  
 [!code-cpp[Formatting.Numeric.Standard#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#3)]
 [!code-csharp[Formatting.Numeric.Standard#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#3)]
 [!code-vb[Formatting.Numeric.Standard#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#3)]  
  
 [表のトップへ](#table)  
  
<a name="FFormatString"></a>   
## <a name="the-fixed-point-f-format-specifier"></a>固定小数点 ("F") 書式指定子  
 固定小数点 ("F") 書式指定子は、形式の文字列に数値を変換"-'-ddd.ddd...'" この "d" は 0 ～ 9 の 1 桁の数字を示します。 負の数値の場合、変換後の文字列の先頭にマイナス記号が挿入されます。  
  
 精度指定子は、小数部の桁数を示します。 精度指定子を省略すると、現在の <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> プロパティによって桁数が指定されます。  
  
 結果文字列は、現在の <xref:System.Globalization.NumberFormatInfo> オブジェクトの書式情報に影響されます。 結果文字列の書式を制御する <xref:System.Globalization.NumberFormatInfo> オブジェクトのプロパティの一覧を次の表に示します。  
  
|NumberFormatInfo のプロパティ|説明|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|数値が負であることを示す文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|整数部と小数部を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|既定の小数点以下桁数を定義します。 この値は、精度指定子を使用してオーバーライドできます。|  
  
 次の例では、固定小数点の書式指定子を使って <xref:System.Double> および <xref:System.Int32> 値の書式を設定します。  
  
 [!code-cpp[Formatting.Numeric.Standard#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#4)]
 [!code-csharp[Formatting.Numeric.Standard#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#4)]
 [!code-vb[Formatting.Numeric.Standard#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#4)]  
  
 [表のトップへ](#table)  
  
<a name="GFormatString"></a>   
## <a name="the-general-g-format-specifier"></a>一般 ("G") 書式指定子  
 一般 ("G") 書式指定子は、数値の型や、精度指定子が指定されているかどうかに応じて、固定小数点表記または指数表記のいずれかのより簡潔な形式に数値を変換します。 精度指定子は、結果文字列の有効桁数の最大値を定義します。 精度指定子が省略されている場合や、0 である場合は、次の表に示すように、数値の型によって既定の精度が決定されます。  
  
|数値型|既定の精度|  
|------------------|-----------------------|  
|<xref:System.Byte> または <xref:System.SByte>|3 桁|  
|<xref:System.Int16> または <xref:System.UInt16>|5 桁|  
|<xref:System.Int32> または <xref:System.UInt32>|10 桁|  
|<xref:System.Int64>|19 桁|  
|<xref:System.UInt64>|20 桁|  
|<xref:System.Numerics.BigInteger>|無制限 (["R"](#RFormatString) と同じ)|  
|<xref:System.Single>|7 桁|  
|<xref:System.Double>|15 桁|  
|<xref:System.Decimal>|29 桁|  
  
 数値を指数表記で表した結果の指数部が -5 よりも大きく、精度指定子よりも小さい場合は、固定小数点表記が使用されます。それ以外の場合は、指数表記が使用されます。 結果には必要に応じて小数点が含まれ、小数点の後続のゼロは省略されます。 精度指定子が存在し、指定された精度を結果の有効桁数が超える場合は、超過した桁は丸められ削除されます。  
  
 ただし、数値が <xref:System.Decimal> で、精度指定子が省略されている場合は、常に固定小数点表記が使用され、後続のゼロは保持されます。  
  
 指数表記が使用される場合、結果の指数部には、書式指定子が "G" のときには "E"、書式指定子が "g" のときには "e" というプレフィックスが付きます。 指数部には少なくとも 2 桁が含まれます。 これは、指数部に少なくとも 3 桁が含まれる、指数書式指定子によって生成される指数表記の書式とは異なります。  
 
なおで使用する場合、<xref:System.Double>値、"G17"書式指定子により、元の<xref:System.Double>値のラウンドト リップでは正常にします。 これは、ため<xref:System.Double>は、IEEE 754 2008 準拠倍精度 (`binary64`) 浮動小数点数の最大 17 桁の精度を提供します。 代わりに、使用することをお勧め、 ["R"書式指定子](#RFormatString)ラウンドト リップに成功の倍精度浮動小数点値に、場合によっては"R"が失敗したため、します。 次の例は、このような 1 つのケースを示しています。

[!code-csharp[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/csharp/g17.cs)]   
[!code-vb[Round-tripping a Double](../../../samples/snippets/standard/base-types/format-strings/vb/g17.vb)]   

使用すると、<xref:System.Single>値、"G9"書式指定子により、元の<xref:System.Single>値のラウンドト リップでは正常にします。 これは、ため<xref:System.Single>は、IEEE 754 2008 準拠単精度 (`binary32`) 浮動小数点数の最大 9 桁の精度を提供します。 代わりに、使用することをお勧め、 ["R"書式指定子](#RFormatString)ラウンドト リップに成功の単精度浮動小数点値に、場合によっては"R"が失敗したため、します。

 結果文字列は、現在の <xref:System.Globalization.NumberFormatInfo> オブジェクトの書式情報に影響されます。 結果文字列の書式を制御する <xref:System.Globalization.NumberFormatInfo> のプロパティの一覧を次の表に示します。  
  
|NumberFormatInfo のプロパティ|説明|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|数値が負であることを示す文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|整数部と小数部を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|指数部が正であることを示す文字列を定義します。|  
  
 次の例では、一般書式指定子を使って、さまざまな浮動小数点値の書式を設定します。  
  
 [!code-cpp[Formatting.Numeric.Standard#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#5)]
 [!code-csharp[Formatting.Numeric.Standard#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#5)]
 [!code-vb[Formatting.Numeric.Standard#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#5)]  
  
 [表のトップへ](#table)  
  
<a name="NFormatString"></a>   
## <a name="the-numeric-n-format-specifier"></a>数値 ("N") 書式指定子  
 "N" (Numeric: 数値) は、数値を "-d,ddd,ddd.ddd…" という形式の文字列に変換する書式指定子です。"-" は負数記号を示し (必要な場合)、"d" は数字 (0 ～ 9) を示し、"," は桁区切り記号を示し、"." は小数点記号を示します。 精度指定子は、小数部の桁数を示します。 精度指定子を省略すると、現在の <xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A?displayProperty=nameWithType> プロパティによって小数部の桁数が定義されます。  
  
 結果文字列は、現在の <xref:System.Globalization.NumberFormatInfo> オブジェクトの書式情報に影響されます。 結果文字列の書式を制御する <xref:System.Globalization.NumberFormatInfo> のプロパティの一覧を次の表に示します。  
  
|NumberFormatInfo のプロパティ|説明|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|数値が負であることを示す文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberNegativePattern%2A>|負の値の書式を定義し、かっこと <xref:System.Globalization.NumberFormatInfo.NegativeSign%2A> プロパティのどちらによって負の符号が表されるかを指定します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSizes%2A>|桁区切り記号の間の桁数を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator%2A>|整数の桁を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|整数部と小数部を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits%2A>|既定の小数点以下桁数を定義します。 この値は、精度指定子を使用してオーバーライドできます。|  
  
 次の例では、数値書式指定子を使って、さまざまな浮動小数点値の書式を設定します。  
  
 [!code-cpp[Formatting.Numeric.Standard#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#6)]
 [!code-csharp[Formatting.Numeric.Standard#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#6)]
 [!code-vb[Formatting.Numeric.Standard#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#6)]  
  
 [表のトップへ](#table)  
  
<a name="PFormatString"></a>   
## <a name="the-percent-p-format-specifier"></a>パーセント ("P") 書式指定子  
 パーセント ("P") 書式指定子は、数値に 100 を掛けて、パーセントを表す文字列に変換します。 精度指定子は、小数部の桁数を示します。 精度指定子を省略すると、現在の <xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A> プロパティによって指定される既定の桁数が使用されます。  
  
 返される文字列の書式を制御する <xref:System.Globalization.NumberFormatInfo> のプロパティの一覧を次の表に示します。  
  
|NumberFormatInfo のプロパティ|説明|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.PercentPositivePattern%2A>|正の値のパーセント記号の位置を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.PercentNegativePattern%2A>|負の値のパーセント記号と負の符号の位置を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|数値が負であることを示す文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.PercentSymbol%2A>|パーセント記号を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits%2A>|パーセント値の既定の小数点以下桁数を定義します。 この値は、精度指定子を使用してオーバーライドできます。|  
|<xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator%2A>|整数部と小数部を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator%2A>|整数の桁を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.PercentGroupSizes%2A>|桁を何桁ごとに区切るかを定義します。|  
  
 次の例では、パーセント書式指定子を使って、浮動小数点値の書式を設定します。  
  
 [!code-cpp[Formatting.Numeric.Standard#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#7)]
 [!code-csharp[Formatting.Numeric.Standard#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#7)]
 [!code-vb[Formatting.Numeric.Standard#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#7)]  
  
 [表のトップへ](#table)  
  
<a name="RFormatString"></a>   
## <a name="the-round-trip-r-format-specifier"></a>ラウンドトリップ ("R") 書式指定子  
 ラウンドト リップ ("R") 書式指定子は、文字列に変換される数値の値を数値に解析することを確認しようとします。 この書式指定は、<xref:System.Single> 型、<xref:System.Double> 型、および <xref:System.Numerics.BigInteger> 型でだけサポートされています。  

<xref:System.Double>と<xref:System.Single>値、場合によっては、"R"書式指定子は、元の値をラウンドト リップに成功に失敗しも比較的不十分なパフォーマンスを提供します。 代わりに、推奨を使用すること、 ["G17"](#GFormatString)書式指定子の<xref:System.Double>値、および["G9"](#GFormatString)書式指定子をラウンドト リップに成功<xref:System.Single>値。

 この指定子を使用して <xref:System.Numerics.BigInteger> 値の書式を設定すると、その文字列形式に <xref:System.Numerics.BigInteger> 値の有効桁数がすべて含まれます。  
  
 精度指定子は、指定できますが無視されます。 ラウンドトリップ指定子と精度指定子の両方を指定すると、ラウンドトリップ指定子が優先されます。    
 結果文字列は、現在の <xref:System.Globalization.NumberFormatInfo> オブジェクトの書式情報に影響されます。 結果文字列の書式を制御する <xref:System.Globalization.NumberFormatInfo> のプロパティの一覧を次の表に示します。  
  
|NumberFormatInfo のプロパティ|説明|  
|-------------------------------|-----------------|  
|<xref:System.Globalization.NumberFormatInfo.NegativeSign%2A>|数値が負であることを示す文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator%2A>|整数部と小数部を区切る文字列を定義します。|  
|<xref:System.Globalization.NumberFormatInfo.PositiveSign%2A>|指数部が正であることを示す文字列を定義します。|  
  
 次の形式の例、<xref:System.Numerics.BigInteger>ラウンドト リップ書式指定子を持つ値です。  
  
 [!code-cpp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cpp)]
 [!code-csharp[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.cs)]
 [!code-vb[R format specifier with a BigInteger](../../../samples/snippets/standard/base-types/format-strings/biginteger-r.vb)]  
  
> [!IMPORTANT]
>  場合によっては、`/platform:x64` スイッチまたは `/platform:anycpu` スイッチを使用してコンパイルして 64 ビット システムで実行すると、"R" 標準の数値書式指定文字列で書式設定される <xref:System.Double> 値のラウンドトリップに失敗することがあります。 詳細については、次の段落を参照してください。  
  
 `/platform:x64` スイッチまたは `/platform:anycpu` スイッチを使用してコンパイルして 64 ビット システムで実行すると、「R」標準の数値書式指定文字列を使用して書式設定される <xref:System.Double> 値のラウンドトリップが失敗するという問題を回避するために、<xref:System.Double> 値を「G17」標準の数値書式指定文字列を使用して書式設定することができます。 次の例では、ラウンドトリップに失敗する <xref:System.Double> 値を持つ "R" 書式指定文字列を使用しています。元の値のラウンドトリップに成功する "G17" 書式指定文字列も使用しています。  
  
 [!code-csharp[System.Double.ToString#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Double.ToString/cs/roundtripex1.cs#5)]
 [!code-vb[System.Double.ToString#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Double.ToString/vb/roundtripex1.vb#5)]  
  
 [表のトップへ](#table)  
  
<a name="XFormatString"></a>   
## <a name="the-hexadecimal-x-format-specifier"></a>16 進数 ("X") 書式指定子  
 16 進数 ("X") 書式指定子は、16 進数文字列に数値を変換します。 書式指定子の大文字と小文字によって、9 よりも大きい 16 進数値を示すアルファベット文字が大文字と小文字のどちらで表示されるかが決まります。 たとえば、"X" を指定すると "ABCDEF" となり、"x" を指定すると "abcdef" となります。 この書式指定は整数型でだけサポートされています。  
  
 精度指定子は、変換後の文字列の最小桁数を示します。 必要に応じて、精度指定子によって指定された桁数に達するまで、数値の左側にゼロが埋め込まれます。  
  
 結果文字列は、現在の <xref:System.Globalization.NumberFormatInfo> オブジェクトの書式情報に影響されません。  
  
 次の例では、16 進数の書式指定子を使って <xref:System.Int32> 値の書式を設定します。  
  
 [!code-cpp[Formatting.Numeric.Standard#9](../../../samples/snippets/cpp/VS_Snippets_CLR/Formatting.Numeric.Standard/cpp/Standard.cpp#9)]
 [!code-csharp[Formatting.Numeric.Standard#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Numeric.Standard/cs/Standard.cs#9)]
 [!code-vb[Formatting.Numeric.Standard#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Numeric.Standard/vb/Standard.vb#9)]  
  
 [表のトップへ](#table)  
  
<a name="NotesStandardFormatting"></a>   
## <a name="notes"></a>ノート  
  
### <a name="control-panel-settings"></a>コントロール パネルの設定  
 コントロール パネルの **[地域と言語のオプション]** での設定は、書式設定操作によって生成される結果の文字列に影響します。 これらの設定は、書式設定の制御に使用される値を提供する現在のスレッド カルチャに関連付けられた <xref:System.Globalization.NumberFormatInfo> オブジェクトを初期化するために使用されます。 コンピューターで使用する設定が異なる場合は、生成される文字列も異なります。  
  
 さらに場合、<xref:System.Globalization.CultureInfo.%23ctor%28System.String%29?displayProperty=nameWithType>コンス トラクターを使用して、新しいインスタンスを作成する<xref:System.Globalization.CultureInfo>を現在のシステム カルチャによって確立された任意のカスタマイズと同じカルチャを表すオブジェクト、**地域と言語のオプション**コントロール パネル では、新しいに適用される<xref:System.Globalization.CultureInfo>オブジェクト。 <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> コンストラクターを使用すると、システムに対するカスタマイズが反映されない <xref:System.Globalization.CultureInfo> オブジェクトを作成できます。  
  
### <a name="numberformatinfo-properties"></a>NumberFormatInfo のプロパティ  
 書式設定は、現在の <xref:System.Globalization.NumberFormatInfo> オブジェクトのプロパティの影響を受けます。このオブジェクトは、現在のスレッド カルチャによって暗黙的に指定されるか、または書式設定を実行するメソッドの <xref:System.IFormatProvider> パラメーターによって明示的に指定されます。 このパラメーターには、<xref:System.Globalization.NumberFormatInfo> オブジェクトまたは <xref:System.Globalization.CultureInfo> オブジェクトを指定してください。  
  
> [!NOTE]
>  数値の書式設定に使用するパターンまたは文字列のカスタマイズの詳細については、<xref:System.Globalization.NumberFormatInfo> クラスに関するトピックを参照してください。  
  
### <a name="integral-and-floating-point-numeric-types"></a>整数数値型と浮動小数点数値型  
 標準の数値書式指定子の記述で、整数数値型または浮動小数点数値型が参照されている場合があります。 整数数値型には、<xref:System.Byte>、<xref:System.SByte>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.UInt16>、<xref:System.UInt32>、<xref:System.UInt64>、および <xref:System.Numerics.BigInteger> があります。 浮動小数点数値型には、<xref:System.Decimal>、<xref:System.Single>、および <xref:System.Double> があります。  
  
### <a name="floating-point-infinities-and-nan"></a>浮動小数点の無限大値と NaN (非数) 値  
 <xref:System.Single> の浮動小数点型または <xref:System.Double> の浮動小数点型が正の無限大、負の無限大、または NaN (非数) である場合は、書式指定文字列とは関係なく、現在適用可能な <xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol%2A> オブジェクトによって指定される <xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol%2A>、<xref:System.Globalization.NumberFormatInfo.NaNSymbol%2A>、または <xref:System.Globalization.NumberFormatInfo> の各プロパティの値は、書式設定された文字列となります。  
  
<a name="example"></a>   
## <a name="example"></a>例  
 次の例では、en-US カルチャおよびすべての標準数値書式指定子を使用して、整数値と浮動小数点数値を書式設定します。 この例では 2 つの特定の数値型 (<xref:System.Double> および <xref:System.Int32>) を使用していますが、他の数値基本型 (<xref:System.Byte>、<xref:System.SByte>、<xref:System.Int16>、<xref:System.Int32>、<xref:System.Int64>、<xref:System.UInt16>、<xref:System.UInt32>、<xref:System.UInt64><xref:System.Numerics.BigInteger>、<xref:System.Decimal>、および <xref:System.Single>) でも類似した結果が得られます。  
  
 [!code-csharp[system.x.tostring-and-culture#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.X.ToString-and-Culture/cs/xts.cs#1)]
 [!code-vb[system.x.tostring-and-culture#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.X.ToString-and-Culture/vb/xts.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Globalization.NumberFormatInfo>  
 [Custom Numeric Format Strings](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [型の書式設定](../../../docs/standard/base-types/formatting-types.md)  
 [方法: 数値に先行するゼロを埋め込む](../../../docs/standard/base-types/how-to-pad-a-number-with-leading-zeros.md)  
 [サンプル: .NET Framework 4 の書式設定ユーティリティ](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)  
 [複合書式指定](../../../docs/standard/base-types/composite-formatting.md)
