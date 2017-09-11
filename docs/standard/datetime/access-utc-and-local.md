---
title: "方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする"
description: "方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 13454d47-d957-421b-9ecd-940058b8835e
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: fcc48e40cdad25c6142dbc3a86513b816378fa4b
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="841f0-104">方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする</span><span class="sxs-lookup"><span data-stu-id="841f0-104">How to: access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="841f0-105">[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスに用意されている&2; つのプロパティ、`Utc` および `Local` を使用すると、コードから定義済みのタイム ゾーン オブジェクトにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="841f0-105">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class provides two properties, `Utc` and `Local`, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="841f0-106">このトピックでは、これらのプロパティから返される `TimeZoneInfo` オブジェクトにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="841f0-106">This topic discusses how to access the `TimeZoneInfo` objects returned by those properties.</span></span>

## <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="841f0-107">世界協定時刻 (UTC) の TimeZoneInfo オブジェクトにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="841f0-107">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="841f0-108">**static** (Visual Basic では **Shared**) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティを使用して、世界協定時刻にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="841f0-108">Use the **static** (**Shared** in Visual Basic) [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="841f0-109">プロパティから返された [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをオブジェクト変数に割り当てるのではなく、そのまま [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティを使用して世界協定時刻にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="841f0-109">Rather than assigning the [TimeZoneInfo](xref:System.TimeZoneInfo) object returned by the property to an object variable, continue to access Coordinated Universal Time through the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property.</span></span>


## <a name="to-access-the-local-time-zone"></a><span data-ttu-id="841f0-110">ローカル タイム ゾーンにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="841f0-110">To access the local time zone</span></span>

1. <span data-ttu-id="841f0-111">**static** (Visual Basic では **Shared**) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティを使用して、ローカル タイム ゾーンにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="841f0-111">Use the **static** (**Shared** in Visual Basic) [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property to access the local system time zone.</span></span>

2. <span data-ttu-id="841f0-112">プロパティから返された [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをオブジェクト変数に割り当てるのではなく、そのまま [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティを使用してローカル タイム ゾーンにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="841f0-112">Rather than assigning the [TimeZoneInfo](xref:System.TimeZoneInfo) object returned by the property to an object variable, continue to access the local time zone through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property.</span></span>

## <a name="example"></a><span data-ttu-id="841f0-113">例</span><span class="sxs-lookup"><span data-stu-id="841f0-113">Example</span></span>

<span data-ttu-id="841f0-114">次のコードでは、[TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティと [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティを使用して、米国およびカナダ東部標準時タイム ゾーンの時刻を変換し、コンソールにタイム ゾーンの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="841f0-114">The following code uses the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) and [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

```csharp
// Create Eastern Standard Time value and TimeZoneInfo object      
DateTime estTime = new DateTime(2007, 1, 1, 00, 00, 00);
string timeZoneName = "Eastern Standard Time";
try
{
   TimeZoneInfo est = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName);

   // Convert EST to local time
   DateTime localTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local);
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", 
           estTime, 
           est, 
           localTime, 
           TimeZoneInfo.Local.IsDaylightSavingTime(localTime) ?
                     TimeZoneInfo.Local.DaylightName : 
                     TimeZoneInfo.Local.StandardName);

   // Convert EST to UTC
   DateTime utcTime = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc);
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", 
           estTime, 
           est, 
           utcTime, 
           TimeZoneInfo.Utc.StandardName);
}
catch (TimeZoneNotFoundException)
{
   Console.WriteLine("The {0} zone cannot be found in the registry.", 
                     timeZoneName);
}
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The registry contains invalid data for the {0} zone.", 
                     timeZoneName);
}
```

```vb
' Create Eastern Standard Time value and TimeZoneInfo object      
Dim estTime As Date = #01/01/2007 00:00:00#
Dim timeZoneName As String = "Eastern Standard Time"
Try
   Dim est As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timeZoneName)

   ' Convert EST to local time
   Dim localTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Local)
   Console.WriteLine("At {0} {1}, the local time is {2} {3}.", _
           estTime, _
           est, _
           localTime, _
           IIf(TimeZoneInfo.Local.IsDaylightSavingTime(localTime), _
               TimeZoneInfo.Local.DaylightName, _
               TimeZoneInfo.Local.StandardName))

   ' Convert EST to UTC
   Dim utcTime As Date = TimeZoneInfo.ConvertTime(estTime, est, TimeZoneInfo.Utc)
   Console.WriteLine("At {0} {1}, the time is {2} {3}.", _
           estTime, _
           est, _
           utcTime, _
           TimeZoneInfo.Utc.StandardName)
Catch e As TimeZoneNotFoundException
   Console.WriteLine("The {0} zone cannot be found in the registry.", _
                     timeZoneName)
Catch e As InvalidTimeZoneException
   Console.WriteLine("The registry contains invalid data for the {0} zone.", _
                     timeZoneName)
End Try
```

<span data-ttu-id="841f0-115">ローカル タイム ゾーンにアクセスする場合は、ローカル タイム ゾーンを [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクト変数に割り当てることはせず、常に [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティを使用してください。</span><span class="sxs-lookup"><span data-stu-id="841f0-115">You should always access the local time zone through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property rather than assigning the local time zone to a [TimeZoneInfo](xref:System.TimeZoneInfo) object variable.</span></span> <span data-ttu-id="841f0-116">同様に、世界協定時刻にアクセスする場合は、UTC ゾーンを [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクト変数に割り当てることはせず、常に [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティを使用してください。</span><span class="sxs-lookup"><span data-stu-id="841f0-116">Similarly, you should always access Coordinated Universal Time through the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) property rather than assigning the UTC zone to a [TimeZoneInfo](xref:System.TimeZoneInfo) object variable.</span></span> <span data-ttu-id="841f0-117">これにより、[TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクト変数が外部メソッドによって無効になるのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="841f0-117">This prevents the [TimeZoneInfo](xref:System.TimeZoneInfo) object variable from being invalidated by an external method.</span></span>


## <a name="see-also"></a><span data-ttu-id="841f0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="841f0-118">See Also</span></span>

[<span data-ttu-id="841f0-119">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="841f0-119">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="841f0-120">ローカル システムで定義されているタイム ゾーンの検索</span><span class="sxs-lookup"><span data-stu-id="841f0-120">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)

