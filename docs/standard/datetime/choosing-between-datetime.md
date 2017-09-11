---
title: "DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け"
description: "DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/11/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 2dd84ee8-9f0f-4054-9537-155857a460cd
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: aeb1928be32584ee4b6acf7c9a4f4330daedc590
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a><span data-ttu-id="35dde-104">DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け</span><span class="sxs-lookup"><span data-stu-id="35dde-104">Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>

<span data-ttu-id="35dde-105">日時情報を使用する .NET アプリケーションは非常に多様であり、その情報をさまざまな方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="35dde-105">.NET applications that use date and time information are very diverse and can use that information in several ways.</span></span> <span data-ttu-id="35dde-106">より一般的な日時情報の用途には、次の&1; つ以上が含まれます。</span><span class="sxs-lookup"><span data-stu-id="35dde-106">The more common uses of date and time information include one or more of the following:</span></span>

* <span data-ttu-id="35dde-107">日付のみを反映する (時刻情報は重要ではない)。</span><span class="sxs-lookup"><span data-stu-id="35dde-107">To reflect a date only, so that time information is not important.</span></span>

* <span data-ttu-id="35dde-108">時刻のみを反映する (日付情報は重要ではない)。</span><span class="sxs-lookup"><span data-stu-id="35dde-108">To reflect a time only, so that date information is not important.</span></span>

* <span data-ttu-id="35dde-109">特定の時刻と場所に関連付けられていない抽象日時を反映する (たとえば、国際的チェーンのほとんどのストアは週中の午前 9:00 にオープンする)。</span><span class="sxs-lookup"><span data-stu-id="35dde-109">To reflect an abstract date and time that is not tied to a specific time and place (for example, most stores in an international chain open on weekdays at 9:00 A.M.).</span></span>

* <span data-ttu-id="35dde-110">.NET アプリケーションの外部ソースから日時情報を取得する (通常、日時情報は単純なデータ型に格納される)。</span><span class="sxs-lookup"><span data-stu-id="35dde-110">To retrieve date and time information from sources outside of the .NET application, typically where date and time information is stored in a simple data type.</span></span>

* <span data-ttu-id="35dde-111">単一の時点を一意かつ明確に識別する。</span><span class="sxs-lookup"><span data-stu-id="35dde-111">To uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="35dde-112">ホスト システムでのみ日付と時刻を明確にする必要があるアプリケーションもあれば、システム全体で明確にする必要があるアプリケーションもあります (つまり、1 つのシステムでシリアル化される日付は有意に逆シリアル化し、世界中のどの場所においても別のシステムで使用できます)。</span><span class="sxs-lookup"><span data-stu-id="35dde-112">Some applications require that a date and time be unambiguous only on the host system; others require that it be unambiguous across systems (that is, a date serialized on one system can be meaningfully deserialized and used on another system anywhere in the world).</span></span> 

* <span data-ttu-id="35dde-113">関連する複数の時刻を保持する (要求元の現地時刻やサーバーの Web 要求受信時刻など)。</span><span class="sxs-lookup"><span data-stu-id="35dde-113">To preserve multiple related times (such as the requestor's local time and the server's time of receipt for a Web request).</span></span>

* <span data-ttu-id="35dde-114">日付と時刻の演算を実行する (これにより、おそらく単一時点が一意かつ明確に識別される)。</span><span class="sxs-lookup"><span data-stu-id="35dde-114">To perform date and time arithmetic, possibly with a result that uniquely and unambiguously identifies a single point in time.</span></span> 

<span data-ttu-id="35dde-115">.NET には、[System.DateTime](xref:System.DateTime)、[System.DateTimeOffset](xref:System.DateTimeOffset)、[System.TimeSpan](xref:System.TimeSpan)、[System.TimeZoneInfo](xref:System.TimeZoneInfo) の各型が含まれます。このすべては、日付と時刻を使用するアプリケーションを構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="35dde-115">.NET includes the [System.DateTime](xref:System.DateTime), [System.DateTimeOffset](xref:System.DateTimeOffset), [System.TimeSpan](xref:System.TimeSpan), and [System.TimeZoneInfo](xref:System.TimeZoneInfo) types, all of which can be used to build applications that work with dates and times.</span></span> 

> [!NOTE]
> <span data-ttu-id="35dde-116">このトピックでは古い `TimeZone` 型については説明されません。その機能は、[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスにほぼ完全に組み込まれているからです。</span><span class="sxs-lookup"><span data-stu-id="35dde-116">This topic does not discuss the older `TimeZone` type, because its functionality is almost entirely incorporated in the [System.TimeZoneInfo](xref:System.TimeZoneInfo) class.</span></span> <span data-ttu-id="35dde-117">開発者は可能な限り、`TimeZone` クラスの代わりに [System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35dde-117">Whenever possible, developers should use the [System.TimeZoneInfo](xref:System.TimeZoneInfo) class instead of the `TimeZone` class.</span></span>


## <a name="the-datetime-structure"></a><span data-ttu-id="35dde-118">DateTime 構造体</span><span class="sxs-lookup"><span data-stu-id="35dde-118">The DateTime structure</span></span>

<span data-ttu-id="35dde-119">[System.DateTime](xref:System.DateTime) 値は、特定の日付と時刻を定義します。</span><span class="sxs-lookup"><span data-stu-id="35dde-119">A [System.DateTime](xref:System.DateTime) value defines a particular date and time.</span></span> <span data-ttu-id="35dde-120">これには日付と時刻が属するタイム ゾーンに関する限られた情報を提供する [Kind](xref:System.DateTime.Kind) プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="35dde-120">It includes a [Kind](xref:System.DateTime.Kind) property that provides limited information about the time zone to which that date and time belongs.</span></span> <span data-ttu-id="35dde-121">[Kind](xref:System.DateTime.Kind) プロパティによって返される [DateTimeKind](xref:System.DateTimeKind) 値は、[DateTime](xref:System.DateTime) 値が現地時刻 ([DateTimeKind.Local](xref:System.DateTimeKind.Local))、世界協定時刻 (UTC) ([DateTimeKind.Utc](xref:System.DateTimeKind.Utc))、指定されていない時刻 ([DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified)) のうちのどれを表すかを示します。</span><span class="sxs-lookup"><span data-stu-id="35dde-121">The [DateTimeKind](xref:System.DateTimeKind) value returned by the [Kind](xref:System.DateTime.Kind) property indicates whether the [DateTime](xref:System.DateTime) value represents the local time [DateTimeKind.Local](xref:System.DateTimeKind.Local)), Coordinated Universal Time (UTC) [DateTimeKind.Utc](xref:System.DateTimeKind.Utc), or an unspecified time [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified).</span></span>

<span data-ttu-id="35dde-122">[DateTime](xref:System.DateTime) 構造体は、次の操作を実行するアプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="35dde-122">The [DateTime](xref:System.DateTime) structure is suitable for applications that do the following:</span></span> 

* <span data-ttu-id="35dde-123">日付のみを使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="35dde-123">Work with dates only.</span></span>

* <span data-ttu-id="35dde-124">時刻のみを使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="35dde-124">Work with times only.</span></span>

* <span data-ttu-id="35dde-125">抽象日時を使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="35dde-125">Work with abstract dates and times.</span></span>

* <span data-ttu-id="35dde-126">タイム ゾーン情報がない日時を使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="35dde-126">Work with dates and times for which time zone information is missing.</span></span> 

* <span data-ttu-id="35dde-127">UTC 日時のみを使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="35dde-127">Work with UTC dates and times only.</span></span> 

* <span data-ttu-id="35dde-128">SQL データベースなど、.NET Framework の外部ソースから日時情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="35dde-128">Retrieve date and time information from sources outside the .NET Framework, such as SQL databases.</span></span> <span data-ttu-id="35dde-129">通常、これらのソースは、[DateTime](xref:System.DateTime) 構造体と互換性のある単純な形式で日時情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="35dde-129">Typically, these sources store date and time information in a simple format that is compatible with the [DateTime](xref:System.DateTime) structure.</span></span>

* <span data-ttu-id="35dde-130">日付と時刻の演算を実行しますが、これは一般的な結果に関するものです。</span><span class="sxs-lookup"><span data-stu-id="35dde-130">Perform date and time arithmetic, but are concerned with general results.</span></span> <span data-ttu-id="35dde-131">たとえば、6 カ月を特定の日付と時刻に加算する加算演算では、多くの場合、結果を夏時間に合わせて調整するかどうかは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="35dde-131">For example, in an addition operation that adds six months to a particular date and time, it is often not important whether the result is adjusted for daylight saving time.</span></span>

<span data-ttu-id="35dde-132">特定の [DateTime](xref:System.DateTime) 値が UTC を表さない場合、通常、その日付と時刻の値は、あいまいであるか、その移植性に限定されます。</span><span class="sxs-lookup"><span data-stu-id="35dde-132">Unless a particular [DateTime](xref:System.DateTime) value represents UTC, that date and time value is often ambiguous or limited in its portability.</span></span> <span data-ttu-id="35dde-133">たとえば、[DateTime](xref:System.DateTime) 値が現地時刻を表す場合、そのローカル タイム ゾーン内で移植することができます (つまり、同じタイム ゾーンにある別のシステムで値が逆シリアル化されると、その値は明確に単一時点を識別します)。</span><span class="sxs-lookup"><span data-stu-id="35dde-133">For example, if a [DateTime](xref:System.DateTime) value represents the local time, it is portable within that local time zone (that is, if the value is deserialized on another system in the same time zone, that value still unambiguously identifies a single point in time).</span></span> <span data-ttu-id="35dde-134">ローカル タイム ゾーン外では、その [DateTime](xref:System.DateTime) 値は複数の意味を持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="35dde-134">Outside the local time zone, that [DateTime](xref:System.DateTime) value can have multiple interpretations.</span></span> <span data-ttu-id="35dde-135">値の [Kind](xref:System.DateTime.Kind) プロパティが [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified) の場合、移植性は低くなります。同じタイム ゾーン内であいまいになり、最初にシリアル化したのと同じシステムにおいてさえもあいまいになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35dde-135">If the value's [Kind](xref:System.DateTime.Kind) property is [DateTimeKind.Unspecified](xref:System.DateTimeKind.Unspecified), it is even less portable: it is now ambiguous within the same time zone and possibly even on the same system on which it was first serialized.</span></span> <span data-ttu-id="35dde-136">[DateTime](xref:System.DateTime) 値が UTC を表す場合のみ、値が使用されるシステムまたはタイム ゾーンに関係なく、その値は明確に単一時点を識別します。</span><span class="sxs-lookup"><span data-stu-id="35dde-136">Only if a [DateTime](xref:System.DateTime) value represents UTC does that value unambiguously identify a single point in time regardless of the system or time zone in which the value is used.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35dde-137">[DateTime](xref:System.DateTime) データを保存または共有する際、UTC を使用する必要があり、[DateTime](xref:System.DateTime) 値の [Kind](xref:System.DateTime.Kind) プロパティを [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35dde-137">When saving or sharing [DateTime](xref:System.DateTime) data, UTC should be used and the [DateTime](xref:System.DateTime) value's [Kind](xref:System.DateTime.Kind) property should be set to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="the-datetimeoffset-structure"></a><span data-ttu-id="35dde-138">DateTimeOffset 構造体</span><span class="sxs-lookup"><span data-stu-id="35dde-138">The DateTimeOffset structure</span></span>

<span data-ttu-id="35dde-139">[System.DateTimeOffset](xref:System.DateTimeOffset) 構造体は、日付と時刻の値、およびその値と UTC との差異を示すオフセットを表します。</span><span class="sxs-lookup"><span data-stu-id="35dde-139">The [System.DateTimeOffset](xref:System.DateTimeOffset) structure represents a date and time value, together with an offset that indicates how much that value differs from UTC.</span></span> <span data-ttu-id="35dde-140">そのため、値は常に明確に単一時点を識別します。</span><span class="sxs-lookup"><span data-stu-id="35dde-140">Thus, the value always unambiguously identifies a single point in time.</span></span> 

<span data-ttu-id="35dde-141">[DateTimeOffset](xref:System.DateTimeOffset) 型には、[DateTime](xref:System.DateTime) 型のすべての機能に加え、タイム ゾーンの処理機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="35dde-141">The [DateTimeOffset](xref:System.DateTimeOffset) type includes all of the functionality of the [DateTime](xref:System.DateTime) type along with time zone awareness.</span></span> <span data-ttu-id="35dde-142">そのため、次の操作を実行するアプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="35dde-142">This makes it is suitable for applications that do the following:</span></span> 

* <span data-ttu-id="35dde-143">単一の時点を一意かつ明確に識別する。</span><span class="sxs-lookup"><span data-stu-id="35dde-143">Uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="35dde-144">[DateTimeOffset](xref:System.DateTimeOffset) 型を使用して、「現在」の意味を明確に定義し、トランザクションの時刻を記録し、システム イベントまたはアプリケーション イベントの時刻を記録し、ファイル作成時刻とファイル変更時刻を記録することができます。</span><span class="sxs-lookup"><span data-stu-id="35dde-144">The [DateTimeOffset](xref:System.DateTimeOffset) type can be used to unambiguously define the meaning of "now", to log transaction times, to log the times of system or application events, and to record file creation and modification times.</span></span> 

* <span data-ttu-id="35dde-145">一般的な日付と時刻の演算を実行する。</span><span class="sxs-lookup"><span data-stu-id="35dde-145">Perform general date and time arithmetic.</span></span>

* <span data-ttu-id="35dde-146">その時刻が&2; つの別々の値または構造体の&2; つのメンバーである場合、関連する複数の時刻を保持する。</span><span class="sxs-lookup"><span data-stu-id="35dde-146">Preserve multiple related times, as long as those times are stored as two separate values or as two members of a structure.</span></span>

> [!NOTE]
> <span data-ttu-id="35dde-147">[DateTimeOffset](xref:System.DateTimeOffset) 値のこの用途は、[DateTime](xref:System.DateTime) 値の用途と比べてはるかに一般的です。</span><span class="sxs-lookup"><span data-stu-id="35dde-147">These uses for [DateTimeOffset](xref:System.DateTimeOffset) values are much more common than those for [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="35dde-148">その結果、[DateTimeOffset](xref:System.DateTimeOffset) はアプリケーション開発の既定の日付時刻型と見なされます。</span><span class="sxs-lookup"><span data-stu-id="35dde-148">As a result, [DateTimeOffset](xref:System.DateTimeOffset) should be considered the default date and time type for application development.</span></span>

<span data-ttu-id="35dde-149">[DateTimeOffset](xref:System.DateTimeOffset) 値は特定のタイム ゾーンと関連付けられていませんが、さまざまなタイム ゾーンから派生することができます。</span><span class="sxs-lookup"><span data-stu-id="35dde-149">A [DateTimeOffset](xref:System.DateTimeOffset) value is not tied to a particular time zone, but can originate from any of a variety of time zones.</span></span> <span data-ttu-id="35dde-150">これを説明するために、いくつかの [DateTimeOffset](xref:System.DateTimeOffset) 値 (ローカルの太平洋標準時を含む) が属することができるタイム ゾーンの一覧を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="35dde-150">To illustrate this, the following example lists the time zones to which a number of [DateTimeOffset](xref:System.DateTimeOffset) values (including a local Pacific Standard Time) can belong.</span></span>

```csharp
using System;
using System.Collections.ObjectModel;

public class TimeOffsets
{
   public static void Main()
   {
      DateTime thisDate = new DateTime(2007, 3, 10, 0, 0, 0);
      DateTime dstDate = new DateTime(2007, 6, 10, 0, 0, 0);
      DateTimeOffset thisTime;

      thisTime = new DateTimeOffset(dstDate, new TimeSpan(-7, 0, 0));
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(-6, 0, 0));  
      ShowPossibleTimeZones(thisTime);

      thisTime = new DateTimeOffset(thisDate, new TimeSpan(+1, 0, 0));
      ShowPossibleTimeZones(thisTime);
   }

   private static void ShowPossibleTimeZones(DateTimeOffset offsetTime)
   {
      TimeSpan offset = offsetTime.Offset;
      ReadOnlyCollection<TimeZoneInfo> timeZones;

      Console.WriteLine("{0} could belong to the following time zones:", 
                        offsetTime.ToString());
      // Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones();     
      // Iterate time zones 
      foreach (TimeZoneInfo timeZone in timeZones)
      {
         // Compare offset with offset for that date in that time zone
         if (timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset))
            Console.WriteLine("   {0}", timeZone.DisplayName);
      }
      Console.WriteLine();
   } 
}
// This example displays the following output to the console:
//       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
//          (GMT-07:00) Arizona
//          (GMT-08:00) Pacific Time (US & Canada)
//          (GMT-08:00) Tijuana, Baja California
//       
//       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
//          (GMT-06:00) Central America
//          (GMT-06:00) Central Time (US & Canada)
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
//          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
//          (GMT-06:00) Saskatchewan
//       
//       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
//          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
//          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
//          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
//          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
//          (GMT+01:00) West Central Africa
```

```vb
Imports System.Collections.ObjectModel

Module TimeOffsets
   Public Sub Main()
      Dim thisTime As DateTimeOffset 

      thisTime = New DateTimeOffset(#06/10/2007#, New TimeSpan(-7, 0, 0))
      ShowPossibleTimeZones(thisTime) 

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(-6, 0, 0))  
      ShowPossibleTimeZones(thisTime)

      thisTime = New DateTimeOffset(#03/10/2007#, New TimeSpan(+1, 0, 0))
      ShowPossibleTimeZones(thisTime)
   End Sub

   Private Sub ShowPossibleTimeZones(offsetTime As DateTimeOffset)
      Dim offset As TimeSpan = offsetTime.Offset
      Dim timeZones As ReadOnlyCollection(Of TimeZoneInfo)

      Console.WriteLine("{0} could belong to the following time zones:", _
                        offsetTime.ToString())
      ' Get all time zones defined on local system
      timeZones = TimeZoneInfo.GetSystemTimeZones()     
      ' Iterate time zones
      For Each timeZone As TimeZoneInfo In timeZones
         ' Compare offset with offset for that date in that time zone
         If timeZone.GetUtcOffset(offsetTime.DateTime).Equals(offset) Then
            Console.WriteLine("   {0}", timeZone.DisplayName)
         End If   
      Next
      Console.WriteLine()
   End Sub
End Module
' This example displays the following output to the console:
'       6/10/2007 12:00:00 AM -07:00 could belong to the following time zones:
'          (GMT-07:00) Arizona
'          (GMT-08:00) Pacific Time (US & Canada)
'          (GMT-08:00) Tijuana, Baja California
'       
'       3/10/2007 12:00:00 AM -06:00 could belong to the following time zones:
'          (GMT-06:00) Central America
'          (GMT-06:00) Central Time (US & Canada)
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - New
'          (GMT-06:00) Guadalajara, Mexico City, Monterrey - Old
'          (GMT-06:00) Saskatchewan
'       
'       3/10/2007 12:00:00 AM +01:00 could belong to the following time zones:
'          (GMT+01:00) Amsterdam, Berlin, Bern, Rome, Stockholm, Vienna
'          (GMT+01:00) Belgrade, Bratislava, Budapest, Ljubljana, Prague
'          (GMT+01:00) Brussels, Copenhagen, Madrid, Paris
'          (GMT+01:00) Sarajevo, Skopje, Warsaw, Zagreb
'          (GMT+01:00) West Central Africa
```

<span data-ttu-id="35dde-151">この例の日付と時刻の値はそれぞれ少なくとも&3; つの異なるタイム ゾーンに属することができることを出力は示しています。</span><span class="sxs-lookup"><span data-stu-id="35dde-151">The output shows that each date and time value in this example can belong to at least three different time zones.</span></span> <span data-ttu-id="35dde-152">[DateTimeOffset](xref:System.DateTimeOffset) 値の 6/10/2007 は、日付と時刻の値が夏時間を表す場合、UTC のそのオフセットは必ずしも元のタイム ゾーンの基本 UTC オフセット、またはその表示名から見つかる UTC のオフセットと一致しないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="35dde-152">The [DateTimeOffset](xref:System.DateTimeOffset) value of 6/10/2007 shows that if a date and time value represents a daylight saving time, its offset from UTC does not even necessarily correspond to the originating time zone's base UTC offset or to the offset from UTC found in its display name.</span></span> <span data-ttu-id="35dde-153">これは、単一の [DateTimeOffset](xref:System.DateTimeOffset) 値はそのタイム ゾーンと密接に関連していないために夏時間との間のタイム ゾーンの遷移を反映することができないことを意味しています。</span><span class="sxs-lookup"><span data-stu-id="35dde-153">This means that, because a single [DateTimeOffset](xref:System.DateTimeOffset)  value is not tightly coupled with its time zone, it cannot reflect a time zone's transition to and from daylight saving time.</span></span> <span data-ttu-id="35dde-154">これは特に、日付と時刻の演算を使用して [DateTimeOffset](xref:System.DateTimeOffset) 値を操作する際に問題となる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35dde-154">This can be particularly problematic when date and time arithmetic is used to manipulate a [DateTimeOffset](xref:System.DateTimeOffset) value.</span></span> <span data-ttu-id="35dde-155">タイム ゾーンの調整規則を考慮に入れた日付と時刻の演算を実行する方法については、「[日付と時刻を使用した算術演算の実行](performing-arithmetic-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35dde-155">For a discussion of how to perform date and time arithmetic in a way that takes account of a time zone's adjustment rules, see [Performing arithmetic operations with dates and times](performing-arithmetic-operations.md).</span></span>

## <a name="the-timespan-structure"></a><span data-ttu-id="35dde-156">TimeSpan 構造体</span><span class="sxs-lookup"><span data-stu-id="35dde-156">The TimeSpan structure</span></span>

<span data-ttu-id="35dde-157">[System.TimeSpan](xref:System.TimeSpan) 構造体は、時間間隔を表します。</span><span class="sxs-lookup"><span data-stu-id="35dde-157">The [System.TimeSpan](xref:System.TimeSpan) structure represents a time interval.</span></span> <span data-ttu-id="35dde-158">その&2; つの一般的な用途は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="35dde-158">Its two typical uses are:</span></span> 

* <span data-ttu-id="35dde-159">2 つの日付と時刻の値の間の時間を反映する。</span><span class="sxs-lookup"><span data-stu-id="35dde-159">Reflecting the time interval between two date and time values.</span></span> <span data-ttu-id="35dde-160">たとえば、ある値から [DateTime](xref:System.DateTime) 値を減算すると、[TimeSpan](xref:System.TimeSpan) 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="35dde-160">For example, subtracting one [DateTime](xref:System.DateTime) value from another returns a [TimeSpan](xref:System.TimeSpan) value.</span></span> 

* <span data-ttu-id="35dde-161">経過時間を測定する。</span><span class="sxs-lookup"><span data-stu-id="35dde-161">Measuring elapsed time.</span></span> <span data-ttu-id="35dde-162">たとえば、[Stopwatch.Elapsed](xref:System.Diagnostics.Stopwatch.Elapsed) プロパティは、経過時間の測定を開始する [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch) メソッドの&1; つを呼び出してから経過した時間間隔を反映する [TimeSpan](xref:System.TimeSpan) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="35dde-162">For example, the [Stopwatch.Elapsed](xref:System.Diagnostics.Stopwatch.Elapsed) property returns a [TimeSpan](xref:System.TimeSpan) value that reflects the time interval that has elapsed since the call to one of the [System.Diagnostics.Stopwatch](xref:System.Diagnostics.Stopwatch) methods that begins to measure elapsed time.</span></span>

<span data-ttu-id="35dde-163">値が特定時刻への参照がない値が時間を反映する際、[DateTime](xref:System.DateTime) 値の代わりに [TimeSpan](xref:System.TimeSpan) 値を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="35dde-163">A [TimeSpan](xref:System.TimeSpan) value can also be used as a replacement for a [DateTime](xref:System.DateTime) value when that value reflects a time without reference to a particular time of day.</span></span> <span data-ttu-id="35dde-164">この用途は [DateTime.TimeOfDay](xref:System.DateTime.TimeOfDay) および [DateTimeOffset.TimeOfDay](xref:System.DateTimeOffset.TimeOfDay) プロパティと似ています。これらのプロパティは、日付への参照なしの時間を表す [TimeSpan](xref:System.TimeSpan) 値を返します。</span><span class="sxs-lookup"><span data-stu-id="35dde-164">This usage is similar to the [DateTime.TimeOfDay](xref:System.DateTime.TimeOfDay) and [DateTimeOffset.TimeOfDay](xref:System.DateTimeOffset.TimeOfDay) properties, which return a [TimeSpan](xref:System.TimeSpan) value that represents the time without reference to a date.</span></span> <span data-ttu-id="35dde-165">たとえば、[TimeSpan](xref:System.TimeSpan) 構造体を使用して、ストアの開店時刻または閉店時刻を反映したり、標準イベントが発生したときの時刻を表したりするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="35dde-165">For example, the [TimeSpan](xref:System.TimeSpan) structure can be used to reflect a store's daily opening or closing time, or it can be used to represent the time at which any regular event occurs.</span></span>

<span data-ttu-id="35dde-166">以下の例では、開店時刻と閉店時刻用の [TimeSpan](xref:System.TimeSpan) オブジェクト、およびストアのタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを含む `StoreInfo` 構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="35dde-166">The following example defines a `StoreInfo` structure that includes [TimeSpan](xref:System.TimeSpan) objects for store opening and closing times, as well as a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the store's time zone.</span></span> <span data-ttu-id="35dde-167">構造体には、`IsOpenNow`、`IsOpenAt` という&2; つのメソッドも含まれます。これは、ローカル タイム ゾーンにいると想定されるユーザーによって指定された時刻にストアがオープンするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="35dde-167">The structure also includes two methods, `IsOpenNow` and `IsOpenAt`, that indicates whether the store is open at a time specified by the user, who is assumed to be in the local time zone.</span></span>  

```csharp
using System;

public struct StoreInfo
{
   public String store;
   public TimeZoneInfo tz;
   public TimeSpan open;
   public TimeSpan close;

   public bool IsOpenNow()
   {
      return IsOpenAt(DateTime.TimeOfDay);
   }

   public bool IsOpenAt(TimeSpan time)
   {
      TimeZoneInfo local = TimeZoneInfo.Local;
      TimeSpan offset = TimeZoneInfo.BaseUtcOffset;

      // Is the store in the same time zone?
      if (tz.Equals(local)) {
         return time >= open & time <= close;
      }
   }
}
```

```vb
Public Structure StoreInfo
   Dim store As String
   Dim tz As TimeZoneInfo
   Dim open As TimeSpan
   Dim close As TimeSpan

   Public Function IsOpenNow() As Boolean
      Return IsOpenAt(Date.Now.TimeOfDay)
   End Function

   Public Function IsOpenAt(time As TimeSpan) As Boolean
      Dim local As TimeZoneInfo = TimeZoneInfo.Local
      Dim offset As TimeSpan = TimeZoneInfo.Local.BaseUtcOffset

      ' Is the store in the same time zone?
      If tz.Equals(local) Then
         Return time >= open And time <= close
      Else
         Dim delta As TimeSpan = TimeSpan.Zero
         Dim storeDelta As TimeSpan = TimeSpan.Zero

         ' Is it daylight saving time in either time zone?
         If local.IsDaylightSavingTime(Date.Now.Date + time) Then
            delta = local.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         If tz.IsDaylightSavingTime(TimeZoneInfo.ConvertTime(Date.Now.Date + time, local, tz))
            storeDelta = tz.GetAdjustmentRules(local.GetAdjustmentRules().Length - 1).DaylightDelta
         End If
         Dim comparisonTime As TimeSpan = time + (offset - tz.BaseUtcOffset).Negate() + (delta - storeDelta).Negate
         Return (comparisonTime >= open And comparisonTime <= close)
      End If
   End Function
End Structure
```

<span data-ttu-id="35dde-168">`StoreInfo` 構造体をクライアント コードで次のように使用できます。</span><span class="sxs-lookup"><span data-stu-id="35dde-168">The `StoreInfo` structure can then be used by client code like the following.</span></span> 

```csharp
public class Example
{
   public static void Main()
   {
      // Instantiate a StoreInfo object.
      var store103 = new StoreInfo();
      store103.store = "Store #103";
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
      // Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0);
      // Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0);

      Console.WriteLine("Store is open now at {0}: {1}",
                        DateTime.TimeOfDay, store103.IsOpenNow());
      TimeSpan[] times = { new TimeSpan(8, 0, 0), new TimeSpan(21, 0, 0),
                           new TimeSpan(4, 59, 0), new TimeSpan(18, 31, 0) };
      foreach (var time in times)
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time));
   }
}
// The example displays the following output:
//       Store is open now at 15:29:01.6129911: True
//       Store is open at 08:00:00: True
//       Store is open at 21:00:00: False
//       Store is open at 04:59:00: False
//       Store is open at 18:31:00: False
```

```vb
Module Example
   Public Sub Main()
      ' Instantiate a StoreInfo object.
      Dim store103 As New StoreInfo()
      store103.store = "Store #103"
      store103.tz = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
      ' Store opens at 8:00.
      store103.open = new TimeSpan(8, 0, 0)
      ' Store closes at 9:30.
      store103.close = new TimeSpan(21, 30, 0)

      Console.WriteLine("Store is open now at {0}: {1}",
                        Date.Now.TimeOfDay, store103.IsOpenNow())
      Dim times() As TimeSpan = { New TimeSpan(8, 0, 0),
                                  New TimeSpan(21, 0, 0),
                                  New TimeSpan(4, 59, 0),
                                  New TimeSpan(18, 31, 0) }
      For Each time In times
         Console.WriteLine("Store is open at {0}: {1}",
                           time, store103.IsOpenAt(time))
      Next
   End Sub
End Module
' The example displays the following output:
'       Store is open now at 15:29:01.6129911: True
'       Store is open at 08:00:00: True
'       Store is open at 21:00:00: False
'       Store is open at 04:59:00: False
'       Store is open at 18:31:00: False
```

## <a name="the-timezoneinfo-class"></a><span data-ttu-id="35dde-169">TimeZoneInfo クラス</span><span class="sxs-lookup"><span data-stu-id="35dde-169">The TimeZoneInfo class</span></span>

<span data-ttu-id="35dde-170">[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスは地球のタイム ゾーンを表し、1 つのタイム ゾーンの日付と時刻の値を、別のタイム ゾーンの日付と時刻の値に変換できるようにします。</span><span class="sxs-lookup"><span data-stu-id="35dde-170">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class represents any of the earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone.</span></span> <span data-ttu-id="35dde-171">[TimeZoneInfo](xref:System.TimeZoneInfo) クラスにより、日付と時刻を使用して、どの日付と時刻の値も明確に単一時点を識別できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="35dde-171">The [TimeZoneInfo](xref:System.TimeZoneInfo) class makes it possible to work with dates and times so that any date and time value unambiguously identifies a single point in time.</span></span>

<span data-ttu-id="35dde-172">場合によっては、[TimeZoneInfo](xref:System.TimeZoneInfo) クラスをフル活用するために、開発作業をさらに実行する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="35dde-172">In some cases, taking full advantage of the [TimeZoneInfo](xref:System.TimeZoneInfo) class may require further development work.</span></span> <span data-ttu-id="35dde-173">日付と時刻の値は、それが属するタイム ゾーンに密接に関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="35dde-173">Date and time values are not tightly coupled with the time zones to which they belong.</span></span> <span data-ttu-id="35dde-174">結果として、アプリケーションが日付と時刻をその関連タイム ゾーンとリンクするメカニズムを提供していない場合、特定の日付と時刻の値とそのタイム ゾーンの関連付けは簡単に解除されます。</span><span class="sxs-lookup"><span data-stu-id="35dde-174">As a result, unless your application provides some mechanism for linking a date and time with its associated time zone, it is easy for a particular date and time value to become disassociated from its time zone.</span></span> <span data-ttu-id="35dde-175">この情報をリンクする&1; つの方法は、日付と時刻の値とその関連タイム ゾーン オブジェクトの両方を含むクラスまたは構造体を定義するという方法です。</span><span class="sxs-lookup"><span data-stu-id="35dde-175">One method of linking this information is to define a class or structure that contains both the date and time value and its associated time zone object.</span></span>

<span data-ttu-id="35dde-176">日付と時刻のオブジェクトをインスタンスするときにその日付と時刻の値が属するタイム ゾーンがわかっている場合のみ、.NET でタイム ゾーンのサポートを利用できます。</span><span class="sxs-lookup"><span data-stu-id="35dde-176">Taking advantage of time zone support in .NET is possible only if the time zone to which a date and time value belongs is known when that date and time object is instantiated.</span></span> <span data-ttu-id="35dde-177">特に Web またはネットワーク アプリケーションでは、これは該当しません。</span><span class="sxs-lookup"><span data-stu-id="35dde-177">This is often not the case, particularly in Web or network applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="35dde-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="35dde-178">See Also</span></span>

[<span data-ttu-id="35dde-179">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="35dde-179">Dates, times, and time zones</span></span>](index.md)
