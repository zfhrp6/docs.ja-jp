---
title: "日付と時刻を使用した算術演算の実行"
description: "日付と時刻を使用した算術演算の実行"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 589ac5ec-8365-4a0d-bc38-72183718110c
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: b872cc4c2b799ddafc9df263795d860754d1ec17
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="performing-arithmetic-operations-with-dates-and-times"></a><span data-ttu-id="dbe5f-104">日付と時刻を使用した算術演算の実行</span><span class="sxs-lookup"><span data-stu-id="dbe5f-104">Performing arithmetic operations with dates and times</span></span>

<span data-ttu-id="dbe5f-105">[System.DateTime](xref:System.DateTime) 構造体と [System.DateTimeOffset](xref:System.DateTimeOffset) 構造体には、その値に対して算術演算を実行するメンバーが用意されていますが、算術演算の結果は大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-105">Although both the [System.DateTime](xref:System.DateTime) and the [System.DateTimeOffset](xref:System.DateTimeOffset) structures provide members that perform arithmetic operations on their values, the results of arithmetic operations are very different.</span></span> <span data-ttu-id="dbe5f-106">この記事では、それらの相違点を検討し、日付と時刻のデータがどの程度タイム ゾーンに対応しているかを明らかにして、日付と時刻のデータを使用してタイム ゾーンに完全に対応した操作を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-106">This article examines those differences, relates them to degrees of time zone awareness in date and time data, and discusses how to perform fully time zone aware operations using date and time data.</span></span>

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a><span data-ttu-id="dbe5f-107">DateTime 値を使用した比較および算術演算</span><span class="sxs-lookup"><span data-stu-id="dbe5f-107">Comparisons and Arithmetic Operations with DateTime Values</span></span>

<span data-ttu-id="dbe5f-108">[System.DateTime](xref:System.DateTime) 値は、制限付きでタイム ゾーンに対応しています。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-108">[System.DateTime](xref:System.DateTime) values possess a limited degree of time zone awareness.</span></span> <span data-ttu-id="dbe5f-109">[DateTime.Kind](xref:System.DateTime.Kind) プロパティでは、[System.DateTimeKind](xref:System.DateTimeKind) 値を日付と時刻に割り当てて、その日付と時刻が現地時刻、世界協定時刻 (UTC)、またはタイム ゾーンが指定されていない時刻のどれを表すかを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-109">The [DateTime.Kind](xref:System.DateTime.Kind) property allows a [System.DateTimeKind](xref:System.DateTimeKind) value to be assigned to the date and time to indicate whether it represents local time, Coordinated Universal Time (UTC), or the time in an unspecified time zone.</span></span> <span data-ttu-id="dbe5f-110">ただし、この制限付きのタイム ゾーン情報は、[DateTime](xref:System.DateTime) 値に対して比較操作を行うか、日付と時刻の算術演算を実行するときには無視されます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-110">However, this limited time zone information is ignored when comparing or performing date and time arithmetic on [DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="dbe5f-111">次の例では、現在の現地時刻と現在の UTC 時刻を比較することで、この問題を示しています。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-111">The following example, which compares the current local time with the current UTC time, illustrates this.</span></span>

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateManipulation
{
   public static void Main()
   {
      DateTime localTime = DateTime.Now;
      DateTime utcTime = DateTime.UtcNow;

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", 
                        localTime.Kind.ToString(), 
                        utcTime.Kind.ToString(), 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The {0} time is {1} the {2} time.", 
                        localTime.Kind.ToString(), 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)), 
                        utcTime.Kind.ToString());  
   }
}
// If run in the U.S. Pacific Standard Time zone, the example displays 
// the following output to the console:
//    Difference between Local and Utc time: -7:0 hours
//    The Local time is EarlierThan the Utc time.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateManipulation
   Public Sub Main()
      Dim localTime As Date = Date.Now
      Dim utcTime As Date = Date.UtcNow

      Console.WriteLine("Difference between {0} and {1} time: {2}:{3} hours", _
                        localTime.Kind.ToString(), _
                        utcTime.Kind.ToString(), _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The {0} time is {1} the {2} time.", _
                        localTime.Kind.ToString(), _ 
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)), _
                        utcTime.Kind.ToString())  
      ' If run in the U.S. Pacific Standard Time zone, the example displays 
      ' the following output to the console:
      '    Difference between Local and Utc time: -7:0 hours
      '    The Local time is EarlierThan the Utc time.                                                    
   End Sub
End Module
```

<span data-ttu-id="dbe5f-112">[DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) メソッドは、現地時刻が UTC 時刻より早い (より小さい) という結果を出力しており、減算の操作は、UTC と米国の太平洋標準時ゾーンにあるシステムの現地時刻との差が7 時間であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-112">The [DateTime.CompareTo(DateTime, DateTime)](xref:System.DateTime.Compare(System.DateTime,System.DateTime)) method reports that the local time is earlier than (or less than) the UTC time, and the subtraction operation indicates that the difference between UTC and the local time for a system in the U.S. Pacific Standard Time zone is seven hours.</span></span> <span data-ttu-id="dbe5f-113">しかし、これら&2; つの値は、ある特定の時点を異なる表現で示したものであるため、この場合、時間差の原因は、UTC を基準としたローカル タイム ゾーンのオフセットにあることは明らかです。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-113">But because these two values provide different representations of a single point in time, it is clear in this case that this time interval is completely attributable to the local time zone's offset from UTC.</span></span> 

<span data-ttu-id="dbe5f-114">一般的に、[DateTimeKind](xref:System.DateTimeKind) プロパティは、[DateTime](xref:System.DateTime) の比較および算術メソッドによって返される結果に影響を与えません (2 つの同じ時点の比較結果が示すとおり)。ただし、その結果の解釈には影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-114">More generally, the [DateTimeKind](xref:System.DateTimeKind) property does not affect the results returned by [DateTime](xref:System.DateTime) comparison and arithmetic methods (as the comparison of two identical points in time indicates), although it can affect the interpretation of those results.</span></span> <span data-ttu-id="dbe5f-115">例:</span><span class="sxs-lookup"><span data-stu-id="dbe5f-115">For example:</span></span>

* <span data-ttu-id="dbe5f-116">算術演算の実行対象となる&2; つの日付と時刻の値の [DateTimeKind](xref:System.DateTimeKind) プロパティが両方とも [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) である場合、実行結果には、2 つの値の実際の時間差が反映されます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-116">The result of any arithmetic operation performed on two date and time values whose [DateTimeKind](xref:System.DateTimeKind) properties both equal [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) reflects the actual time interval between the two values.</span></span> <span data-ttu-id="dbe5f-117">同様に、そのような&2; つの日付と時刻の値を比較した結果には、2 つの時間の関係が正確に反映されます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-117">Similarly, the comparison of two such date and time values accurately reflects the relationship between times.</span></span>

* <span data-ttu-id="dbe5f-118">算術演算または比較操作の実行対象となる&2; つの日付と時刻の値の [DateTimeKind](xref:System.DateTimeKind) プロパティが両方とも [DateTimeKind.Local](xref:System.DateTimeKind.Local) であるか、または&2; つの日付と時刻の値の [DateTimeKind](xref:System.DateTimeKind) プロパティ値が異なる場合、実行結果には、2 つの値の間の時刻差が反映されます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-118">The result of any arithmetic or comparison operation performed on two date and time values whose [DateTimeKind](xref:System.DateTimeKind) properties both equal [DateTimeKind.Local](xref:System.DateTimeKind.Local) or on two date and time values with different [DateTimeKind](xref:System.DateTimeKind) property values reflects the difference in clock time between the two values.</span></span> 

* <span data-ttu-id="dbe5f-119">ローカルの日付と時刻の値に対する算術演算または比較操作では、特定の値があいまいであるかや、無効であるかどうかは考慮されず、ローカル タイム ゾーンでの夏時間の開始や終了による調整規則の影響についても考慮されません。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-119">Arithmetic or comparison operations on local date and time values do not consider whether a particular value is ambiguous or invalid, nor do they take account of the effect of any adjustment rules that result from the local time zone's transition to or from daylight saving time.</span></span>

* <span data-ttu-id="dbe5f-120">UTC と現地時刻の差を比較または計算する操作の結果には、UTC を基準としたローカル タイム ゾーンのオフセットに等しい時間差が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-120">Any operation that compares or calculates the difference between UTC and a local time includes a time interval equal to the local time zone's offset from UTC in the result.</span></span> 

* <span data-ttu-id="dbe5f-121">タイム ゾーンが指定されていない時刻と UTC または現地時刻との差を比較または計算する操作では、単純な時刻差が反映されます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-121">Any operation that compares or calculates the difference between an unspecified time and either UTC or the local time reflects simple clock time.</span></span> <span data-ttu-id="dbe5f-122">タイム ゾーンの違いは考慮されず、結果にはタイム ゾーン調整規則の適用が反映されません。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-122">Time zone differences are not considered, and the result does not reflect the application of time zone adjustment rules.</span></span> 

* <span data-ttu-id="dbe5f-123">タイム ゾーンが指定されていない&2; つの時刻の差を比較または計算する操作の結果には、2 つの異なるタイム ゾーンの時刻の差を反映した未知の時間差が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-123">Any operation that compares or calculates the difference between two unspecified times may include an unknown interval that reflects the difference between the time in two different time zones.</span></span>

<span data-ttu-id="dbe5f-124">多くの場合、タイム ゾーンの違いは日付と時刻の計算には影響しないか、または日付と時刻のデータのコンテキストによって比較操作や算術演算の意味が規定されます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-124">There are many scenarios in which time zone differences do not affect date and time calculations or in which the context of the date and time data defines the meaning of comparison or arithmetic operations.</span></span> <span data-ttu-id="dbe5f-125">これらの詳細については、「[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](choosing-between-datetime.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-125">For a discussion of some of these, see [Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](choosing-between-datetime.md).</span></span>

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a><span data-ttu-id="dbe5f-126">DateTimeOffset 値を使用した比較および算術演算</span><span class="sxs-lookup"><span data-stu-id="dbe5f-126">Comparisons and Arithmetic Operations with DateTimeOffset Values</span></span>

<span data-ttu-id="dbe5f-127">[System.DateTimeOffset](xref:System.DateTimeOffset) 値には、日付と時刻だけでなく、UTC を基準としてその日付と時刻を明確に定義するオフセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-127">A [System.DateTimeOffset](xref:System.DateTimeOffset) value includes not only a date and time, but also an offset that unambiguously defines that date and time relative to UTC.</span></span> <span data-ttu-id="dbe5f-128">このため、[System.DateTime](xref:System.DateTime) 値とはいくらか異なる等価性を規定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-128">This makes it possible to define equality somewhat differently than for [System.DateTime](xref:System.DateTime) values.</span></span> <span data-ttu-id="dbe5f-129">[DateTime](xref:System.DateTime) 値が等しくなるのは日付と時刻の値が同じ場合ですが、[DateTimeOffset](xref:System.DateTimeOffset) 値が等しくなるのは、両方の値が同じ時点を表す場合です。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-129">Whereas [DateTime](xref:System.DateTime) values are equal if they have the same date and time value, [DateTimeOffset](xref:System.DateTimeOffset) values are equal if they both refer to the same point in time.</span></span> <span data-ttu-id="dbe5f-130">これにより、2 つの日付と時刻の間隔を決定する比較操作やほとんどの算術演算では、[DateTimeOffset](xref:System.DateTimeOffset) 値を使用すると、より正確な結果を得ることができ、結果を正しく解釈する手間を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-130">This makes a [DateTimeOffset](xref:System.DateTimeOffset) value more accurate and less in need of interpretation when used in comparisons and in most arithmetic operations that determine the interval between two dates and times.</span></span> <span data-ttu-id="dbe5f-131">次の例では、現地時刻と UTC の DateTime 値を比較した前の例に [DateTimeOffset](xref:System.DateTimeOffset) を使用して、動作の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-131">The following example, which is the [DateTimeOffset](xref:System.DateTimeOffset) equivalent to the previous example that compared local and UTC DateTime values, illustrates this difference in behavior.</span></span>

```csharp
using System;

public enum TimeComparison
{
   EarlierThan = -1,
   TheSameAs = 0,
   LaterThan = 1
}

public class DateTimeOffsetManipulation
{
   public static void Main()
   {
      DateTimeOffset localTime = DateTimeOffset.Now;
      DateTimeOffset utcTime = DateTimeOffset.UtcNow;

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours", 
                        (localTime - utcTime).Hours, 
                        (localTime - utcTime).Minutes);
      Console.WriteLine("The local time is {0} UTC.", 
                        Enum.GetName(typeof(TimeComparison), localTime.CompareTo(utcTime)));  
   }
}
// Regardless of the local time zone, the example displays 
// the following output to the console:
//    Difference between local time and UTC: 0:00 hours.
//    The local time is TheSameAs UTC.
```

```vb
Public Enum TimeComparison As Integer
   EarlierThan = -1
   TheSameAs = 0
   LaterThan = 1
End Enum

Module DateTimeOffsetManipulation
   Public Sub Main()
      Dim localTime As DateTimeOffset = DateTimeOffset.Now
      Dim utcTime As DateTimeOffset = DateTimeOffset.UtcNow

      Console.WriteLine("Difference between local time and UTC: {0}:{1:D2} hours.", _
                        (localTime - utcTime).Hours, _
                        (localTime - utcTime).Minutes)
      Console.WriteLine("The local time is {0} UTC.", _
                        [Enum].GetName(GetType(TimeComparison), localTime.CompareTo(utcTime)))  
   End Sub
End Module
' Regardless of the local time zone, the example displays 
' the following output to the console:
'    Difference between local time and UTC: 0:00 hours.
'    The local time is TheSameAs UTC.
'          Console.WriteLine(e.GetType().Name)
```

<span data-ttu-id="dbe5f-132">この例では、[DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) メソッドが、現在の現地時刻と現在の UTC 時刻が等しいことを示しており、[DateTimeOffset](xref:System.DateTimeOffset) 値を減算することで、2 つの時刻の差が [TimeSpan.Zero](xref:System.TimeSpan.Zero) であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-132">In this example, the [DateTimeOffset.CompareTo](xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)) method indicates that the current local time and the current UTC time are equal, and subtraction of [DateTimeOffset](xref:System.DateTimeOffset) values indicates that the difference between the two times is [TimeSpan.Zero](xref:System.TimeSpan.Zero).</span></span> 

<span data-ttu-id="dbe5f-133">日付と時刻の算術演算に [DateTimeOffset](xref:System.DateTimeOffset) 値を使用する際の主な制限は、[DateTimeOffset](xref:System.DateTimeOffset) 値はタイム ゾーンに一部対応していますが、完全対応しているわけではないことです。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-133">The chief limitation of using [DateTimeOffset](xref:System.DateTimeOffset) values in date and time arithmetic is that although [DateTimeOffset](xref:System.DateTimeOffset) values have some time zone awareness, they are not fully time zone aware.</span></span> <span data-ttu-id="dbe5f-134">[DateTimeOffset](xref:System.DateTimeOffset) 値のオフセットには、[DateTimeOffset](xref:System.DateTimeOffset) 変数に最初に値が割り当てられたときに UTC を基準としたタイム ゾーンのオフセットが反映されますが、その後は、タイム ゾーンと関連付けられなくなります。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-134">Although the [DateTimeOffset](xref:System.DateTimeOffset) value's offset reflects a time zone's offset from UTC when a [DateTimeOffset](xref:System.DateTimeOffset) variable is first assigned a value, it becomes disassociated from the time zone thereafter.</span></span> <span data-ttu-id="dbe5f-135">特定可能な時刻との直接の関連付けは失われるため、日付と時刻の間隔に対して加算や減算を行っても、タイム ゾーンの調整規則は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-135">Because it is no longer directly associated with an identifiable time, the addition and subtraction of date and time intervals does not consider a time zone's adjustment rules.</span></span> 

<span data-ttu-id="dbe5f-136">たとえば、米国の中部標準時のタイム ゾーンが夏時間に移行するのは、</span><span class="sxs-lookup"><span data-stu-id="dbe5f-136">To illustrate, the transition to daylight saving time in the U.S. Central Standard Time zone occurs at 2:00 A.M.</span></span> <span data-ttu-id="dbe5f-137">2008 年 3 月 9 日の午前 2 時です。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-137">on March 9, 2008.</span></span> <span data-ttu-id="dbe5f-138">つまり、中部標準時の 2008 年 3 月 9 日の午前 1 時 30 分に</span><span class="sxs-lookup"><span data-stu-id="dbe5f-138">This means that adding a two and a half hour interval to a Central Standard time of 1:30 A.M.</span></span> <span data-ttu-id="dbe5f-139">2 時間 30 分の間隔を加算すると、日付と時刻は 2008 年 3 月 9 日の</span><span class="sxs-lookup"><span data-stu-id="dbe5f-139">on March 9, 2008, should produce a date and time of 5:00 A.M.</span></span> <span data-ttu-id="dbe5f-140">午前 5 時になります。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-140">on March 9, 2008.</span></span> <span data-ttu-id="dbe5f-141">しかし、次の例に示すように、加算の結果は 2008 年 3 月 9 日の</span><span class="sxs-lookup"><span data-stu-id="dbe5f-141">However, as the following example shows, the result of the addition is 4:00 A.M.</span></span> <span data-ttu-id="dbe5f-142">午前 4 時です。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-142">on March 9, 2008.</span></span> <span data-ttu-id="dbe5f-143">この操作の結果は正しい時点を表していますが、目的のタイム ゾーンの時刻ではありません (つまり、予想されるタイム ゾーンのオフセットが適用されていません)。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-143">Note that this result of this operation does represent the correct point in time, although it is not the time in the time zone in which we are interested (that is, it does not have the expected time zone offset).</span></span>

```csharp
using System;

public class IntervalArithmetic
{
   public static void Main()
   {
      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      const string tzName = "Central Standard Time";
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime));

         // Add two and a half hours      
         DateTimeOffset centralTime2 = centralTime1.Add(twoAndAHalfHours);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

```vb
Module IntervalArithmetic
   Public Sub Main()
      Dim generalTime As Date = #03/09/2008 1:30AM#
      Const tzName As String = "Central Standard Time"
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    TimeZoneInfo.FindSystemTimeZoneById(tzName).GetUtcOffset(generalTime))

         ' Add two and a half hours      
         Dim centralTime2 As DateTimeOffset = centralTime1.Add(twoAndAHalfHours)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 4:00:00 AM -06:00
```

## <a name="arithmetic-operations-with-times-in-time-zones"></a><span data-ttu-id="dbe5f-144">タイム ゾーンの時刻を使用した算術演算</span><span class="sxs-lookup"><span data-stu-id="dbe5f-144">Arithmetic Operations with Times in Time Zones</span></span>

<span data-ttu-id="dbe5f-145">[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスには、日付と時刻の算術演算を実行するときに調整規則を自動的に適用するメソッドは用意されていません。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-145">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class does not provide any methods that automatically apply adjustment rules when you perform date and time arithmetic.</span></span> <span data-ttu-id="dbe5f-146">ただし、あるタイム ゾーンの時刻を UTC に変換してから算術演算を実行し、その後 UTC から元のタイム ゾーンの時刻に再変換することで、調整規則を適用したときと同じ結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-146">However, you can do this by converting the time in a time zone to UTC, performing the arithmetic operation, and then converting from UTC back to the time in the time zone.</span></span> <span data-ttu-id="dbe5f-147">詳細については、「[方法 : 日付と時刻の演算でタイム ゾーンを使用する](use-time-zones-in-arithmetic.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-147">For details, see [How to: Use Time Zones in Date and Time Arithmetic](use-time-zones-in-arithmetic.md).</span></span>

<span data-ttu-id="dbe5f-148">たとえば、次のコードは、2008 年 3 月 9 日の午前 2 時に 2 時間 30 分を加算する</span><span class="sxs-lookup"><span data-stu-id="dbe5f-148">For example, the following code is similar to the previous code that added two-and-a-half hours to 2:00 A.M.</span></span> <span data-ttu-id="dbe5f-149">前のコードと似ています。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-149">on March 9, 2008.</span></span> <span data-ttu-id="dbe5f-150">ただし、中部標準時を UTC に変換した後に日付と時刻の算術演算を実行し、その結果を UTC から中部標準時に変換するため、得られた時刻は中部標準時タイム ゾーンの夏時間への移行を反映しています。</span><span class="sxs-lookup"><span data-stu-id="dbe5f-150">However, because it converts a Central Standard time to UTC before it performs date and time arithmetic, and then converts the result from UTC back to Central Standard time, the resulting time reflects the Central Standard Time Zone's transition to daylight saving time.</span></span>

```csharp
using System;

public class TimeZoneAwareArithmetic
{
   public static void Main()
   {
      const string tzName = "Central Standard Time";

      DateTime generalTime = new DateTime(2008, 3, 9, 1, 30, 0);
      TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
      TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

      // Instantiate DateTimeOffset value to have correct CST offset
      try
      {
         DateTimeOffset centralTime1 = new DateTimeOffset(generalTime, 
                                       cst.GetUtcOffset(generalTime));

         // Add two and a half hours
         DateTimeOffset utcTime = centralTime1.ToUniversalTime();
         utcTime += twoAndAHalfHours;

         DateTimeOffset centralTime2 = TimeZoneInfo.ConvertTime(utcTime, cst);
         // Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, 
                                                    twoAndAHalfHours.ToString(), 
                                                    centralTime2);  
      }
      catch (TimeZoneNotFoundException)
      {
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.");
      }
   }
}
// The example displays the following output to the console:
//    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

```vb
Module TimeZoneAwareArithmetic
   Public Sub Main()
      Const tzName As String = "Central Standard Time"

      Dim generalTime As Date = #03/09/2008 1:30AM#
      Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName) 
      Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

      ' Instantiate DateTimeOffset value to have correct CST offset
      Try
         Dim centralTime1 As New DateTimeOffset(generalTime, _
                    cst.GetUtcOffset(generalTime))

         ' Add two and a half hours 
         Dim utcTime As DateTimeOffset = centralTime1.ToUniversalTime()
         utcTime += twoAndAHalfHours

         Dim centralTime2 As DateTimeOffset = TimeZoneInfo.ConvertTime(utcTime, cst)
         ' Display result
         Console.WriteLine("{0} + {1} hours = {2}", centralTime1, _
                                                    twoAndAHalfHours.ToString(), _
                                                    centralTime2)   
      Catch e As TimeZoneNotFoundException
         Console.WriteLine("Unable to retrieve Central Standard Time zone information.")
      End Try
   End Sub
End Module
' The example displays the following output to the console:
'    3/9/2008 1:30:00 AM -06:00 + 02:30:00 hours = 3/9/2008 5:00:00 AM -05:00
```

## <a name="see-also"></a><span data-ttu-id="dbe5f-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbe5f-151">See Also</span></span>

[<span data-ttu-id="dbe5f-152">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="dbe5f-152">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="dbe5f-153">方法: 日付と時刻の演算でタイム ゾーンを使用する</span><span class="sxs-lookup"><span data-stu-id="dbe5f-153">How to: use time zones in date and time arithmetic</span></span>](use-time-zones-in-arithmetic.md)



