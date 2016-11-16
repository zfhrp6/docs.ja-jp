---
title: "標準の数値書式指定文字列"
description: "標準の数値書式指定文字列"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 285faf73-466a-4af0-8eba-7e509958f240
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 5f5ee73c7c9e0ecdce8aa0d75a630decea57704b

---

# <a name="standard-numeric-format-strings"></a>標準の数値書式指定文字列

一般的な数値型を書式設定するには、標準の数値書式指定文字列を使用します。 標準の数値書式指定文字列の形式は **A**_xx_ です。 

* **A** は*書式指定子*で、1 文字の英文字です。 空白を含む複数の英文字で構成される数値書式指定文字列は、カスタム数値書式指定文字列として解釈されます。 詳細については、「[カスタム数値書式指定文字列](custom-numeric.md)」をご覧ください。 

* *xx* は*精度指定子*で、省略可能な整数値です。 精度指定子は 0 ～ 99 の範囲で指定され、結果の桁数に影響します。 精度指定子は、文字列形式の数値の桁数を制御することに注意してください。 精度指定子では、数値を丸めません。 丸め操作を実行するには、[Math.Ceiling](xref:System.Math)、[Math.Floor](xref:System.Math)、または [Math.Round](xref:System.Math) の各メソッドを使用します。 

*精度指定子*が結果文字列内の小数部の桁数を制御する際、結果文字列は、ゼロから離れる方向に丸められる数を反映します (つまり、[MidpointRounding.AwayFromZero](xref:System.MidpointRounding.AwayFromZero) を使用します)。 

> [!NOTE]
> 精度指定子は、結果文字列の桁数を決定します。 結果文字列に先頭または末尾のスペースを埋め込むには、[複合書式指定](composite-format.md)機能を使用して、書式指定項目に *alignment コンポーネント*を定義します。 

標準の数値書式指定文字列は、すべての数値型の `ToString` メソッドの一部のオーバーロードでサポートされています。 たとえば、[Int32](xref:System.Int32) 型の [ToString(String)](xref:System.Int32.ToString(System.String)) および [ToString(String, IFormatProvider)](xref:System.Int32.ToString(System.String,System.IFormatProvider)) メソッドに数値書式指定文字列を指定できます。 標準の数値書式指定文字列は、.NET の[複合書式指定](composite-format.md)機能でもサポートされています。この機能を使用するメソッドには、[Console](xref:System.Console) および [StreamWriter](xref:System.IO.StreamWriter) クラスの一部の `Write` および `WriteLine` メソッド、[String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) メソッド、および [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) メソッドがあります。 複合書式指定機能により、複数のデータ項目の文字列表現を 1 つの文字列にまとめ、フィールド幅を指定し、フィールドの数値の位置を揃えることができます。 詳細については、「[複合書式指定](composite-format.md)」をご覧ください。 

次の表に、標準数値書式指定子の説明および書式指定子ごとのサンプル出力を示します。 標準の数値書式指定文字列の使用方法については、「[メモ](#notes)」をご覧ください。それらを使用する包括的な例については、「[例](#example)」をご覧ください。

|書式指定子|名前|説明|例|  
|----------------------|----------|-----------------|--------------|  
|"C" または "c"|通貨|結果: 通貨値。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: [NumberFormatInfo.CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) によって定義されます。<br /><br /> |123.456 ("C", en-US) -> $123.46<br /><br /> 123.456 ("C", fr-FR) -> 123,46 €<br /><br /> 123.456 ("C", ja-JP) -> ¥123<br /><br /> -123.456 ("C3", en-US) -> ($123.456)<br /><br /> -123.456 ("C3", fr-FR) -> -123,456 €<br /><br /> -123.456 ("C3", ja-JP) -> -¥123.456|  
|"D" または "d"|Decimal (10 進数型)|結果: 必要に応じて負の符号が付く整数。<br /><br /> サポート: 整数型のみ。<br /><br /> 精度指定子: 最小桁数。<br /><br /> 既定の精度指定子: 必要な最小桁数。<br /><br /> |1234 ("D") -> 1234<br /><br /> -1234 ("D6") -> -001234|  
|"E" または "e"|指数|結果: 指数表記。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: 6。<br /><br /> |1052.0329112756 ("E", en-US) -> 1.052033E+003<br /><br /> 1052.0329112756 ("e", fr-FR) -> 1,052033e+003<br /><br /> -1052.0329112756 ("e2", en-US) -> -1.05e+003<br /><br /> -1052.0329112756 ("E2", fr_FR) -> -1,05E+003|  
|"F" または "f"|固定小数点|結果: 必要に応じて負の符号が付く整数と小数。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) によって定義されます。<br /><br /> |1234.567 ("F", en-US) -> 1234.57<br /><br /> 1234.567 ("F", de-DE) -> 1234,57<br /><br /> 1234 ("F1", en-US) -> 1234.0<br /><br /> 1234 ("F1", de-DE) -> 1234,0<br /><br /> -1234.56 ("F4", en-US) -> -1234.5600<br /><br /> -1234.56 ("F4", de-DE) -> -1234,5600|  
|"G" または "g"|全般|結果: 固定小数点表記または指数表記のいずれかのより簡潔な形式。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 有効桁数。<br /><br /> 既定の精度指定子: 数値型によって異なります。<br /><br /> |-123.456 ("G", en-US) -> -123.456<br /><br /> -123.456 ("G", sv-SE) -> -123,456<br /><br /> 123.4546 ("G4", en-US) -> 123.5<br /><br /> 123.4546 ("G4", sv-SE) -> 123,5<br /><br /> -1.234567890e-25 ("G", en-US) -> -1.23456789E-25<br /><br /> -1.234567890e-25 ("G", sv-SE) -> -1,23456789E-25|  
|"N" または "n"|Number|結果: 必要に応じて負の符号が付く整数と小数、桁区切り記号、および小数点記号。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) によって定義されます。<br /><br /> |1234.567 ("N", en-US) -> 1,234.57<br /><br /> 1234.567 ("N", ru-RU) -> 1 234,57<br /><br /> 1234 ("N1", en-US) -> 1,234.0<br /><br /> 1234 ("N1", ru-RU) -> 1 234,0<br /><br /> -1234.56 ("N3", en-US) -> -1,234.560<br /><br /> -1234.56 ("N3", ru-RU) -> -1 234,560|  
|"P" または "p"|パーセント|結果: 数値に 100 を掛けて、パーセント記号を付けて表示します。<br /><br /> サポート: すべての数値型。<br /><br /> 精度指定子: 小数部の桁数。<br /><br /> 既定の精度指定子: [NumberFormatInfo.PercentDecimalDigits](assetId:///P:System.Globalization.NumberFormatInfo.PercentDecimalDigits?qualifyHint=True&autoUpgrade=True) によって定義されます。<br /><br /> |1 ("P", en-US) -> 100.00 %<br /><br /> 1 ("P", fr-FR) -> 100,00 %<br /><br /> -0.39678 ("P1", en-US) -> -39.7 %<br /><br /> -0.39678 ("P1", fr-FR) -> -39,7 %|  
|"R" または "r"|ラウンドトリップ|結果: 同じ数値にラウンドトリップできる文字列。<br /><br /> サポート: [Single](xref:System.Single)、[Double](xref:System.Double)、および [BigInteger](xref:System.Numerics.BigInteger)。<br /><br /> 精度指定子: 無視されます。<br /><br /> |123456789.12345678 ("R") -> 123456789.12345678<br /><br /> -1234567890.12345678 ("R") -> -1234567890.1234567|  
|"X" または "x"|16 進数|結果: 16 進数文字列。<br /><br /> サポート: 整数型のみ。<br /><br /> 精度指定子: 結果文字列の桁数。<br /><br /> |255 ("X") -> FF<br /><br /> -1 ("x") -> ff<br /><br /> 255 ("x4") -> 00ff<br /><br /> -1 ("X4") -> 00FF|  
|その他の 1 文字|未定義の指定子|結果: 実行時に [FormatException](xref:System.FormatException) をスローします。|| 

## <a name="using-standard-numeric-format-strings"></a>標準の数値書式指定文字列の使用

標準の数値書式指定文字列を使用すると、次のいずれかの方法で数値の書式を定義できます。

* *format* パラメーターを持つ `ToString` メソッドのオーバーロードに渡す。 次の例では、数値の書式を現在のカルチャ (ここでは en-US) の通貨文字列に設定しています。 

  ```csharp
  decimal value = 123.456m;
  Console.WriteLine(value.ToString("C2"));
  // Displays $123.46
  ```

  ```vb
  Dim value As Decimal = 123.456d
  Console.WriteLine(value.ToString("C2"))         
  ' Displays $123.46
  ```
  
* [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))、[Console.WriteLine](xref:System.Console.WriteLine)、および [StringBuilder.AppendFormat](xref:System.Text.StringBuilder.AppendFormat(System.IFormatProvider,System.String,System.Object)) などのメソッドで使用される書式指定項目の *formatString* 引数として渡す。 詳細については、「[複合書式指定](composite-format.md)」をご覧ください。 次の例では、書式指定項目を使用して文字列に通貨値を挿入しています。

  ```csharp
  decimal value = 123.456m;
  Console.WriteLine("Your account balance is {0:C2}.", value);
  // Displays "Your account balance is $123.46."
  ```

  ```vb
  Dim value As Decimal = 123.456d
  Console.WriteLine("Your account balance is {0:C2}.", value)
  ' Displays "Your account balance is $123.46."
  ```
  
  オプションで alignment 引数を渡して、数値フィールドの幅と、その値を右揃えまたは左揃えにするかどうかを指定します。 次の例では、通貨の値が 28 文字フィールドでは左揃えになっており、14 文字フィールドでは右揃えになっています。
  
  ```csharp
  decimal[] amounts = { 16305.32m, 18794.16m };
  Console.WriteLine("   Beginning Balance           Ending Balance");
  Console.WriteLine("   {0,-28:C2}{1,14:C2}", amounts[0], amounts[1]);
  // Displays:
  //        Beginning Balance           Ending Balance
  //        $16,305.32                      $18,794.16
  ```

  ```vb
  Dim amounts() As Decimal = { 16305.32d, 18794.16d }
  Console.WriteLine("   Beginning Balance           Ending Balance")
  Console.WriteLine("   {0,-28:C2}{1,14:C2}", amounts(0), amounts(1))
  ' Displays:
  '        Beginning Balance           Ending Balance
  '        $16,305.32                      $18,794.16
  ```
  
以降では、それぞれの標準の数値書式指定文字列について詳しく説明します。

## <a name="the-currency-c-format-specifier"></a>通貨 ("C") 書式指定子

"C" (通貨) 書式指定子は、金額を表す文字列に数値を変換します。 精度指定子は、結果文字列の小数部の桁数を示します。 精度指定子を省略すると、[NumberFormatInfo.CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) プロパティによって既定の桁数が定義されます。

書式指定される値が指定または既定の小数部の桁数を超えている場合、小数値は結果文字列で丸められます。 指定した小数部の桁数の右側にある値が 5 以上の場合、結果文字列の最後の桁はゼロから離れる方向に丸められます。

結果文字列は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、返される文字列の書式を制御する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) プロパティの一覧を示します。

NumberFormatInfo のプロパティ | 説明
------------------------- | -----------
[CurrencyPositivePattern](xref:System.Globalization.NumberFormatInfo.CurrencyPositivePattern) | 正の値の通貨記号の位置を定義します。
[CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) | 負の値の通貨記号の位置を定義し、かっこと [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) プロパティのどちらで負の符号が表されるかを指定します。
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | [CurrencyNegativePattern](xref:System.Globalization.NumberFormatInfo.CurrencyNegativePattern) でかっこを使用しないように指定されている場合に使用される負の符号を定義します。 
[CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) | 通貨記号を定義します。
[CurrencyDecimalDigits](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalDigits) | 通貨値の既定の小数点以下桁数を定義します。 この値は、精度指定子を使用してオーバーライドできます。
[CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) | 整数部と小数部を区切る文字列を定義します。
[CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) | 整数の桁を区切る文字列を定義します。 
[CurrencyGroupSizes](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSizes) | 桁を何桁ごとに区切るかを定義します。

次の例では、通貨書式指定子を使って [Double](xref:System.Double) 値の書式を設定します。 

```csharp
double value = 12345.6789;
Console.WriteLine(value.ToString("C", CultureInfo.CurrentCulture));

Console.WriteLine(value.ToString("C3", CultureInfo.CurrentCulture));

Console.WriteLine(value.ToString("C3", 
                  CultureInfo.CreateSpecificCulture("da-DK")));
// The example displays the following output on a system whose
// current culture is English (United States):
//       $12,345.68
//       $12,345.679
//       kr 12.345,679
```

```vb
Dim value As Double = 12345.6789
Console.WriteLine(value.ToString("C", CultureInfo.CurrentCulture))

Console.WriteLine(value.ToString("C3", CultureInfo.CurrentCulture))

Console.WriteLine(value.ToString("C3", _
                  CultureInfo.CreateSpecificCulture("da-DK")))
' The example displays the following output on a system whose
' current culture is English (United States):
'       $12,345.68
'       $12,345.679
'       kr 12.345,679
```

## <a name="the-decimal-d-format-specifier"></a>10 進数 ("D") 書式指定子

"D" (10 進数) 書式指定子は、0 ～ 9 の数字から成る文字列に数値を変換します。負の数値の場合は、文字列の先頭にマイナス記号が挿入されます。 この書式指定は整数型でだけサポートされています。

精度指定子は、変換後の文字列の最小桁数を示します。 必要に応じて、精度指定子によって指定された桁数に達するまで、数値の左側にゼロが埋め込まれます。 精度指定子が指定されていない場合の既定値は、先行するゼロを含めずに整数を表すために必要な最小値です。

結果文字列は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの書式情報に影響されます。 次の表に示すように、結果文字列の書式に影響を与えるプロパティは 1 つです。 

NumberFormatInfo のプロパティ | 説明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 数値が負であることを示す文字列を定義します。 

次の例では、10 進数の書式指定子を使って [Int32](xref:System.Int32) 値の書式を設定します。

```csharp
int value; 

value = 12345;
Console.WriteLine(value.ToString("D"));
// Displays 12345
Console.WriteLine(value.ToString("D8"));
// Displays 00012345

value = -12345;
Console.WriteLine(value.ToString("D"));
// Displays -12345
Console.WriteLine(value.ToString("D8"));
// Displays -00012345
```

```vb
Dim value As Integer 

value = 12345
Console.WriteLine(value.ToString("D"))
' Displays 12345   
Console.WriteLine(value.ToString("D8"))
' Displays 00012345

value = -12345
Console.WriteLine(value.ToString("D"))
' Displays -12345
Console.WriteLine(value.ToString("D8"))
' Displays -00012345
```

## <a name="the-exponential-e-format-specifier"></a>指数 ("E") 書式指定子

指数 ("E") 書式指定子は、"-d.ddd…E+ddd" または "-d.ddd…e+ddd" という形式の文字列に数値を変換します。この "d" は 0 ～ 9 の 1 桁の数字を示します。 負の数値の場合、変換後の文字列の先頭にマイナス記号が挿入されます。 小数点の前には 1 桁の数字が必ず示されます。 

精度指定子は、小数部の桁数を示します。 精度指定子を省略すると、小数部の桁数として既定の 6 桁が使用されます。 

書式指定子が大文字の場合は指数部の前に "E" が挿入され、小文字の場合は "e" が挿入されます。 指数部は常に、プラス記号またはマイナス記号のいずれかと、3 桁以上の桁で構成されます。 指数部の桁数が最小桁数の 3 桁よりも少ない場合には、3 桁になるようにゼロが埋め込まれます。

結果文字列は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、返される文字列の書式を制御する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) プロパティの一覧を示します。

NumberFormatInfo のプロパティ | 説明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 係数と指数部の両方で数値が負であることを示す文字列を定義します。 
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 係数の整数部と小数部を区切る文字列を定義します。
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | 指数部が正であることを示す文字列を定義します。

次の例では、指数書式指定子を使って [Double](xref:System.Double) 値の書式を設定します。 

```csharp
double value = 12345.6789;
Console.WriteLine(value.ToString("E", CultureInfo.InvariantCulture));
// Displays 1.234568E+004

Console.WriteLine(value.ToString("E10", CultureInfo.InvariantCulture));
// Displays 1.2345678900E+004

Console.WriteLine(value.ToString("e4", CultureInfo.InvariantCulture));
// Displays 1.2346e+004

Console.WriteLine(value.ToString("E", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 1,234568E+004
```

```vb
Dim value As Double = 12345.6789
Console.WriteLine(value.ToString("E", CultureInfo.InvariantCulture))
' Displays 1.234568E+004

Console.WriteLine(value.ToString("E10", CultureInfo.InvariantCulture))
' Displays 1.2345678900E+004

Console.WriteLine(value.ToString("e4", CultureInfo.InvariantCulture))
' Displays 1.2346e+004

Console.WriteLine(value.ToString("E", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 1,234568E+004
```

## <a name="the-fixedpoint-f-format-specifier"></a>固定小数点 ("F") 書式指定子

固定小数点 ("F) 書式指定子は、"-ddd.ddd…" という形式の文字列に数値を変換します。 この "d" は 0 ～ 9 の 1 桁の数字を示します。 負の数値の場合、変換後の文字列の先頭にマイナス記号が挿入されます。 

精度指定子は、小数部の桁数を示します。 精度指定子を省略すると、現在の [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) プロパティによって桁数が指定されます。

結果文字列は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、結果文字列の書式を制御する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトのプロパティの一覧を示します。

NumberFormatInfo のプロパティ | 説明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 数値が負であることを示す文字列を定義します。
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 整数部と小数部を区切る文字列を定義します。
[NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) | 既定の小数点以下桁数を定義します。 この値は、精度指定子を使用してオーバーライドできます。

次の例では、固定小数点の書式指定子を使って [Double](xref:System.Double) および [Int32](xref:System.Int32) 値の書式を設定します。

```csharp
int integerNumber;
integerNumber = 17843;
Console.WriteLine(integerNumber.ToString("F", 
                  CultureInfo.InvariantCulture));
// Displays 17843.00

integerNumber = -29541;
Console.WriteLine(integerNumber.ToString("F3", 
                  CultureInfo.InvariantCulture));
// Displays -29541.000

double doubleNumber;
doubleNumber = 18934.1879;
Console.WriteLine(doubleNumber.ToString("F", CultureInfo.InvariantCulture));
// Displays 18934.19

Console.WriteLine(doubleNumber.ToString("F0", CultureInfo.InvariantCulture));
// Displays 18934

doubleNumber = -1898300.1987;
Console.WriteLine(doubleNumber.ToString("F1", CultureInfo.InvariantCulture));  
// Displays -1898300.2

Console.WriteLine(doubleNumber.ToString("F3", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays -1898300,199 
```

```vb
Dim integerNumber As Integer
integerNumber = 17843
Console.WriteLine(integerNumber.ToString("F", CultureInfo.InvariantCulture))
' Displays 17843.00

integerNumber = -29541
Console.WriteLine(integerNumber.ToString("F3", CultureInfo.InvariantCulture))
' Displays -29541.000

Dim doubleNumber As Double
doubleNumber = 18934.1879
Console.WriteLine(doubleNumber.ToString("F", CultureInfo.InvariantCulture))
' Displays 18934.19

Console.WriteLine(doubleNumber.ToString("F0", CultureInfo.InvariantCulture))
' Displays 18934

doubleNumber = -1898300.1987
Console.WriteLine(doubleNumber.ToString("F1", CultureInfo.InvariantCulture))  
' Displays -1898300.2

Console.WriteLine(doubleNumber.ToString("F3", _ 
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays -1898300,199                        
```

## <a name="the-general-g-format-specifier"></a>一般 ("G") 書式指定子

一般 ("G") 書式指定子は、数値の型や、精度指定子が指定されているかどうかに応じて、固定小数点表記または指数表記のいずれかのより簡潔な形式に数値を変換します。 精度指定子は、結果文字列の有効桁数の最大値を定義します。 精度指定子が省略されている場合や、0 である場合は、次の表に示すように、数値の型によって既定の精度が決定されます。 

数値型 | 既定の精度
------------ | -----------------
[Byte](xref:System.Byte) または [SByte](xref:System.SByte) | 3 桁
[Int16](xref:System.Int16) または [UInt16](xref:System.UInt16) | 5 桁
[Int32](xref:System.Int32) または [UInt32](xref:System.UInt32) | 10 桁
[Int64](xref:System.Int64) | 19 桁
[UInt64](xref:System.UInt64) | 20 桁
[BigInteger](xref:System.Numerics.BigInteger) | 無制限 ("R" と同じ)
[Single](xref:System.Single) | 7 桁
[Double](xref:System.Double) | 15 桁
[Decimal](xref:System.Decimal) | 29 桁

数値を指数表記で表した結果の指数部が -5 よりも大きく、精度指定子よりも小さい場合は、固定小数点表記が使用されます。それ以外の場合は、指数表記が使用されます。 結果には必要に応じて小数点が含まれ、小数点の後続のゼロは省略されます。 精度指定子が存在し、指定された精度を結果の有効桁数が超える場合は、超過した桁は丸められ削除されます。 

ただし、数値が [Decimal](xref:System.Decimal) で、精度指定子が省略されている場合は、常に固定小数点表記が使用され、後続のゼロは保持されます。

指数表記が使用される場合、結果の指数部には、書式指定子が "G" のときには "E"、書式指定子が "g" のときには "e" というプレフィックスが付きます。 指数部には少なくとも 2 桁が含まれます。 これは、指数部に少なくとも 3 桁が含まれる、指数書式指定子によって生成される指数表記の書式とは異なります。

結果文字列は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、結果文字列の書式を制御する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) プロパティの一覧を示します。

NumberFormatInfo のプロパティ | 説明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 数値が負であることを示す文字列を定義します。
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 整数部と小数部を区切る文字列を定義します。
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | 指数部が正であることを示す文字列を定義します。 

次の例では、一般書式指定子を使って、さまざまな浮動小数点値の書式を設定します。

```csharp
double number;

number = 12345.6789;      
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays  12345.6789
Console.WriteLine(number.ToString("G", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 12345,6789

Console.WriteLine(number.ToString("G7", CultureInfo.InvariantCulture));
// Displays 12345.68 

number = .0000023;
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays 2.3E-06       
Console.WriteLine(number.ToString("G", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 2,3E-06

number = .0023;
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture));
// Displays 0.0023

number = 1234;
Console.WriteLine(number.ToString("G2", CultureInfo.InvariantCulture));
// Displays 1.2E+03

number = Math.PI;
Console.WriteLine(number.ToString("G5", CultureInfo.InvariantCulture));
// Displays 3.1416    
```

```vb
Dim number As Double

number = 12345.6789      
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays  12345.6789
Console.WriteLine(number.ToString("G", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 12345,6789

Console.WriteLine(number.ToString("G7", CultureInfo.InvariantCulture))
' Displays 12345.68 

number = .0000023
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays 2.3E-06       
Console.WriteLine(number.ToString("G", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 2,3E-06

number = .0023
Console.WriteLine(number.ToString("G", CultureInfo.InvariantCulture))
' Displays 0.0023

number = 1234
Console.WriteLine(number.ToString("G2", CultureInfo.InvariantCulture))
' Displays 1.2E+03

number = Math.Pi
Console.WriteLine(number.ToString("G5", CultureInfo.InvariantCulture))
' Displays 3.1416
```

## <a name="the-numeric-n-format-specifier"></a>数値 ("N") 書式指定子

"N" (Numeric: 数値) は、数値を "-d,ddd,ddd.ddd…" という形式の文字列に変換する書式指定子です。"-" は負数記号を示し (必要な場合)、"d" は数字 (0 ～ 9) を示し、"," は桁区切り記号を示し、"." は小数点記号を示します。 精度指定子は、小数部の桁数を示します。 精度指定子を省略すると、現在の [NumberFormatInfo.NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) プロパティによって小数部の桁数が定義されます。

結果文字列は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、結果文字列の書式を制御する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) プロパティの一覧を示します。

NumberFormatInfo のプロパティ | 説明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 数値が負であることを示す文字列を定義します。
[NumberNegativePattern](xref:System.Globalization.NumberFormatInfo.NumberNegativePattern) | 負の値の書式を定義し、かっこと [NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) プロパティのどちらで負の符号が表されるかを指定します。
[NumberGroupSizes](xref:System.Globalization.NumberFormatInfo.NumberGroupSizes) | 桁区切り記号の間の桁数を定義します。
[NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) | 整数の桁を区切る文字列を定義します。
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 整数部と小数部を区切る文字列を定義します。
[NumberDecimalDigits](xref:System.Globalization.NumberFormatInfo.NumberDecimalDigits) | 既定の小数点以下桁数を定義します。 この値は、精度指定子を使用してオーバーライドできます。

次の例では、数値書式指定子を使って、さまざまな浮動小数点値の書式を設定します。

```csharp
double dblValue = -12445.6789;
Console.WriteLine(dblValue.ToString("N", CultureInfo.InvariantCulture));
// Displays -12,445.68
Console.WriteLine(dblValue.ToString("N1", 
                  CultureInfo.CreateSpecificCulture("sv-SE")));
// Displays -12 445,7

int intValue = 123456789;
Console.WriteLine(intValue.ToString("N1", CultureInfo.InvariantCulture));
// Displays 123,456,789.0 
```

```vb
Dim dblValue As Double = -12445.6789
Console.WriteLine(dblValue.ToString("N", CultureInfo.InvariantCulture))
' Displays -12,445.68
Console.WriteLine(dblValue.ToString("N1", _
                  CultureInfo.CreateSpecificCulture("sv-SE")))
' Displays -12 445,7

Dim intValue As Integer = 123456789
Console.WriteLine(intValue.ToString("N1", CultureInfo.InvariantCulture))
' Displays 123,456,789.0 
```

## <a name="the-percent-p-format-specifier"></a>パーセント ("P") 書式指定子

パーセント ("P") 書式指定子は、数値に 100 を掛けて、パーセントを表す文字列に変換します。 精度指定子は、小数部の桁数を示します。 精度指定子を省略すると、現在の [PercentDecimalDigits](xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits) プロパティによって指定される既定の桁数が使用されます。

次の表に、返される文字列の書式を制御する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) プロパティの一覧を示します。

umberFormatInfo プロパティ | 説明
------------------------- | -----------
[PercentPositivePattern](xref:System.Globalization.NumberFormatInfo.PercentPositivePattern) | 正の値のパーセント記号の位置を定義します。
[PercentNegativePattern](xref:System.Globalization.NumberFormatInfo.PercentNegativePattern) | 
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 数値が負であることを示す文字列を定義します。
[PercentSymbol](xref:System.Globalization.NumberFormatInfo.PercentSymbol) | パーセント記号を定義します。
[PercentDecimalDigits](xref:System.Globalization.NumberFormatInfo.PercentDecimalDigits) | パーセント値の既定の小数点以下桁数を定義します。 この値は、精度指定子を使用してオーバーライドできます。
[PercentDecimalSeparator](xref:System.Globalization.NumberFormatInfo.PercentDecimalSeparator) | 整数部と小数部を区切る文字列を定義します。
[PercentGroupSeparator](xref:System.Globalization.NumberFormatInfo.PercentGroupSeparator) | 整数の桁を区切る文字列を定義します。 
[PercentGroupSizes](xref:System.Globalization.NumberFormatInfo.PercentGroupSizes) | 桁を何桁ごとに区切るかを定義します。

次の例では、パーセント書式指定子を使って、浮動小数点値の書式を設定します。

```csharp
double number = .2468013;
Console.WriteLine(number.ToString("P", CultureInfo.InvariantCulture));
// Displays 24.68 %
Console.WriteLine(number.ToString("P", 
                  CultureInfo.CreateSpecificCulture("hr-HR")));
// Displays 24,68%     
Console.WriteLine(number.ToString("P1", CultureInfo.InvariantCulture));
// Displays 24.7 %
```

```vb
Dim number As Double = .2468013
Console.WriteLine(number.ToString("P", CultureInfo.InvariantCulture))
' Displays 24.68 %
Console.WriteLine(number.ToString("P", _
                  CultureInfo.CreateSpecificCulture("hr-HR")))
' Displays 24,68%     
Console.WriteLine(number.ToString("P1", CultureInfo.InvariantCulture))
' Displays 24.7 %
```

## <a name="the-roundtrip-r-format-specifier"></a>ラウンドトリップ ("R") 書式指定子

ラウンドトリップ ("R") 書式指定子は、数値の変換後の文字列が、変換前と同じ数値へ戻るように解析されること確認するために使用されます。 この書式指定は、[Single](xref:System.Single) 型、[Double](xref:System.Double) 型、および [BigInteger](xref:System.Numerics.BigInteger) 型でのみサポートされています。 

この指定子を使用して [BigInteger](xref:System.Numerics.BigInteger) 値の書式を設定すると、その文字列形式に [BigInteger](xref:System.Numerics.BigInteger) 値の有効桁数がすべて含まれます。 この指定子を使用して [Single](xref:System.Single) または [Double](xref:System.Double) 値の書式を設定すると、最初に一般書式を使用して数値がテストされます。このとき、[Double](xref:System.Double) の場合は 15 桁、[Single](xref:System.Single) の場合は 7 桁の有効桁数が使用されます。 変換後の文字列を解析して変換前の数値へ戻った場合には、一般書式指定子を使用してこの数値の書式が設定されます。 変換後の文字列が解析によって変換前の数値に戻らなかった場合、[Double](xref:System.Double) は 17 桁、[Single](xref:System.Single) は 9 桁の有効桁数でこの値の形式が設定されます。 

精度指定子は、指定できますが無視されます。 ラウンドトリップ指定子と精度指定子の両方を指定すると、ラウンドトリップ指定子が優先されます。 

結果文字列は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、結果文字列の書式を制御する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) プロパティの一覧を示します。

NumberFormatInfo のプロパティ | 説明
------------------------- | -----------
[NegativeSign](xref:System.Globalization.NumberFormatInfo.NegativeSign) | 数値が負であることを示す文字列を定義します。
[NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) | 整数部と小数部を区切る文字列を定義します。
[PositiveSign](xref:System.Globalization.NumberFormatInfo.PositiveSign) | 指数部が正であることを示す文字列を定義します。

 次の例では、ラウンドトリップ書式指定子を使って [Double](xref:System.Double) 値の書式を設定します。

```csharp
double value;

value = Math.PI;
Console.WriteLine(value.ToString("r"));
// Displays 3.1415926535897931
Console.WriteLine(value.ToString("r", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays 3,1415926535897931
value = 1.623e-21;
Console.WriteLine(value.ToString("r"));
// Displays 1.623E-21
```

```vb
Dim value As Double

value = Math.Pi
Console.WriteLine(value.ToString("r"))
' Displays 3.1415926535897931
Console.WriteLine(value.ToString("r", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays 3,1415926535897931
value = 1.623e-21
Console.WriteLine(value.ToString("r"))
' Displays 1.623E-21
```

## <a name="the-hexadecimal-x-format-specifier"></a>16 進数 ("X") 書式指定子

16 進数 ("X") 書式指定子は、16 進数文字列に数値を変換します。 書式指定子の大文字と小文字によって、9 よりも大きい 16 進数値を示すアルファベット文字が大文字と小文字のどちらで表示されるかが決まります。 たとえば、"X" を指定すると "ABCDEF" となり、"x" を指定すると "abcdef" となります。 この書式指定は整数型でだけサポートされています。

精度指定子は、変換後の文字列の最小桁数を示します。 必要に応じて、精度指定子によって指定された桁数に達するまで、数値の左側にゼロが埋め込まれます。

結果文字列は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトの書式情報に影響されません。 

次の例では、16 進数の書式指定子を使って [Int32](xref:System.Int32) 値の書式を設定します。

```csharp
int value; 

value = 0x2045e;
Console.WriteLine(value.ToString("x"));
// Displays 2045e
Console.WriteLine(value.ToString("X"));
// Displays 2045E
Console.WriteLine(value.ToString("X8"));
// Displays 0002045E

value = 123456789;
Console.WriteLine(value.ToString("X"));
// Displays 75BCD15
Console.WriteLine(value.ToString("X2"));
// Displays 75BCD15
```

```vb
Dim value As Integer 

value = &h2045e
Console.WriteLine(value.ToString("x"))
' Displays 2045e
Console.WriteLine(value.ToString("X"))
' Displays 2045E
Console.WriteLine(value.ToString("X8"))
' Displays 0002045E

value = 123456789
Console.WriteLine(value.ToString("X"))
' Displays 75BCD15
Console.WriteLine(value.ToString("X2"))
' Displays 75BCD15
```

## <a name="notes"></a>ノート

### <a name="numberformatinfo-properties"></a>NumberFormatInfo のプロパティ

書式設定は、現在の [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトのプロパティの影響を受けます。このオブジェクトは、現在のスレッド カルチャによって暗黙的に指定されるか、または書式設定を実行するメソッドの [IFormatProvider](xref:System.IFormatProvider) パラメーターによって明示的に指定されます。 このパラメーターには、[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) または [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトを指定してください。 

### <a name="integral-and-floatingpoint-numeric-types"></a>整数数値型と浮動小数点数値型

標準の数値書式指定子の記述で、整数数値型または浮動小数点数値型が参照されている場合があります。 整数数値型には、[Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[Int32](xref:System.Int32)、[Int64](xref:System.Int64)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)、および [BigInteger](xref:System.Numerics.BigInteger) があります。 浮動小数点数値型には、[Decimal](xref:System.Decimal)、[Single](xref:System.Single)、および [Double](xref:System.Double) があります。 

### <a name="floatingpoint-infinities-and-nan"></a>浮動小数点の無限大値と NAN (非数) 値

[Single](xref:System.Single) または [Double](xref:System.Double) 浮動小数点型の値が正の無限大、負の無限大、または NaN (非数) である場合は、書式指定文字列とは関係なく、現在適用可能な [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトによって指定される [PositiveInfinitySymbol](xref:System.Globalization.NumberFormatInfo.PositiveInfinitySymbol)、[NegativeInfinitySymbol](xref:System.Globalization.NumberFormatInfo.NegativeInfinitySymbol)、または [NaNSymbol](xref:System.Globalization.NumberFormatInfo.NaNSymbol) の各プロパティの値は、書式設定された文字列となります。

## <a name="example"></a>例

次の例では、en-US カルチャおよびすべての標準数値書式指定子を使用して、整数値と浮動小数点数値を書式設定します。 この例では 2 つの特定の数値型 ([Double](xref:System.Double) および [Int32](xref:System.Int32)) を使用していますが、他の数値基本型 ([Byte](xref:System.Byte)、[SByte](xref:System.SByte)、[Int16](xref:System.Int16)、[Int64](xref:System.Int64)、[UInt16](xref:System.UInt16)、[UInt32](xref:System.UInt32)、[UInt64](xref:System.UInt64)、[BigInteger](xref:System.Numerics.BigInteger)、[Decimal](xref:System.Decimal)、および [Single](xref:System.Single)) でも類似した結果が得られます。 

```csharp
using System;
using System.Globalization;
using System.Threading;

public class NumericFormats
{
   public static void Main()
   {
      // Display string representations of numbers for en-us culture
      CultureInfo ci = new CultureInfo("en-us");

      // Output floating point values
      double floating = 10761.937554;
      Console.WriteLine("C: {0}", 
              floating.ToString("C", ci));           // Displays "C: $10,761.94"
      Console.WriteLine("E: {0}", 
              floating.ToString("E03", ci));         // Displays "E: 1.076E+004"
      Console.WriteLine("F: {0}", 
              floating.ToString("F04", ci));         // Displays "F: 10761.9376"         
      Console.WriteLine("G: {0}",  
              floating.ToString("G", ci));           // Displays "G: 10761.937554"
      Console.WriteLine("N: {0}", 
              floating.ToString("N03", ci));         // Displays "N: 10,761.938"
      Console.WriteLine("P: {0}", 
              (floating/10000).ToString("P02", ci)); // Displays "P: 107.62 %"
      Console.WriteLine("R: {0}", 
              floating.ToString("R", ci));           // Displays "R: 10761.937554"            
      Console.WriteLine();

      // Output integral values
      int integral = 8395;
      Console.WriteLine("C: {0}", 
              integral.ToString("C", ci));           // Displays "C: $8,395.00"
      Console.WriteLine("D: {0}", 
              integral.ToString("D6", ci));          // Displays "D: 008395" 
      Console.WriteLine("E: {0}", 
              integral.ToString("E03", ci));         // Displays "E: 8.395E+003"
      Console.WriteLine("F: {0}", 
              integral.ToString("F01", ci));         // Displays "F: 8395.0"    
      Console.WriteLine("G: {0}",  
              integral.ToString("G", ci));           // Displays "G: 8395"
      Console.WriteLine("N: {0}", 
              integral.ToString("N01", ci));         // Displays "N: 8,395.0"
      Console.WriteLine("P: {0}", 
              (integral/10000.0).ToString("P02", ci)); // Displays "P: 83.95 %"
      Console.WriteLine("X: 0x{0}", 
              integral.ToString("X", ci));           // Displays "X: 0x20CB"
      Console.WriteLine();
   }
}
```

```vb
Option Strict On

Imports System.Globalization
Imports System.Threading

Module NumericFormats
   Public Sub Main()
      ' Display string representations of numbers for en-us culture
      Dim ci As New CultureInfo("en-us")

      ' Output floating point values
      Dim floating As Double = 10761.937554
      Console.WriteLine("C: {0}", _
              floating.ToString("C", ci))           ' Displays "C: $10,761.94"
      Console.WriteLine("E: {0}", _
              floating.ToString("E03", ci))         ' Displays "E: 1.076E+004"
      Console.WriteLine("F: {0}", _
              floating.ToString("F04", ci))         ' Displays "F: 10761.9376"         
      Console.WriteLine("G: {0}", _ 
              floating.ToString("G", ci))           ' Displays "G: 10761.937554"
      Console.WriteLine("N: {0}", _
              floating.ToString("N03", ci))         ' Displays "N: 10,761.938"
      Console.WriteLine("P: {0}", _
              (floating/10000).ToString("P02", ci)) ' Displays "P: 107.62 %"
      Console.WriteLine("R: {0}", _
              floating.ToString("R", ci))           ' Displays "R: 10761.937554"            
      Console.WriteLine()

      ' Output integral values
      Dim integral As Integer = 8395
      Console.WriteLine("C: {0}", _
              integral.ToString("C", ci))           ' Displays "C: $8,395.00"
      Console.WriteLine("D: {0}", _
              integral.ToString("D6"))              ' Displays "D: 008395" 
      Console.WriteLine("E: {0}", _
              integral.ToString("E03", ci))         ' Displays "E: 8.395E+003"
      Console.WriteLine("F: {0}", _
              integral.ToString("F01", ci))         ' Displays "F: 8395.0"    
      Console.WriteLine("G: {0}", _ 
              integral.ToString("G", ci))           ' Displays "G: 8395"
      Console.WriteLine("N: {0}", _
              integral.ToString("N01", ci))         ' Displays "N: 8,395.0"
      Console.WriteLine("P: {0}", _
              (integral/10000).ToString("P02", ci)) ' Displays "P: 83.95 %"
      Console.WriteLine("X: 0x{0}", _
              integral.ToString("X", ci))           ' Displays "X: 0x20CB"
      Console.WriteLine()
   End Sub
End Module
```

## <a name="see-also"></a>関連項目

[System.Globalization.NumberFormatInfo](xref:System.Globalization.NumberFormatInfo)

[カスタム数値書式指定文字列](custom-numeric.md)

[型の書式設定](formatting-types.md)

[方法: 数値に先行するゼロを埋め込む](pad-number.md)

[複合書式指定](composite-format.md)



<!--HONumber=Nov16_HO1-->


