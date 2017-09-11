---
title: "方法: あいまいな時刻を解決する"
description: "あいまいな時刻を解決する方法"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: e86050c6-d16d-405e-8bba-7205945c9a81
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f4ab3b4bf3487e70be7e885e9b8a2281927eb30e
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="8b9ab-104">方法: あいまいな時刻を解決する</span><span class="sxs-lookup"><span data-stu-id="8b9ab-104">How to: resolve ambiguous times</span></span>

<span data-ttu-id="8b9ab-105">あいまいな時刻とは、複数の世界協定時刻 (UTC) にマップされる時刻です。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-105">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="8b9ab-106">これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-106">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="8b9ab-107">あいまいな時刻を処理する場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-107">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="8b9ab-108">時刻が UTC にどのようにマップされるかを想定します。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-108">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="8b9ab-109">たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-109">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="8b9ab-110">あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-110">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="8b9ab-111">この記事では、タイム ゾーンの標準時刻を表すと想定して、あいまいな時刻を解決する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-111">This article shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

## <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="8b9ab-112">あいまいな時刻をタイム ゾーンの標準時刻にマップするには</span><span class="sxs-lookup"><span data-stu-id="8b9ab-112">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="8b9ab-113">[System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) または [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) メソッドを呼び出して、時刻があいまいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-113">Call the [System.TimeZoneInfo.IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) or [System.TimeZoneInfo.IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="8b9ab-114">時刻があいまいな場合は、タイム ゾーンの [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) プロパティによって返される [TimeSpan](xref:System.TimeSpan) オブジェクトから時刻を減算します。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-114">If the time is ambiguous, subtract the time from the [TimeSpan](xref:System.TimeSpan) object returned by the time zone's [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property.</span></span>

3. <span data-ttu-id="8b9ab-115">`static` (Visual Basic では `Shared`) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) メソッドを呼び出して、UTC の日付と時刻の値の [Kind](xref:System.DateTime.Kind) プロパティを [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) に設定します。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-115">Call the `static` (`Shared` in Visual Basic) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method to set the UTC date and time value's [Kind](xref:System.DateTime.Kind) property to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="example"></a><span data-ttu-id="8b9ab-116">例</span><span class="sxs-lookup"><span data-stu-id="8b9ab-116">Example</span></span>

<span data-ttu-id="8b9ab-117">次の例では、あいまいな時刻がローカル タイム ゾーンの標準時刻を表すと想定して、あいまいな [DateTime](xref:System.DateTime) を UTC に変換する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-117">The following example illustrates how to convert an ambiguous [DateTime](xref:System.DateTime) to UTC by assuming that it represents the local time zone's standard time.</span></span> 

```csharp
private DateTime ResolveAmbiguousTime(DateTime ambiguousTime)
{
   // Time is not ambiguous
   if (! TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime))
   { 
      return ambiguousTime; 
   }
   // Time is ambiguous
   else
   {
      DateTime utcTime = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, 
                                              DateTimeKind.Utc);      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", 
                        ambiguousTime, utcTime, utcTime.Kind.ToString());
      return utcTime;            
   }   
}
```

```vb
Private Function ResolveAmbiguousTime(ambiguousTime As Date) As Date
   ' Time is not ambiguous
   If Not TimeZoneInfo.Local.IsAmbiguousTime(ambiguousTime) Then 
      Return TimeZoneInfo.ConvertTimeToUtc(ambiguousTime) 
   ' Time is ambiguous
   Else
      Dim utcTime As Date = DateTime.SpecifyKind(ambiguousTime - TimeZoneInfo.Local.BaseUtcOffset, DateTimeKind.Utc)      
      Console.WriteLine("{0} local time corresponds to {1} {2}.", ambiguousTime, utcTime, utcTime.Kind.ToString())
      Return utcTime            
   End If   
End Function
```

<span data-ttu-id="8b9ab-118">この例は、渡された [DateTime](xref:System.DateTime) 値があいまいかどうかを判定する `ResolveAmbiguousTime` という名前のメソッドで構成されます。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-118">The example consists of a method named `ResolveAmbiguousTime` that determines whether the [DateTime](xref:System.DateTime) value passed to it is ambiguous.</span></span> <span data-ttu-id="8b9ab-119">値があいまいな場合、メソッドは対応する UTC 時刻を表す [DateTime](xref:System.DateTime) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-119">If the value is ambiguous, the method returns a [DateTime](xref:System.DateTime) value that represents the corresponding UTC time.</span></span> <span data-ttu-id="8b9ab-120">このメソッドは、ローカル タイム ゾーンの [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) プロパティの値をローカル時刻から減算して、この変換を行います。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-120">The method handles this conversion by subtracting the value of the local time zone's [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property from the local time.</span></span> 

<span data-ttu-id="8b9ab-121">通常、あいまいな時刻の処理では、[GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) メソッドを呼び出し、あいまいな時刻に対して考えられる UTC オフセットが格納されている [TimeSpan](xref:System.TimeSpan) オブジェクトの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-121">Ordinarily, an ambiguous time is handled by calling the [GetAmbiguousTimeOffsets](xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets(System.DateTime)) method to retrieve an array of [TimeSpan](xref:System.TimeSpan) objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="8b9ab-122">しかし、この例は、あいまいな時刻は常にタイム ゾーンの標準時刻にマップされるという想定に基づいています。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-122">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="8b9ab-123">[BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) プロパティは、UTC とタイム ゾーンの標準時刻の間のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="8b9ab-123">The [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property returns the offset between UTC and a time zone's standard time.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b9ab-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b9ab-124">See Also</span></span>

[<span data-ttu-id="8b9ab-125">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="8b9ab-125">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="8b9ab-126">方法: ユーザーがあいまいな時刻を解決できるようにする</span><span class="sxs-lookup"><span data-stu-id="8b9ab-126">How to: let users resolve ambiguous times</span></span>](let-users-resolve-ambiguous-times.md)


