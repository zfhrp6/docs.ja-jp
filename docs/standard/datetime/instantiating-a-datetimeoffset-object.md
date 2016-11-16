---
title: "DateTimeOffset オブジェクトのインスタンス化"
description: "DateTimeOffset オブジェクトのインスタンス化"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 476fe67b-6be4-4435-88ab-ced37304f1d1
translationtype: Human Translation
ms.sourcegitcommit: c40c28da09e8a122b542463c197196c82c81dd19
ms.openlocfilehash: 330371397d0ec258597e4e4f109f3f1bb35df6b7

---

# <a name="instantiating-a-datetimeoffset-object"></a>DateTimeOffset オブジェクトのインスタンス化

[System.DateTimeOffset](xref:System.DateTimeOffset) 構造体は、新しい [DateTimeOffset](xref:System.DateTimeOffset) 値を作成するためのさまざまな方法を提供します。 それらの多くは新しい [System.DateTime](xref:System.DateTime) 値をインスタンス化するために使用できるメソッドに直接対応し、世界協定時刻 (UTC) からの日時値のオフセットを指定できる拡張が加えられています。 特に、次の方法で、[DateTimeOffset](xref:System.DateTimeOffset) 値をインスタンス化できます。

* [DateTimeOffset](xref:System.DateTimeOffset) コンストラクターを呼び出す。

* 値を [DateTimeOffset](xref:System.DateTimeOffset) 値に暗黙的に変換する。

* 日付と時刻の文字列形式を解析する。

## <a name="date-and-time-literals"></a>日付と時刻のリテラル

これをサポートしている言語では、[DateTime](xref:System.DateTime) 値をインスタンス化する最も一般的な方法の 1 つが、ハード コーディングされたリテラル値として日付と時刻を指定することです。 たとえば、次の Visual Basic コードでは、値が 2008 年 1 月 1 日午前 10時 00分の [DateTime](xref:System.DateTime) オブジェクトを作成しています。

```vb
Dim literalDate1 As Date = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate1.ToString())
' Displays:
'              5/1/2008 8:06:32 AM
```

[DateTime](xref:System.DateTime) リテラルをサポートする言語を使用している場合は、日付と時刻のリテラルを使用して、[DateTimeOffset](xref:System.DateTimeOffset) 値を初期化することもできます。 たとえば、次の Visual Basic コードでは、[DateTimeOffset](xref:System.DateTimeOffset) オブジェクトを作成しています。

```vb
Dim literalDate As DateTimeOffset = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate.ToString())
' Displays:
'              5/1/2008 8:06:32 AM -07:00
```

コンソール出力に示すように、このように作成された [DateTimeOffset](xref:System.DateTimeOffset) 値には、ローカル タイム ゾーンのオフセットが割り当てられます。 つまり、文字リテラルを使用して割り当てられた [DateTimeOffset](xref:System.DateTimeOffset) 値は、別のコンピューターでコードが実行された場合に、単一の特定の時点を識別しないことを意味します。

## <a name="datetimeoffset-constructors"></a>DateTimeOffset コンストラクター

[System.DateTimeOffset](xref:System.DateTimeOffset) 型は、5 つのコンストラクターを定義します。 それらのうちの 3 つは、[DateTime](xref:System.DateTime) コンストラクターに直接対応し、UTC からの日付と時刻のオフセットを定義する [System.TimeSpan](xref:System.TimeSpan) 型のパラメーターが追加されています。 これらにより、個々の日付と時刻のコンポーネントの値に基づいて、[DateTimeOffset](xref:System.DateTimeOffset) 値を定義できます。 たとえば、次のコードはこれらの 3 つのコンストラクターを使用して、7/1/2008 12:05 AM +01:00 の同じ値で [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトをインスタンス化しています。

```csharp
DateTimeOffset dateAndTime;

// Instantiate date and time using years, months, days, 
// hours, minutes, and seconds
dateAndTime = new DateTimeOffset(2008, 5, 1, 8, 6, 32, 
                                 new TimeSpan(1, 0, 0));
Console.WriteLine(dateAndTime);
// Instantiate date and time using years, months, days,
// hours, minutes, seconds, and milliseconds
dateAndTime = new DateTimeOffset(2008, 5, 1, 8, 6, 32, 545, 
                                 new TimeSpan(1, 0, 0));
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), 
                             dateAndTime.ToString("zzz"));

// Instantiate date and time using number of ticks
// 05/01/2008 8:06:32 AM is 633,452,259,920,000,000 ticks
dateAndTime = new DateTimeOffset(633452259920000000, new TimeSpan(1, 0, 0));  
Console.WriteLine(dateAndTime);
// The example displays the following output to the console:
//       5/1/2008 8:06:32 AM +01:00
//       5/1/2008 8:06:32 AM +01:00
//       5/1/2008 8:06:32 AM +01:00
```

```vb
Dim dateAndTime As DateTimeOffset

' Instantiate date and time using years, months, days, 
' hours, minutes, and seconds
dateAndTime = New DateTimeOffset(2008, 5, 1, 8, 6, 32, _
                                 New TimeSpan(1, 0, 0))
Console.WriteLine(dateAndTime)
' Instantiate date and time using years, months, days,
' hours, minutes, seconds, and milliseconds
dateAndTime = New DateTimeOffset(2008, 5, 1, 8, 6, 32, 545, _
                                 New TimeSpan(1, 0, 0))
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), _
                             dateAndTime.ToString("zzz"))

' Instantiate date and time using Persian calendar with years,
' months, days, hours, minutes, seconds, and milliseconds
dateAndTime = New DateTimeOffset(1387, 2, 12, 8, 6, 32, 545, New PersianCalendar, New TimeSpan(1, 0, 0))
' Note that the console output displays the date in the Gregorian
' calendar, not the Persian calendar. 
Console.WriteLine("{0} {1}", dateAndTime.ToString("G"), _
                             dateAndTime.ToString("zzz"))

' Instantiate date and time using number of ticks
' 05/01/2008 8:06:32 AM is 633,452,259,920,000,000 ticks
dateAndTime = New DateTimeOffset(633452259920000000, New TimeSpan(1, 0, 0))  
Console.WriteLine(dateAndTime)
' The example displays the following output to the console:
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
'       5/1/2008 8:06:32 AM +01:00
```

[PersianCalendar](xref:System.Globalization.PersianCalendar) オブジェクトをそのコンストラクターへの引数の 1 つとして使用して、インスタンス化された [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトの値がコンソールに表示されると、ペルシャ暦ではなく、グレゴリオ暦の日付として表されることに注意してください。 

他の 2 つのコンストラクターは、DateTime 値から [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトを作成します。 1 つ目のコンストラクターには、[DateTimeOffset](xref:System.DateTimeOffset) 値に変換される 1 つのパラメーター [DateTime](xref:System.DateTime) 値があります。 結果の [DateTimeOffset](xref:System.DateTimeOffset) 値のオフセットは、コンストラクターの単一の [DateTime](xref:System.DateTime) パラメーターの [Kind](xref:System.DateTime.Kind) プロパティによって異なります。 その値が [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) の場合、オフセットは [TimeSpan.Zero](xref:System.TimeSpan.Zero) に等しい値に設定されます。 それ以外の場合、オフセットはローカル タイム ゾーンのオフセットと等しい値に設定されます。 次の例に、このコンストラクターを使用して、UTC とローカル タイム ゾーンを表す [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトをインスタンス化する方法を示します。

```csharp
// Declare date; Kind property is DateTimeKind.Unspecified
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
DateTimeOffset targetTime;

// Instantiate a DateTimeOffset value from a UTC time 
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = new DateTimeOffset(utcTime);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc, 
// the offset is TimeSpan.Zero.

// Instantiate a DateTimeOffset value from a UTC time with a zero offset
targetTime = new DateTimeOffset(utcTime, TimeSpan.Zero);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc, 
// the call to the constructor succeeds

// Instantiate a DateTimeOffset value from a UTC time with a negative offset
try
{
   targetTime = new DateTimeOffset(utcTime, new TimeSpan(-2, 0, 0));
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      targetTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM +00:00 failed.

// Instantiate a DateTimeOffset value from a local time
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = new DateTimeOffset(localTime);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Local, 
// the offset is that of the local time zone.

// Instantiate a DateTimeOffset value from an unspecified time
targetTime = new DateTimeOffset(sourceDate);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Unspecified, 
// the offset is that of the local time zone.
```

```vb
' Declare date; Kind property is DateTimeKind.Unspecified
Dim sourceDate As Date = #5/1/2008 8:30 AM#
Dim targetTime As DateTimeOffset

' Instantiate a DateTimeOffset value from a UTC time 
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = New DateTimeOffset(utcTime)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM +00:00
' Because the Kind property is DateTimeKind.Utc, 
' the offset is TimeSpan.Zero.


' Instantiate a DateTimeOffset value from a local time
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = New DateTimeOffset(localTime)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -07:00
' Because the Kind property is DateTimeKind.Local, 
' the offset is that of the local time zone.

' Instantiate a DateTimeOffset value from an unspecified time
targetTime = New DateTimeOffset(sourceDate)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -07:00
' Because the Kind property is DateTimeKind.Unspecified, 
' the offset is that of the local time zone.
```

> [!NOTE]
> 単一の [DateTime](xref:System.DateTime) パラメーターを持つ [DateTimeOffset](xref:System.DateTimeOffset) コンストラクターのオーバーロードを呼び出すことは、[DateTime](xref:System.DateTime) 値の [DateTimeOffset](xref:System.DateTimeOffset) への暗黙の変換を実行することと同じです。

[DateTime](xref:System.DateTime) 値から [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトを作成する 2 つ目のコンストラクターには、変換する [DateTime](xref:System.DateTime) 値と UTC からの日付と時刻のオフセットを表す [TimeSpan](xref:System.TimeSpan) 値の 2 つのパラメーターがあります。 このオフセット値はコンストラクターの最初のパラメーターの [Kind](xref:System.DateTime.Kind) プロパティに対応している必要があり、そうでないと、[System.ArgumentException](xref:System.ArgumentException) がスローされます。 最初のパラメーターの [Kind](xref:System.DateTime.Kind) プロパティが、[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) である場合、2 番目のパラメーターの値は [TimeSpan.Zero](xref:System.TimeSpan.Zero) である必要があります。 最初のパラメーターの [Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Local](xref:System.DateTimeKind.Local) である場合、2 番目のパラメーターの値はローカル システムのタイム ゾーンのオフセットである必要があります。 最初のパラメーターの [Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) である場合は、オフセットに任意の有効な値を指定できます。 次のコードは、[DateTime](xref:System.DateTime) 値を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換するためのこのコンストラクターの呼び出しを示しています。

```csharp
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
DateTimeOffset targetTime;

// Instantiate a DateTimeOffset value from a UTC time with a zero offset.
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = new DateTimeOffset(utcTime, TimeSpan.Zero);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM +00:00
// Because the Kind property is DateTimeKind.Utc,  
// the call to the constructor succeeds

// Instantiate a DateTimeOffset value from a UTC time with a non-zero offset.
try
{
   targetTime = new DateTimeOffset(utcTime, new TimeSpan(-2, 0, 0));
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      utcTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

// Instantiate a DateTimeOffset value from a local time with 
// the offset of the local time zone
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = new DateTimeOffset(localTime, 
                                TimeZoneInfo.Local.GetUtcOffset(localTime));
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -07:00
// Because the Kind property is DateTimeKind.Local and the offset matches
// that of the local time zone, the call to the constructor succeeds.

// Instantiate a DateTimeOffset value from a local time with a zero offset.
try
{
   targetTime = new DateTimeOffset(localTime, TimeSpan.Zero);
   Console.WriteLine(targetTime);
}
catch (ArgumentException)
{
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", 
                      localTime);
}   
// Throws exception and displays the following to the console:
//   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

// Instantiate a DateTimeOffset value with an arbitary time zone. 
string timeZoneName = "Central Standard Time";
TimeSpan offset = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName). 
                         GetUtcOffset(sourceDate); 
targetTime = new DateTimeOffset(sourceDate, offset);
Console.WriteLine(targetTime);
// Displays 5/1/2008 8:30:00 AM -05:00
```

```vb
Dim sourceDate As Date = #5/1/2008 8:30 AM#
Dim targetTime As DateTimeOffset

' Instantiate a DateTimeOffset value from a UTC time with a zero offset.
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = New DateTimeOffset(utcTime, TimeSpan.Zero)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM +00:00
' Because the Kind property is DateTimeKind.Utc,  
' the call to the constructor succeeds.

' Instantiate a DateTimeOffset value from a UTC time with a non-zero offset.
Try
   targetTime = New DateTimeOffset(utcTime, New TimeSpan(-2, 0, 0))
   Console.WriteLine(targetTime)
Catch e As ArgumentException
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", _
                      utcTime)
End Try   
' Throws exception and displays the following to the console:
'   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

' Instantiate a DateTimeOffset value from a local time with 
' the offset of the local time zone.
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = New DateTimeOffset(localTime, _
                                TimeZoneInfo.Local.GetUtcOffset(localTime))
Console.WriteLine(targetTime)
' Because the Kind property is DateTimeKind.Local and the offset matches
' that of the local time zone, the call to the constructor succeeds.

' Instantiate a DateTimeOffset value from a local time with a zero offset.
Try
   targetTime = New DateTimeOffset(localTime, TimeSpan.Zero)
   Console.WriteLine(targetTime)
Catch e As ArgumentException
   Console.WriteLine("Attempt to create DateTimeOffset value from {0} failed.", _
                      localTime)
End Try   
' Throws exception and displays the following to the console:
'   Attempt to create DateTimeOffset value from 5/1/2008 8:30:00 AM failed.

' Instantiate a DateTimeOffset value with an arbitary time zone. 
Dim timeZoneName As String = "Central Standard Time"
Dim offset As TimeSpan = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName). _
                         GetUtcOffset(sourceDate) 
targetTime = New DateTimeOffset(sourceDate, offset)
Console.WriteLine(targetTime)
' Displays 5/1/2008 8:30:00 AM -05:00
```

## <a name="implicit-type-conversion"></a>無効な型変換
 
[System.DateTimeOffset](xref:System.DateTimeOffset) 型は、[System.DateTime](xref:System.DateTime) 値から [DateTimeOffset](xref:System.DateTimeOffset) 値への 1 つの暗黙的な型変換をサポートしています (暗黙的な型変換とは、明示的なキャスト (C# の場合) または変換 (Visual Basic の場合) を必要とせず、情報を失わない 1 つの型から別の型への変換です)。 これにより、次のようなコードが可能となります。

```csharp
DateTimeOffset targetTime;

// The Kind property of sourceDate is DateTimeKind.Unspecified
DateTime sourceDate = new DateTime(2008, 5, 1, 8, 30, 0);
targetTime = sourceDate;
Console.WriteLine(targetTime);   
// Displays 5/1/2008 8:30:00 AM -07:00

// define a UTC time (Kind property is DateTimeKind.Utc)
DateTime utcTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Utc);
targetTime = utcTime;
Console.WriteLine(targetTime);   
// Displays 5/1/2008 8:30:00 AM +00:00

// Define a local time (Kind property is DateTimeKind.Local)
DateTime localTime = DateTime.SpecifyKind(sourceDate, DateTimeKind.Local);
targetTime = localTime;
Console.WriteLine(targetTime);      
// Displays 5/1/2008 8:30:00 AM -07:00
```

```vb
Dim targetTime As DateTimeOffset

' The Kind property of sourceDate is DateTimeKind.Unspecified
Dim sourceDate As Date = #5/1/2008 8:30 AM#
targetTime = sourceDate
Console.WriteLine(targetTime)   
' Displays 5/1/2008 8:30:00 AM -07:00

' define a UTC time (Kind property is DateTimeKind.Utc)
Dim utcTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Utc)
targetTime = utcTime
Console.WriteLine(targetTime)   
' Displays 5/1/2008 8:30:00 AM +00:00

' Define a local time (Kind property is DateTimeKind.Local)
Dim localTime As Date = Date.SpecifyKind(sourceDate, DateTimeKind.Local)
targetTime = localTime
Console.WriteLine(targetTime)      
' Displays 5/1/2008 8:30:00 AM -07:00
```

結果の [DateTimeOffset](xref:System.DateTimeOffset) 値のオフセットは、DateTime.Kind](xref:System.DateTime.Kind) プロパティ値によって異なります。 その値が [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) の場合、オフセットは [TimeSpan.Zero](xref:System.TimeSpan.Zero) に等しい値に設定されます。 その値が [DateTimeKind.Local](xref:System.DateTimeKind.Local) または [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) のいずれかの場合、オフセットはローカル タイム ゾーンのオフセットに等しい値に設定されます。

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>日付と時刻の文字列形式の解析

[System.DateTimeOffset](xref:System.DateTimeOffset) 型は、日付と時刻の文字列形式を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換できる 4 つのメソッドをサポートしています。

* [Parse](xref:System.DateTimeOffset.Parse(System.String)) は、日付と時刻の文字列形式を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換し、変換が失敗した場合、例外をスローします。

* [TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@)) は、日付と時刻の文字列形式を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換し、変換が失敗した場合は、`false` を返します。

* [ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) は、指定した形式の日付と時刻の文字列形式を、[DateTimeOffset](xref:System.DateTimeOffset) 値に変換しようと試みます。 変換が失敗すると、メソッドは例外をスローします。

* [TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) は、指定した形式の日付と時刻の文字列形式を、[DateTimeOffset](xref:System.DateTimeOffset) 値に変換しようと試みます。 変換が失敗すると、メソッドは `false` を返します。

次の例では、[DateTimeOffset](xref:System.DateTimeOffset) 値をインスタンス化するこれらの 4 つの各文字列変換メソッドの呼び出しを示しています。

```csharp
string timeString; 
DateTimeOffset targetTime;

timeString = "05/01/2008 8:30 AM +01:00";
try
{
   targetTime = DateTimeOffset.Parse(timeString);
   Console.WriteLine(targetTime);
}
catch (FormatException)
{
   Console.WriteLine("Unable to parse {0}.", timeString);   
}   

timeString = "05/01/2008 8:30 AM";
if (DateTimeOffset.TryParse(timeString, out targetTime))
   Console.WriteLine(targetTime);
else
   Console.WriteLine("Unable to parse {0}.", timeString);   

timeString = "Thursday, 01 May 2008 08:30";
try
{
   targetTime = DateTimeOffset.ParseExact(timeString, "f", 
                CultureInfo.InvariantCulture);
   Console.WriteLine(targetTime);
}
catch (FormatException)
{
   Console.WriteLine("Unable to parse {0}.", timeString);   
}   

timeString = "Thursday, 01 May 2008 08:30 +02:00";
string formatString; 
formatString = CultureInfo.InvariantCulture.DateTimeFormat.LongDatePattern +
                " " +
                CultureInfo.InvariantCulture.DateTimeFormat.ShortTimePattern +
                " zzz"; 
if (DateTimeOffset.TryParseExact(timeString, 
                                formatString, 
                                CultureInfo.InvariantCulture, 
                                DateTimeStyles.AllowLeadingWhite, 
                                out targetTime))
   Console.WriteLine(targetTime);
else
   Console.WriteLine("Unable to parse {0}.", timeString);
// The example displays the following output to the console:
//    5/1/2008 8:30:00 AM +01:00
//    5/1/2008 8:30:00 AM -07:00
//    5/1/2008 8:30:00 AM -07:00
//    5/1/2008 8:30:00 AM +02:00
```

```vb
Dim timeString As String 
Dim targetTime As DateTimeOffset

timeString = "05/01/2008 8:30 AM +01:00"
Try
   targetTime = DateTimeOffset.Parse(timeString)
   Console.WriteLine(targetTime)
Catch e As FormatException
   Console.WriteLine("Unable to parse {0}.", timeString)   
End Try   

timeString = "05/01/2008 8:30 AM"
If DateTimeOffset.TryParse(timeString, targetTime) Then
   Console.WriteLine(targetTime)
Else
   Console.WriteLine("Unable to parse {0}.", timeString)   
End If

timeString = "Thursday, 01 May 2008 08:30"
Try
   targetTime = DateTimeOffset.ParseExact(timeString, "f", _
                CultureInfo.InvariantCulture)
   Console.WriteLine(targetTime)
Catch e As FormatException
   Console.WriteLine("Unable to parse {0}.", timeString)   
End Try   

timeString = "Thursday, 01 May 2008 08:30 +02:00"
Dim formatString As String 
formatString = CultureInfo.InvariantCulture.DateTimeFormat.LongDatePattern & _
                " " & _
                CultureInfo.InvariantCulture.DateTimeFormat.ShortTimePattern & _
                " zzz" 
If DateTimeOffset.TryParseExact(timeString, _
                                formatString, _
                                CultureInfo.InvariantCulture, _
                                DateTimeStyles.AllowLeadingWhite, _
                                targetTime) Then
   Console.WriteLine(targetTime)
Else
   Console.WriteLine("Unable to parse {0}.", timeString)
End If      
' The example displays the following output to the console:
'    5/1/2008 8:30:00 AM +01:00
'    5/1/2008 8:30:00 AM -07:00
'    5/1/2008 8:30:00 AM -07:00
'    5/1/2008 8:30:00 AM +02:00
```

## <a name="see-also"></a>関連項目

[日付、時刻およびタイム ゾーン](index.md)




<!--HONumber=Nov16_HO1-->


