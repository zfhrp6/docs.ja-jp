---
title: "方法 : 日付と時刻の演算でタイム ゾーンを使用する"
description: "方法 : 日付と時刻の演算でタイム ゾーンを使用する"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 26870cdc-1709-4978-831b-ff2a2f24856f
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: a86471972d42adcbc412cc8eeb300410ca8a9c42
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="0738f-104">方法 : 日付と時刻の演算でタイム ゾーンを使用する</span><span class="sxs-lookup"><span data-stu-id="0738f-104">How to: use time zones in date and time arithmetic</span></span>

<span data-ttu-id="0738f-105">通常、[System.DateTimeOffset](xref:System.DateTimeOffset) の値を使用して日付と時刻の演算を実行するときに、結果にはタイム ゾーンの調整規則が反映されません。</span><span class="sxs-lookup"><span data-stu-id="0738f-105">Ordinarily, when you perform date and time arithmetic using [System.DateTimeOffset](xref:System.DateTimeOffset) values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="0738f-106">これは、日時の値のタイム ゾーンを明確に識別できる場合でも同じです。</span><span class="sxs-lookup"><span data-stu-id="0738f-106">This is true even when the time zone of the date and time value is clearly identifiable.</span></span> <span data-ttu-id="0738f-107">この記事では、特定のタイム ゾーンに属する日時の値の算術演算を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0738f-107">This article shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="0738f-108">算術演算の結果には、タイム ゾーンの調整規則が反映されます。</span><span class="sxs-lookup"><span data-stu-id="0738f-108">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

## <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="0738f-109">日付と時刻の演算に調整規則を適用するには</span><span class="sxs-lookup"><span data-stu-id="0738f-109">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="0738f-110">なんらかの方法を実装して、日付と時刻の値と、その値が属するタイム ゾーンを密接に結び付けます。</span><span class="sxs-lookup"><span data-stu-id="0738f-110">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="0738f-111">たとえば、日付と時刻の値とそのタイム ゾーンの両方を含む構造体を宣言します。</span><span class="sxs-lookup"><span data-stu-id="0738f-111">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="0738f-112">次の例では、この方法を使用して [DateTimeOffset](xref:System.DateTimeOffset) の値とそのタイム ゾーンをリンクします。</span><span class="sxs-lookup"><span data-stu-id="0738f-112">The following example uses this approach to link a [DateTimeOffset](xref:System.DateTimeOffset) value with its time zone.</span></span>

    ```csharp
    // Define a structure for DateTime values for internal use only
    internal struct TimeWithTimeZone
    {
    TimeZoneInfo TimeZone;
    DateTimeOffset Time;
    }
    ```

    ```vb
    ' Define a structure for DateTime values for internal use only
    Friend Structure TimeWithTimeZone
       Dim TimeZone As TimeZoneInfo
       Dim Time As Date
    End Structure
    ```
    
2. <span data-ttu-id="0738f-113">[TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) メソッドを呼び出して、時刻を世界協定時刻 (UTC) に変換します。</span><span class="sxs-lookup"><span data-stu-id="0738f-113">Convert a time to Coordinated Universal Time (UTC) by calling the [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span>

3. <span data-ttu-id="0738f-114">UTC 時刻で算術演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="0738f-114">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="0738f-115">[TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) メソッドを呼び出して、時刻を UTC から元の時刻に関連付けられているタイム ゾーンに変換します。</span><span class="sxs-lookup"><span data-stu-id="0738f-115">Convert the time from UTC to the original time's associated time zone by calling the [TimeZoneInfo.ConvertTime(DateTime, TimeZoneInfo)](xref:System.TimeZoneInfo.ConvertTime(System.DateTime,System.TimeZoneInfo)) method.</span></span> 

## <a name="example"></a><span data-ttu-id="0738f-116">例</span><span class="sxs-lookup"><span data-stu-id="0738f-116">Example</span></span>

<span data-ttu-id="0738f-117">次の例では、中部標準時の 2008 年 3 月 9 日午前 1 時 30 分に、2 時間 30 分を</span><span class="sxs-lookup"><span data-stu-id="0738f-117">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="0738f-118">加えます。</span><span class="sxs-lookup"><span data-stu-id="0738f-118">Central Standard Time.</span></span> <span data-ttu-id="0738f-119">夏時間へのタイム ゾーンの切り替えは、30 分後の 2008 年 3 月 9 日午前 2 時に</span><span class="sxs-lookup"><span data-stu-id="0738f-119">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="0738f-120">発生します。</span><span class="sxs-lookup"><span data-stu-id="0738f-120">on March 9, 2008.</span></span> <span data-ttu-id="0738f-121">この例は前に示した 4 つの手順に従うため、結果は正しい時刻である 2008 年 3 月 9 日午前 5 時に</span><span class="sxs-lookup"><span data-stu-id="0738f-121">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="0738f-122">なります。</span><span class="sxs-lookup"><span data-stu-id="0738f-122">on March 9, 2008.</span></span> 

```csharp
using System;

public struct TimeZoneTime
{
   public TimeZoneInfo TimeZone;
   public DateTimeOffset Time;

   public TimeZoneTime(TimeZoneInfo tz, DateTimeOffset time)
   {
      if (tz == null) 
         throw new ArgumentNullException("The time zone cannot be a null reference.");

      this.TimeZone = tz;
      this.Time = time;   
   }

   public TimeZoneTime AddTime(TimeSpan interval)
   {
      // Convert time to UTC
      DateTimeOffset utcTime = TimeZoneInfo.ConvertTime(this.Time, TimeZoneInfo.Utc);      
      // Add time interval to time
      utcTime = utcTime.Add(interval);
      // Convert time back to time in time zone
      return new TimeZoneTime(this.TimeZone, TimeZoneInfo.ConvertTime(utcTime, this.TimeZone));
   }
}

public class TimeArithmetic
{
   public const string tzName = "Central Standard Time";

   public static void Main()
   {
      try
      {
         TimeZoneTime cstTime1, cstTime2;

         TimeZoneInfo cst = TimeZoneInfo.FindSystemTimeZoneById(tzName);
         DateTime time1 = new DateTime(2008, 3, 9, 1, 30, 0);          
         TimeSpan twoAndAHalfHours = new TimeSpan(2, 30, 0);

         cstTime1 = new TimeZoneTime(cst, 
                        new DateTimeOffset(time1, cst.GetUtcOffset(time1)));
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours);
         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, 
                                                    twoAndAHalfHours.ToString(),  
                                                    cstTime2.Time);
      }
      catch
      {
         Console.WriteLine("Unable to find {0}.", tzName);
      }
   }
}
```

```vb
Public Structure TimeZoneTime
   Public TimeZone As TimeZoneInfo
   Public Time As Date

   Public Sub New(tz As TimeZoneInfo, time As Date)
      If tz Is Nothing Then _
         Throw New ArgumentNullException("The time zone cannot be a null reference.")

      Me.TimeZone = tz
      Me.Time = time
   End Sub

   Public Function AddTime(interval As TimeSpan) As TimeZoneTime
      ' Convert time to UTC
      Dim utcTime As DateTime = TimeZoneInfo.ConvertTimeToUtc(Me.Time, _
                                                              Me.TimeZone)      
      ' Add time interval to time
      utcTime = utcTime.Add(interval)
      ' Convert time back to time in time zone
      Return New TimeZoneTime(Me.TimeZone, TimeZoneInfo.ConvertTime(utcTime, _
                              TimeZoneInfo.Utc, Me.TimeZone))
   End Function
End Structure

Module TimeArithmetic
   Public Const tzName As String = "Central Standard Time"

   Public Sub Main()
      Try
         Dim cstTime1, cstTime2 As TimeZoneTime

         Dim cst As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById(tzName)
         Dim time1 As Date = #03/09/2008 1:30AM#
         Dim twoAndAHalfHours As New TimeSpan(2, 30, 0)

         cstTime1 = New TimeZoneTime(cst, time1)
         cstTime2 = cstTime1.AddTime(twoAndAHalfHours)

         Console.WriteLine("{0} + {1} hours = {2}", cstTime1.Time, _
                                                    twoAndAHalfHours.ToString(), _ 
                                                    cstTime2.Time)  
      Catch
         Console.WriteLine("Unable to find {0}.", tzName)
      End Try   
   End Sub   
End Module
```

<span data-ttu-id="0738f-123">最初に UTC に変換せず、単に [DateTimeOffset](xref:System.DateTimeOffset) 値に対してこの加算を実行すると、結果には正しい時刻が反映されますが、その時刻に対して指定されたタイム ゾーンのオフセットは反映されません。</span><span class="sxs-lookup"><span data-stu-id="0738f-123">Note that if this addition is simply performed on the [DateTimeOffset](xref:System.DateTimeOffset) value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span> 

<span data-ttu-id="0738f-124">[DateTimeOffset](xref:System.DateTimeOffset) 値は、属している可能性のあるどのタイム ゾーンとも関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="0738f-124">[DateTimeOffset](xref:System.DateTimeOffset) values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="0738f-125">タイム ゾーンの調整規則が自動的に適用されるような方法で日付と時刻の演算を実行するには、日付と時刻の値の属するタイム ゾーンがすぐに識別できる状態でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="0738f-125">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="0738f-126">つまり、日時と関連付けられているタイム ゾーンを密に結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0738f-126">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="0738f-127">これは、次のようないくつかの方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0738f-127">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="0738f-128">アプリケーションで使用されるすべての時刻が、特定のタイム ゾーンに属するものと仮定します。</span><span class="sxs-lookup"><span data-stu-id="0738f-128">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="0738f-129">この方法は、適切な場合もありますが、柔軟性が限られ、移植性が制限される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="0738f-129">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="0738f-130">日時と関連付けられているタイム ゾーンを型のフィールドとして組み込むことで、両者を密に結合する型を定義します。</span><span class="sxs-lookup"><span data-stu-id="0738f-130">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="0738f-131">コード例ではこの方法を使用して、日時とタイム ゾーンを&2; つのメンバー フィールドに格納する構造体を定義しています。</span><span class="sxs-lookup"><span data-stu-id="0738f-131">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="0738f-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="0738f-132">See Also</span></span>

[<span data-ttu-id="0738f-133">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="0738f-133">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="0738f-134">日付と時刻を使用した算術演算の実行</span><span class="sxs-lookup"><span data-stu-id="0738f-134">Performing arithmetic operations with dates and times</span></span>](performing-arithmetic-operations.md)

