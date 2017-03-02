---
title: "標準の日時書式指定文字列"
description: "標準の日時書式指定文字列"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: be239871-10cc-4949-b548-200bb260630a
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f9247bae0d290db570b8cd8885e654524ea2f36b
ms.lasthandoff: 03/02/2017

---

# <a name="standard-date-and-time-format-strings"></a>標準の日時書式指定文字列

標準の日時書式指定文字列は、単一の書式指定子を使用して日付と時刻の値のテキスト表現を定義します。 空白を含む複数の文字で構成される日時書式指定文字列は、カスタム日時書式指定文字列として解釈されます。詳細については、「[カスタム日時書式指定文字列](custom-datetime.md)」をご覧ください。 標準またはカスタムの書式指定文字列には、次の&2; とおりの使用方法があります。

* 書式設定操作によって生成される文字列を定義する。

* 解析操作によって [DateTime](xref:System.DateTime) または [DateTimeOffset](xref:System.DateTimeOffset) 値に変換できる日付と時刻の値のテキスト表現を定義する。

標準の日時書式指定文字列は、[DateTime](xref:System.DateTime) および [DateTimeOffset](xref:System.DateTimeOffset) の両方の値で使用できます。 

標準日時書式指定子を次の表に示します。 特に明記されない限り、特定の標準日時書式指定子は、[DateTime](xref:System.DateTime) 値で使用しても、[DateTimeOffset](xref:System.DateTimeOffset) 値で使用してもまったく同じ文字列形式を生成します。 標準の日時書式指定文字列の使用方法については、「[メモ](#notes)」をご覧ください。

書式指定子 | 説明 | 例
---------------- | ----------- | --------
"d" | 短い形式の日付パターン。 | `2009-06-15T13:45:30 -> 6/15/2009 (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 (fr-FR)`; `2009-06-15T13:45:30 -> 2009/06/15 (ja-JP)`
"D" | 長い形式の日付パターン。 | `2009-06-15T13:45:30 -> Monday, June 15, 2009 (en-US)`; `2009-06-15T13:45:30 -> 15 июня 2009 г. (ru-RU)`; `2009-06-15T13:45:30 -> Montag, 15. Juni 2009 (de-DE)`
"f" | 完全な日付と時刻のパターン (短い形式の時刻)。 | `2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 13:45 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45 μμ (el-GR)`
"F" | 完全な日付と時刻のパターン (長い形式の時刻)。 | `2009-06-15T13:45:30 -> Monday, June 15, 2009 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 13:45:30 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 1:45:30 μμ (el-GR)`
"g" | 一般の日付と時刻のパターン (短い形式の時刻)。 | `2009-06-15T13:45:30 -> 6/15/2009 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 13:45 (es-ES)`; `2009-06-15T13:45:30 -> 2009/6/15 13:45 (zh-CN)`
"G" | 一般の日付と時刻のパターン (長い形式の時刻)。 | `2009-06-15T13:45:30 -> 6/15/2009 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> 15/06/2009 13:45:30 (es-ES)`; `2009-06-15T13:45:30 -> 2009/6/15 13:45:30 (zh-CN)`
"M"、"m' | 月日パターン。 | `2009-06-15T13:45:30 -> June 15 (en-US)`; `2009-06-15T13:45:30 -> 15. juni (da-DK)`; `2009-06-15T13:45:30 -> 15 Juni (id-ID)`
"O"、"o" | ラウンドトリップする日付と時刻のパターン。 | [DateTime](xref:System.DateTime) 値: `2009-06-15T13:45:30 (DateTimeKind.Local) --> 2009-06-15T13:45:30.0000000-07:00`; `2009-06-15T13:45:30 (DateTimeKind.Utc) --> 2009-06-15T13:45:30.0000000Z`; `2009-06-15T13:45:30 (DateTimeKind.Unspecified) --> 2009-06-15T13:45:30.0000000` [DateTimeOffset](xref:System.DateTimeOffset) 値: `2009-06-15T13:45:30-07:00 --> 2009-06-15T13:45:30.0000000-07:00`
"R"、"r" | RFC1123 パターン。 | `2009-06-15T13:45:30 -> Mon, 15 Jun 2009 20:45:30 GMT`
"s" | 並べ替え可能な日付と時刻のパターン。 | `2009-06-15T13:45:30 (DateTimeKind.Local) -> 2009-06-15T13:45:30`; `2009-06-15T13:45:30 (DateTimeKind.Utc) -> 2009-06-15T13:45:30`
"t" | 短い形式の時刻パターン。 | `2009-06-15T13:45:30 -> 1:45 PM (en-US)`; `2009-06-15T13:45:30 -> 13:45 (hr-HR)`; `2009-06-15T13:45:30 -> 01:45 م (ar-EG)` 
"T" | 長い形式の時刻パターン。 | `2009-06-15T13:45:30 -> 1:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> 13:45:30 (hr-HR)`; `2009-06-15T13:45:30 -> 01:45:30 م (ar-EG)`
"u" | 並べ替え可能な日付と時刻のパターン (世界時刻)。 | [DateTime](xref:System.DateTime) 値の場合: `2009-06-15T13:45:30 -> 2009-06-15 13:45:30Z` [DateTimeOffset](xref:System.DateTimeOffset) 値の場合: `2009-06-15T13:45:30 -> 2009-06-15 20:45:30Z`
"U" | 完全な日付と時刻のパターン (世界時刻)。 | `2009-06-15T13:45:30 -> Monday, June 15, 2009 8:45:30 PM (en-US)`; `2009-06-15T13:45:30 -> den 15 juni 2009 20:45:30 (sv-SE)`; `2009-06-15T13:45:30 -> Δευτέρα, 15 Ιουνίου 2009 8:45:30 μμ (el-GR)`
"Y"、"y" | 年月パターン。 | `2009-06-15T13:45:30 -> June, 2009 (en-US)`; `2009-06-15T13:45:30 -> juni 2009 (da-DK)`; `2009-06-15T13:45:30 -> Juni 2009 (id-ID)`
その他の&1; 文字 | 未定義の指定子。 | ランタイム [FormatException](xref:System.FormatException) をスローします。

## <a name="how-standard-format-strings-work"></a>標準書式指定文字列の動作

書式設定操作では、標準書式指定文字列はカスタム書式指定文字列のエイリアスにすぎません。 エイリアスを使ってカスタム書式指定文字列を表すことの利点は、カスタム書式指定文字列はそれ自体が変化する場合があるのに対し、エイリアスは不変であるという点です。 通常、日付と時刻の値の文字列形式はカルチャによって変わるため、この点は重要です。 たとえば、"d" 標準書式指定文字列は、日付と時刻の値を短い日付形式のパターンで表示することを意味します。 インバリアント カルチャでは、このパターンは "MM/dd/yyyy" になります。 fr-FR カルチャでは、これが "dd/MM/yyyy" になります。 ja-JP カルチャでは、これが "yyyy/MM/dd" になります。

書式設定操作の標準書式指定文字列が特定のカルチャのカスタム書式指定文字列に対応付けられている場合は、使用するカスタム書式指定文字列に該当するカルチャを次のいずれかの方法で定義できます。

* 既定の (現在の) カルチャを使用できます。 次の例では、現在のカルチャの短い日付形式を使って日付を表示します。 この場合、現在のカルチャは en-US です。 

  ```csharp
  // Display using current (en-us) culture's short date format
  DateTime thisDate = new DateTime(2008, 3, 15);
  Console.WriteLine(thisDate.ToString("d"));           // Displays 3/15/2008
  ```

  ```vb
  ' Display using current (en-us) culture's short date format
  Dim thisDate As Date = #03/15/2008#
  Console.WriteLine(thisDate.ToString("d"))     ' Displays 3/15/2008
  ```
  
* 使用する書式のカルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトを、[IFormatProvider](xref:System.IFormatProvider) パラメーターを持つメソッドに渡すことができます。 次の例では、pt-BR カルチャの短い日付形式を使って日付を表示します。
  
  ```csharp
  // Display using pt-BR culture's short date format
  DateTime thisDate = new DateTime(2008, 3, 15);
  CultureInfo culture = new CultureInfo("pt-BR");      
  Console.WriteLine(thisDate.ToString("d", culture));  // Displays 15/3/2008
  ```

  ```vb
  ' Display using pt-BR culture's short date format
  Dim thisDate As Date = #03/15/2008#
  Dim culture As New CultureInfo("pt-BR")      
  Console.WriteLine(thisDate.ToString("d", culture))   ' Displays 15/3/2008
  ```
  
* 書式情報を提供する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトを、[IFormatProvider](xref:System.IFormatProvider) パラメーターを持つメソッドに渡すことができます。 次の例では、hr-HR カルチャの DateTimeFormatInfo オブジェクトに基づく短い日付形式で日付を表示します。  

  ```csharp
  // Display using date format information from hr-HR culture
  DateTime thisDate = new DateTime(2008, 3, 15);
  DateTimeFormatInfo fmt = (new CultureInfo("hr-HR")).DateTimeFormat;
  Console.WriteLine(thisDate.ToString("d", fmt));      // Displays 15.3.2008
  ```

  ```vb
  ' Display using date format information from hr-HR culture
  Dim thisDate As Date = #03/15/2008#
  Dim fmt As DateTimeFormatInfo = (New CultureInfo("hr-HR")).DateTimeFormat
  Console.WriteLine(thisDate.ToString("d", fmt))   ' Displays 15.3.2008
  ```
  
標準書式指定文字列には、長いカスタム書式指定文字列に代わる、不変の省略形としての利用価値もあります。 このカテゴリに該当する標準書式指定文字列は、"O" (または "o")、"R" (または "r")、"s"、"u" の&4; つです。 これらの文字列は、インバリアント カルチャで定義されたカスタム書式指定文字列に対応します。 これらの書式指定文字列によって生成される日時値の文字列形式は、カルチャに関係なく一定です。 次の表で、この&4; つの標準日時書式指定文字列について説明します。

標準書式指定文字列 | DateTimeFormatInfo.InvariantInfo プロパティによる定義 | カスタム書式指定文字列
---------------------- | ---------------------------------------------------- | --------------------
"O" または "o" | なし | yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzz
"R" または "r" | [RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) | ddd, dd MMM yyyy HH':'mm':'ss 'GMT'
"s" | [SortableDateTime](xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern) | yyyy'-'MM'-'dd'T'HH':'mm':'ss
"u" | [UniversalSortableDateTime](xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern) | yyyy'-'MM'-'dd HH':'mm':'ss'Z'

以降のセクションでは、[DateTime](xref:System.DateTime) および [DateTimeOffset](xref:System.DateTimeOffset) 値の標準書式指定子について説明します。

## <a name="the-short-date-d-format-specifier"></a>短い形式の日付 ("d") 書式指定子

"d" 標準書式指定子は、特定のカルチャの [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 たとえば、インバリアント カルチャの [ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) プロパティによって返されるカスタム書式指定文字列は "MM/dd/yyyy" です。 

次の表に、返される文字列の書式を制御する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。
次の例では、"d" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008,4, 10);
Console.WriteLine(date1.ToString("d", DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays 4/10/2008                       
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("en-NZ")));
// Displays 10/04/2008                       
Console.WriteLine(date1.ToString("d", 
                  CultureInfo.CreateSpecificCulture("de-DE")));
// Displays 10.04.2008 
```

```vb
Dim date1 As Date = #4/10/2008#
Console.WriteLine(date1.ToString("d", DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays 4/10/2008                       
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("en-NZ")))
' Displays 10/04/2008                       
Console.WriteLine(date1.ToString("d", _
                  CultureInfo.CreateSpecificCulture("de-DE")))
' Displays 10.04.2008 
```

## <a name="the-long-date-d-format-specifier"></a>長い形式の日付 ("D") 書式指定子

"D" 標準書式指定子は、現在の [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 たとえば、インバリアント カルチャのカスタム書式指定文字列は "dddd, dd MMMM yyyy" です。

次の表に、返される文字列の書式を制御する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。

プロパティ | 説明
-------- | -----------
[LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) | 結果文字列の全体的な書式を定義します。
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | 結果文字列に含まれるローカライズされた日付の名前を定義します。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 結果文字列に含まれるローカライズされた月の名前を定義します。

次の例では、"D" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10);
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008                        
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("pt-BR")));
// Displays quinta-feira, 10 de abril de 2008                        
Console.WriteLine(date1.ToString("D", 
                  CultureInfo.CreateSpecificCulture("es-MX")));
// Displays jueves, 10 de abril de 2008
```

```vb
Dim date1 As Date = #4/10/2008#
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008                        
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("pt-BR")))
' Displays quinta-feira, 10 de abril de 2008                        
Console.WriteLine(date1.ToString("D", _
                  CultureInfo.CreateSpecificCulture("es-MX")))
' Displays jueves, 10 de abril de 2008
```

## <a name="the-full-date-short-time-f-format-specifier"></a>完全な日付と短い形式の時刻 ("f") 書式指定子

"f" 標準書式指定子は、長い形式の日付 ("D") パターンと短い形式の時刻 ("t") パターンを空白で区切って組み合わせて表します。

結果文字列は、特定の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、返される文字列の書式を制御できる [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。 一部のカルチャの [DateTimeFormatInfo.LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) および [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) プロパティによって返されるカスタム書式指定子では、一部のプロパティが使用されない場合があります。

プロパティ | 説明
-------- | -----------
[LongDatePattern](xref:System.Globalization.DateTimeFormatInfo.LongDatePattern) | 結果文字列の日付要素の書式を定義します。
[ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | 結果文字列の時刻要素の書式を定義します。
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | 結果文字列に含まれるローカライズされた日付の名前を定義します。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 結果文字列に含まれるローカライズされた月の名前を定義します。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 午前 0 時から正午前までの時刻を 12 時間形式で示す文字列を定義します。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 正午から午前 0 時前までの時刻を 12 時間形式で示す文字列を定義します。

次の例では、"f" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("f", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 6:30 AM                        
Console.WriteLine(date1.ToString("f", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays jeudi 10 avril 2008 06:30 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("f", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 6:30 AM                        
Console.WriteLine(date1.ToString("f", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays jeudi 10 avril 2008 06:30 
```

## <a name="the-full-date-long-time-f-format-specifier"></a>完全な日付と長い形式の時刻 ("F") 書式指定子

"F" 標準書式指定子は、現在の [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 たとえば、インバリアント カルチャのカスタム書式指定文字列は "dddd, dd MMMM yyyy HH:mm:ss" です。

次の表に、返される文字列の書式を制御できる [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。 一部のカルチャの [FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) プロパティによって返されるカスタム書式指定子では、一部のプロパティが使用されない場合があります。

プロパティ | 説明
-------- | -----------
[FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) | 結果文字列の全体的な書式を定義します。
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | 結果文字列に含まれるローカライズされた日付の名前を定義します。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 結果文字列に含まれるローカライズされた月の名前を定義します。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 午前 0 時から正午前までの時刻を 12 時間形式で示す文字列を定義します。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 正午から午前 0 時前までの時刻を 12 時間形式で示す文字列を定義します。

次の例では、"F" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("F", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("F", 
                  CultureInfo.CreateSpecificCulture("fr-FR")));
// Displays jeudi 10 avril 2008 06:30:00 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("F", _
                  CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("F", _
                  CultureInfo.CreateSpecificCulture("fr-FR")))
' Displays jeudi 10 avril 2008 06:30:00 
```

## <a name="the-general-date-short-time-g-format-specifier"></a>一般の日付と短い形式の時刻 ("g") 書式指定子

"g" 標準書式指定子は、短い形式の日付 ("d") パターンと短い形式の時刻 ("t") パターンを空白で区切って組み合わせて表します。

結果文字列は、特定の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、返される文字列の書式を制御できる [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。 一部のカルチャの [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) および [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) プロパティによって返されるカスタム書式指定子では、一部のプロパティが使用されない場合があります。

プロパティ | 説明
-------- | -----------
[ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) | 結果文字列の日付要素の書式を定義します。
[ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | 結果文字列の時刻要素の書式を定義します。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 午前 0 時から正午前までの時刻を 12 時間形式で示す文字列を定義します。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 正午から午前 0 時前までの時刻を 12 時間形式で示す文字列を定義します。

次の例では、"g" 書式指定子を使用して、日付と時刻の値を表示します。 

``` csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("g", 
                  DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008 06:30                      
Console.WriteLine(date1.ToString("g", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 4/10/2008 6:30 AM                       
Console.WriteLine(date1.ToString("g", 
                  CultureInfo.CreateSpecificCulture("fr-BE")));
// Displays 10/04/2008 6:30 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("g", _
                  DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008 06:30                      
Console.WriteLine(date1.ToString("g", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 4/10/2008 6:30 AM                       
Console.WriteLine(date1.ToString("g", _
                  CultureInfo.CreateSpecificCulture("fr-BE")))
' Displays 10/04/2008 6:30  
```

## <a name="the-general-date-long-time-g-format-specifier"></a>一般の日付と長い形式の時刻 ("G") 書式指定子

"G" 標準書式指定子は、短い形式の日付 ("d") パターンと長い形式の時刻 ("T") パターンを空白で区切って組み合わせて表します。

結果文字列は、特定の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、返される文字列の書式を制御できる [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。 一部のカルチャの [DateTimeFormatInfo.ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) および [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) プロパティによって返されるカスタム書式指定子では、一部のプロパティが使用されない場合があります。

プロパティ | 説明
-------- | -----------
[ShortDatePattern](xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern) | 結果文字列の日付要素の書式を定義します。
[LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) | 結果文字列の時刻要素の書式を定義します。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 午前 0 時から正午前までの時刻を 12 時間形式で示す文字列を定義します。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 正午から午前 0 時前までの時刻を 12 時間形式で示す文字列を定義します。

次の例では、"G" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("G", 
                  DateTimeFormatInfo.InvariantInfo));
// Displays 04/10/2008 06:30:00
Console.WriteLine(date1.ToString("G", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 4/10/2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("G", 
                  CultureInfo.CreateSpecificCulture("nl-BE")));
// Displays 10/04/2008 6:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("G", _
                  DateTimeFormatInfo.InvariantInfo))
' Displays 04/10/2008 06:30:00
Console.WriteLine(date1.ToString("G", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 4/10/2008 6:30:00 AM                        
Console.WriteLine(date1.ToString("G", _
                  CultureInfo.CreateSpecificCulture("nl-BE")))
' Displays 10/04/2008 6:30:00                       
```

## <a name="the-month-m-m-format-specifier"></a>月 ("M"、"m") 書式指定子

"M" または "m" 標準書式指定子は、現在の [DateTimeFormatInfo.MonthDayPattern](xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 たとえば、インバリアント カルチャのカスタム書式指定文字列は "MMMM dd" です。

次の表に、返される文字列の書式を制御する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。

プロパティ | 説明
-------- | -----------
[MonthDayPattern](xref:System.Globalization.DateTimeFormatInfo.MonthDayPattern) | 結果文字列の全体的な書式を定義します。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 結果文字列に含まれるローカライズされた月の名前を定義します。

次の例では、"m" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("m", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays April 10                        
Console.WriteLine(date1.ToString("m", 
                  CultureInfo.CreateSpecificCulture("ms-MY")));
// Displays 10 April  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("m", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays April 10                        
Console.WriteLine(date1.ToString("m", _
                  CultureInfo.CreateSpecificCulture("ms-MY")))
' Displays 10 April
```

## <a name="the-round-trip-o-o-format-specifier"></a>ラウンドトリップ ("O"、"o") 書式指定子

"O" または "o" 標準書式指定子は、タイム ゾーン情報を保持するパターンを使用するカスタム日時書式指定文字列を表し、ISO 8601 に準拠する結果文字列を生成します。 この書式指定子は、[DateTime](xref:System.DateTime) 値の日付と時刻の値を、[DateTime.Kind](xref:System.DateTime.Kind) プロパティと共にテキストとして保持できるように設計されています。 styles パラメーターが [DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) に設定されている場合は、[DateTime.Parse(String, IFormatProvider, DateTimeStyles)](xref:System.DateTime.Parse(System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) または [DateTime.ParseExact](xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles)) メソッドを使用して、書式設定された文字列を変換前の文字列に戻すことができます。 

"O" または "o" 標準書式指定子は、DateTime 値の "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" カスタム書式指定文字列と [DateTimeOffset](xref:System.DateTimeOffset) 値の "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffzzz" カスタム書式指定文字列に対応します。 この文字列の中で、個々の文字 (ハイフン、コロン、アルファベットの "T" など) を区切る一対の単一引用符は、各文字がリテラルであって変更できないことを示します。 アポストロフィは、出力された文字列には現れません。 

"O" または "o" 標準書式指定子 (および "yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'fffffffK" カスタム書式指定文字列) は、[DateTime](xref:System.DateTime) 値の [Kind](xref:System.DateTime.Kind) プロパティを保持するため、ISO 8601 の 3 種類のタイム ゾーン情報表記形式を利用します。 

* [DateTimeKind.Local](xref:System.DateTimeKind.Local) 日時値のタイム ゾーン コンポーネントは、UTC からのオフセットです (例: +01:00、-07:00)。 すべての DateTimeOffset 値もこの形式で表記されます。 

* [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) 日時値のタイム ゾーン コンポーネントは、"Z" (ゼロ オフセットを示す) を使用して UTC を表記します。 

* [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) 日時値にはタイム ゾーン情報はありません。 

"O" または "o" 標準書式指定子は国際基準に準拠しているため、この指定子を使用する書式設定操作または解析操作では常に、インバリアント カルチャとグレゴリオ暦が使用されます。 

[DateTime](xref:System.DateTime) と [DateTimeOffset](xref:System.DateTimeOffset) の `Parse`、`TryParse`、`ParseExact`、および `TryParseExact` メソッドに渡される文字列が、これらの書式で表記される場合には、書式指定子 "O" または "o" を使用して解析できます。 [DateTime](xref:System.DateTime) オブジェクトの場合、呼び出す解析オーバーロードには、[DateTimeStyles.RoundtripKind](xref:System.Globalization.DateTimeStyles.RoundtripKind) の値が指定された styles パラメーターも含まれている必要があります。 "O" または "o" 書式指定子に対応するカスタム書式文字列を使用して解析メソッドを呼び出した結果は、"O" または "o" を使用した場合の結果と同じではないことに注意してください。 これは、カスタム書式文字列を使用する解析メソッドでは、タイム ゾーン コンポーネントがない日時値または "Z" を使用して UTC を示している日時値の文字列形式を解析できないためです。 

次の例では、米国太平洋標準時タイム ゾーンのシステム上で "o" 書式指定子を使用して、一連の [DateTime](xref:System.DateTime) 値および [DateTimeOffset](xref:System.DateTimeOffset) 値を表示します。 

```csharp
using System;

public class Example
{
   public static void Main()
   {
       DateTime dat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                   DateTimeKind.Unspecified);
       Console.WriteLine("{0} ({1}) --> {0:O}", dat, dat.Kind); 

       DateTime uDat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                    DateTimeKind.Utc);
       Console.WriteLine("{0} ({1}) --> {0:O}", uDat, uDat.Kind);

       DateTime lDat = new DateTime(2009, 6, 15, 13, 45, 30, 
                                    DateTimeKind.Local);
       Console.WriteLine("{0} ({1}) --> {0:O}\n", lDat, lDat.Kind);

       DateTimeOffset dto = new DateTimeOffset(lDat);
       Console.WriteLine("{0} --> {0:O}", dto);
   }
}
// The example displays the following output:
//    6/15/2009 1:45:30 PM (Unspecified) --> 2009-06-15T13:45:30.0000000
//    6/15/2009 1:45:30 PM (Utc) --> 2009-06-15T13:45:30.0000000Z
//    6/15/2009 1:45:30 PM (Local) --> 2009-06-15T13:45:30.0000000-07:00
//    
//    6/15/2009 1:45:30 PM -07:00 --> 2009-06-15T13:45:30.0000000-07:00
```

```vb
Module Example
   Public Sub Main()
       Dim dat As New Date(2009, 6, 15, 13, 45, 30, 
                           DateTimeKind.Unspecified)
       Console.WriteLine("{0} ({1}) --> {0:O}", dat, dat.Kind) 

       Dim uDat As New Date(2009, 6, 15, 13, 45, 30, DateTimeKind.Utc)
       Console.WriteLine("{0} ({1}) --> {0:O}", uDat, uDat.Kind)

       Dim lDat As New Date(2009, 6, 15, 13, 45, 30, DateTimeKind.Local)
       Console.WriteLine("{0} ({1}) --> {0:O}", lDat, lDat.Kind)
       Console.WriteLine()

       Dim dto As New DateTimeOffset(lDat)
       Console.WriteLine("{0} --> {0:O}", dto)
   End Sub
End Module
' The example displays the following output:
'    6/15/2009 1:45:30 PM (Unspecified) --> 2009-06-15T13:45:30.0000000
'    6/15/2009 1:45:30 PM (Utc) --> 2009-06-15T13:45:30.0000000Z
'    6/15/2009 1:45:30 PM (Local) --> 2009-06-15T13:45:30.0000000-07:00
'    
'    6/15/2009 1:45:30 PM -07:00 --> 2009-06-15T13:45:30.0000000-07:00
```

次の例では、"o" 書式指定子を使用して書式設定された文字列を作成し、日付および時刻の `Parse` メソッドを呼び出して元の日時値を復元します。

```csharp
// Round-trip DateTime values.
DateTime originalDate, newDate;
string dateString;
// Round-trip a local time.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 10, 6, 30, 0), DateTimeKind.Local);
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);
// Round-trip a UTC time.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 12, 9, 30, 0), DateTimeKind.Utc);                  
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);
// Round-trip time in an unspecified time zone.
originalDate = DateTime.SpecifyKind(new DateTime(2008, 4, 13, 12, 30, 0), DateTimeKind.Unspecified);                  
dateString = originalDate.ToString("o");
newDate = DateTime.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, 
                  newDate, newDate.Kind);

// Round-trip a DateTimeOffset value.
DateTimeOffset originalDTO = new DateTimeOffset(2008, 4, 12, 9, 30, 0, new TimeSpan(-8, 0, 0));
dateString = originalDTO.ToString("o");
DateTimeOffset newDTO = DateTimeOffset.Parse(dateString, null, DateTimeStyles.RoundtripKind);
Console.WriteLine("Round-tripped {0} to {1}.", originalDTO, newDTO);
// The example displays the following output:
//    Round-tripped 4/10/2008 6:30:00 AM Local to 4/10/2008 6:30:00 AM Local.
//    Round-tripped 4/12/2008 9:30:00 AM Utc to 4/12/2008 9:30:00 AM Utc.
//    Round-tripped 4/13/2008 12:30:00 PM Unspecified to 4/13/2008 12:30:00 PM Unspecified.
//    Round-tripped 4/12/2008 9:30:00 AM -08:00 to 4/12/2008 9:30:00 AM -08:00.
```

```vb
' Round-trip DateTime values.
Dim originalDate, newDate As Date
Dim dateString As String
' Round-trip a local time.
originalDate = Date.SpecifyKind(#4/10/2008 6:30AM#, DateTimeKind.Local)
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)
' Round-trip a UTC time.
originalDate = Date.SpecifyKind(#4/12/2008 9:30AM#, DateTimeKind.Utc)                  
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)
' Round-trip time in an unspecified time zone.
originalDate = Date.SpecifyKind(#4/13/2008 12:30PM#, DateTimeKind.Unspecified)                  
dateString = originalDate.ToString("o")
newDate = Date.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} {1} to {2} {3}.", originalDate, originalDate.Kind, _
                  newDate, newDate.Kind)

' Round-trip a DateTimeOffset value.
Dim originalDTO As New DateTimeOffset(#4/12/2008 9:30AM#, New TimeSpan(-8, 0, 0))
dateString = originalDTO.ToString("o")
Dim newDTO As DateTimeOffset = DateTimeOffset.Parse(dateString, Nothing, DateTimeStyles.RoundtripKind)
Console.WriteLine("Round-tripped {0} to {1}.", originalDTO, newDTO)
' The example displays the following output:
'    Round-tripped 4/10/2008 6:30:00 AM Local to 4/10/2008 6:30:00 AM Local.
'    Round-tripped 4/12/2008 9:30:00 AM Utc to 4/12/2008 9:30:00 AM Utc.
'    Round-tripped 4/13/2008 12:30:00 PM Unspecified to 4/13/2008 12:30:00 PM Unspecified.
'    Round-tripped 4/12/2008 9:30:00 AM -08:00 to 4/12/2008 9:30:00 AM -08:00.
```

## <a name="the-rfc1123-r-r-format-specifier"></a>RFC1123 ("R"、"r") 書式指定子

"R" または "r" 標準書式指定子は、[DateTimeFormatInfo.RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 このパターンは定義済みの標準を反映し、プロパティは読み取り専用です。 したがって、使用されるカルチャまたは指定された書式プロバイダーに関係なく、常に同じです。 カスタム書式指定文字列は、"ddd, dd MMM yyyy HH':'mm':'ss 'GMT'" です。 この標準書式指定子を使用した場合、書式設定操作または解析操作で常にインバリアント カルチャが使用されます。

結果文字列は、インバリアント カルチャを表す [DateTimeFormatInfo.InvariantInfo](xref:System.Globalization.DateTimeFormatInfo.InvariantInfo) プロパティによって返される [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトの次のプロパティに影響されます。

プロパティ | 説明
-------- | -----------
[RFC1123Pattern](xref:System.Globalization.DateTimeFormatInfo.RFC1123Pattern) | 結果文字列の書式を定義します。
[AbbreviatedDayNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedDayNames) | 結果文字列に含まれる日付の省略名を定義します。
[AbbreviatedMonthNames](xref:System.Globalization.DateTimeFormatInfo.AbbreviatedMonthNames) | 結果文字列に含まれる月の省略名を定義します。

RFC 1123 標準では、時刻は世界協定時刻 (UTC) で表されますが、書式設定操作では、書式設定される [DateTime](xref:System.DateTime) オブジェクトの値は変更されません。 そのため、書式設定操作を行う前に [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) メソッドを呼び出して、[DateTime](xref:System.DateTime) 値を UTC に変換する必要があります。 一方、[DateTimeOffset](xref:System.DateTimeOffset) 値では、この変換が自動的に行われます。書式設定操作の前に [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) メソッドを呼び出す必要はありません。 

次の例では、米国太平洋標準時タイム ゾーンのシステム上で "r" 書式指定子を使用して、[DateTime](xref:System.DateTime) および [DateTimeOffset](xref:System.DateTimeOffset) 値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
DateTimeOffset dateOffset = new DateTimeOffset(date1, 
                            TimeZoneInfo.Local.GetUtcOffset(date1));
Console.WriteLine(date1.ToUniversalTime().ToString("r"));
// Displays Thu, 10 Apr 2008 13:30:00 GMT                       
Console.WriteLine(dateOffset.ToUniversalTime().ToString("r"));
// Displays Thu, 10 Apr 2008 13:30:00 GMT  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Dim dateOffset As New DateTimeOffset(date1, TimeZoneInfo.Local.GetUtcOFfset(date1))
Console.WriteLine(date1.ToUniversalTime.ToString("r"))
' Displays Thu, 10 Apr 2008 13:30:00 GMT                       
Console.WriteLine(dateOffset.ToUniversalTime.ToString("r"))
' Displays Thu, 10 Apr 2008 13:30:00 GMT
```

## <a name="the-sortable-s-format-specifier"></a>並べ替え可能な日付と時刻 ("s") 書式指定子

"s" 標準書式指定子は、[DateTimeFormatInfo.SortableDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.SortableDateTimePattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 このパターンは定義済みの標準 (ISO 8601) を反映し、プロパティは読み取り専用です。 したがって、使用されるカルチャまたは指定された書式プロバイダーに関係なく、常に同じです。 カスタム書式指定文字列は、"yyyy'-'MM'-'dd'T'HH':'mm':'ss" です。

"s" 書式指定子の目的は、日付と時刻の値に基づいて、一貫して昇順または降順で並べ替える結果の文字列を作成することです。 そのため、"s" 標準書式指定子は一貫性のある形式で日付と時刻の値を表していますが、書式設定操作によって、書式設定の対象となる日付と時刻のオブジェクトの値が、その [DateTime.Kind](xref:System.DateTime.Kind) プロパティや [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) 値を反映するように変更されることはありません。 たとえば、日付と時刻値の 2014-11-15T18:32:17+00:00 と 2014-11-15T18:32:17+08:00 を書式設定することで生成される結果文字列は同じになります。 

この標準書式指定子を使用した場合、書式設定操作または解析操作で常にインバリアント カルチャが使用されます。 

次の例では、米国太平洋標準時タイム ゾーンのシステム上で "s" 書式指定子を使用して、[DateTime](xref:System.DateTime) および [DateTimeOffset](xref:System.DateTimeOffset) 値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("s"));
// Displays 2008-04-10T06:30:00
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("s"))
' Displays 2008-04-10T06:30:00 
```

## <a name="the-short-time-t-format-specifier"></a>短い形式の時刻 ("t") 書式指定子

"t" 標準書式指定子は、現在の [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 たとえば、インバリアント カルチャのカスタム書式指定文字列は "HH:mm" です。

結果文字列は、特定の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトの書式情報に影響されます。 次の表に、返される文字列の書式を制御できる [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。 一部のカルチャの [DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) プロパティによって返されるカスタム書式指定子では、一部のプロパティが使用されない場合があります。

プロパティ | 説明
-------- | -----------
[DateTimeFormatInfo.ShortTimePattern](xref:System.Globalization.DateTimeFormatInfo.ShortTimePattern) | 結果文字列の時刻要素の書式を定義します。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 午前 0 時から正午前までの時刻を 12 時間形式で示す文字列を定義します。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 正午から午前 0 時前までの時刻を 12 時間形式で示す文字列を定義します。

次の例では、"t" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("t", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 6:30 AM                        
Console.WriteLine(date1.ToString("t", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays 6:30  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("t", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 6:30 AM                        
Console.WriteLine(date1.ToString("t", _
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays 6:30
```

## <a name="the-long-time-t-format-specifier"></a>長い形式の時刻 ("T") 書式指定子

"T" 標準書式指定子は、特定のカルチャの [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 たとえば、インバリアント カルチャのカスタム書式指定文字列は "HH:mm:ss" です。

次の表に、返される文字列の書式を制御できる [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。 一部のカルチャの [DateTimeFormatInfo.LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) プロパティによって返されるカスタム書式指定子では、一部のプロパティが使用されない場合があります。

プロパティ | 説明
-------- | -----------
[LongTimePattern](xref:System.Globalization.DateTimeFormatInfo.LongTimePattern) | 結果文字列の時刻要素の書式を定義します。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 午前 0 時から正午前までの時刻を 12 時間形式で示す文字列を定義します。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 正午から午前 0 時前までの時刻を 12 時間形式で示す文字列を定義します。

次の例では、"T" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("T", 
                  CultureInfo.CreateSpecificCulture("en-us")));
// Displays 6:30:00 AM                       
Console.WriteLine(date1.ToString("T", 
                  CultureInfo.CreateSpecificCulture("es-ES")));
// Displays 6:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("T", _
                  CultureInfo.CreateSpecificCulture("en-us")))
' Displays 6:30:00 AM                       
Console.WriteLine(date1.ToString("T", _
                  CultureInfo.CreateSpecificCulture("es-ES")))
' Displays 6:30:00 
```

## <a name="the-universal-sortable-u-format-specifier"></a>世界共通の並べ替え可能な日付と時刻 ("u") 書式指定子

"u" 標準書式指定子は、[DateTimeFormatInfo.UniversalSortableDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 このパターンは定義済みの標準を反映し、プロパティは読み取り専用です。 したがって、使用されるカルチャまたは指定された書式プロバイダーに関係なく、常に同じです。 カスタム書式指定文字列は、"yyyy'-'MM'-'dd HH':'mm':'ss'Z'" です。 この標準書式指定子を使用した場合、書式設定操作または解析操作で常にインバリアント カルチャが使用されます。 

結果文字列では、時刻は世界協定時刻 (UTC) で表される必要がありますが、書式設定操作では、元の [DateTime](xref:System.DateTime) 値の変換は実行されません。 そのため、書式設定する前に [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) メソッドを呼び出して、[DateTime](xref:System.DateTime) 値を UTC に変換する必要があります。 一方、[DateTimeOffset](xref:System.DateTimeOffset) 値では、この変換が自動的に行われます。書式設定操作の前に [DateTimeOffset.ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) メソッドを呼び出す必要はありません。   

次の例では、"u" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToUniversalTime().ToString("u"));
// Displays 2008-04-10 13:30:00Z
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToUniversalTime.ToString("u"))
' Displays 2008-04-10 13:30:00Z                       
```

## <a name="the-universal-full-u-format-specifier"></a>世界共通の完全な日付と時刻 ("U") 書式指定子

"U" 標準書式指定子は、指定されたカルチャの [DateTimeFormatInfo.FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 このパターンは、"F" パターンと同じです。 ただし、[DateTime](xref:System.DateTime) 値は、書式設定される前に、自動的に UTC に変換されます。

次の表に、返される文字列の書式を制御できる [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。 一部のカルチャの [FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) プロパティによって返されるカスタム書式指定子では、一部のプロパティが使用されない場合があります。

プロパティ | 説明
-------- | -----------
[FullDateTimePattern](xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern) | 結果文字列の全体的な書式を定義します。
[DayNames](xref:System.Globalization.DateTimeFormatInfo.DayNames) | 結果文字列に含まれるローカライズされた日付の名前を定義します。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 結果文字列に含まれるローカライズされた月の名前を定義します。
[AMDesignator](xref:System.Globalization.DateTimeFormatInfo.AMDesignator) | 午前 0 時から正午前までの時刻を 12 時間形式で示す文字列を定義します。
[PMDesignator](xref:System.Globalization.DateTimeFormatInfo.PMDesignator) | 正午から午前 0 時前までの時刻を 12 時間形式で示す文字列を定義します。

"U" 書式指定子は、[DateTimeOffset](xref:System.DateTimeOffset) 型ではサポートされません。この書式指定子を使って [DateTimeOffset](xref:System.DateTimeOffset) 値の書式を設定しようとすると、[FormatException](xref:System.FormatException) がスローされます。

次の例では、"U" 書式指定子を使用して、日付と時刻の値を表示します。

``` csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("U", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays Thursday, April 10, 2008 1:30:00 PM                       
Console.WriteLine(date1.ToString("U", 
                  CultureInfo.CreateSpecificCulture("sv-FI")));
// Displays den 10 april 2008 13:30:00  
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("U", CultureInfo.CreateSpecificCulture("en-US")))
' Displays Thursday, April 10, 2008 1:30:00 PM                       
Console.WriteLine(date1.ToString("U", CultureInfo.CreateSpecificCulture("sv-FI")))
' Displays den 10 april 2008 13:30:00                       
```

## <a name="the-year-month-y-y-format-specifier"></a>年月 ("Y"、"y") 書式指定子

"Y" または "y" 標準書式指定子は、特定のカルチャの [DateTimeFormatInfo.YearMonthPattern](xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern) プロパティで定義されるカスタム日時書式指定文字列を表します。 たとえば、インバリアント カルチャのカスタム書式指定文字列は "yyyy MMMM" です。

次の表に、返される文字列の書式を制御する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクト プロパティの一覧を示します。

プロパティ | 説明
-------- | -----------
[YearMonthPattern](xref:System.Globalization.DateTimeFormatInfo.YearMonthPattern) | 結果文字列の全体的な書式を定義します。
[MonthNames](xref:System.Globalization.DateTimeFormatInfo.MonthNames) | 結果文字列に含まれるローカライズされた月の名前を定義します。

次の例では、"y" 書式指定子を使用して、日付と時刻の値を表示します。

```csharp
DateTime date1 = new DateTime(2008, 4, 10, 6, 30, 0);
Console.WriteLine(date1.ToString("Y", 
                  CultureInfo.CreateSpecificCulture("en-US")));
// Displays April, 2008                       
Console.WriteLine(date1.ToString("y", 
                  CultureInfo.CreateSpecificCulture("af-ZA")));
// Displays April 2008 
```

```vb
Dim date1 As Date = #4/10/2008 6:30AM#
Console.WriteLine(date1.ToString("Y", CultureInfo.CreateSpecificCulture("en-US")))
' Displays April, 2008                       
Console.WriteLine(date1.ToString("y", CultureInfo.CreateSpecificCulture("af-ZA")))
' Displays April 2008
```                       

## <a name="notes"></a>ノート

### <a name="datetimeformatinfo-properties"></a>DateTimeFormatInfo のプロパティ

書式設定は、現在の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのプロパティの影響を受けます。このオブジェクトは、現在のスレッド カルチャによって暗黙的に指定されるか、または書式設定を実行するメソッドの [IFormatProvider](xref:System.IFormatProvider) パラメーターによって明示的に指定されます。 [IFormatProvider](xref:System.IFormatProvider) パラメーターには、カルチャを表す [CultureInfo](xref:System.Globalization.CultureInfo) オブジェクトを指定するか、特定のカルチャの日時書式設定規則を表す [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトを指定する必要があります。 標準日時書式指定子の多くは、現在の [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) オブジェクトのプロパティによって定義されている書式設定パターンのエイリアスです。 一部の標準日時書式指定子によって生成される結果は、対応する [DateTimeFormatInfo](xref:System.Globalization.DateTimeFormatInfo) プロパティの対応する日時形式パターンを変更することによって変えることができます。

## <a name="see-also"></a>関連項目

[型の書式設定](formatting-types.md)

[カスタム日時書式指定文字列](custom-datetime.md)


