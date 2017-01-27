---
title: ".NET での数値文字列の解析"
description: ".NET での数値文字列の解析"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e393430a-731a-49fa-83de-ff7ed52d5704
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 209d24d32eb3b235ff2fde2ef11ffd0ee4e930cf

---

# <a name="parsing-numeric-strings-in-net"></a>.NET での数値文字列の解析

すべての数値型には、2 つの静的解析メソッド (`Parse` と `TryParse`) があり、数字の文字列形式を数値型に変換するために使用できます。 これらのメソッドでは、[標準の数値書式指定文字列](standard-numeric.md)と[カスタム数値書式指定文字列](custom-numeric.md)で記述されている書式指定文字列を使用して、生成された文字列を解析できます。 既定では、`Parse` と `TryParse` メソッドは、10 進数の整数を含む文字列を整数値のみに正常に変換することができます。 これらのメソッドは、整数部と小数部、グループ区切り、および小数点記号を含む文字列を浮動小数点値に正常に変換できます。 `TryParse` メソッドが `false` を返すのに対して、`Parse` メソッドは操作が失敗した場合に例外をスローします。

## <a name="parsing-and-format-providers"></a>解析と書式プロバイダー

通常、数値の文字列形式はカルチャによって異なります。 通貨記号、グループ (または千単位) 区切り、および小数点記号などの数値文字列の要素は、カルチャによって大きく異なります。 暗黙的または明示的のいずれかの解析メソッドでは、これらのカルチャ固有のバリエーションを認識する書式プロバイダーを使用します。 書式プロバイダーが `Parse` または `TryParse` メソッドの呼び出しで指定されない場合、現在のスレッド カルチャ ([NumberFormatInfo.CurrentInfo](xref:System.Globalization.NumberFormatInfo.CurrentInfo) プロパティで返された [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクト) と関連付けられた書式プロバイダーが使用されます。 

書式プロバイダーは、[IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) 実装によって示されます。 このインターフェイスには、1 つのメンバー ([GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) メソッド) があり、その 1 つのパラメーターは、書式設定される型を示す [Type](xref:System.Type) オブジェクトです。 このメソッドは、書式情報を示すオブジェクトを返します。 .NET では、数値文字列を解析するために、次の 2 つの [IFormatProvider](xref:System.Globalization.NumberFormatInfo.CurrentInfo) の実装をサポートします。

* [CultureInfo.GetFormat](xref:System.Globalization.CultureInfo.GetFormat(System.Type)) メソッドが、カルチャ固有の書式情報を提供する [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを返す、[CultureInfo](xref:System.Globalization.CultureInfo) オブジェクト。

* [NumberFormatInfo.GetFormat](xref:System.Globalization.NumberFormatInfo.GetFormat(System.Type)) メソッドがそれ自体を返す、[NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクト。

次の例では、配列内の各文字列を [Double](xref:System.Double) 値に変換しようとします。 最初に、英語 (米国) カルチャの規則を反映する書式プロバイダーを使用して、文字列を解析しようとします。 この操作が [FormatException](xref:System.FormatException) をスローする場合、フランス語 (フランス) カルチャの規則を反映する書式プロバイダーを使用して、文字列を解析しようとしています。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] values = { "1,304.16", "$1,456.78", "1,094", "152", 
                          "123,45 €", "1 304,16", "Ae9f" };
      double number;
      CultureInfo culture = null;

      foreach (string value in values) {
         try {
            culture = CultureInfo.CreateSpecificCulture("en-US");
            number = Double.Parse(value, culture);
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
         }   
         catch (FormatException) {
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value);
            culture = CultureInfo.CreateSpecificCulture("fr-FR");
            try {
               number = Double.Parse(value, culture);
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number);
            }
            catch (FormatException) {
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value);
            }
         }
         Console.WriteLine();
      }   
   }
}
// The example displays the following output:
//    en-US: 1,304.16 --> 1304.16
//    
//    en-US: Unable to parse '$1,456.78'.
//    fr-FR: Unable to parse '$1,456.78'.
//    
//    en-US: 1,094 --> 1094
//    
//    en-US: 152 --> 152
//    
//    en-US: Unable to parse '123,45 €'.
//    fr-FR: Unable to parse '123,45 €'.
//    
//    en-US: Unable to parse '1 304,16'.
//    fr-FR: 1 304,16 --> 1304.16
//    
//    en-US: Unable to parse 'Ae9f'.
//    fr-FR: Unable to parse 'Ae9f'.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim values() As String = { "1,304.16", "$1,456.78", "1,094", "152", 
                                 "123,45 €", "1 304,16", "Ae9f" }
      Dim number As Double
      Dim culture As CultureInfo = Nothing

      For Each value As String In values
         Try
            culture = CultureInfo.CreateSpecificCulture("en-US")
            number = Double.Parse(value, culture)
            Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
         Catch e As FormatException
            Console.WriteLine("{0}: Unable to parse '{1}'.", 
                              culture.Name, value)
            culture = CultureInfo.CreateSpecificCulture("fr-FR")
            Try
               number = Double.Parse(value, culture)
               Console.WriteLine("{0}: {1} --> {2}", culture.Name, value, number)
            Catch ex As FormatException
               Console.WriteLine("{0}: Unable to parse '{1}'.", 
                                 culture.Name, value)
            End Try
         End Try
         Console.WriteLine()
      Next
   End Sub
End Module
' The example displays the following output:
'    en-US: 1,304.16 --> 1304.16
'    
'    en-US: Unable to parse '$1,456.78'.
'    fr-FR: Unable to parse '$1,456.78'.
'    
'    en-US: 1,094 --> 1094
'    
'    en-US: 152 --> 152
'    
'    en-US: Unable to parse '123,45 €'.
'    fr-FR: Unable to parse '123,45 €'.
'    
'    en-US: Unable to parse '1 304,16'.
'    fr-FR: 1 304,16 --> 1304.16
'    
'    en-US: Unable to parse 'Ae9f'.
'    fr-FR: Unable to parse 'Ae9f'.
```

## <a name="parsing-and-numberstyles-values"></a>解析と NumberStyles 値

解析操作が処理できるスタイル要素 (空白文字、グループ区切り、小数点の記号など) は、[NumberStyles](xref:System.Globalization.NumberStyles) 列挙値によって定義されます。 既定では、整数値を表す文字列は、[NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) 値を使用して解析されます。これは、数値、先頭と末尾の空白、および先頭の符号のみを許可します。 浮動小数点値を表す文字列は、[NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) と [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) 値の組み合わせを使用して解析されます。この複合スタイルは、先頭と末尾の空白、先頭の符号、小数点記号、グループ区切り、および指数と共に 10 進数を許可します。 [NumberStyles](xref:System.Globalization.NumberStyles) 型のパラメーターを含む、`Parse` または `TryParse` メソッドのオーバーロードを呼び出し、1 つ以上の [NumberStyles](xref:System.Globalization.NumberStyles) フラグを設定すると、解析操作が成功するように、文字列で示すことができるスタイル要素を制御することができます。 

たとえば、グループ区切りを含む文字列は、[Int32.Parse(String)](xref:System.Int32.Parse(System.String)) メソッドを使用して、[Int32](xref:System.Int32) 値に変換することはできません。 ただし、次の例に示すように、[NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) フラグを使用した場合、この変換は成功します。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string value = "1,304";
      int number;
      IFormatProvider provider = CultureInfo.CreateSpecificCulture("en-US");
      if (Int32.TryParse(value, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);

      if (Int32.TryParse(value, NumberStyles.Integer | NumberStyles.AllowThousands, 
                        provider, out number))
         Console.WriteLine("{0} --> {1}", value, number);
      else
         Console.WriteLine("Unable to convert '{0}'", value);
   }
}
// The example displays the following output:
//       Unable to convert '1,304'
//       1,304 --> 1304
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim value As String = "1,304"
      Dim number As Integer
      Dim provider As IFormatProvider = CultureInfo.CreateSpecificCulture("en-US")
      If Int32.TryParse(value, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If

      If Int32.TryParse(value, NumberStyles.Integer Or NumberStyles.AllowThousands, 
                        provider, number) Then
         Console.WriteLine("{0} --> {1}", value, number)
      Else
         Console.WriteLine("Unable to convert '{0}'", value)
      End If
   End Sub
End Module
' The example displays the following output:
'       Unable to convert '1,304'
'       1,304 --> 1304
```

> **警告**
>
> 解析操作は、常に特定のカルチャの書式規則を使用します。 [CultureInfo](xref:System.Globalization.CultureInfo) または [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) オブジェクトを渡してカルチャを指定しない場合、現在のスレッドに関連付けられているカルチャが使用されます。
 
次の表では、[NumberStyles](xref:System.Globalization.NumberStyles) 列挙体のメンバーを一覧し、そのメンバーが解析操作に与える影響について説明します。

NumberStyles 値 | 解析する文字列への影響
------------------ | --------------------------------- 
[NumberStyles.None](xref:System.Globalization.NumberStyles.None) | 数字のみが許可されます。
[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint) | 小数点の記号と桁数が許可されます。 整数値の場合、0 のみが小数点の桁数として許可されます。 有効な小数点記号は、[NumberFormatInfo.NumberDecimalSeparator](xref:System.Globalization.NumberFormatInfo.NumberDecimalSeparator) または [NumberFormatInfo.CurrencyDecimalSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyDecimalSeparator) プロパティによって決定されます。
[NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) | "e" または "E" の文字は、指数表記を示すために使用できます。
[NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite) | 先頭の空白が許可されます。
[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite) | 末尾の空白が許可されます。
[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) | 正または負の符号には、数字の先頭に追加できます。
[NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign) | 正または負の符号は、数字の後に続けることができます。
[NumberStyles.AllowParentheses](xref:System.Globalization.NumberStyles.AllowParentheses) | かっこは、負の符号を示すために使用できます。
[NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) | グループ区切りが許可されます。 グループ区切りは、[NumberFormatInfo.NumberGroupSeparator](xref:System.Globalization.NumberFormatInfo.NumberGroupSeparator) または [NumberFormatInfo.CurrencyGroupSeparator](xref:System.Globalization.NumberFormatInfo.CurrencyGroupSeparator) プロパティによって決定されます。
[NumberStyles.AllowCurrencySymbol](xref:System.Globalization.NumberStyles.AllowCurrencySymbol) | 通貨記号が許可されます。 通貨記号は、[NumberFormatInfo.CurrencySymbol](xref:System.Globalization.NumberFormatInfo.CurrencySymbol) プロパティによって定義されます。
[NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) | 解析する文字列は、16 進数として解釈されます。 これには、16 進数の値の 0 ～ 9、A ～ F、a ～ f を含めることができます。 このフラグは、整数値を解析するためにだけに使用できます。
 
さらに、[NumberStyles](xref:System.Globalization.NumberStyles) 列挙体は、複数の [NumberStyles](xref:System.Globalization.NumberStyles) フラグを含む、次の複合スタイルを指定します。 

複合 NumberStyles 値 | 数値を含む
---------------------------- | ---------------- 
[NumberStyles.Integer](xref:System.Globalization.NumberStyles.Integer) | [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、および [NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign) のスタイルを含みます。 これは、整数値を解析するために使用される既定のスタイルです。
[NumberStyles.Number](xref:System.Globalization.NumberStyles.Number) | [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign)、[NumberStyles.AllowTrailingSign](xref:System.Globalization.NumberStyles.AllowTrailingSign)、[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint)、および [NumberStyles.AllowThousands](xref:System.Globalization.NumberStyles.AllowThousands) のスタイルを含みます。
[NumberStyles.Float](xref:System.Globalization.NumberStyles.Float) | [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、[NumberStyles.AllowLeadingSign](xref:System.Globalization.NumberStyles.AllowLeadingSign)、[NumberStyles.AllowDecimalPoint](xref:System.Globalization.NumberStyles.AllowDecimalPoint)、および [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) のスタイルを含みます。
[NumberStyles.Currency](xref:System.Globalization.NumberStyles.Currency) | [NumberStyles.AllowExponent](xref:System.Globalization.NumberStyles.AllowExponent) および [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) を除く、すべてのスタイルを含みます。
[NumberStyles.Any](xref:System.Globalization.NumberStyles.Any) | [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) を除く、すべてのスタイルを含みます。
[NumberStyles.HexNumber](xref:System.Globalization.NumberStyles.HexNumber) | [NumberStyles.AllowLeadingWhite](xref:System.Globalization.NumberStyles.AllowLeadingWhite)、[NumberStyles.AllowTrailingWhite](xref:System.Globalization.NumberStyles.AllowTrailingWhite)、および [NumberStyles.AllowHexSpecifier](xref:System.Globalization.NumberStyles.AllowHexSpecifier) のスタイルを含みます。
 
## <a name="parsing-and-unicode-digits"></a>解析と Unicode 数字

Unicode 標準では、さまざまな書記体系で数字のコード ポイントを定義します。 たとえば、U+0030 ～ U+0039 のコード ポイントは、0 ～ 9 の基本ラテンの数字を示し、U+09E6 ～ U+09EF のコード ポイントは、0 ～ 9 の数字のバングラ語の数字を示し、U+FF10 ～ U+FF19 のコード ポイントは、0 ～ 9 の全角の数字を示します。 ただし、解析メソッドで認識される数字は、U+0030 ～ U+0039 のコード ポイントの基本ラテンの数字 0 ～ 9 のみです。 数値解析メソッドがその他の数字を含む文字列を渡す場合、メソッドは [FormatException](xref:System.FormatException) をスローします。

次の例では、[Int32.Parse](xref:System.Int32.Parse(System.String)) メソッドを使用して、異なる書記体系の数字で構成される文字列を解析します。 例の出力に示されているように、基本ラテンの数字を解析する試行は成功しますが、全角、アラビア インド、バングラ語の数字を解析する試行は失敗します。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string value;
      // Define a string of basic Latin digits 1-5.
      value = "\u0031\u0032\u0033\u0034\u0035";
      ParseDigits(value);

      // Define a string of Fullwidth digits 1-5.
      value = "\uFF11\uFF12\uFF13\uFF14\uFF15";
      ParseDigits(value);

      // Define a string of Arabic-Indic digits 1-5.
      value = "\u0661\u0662\u0663\u0664\u0665";
      ParseDigits(value);

      // Define a string of Bangla digits 1-5.
      value = "\u09e7\u09e8\u09e9\u09ea\u09eb";
      ParseDigits(value);
   }

   static void ParseDigits(string value)
   {
      try {
         int number = Int32.Parse(value);
         Console.WriteLine("'{0}' --> {1}", value, number);
      }   
      catch (FormatException) {
         Console.WriteLine("Unable to parse '{0}'.", value);      
      }     
   }
}
// The example displays the following output:
//       '12345' --> 12345
//       Unable to parse '１２３４５'.
//       Unable to parse '١٢٣٤٥'.
//       Unable to parse '১২৩৪৫'.
```

```vb
Module Example
   Public Sub Main()
      Dim value As String
      ' Define a string of basic Latin digits 1-5.
      value = ChrW(&h31) + ChrW(&h32) + ChrW(&h33) + ChrW(&h34) + ChrW(&h35)
      ParseDigits(value)

      ' Define a string of Fullwidth digits 1-5.
      value = ChrW(&hff11) + ChrW(&hff12) + ChrW(&hff13) + ChrW(&hff14) + ChrW(&hff15)
      ParseDigits(value)

      ' Define a string of Arabic-Indic digits 1-5.
      value = ChrW(&h661) + ChrW(&h662) + ChrW(&h663) + ChrW(&h664) + ChrW(&h665)
      ParseDigits(value)

      ' Define a string of Bangla digits 1-5.
      value = ChrW(&h09e7) + ChrW(&h09e8) + ChrW(&h09e9) + ChrW(&h09ea) + ChrW(&h09eb)
      ParseDigits(value)
   End Sub

   Sub ParseDigits(value As String)
      Try
         Dim number As Integer = Int32.Parse(value)
         Console.WriteLine("'{0}' --> {1}", value, number)
      Catch e As FormatException
         Console.WriteLine("Unable to parse '{0}'.", value)      
      End Try     
   End Sub
End Module
' The example displays the following output:
'       '12345' --> 12345
'       Unable to parse '１２３４５'.
'       Unable to parse '١٢٣٤٥'.
'       Unable to parse '১২৩৪৫'.
```

## <a name="see-also"></a>関連項目

[System.Globalization.NumberStyles](xref:System.Globalization.NumberStyles)

[.NET での文字列の解析](parsing-strings.md)

[.NET での型の書式設定](formatting-types.md)




<!--HONumber=Nov16_HO3-->


