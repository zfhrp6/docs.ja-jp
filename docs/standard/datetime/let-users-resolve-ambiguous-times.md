---
title: "方法 : ユーザーがあいまいな時刻を解決できるようにする"
description: "方法 : ユーザーがあいまいな時刻を解決できるようにする"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: d6858a5c-02ab-4367-9e08-fa22c051c38d
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: ede8d021a4f524cf37f7ad00b6aed89d1b1729f8
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-let-users-resolve-ambiguous-times"></a><span data-ttu-id="f1626-104">方法 : ユーザーがあいまいな時刻を解決できるようにする</span><span class="sxs-lookup"><span data-stu-id="f1626-104">How to: let users resolve ambiguous times</span></span>

<span data-ttu-id="f1626-105">あいまいな時刻は複数の世界協定時刻 (UTC) にマップされる時刻です。</span><span class="sxs-lookup"><span data-stu-id="f1626-105">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="f1626-106">これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。</span><span class="sxs-lookup"><span data-stu-id="f1626-106">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="f1626-107">あいまいな時刻を処理する場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f1626-107">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="f1626-108">あいまいな時刻が、ユーザーによって入力されたデータの項目の場合は、あいまいさの解決をユーザーに任せることができます。</span><span class="sxs-lookup"><span data-stu-id="f1626-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

* <span data-ttu-id="f1626-109">時刻が UTC にどのようにマップされるかを想定します。</span><span class="sxs-lookup"><span data-stu-id="f1626-109">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="f1626-110">たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。</span><span class="sxs-lookup"><span data-stu-id="f1626-110">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

<span data-ttu-id="f1626-111">この記事では、ユーザーにあいまいな時刻を解決させる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f1626-111">This article shows how to let a user resolve an ambiguous time.</span></span>

## <a name="to-let-a-user-resolve-an-ambiguous-time"></a><span data-ttu-id="f1626-112">ユーザーにあいまいな時刻を解決させるには</span><span class="sxs-lookup"><span data-stu-id="f1626-112">To let a user resolve an ambiguous time</span></span>

1. <span data-ttu-id="f1626-113">ユーザーによって入力された日付と時刻を取得します。</span><span class="sxs-lookup"><span data-stu-id="f1626-113">Get the date and time input by the user.</span></span>

2. <span data-ttu-id="f1626-114">[IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) または [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) メソッドを呼び出して、時刻があいまいかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="f1626-114">Call the [IsAmbiguousTime(DateTime)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTime)) or [IsAmbiguousTime(DateTimeOffset)](xref:System.TimeZoneInfo.IsAmbiguousTime(System.DateTimeOffset)) method to determine whether the time is ambiguous.</span></span>

3. <span data-ttu-id="f1626-115">ユーザーに目的のオフセットを選択させます。</span><span class="sxs-lookup"><span data-stu-id="f1626-115">Let the user select the desired offset.</span></span>

4. <span data-ttu-id="f1626-116">ローカル時刻からユーザーによって選択されたオフセットを減算して、UTC の日時を取得します。</span><span class="sxs-lookup"><span data-stu-id="f1626-116">Get the UTC date and time by subtracting the offset selected by the user from the local time.</span></span>

5. <span data-ttu-id="f1626-117">`static` ( Visual Basic では `Shared`) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) メソッドを呼び出して、UTC の日時値の [Kind](xref:System.DateTime.Kind) プロパティを [DateTimeKind.Utc](xref:System.DateTimeKind.Utc) に設定します。</span><span class="sxs-lookup"><span data-stu-id="f1626-117">Call the `static` (`Shared` in Visual Basic ) [SpecifyKind](xref:System.DateTime.SpecifyKind(System.DateTime,System.DateTimeKind)) method to set the UTC date and time value's [Kind](xref:System.DateTime.Kind) property to [DateTimeKind.Utc](xref:System.DateTimeKind.Utc).</span></span>

## <a name="example"></a><span data-ttu-id="f1626-118">例</span><span class="sxs-lookup"><span data-stu-id="f1626-118">Example</span></span>

<span data-ttu-id="f1626-119">次の例では、ユーザーに日付と時刻を入力するように求め、それがあいまいである場合は、ユーザーにあいまいな時刻をマップする UTC 時刻を選択させています。</span><span class="sxs-lookup"><span data-stu-id="f1626-119">The following example prompts the user to enter a date and time and, if it is ambiguous, lets the user select the UTC time that the ambiguous time maps to.</span></span> <span data-ttu-id="f1626-120">この例では、[DateTime](xref:System.DateTime) オブジェクトを使用しています。必要に応じて、[DateTimeOffset](xref:System.DateTimeOffset) オブジェクトに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="f1626-120">The example uses a [DateTime](xref:System.DateTime) object; you can substitute a [DateTimeOffset](xref:System.DateTimeOffset) object if desired.</span></span>

```csharp
private void GetUserDateInput()
{
   // Get date and time from user
   DateTime inputDate = GetUserDateTime();
   DateTime utcDate;

   // Exit if date has no significant value
   if (inputDate == DateTime.MinValue) return;

   if (TimeZoneInfo.Local.IsAmbiguousTime(inputDate))
   {
      Console.WriteLine("The date you've entered is ambiguous.");
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:");
      TimeSpan[] offsets = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate);
      for (int ctr = 0; ctr < offsets.Length; ctr++)
      {
         Console.WriteLine("{0}.) {1} hours, {2} minutes", ctr, offsets[ctr].Hours, offsets[ctr].Minutes);
      }
      Console.Write("> ");
      int selection = Convert.ToInt32(Console.ReadLine());

      // Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = DateTime.SpecifyKind(inputDate - offsets[selection], DateTimeKind.Utc);

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());
   }
   else
   {
      utcDate = inputDate.ToUniversalTime();
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString());    
   }
}

private DateTime GetUserDateTime() 
{
   bool exitFlag = false;             // flag to exit loop if date is valid
   string dateString;  
   DateTime inputDate = DateTime.MinValue;

   Console.Write("Enter a local date and time: ");
   while (! exitFlag)
   {
      dateString = Console.ReadLine();
      if (dateString.ToUpper() == "E")
         exitFlag = true;

      if (DateTime.TryParse(dateString, out inputDate))
         exitFlag = true;
      else
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ");
   }

   return inputDate;        
}
```

```vb
Private Sub GetUserDateInput()
   ' Get date and time from user
   Dim inputDate As Date = GetUserDateTime()
   Dim utcDate As Date

   ' Exit if date has no significant value
   If inputDate = Date.MinValue Then Exit Sub

   If TimeZoneInfo.Local.IsAmbiguousTime(inputDate) Then
      Console.WriteLine("The date you've entered is ambiguous.")
      Console.WriteLine("Please select the correct offset from Universal Coordinated Time:")
      Dim offsets() As TimeSpan = TimeZoneInfo.Local.GetAmbiguousTimeOffsets(inputDate)
      For ctr As Integer = 0 to offsets.Length - 1
         Dim zoneDescription As String
         If offsets(ctr).Equals(TimeZoneInfo.Local.BaseUtcOffset) Then 
            zoneDescription = TimeZoneInfo.Local.StandardName
         Else
            zoneDescription = TimeZoneInfo.Local.DaylightName
         End If
         Console.WriteLine("{0}.) {1} hours, {2} minutes ({3})", _
                           ctr, offsets(ctr).Hours, offsets(ctr).Minutes, zoneDescription)
      Next         
      Console.Write("> ")
      Dim selection As Integer = CInt(Console.ReadLine())

      ' Convert local time to UTC, and set Kind property to DateTimeKind.Utc
      utcDate = Date.SpecifyKind(inputDate - offsets(selection), DateTimeKind.Utc)

      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())
   Else
      utcDate = inputDate.ToUniversalTime()
      Console.WriteLine("{0} local time corresponds to {1} {2}.", inputDate, utcDate, utcDate.Kind.ToString())    
   End If
End Sub

Private Function GetUserDateTime() As Date
   Dim exitFlag As Boolean = False            ' flag to exit loop if date is valid
   Dim dateString As String 
   Dim inputDate As Date = Date.MinValue

   Console.Write("Enter a local date and time: ")
   Do While Not exitFlag
      dateString = Console.ReadLine()
      If dateString.ToUpper = "E" Then exitFlag = True
      If Date.TryParse(dateString, inputDate) Then
         exitFlag = true
      Else   
         Console.Write("Enter a valid date and time, or enter 'e' to exit: ")
      End If
   Loop

   Return inputDate        
End Function
```

<span data-ttu-id="f1626-121">このコード例の核心は、[TimeSpan](xref:System.TimeSpan) オブジェクトの配列を使用して、UTC からのあいまいな時刻の可能性のあるオフセットを示すことです。</span><span class="sxs-lookup"><span data-stu-id="f1626-121">The core of the example code uses an array of [TimeSpan](xref:System.TimeSpan) objects to indicate possible offsets of the ambiguous time from UTC.</span></span> <span data-ttu-id="f1626-122">ただし、これらのオフセットは、ユーザーにとって意味がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1626-122">However, these offsets are unlikely to be meaningful to the user.</span></span> <span data-ttu-id="f1626-123">オフセットの意味を明確にするには、コードで、オフセットがローカル タイム ゾーンの標準時刻を表すか、または夏時間を表すかに注意します。</span><span class="sxs-lookup"><span data-stu-id="f1626-123">To clarify the meaning of the offsets, the code also notes whether an offset represents the local time zone's standard time or its daylight saving time.</span></span> <span data-ttu-id="f1626-124">コードで標準時間と夏時間を判断するには、そのオフセットと [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) プロパティの値を比較します。</span><span class="sxs-lookup"><span data-stu-id="f1626-124">The code determines which time is standard and which time is daylight by comparing the offset with the value of the [BaseUtcOffset](xref:System.TimeZoneInfo.BaseUtcOffset) property.</span></span> <span data-ttu-id="f1626-125">このプロパティは、UTC とタイム ゾーンの標準時間の差を示します。</span><span class="sxs-lookup"><span data-stu-id="f1626-125">This property indicates the difference between the UTC and the time zone's standard time.</span></span>

<span data-ttu-id="f1626-126">この例では、ローカル タイム ゾーンへのすべての参照は [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティによって行われます。ローカル タイム ゾーンが、オブジェクト変数に割り当てられることはありません。</span><span class="sxs-lookup"><span data-stu-id="f1626-126">In this example, all references to the local time zone are made through the [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="f1626-127">これは、別の呼び出しがキャッシ データをクリアして、ローカル タイム ゾーンが割り当てられているオブジェクトが無効にされる可能性があるために、推奨される方法です。</span><span class="sxs-lookup"><span data-stu-id="f1626-127">This is a recommended practice because another call could clear the cached data and invalidate any objects that the local time zone is assigned to.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1626-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1626-128">See Also</span></span>

[<span data-ttu-id="f1626-129">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="f1626-129">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="f1626-130">方法: あいまいな時刻を解決する</span><span class="sxs-lookup"><span data-stu-id="f1626-130">How to: resolve ambiguous times</span></span>](resolve-ambiguous-times.md)


