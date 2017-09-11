---
title: "DateTimeOffset オブジェクトのインスタンス化"
description: "DateTimeOffset オブジェクトのインスタンス化"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 476fe67b-6be4-4435-88ab-ced37304f1d1
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 26be324eb5d58b94a71e89aba213f107cf8dfd1e
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="instantiating-a-datetimeoffset-object"></a><span data-ttu-id="34175-104">DateTimeOffset オブジェクトのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="34175-104">Instantiating a DateTimeOffset object</span></span>

<span data-ttu-id="34175-105">[System.DateTimeOffset](xref:System.DateTimeOffset) 構造体は、新しい [DateTimeOffset](xref:System.DateTimeOffset) 値を作成するためのさまざまな方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="34175-105">The [System.DateTimeOffset](xref:System.DateTimeOffset) structure offers a number of ways to create new [DateTimeOffset](xref:System.DateTimeOffset) values.</span></span> <span data-ttu-id="34175-106">それらの多くは新しい [System.DateTime](xref:System.DateTime) 値をインスタンス化するために使用できるメソッドに直接対応し、世界協定時刻 (UTC) からの日時値のオフセットを指定できる拡張が加えられています。</span><span class="sxs-lookup"><span data-stu-id="34175-106">Many of them correspond directly to the methods available for instantiating new [System.DateTime](xref:System.DateTime) values, with enhancements that allow you to specify the date and time value's offset from Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="34175-107">特に、次の方法で、[DateTimeOffset](xref:System.DateTimeOffset) 値をインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="34175-107">In particular, you can instantiate a [DateTimeOffset](xref:System.DateTimeOffset) value in the following ways:</span></span>

* <span data-ttu-id="34175-108">[DateTimeOffset](xref:System.DateTimeOffset) コンストラクターを呼び出す。</span><span class="sxs-lookup"><span data-stu-id="34175-108">By calling a [DateTimeOffset](xref:System.DateTimeOffset) constructor.</span></span>

* <span data-ttu-id="34175-109">値を [DateTimeOffset](xref:System.DateTimeOffset) 値に暗黙的に変換する。</span><span class="sxs-lookup"><span data-stu-id="34175-109">By implicitly converting a value to [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

* <span data-ttu-id="34175-110">日付と時刻の文字列形式を解析する。</span><span class="sxs-lookup"><span data-stu-id="34175-110">By parsing the string representation of a date and time.</span></span>

## <a name="date-and-time-literals"></a><span data-ttu-id="34175-111">日付と時刻のリテラル</span><span class="sxs-lookup"><span data-stu-id="34175-111">Date and Time Literals</span></span>

<span data-ttu-id="34175-112">これをサポートしている言語では、[DateTime](xref:System.DateTime) 値をインスタンス化する最も一般的な方法の&1; つが、ハード コーディングされたリテラル値として日付と時刻を指定することです。</span><span class="sxs-lookup"><span data-stu-id="34175-112">For languages that support it, one of the most common ways to instantiate a [DateTime](xref:System.DateTime) value is to provide the date and time as a hard-coded literal value.</span></span> <span data-ttu-id="34175-113">たとえば、次の Visual Basic コードでは、値が 2008 年 1 月 1 日午前 10時 00分の [DateTime](xref:System.DateTime) オブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="34175-113">For example, the following Visual Basic code creates a [DateTime](xref:System.DateTime) object whose value is January 1, 2008, at 10:00 AM.</span></span>

```vb
Dim literalDate1 As Date = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate1.ToString())
' Displays:
'              5/1/2008 8:06:32 AM
```

<span data-ttu-id="34175-114">[DateTime](xref:System.DateTime) リテラルをサポートする言語を使用している場合は、日付と時刻のリテラルを使用して、[DateTimeOffset](xref:System.DateTimeOffset) 値を初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="34175-114">[DateTimeOffset](xref:System.DateTimeOffset) values can also be initialized using date and time literals when using languages that support [DateTime](xref:System.DateTime) literals.</span></span> <span data-ttu-id="34175-115">たとえば、次の Visual Basic コードでは、[DateTimeOffset](xref:System.DateTimeOffset) オブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="34175-115">For example, the following Visual Basic code creates a [DateTimeOffset](xref:System.DateTimeOffset) object.</span></span>

```vb
Dim literalDate As DateTimeOffset = #05/01/2008 8:06:32 AM#
Console.WriteLine(literalDate.ToString())
' Displays:
'              5/1/2008 8:06:32 AM -07:00
```

<span data-ttu-id="34175-116">コンソール出力に示すように、このように作成された [DateTimeOffset](xref:System.DateTimeOffset) 値には、ローカル タイム ゾーンのオフセットが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="34175-116">As the console output shows, the [DateTimeOffset](xref:System.DateTimeOffset) value created in this way is assigned the offset of the local time zone.</span></span> <span data-ttu-id="34175-117">つまり、文字リテラルを使用して割り当てられた [DateTimeOffset](xref:System.DateTimeOffset) 値は、別のコンピューターでコードが実行された場合に、単一の特定の時点を識別しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="34175-117">This means that a [DateTimeOffset](xref:System.DateTimeOffset) value assigned using a character literal does not identify a single point of time if the code is run on different computers.</span></span>

## <a name="datetimeoffset-constructors"></a><span data-ttu-id="34175-118">DateTimeOffset コンストラクター</span><span class="sxs-lookup"><span data-stu-id="34175-118">DateTimeOffset Constructors</span></span>

<span data-ttu-id="34175-119">[System.DateTimeOffset](xref:System.DateTimeOffset) 型は、5 つのコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="34175-119">The [System.DateTimeOffset](xref:System.DateTimeOffset) type defines five constructors.</span></span> <span data-ttu-id="34175-120">それらのうちの&3; つは、[DateTime](xref:System.DateTime) コンストラクターに直接対応し、UTC からの日付と時刻のオフセットを定義する [System.TimeSpan](xref:System.TimeSpan) 型のパラメーターが追加されています。</span><span class="sxs-lookup"><span data-stu-id="34175-120">Three of them correspond directly to [DateTime](xref:System.DateTime) constructors, with an additional parameter of type [System.TimeSpan](xref:System.TimeSpan) that defines the date and time's offset from UTC.</span></span> <span data-ttu-id="34175-121">これらにより、個々の日付と時刻のコンポーネントの値に基づいて、[DateTimeOffset](xref:System.DateTimeOffset) 値を定義できます。</span><span class="sxs-lookup"><span data-stu-id="34175-121">These allow you to define a [DateTimeOffset](xref:System.DateTimeOffset) value based on the value of its individual date and time components.</span></span> <span data-ttu-id="34175-122">たとえば、次のコードはこれらの 3 つのコンストラクターを使用して、7/1/2008 12:05 AM +01:00 の同じ値で [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトをインスタンス化しています。</span><span class="sxs-lookup"><span data-stu-id="34175-122">For example, the following code uses these three constructors to instantiate [DateTimeOffset](xref:System.DateTimeOffset) objects with identical values of 7/1/2008 12:05 AM +01:00.</span></span>

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

<span data-ttu-id="34175-123">[PersianCalendar](xref:System.Globalization.PersianCalendar) オブジェクトをそのコンストラクターへの引数の&1; つとして使用して、インスタンス化された [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトの値がコンソールに表示されると、ペルシャ暦ではなく、グレゴリオ暦の日付として表されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="34175-123">Note that, when the value of the [DateTimeOffset](xref:System.DateTimeOffset) object instantiated using a [PersianCalendar](xref:System.Globalization.PersianCalendar) object as one of the arguments to its constructor is displayed to the console, it is expressed as a date in the Gregorian rather than the Persian calendar.</span></span> 

<span data-ttu-id="34175-124">他の&2; つのコンストラクターは、DateTime 値から [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="34175-124">The other two constructors create a [DateTimeOffset](xref:System.DateTimeOffset) object from a DateTime value.</span></span> <span data-ttu-id="34175-125">1 つ目のコンストラクターには、[DateTimeOffset](xref:System.DateTimeOffset) 値に変換される&1; つのパラメーター [DateTime](xref:System.DateTime) 値があります。</span><span class="sxs-lookup"><span data-stu-id="34175-125">The first of these has a single parameter, the [DateTime](xref:System.DateTime) value to convert to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="34175-126">結果の [DateTimeOffset](xref:System.DateTimeOffset) 値のオフセットは、コンストラクターの単一の [DateTime](xref:System.DateTime) パラメーターの [Kind](xref:System.DateTime.Kind) プロパティによって異なります。</span><span class="sxs-lookup"><span data-stu-id="34175-126">The offset of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value depends on the [Kind](xref:System.DateTime.Kind) property of the constructor's single [DateTime](xref:System.DateTime) parameter.</span></span> <span data-ttu-id="34175-127">その値が [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) の場合、オフセットは [TimeSpan.Zero](xref:System.TimeSpan.Zero) に等しい値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="34175-127">If its value is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), the offset is set equal to [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> <span data-ttu-id="34175-128">それ以外の場合、オフセットはローカル タイム ゾーンのオフセットと等しい値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="34175-128">Otherwise, its offset is set equal to that of the local time zone.</span></span> <span data-ttu-id="34175-129">次の例に、このコンストラクターを使用して、UTC とローカル タイム ゾーンを表す [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトをインスタンス化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="34175-129">The following example illustrates the use of this constructor to instantiate [DateTimeOffset](xref:System.DateTimeOffset) objects representing UTC and the local time zone:</span></span>

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
> <span data-ttu-id="34175-130">単一の [DateTime](xref:System.DateTime) パラメーターを持つ [DateTimeOffset](xref:System.DateTimeOffset) コンストラクターのオーバーロードを呼び出すことは、[DateTime](xref:System.DateTime) 値の [DateTimeOffset](xref:System.DateTimeOffset) への暗黙の変換を実行することと同じです。</span><span class="sxs-lookup"><span data-stu-id="34175-130">Calling the overload of the [DateTimeOffset](xref:System.DateTimeOffset) constructor that has a single [DateTime](xref:System.DateTime) parameter is equivalent to performing an implicit conversion of a [DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

<span data-ttu-id="34175-131">[DateTime](xref:System.DateTime) 値から [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトを作成する&2; つ目のコンストラクターには、変換する [DateTime](xref:System.DateTime) 値と UTC からの日付と時刻のオフセットを表す [TimeSpan](xref:System.TimeSpan) 値の&2; つのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="34175-131">The second constructor that creates a [DateTimeOffset](xref:System.DateTimeOffset) object from a [DateTime](xref:System.DateTime) value has two parameters: the [DateTime](xref:System.DateTime) value to convert, and a [TimeSpan](xref:System.TimeSpan) value representing the date and time's offset from UTC.</span></span> <span data-ttu-id="34175-132">このオフセット値はコンストラクターの最初のパラメーターの [Kind](xref:System.DateTime.Kind) プロパティに対応している必要があり、そうでないと、[System.ArgumentException](xref:System.ArgumentException) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="34175-132">This offset value must correspond to the [Kind](xref:System.DateTime.Kind) property of the constructor's first parameter or an [System.ArgumentException](xref:System.ArgumentException) is thrown.</span></span> <span data-ttu-id="34175-133">最初のパラメーターの [Kind](xref:System.DateTime.Kind) プロパティが、[DateTimeKind.Utc](xref:System.DateTimeKind.Utc) である場合、2 番目のパラメーターの値は [TimeSpan.Zero](xref:System.TimeSpan.Zero) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="34175-133">If the [Kind](xref:System.DateTime.Kind) property of the first parameter is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), the value of the second parameter must be [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> <span data-ttu-id="34175-134">最初のパラメーターの [Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Local](xref:System.DateTimeKind.Local) である場合、2 番目のパラメーターの値はローカル システムのタイム ゾーンのオフセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="34175-134">If the [Kind](xref:System.DateTime.Kind) property of the first parameter is [DateTimeKind.Local](xref:System.DateTimeKind.Local), the value of the second parameter must be the offset of the local system's time zone.</span></span> <span data-ttu-id="34175-135">最初のパラメーターの [Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) である場合は、オフセットに任意の有効な値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="34175-135">If the [Kind](xref:System.DateTime.Kind) property of the first parameter is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), the offset can be any valid value.</span></span> <span data-ttu-id="34175-136">次のコードは、[DateTime](xref:System.DateTime) 値を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換するためのこのコンストラクターの呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="34175-136">The following code illustrates calls to this constructor to convert [DateTime](xref:System.DateTime) to [DateTimeOffset](xref:System.DateTimeOffset) values.</span></span>

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

## <a name="implicit-type-conversion"></a><span data-ttu-id="34175-137">無効な型変換</span><span class="sxs-lookup"><span data-stu-id="34175-137">Implicit Type Conversion</span></span>
 
<span data-ttu-id="34175-138">[System.DateTimeOffset](xref:System.DateTimeOffset) 型は、[System.DateTime](xref:System.DateTime) 値から [DateTimeOffset](xref:System.DateTimeOffset) 値への&1; つの暗黙的な型変換をサポートしています</span><span class="sxs-lookup"><span data-stu-id="34175-138">The [System.DateTimeOffset](xref:System.DateTimeOffset) type supports one implicit type conversion: from a [System.DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="34175-139">(暗黙的な型変換とは、明示的なキャスト (C# の場合) または変換 (Visual Basic の場合) を必要とせず、情報を失わない&1; つの型から別の型への変換です)。</span><span class="sxs-lookup"><span data-stu-id="34175-139">(An implicit type conversion is a conversion from one type to another that does not require an explicit cast (in C#) or conversion (in Visual Basic) and that does not lose information.</span></span> <span data-ttu-id="34175-140">これにより、次のようなコードが可能となります。</span><span class="sxs-lookup"><span data-stu-id="34175-140">It makes code like the following possible.</span></span>

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

<span data-ttu-id="34175-141">結果の [DateTimeOffset](xref:System.DateTimeOffset) 値のオフセットは、DateTime.Kind](xref:System.DateTime.Kind) プロパティ値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="34175-141">The offset of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value depends on the DateTime.Kind](xref:System.DateTime.Kind) property value.</span></span> <span data-ttu-id="34175-142">その値が [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) の場合、オフセットは [TimeSpan.Zero](xref:System.TimeSpan.Zero) に等しい値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="34175-142">If its value is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), the offset is set equal to [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> <span data-ttu-id="34175-143">その値が [DateTimeKind.Local](xref:System.DateTimeKind.Local) または [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) のいずれかの場合、オフセットはローカル タイム ゾーンのオフセットに等しい値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="34175-143">If its value is either [DateTimeKind.Local](xref:System.DateTimeKind.Local) or [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), the offset is set equal to that of the local time zone.</span></span>

## <a name="parsing-the-string-representation-of-a-date-and-time"></a><span data-ttu-id="34175-144">日付と時刻の文字列形式の解析</span><span class="sxs-lookup"><span data-stu-id="34175-144">Parsing the String Representation of a Date and Time</span></span>

<span data-ttu-id="34175-145">[System.DateTimeOffset](xref:System.DateTimeOffset) 型は、日付と時刻の文字列形式を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換できる&4; つのメソッドをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="34175-145">The [System.DateTimeOffset](xref:System.DateTimeOffset) type supports four methods that allow you to convert the string representation of a date and time into a [DateTimeOffset](xref:System.DateTimeOffset) value:</span></span>

* <span data-ttu-id="34175-146">[Parse](xref:System.DateTimeOffset.Parse(System.String)) は、日付と時刻の文字列形式を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換し、変換が失敗した場合、例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="34175-146">[Parse](xref:System.DateTimeOffset.Parse(System.String)), which tries to convert the string representation of a date and time to a [DateTimeOffset](xref:System.DateTimeOffset) value and throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="34175-147">[TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@)) は、日付と時刻の文字列形式を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換し、変換が失敗した場合は、`false` を返します。</span><span class="sxs-lookup"><span data-stu-id="34175-147">[TryParse](xref:System.DateTimeOffset.TryParse(System.String,System.DateTimeOffset@)), which tries to convert the string representation of a date and time to a [DateTimeOffset](xref:System.DateTimeOffset) value and returns `false` if the conversion fails.</span></span>

* <span data-ttu-id="34175-148">[ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)) は、指定した形式の日付と時刻の文字列形式を、[DateTimeOffset](xref:System.DateTimeOffset) 値に変換しようと試みます。</span><span class="sxs-lookup"><span data-stu-id="34175-148">[ParseExact](xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)), which tries to convert the string representation of a date and time in a specified format to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="34175-149">変換が失敗すると、メソッドは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="34175-149">The method throws an exception if the conversion fails.</span></span>

* <span data-ttu-id="34175-150">[TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)) は、指定した形式の日付と時刻の文字列形式を、[DateTimeOffset](xref:System.DateTimeOffset) 値に変換しようと試みます。</span><span class="sxs-lookup"><span data-stu-id="34175-150">[TryParseExact](xref:System.DateTimeOffset.TryParseExact(System.String,System.String,System.IFormatProvider,System.Globalization.DateTimeStyles,System.DateTimeOffset@)), which tries to convert the string representation of a date and time in a specified format to a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="34175-151">変換が失敗すると、メソッドは `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="34175-151">The method returns `false` if the conversion fails.</span></span>

<span data-ttu-id="34175-152">次の例では、[DateTimeOffset](xref:System.DateTimeOffset) 値をインスタンス化するこれらの&4; つの各文字列変換メソッドの呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="34175-152">The following example illustrates calls to each of these four string conversion methods to instantiate a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="34175-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="34175-153">See Also</span></span>

[<span data-ttu-id="34175-154">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="34175-154">Dates, times, and time zones</span></span>](index.md)


