---
title: "タイム ゾーン間での時刻の変換"
description: "タイム ゾーン間での時刻の変換"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf8f74e6-e7f2-4c2a-a04c-57db0e28dd36
ms.translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: c2baa48c3b79dfbc5d39652cc57fe015a2313d6e
ms.contentlocale: ja-jp
ms.lasthandoff: 11/16/2016

---

# <a name="converting-times-between-time-zones"></a><span data-ttu-id="b9926-104">タイム ゾーン間での時刻の変換</span><span class="sxs-lookup"><span data-stu-id="b9926-104">Converting times between time zones</span></span>

<span data-ttu-id="b9926-105">日時を使用するすべてのアプリケーションで、タイム ゾーン間の違いを処理することの重要性が高まっています。</span><span class="sxs-lookup"><span data-stu-id="b9926-105">It is becoming increasingly important for any application that works with dates and times to handle differences between time zones.</span></span> <span data-ttu-id="b9926-106">アプリケーションでは、すべての時刻を現地時刻で表現できることを前提とはしていません。現地時刻は、[System.DateTime](xref:System.DateTime) 構造体から取得できる時刻です。</span><span class="sxs-lookup"><span data-stu-id="b9926-106">An application can no longer assume that all times can be expressed in the local time, which is the time available from the [System.DateTime](xref:System.DateTime) structure.</span></span> <span data-ttu-id="b9926-107">たとえば、米国東部の現在の時刻を表示する Web ページには、東アジアの顧客に対する信頼性を欠いています。</span><span class="sxs-lookup"><span data-stu-id="b9926-107">For example, a Web page that displays the current time in the eastern part of the United States will lack credibility to a customer in eastern Asia.</span></span> <span data-ttu-id="b9926-108">このトピックでは、時刻をあるタイム ゾーンから別のタイム ゾーンに変換する方法、およびタイム ゾーン対応に制限のある [System.DateTimeOffset](xref:System.DateTimeOffset) 値を変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b9926-108">This topic explains how to convert times from one time zone to another, as well as how to convert [System.DateTimeOffset](xref:System.DateTimeOffset) values that have limited time zone awareness.</span></span>

## <a name="converting-to-coordinated-universal-time"></a><span data-ttu-id="b9926-109">世界協定時刻への変換</span><span class="sxs-lookup"><span data-stu-id="b9926-109">Converting to Coordinated Universal Time</span></span>

<span data-ttu-id="b9926-110">世界協定時刻 (UTC) は、高精度の原子時標準です。</span><span class="sxs-lookup"><span data-stu-id="b9926-110">Coordinated Universal Time (UTC) is a high-precision, atomic time standard.</span></span> <span data-ttu-id="b9926-111">世界のタイム ゾーンは、UTC からの正または負のオフセットとして表現されます。</span><span class="sxs-lookup"><span data-stu-id="b9926-111">The world’s time zones are expressed as positive or negative offsets from UTC.</span></span> <span data-ttu-id="b9926-112">したがって、UTC はタイム ゾーンの影響を受けない、またはタイム ゾーンに依存しない種類の時刻を提供します。</span><span class="sxs-lookup"><span data-stu-id="b9926-112">Thus, UTC provides a kind of time-zone free or time-zone neutral time.</span></span> <span data-ttu-id="b9926-113">コンピューター間の日時の移植性が重要となる場合には、UTC 時刻の使用が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="b9926-113">The use of UTC time is recommended when a date and time's portability across computers is important.</span></span> <span data-ttu-id="b9926-114">個別のタイム ゾーンを UTC に変換すると、時間の比較が容易になります。</span><span class="sxs-lookup"><span data-stu-id="b9926-114">Converting individual time zones to UTC makes time comparisons easy.</span></span>

> [!NOTE]
> <span data-ttu-id="b9926-115">また、ある時点を明確に表すように [DateTimeOffset](xref:System.DateTimeOffset) 構造体をシリアル化することもできます。</span><span class="sxs-lookup"><span data-stu-id="b9926-115">You can also serialize a [DateTimeOffset](xref:System.DateTimeOffset) structure to unambiguously represent a single point in time.</span></span> <span data-ttu-id="b9926-116">[DateTimeOffset](xref:System.DateTimeOffset) オブジェクトは日時値を UTC からのオフセットと共に格納するので、特定の時点を常に UTC と関連付けて表します。</span><span class="sxs-lookup"><span data-stu-id="b9926-116">Because [DateTimeOffset](xref:System.DateTimeOffset) objects store a date and time value along with its offset from UTC, they always represent a particular point in time in relationship to UTC.</span></span>

<span data-ttu-id="b9926-117">時刻を UTC に変換する最も簡単な方法としては、`static` (Visual Basic では `Shared`) [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b9926-117">The easiest way to convert a time to UTC is to call the `static` (`Shared` in Visual Basic) [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) method.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="b9926-118">`TimeZoneInfo.ConvertTimeToUtc(DateTime)` メソッドは現在 .NET Core で使用できません。</span><span class="sxs-lookup"><span data-stu-id="b9926-118">The `TimeZoneInfo.ConvertTimeToUtc(DateTime)` method isn't currently available in .NET Core.</span></span> 

<span data-ttu-id="b9926-119">次の表に示すように、このメソッドによって実行される実際の変換は、`DateTime` パラメーターの [Kind](xref:System.DateTime.Kind) プロパティの値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b9926-119">The exact conversion performed by the method depends on the value of the `DateTime` parameter's [Kind](xref:System.DateTime.Kind) property, as the following table shows.</span></span>

<span data-ttu-id="b9926-120">[DateTime.Kind](xref:System.DateTimeKind) プロパティ</span><span class="sxs-lookup"><span data-stu-id="b9926-120">[DateTime.Kind](xref:System.DateTimeKind) property</span></span> | <span data-ttu-id="b9926-121">変換</span><span class="sxs-lookup"><span data-stu-id="b9926-121">Conversion</span></span>
---------------------------------------------------------------------------------------------- | ----------
[<span data-ttu-id="b9926-122">DateTimeKind.Local</span><span class="sxs-lookup"><span data-stu-id="b9926-122">DateTimeKind.Local</span></span>](xref:System.DateTimeKind.Local) | <span data-ttu-id="b9926-123">現地時刻を UTC に変換します。</span><span class="sxs-lookup"><span data-stu-id="b9926-123">Converts local time to UTC.</span></span>
[<span data-ttu-id="b9926-124">DateTimeKind.Unspecified</span><span class="sxs-lookup"><span data-stu-id="b9926-124">DateTimeKind.Unspecified</span></span>](xref:System.DateTimeKind.Unspecified) | <span data-ttu-id="b9926-125">`DateTime` パラメーターが現地時刻であることを前提とし、現地時刻を UTC に変換します。</span><span class="sxs-lookup"><span data-stu-id="b9926-125">Assumes the `DateTime` parameter is local time and converts local time to UTC.</span></span>
[<span data-ttu-id="b9926-126">DateTimeKind.Utc</span><span class="sxs-lookup"><span data-stu-id="b9926-126">DateTimeKind.Utc</span></span>](xref:System.DateTimeKind.Utc) | <span data-ttu-id="b9926-127">`DateTime` パラメーターを変更せずに返します。</span><span class="sxs-lookup"><span data-stu-id="b9926-127">Returns the `DateTime` parameter unchanged.</span></span>

<span data-ttu-id="b9926-128">次のコードは、現在の現地時刻を UTC に変換し、コンソールに結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="b9926-128">The following code converts the current local time to UTC and displays the result to the console.</span></span>

```csharp
DateTime dateNow = DateTime.Now;
Console.WriteLine("The date and time are {0} UTC.", 
                   TimeZoneInfo.ConvertTimeToUtc(dateNow));
```

```vb
Dim dateNow As Date = Date.Now      
Console.WriteLine("The date and time are {0} UTC.", _
                  TimeZoneInfo.ConvertTimeToUtc(dateNow))
```

> [!NOTE]
><span data-ttu-id="b9926-129">[TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) メソッドは、[TimeZone.ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) メソッドおよび [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) メソッドと同じ結果を必ずしも生成するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b9926-129">The [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) method does not necessarily produce results that are identical to the [TimeZone.ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) and [DateTime.ToUniversalTime](xref:System.DateTime.ToUniversalTime) methods.</span></span> <span data-ttu-id="b9926-130">ホスト システムのローカル タイム ゾーンに複数の調整規則が含まれる場合、[TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/System.TimeZone.ConvertTimeToUtc(v=vs.110).aspx) は特定の日時に適切な規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="b9926-130">If the host system's local time zone includes multiple adjustment rules, [TimeZoneInfo.ConvertTimeToUtc(DateTime)](https://msdn.microsoft.com/en-us/library/System.TimeZone.ConvertTimeToUtc(v=vs.110).aspx) applies the appropriate rule to a particular date and time.</span></span> <span data-ttu-id="b9926-131">他の 2 つのメソッドは、常に最新の調整規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="b9926-131">The other two methods always apply the latest adjustment rule.</span></span>

<span data-ttu-id="b9926-132">日時値が現地時刻と UTC のどちらかを表さない場合、[ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) メソッドは不正な結果を返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b9926-132">If the date and time value does not represent either the local time or UTC, the [ToUniversalTime](https://msdn.microsoft.com/en-us/library/System.TimeZone.ToUniversalTime(v=vs.110).aspx) method will likely return an erroneous result.</span></span> <span data-ttu-id="b9926-133">ただし、[TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) メソッドを使用して、指定したタイム ゾーンから日時を変換できます</span><span class="sxs-lookup"><span data-stu-id="b9926-133">However, you can use the [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) method to convert the date and time from a specified time zone.</span></span> <span data-ttu-id="b9926-134">(変換先のタイム ゾーンを表す TimeZoneInfo オブジェクトを取得する方法の詳細については、「[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="b9926-134">(For details on retrieving a TimeZoneInfo object that represents the destination time zone, see [Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md).</span></span> <span data-ttu-id="b9926-135">次のコードは、[TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) メソッドを使用して東部標準時を UTC に変換します。</span><span class="sxs-lookup"><span data-stu-id="b9926-135">The following code uses the [TimeZoneInfo.ConvertTimeToUtc](https://msdn.microsoft.com/en-us/library/bb381744(v=vs.110).aspx) method to convert Eastern Standard Time to UTC.</span></span>

```csharp
DateTime easternTime = new DateTime(2007, 01, 02, 12, 16, 00);
string easternZoneId = "Eastern Standard Time";
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId);
   Console.WriteLine("The date and time are {0} UTC.", 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("Unable to find the {0} zone in the registry.", 
                     easternZoneId);
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", 
                     easternZoneId);
}
```

```vb
Dim easternTime As New Date(2007, 01, 02, 12, 16, 00)
Dim easternZoneId As String = "Eastern Standard Time"
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(easternZoneId)
   Console.WriteLine("The date and time are {0} UTC.", _ 
                     TimeZoneInfo.ConvertTimeToUtc(easternTime, easternZone))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("Unable to find the {0} zone in the registry.", _
                     easternZoneId)
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the {0} zone has been corrupted.", _ 
                     easternZoneId)
End Try    
```

<span data-ttu-id="b9926-136">[DateTime](xref:System.DateTime) オブジェクトの [Kind](xref:System.DateTimeKind) プロパティとタイム ゾーンが一致しない場合、このメソッドは [ArgumentException](xref:System.ArgumentException) をスローします。</span><span class="sxs-lookup"><span data-stu-id="b9926-136">Note that this method throws an [ArgumentException](xref:System.ArgumentException) if the [DateTime](xref:System.DateTime) object's [Kind](xref:System.DateTimeKind) property and the time zone are mismatched.</span></span> <span data-ttu-id="b9926-137">Kind プロパティが [DateTimeKind.Local](xref:System.DateTimeKind.Local) であるが [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトがローカル タイム ゾーンを表さない場合、または Kind プロパティが [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) であるが [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトが [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) と等しくない場合に、不一致が発生します。</span><span class="sxs-lookup"><span data-stu-id="b9926-137">A mismatch occurs if the Kind property is [DateTimeKind.Local](xref:System.DateTimeKind.Local) but the [TimeZoneInfo](xref:System.TimeZoneInfo) object does not represent the local time zone, or if the Kind property is [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) but the [TimeZoneInfo](xref:System.TimeZoneInfo) object does not equal [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

<span data-ttu-id="b9926-138">これらすべてのメソッドは、パラメーターとして [DateTime](xref:System.DateTime) 値を受け取り、[DateTime](xref:System.DateTime) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="b9926-138">All of these methods take [DateTime](xref:System.DateTime) values as parameters and return a [DateTime](xref:System.DateTime) value.</span></span> <span data-ttu-id="b9926-139">[DateTimeOffset](xref:System.DateTimeOffset) 値について、[DateTimeOffset](xref:System.DateTimeOffset) 構造体には、現在のインスタンスの日時を UTC に変換する [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) インスタンス メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9926-139">For [DateTimeOffset](xref:System.DateTimeOffset) values, the [DateTimeOffset](xref:System.DateTimeOffset) structure has a [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) instance method that converts the date and time of the current instance to UTC.</span></span> <span data-ttu-id="b9926-140">次の例では、[ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) メソッドを呼び出して、現地時刻およびその他のいくつかの時刻を世界協定時刻 (UTC) に変換します。</span><span class="sxs-lookup"><span data-stu-id="b9926-140">The following example calls the [ToUniversalTime](xref:System.DateTimeOffset.ToUniversalTime) method to convert a local time and several other times to Coordinated Universal Time (UTC).</span></span>

```csharp
DateTimeOffset localTime, otherTime, universalTime;

// Define local time in local time zone
localTime = new DateTimeOffset(new DateTime(2007, 6, 15, 12, 0, 0));
Console.WriteLine("Local time: {0}", localTime);
Console.WriteLine();

// Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero);
Console.WriteLine("Other time: {0}", otherTime);
Console.WriteLine("{0} = {1}: {2}", 
                  localTime, otherTime, 
                  localTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  localTime, otherTime, 
                  localTime.EqualsExact(otherTime));
Console.WriteLine();

// Convert other time to UTC
universalTime = localTime.ToUniversalTime(); 
Console.WriteLine("Universal time: {0}", universalTime);
Console.WriteLine("{0} = {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.Equals(otherTime));
Console.WriteLine("{0} exactly equals {1}: {2}", 
                  otherTime, universalTime, 
                  universalTime.EqualsExact(otherTime));
Console.WriteLine();
// The example produces the following output to the console:
//    Local time: 6/15/2007 12:00:00 PM -07:00
//    
//    Other time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
//    
//    Universal time: 6/15/2007 7:00:00 PM +00:00
//    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
//    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

```vb
Dim localTime, otherTime, universalTime As DateTimeOffset

' Define local time in local time zone
localTime = New DateTimeOffset(#6/15/2007 12:00:00PM#)
Console.WriteLine("Local time: {0}", localTime)
Console.WriteLine()

' Convert local time to offset 0 and assign to otherTime
otherTime = localTime.ToOffset(TimeSpan.Zero)
Console.WriteLine("Other time: {0}", otherTime)
Console.WriteLine("{0} = {1}: {2}", _
                  localTime, otherTime, _
                  localTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  localTime, otherTime, _
                  localTime.EqualsExact(otherTime))
Console.WriteLine()

' Convert other time to UTC
universalTime = localTime.ToUniversalTime() 
Console.WriteLine("Universal time: {0}", universalTime)
Console.WriteLine("{0} = {1}: {2}", _
                  otherTime, universalTime, _ 
                  universalTime.Equals(otherTime))
Console.WriteLine("{0} exactly equals {1}: {2}", _ 
                  otherTime, universalTime, _
                  universalTime.EqualsExact(otherTime))
Console.WriteLine()
' The example produces the following output to the console:
'    Local time: 6/15/2007 12:00:00 PM -07:00
'    
'    Other time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 12:00:00 PM -07:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 12:00:00 PM -07:00 exactly equals 6/15/2007 7:00:00 PM +00:00: False
'    
'    Universal time: 6/15/2007 7:00:00 PM +00:00
'    6/15/2007 7:00:00 PM +00:00 = 6/15/2007 7:00:00 PM +00:00: True
'    6/15/2007 7:00:00 PM +00:00 exactly equals 6/15/2007 7:00:00 PM +00:00: True 
```

## <a name="converting-utc-to-a-designated-time-zone"></a><span data-ttu-id="b9926-141">UTC から指定したタイム ゾーンへの変換</span><span class="sxs-lookup"><span data-stu-id="b9926-141">Converting UTC to a designated time zone</span></span>

<span data-ttu-id="b9926-142">UTC を現地時刻に変換するには、後の「[UTC から現地時刻への変換](#converting-utc-to-local-time)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9926-142">To convert UTC to local time, see the [Converting UTC to local time](#converting-utc-to-local-time) section that follows.</span></span> 

<span data-ttu-id="b9926-143">UTC を、指定した任意のタイム ゾーンの時刻に変換するには、[ConvertTimeFromUtc](https://msdn.microsoft.com/en-us/library/System.TimeZoneInfo.converttimefromutc(v=vs.110).aspx) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b9926-143">To convert UTC to the time in any time zone that you designate, call the [ConvertTimeFromUtc](https://msdn.microsoft.com/en-us/library/System.TimeZoneInfo.converttimefromutc(v=vs.110).aspx) method.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="b9926-144">.NET Core では、\`TimeZoneInfo.ConvertTimeFromUtc' メソッドは現在使用できません。</span><span class="sxs-lookup"><span data-stu-id="b9926-144">The \`TimeZoneInfo.ConvertTimeFromUtc' method isn't currently available in .NET Core.</span></span> 

<span data-ttu-id="b9926-145">このメソッドは、次の 2 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="b9926-145">The method takes two parameters:</span></span>

* <span data-ttu-id="b9926-146">変換対象の UTC。</span><span class="sxs-lookup"><span data-stu-id="b9926-146">The UTC to convert.</span></span> <span data-ttu-id="b9926-147">これは、[Kind](xref:System.DateTime.Kind) にプロパティが [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) または [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) に設定されている [DateTime](xref:System.DateTime) 値でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="b9926-147">This must be a [DateTime](xref:System.DateTime) value whose [Kind](xref:System.DateTime.Kind) property is set to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) or [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span></span> 

* <span data-ttu-id="b9926-148">UTC の変換先のタイム ゾーン。</span><span class="sxs-lookup"><span data-stu-id="b9926-148">The time zone to convert the UTC to.</span></span> 

<span data-ttu-id="b9926-149">次のコードは、UTC を中部標準時に変換します。</span><span class="sxs-lookup"><span data-stu-id="b9926-149">The following code converts UTC to Central Standard Time.</span></span>

```csharp
DateTime timeUtc = DateTime.UtcNow;
try
{
   TimeZoneInfo cstZone = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time");
   DateTime cstTime = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone);
   Console.WriteLine("The date and time are {0} {1}.", 
                     cstTime, 
                     cstZone.IsDaylightSavingTime(cstTime) ?
                             cstZone.DaylightName : cstZone.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Central Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.");
}
```

```vb
Dim timeUtc As Date = Date.UtcNow
Try
   Dim cstZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Central Standard Time")
   Dim cstTime As Date = TimeZoneInfo.ConvertTimeFromUtc(timeUtc, cstZone)
   Console.WriteLine("The date and time are {0} {1}.", _
                     cstTime, _
                     IIf(cstZone.IsDaylightSavingTime(cstTime), _
                         cstZone.DaylightName, cstZone.StandardName))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Central Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Central Standard Time zone has been corrupted.")
End Try
``` 

## <a name="converting-utc-to-local-time"></a><span data-ttu-id="b9926-150">UTC から現地時刻への変換</span><span class="sxs-lookup"><span data-stu-id="b9926-150">Converting UTC to local time</span></span>

<span data-ttu-id="b9926-151">UTC を現地時刻に変換するには、時刻を変換する対象の [DateTime](xref:System.DateTime) オブジェクトの [DateTime.ToLocalTime](xref:System.DateTime) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b9926-151">To convert UTC to local time, call the [DateTime.ToLocalTime](xref:System.DateTime) method of the [DateTime](xref:System.DateTime) object whose time you want to convert.</span></span> <span data-ttu-id="b9926-152">次の表に示すように、このメソッドの実際の動作は、オブジェクトの [Kind](xref:System.DateTime.Kind) プロパティの値によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b9926-152">The exact behavior of the method depends on the value of the object’s [Kind](xref:System.DateTime.Kind) property, as the following table shows.</span></span>

<span data-ttu-id="b9926-153">[DateTime.Kind](xref:System.DateTimeKind) プロパティ</span><span class="sxs-lookup"><span data-stu-id="b9926-153">[DateTime.Kind](xref:System.DateTimeKind) property</span></span> | <span data-ttu-id="b9926-154">変換</span><span class="sxs-lookup"><span data-stu-id="b9926-154">Conversion</span></span>
---------------------------------------------------------------------------------------------- | ----------
[<span data-ttu-id="b9926-155">DateTimeKind.Local</span><span class="sxs-lookup"><span data-stu-id="b9926-155">DateTimeKind.Local</span></span>](xref:System.DateTimeKind.Local) | <span data-ttu-id="b9926-156">[DateTime](xref:System.DateTime) 値を変更せずに返します。</span><span class="sxs-lookup"><span data-stu-id="b9926-156">Returns the [DateTime](xref:System.DateTime) value unchanged.</span></span>
[<span data-ttu-id="b9926-157">DateTimeKind.Unspecified</span><span class="sxs-lookup"><span data-stu-id="b9926-157">DateTimeKind.Unspecified</span></span>](xref:System.DateTimeKind.Unspecified) | <span data-ttu-id="b9926-158">[DateTime](xref:System.DateTime) 値が UTC であることを前提とし、UTC を現地時刻に変換します。</span><span class="sxs-lookup"><span data-stu-id="b9926-158">Assumes that the [DateTime](xref:System.DateTime) value is UTC and converts the UTC to local time.</span></span>
[<span data-ttu-id="b9926-159">DateTimeKind.Utc</span><span class="sxs-lookup"><span data-stu-id="b9926-159">DateTimeKind.Utc</span></span>](xref:System.DateTimeKind.Utc) | <span data-ttu-id="b9926-160">[DateTime](xref:System.DateTime) 値を現地時刻に変換します。</span><span class="sxs-lookup"><span data-stu-id="b9926-160">Converts the [DateTime](xref:System.DateTime) value to local time.</span></span>

## <a name="converting-between-any-two-time-zones"></a><span data-ttu-id="b9926-161">任意の 2 つのタイム ゾーン間での変換</span><span class="sxs-lookup"><span data-stu-id="b9926-161">Converting between any two time zones</span></span>

<span data-ttu-id="b9926-162">静的な [TimeZoneInfo.ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) メソッドを使用すると、任意の 2 つのタイム ゾーン間で変換を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b9926-162">You can convert between any two time zones by using the static [TimeZoneInfo.ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span> <span data-ttu-id="b9926-163">このメソッドのパラメーターは、変換対象の [DateTime](xref:System.DateTime) 値、日時値のタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクト、および日時値の変換先のタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="b9926-163">This method's parameters are the [DateTime](xref:System.DateTime) value to convert, a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the time zone of the date and time value, and a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the time zone to convert the date and time value to.</span></span>

<span data-ttu-id="b9926-164">このメソッドでは、変換対象の日時値の [Kind](xref:System.DateTime.Kind) プロパティと、タイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトまたはタイム ゾーン識別子とが、相互に対応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9926-164">The method requires that the [Kind](xref:System.DateTime.Kind) property of the date and time value to convert and the [TimeZoneInfo](xref:System.TimeZoneInfo) object or time zone identifier that represents its time zone correspond to one another.</span></span> <span data-ttu-id="b9926-165">それ以外の場合は、[ArgumentException](xref:System.ArgumentException) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b9926-165">Otherwise, an [ArgumentException](xref:System.ArgumentException) is thrown.</span></span> <span data-ttu-id="b9926-166">たとえば、日時値の [Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Local](xref:System.DateTimeKind.Local) である場合に、このメソッドにパラメーターとして渡された [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトが [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) と等しくなければ、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b9926-166">For example, if the [Kind](xref:System.DateTime.Kind) property of the date and time value is [DateTimeKind.Local](xref:System.DateTimeKind.Local), an exception is thrown if the [TimeZoneInfo](xref:System.TimeZoneInfo) object passed as a parameter to the method is not equal to [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local).</span></span> <span data-ttu-id="b9926-167">また、このメソッドにパラメーターとして渡された識別子が [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) と等しくない場合にも、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b9926-167">An exception is also thrown if the identifier passed as a parameter to the method is not equal to [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id).</span></span>

<span data-ttu-id="b9926-168">次の例では、[ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) メソッドを使用してハワイ標準時を現地時刻に変換します。</span><span class="sxs-lookup"><span data-stu-id="b9926-168">The following example uses the [ConvertTime](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method to convert from Hawaiian Standard Time to local time.</span></span>

```csharp
DateTime hwTime = new DateTime(2007, 02, 01, 08, 00, 00);
try
{
   TimeZoneInfo hwZone = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time");
   Console.WriteLine("{0} {1} is {2} local time.", 
           hwTime, 
           hwZone.IsDaylightSavingTime(hwTime) ? hwZone.DaylightName : hwZone.StandardName, 
           TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local));
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.");
}                           
catch (InvalidTimeZoneException)
{
   Console.WriteLine("Registry data on the Hawaiian STandard Time zone has been corrupted.");
}
```

```vb
Dim hwTime As Date = #2/01/2007 8:00:00 AM#
Try
   Dim hwZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Hawaiian Standard Time")
   Console.WriteLine("{0} {1} is {2} local time.", _
                     hwTime, _
                     IIf(hwZone.IsDaylightSavingTime(hwTime), hwZone.DaylightName, hwZone.StandardName), _
                     TimeZoneInfo.ConvertTime(hwTime, hwZone, TimeZoneInfo.Local))
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The registry does not define the Hawaiian Standard Time zone.")
Catch e As InvalidTimeZoneException
   Console.WriteLine("Registry data on the Hawaiian Standard Time zone has been corrupted.")
End Try
```

## <a name="converting-datetimeoffset-values"></a><span data-ttu-id="b9926-169">DateTimeOffset 値の変換</span><span class="sxs-lookup"><span data-stu-id="b9926-169">Converting DateTimeOffset values</span></span>

<span data-ttu-id="b9926-170">[System.DateTimeOffset](xref:System.DateTimeOffset) オブジェクトによって表される日時値は、完全にはタイム ゾーン対応ではありません。これは、オブジェクトがインスタンス化された時点でそのタイム ゾーンとの関連付けが解除されるためです。</span><span class="sxs-lookup"><span data-stu-id="b9926-170">Date and time values represented by [System.DateTimeOffset](xref:System.DateTimeOffset) objects are not fully time-zone aware because the object is disassociated from its time zone at the time it is instantiated.</span></span> <span data-ttu-id="b9926-171">ただし、アプリケーションでは多くの場合、特定のタイム ゾーンの時刻ではなく、単に UTC からの 2 つの異なるオフセットに基づいて日時を変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9926-171">However, in many cases an application simply needs to convert a date and time based on two different offsets from UTC rather than on the time in particular time zones.</span></span> <span data-ttu-id="b9926-172">この変換を実行するには、現在のインスタンスの [ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b9926-172">To perform this conversion, you can call the current instance's [ToOffset](xref:System.DateTimeOffset.ToOffset(System.TimeSpan)) method.</span></span> <span data-ttu-id="b9926-173">このメソッドの単一のパラメーターは、メソッドが返す新しい日時値のオフセットを表す [TimeSpan](xref:System.TimeSpan) です。</span><span class="sxs-lookup"><span data-stu-id="b9926-173">The method's single parameter is [TimeSpan](xref:System.TimeSpan) representing the offset of the new date and time value that the method is to return.</span></span>  

<span data-ttu-id="b9926-174">たとえば、Web ページに対するユーザー要求の日時が既知であり、MM/dd/yyyy hh:mm:ss zzzz の形式で文字列としてシリアル化される場合、次の `ReturnTimeOnServer` メソッドは、この日時値を Web サーバー上の日時に変換します。</span><span class="sxs-lookup"><span data-stu-id="b9926-174">For example, if the date and time of a user request for a Web page is known and is serialized as a string in the format MM/dd/yyyy hh:mm:ss zzzz, the following `ReturnTimeOnServer` method converts this date and time value to the date and time on the Web server.</span></span>

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";
   TimeSpan serverOffset = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now);

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = clientTime.ToOffset(serverOffset);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"
   Dim serverOffset As TimeSpan = TimeZoneInfo.Local.GetUtcOffset(DateTimeOffset.Now)

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = clientTime.ToOffset(serverOffset)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

<span data-ttu-id="b9926-175">このメソッドが、UTC よりも 5 時間遅いタイム ゾーンの日時を表す文字列 "9/1/2007 5:32:07 -05:00" を渡された場合、米国の太平洋標準時ゾーンにあるサーバー用に 9/1/2007 3:32:07 AM -07:00 を返します。</span><span class="sxs-lookup"><span data-stu-id="b9926-175">If the method is passed the string "9/1/2007 5:32:07 -05:00", which represents the date and time in a time zone five hours earlier than UTC, it returns 9/1/2007 3:32:07 AM -07:00 for a server located in the U.S. Pacific Standard Time zone.</span></span>

<span data-ttu-id="b9926-176">[TimeZoneInfo](xref:System.TimeZoneInfo) クラスには、[System.DateTimeOffset](xref:System.DateTimeOffset) 値によるタイム ゾーン変換を実行する、オーバーロードされた [TimeZoneInfo.ConvertTime (DateTimeOffset、TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) メソッドも含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9926-176">The [TimeZoneInfo](xref:System.TimeZoneInfo) class also includes an overloaded [TimeZoneInfo.ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) method that performs time zone conversions with [System.DateTimeOffset](xref:System.DateTimeOffset) values.</span></span> <span data-ttu-id="b9926-177">このメソッドのパラメーターは、[System.DateTimeOffset](xref:System.DateTimeOffset) 値と、時刻の変換先となるタイム ゾーンへの参照です。</span><span class="sxs-lookup"><span data-stu-id="b9926-177">The method's parameters are a [System.DateTimeOffset](xref:System.DateTimeOffset) value and a reference to the time zone to which the time is to be converted.</span></span> <span data-ttu-id="b9926-178">このメソッド呼び出しは、[System.DateTimeOffset](xref:System.DateTimeOffset) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="b9926-178">The method call returns a [System.DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="b9926-179">たとえば、前の例の `ReturnTimeOnServer` メソッドを次のように書き換えて、[ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b9926-179">For example, the `ReturnTimeOnServer` method in the previous example could be rewritten as follows to call the [ConvertTime(DateTimeOffset, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTimeOffset,System.TimeZoneInfo)) method.</span></span>

```csharp
public DateTimeOffset ReturnTimeOnServer(string clientString)
{
   string format = @"M/d/yyyy H:m:s zzz";

   try
   {      
      DateTimeOffset clientTime = DateTimeOffset.ParseExact(clientString, format, 
                                  CultureInfo.InvariantCulture);
      DateTimeOffset serverTime = TimeZoneInfo.ConvertTime(clientTime, 
                                  TimeZoneInfo.Local);
      return serverTime;
   }
   catch (FormatException)
   {
      return DateTimeOffset.MinValue;
   }
}
```

```vb
Public Function ReturnTimeOnServer(clientString As String) As DateTimeOffset
   Dim format As String = "M/d/yyyy H:m:s zzz"

   Try      
      Dim clientTime As DateTimeOffset = DateTimeOffset.ParseExact(clientString, format, CultureInfo.InvariantCulture)
      Dim serverTime As DateTimeOffset = TimeZoneInfo.ConvertTime(clientTime, TimeZoneInfo.Local)
      Return serverTime
   Catch e As FormatException
      Return DateTimeOffset.MinValue
   End Try    
End Function
```

## <a name="see-also"></a><span data-ttu-id="b9926-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9926-180">See also</span></span>

[<span data-ttu-id="b9926-181">TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="b9926-181">TimeZoneInfo</span></span>](xref:System.TimeZoneInfo)

[<span data-ttu-id="b9926-182">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="b9926-182">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="b9926-183">ローカル システムで定義されているタイム ゾーンの検索</span><span class="sxs-lookup"><span data-stu-id="b9926-183">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)



