---
title: "DateTime と DateTimeOffset 間の変換"
description: "DateTime と DateTimeOffset 間の変換"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fab3af5b-5d0f-4384-a40a-1b5d99b30dd1
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 2ba70e9ea39148d040bdb46d5e00ea50dcbb8980
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="converting-between-datetime-and-datetimeoffset"></a><span data-ttu-id="e5256-104">DateTime と DateTimeOffset 間の変換</span><span class="sxs-lookup"><span data-stu-id="e5256-104">Converting between DateTime and DateTimeOffset</span></span>

<span data-ttu-id="e5256-105">[System.DateTimeOffset](xref:System.DateTimeOffset) 構造体は、[System.DateTime](xref:System.DateTime) 構造体よりも高度なタイム ゾーン対応を実現しますが、メソッド呼び出しでは [DateTime](xref:System.DateTime) パラメーターがよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="e5256-105">Although the [System.DateTimeOffset](xref:System.DateTimeOffset) structure provides a greater degree of time zone awareness than the [System.DateTime](xref:System.DateTime) structure, [DateTime](xref:System.DateTime) parameters are used more commonly in method calls.</span></span> <span data-ttu-id="e5256-106">このため、[DateTimeOffset](xref:System.DateTimeOffset) 値を [DateTime](xref:System.DateTime) 値に、またはその逆方向に変換する機能が特に重要です。</span><span class="sxs-lookup"><span data-stu-id="e5256-106">Because of this, the ability to convert [DateTimeOffset](xref:System.DateTimeOffset) values to [DateTime](xref:System.DateTime) values and vice versa is particularly important.</span></span> <span data-ttu-id="e5256-107">この記事では、タイム ゾーン情報をできるだけ多く保持するようにこれらの変換を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e5256-107">This article shows how to perform these conversions in a way that preserves as much time zone information as possible.</span></span>

> [!NOTE]
> <span data-ttu-id="e5256-108">[DateTime](xref:System.DateTime) 型と [DateTimeOffset](xref:System.DateTimeOffset) 型は両方とも、タイム ゾーンの時刻を表す場合に制限があります。</span><span class="sxs-lookup"><span data-stu-id="e5256-108">Both the [DateTime](xref:System.DateTime) and the [DateTimeOffset](xref:System.DateTimeOffset) types have some limitations when representing times in time zones.</span></span> <span data-ttu-id="e5256-109">[DateTime](xref:System.DateTime) は、その [Kind](xref:System.DateTime.Kind) プロパティによって世界協定時刻 (UTC) とシステムのローカル タイム ゾーンのみを反映できます。</span><span class="sxs-lookup"><span data-stu-id="e5256-109">With its [Kind](xref:System.DateTime.Kind) property, [DateTime](xref:System.DateTime) is able to reflect only Coordinated Universal Time (UTC) and the system's local time zone.</span></span> <span data-ttu-id="e5256-110">[DateTimeOffset](xref:System.DateTimeOffset) は、UTC からの時間のオフセットを反映しますが、そのオフセットが所属する実際のタイム ゾーンは反映しません。</span><span class="sxs-lookup"><span data-stu-id="e5256-110">[DateTimeOffset](xref:System.DateTimeOffset) reflects a time's offset from UTC, but it does not reflect the actual time zone to which that offset belongs.</span></span> <span data-ttu-id="e5256-111">時刻の値とタイム ゾーンのサポートの詳細については、「[DateTime DateTimeOffset TimeSpan、および TimeZoneInfo の使い分け](choosing-between-datetime.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5256-111">For details about time values and support for time zones, see [Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md).</span></span>

## <a name="conversions-from-datetime-to-datetimeoffset"></a><span data-ttu-id="e5256-112">DateTime から DateTimeOffset への変換</span><span class="sxs-lookup"><span data-stu-id="e5256-112">Conversions from DateTime to DateTimeOffset</span></span>

<span data-ttu-id="e5256-113">[DateTimeOffset](xref:System.DateTimeOffset) 構造体は、ほとんどの変換に適した、[DateTime](xref:System.DateTime) から [DateTimeOffset](xref:System.DateTimeOffset) への変換を実行する次の&2; つの相当する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="e5256-113">The [DateTimeOffset](xref:System.DateTimeOffset) structure provides two equivalent ways to perform [DateTime](xref:System.DateTime) to [DateTimeOffset](xref:System.DateTimeOffset) conversion that are suitable for most conversions:</span></span>

* <span data-ttu-id="e5256-114">[DateTimeOffset(DateTime)](xref:System.DateTimeOffset) コンストラクター。[DateTime](xref:System.DateTime) 値に基づいて新しい [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5256-114">The [DateTimeOffset(DateTime)](xref:System.DateTimeOffset) constructor, which creates a new [DateTimeOffset](xref:System.DateTimeOffset) object based on a [DateTime](xref:System.DateTime) value.</span></span>

* <span data-ttu-id="e5256-115">暗黙的な変換演算子。[DateTime](xref:System.DateTime) 値を [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトに割り当て可能にします。</span><span class="sxs-lookup"><span data-stu-id="e5256-115">The implicit conversion operator, which allows you to assign a [DateTime](xref:System.DateTime) value to a [DateTimeOffset](xref:System.DateTimeOffset) object.</span></span>

<span data-ttu-id="e5256-116">UTC と現地の [DateTime](xref:System.DateTime) 値について、変換後の [DateTimeOffset](xref:System.DateTimeOffset) 値の [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) プロパティは、UTC またはローカル タイム ゾーン オフセットを正確に反映します。</span><span class="sxs-lookup"><span data-stu-id="e5256-116">For UTC and local [DateTime](xref:System.DateTime) values, the [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) property of the resulting [DateTimeOffset](xref:System.DateTimeOffset) value accurately reflects the UTC or local time zone offset.</span></span> <span data-ttu-id="e5256-117">たとえば、次のコードは、UTC 時刻を同等の [DateTimeOffset](xref:System.DateTimeOffset) 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="e5256-117">For example, the following code converts a UTC time to its equivalent [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> 

```csharp
DateTime utcTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
utcTime1 = DateTime.SpecifyKind(utcTime1, DateTimeKind.Utc);
DateTimeOffset utcTime2 = utcTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  utcTime1, 
                  utcTime1.Kind.ToString(), 
                  utcTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM +00:00
```

```vb
Dim utcTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, _
                                        DateTimeKind.Utc)
Dim utcTime2 As DateTimeOffset = utcTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  utcTime1, _
                  utcTime1.Kind.ToString(), _
                  utcTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Utc to a DateTimeOffset value of 6/19/2008 7:00:00 AM  +00:00
```

<span data-ttu-id="e5256-118">この場合、`utcTime2` 変数のオフセットは 00:00 です。</span><span class="sxs-lookup"><span data-stu-id="e5256-118">In this case, the offset of the `utcTime2` variable is 00:00.</span></span> <span data-ttu-id="e5256-119">同様に、次のコードは、現地時刻を同等の [DateTimeOffset](xref:System.DateTimeOffset) 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="e5256-119">Similarly, the following code converts a local time to its equivalent [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

```csharp
DateTime localTime1 = new DateTime(2008, 6, 19, 7, 0, 0);
localTime1 = DateTime.SpecifyKind(localTime1, DateTimeKind.Local);
DateTimeOffset localTime2 = localTime1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  localTime1, 
                  localTime1.Kind.ToString(), 
                  localTime2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim localTime1 As Date = Date.SpecifyKind(#06/19/2008 7:00AM#, DateTimeKind.Local)
Dim localTime2 As DateTimeOffset = localTime1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  localTime1, _
                  localTime1.Kind.ToString(), _
                  localTime2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Local to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

<span data-ttu-id="e5256-120">ただし、[Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) である [DateTime](xref:System.DateTime) 値については、これらの&2; つの変換メソッドは、オフセットがローカル タイム ゾーンのオフセットである [DateTimeOffset](xref:System.DateTimeOffset) 値を生成します。</span><span class="sxs-lookup"><span data-stu-id="e5256-120">However, for [DateTime](xref:System.DateTime) values whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), these two conversion methods produce a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset is that of the local time zone.</span></span> <span data-ttu-id="e5256-121">米国の太平洋標準時ゾーンでの実行例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e5256-121">This is shown in the following example, which is run in the U.S. Pacific Standard Time zone.</span></span>

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);  // Kind is DateTimeKind.Unspecified
DateTimeOffset time2 = time1;
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", 
                  time1, 
                  time1.Kind.ToString(), 
                  time2);
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Dim time2 As DateTimeOffset = time1
Console.WriteLine("Converted {0} {1} to a DateTimeOffset value of {2}", _
                  time1, _
                  time1.Kind.ToString(), _
                  time2)
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTimeOffset value of 6/19/2008 7:00:00 AM -07:00
```

<span data-ttu-id="e5256-122">[DateTime](xref:System.DateTime) 値がローカル タイム ゾーンまたは UTC 以外の何らかの日時を反映している場合は、オーバーロードされた [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset) コンストラクターを呼び出して、この値を [DateTimeOffset](xref:System.DateTimeOffset) 値に変換し、そのタイム ゾーン情報を保持することができます。</span><span class="sxs-lookup"><span data-stu-id="e5256-122">If the [DateTime](xref:System.DateTime) value reflects the date and time in something other than the local time zone or UTC, you can convert it to a [DateTimeOffset](xref:System.DateTimeOffset) value and preserve its time zone information by calling the overloaded [DateTimeOffset(DateTime, TimeSpan)](xref:System.DateTimeOffset) constructor.</span></span> <span data-ttu-id="e5256-123">たとえば、次の例では、中部標準時を反映する [DateTimeOffset](xref:System.DateTimeOffset) オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="e5256-123">For example, the following example instantiates a [DateTimeOffset](xref:System.DateTimeOffset) object that reflects Central Standard Time.</span></span>

```csharp
DateTime time1 = new DateTime(2008, 6, 19, 7, 0, 0);     // Kind is DateTimeKind.Unspecified
try
{
   DateTimeOffset time2 = new DateTimeOffset(time1, 
                  TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)); 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", 
                     time1, 
                     time1.Kind.ToString(), 
                     time2);
}
// Handle exception if time zone is not defined in registry
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to identify target time zone for conversion.");
}
// This example displays the following output to the console:
//    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

```vb
Dim time1 As Date = #06/19/2008 7:00AM#      ' Kind is DateTimeKind.Unspecified
Try
   Dim time2 As New DateTimeOffset(time1, _
                    TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(time1)) 
   Console.WriteLine("Converted {0} {1} to a DateTime value of {2}", _
                     time1, _
                     time1.Kind.ToString(), _
                     time2)
' Handle exception if time zone is not defined in registry
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to identify target time zone for conversion.")
End Try
' This example displays the following output to the console:
'    Converted 6/19/2008 7:00:00 AM Unspecified to a DateTime value of 6/19/2008 7:00:00 AM -05:00
```

<span data-ttu-id="e5256-124">このコンストラクター オーバーロードの&2; 番目のパラメーターは、UTC からの時刻のオフセットを表す [System.TimeSpan](xref:System.TimeSpan) オブジェクトです。このオブジェクトは、時刻の対応するタイム ゾーンの [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) メソッドを呼び出して取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5256-124">The second parameter to this constructor overload, a [System.TimeSpan](xref:System.TimeSpan) object that represents the time's offset from UTC, should be retrieved by calling the [TimeZoneInfo.GetUtcOffset(DateTime)](xref:System.TimeZoneInfo) method of the time's corresponding time zone.</span></span> <span data-ttu-id="e5256-125">このメソッドの単一のパラメーターは、変換する日時を表す [DateTime](xref:System.DateTime) 値です。</span><span class="sxs-lookup"><span data-stu-id="e5256-125">The method's single parameter is the [DateTime](xref:System.DateTime) value that represents the date and time to be converted.</span></span> <span data-ttu-id="e5256-126">タイム ゾーンで夏時間がサポートされている場合、このパラメーターにより、このメソッドはその特定の日時に対して適切なオフセットを決定できます。</span><span class="sxs-lookup"><span data-stu-id="e5256-126">If the time zone supports daylight saving time, this parameter allows the method to determine the appropriate offset for that particular date and time.</span></span>

## <a name="conversions-from-datetimeoffset-to-datetime"></a><span data-ttu-id="e5256-127">DateTimeOffset から DateTime への変換</span><span class="sxs-lookup"><span data-stu-id="e5256-127">Conversions from DateTimeOffset to DateTime</span></span>

<span data-ttu-id="e5256-128">[DateTimeOffset](xref:System.DateTimeOffset) から [DateTime](xref:System.DateTime) への変換の実行には、[DateTime](xref:System.DateTime) プロパティが最もよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="e5256-128">The [DateTime](xref:System.DateTime) property is most commonly used to perform [DateTimeOffset](xref:System.DateTimeOffset) to [DateTime](xref:System.DateTime) conversion.</span></span> <span data-ttu-id="e5256-129">ただし、次の例に示すように、このプロパティは、[Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) である [DateTime](xref:System.DateTime) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="e5256-129">However, it returns a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), as the following example illustrates.</span></span> 

```csharp
DateTime baseTime = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset sourceTime;
DateTime targetTime;

// Convert UTC to DateTime value
sourceTime = new DateTimeOffset(baseTime, TimeSpan.Zero);
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert local time to DateTime value
sourceTime = new DateTimeOffset(baseTime, 
                                TimeZoneInfo.Local.GetUtcOffset(baseTime));
targetTime = sourceTime.DateTime;
Console.WriteLine("{0} converts to {1} {2}", 
                  sourceTime, 
                  targetTime, 
                  targetTime.Kind.ToString());

// Convert Central Standard Time to a DateTime value
try
{
   TimeSpan offset = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime);
   sourceTime = new DateTimeOffset(baseTime, offset);
   targetTime = sourceTime.DateTime;
   Console.WriteLine("{0} converts to {1} {2}", 
                     sourceTime, 
                     targetTime, 
                     targetTime.Kind.ToString());
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.");
} 
// This example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
//    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

```vb
Const baseTime As Date = #06/19/2008 7:00AM#
Dim sourceTime As DateTimeOffset
Dim targetTime As Date

' Convert UTC to DateTime value
sourceTime = New DateTimeOffset(baseTime, TimeSpan.Zero)
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert local time to DateTime value
sourceTime = New DateTimeOffset(baseTime, _
                                TimeZoneInfo.Local.GetUtcOffset(baseTime))
targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())

' Convert Central Standard Time to a DateTime value
Try
   Dim offset As TimeSpan = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(baseTime)
   sourceTime = New DateTimeOffset(baseTime, offset)
   targetTime = sourceTime.DateTime
Console.WriteLine("{0} converts to {1} {2}", _
                  sourceTime, _
                  targetTime, _
                  targetTime.Kind.ToString())
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to create DateTimeOffset based on U.S. Central Standard Time.")
End Try 
' This example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -07:00 converts to 6/19/2008 7:00:00 AM Unspecified
'    6/19/2008 7:00:00 AM -05:00 converts to 6/19/2008 7:00:00 AM Unspecified 
```

<span data-ttu-id="e5256-130">つまり、[DateTime](xref:System.DateTime) プロパティを使用すると、変換によって [DateTimeOffset](xref:System.DateTimeOffset) 値と UTC との関係に関するすべての情報が失われます。</span><span class="sxs-lookup"><span data-stu-id="e5256-130">This means that any information about the [DateTimeOffset](xref:System.DateTimeOffset) value's relationship to UTC is lost by the conversion when the [DateTime](xref:System.DateTime) property is used.</span></span> <span data-ttu-id="e5256-131">このことは、UTC 時刻またはシステムの現地時刻に対応する [DateTimeOffset](xref:System.DateTimeOffset) 値に影響を与えます。これは、[DateTime](xref:System.DateTime) 構造体が、その [Kind](xref:System.DateTime.Kind) プロパティでこれらの&2; つのタイム ゾーンのみを反映するためです。</span><span class="sxs-lookup"><span data-stu-id="e5256-131">This affects [DateTimeOffset](xref:System.DateTimeOffset) values that correspond to UTC time or to the system's local time because the [DateTime](xref:System.DateTime) structure reflects only those two time zones in its [Kind](xref:System.DateTime.Kind) property.</span></span>

<span data-ttu-id="e5256-132">[DateTimeOffset](xref:System.DateTimeOffset) を [DateTime](xref:System.DateTime) 値に変換するときにできるだけ多くのタイム ゾーン情報を保持するには、[DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) プロパティと [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5256-132">To preserve as much time zone information as possible when converting a [DateTimeOffset](xref:System.DateTimeOffset) to a [DateTime](xref:System.DateTime) value, you can use the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) and [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) properties.</span></span> 

## <a name="converting-a-utc-time"></a><span data-ttu-id="e5256-133">UTC 時刻の変換</span><span class="sxs-lookup"><span data-stu-id="e5256-133">Converting a UTC Time</span></span>

<span data-ttu-id="e5256-134">変換された [DateTime](xref:System.DateTime) 値が UTC 時刻であることを示すには、[DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) プロパティの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e5256-134">To indicate that a converted [DateTime](xref:System.DateTime) value is the UTC time, you can retrieve the value of the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property.</span></span> <span data-ttu-id="e5256-135">このプロパティは、[DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) プロパティと次の&2; つの点で異なります。</span><span class="sxs-lookup"><span data-stu-id="e5256-135">It differs from the [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) property in two ways:</span></span>

* <span data-ttu-id="e5256-136">[Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) である [DateTime](xref:System.DateTime) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="e5256-136">It returns a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

* <span data-ttu-id="e5256-137">[DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) プロパティ値が [TimeSpan.Zero](xref:System.TimeSpan.Zero) と等しくない場合、時刻を UTC に変換します。</span><span class="sxs-lookup"><span data-stu-id="e5256-137">If the [DateTimeOffset.Offset](xref:System.DateTimeOffset.Offset) property value does not equal [TimeSpan.Zero](xref:System.TimeSpan.Zero), it converts the time to UTC.</span></span>

> [!NOTE]
> <span data-ttu-id="e5256-138">アプリケーションで、[DateTime](xref:System.DateTime) 値によってある時点を明確に識別する必要がある場合、[DateTimeOffset](xref:System.DateTimeOffset) から [DateTime](xref:System.DateTime) へのすべての変換を処理するために、[DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) プロパティの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="e5256-138">If your application requires that converted [DateTime](xref:System.DateTime) values unambiguously identify a single point in time, you should consider using the [DateTimeOffset.UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property to handle all [DateTimeOffset](xref:System.DateTimeOffset) to [DateTime](xref:System.DateTime) conversions.</span></span>

<span data-ttu-id="e5256-139">次のコードは、[UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) プロパティを使用して、オフセットが [TimeSpan.Zero](xref:System.TimeSpan.Zero) と等しい [DateTimeOffset](xref:System.DateTimeOffset) 値を [DateTime](xref:System.DateTime) 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="e5256-139">The following code uses the [UtcDateTime](xref:System.DateTimeOffset.UtcDateTime) property to convert a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset equals [TimeSpan.Zero](xref:System.TimeSpan.Zero) to a [DateTime](xref:System.DateTime) value.</span></span>

```csharp
DateTimeOffset utcTime1 = new DateTimeOffset(2008, 6, 19, 7, 0, 0, TimeSpan.Zero);
DateTime utcTime2 = utcTime1.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

```vb
Dim utcTime1 As New DateTimeOffset(#06/19/2008 7:00AM#, TimeSpan.Zero)
Dim utcTime2 As Date = utcTime1.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
```

<span data-ttu-id="e5256-140">次のコードは、UtcDateTime プロパティを使用して、[DateTimeOffset](xref:System.DateTimeOffset) 値に対してタイム ゾーン変換と型変換の両方を実行します。</span><span class="sxs-lookup"><span data-stu-id="e5256-140">The following code uses the UtcDateTime property to perform both a time zone conversion and a type conversion on a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span>

```csharp
DateTimeOffset originalTime = new DateTimeOffset(2008, 6, 19, 7, 0, 0, new TimeSpan(5, 0, 0));
DateTime utcTime = originalTime.UtcDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalTime, 
                  utcTime, 
                  utcTime.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

```vb
Dim originalTime As New DateTimeOffset(#6/19/2008 7:00AM#, _
                                       New TimeSpan(5, 0, 0))
Dim utcTime As Date = originalTime.UtcDateTime
Console.WriteLine("{0} converted to {1} {2}", _ 
                  originalTime, _
                  utcTime, _
                  utcTime.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM +05:00 converted to 6/19/2008 2:00:00 AM Utc
```

## <a name="converting-a-local-time"></a><span data-ttu-id="e5256-141">現地時刻の変換</span><span class="sxs-lookup"><span data-stu-id="e5256-141">Converting a Local Time</span></span>

<span data-ttu-id="e5256-142">[DateTimeOffset](xref:System.DateTimeOffset) 値が現地時刻を表すことを示すには、[DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) プロパティによって返される [DateTime](xref:System.DateTime) 値を静的な [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e5256-142">To indicate that a [DateTimeOffset](xref:System.DateTimeOffset) value represents the local time, you can pass the [DateTime](xref:System.DateTime) value returned by the [DateTimeOffset.DateTime](xref:System.DateTimeOffset.DateTime) property to the static [DateTime.SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method.</span></span> <span data-ttu-id="e5256-143">このメソッドは、その最初のパラメーターとして渡された日時を返しますが、[Kind](xref:System.DateTime.Kind) プロパティを、その&2; 番目のパラメーターによって指定された値に設定します。</span><span class="sxs-lookup"><span data-stu-id="e5256-143">The method returns the date and time passed to it as its first parameter, but sets the [Kind](xref:System.DateTime.Kind) property to the value specified by its second parameter.</span></span> <span data-ttu-id="e5256-144">次のコードは、オフセットがローカル タイム ゾーンのオフセットに対応する [DateTimeOffset](xref:System.DateTimeOffset) 値を変換する際に、[SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5256-144">The following code uses the [SpecifyKind(DateTime, DateTimeKind)](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method when converting a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset corresponds to that of the local time zone.</span></span>

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset utcTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime utcTime2 = utcTime1.DateTime;
if (utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime))) 
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local);

Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime1, 
                  utcTime2, 
                  utcTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim utcTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim utcTime2 As Date = utcTime1.DateTime
If utcTime1.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(utcTime1.DateTime)) Then
   utcTime2 = DateTime.SpecifyKind(utcTime2, DateTimeKind.Local)
End If   
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime1, _
                  utcTime2, _
                  utcTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

<span data-ttu-id="e5256-145">[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用して、[DateTimeOffset](xref:System.DateTimeOffset) 値をローカルの [DateTime](xref:System.DateTime) 値に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="e5256-145">You can also use the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to convert a [DateTimeOffset](xref:System.DateTimeOffset) value to a local [DateTime](xref:System.DateTime) value.</span></span> <span data-ttu-id="e5256-146">返される [DateTime](xref:System.DateTime) 値の [Kind](xref:System.DateTime.Kind) プロパティは、[DateTimeKind.Local](xref:System.DateTimeKind.Local) です。</span><span class="sxs-lookup"><span data-stu-id="e5256-146">The [Kind](xref:System.DateTime.Kind) property of the returned [DateTime](xref:System.DateTime) value is [DateTimeKind.Local](xref:System.DateTimeKind.Local).</span></span> <span data-ttu-id="e5256-147">次のコードは、オフセットがローカル タイム ゾーンのオフセットに対応する [DateTimeOffset](xref:System.DateTimeOffset) 値を変換する際に、[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5256-147">The following code uses the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property when converting a [DateTimeOffset](xref:System.DateTimeOffset) value whose offset corresponds to that of the local time zone.</span></span>

```csharp
DateTime sourceDate = new DateTime(2008, 6, 19, 7, 0, 0);
DateTimeOffset localTime1 = new DateTimeOffset(sourceDate, 
                          TimeZoneInfo.Local.GetUtcOffset(sourceDate));
DateTime localTime2 = localTime1.LocalDateTime;

Console.WriteLine("{0} converted to {1} {2}", 
                  localTime1, 
                  localTime2, 
                  localTime2.Kind.ToString());
// The example displays the following output to the console:
//   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
```

```vb
Dim sourceDate As Date = #06/19/2008 7:00AM#
Dim localTime1 As New DateTimeOffset(sourceDate, _
                                   TimeZoneInfo.Local.GetUtcOffset(sourceDate))
Dim localTime2 As Date = localTime1.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime1, _
                  localTime2, _
                  localTime2.Kind.ToString())
' The example displays the following output to the console:
'   6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local 
```

<span data-ttu-id="e5256-148">[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用して [DateTime](xref:System.DateTime) 値を取得する場合、このプロパティの `get` アクセサーは、最初に [DateTimeOffset](xref:System.DateTimeOffset) 値を UTC に変換してから、[DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset) メソッドを呼び出して現地時刻に変換します。</span><span class="sxs-lookup"><span data-stu-id="e5256-148">When you retrieve a [DateTime](xref:System.DateTime) value using the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property, the property's `get` accessor first converts the [DateTimeOffset](xref:System.DateTimeOffset) value to UTC, then converts it to local time by calling the [DateTimeOffset.ToLocalTime](xref:System.DateTimeOffset) method.</span></span> <span data-ttu-id="e5256-149">つまり、[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティから値を取得して、型変換を実行するのと同時にタイム ゾーン変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e5256-149">This means that you can retrieve a value from the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to perform a time zone conversion at the same time that you perform a type conversion.</span></span> <span data-ttu-id="e5256-150">また、変換の実行にローカル タイム ゾーンの調整規則が適用されることも意味します。</span><span class="sxs-lookup"><span data-stu-id="e5256-150">It also means that the local time zone's adjustment rules are applied in performing the conversion.</span></span> <span data-ttu-id="e5256-151">次のコードは、[DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) プロパティを使用して型変換とタイム ゾーン変換の両方を実行する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="e5256-151">The following code illustrates the use of the [DateTimeOffset.LocalDateTime](xref:System.DateTimeOffset.LocalDateTime) property to perform both a type and a time zone conversion.</span></span>

```csharp
DateTimeOffset originalDate;
DateTime localDate;

// Convert time originating in a different time zone
originalDate = new DateTimeOffset(2008, 6, 18, 7, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// Convert time originating in a different time zone 
// so local time zone's adjustment rules are applied
originalDate = new DateTimeOffset(2007, 11, 4, 4, 0, 0, 
                                  new TimeSpan(-5, 0, 0));
localDate = originalDate.LocalDateTime;
Console.WriteLine("{0} converted to {1} {2}", 
                  originalDate, 
                  localDate, 
                  localDate.Kind.ToString());
// The example displays the following output to the console:
//       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
//       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

```vb
Dim originalDate As DateTimeOffset
Dim localDate As Date

' Convert time originating in a different time zone
originalDate = New DateTimeOffset(#06/19/2008 7:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' Convert time originating in a different time zone 
' so local time zone's adjustment rules are applied
originalDate = New DateTimeOffset(#11/04/2007 4:00AM#, _
                                  New TimeSpan(-5, 0, 0))
localDate = originalDate.LocalDateTime
Console.WriteLine("{0} converted to {1} {2}", _
                  originalDate, _
                  localDate, _
                  localDate.Kind.ToString())
' The example displays the following output to the console:
'       6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 5:00:00 AM Local
'       11/4/2007 4:00:00 AM -05:00 converted to 11/4/2007 1:00:00 AM Local
```

## <a name="a-general-purpose-conversion-method"></a><span data-ttu-id="e5256-152">汎用変換メソッド</span><span class="sxs-lookup"><span data-stu-id="e5256-152">A General-Purpose Conversion Method</span></span>

<span data-ttu-id="e5256-153">次の例では、[DateTimeOffset](xref:System.DateTimeOffset) 値を [DateTime](xref:System.DateTime) 値に変換する `ConvertFromDateTimeOffset` という名前のメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="e5256-153">The following example defines a method named `ConvertFromDateTimeOffset` that converts [DateTimeOffset](xref:System.DateTimeOffset) values to [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="e5256-154">オフセットに基づき、[DateTimeOffset](xref:System.DateTimeOffset) 値が UTC 時刻、現地時刻、またはその他の時刻であるかどうかを判断し、その結果に応じて、返される日時値の [Kind](xref:System.DateTime.Kind) プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="e5256-154">Based on its offset, it determines whether the [DateTimeOffset](xref:System.DateTimeOffset) value is a UTC time, a local time, or some other time, and defines the returned date and time value's [Kind](xref:System.DateTime.Kind) property accordingly.</span></span> 

```csharp
static DateTime ConvertFromDateTimeOffset(DateTimeOffset dateTime)
{
   if (dateTime.Offset.Equals(TimeSpan.Zero))
      return dateTime.UtcDateTime;
   else if (dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime)))
      return DateTime.SpecifyKind(dateTime.DateTime, DateTimeKind.Local);
   else
      return dateTime.DateTime;   
}
```

```vb
Function ConvertFromDateTimeOffset(dateTime As DateTimeOffset) As Date
   If dateTime.Offset.Equals(TimeSpan.Zero) Then
      Return dateTime.UtcDateTime
   ElseIf dateTime.Offset.Equals(TimeZoneInfo.Local.GetUtcOffset(dateTime.DateTime))
      Return Date.SpecifyKind(dateTime.DateTime, DateTimeKind.Local)
   Else
      Return dateTime.DateTime   
   End If
```

<span data-ttu-id="e5256-155">次の例では、`ConvertFromDateTimeOffset` メソッドを呼び出して、UTC 時刻、現地時刻、および米国の中部標準時ゾーンの時刻を表す [DateTimeOffset](xref:System.DateTimeOffset) 値を変換します。</span><span class="sxs-lookup"><span data-stu-id="e5256-155">The follow example calls the `ConvertFromDateTimeOffset` method to convert [DateTimeOffset](xref:System.DateTimeOffset) values that represent a UTC time, a local time, and a time in the U.S. Central Standard Time zone.</span></span>

```csharp
DateTime timeComponent = new DateTime(2008, 6, 19, 7, 0, 0);
DateTime returnedDate; 

// Convert UTC time
DateTimeOffset utcTime = new DateTimeOffset(timeComponent, TimeSpan.Zero);
returnedDate = ConvertFromDateTimeOffset(utcTime); 
Console.WriteLine("{0} converted to {1} {2}", 
                  utcTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert local time
DateTimeOffset localTime = new DateTimeOffset(timeComponent, 
                           TimeZoneInfo.Local.GetUtcOffset(timeComponent)); 
returnedDate = ConvertFromDateTimeOffset(localTime);                                          
Console.WriteLine("{0} converted to {1} {2}", 
                  localTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());

// Convert Central Standard Time
DateTimeOffset cstTime = new DateTimeOffset(timeComponent, 
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent));
returnedDate = ConvertFromDateTimeOffset(cstTime);
Console.WriteLine("{0} converted to {1} {2}", 
                  cstTime, 
                  returnedDate, 
                  returnedDate.Kind.ToString());
// The example displays the following output to the console:
//    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
//    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
//    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

```vb
Dim timeComponent As Date = #06/19/2008 7:00AM#
Dim returnedDate As Date 

' Convert UTC time
Dim utcTime As New DateTimeOffset(timeComponent, TimeSpan.Zero)
returnedDate = ConvertFromDateTimeOffset(utcTime) 
Console.WriteLine("{0} converted to {1} {2}", _
                  utcTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert local time
Dim localTime As New DateTimeOffset(timeComponent, _
                                    TimeZoneInfo.Local.GetUtcOffset(timeComponent)) 
returnedDate = ConvertFromDateTimeOffset(localTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  localTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())

' Convert Central Standard Time
Dim cstTime As New DateTimeOffset(timeComponent, _
               TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time").GetUtcOffset(timeComponent))
returnedDate = ConvertFromDateTimeOffset(cstTime)                                                                  
Console.WriteLine("{0} converted to {1} {2}", _
                  cstTime, _
                  returnedDate, _
                  returnedDate.Kind.ToString())
' The example displays the following output to the console:
'    6/19/2008 7:00:00 AM +00:00 converted to 6/19/2008 7:00:00 AM Utc
'    6/19/2008 7:00:00 AM -07:00 converted to 6/19/2008 7:00:00 AM Local
'    6/19/2008 7:00:00 AM -05:00 converted to 6/19/2008 7:00:00 AM Unspecified
```

<span data-ttu-id="e5256-156">このコードは次の&2; つのことを前提としますが、アプリケーションおよびその日時値のソースによっては常に有効とは限らないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e5256-156">Note that this code makes two assumptions that, depending on the application and the source of its date and time values, may not always be valid:</span></span>

* <span data-ttu-id="e5256-157">オフセットが [TimeSpan.Zero](xref:System.TimeSpan.Zero) である日時値が UTC を表すことを前提とします。</span><span class="sxs-lookup"><span data-stu-id="e5256-157">It assumes that a date and time value whose offset is [TimeSpan.Zero](xref:System.TimeSpan.Zero) represents UTC.</span></span> <span data-ttu-id="e5256-158">実際には、UTC は特定のタイム ゾーンの時刻ではなく、世界のタイム ゾーンの時刻を標準化する際に基準となる時刻です。</span><span class="sxs-lookup"><span data-stu-id="e5256-158">In fact, UTC is not a time in a particular time zone, but the time in relation to which the times in the world's time zones are standardized.</span></span> <span data-ttu-id="e5256-159">タイム ゾーンのオフセットが [Zero](xref:System.TimeSpan.Zero) である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e5256-159">Time zones can also have an offset of [Zero](xref:System.TimeSpan.Zero).</span></span>

* <span data-ttu-id="e5256-160">オフセットがローカル タイム ゾーンのオフセットと等しい日時が、ローカル タイム ゾーンを表すことを前提とします。</span><span class="sxs-lookup"><span data-stu-id="e5256-160">It assumes that a date and time whose offset equals that of the local time zone represents the local time zone.</span></span> <span data-ttu-id="e5256-161">日時値は元のタイム ゾーンとの関連付けが解除されているので、これは該当しない場合があります。日時は、同じオフセットを持つ別のタイム ゾーンに由来する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5256-161">Because date and time values are disassociated from their original time zone, this may not be the case; the date and time can have originated in another time zone with the same offset.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5256-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5256-162">See Also</span></span>

[<span data-ttu-id="e5256-163">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="e5256-163">Dates, times, and time zones</span></span>](index.md)





