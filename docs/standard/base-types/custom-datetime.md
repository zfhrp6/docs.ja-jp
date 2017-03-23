---
title: "カスタム日時書式指定文字列"
description: "カスタム日時書式指定文字列"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 45f286f5-92c9-4150-957c-fa6d394bc29b
translationtype: Human Translation
ms.sourcegitcommit: 28625def4199a660fe0ea04ab75f4f65d2e0c9c4
ms.openlocfilehash: 285e4bfd6a53d576ce4538b09a2561065c93e399
ms.lasthandoff: 02/23/2017

---

# <a name="custom-date-and-time-format-strings"></a>カスタム日時書式指定文字列

日時書式指定文字列は、[DateTime](xref:System.DateTime) 値または [DateTimeOffset](xref:System.DateTimeOffset) 値の書式設定操作によって生成されるテキスト表現を定義します。 また、文字列を日時に正常に変換するために解析操作で必要となる日時値の表現も定義します。 カスタム書式指定文字列は、1 つ以上のカスタム日時書式指定子で構成されます。 [標準の日時書式指定文字列](standard-datetime.md)以外の文字列は、すべてカスタム日時書式指定文字列として解釈されます。 

カスタム日時書式指定文字列は、[DateTime](xref:System.DateTime) 値で使用することも、[DateTimeOffset](xref:System.DateTimeOffset) 値で使用することもできます。

書式設定操作では、日時インスタンスの `ToString` メソッドまたは複合書式指定をサポートするメソッドで、カスタム日時書式指定文字列を使用できます。 両方の使用例を次に示します。 

```csharp
DateTime thisDate1 = new DateTime(2011, 6, 10);
Console.WriteLine("Today is " + thisDate1.ToString("MMMM dd, yyyy") + ".");

DateTimeOffset thisDate2 = new DateTimeOffset(2011, 6, 10, 15, 24, 16, 
                                              TimeSpan.Zero);
Console.WriteLine("The current date and time: {0:MM/dd/yy H:mm:ss zzz}", 
                   thisDate2); 
// The example displays the following output:
//    Today is June 10, 2011.
//    The current date and time: 06/10/11 15:24:16 +00:00
```

```vb
Dim thisDate1 As Date = #6/10/2011#
Console.WriteLine("Today is " + thisDate1.ToString("MMMM dd, yyyy") + ".")

Dim thisDate2 As New DateTimeOffset(2011, 6, 10, 15, 24, 16, TimeSpan.Zero)
Console.WriteLine("The current date and time: {0:MM/dd/yy H:mm:ss zzz}", 
                   thisDate2) 
' The example displays the following output:
'    Today is June 10, 2011.
'    The current date and time: 06/10/11 15:24:16 +00:00
```

解析操作では、[DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider))、[DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@))、[DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider))、および [DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) の各メソッドで、カスタム日時書式指定文字列を使用できます。 これらのメソッドでは、解析操作が成功するための特定のパターンに入力文字列が完全に一致している必要があります。 日付に日、月、2 桁の年が含まれているかどうかを解析する [DateTimeOffset.ParseExact(String, String, IFormatProvider)](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) メソッドを呼び出す例を次に示します。

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      string[] dateValues = { "30-12-2011", "12-30-2011", 
                              "30-12-11", "12-30-11" };
      string pattern = "MM-dd-yy";
      DateTime parsedDate;

      foreach (var dateValue in dateValues) {
         if (DateTime.TryParseExact(dateValue, pattern, null, 
                                   DateTimeStyles.None, out parsedDate))
            Console.WriteLine("Converted '{0}' to {1:d}.", 
                              dateValue, parsedDate);
         else
            Console.WriteLine("Unable to convert '{0}' to a date and time.", 
                              dateValue);
      }
   }
}
// The example displays the following output:
//    Unable to convert '30-12-2011' to a date and time.
//    Unable to convert '12-30-2011' to a date and time.
//    Unable to convert '30-12-11' to a date and time.
//    Converted '12-30-11' to 12/30/2011.
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim dateValues() As String = { "30-12-2011", "12-30-2011", 
                                      "30-12-11", "12-30-11" }
      Dim pattern As String = "MM-dd-yy"
      Dim parsedDate As Date

      For Each dateValue As String In dateValues
         If DateTime.TryParseExact(dateValue, pattern, Nothing, 
                                   DateTimeStyles.None, parsedDate) Then
            Console.WriteLine("Converted '{0}' to {1:d}.", 
                              dateValue, parsedDate)
         Else
            Console.WriteLine("Unable to convert '{0}' to a date and time.", 
                              dateValue)
         End If                                                         
      Next
   End Sub
End Module
' The example displays the following output:
'    Unable to convert '30-12-2011' to a date and time.
'    Unable to convert '12-30-2011' to a date and time.
'    Unable to convert '30-12-11' to a date and time.
'    Converted '12-30-11' to 12/30/2011.
```

次の表に、カスタム日時書式指定子の説明および書式指定子ごとの書式設定後の文字列を示します。 既定では、結果の文字列は、en-US カルチャの書式指定規則を反映します。 特定の書式指定子でローカライズされた文字列が書式設定後に生成される場合、例には書式設定後の文字列が適用されるカルチャも示されます。 カスタム日時書式指定文字列の使用方法については、「メモ」を参照してください。

書式指定子 | 説明 | 例
---------------- | ----------- | --------
"d" | 月の日にち (1 ～ 31)。 | `2019-06-01T13:45:30 -> 1`; `2019-06-15T13:45:30 -> 15`
"dd" | 月の日にち (01 ～ 31)。 | `2019-06-01T13:45:30 -> 1`; `2019-06-15T13:45:30 -> 15`
"ddd" | 曜日の省略名。 | `2019-06-15T13:45:30 -> Mon (en-US)`; `2019-06-15T13:45:30 -> Пн (ru-RU)`; `2019-06-15T13:45:30 -> lun. (fr-FR)`
"dddd" | 曜日の完全名。 | `2019-06-15T13:45:30 -> Monday (en-US)`; `2019-06-15T13:45:30 -> понедельник (ru-RU)`; `2019-06-15T13:45:30 -> lundi (fr-FR)`
"f" | 日時値の秒部分の&1;/10。 | `2019-06-15T13:45:30.6170000 -> 6`; `2019-06-15T13:45:30.05 -> 0` 
"ff" | 日時値の秒部分の&1;/100。 | `2019-06-15T13:45:30.6170000 -> 61`; `2019-06-15T13:45:30.0050000 -> 00`
"fff" | 日時値の秒部分の&1;/1000。 | `6/15/2019 13:45:30.617 -> 617`; `6/15/2019 13:45:30.0005 -> 000`
"ffff" | 日時値の秒部分の&1;/10000。 | `2019-06-15T13:45:30.6175000 -> 6175`; `2019-06-15T13:45:30.0000500 -> 0000`
"fffff" | 日時値の秒部分の&1;/100000。 | `2019-06-15T13:45:30.6175400 -> 61754`; `6/15/2019 13:45:30.000005 -> 00000`
"ffffff" | 日時値の秒部分の&1;/1000000。 | `2019-06-15T13:45:30.6175420 -> 617542`; `2019-06-15T13:45:30.0000005 -> 000000`
"fffffff" | 日時値の秒部分の&1;/10000000。 | `2019-06-15T13:45:30.6175425 -> 6175425`;`2019-06-15T13:45:30.0001150 -> 0001150`
"F" | 日時値の秒部分の&1;/10 (0 以外の場合)。 | `2019-06-15T13:45:30.6170000 -> 6`; `2019-06-15T13:45:30.0500000 -> (no output)`
"FF" | 日時値の秒部分の&1;/100 (0 以外の場合)。 | `2019-06-15T13:45:30.6170000 -> 61`; `2019-06-15T13:45:30.0050000 -> (no output)`
"FFF" | 日時値の秒部分の&1;/1000 (0 以外の場合)。 | `2019-06-15T13:45:30.6170000 -> 617`; `2019-06-15T13:45:30.0005000 -> (no output)`
"FFFF" | 日時値の秒部分の&1;/10000 (0 以外の場合)。 | `2019-06-15T13:45:30.5275000 -> 5275`; `2019-06-15T13:45:30.0000500 -> (no output)`
"FFFFF" | 日時値の秒部分の&1;/100000 (0 以外の場合)。 | `2019-06-15T13:45:30.6175400 -> 61754`; `2019-06-15T13:45:30.0000050 -> (no output)`
"FFFFFF" | 日時値の秒部分の&1;/1000000 (0 以外の場合)。 | `2019-06-15T13:45:30.6175420 -> 617542`; `2019-06-15T13:45:30.0000005 -> (no output)`
"FFFFFFF" | 日時値の秒部分の&1;/10000000 (0 以外の場合)。 | `2019-06-15T13:45:30.6175425 -> 6175425`; `2019-06-15T13:45:30.0001150 -> 000115`
"g"、"gg" | 時期または時代 (年号)。 | `2019-06-15T13:45:30.6170000 -> A.D.`
"h" | 12 時間形式の時間 (1 ～ 12)。 | `2019-06-15T01:45:30 -> 1`; `2019-06-15T13:45:30 -> 1`
"hh" | 12 時間形式の時間 (01 ～ 12)。 | `2019-06-15T01:45:30 -> 01`; `2019-06-15T13:45:30 -> 01`
"H" | 24 時間形式の時間 (0 ～ 23)。 | `2019-06-15T01:45:30 -> 1`; `2019-06-15T13:45:30 -> 13`
"HH" | 24 時間形式の時間 (00 ～ 23)。 | `2019-06-15T01:45:30 -> 01`; `2019-06-15T13:45:30 -> 13`
"K" | タイム ゾーン情報。 | [DateTime](xref:System.DateTime) 値の場合: `2019-06-15T13:45:30, Kind Unspecified ->`、`2019-06-15T13:45:30, Kind Utc -> Z`、`2019-06-15T13:45:30, Kind Local -> -07:00 (depends on local computer settings)` [DateTimeOffset](xref:System.DateTimeOffset) 値の場合: `2019-06-15T01:45:30-07:00 --> -07:00`、`2019-06-15T08:45:30+00:00 --> +00:00`
"m" | 分 (0 ～ 59)。 | `2019-06-15T01:09:30 -> 9`; `2019-06-15T13:29:30 -> 29`
"mm" | 分 (00 ～ 59)。 | `2019-06-15T01:09:30 -> 09`; `2019-06-15T01:45:30 -> 45`
"M" | 月 (1 ～ 12)。 | `2019-06-15T13:45:30 -> 6`
"MM" | 月 (01 ～ 12)。 | `2019-06-15T13:45:30 -> 06`
"MMM" | 月の省略名。 | `2019-06-15T13:45:30 -> Jun (en-US)`; `2019-06-15T13:45:30 -> juin (fr-FR)`; `2019-06-15T13:45:30 -> Jun (zu-ZA)`
"MMMM" | 月の完全名。 | `2019-06-15T13:45:30 -> June (en-US)`; `2019-06-15T13:45:30 -> juni (da-DK)`; `2019-06-15T13:45:30 -> uJuni (zu-ZA)`
"s" | 秒 (0 ～ 59)。 | `2019-06-15T13:45:09 -> 9`
"ss" | 秒 (00 ～ 59)。 | `2019-06-15T13:45:09 -> 09`
"t" | AM/PM 指定子の最初の文字。 | `2019-06-15T13:45:30 -> P (en-US)`; `2019-06-15T13:45:30 -> 午 (ja-JP)`; `2019-06-15T13:45:30 -> (fr-FR)`
"tt" | AM/PM 指定子。 | `2019-06-15T13:45:30 -> PM (en-US)`; `2019-06-15T13:45:30 -> 午後 (ja-JP)`; `2019-06-15T13:45:30 -> (fr-FR)`
"y" | 年 (0 ～ 99)。 | `0001-01-01T00:00:00 -> 1`; `0900-01-01T00:00:00 -> 0`; `1900-01-01T00:00:00 -> 0`; `2019-06-15T13:45:30 -> 9`; `2019-06-15T13:45:30 -> 19`
"yy" | 年 (00 ～ 99)。 | `0001-01-01T00:00:00 -> 01`; `0900-01-01T00:00:00 -> 00`; `1900-01-01T00:00:00 -> 00`; `2019-06-15T13:45:30 -> 19`
"yyy" | 年 (3 桁以上)。 | `0001-01-01T00:00:00 -> 001`; `0900-01-01T00:00:00 -> 900`; `1900-01-01T00:00:00 -> 1900`; `2019-06-15T13:45:30 -> 2019`
"yyyy" | 年 (4 桁の数値)。 | `0001-01-01T00:00:00 -> 0001`; `0900-01-01T00:00:00 -> 0900`; `1900-01-01T00:00:00 -> 1900`; `2019-06-15T13:45:30 -> 2019`
"yyyyy" | 年 (5 桁の数値)。 | `0001-01-01T00:00:00 -> 00001`; `2019-06-15T13:45:30 -> 02019`
"z" | UTC を基準とする時間単位のオフセット (先行ゼロなし)。 | `2019-06-15T13:45:30-07:00 -> -7`
"zz" | UTC を基準とする時間単位のオフセット (先行ゼロ付きの&1; 桁の値)。 | `2019-06-15T13:45:30-07:00 -> -07`
"zzz" | UTC を基準とする時間および分単位のオフセット。 | `2019-06-15T13:45:30-07:00 -> -07:00`
":" | 時刻の区切り記号。 | `2019-06-15T13:45:30 -> : (en-US)`; `2019-06-15T13:45:30 -> . (it-IT)`; `2019-06-15T13:45:30 -> : (ja-JP)`
"/" | 日付の区切り記号。 | `2019-06-15T13:45:30 -> / (en-US)`; `2019-06-15T13:45:30 -> - (ar-DZ)`; `2019-06-15T13:45:30 -> . (tr-TR)`
"string", 'string' | リテラル文字列の区切り記号。 | `2019-06-15T13:45:30 ("arr:" h:m t) -> arr: 1:45 P`; `2019-06-15T13:45:30 ('arr:' h:m t) -> arr: 1:45 P`
% | 後続の文字をカスタム書式指定子として定義します。 | `2019-06-15T13:45:30 (%h) -> 1`
\ | エスケープ文字。 | `2019-06-15T13:45:30 (h \h) -> 1 h`
その他の文字 | 文字が結果の文字列にそのままコピーされます。 | `2019-06-15T01:45:30 (arr hh:mm t) -> arr 01:45 A`

以降では、それぞれのカスタム日時書式指定子について詳しく説明します。 特に明記されない限り、各指定子は、[DateTime](xref:System.DateTime) 値で使用しても、[DateTimeOffset](xref:System.DateTimeOffset) 値で使用してもまったく同じ文字列形式を生成します。 

## <a name="the-d-custom-format-specifier"></a>"d" カスタム書式指定子

"d" カスタム書式指定子は、月の日にちを 1 ～ 31 の数値として表します。 1 桁の日にちは、先行ゼロなしで書式設定されます。 

"d" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"d" は標準の日時書式指定子として解釈されます。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

次の例では、複数の書式指定文字列の中に "d" カスタム書式指定子が含まれます。 

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15); 

Console.WriteLine(date1.ToString("d, M", 
                  CultureInfo.InvariantCulture)); 
// Displays 29, 8

Console.WriteLine(date1.ToString("d MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays 29 August
Console.WriteLine(date1.ToString("d MMMM", 
                  CultureInfo.CreateSpecificCulture("es-MX")));
// Displays 29 agosto  
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("d, M", _
                  CultureInfo.InvariantCulture)) 
' Displays 29, 8

Console.WriteLine(date1.ToString("d MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays 29 August
Console.WriteLine(date1.ToString("d MMMM", _
                  CultureInfo.CreateSpecificCulture("es-MX")))
' Displays 29 agosto 
```

## <a name="the-dd-custom-format-specifier"></a>"dd" カスタム書式指定子

"dd" カスタム書式指定文字列は、月の日にちを 01 ～ 31 の数値として表します。 1 桁の日にちは、先行ゼロ付きで書式設定されます。 

次の例では、カスタム書式指定文字列の中に "dd" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 1, 2, 6, 30, 15);

Console.WriteLine(date1.ToString("dd, MM", 
                  CultureInfo.InvariantCulture)); 
// 02, 01
```

```vb
Dim date1 As Date = #1/2/2008 6:30:15AM#

Console.WriteLine(date1.ToString("dd, MM", _
                  CultureInfo.InvariantCulture)) 
' 02, 01
```

## <a name="the-ddd-custom-format-specifier"></a>"ddd" カスタム書式指定子

"ddd" カスタム書式指定子は、曜日の省略名を表します。 曜日のローカライズされた省略名は、現在のカルチャまたは特定のカルチャの [DateTimeFormatInfo.AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) プロパティから取得されます。 

次の例では、カスタム書式指定文字列の中に "ddd" カスタム書式指定子が含まれます。 

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays ven. 29 août    
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays ven. 29 août
```

## <a name="the-dddd-custom-format-specifier"></a>"dddd" カスタム書式指定子

"dddd" カスタム書式指定子 (任意の数の "d" 指定子を追加可能) は、曜日の完全名を表します。 曜日のローカライズされた名前は、現在のカルチャまたは特定のカルチャの [DateTimeFormatInfo.DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) プロパティから取得されます。 

次の例では、カスタム書式指定文字列の中に "dddd" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("it-IT")));
// Displays venerdì 29 agosto    
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("it-IT")))
' Displays venerdì 29 agosto                                          
```

## <a name="the-f-custom-format-specifier"></a>"f" カスタム書式指定子

"f" カスタム書式指定子は、秒の端数の最上位桁 (つまり、日時値の秒部分の&1;/10) を表します。

"f" 書式指定子が単独で使用され、その他の書式指定子がない場合、"f" は標準の日時書式指定子として解釈されます。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

[DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider))、[DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@))、[DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider))、[DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) のいずれかのメソッドに渡す書式指定文字列の一部として "f" 書式指定子を使用する場合、"f" 書式指定子の数は、文字列を正しく解析するために、秒の端数の最上位桁数が何桁存在している必要があるかを表します。

次の例では、カスタム書式指定文字列の中に "f" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ff-custom-format-specifier"></a>"ff" カスタム書式指定子

"ff" カスタム書式指定子は、秒の端数の最上位&2; 桁 (つまり、日時値の秒部分の&1;/100) を表します。 

次の例では、カスタム書式指定文字列の中に "ff" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-fff-custom-format-specifier"></a>"fff" カスタム書式指定子

"fff" カスタム書式指定子は、秒の端数の最上位&3; 桁 (つまり、日時値の秒部分の&1;/1000) を表します。 

次の例では、カスタム書式指定文字列の中に "fff" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ffff-custom-format-specifier"></a>"ffff" カスタム書式指定子

"ffff" カスタム書式指定子は、秒の端数の最上位&4; 桁 (つまり、日時値の秒部分の&1;/10000) を表します。

時刻値の&1;/10000 秒要素を表示することもできますが、このような値は意味を持たない場合があります。 日付および時刻の値の精度は、システム クロックの分解能に依存します。

## <a name="the-fffff-custom-format-specifier"></a>"fffff" カスタム書式指定子

"fffff" カスタム書式指定子は、秒の端数の最上位&5; 桁 (つまり、日時値の秒部分の&1;/100000) を表します。

時刻値の&1;/100000 秒要素を表示することもできますが、このような値は意味を持たない場合があります。 日付および時刻の値の精度は、システム クロックの分解能に依存します。 

## <a name="the-ffffff-custom-format-specifier"></a>"ffffff" カスタム書式指定子

"ffffff" カスタム書式指定子は、秒の端数の最上位&6; 桁 (つまり、日時値の秒部分の&1;/1000000) を表します。

時刻値の&1;/1000000 秒要素を表示することもできますが、このような値は意味を持たない場合があります。 日付および時刻の値の精度は、システム クロックの分解能に依存します。 

## <a name="the-fffffff-custom-format-specifier"></a>"fffffff" カスタム書式指定子

"fffffff" カスタム書式指定子は、秒の端数の最上位&7; 桁 (つまり、日時値の秒部分の&1;/10000000) を表します。

時刻値の&1;/10000000 秒要素を表示することもできますが、このような値は意味を持たない場合があります。 日付および時刻の値の精度は、システム クロックの分解能に依存します。 

## <a name="the-f-custom-format-specifier"></a>"F" カスタム書式指定子

"F" カスタム書式指定子は、秒の端数の最上位桁 (つまり、日時値の秒部分の&1;/10) を表します。 その桁がゼロの場合には、何も表示されません。 

"F" 書式指定子が単独で使用され、その他の書式指定子がない場合、"F" は標準の日時書式指定子として解釈されます。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

[DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider))、[DateTime.TryParseExact](xref:System.DateTime.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTime@))、[DateTimeOffset.ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider))、[DateTimeOffset.TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) のいずれかのメソッドの引数として使用された場合、"F" 書式指定子の数は、文字列を正しく解析するために、秒の端数の最上位桁数が最大何桁存在している必要があるかを表します。

次の例では、カスタム書式指定文字列の中に "F" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ff-custom-format-specifier"></a>"FF" カスタム書式指定子

"FF" カスタム書式指定子は、秒の端数の最上位&2; 桁 (つまり、日時値の秒部分の&1;/100) を表します。 ただし、後続のゼロは表示されません。また、2 桁のゼロも表示されません。 

次の例では、カスタム書式指定文字列の中に "FF" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
```

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-fff-custom-format-specifier"></a>"FFF" カスタム書式指定子

"FFF" カスタム書式指定子は、秒の端数の最上位&3; 桁 (つまり、日時値の秒部分の&1;/1000) を表します。 ただし、後続のゼロは表示されません。また、3 桁のゼロも表示されません。 

次の例では、カスタム書式指定文字列の中に "FFF" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15, 18);
CultureInfo ci = CultureInfo.InvariantCulture;

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci));
// Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci));
// Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci));
// Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci));
// Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci));
// Displays 07:27:15.018
````

```vb
Dim date1 As New Date(2008, 8, 29, 19, 27, 15, 018)
Dim ci As CultureInfo = CultureInfo.InvariantCulture

Console.WriteLine(date1.ToString("hh:mm:ss.f", ci))
' Displays 07:27:15.0
Console.WriteLine(date1.ToString("hh:mm:ss.F", ci))
' Displays 07:27:15
Console.WriteLine(date1.ToString("hh:mm:ss.ff", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.FF", ci))
' Displays 07:27:15.01
Console.WriteLine(date1.ToString("hh:mm:ss.fff", ci))
' Displays 07:27:15.018
Console.WriteLine(date1.ToString("hh:mm:ss.FFF", ci))
' Displays 07:27:15.018
```

## <a name="the-ffff-custom-format-specifier"></a>"FFFF" カスタム書式指定子

"FFFF" カスタム書式指定子は、秒の端数の最上位&4; 桁 (つまり、日時値の秒部分の&1;/10000) を表します。 ただし、後続のゼロは表示されません。また、4 桁のゼロも表示されません。

時刻値の&1;/10000 秒要素を表示することもできますが、このような値は意味を持たない場合があります。 日付および時刻の値の精度は、システム クロックの分解能に依存します。

## <a name="the-fffff-custom-format-specifier"></a>"FFFFF" カスタム書式指定子

"FFFFF" カスタム書式指定子は、秒の端数の最上位&5; 桁 (つまり、日時値の秒部分の&1;/100000) を表します。 ただし、後続のゼロは表示されません。また、5 桁のゼロも表示されません。

時刻値の&1;/100000 秒要素を表示することもできますが、このような値は意味を持たない場合があります。 日付および時刻の値の精度は、システム クロックの分解能に依存します。

## <a name="the-ffffff-custom-format-specifier"></a>"FFFFFF" カスタム書式指定子

"FFFFFF" カスタム書式指定子は、秒の端数の最上位&6; 桁 (つまり、日時値の秒部分の&1;/1000000) を表します。 ただし、後続のゼロは表示されません。また、6 桁のゼロも表示されません。

時刻値の&1;/1000000 秒要素を表示することもできますが、このような値は意味を持たない場合があります。 日付および時刻の値の精度は、システム クロックの分解能に依存します。

## <a name="the-fffffff-custom-format-specifier"></a>"FFFFFFF" カスタム書式指定子

"FFFFFFF" カスタム書式指定子は、秒の端数の最上位&7; 桁 (つまり、日時値の秒部分の&1;/10000000) を表します。 ただし、後続のゼロは表示されません。また、7 桁のゼロも表示されません。

時刻値の&1;/10000000 秒要素を表示することもできますが、このような値は意味を持たない場合があります。 日付および時刻の値の精度は、システム クロックの分解能に依存します。

## <a name="the-g-or-gg-custom-format-specifier"></a>"g" または "gg" カスタム書式指定子

"g" または "gg" カスタム書式指定子 (任意の数の "g" 指定子を追加可能) は、A.D. などの時期または時代 (年号) を表します。 書式設定される日付に時期または時代 (年号) の文字列が関連付けられていない場合、この指定子は無視されます。 

"g" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"g" は標準の日時書式指定子として解釈されます。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

次の例では、カスタム書式指定文字列の中に "g" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(70, 08, 04);

Console.WriteLine(date1.ToString("MM/dd/yyyy g", 
                  CultureInfo.InvariantCulture));
// Displays 08/04/0070 A.D.                        
Console.WriteLine(date1.ToString("MM/dd/yyyy g", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));                         
// Displays 08/04/0070 ap. J.-C.
```

```vb
Dim date1 As Date = #08/04/0070#

Console.WriteLine(date1.ToString("MM/dd/yyyy g", _
                  CultureInfo.InvariantCulture))
' Displays 08/04/0070 A.D.                        
Console.WriteLine(date1.ToString("MM/dd/yyyy g", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))                         
' Displays 08/04/0070 ap. J.-C.
```

## <a name="the-h-custom-format-specifier"></a>"h" カスタム書式指定子

"h" カスタム書式指定子は、時間を 1 ～ 12 の数値として表します。つまり、午前 0 時と午後 0 時から時間をカウントする 12 時間制で時間が表されます。 午前&0; 時からの特定の時間を、午後&0; 時からの同じ時間と区別できません。 時間は丸められず、1 桁の時間は先行ゼロなしで書式設定されます。 たとえば、午前と午後の 5:43 という時間は、このカスタム書式指定子によって "5" と表示されます。 

"h" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"h" は標準の日時書式指定子として解釈され、[FormatException](xref:System.FormatException) をスローします。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

次の例では、カスタム書式指定文字列の中に "h" カスタム書式指定子が含まれます。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-hh-custom-format-specifier"></a>"hh" カスタム書式指定子

"hh" カスタム書式指定子 (任意の数の "h" 指定子を追加可能) は、時間を 1 ～ 12 の数値として表します。つまり、午前 0 時と午後 0 時から時間をカウントする 12 時間制で時間が表されます。 午前&0; 時からの特定の時間を、午後&0; 時からの同じ時間と区別できません。 時間は丸められず、1 桁の時間は先行ゼロ付きで書式設定されます。 たとえば、午前と午後の 5:43 という時間は、この書式指定子によって "05" と表示されます。

次の例では、カスタム書式指定文字列の中に "hh" カスタム書式指定子が含まれます。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-h-custom-format-specifier"></a>"H" カスタム書式指定子

"H" カスタム書式指定子は、時間を 0 ～ 23 の数値として表します。つまり、午前 0 時から時間をカウントする 24 時間制で時間が表されます。 1 桁の時間は、先行ゼロなしで書式設定されます。 

"H" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"H" は標準の日時書式指定子として解釈され、[FormatException](xref:System.FormatException) をスローします。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

次の例では、カスタム書式指定文字列の中に "H" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 1, 1, 6, 9, 1);
Console.WriteLine(date1.ToString("H:mm:ss", 
                  CultureInfo.InvariantCulture));
// Displays 6:09:01 
```

```vb
Dim date1 As Date = #6:09:01AM#
Console.WriteLine(date1.ToString("H:mm:ss", _
                  CultureInfo.InvariantCulture))
' Displays 6:09:01 
```

## <a name="the-hh-custom-format-specifier"></a>"HH" カスタム書式指定子

"HH" カスタム書式指定子 (任意の数の "H" 指定子を追加可能) は、時間を 00 ～ 23 の数値として表します。つまり、午前 0 時から時間をカウントする 24 時間制で時間が表されます。 1 桁の時間は、先行ゼロ付きで書式設定されます。 

次の例では、カスタム書式指定文字列の中に "HH" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 1, 1, 6, 9, 1);
Console.WriteLine(date1.ToString("HH:mm:ss", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01                        
```

```vb
Dim date1 As Date = #6:09:01AM#
Console.WriteLine(date1.ToString("HH:mm:ss", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01
```

## <a name="the-k-custom-format-specifier"></a>"K" カスタム書式指定子

"K" カスタム書式指定子は、日付と時刻の値のタイム ゾーン情報を表します。 この書式指定子を [DateTime](xref:System.DateTime) 値で使用した場合、書式設定後の文字列は、[DateTime.Kind](xref:System.DateTime.Kind) プロパティの値によって定義されます。 
 
* ローカル タイム ゾーンの場合 ([DateTimeKind.Local](xref:System.DateTimeKind.Local) の [DateTime.Kind](xref:System.DateTime.Kind) プロパティ値)、この指定子は "zzz" 指定子に相当し、書式設定後の文字列には世界協定時刻 (UTC: Coordinated Universal Time) からのローカル オフセットが含まれます ("-07:00" など)。 

* UTC 時刻の場合 ([DateTimeKind.Utc](xref:System.DateTimeKind.Utc) の [DateTime.Kind](xref:System.DateTime.Kind) プロパティ値)、書式設定後の文字列には UTC 日付を表す "Z" 文字が含まれます。 

* タイム ゾーンが指定されていない時刻の場合 ([DateTime.Kind](xref:System.DateTime.Kind) プロパティ値 = [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified))、[String.Empty](xref:System.String#System_String_Empty) と同じ結果になります。 

"K" 書式指定子を [DateTimeOffset](xref:System.DateTimeOffset) 値で使用した場合、この指定子は "zz" 書式指定子に相当し、書式設定後の文字列には [DateTimeOffset](xref:System.DateTimeOffset) 値の UTC を基準としたオフセットが含まれます。 

"K" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"K" は標準の日時書式指定子として解釈され、[FormatException](xref:System.FormatException) をスローします。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

次の例では、米国太平洋標準時タイム ゾーンのシステムで、"K" カスタム書式指定子と各種の [DateTime](xref:System.DateTime) 値および [DateTimeOffset](xref:System.DateTimeOffset) 値を組み合わせた結果の文字列を表示します。

```csharp
Console.WriteLine(DateTime.Now.ToString("%K"));
// Displays -07:00
Console.WriteLine(DateTime.UtcNow.ToString("%K"));
// Displays Z      
Console.WriteLine("'{0}'", 
                  DateTime.SpecifyKind(DateTime.Now, 
                       DateTimeKind.Unspecified).ToString("%K"));
// Displays ''      
Console.WriteLine(DateTimeOffset.Now.ToString("%K"));
// Displays -07:00
Console.WriteLine(DateTimeOffset.UtcNow.ToString("%K"));
// Displays +00:00
Console.WriteLine(new DateTimeOffset(2008, 5, 1, 6, 30, 0, 
                      new TimeSpan(5, 0, 0)).ToString("%K"));
// Displays +05:00  
```

```vb
Console.WriteLine(Date.Now.ToString("%K"))
' Displays -07:00
Console.WriteLine(Date.UtcNow.ToString("%K"))
' Displays Z      
Console.WriteLine("'{0}'", _
                  Date.SpecifyKind(Date.Now, _
                                   DateTimeKind.Unspecified). _
                  ToString("%K"))
' Displays ''      
Console.WriteLine(DateTimeOffset.Now.ToString("%K"))
' Displays -07:00
Console.WriteLine(DateTimeOffset.UtcNow.ToString("%K"))
' Displays +00:00
Console.WriteLine(New DateTimeOffset(2008, 5, 1, 6, 30, 0, _
                                     New TimeSpan(5, 0, 0)). _
                  ToString("%K"))
' Displays +05:00 
```

## <a name="the-m-custom-format-specifier"></a>"m" カスタム書式指定子

"m" カスタム書式指定子は、分を 0 ～ 59 の数値として表します。 この分は、直前の時間から経過した分数です。 1 桁の分は、先行ゼロなしで書式設定されます。 

"m" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"m" は標準の日時書式指定子として解釈されます。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。 

次の例では、カスタム書式指定文字列の中に "m" カスタム書式指定子が含まれます。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-mm-custom-format-specifier"></a>"mm" カスタム書式指定子

"mm" カスタム書式指定子 (任意の数の "m" 指定子を追加可能) は、分を 00 ～ 59 の数値として表します。 この分は、直前の時間から経過した分数です。 1 桁の分は、先行ゼロ付きで書式設定されます。 

次の例では、カスタム書式指定文字列の中に "mm" カスタム書式指定子が含まれます。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-m-custom-format-specifier"></a>"M" カスタム書式指定子

"M" カスタム書式指定子は、月を 1 ～ 12 (13 の月がある暦の場合は 1 ～ 13) の数値として表します。 1 桁の月は、先行ゼロなしで書式設定されます。 

"M" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"M" は標準の日時書式指定子として解釈されます。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

次の例では、カスタム書式指定文字列の中に "M" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 18);
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays (8) Aug, August
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("nl-NL")));                       
// Displays (8) aug, augustus
Console.WriteLine(date1.ToString("(M) MMM, MMMM", 
                  CultureInfo.CreateSpecificCulture("lv-LV")));                        
// Displays (8) Aug, augusts
```

```vb
Dim date1 As Date = #8/18/2008#
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays (8) Aug, August
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("nl-NL")))                        
' Displays (8) aug, augustus
Console.WriteLine(date1.ToString("(M) MMM, MMMM", _
                  CultureInfo.CreateSpecificCulture("lv-LV")))                        
' Displays (8) Aug, augusts 
```

## <a name="the-mm-custom-format-specifier"></a>"MM" カスタム書式指定子

"MM" カスタム書式指定子は、月を 01 ～ 12 (13 の月がある暦の場合は 1 ～ 13) の数値として表します。 1 桁の月は、先行ゼロ付きで書式設定されます。 

次の例では、カスタム書式指定文字列の中に "MM" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 1, 2, 6, 30, 15);

Console.WriteLine(date1.ToString("dd, MM", 
                  CultureInfo.InvariantCulture)); 
// 02, 01
```

```vb
Dim date1 As Date = #1/2/2008 6:30:15AM#

Console.WriteLine(date1.ToString("dd, MM", _
                  CultureInfo.InvariantCulture)) 
' 02, 01
```

## <a name="the-mmm-custom-format-specifier"></a>"MMM" カスタム書式指定子

"MMM" カスタム書式指定子は、月の省略名を表します。 月のローカライズされた省略名は、現在のカルチャまたは特定のカルチャの [DateTimeFormatInfo.AbbreviatedMonthNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames) プロパティから取得されます。

次の例では、カスタム書式指定文字列の中に "MMM" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays ven. 29 août
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Fri 29 Aug
Console.WriteLine(date1.ToString("ddd d MMM", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays ven. 29 août
```

## <a name="the-mmmm-custom-format-specifier"></a>"MMMM" カスタム書式指定子

"MMMM" カスタム書式指定子は、月の完全名を表します。 月のローカライズされた名前は、現在のカルチャまたは特定のカルチャの [DateTimeFormatInfo.MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) プロパティから取得されます。 

次の例では、カスタム書式指定文字列の中に "MMMM" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(2008, 8, 29, 19, 27, 15);

Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", 
                  CultureInfo.CreateSpecificCulture("it-IT")));
// Displays venerdì 29 agosto 
```

```vb
Dim date1 As Date = #08/29/2008 7:27:15PM#

Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Friday 29 August
Console.WriteLine(date1.ToString("dddd dd MMMM", _
                  CultureInfo.CreateSpecificCulture("it-IT")))
' Displays venerdì 29 agosto  
```

## <a name="the-s-custom-format-specifier"></a>"s" カスタム書式指定子

"s" カスタム書式指定子は、秒を 0 ～ 59 の数値として表します。 この秒は、直前の分から経過した秒数です。 1 桁の秒は、先行ゼロなしで書式設定されます。 

"s" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"s" は標準の日時書式指定子として解釈されます。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。 

次の例では、カスタム書式指定文字列の中に "s" カスタム書式指定子が含まれます。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-ss-custom-format-specifier"></a>"ss" カスタム書式指定子

"ss" カスタム書式指定子 (任意の数の "s" 指定子を追加可能) は、秒を 00 ～ 59 の数値として表します。 この秒は、直前の分から経過した秒数です。 1 桁の秒は、先行ゼロ付きで書式設定されます。 

次の例では、カスタム書式指定文字列の中に "ss" カスタム書式指定子が含まれます。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-t-custom-format-specifier"></a>"t" カスタム書式指定子

"t" カスタム書式指定子は、AM/PM 指定子の最初の文字を表します。 ローカライズされた適切な指定子は、現在のカルチャまたは特定のカルチャの [DateTimeFormatInfo.AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) プロパティまたは [DateTimeFormatInfo.PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) プロパティから取得されます。 AM 指定子は、0:00:00 (午前 0 時) から 11:59:59.999 までのすべての時刻に使用されます。 PM 指定子は、12:00:00 (正午) から 23:59:59.999 までのすべての時刻に使用されます。 

"t" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"t" は標準の日時書式指定子として解釈されます。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

次の例では、カスタム書式指定文字列の中に "t" カスタム書式指定子が含まれます。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1 µ                        
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.InvariantCulture));
// Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", 
                  CultureInfo.CreateSpecificCulture("el-GR")));
// Displays 6:9:1.5 µ
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1 µ                        
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.InvariantCulture))
' Displays 6:9:1.5 P
Console.WriteLine(date1.ToString("h:m:s.F t", _
                  CultureInfo.CreateSpecificCulture("el-GR")))
' Displays 6:9:1.5 µ
```

## <a name="the-tt-custom-format-specifier"></a>"tt" カスタム書式指定子

"tt" カスタム書式指定子 (任意の数の "t" 指定子を追加可能) は、AM/PM 指定子全体を表します。 ローカライズされた適切な指定子は、現在のカルチャまたは特定のカルチャの [DateTimeFormatInfo.AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) プロパティまたは [DateTimeFormatInfo.PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) プロパティから取得されます。 AM 指定子は、0:00:00 (午前 0 時) から 11:59:59.999 までのすべての時刻に使用されます。 PM 指定子は、12:00:00 (正午) から 23:59:59.999 までのすべての時刻に使用されます。

AM と PM を区別する必要のある言語の場合、必ず "tt" 指定子を使用する必要があります。 たとえば、日本語の場合、AM/PM 指定子の&2; 番目の文字は異なりますが、先頭文字は同じです。

次の例では、カスタム書式指定文字列の中に "tt" カスタム書式指定子が含まれます。

```csharp
DateTime date1; 
date1 = new DateTime(2008, 1, 1, 18, 9, 1);
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01 du.
date1 = new DateTime(2008, 1, 1, 18, 9, 1, 500);
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.InvariantCulture));
// Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", 
                  CultureInfo.CreateSpecificCulture("hu-HU")));
// Displays 06:09:01.50 du.
```

```vb
Dim date1 As Date 
date1 = #6:09:01PM#
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01 du.
date1 = New Date(2008, 1, 1, 18, 9, 1, 500)
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.InvariantCulture))
' Displays 06:09:01.50 PM                        
Console.WriteLine(date1.ToString("hh:mm:ss.ff tt", _
                  CultureInfo.CreateSpecificCulture("hu-HU")))
' Displays 06:09:01.50 du.
```

## <a name="the-y-custom-format-specifier"></a>"y" カスタム書式指定子

"y" カスタム書式指定子は、年を&1; 桁または&2; 桁の数値として表します。 年が&2; 桁を超える場合は、下&2; 桁のみが結果に表示されます。 2 桁の年の 1 桁目がゼロで始まる場合 (2008 など)、先行ゼロが省略されます。 

"y" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"y" は標準の日時書式指定子として解釈されます。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

次の例では、カスタム書式指定文字列の中に "y" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yy-custom-format-specifier"></a>"yy" カスタム書式指定子

"yy" カスタム書式指定子は、年を&2; 桁の数値として表します。 年が&2; 桁を超える場合は、下&2; 桁のみが結果に表示されます。 年が&2; 桁に満たない場合は、2 桁になるまで数値が先行ゼロで埋められます。

解析操作では、"yy" カスタム形式指定子を使用した&2; 桁の年は、書式プロバイダーの現在のカレンダーの [Calendar.TwoDigitYearMax](xref:System.Globalization.Calendar.TwoDigitYearMax) プロパティに基づいて解釈されます。 次の例は、このケースでは現在のカルチャである en-US カルチャの既定のグレゴリオ暦を使用して、2 桁の年を持つ日付の文字列形式を解析します。 次に、現在のカルチャの [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトを [TwoDigitYearMax](xref:System.Globalization.GregorianCalendar.TwoDigitYearMax) プロパティが変更されている [GregorianCalendar](xref:System.Globalization.GregorianCalendar) オブジェクトを使用するように変更します。

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fmt = "dd-MMM-yy";
      string value = "24-Jan-49";

      Calendar cal = (Calendar) CultureInfo.CurrentCulture.Calendar.Clone();
      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax);

      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, null));
      Console.WriteLine();

      cal.TwoDigitYearMax = 2099;
      CultureInfo culture = (CultureInfo) CultureInfo.CurrentCulture.Clone();
      culture.DateTimeFormat.Calendar = cal;
      Thread.CurrentThread.CurrentCulture = culture;

      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax);
      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, null));
   }
}
// The example displays the following output:
//       Two Digit Year Range: 1930 - 2029
//       1/24/1949
//       
//       Two Digit Year Range: 2000 - 2099
//       1/24/2049
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fmt As String = "dd-MMM-yy"
      Dim value As String = "24-Jan-49"

      Dim cal As Calendar = CType(CultureInfo.CurrentCulture.Calendar.Clone(), Calendar)
      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax)

      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, Nothing))
      Console.WriteLine()

      cal.TwoDigitYearMax = 2099
      Dim culture As CultureInfo = CType(CultureInfo.CurrentCulture.Clone(), CultureInfo)
      culture.DateTimeFormat.Calendar = cal
      Thread.CurrentThread.CurrentCulture = culture

      Console.WriteLine("Two Digit Year Range: {0} - {1}", 
                        cal.TwoDigitYearMax - 99, cal.TwoDigitYearMax)
      Console.WriteLine("{0:d}", DateTime.ParseExact(value, fmt, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Two Digit Year Range: 1930 - 2029
'       1/24/1949
'       
'       Two Digit Year Range: 2000 - 2099
'       1/24/2049
```

次の例では、カスタム書式指定文字列の中に "yy" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yyy-custom-format-specifier"></a>"yyy" カスタム書式指定子

"yyy" カスタム書式指定子は、年を&3; 桁以上で表します。 年が&3; 桁を超える場合は、それらの数字も結果に含まれます。 年が&3; 桁に満たない場合は、3 桁になるまで数値が先行ゼロで埋められます。

> [!NOTE]
> 年が&5; 桁になることがあるタイ仏暦については、この書式指定子ですべての有効桁が表示されます。

次の例では、カスタム書式指定文字列の中に "yyy" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010      
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010 
```

## <a name="the-yyyy-custom-format-specifier"></a>"yyyy" カスタム書式指定子

"yyyy" カスタム書式指定子は、年を&4; 桁以上で表します。 年が&4; 桁を超える場合は、それらの数字も結果に含まれます。 年が&4; 桁に満たない場合は、4 桁になるまで数値が先行ゼロで埋められます。

> [!NOTE]
> 年が&5; 桁になることがあるタイ仏暦については、この書式指定子ですべての有効桁が表示されます。

次の例では、カスタム書式指定文字列の中に "yyyy" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010 
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010
```

## <a name="the-yyyyy-custom-format-specifier"></a>"yyyyy" カスタム書式指定子

"yyyyy" カスタム書式指定子 (任意の数の "y" 指定子を追加可能) は、年を&5; 桁以上で表します。 年が&5; 桁を超える場合は、それらの数字も結果に含まれます。 年が&5; 桁に満たない場合は、5 桁になるまで数値が先行ゼロで埋められます。

"y" 指定子を追加すると、"y" 指定子の数と同じ桁数になるまで数値が先行ゼロで埋められます。 

次の例では、カスタム書式指定文字列の中に "yyyyy" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = new DateTime(1, 12, 1);
DateTime date2 = new DateTime(2010, 1, 1);
Console.WriteLine(date1.ToString("%y"));
// Displays 1
Console.WriteLine(date1.ToString("yy"));
// Displays 01
Console.WriteLine(date1.ToString("yyy"));
// Displays 001
Console.WriteLine(date1.ToString("yyyy"));
// Displays 0001
Console.WriteLine(date1.ToString("yyyyy"));
// Displays 00001
Console.WriteLine(date2.ToString("%y"));
// Displays 10
Console.WriteLine(date2.ToString("yy"));
// Displays 10
Console.WriteLine(date2.ToString("yyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyy"));
// Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"));
// Displays 02010 
```

```vb
Dim date1 As Date = #12/1/0001#
Dim date2 As Date = #1/1/2010#
Console.WriteLine(date1.ToString("%y"))
' Displays 1
Console.WriteLine(date1.ToString("yy"))
' Displays 01
Console.WriteLine(date1.ToString("yyy"))
' Displays 001
Console.WriteLine(date1.ToString("yyyy"))
' Displays 0001
Console.WriteLine(date1.ToString("yyyyy"))
' Displays 00001
Console.WriteLine(date2.ToString("%y"))
' Displays 10
Console.WriteLine(date2.ToString("yy"))
' Displays 10
Console.WriteLine(date2.ToString("yyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyy"))
' Displays 2010      
Console.WriteLine(date2.ToString("yyyyy"))
' Displays 02010 
```

## <a name="the-z-custom-format-specifier"></a>"z" カスタム書式指定子

[DateTime](xref:System.DateTime) 値で使用した場合、"z" カスタム書式指定子は、オペレーティング システムのローカル タイム ゾーンの、世界協定時刻 (UTC) を基準とした符号付きオフセット (時間単位) を表します。 インスタンスの [DateTime.Kind](xref:System.DateTime.Kind) プロパティの値は反映されません。 そのため、[DateTime](xref:System.DateTime) 値に対して "z" 書式指定子を使用することはお勧めできません。

[DateTimeOffset](xref:System.DateTimeOffset) 値で使用した場合、この書式指定子は、[DateTimeOffset](xref:System.DateTimeOffset) 値の、UTC を基準とするオフセット (時間単位) を表します。 

このオフセットは、常に先頭の符号と共に表示されます。 正符号 (+) は UTC より時間が進んでいることを示し、負符号 (-) は UTC より時間が遅れていることを示します。 1 桁のオフセットは、先行ゼロなしで書式設定されます。 

"z" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"z" は標準の日時書式指定子として解釈され、[FormatException](xref:System.FormatException) をスローします。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。 

次の例では、カスタム書式指定文字列の中に "z" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the-zz-custom-format-specifier"></a>"zz" カスタム書式指定子

[DateTime](xref:System.DateTime) 値で使用した場合、"zz" カスタム書式指定子は、オペレーティング システムのローカル タイム ゾーンの、世界協定時刻 (UTC) を基準とした符号付きオフセット (時間単位) を表します。 インスタンスの [DateTime.Kind](xref:System.DateTime.Kind) プロパティの値は反映されません。 そのため、[DateTime](xref:System.DateTime) 値に対して "zz" 書式指定子を使用することはお勧めできません。

[DateTimeOffset](xref:System.DateTimeOffset) 値で使用した場合、この書式指定子は、[DateTimeOffset](xref:System.DateTimeOffset) 値の、UTC を基準とするオフセット (時間単位) を表します。

このオフセットは、常に先頭の符号と共に表示されます。 正符号 (+) は UTC より時間が進んでいることを示し、負符号 (-) は UTC より時間が遅れていることを示します。 1 桁のオフセットは、先行ゼロ付きで書式設定されます。 

次の例では、カスタム書式指定文字列の中に "zz" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the-zzz-custom-format-specifier"></a>"zzz" カスタム書式指定子

[DateTime](xref:System.DateTime) 値で使用した場合、"zzz" カスタム書式指定子は、オペレーティング システムのローカル タイム ゾーンの、世界協定時刻 (UTC) を基準とした符号付きオフセット (時間単位) を表します。 インスタンスの [DateTime.Kind](xref:System.DateTime.Kind) プロパティの値は反映されません。 そのため、[DateTime](xref:System.DateTime) 値に対して "zzz" 書式指定子を使用することはお勧めできません。

[DateTimeOffset](xref:System.DateTimeOffset) 値で使用した場合、この書式指定子は、[DateTimeOffset](xref:System.DateTimeOffset) 値の、UTC を基準とするオフセット (時間単位) を表します。

このオフセットは、常に先頭の符号と共に表示されます。 正符号 (+) は UTC より時間が進んでいることを示し、負符号 (-) は UTC より時間が遅れていることを示します。 1 桁のオフセットは、先行ゼロ付きで書式設定されます。 

次の例では、カスタム書式指定文字列の中に "zzz" カスタム書式指定子が含まれます。

```csharp
DateTime date1 = DateTime.UtcNow;
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date1));
// Displays -7, -07, -07:00                     

DateTimeOffset date2 = new DateTimeOffset(2008, 8, 1, 0, 0, 0, 
                                          new TimeSpan(6, 0, 0));
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", 
                  date2));
// Displays +6, +06, +06:00
```

```vb
Dim date1 As Date = Date.UtcNow
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date1))
' Displays -7, -07, -07:00                     

Dim date2 As New DateTimeOffset(2008, 8, 1, 0, 0, 0, _
                                New Timespan(6, 0, 0))
Console.WriteLine(String.Format("{0:%z}, {0:zz}, {0:zzz}", _
                  date2))                                     
' Displays +6, +06, +06:00
```

## <a name="the--custom-format-specifier"></a>":" カスタム書式指定子

":" カスタム書式指定子は、時、分、および秒を区別するための時刻の区切り記号を表します。 

":" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"z" は標準の日時書式指定子として解釈され、[FormatException](xref:System.FormatException) をスローします。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

## <a name="the--custom-format-specifier"></a>"/" カスタム書式指定子

"/" カスタム書式指定子は、年、月、および日を区別するための日付の区切り記号を表します。 

"/" 書式指定子が単独で使用され、その他のカスタム書式指定子がない場合、"z" は標準の日時書式指定子として解釈され、[FormatException](xref:System.FormatException) をスローします。 単一の書式指定子を使用する方法の詳細については、このトピックで後述する「[単一のカスタム書式指定子の使用](#using-single-custom-format-specifiers)」を参照してください。

## <a name="character-literals"></a>文字リテラル

カスタム日時書式指定文字列の次の文字は予約済みで、常に書式設定文字として解釈されます。または "、'、/、および \, の場合は、特殊文字として解釈されます。 

  |   |   |   |      
- | - | - | - | -
F | H | K | M | d
f | G | h | m | s
Y | Y | z | % | :
/ | " | ' | \ |
  |   |   |   |
  
その他の文字はすべて、文字リテラルとして常に解釈され、書式設定操作では、変更されずに結果の文字列に含まれます。 解析操作では、これらは入力文字列の文字と完全に一致している必要があります。比較では大文字小文字を区別します。 

次の例には、書式指定文字列でローカル タイム ゾーンを表すため、リテラル文字 "PST" (太平洋標準時) と "PDT" (太平洋夏時間)が含まれています。 文字列は結果の文字列に含まれ、ローカル タイム ゾーン文字列を含む文字列も正常に解析することに注意してください。 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      String[] formats = { "dd MMM yyyy hh:mm tt PST", 
                           "dd MMM yyyy hh:mm tt PDT" };
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(formats[1]));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm PST";
      DateTime newDate;
      if (DateTime.TryParseExact(value, formats, null, 
                                 DateTimeStyles.None, out newDate)) 
         Console.WriteLine(newDate);
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim formats() As String = { "dd MMM yyyy hh:mm tt PST", 
                                  "dd MMM yyyy hh:mm tt PDT" }
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(formats(1)))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm PST"
      Dim newDate As Date
      If Date.TryParseExact(value, formats, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM PDT
'       12/25/2016 12:00:00 PM
```

文字が結果の文字列に含まれるように、または入力文字列で正常に解析されるように、文字が予約文字としてではなく、リテラル文字として解釈されることを示すには、次の&2; つの方法があります。

* 予約済みの各文字をエスケープします。 詳細については、「[エスケープ文字の使用](#using-the-escape-character)」を参照してください。 
  
  次の例には、書式指定文字列でローカル タイム ゾーンを表すため、リテラル文字 "pst"(太平洋標準時間) が含まれています。 "s" と "t" はどちらもカスタム書式指定文字列であるため、どちらの文字も文字リテラルとして解釈されるにはエスケープする必要があります。 
  
```csharp
using System;
using System.Globalization;

public class Example
{
  public static void Main()
  {
      String format = "dd MMM yyyy hh:mm tt p\\s\\t";
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(format));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm pst";
      DateTime newDate;
      if (DateTime.TryParseExact(value, format, null, 
                                  DateTimeStyles.None, out newDate)) 
          Console.WriteLine(newDate);
      else
          Console.WriteLine("Unable to parse '{0}'", value);
  }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim fmt As String = "dd MMM yyyy hh:mm tt p\s\t" 
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(fmt))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm pst"
      Dim newDate As Date
      If Date.TryParseExact(value, fmt, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM pst
'       12/25/2016 12:00:00 PM
```
  
* リテラル文字列全体を引用符またはアポストロフィで囲みます。 次の例は、前の例と似ていますが、区切られた文字列全体が文字リテラルとして解釈されることを示すため、"pst" が引用符で囲まれている点が異なります。 

```csharp
using System;
using System.Globalization;

public class Example
{
   public static void Main()
   {
      String format = "dd MMM yyyy hh:mm tt \"pst\"";
      var dat = new DateTime(2016, 8, 18, 16, 50, 0);
      // Display the result string. 
      Console.WriteLine(dat.ToString(format));

      // Parse a string. 
      String value = "25 Dec 2016 12:00 pm pst";
      DateTime newDate;
      if (DateTime.TryParseExact(value, format, null, 
                                 DateTimeStyles.None, out newDate)) 
         Console.WriteLine(newDate);
      else
         Console.WriteLine("Unable to parse '{0}'", value);
   }
}
// The example displays the following output:
//       18 Aug 2016 04:50 PM PDT
//       12/25/2016 12:00:00 PM
```

```vb
Imports System.Globalization

Module Example
   Public Sub Main()
      Dim fmt As String = "dd MMM yyyy hh:mm tt ""pst"""  
      Dim dat As New Date(2016, 8, 18, 16, 50, 0)
      ' Display the result string. 
      Console.WriteLine(dat.ToString(fmt))

      ' Parse a string. 
      Dim value As String = "25 Dec 2016 12:00 pm pst"
      Dim newDate As Date
      If Date.TryParseExact(value, fmt, Nothing, 
                            DateTimeStyles.None, newDate) Then 
         Console.WriteLine(newDate)
      Else
         Console.WriteLine("Unable to parse '{0}'", value)
      End If                               
   End Sub
End Module
' The example displays the following output:
'       18 Aug 2016 04:50 PM pst
'       12/25/2016 12:00:00 PM
```

## <a name="notes"></a>ノート


### <a name="using-single-custom-format-specifiers"></a>単一のカスタム書式指定子の使用

カスタム日時書式指定文字列は、複数の文字で構成されます。 日時書式指定メソッドでは、1 文字の文字列が標準の日時書式指定文字列として解釈されます。 文字が有効な書式指定子として認識されない場合は [FormatException](xref:System.FormatException) がスローされます。 たとえば、"h" 指定子のみで構成される書式指定文字列は、標準の日時書式指定文字列として解釈されます。 ただし、この場合では、"h" という標準の日時書式指定子が存在しないため、例外がスローされます。 

カスタム日時書式指定子のいずれかを書式指定文字列内の唯一の指定子として使用するには (つまり、"d"、"f"、"F"、"g"、"h"、"H"、"K"、"m"、"M"、"s"、"t"、"y"、"z"、":"、"/" のいずれかのカスタム書式指定子を単体で使用するには)、指定子の前または後に空白を挿入するか、または単一のカスタム日時指定子の前にパーセント ("%") 書式指定子を挿入します。

たとえば、"`%h`" は、現在の日時値が表す時要素を表示するカスタム日時書式指定文字列として解釈されます。 また、" h" または "h " の各書式指定文字列も使用できますが、書式設定後の文字列に時間と共に空白が挿入されます。 これらの&3; つの書式指定文字列の例を次に示します。


```csharp
DateTime dat1 = new DateTime(2009, 6, 15, 13, 45, 0);

Console.WriteLine("'{0:%h}'", dat1);
Console.WriteLine("'{0: h}'", dat1);
Console.WriteLine("'{0:h }'", dat1);
// The example displays the following output:
//       '1'
//       ' 1'
//       '1 '
```

```vb
Dim dat1 As Date = #6/15/2009 1:45PM#

Console.WriteLine("'{0:%h}'", dat1)
Console.WriteLine("'{0: h}'", dat1)
Console.WriteLine("'{0:h }'", dat1)
' The example displays the following output:
'       '1'
'       ' 1'
'       '1 '
```

### <a name="using-the-escape-character"></a>エスケープ文字の使用

書式指定文字列内の "d"、"f"、"F"、"g"、"h"、"H"、"K"、"m"、"M"、"s"、"t"、"y"、"z"、":"、"/" の各文字は、リテラル文字ではなくカスタム書式指定子として解釈されます。 文字が書式指定子として解釈されないようにするには、その文字の前に、エスケープ文字の円記号 (\)) を付けます。 エスケープ文字は、その後に続く文字が、そのまま結果の文字列に含める必要がある文字リテラルであることを示します。

結果の文字列に円記号を含める場合は、円記号をもう&1; つ付加して、円記号自体をエスケープする必要があります (`\\`)。

> [!NOTE]
> C# コンパイラなど、一部のコンパイラでは、同様に、1 つの円記号がエスケープ文字として解釈されることがあります。 書式設定時に文字列が正しく解釈されるようにするには、逐語的文字列リテラル文字 (@ 文字) を文字列の前に使用します。また、円記号の前にもう&1; つ円記号を付ける方法もあります。 両方の方法を次の C# の例に示します。

次の例では、エスケープ文字を使用して、書式設定操作で "h" と "m" の各文字が書式指定子として解釈されないようにします。 

```csharp
DateTime date = new DateTime(2009, 06, 15, 13, 45, 30, 90);
string fmt1 = "h \\h m \\m";
string fmt2 = @"h \h m \m";

Console.WriteLine("{0} ({1}) -> {2}", date, fmt1, date.ToString(fmt1));
Console.WriteLine("{0} ({1}) -> {2}", date, fmt2, date.ToString(fmt2));
// The example displays the following output:
//       6/15/2009 1:45:30 PM (h \h m \m) -> 1 h 45 m
//       6/15/2009 1:45:30 PM (h \h m \m) -> 1 h 45 m
```

```vb
Dim date1 As Date = #6/15/2009 13:45#
Dim fmt As String = "h \h m \m"

Console.WriteLine("{0} ({1}) -> {2}", date1, fmt, date1.ToString(fmt))
' The example displays the following output:
'       6/15/2009 1:45:00 PM (h \h m \m) -> 1 h 45 m 
```

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo のプロパティ

書式設定は、現在の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのプロパティの影響を受けます。このオブジェクトは、現在のスレッド カルチャによって暗黙的に指定されるか、または書式設定を実行するメソッドの [IFormatProvider](xref:System.IFormatProvider) パラメーターによって明示的に指定されます。 [IFormatProvider](xref:System.IFormatProvider) パラメーターには、カルチャを表す [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト、または [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトを指定する必要があります。 

各種のカスタム日時書式指定子によって生成される書式設定後の文字列も、現在の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのプロパティに依存します。 カスタム日時書式指定子によって生成される結果は、対応する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) プロパティを変更することによって変えることができます。 たとえば、"ddd" 書式指定子を使用した場合、書式設定後の文字列には、[AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) 文字列配列に指定されている曜日の省略名が追加されます。 同様に、"MMMM" 書式指定子を使用した場合、書式設定後の文字列には、[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) 文字列配列に指定されている月の正式名が追加されます。

## <a name="see-also"></a>関連項目

[System.DateTime](xref:System.DateTime)

[System.IFormatProvider](xref:System.IFormatProvider)

[型の書式設定](formatting-types.md)

[標準の日時と時刻の書式指定文字列](standard-datetime.md)


