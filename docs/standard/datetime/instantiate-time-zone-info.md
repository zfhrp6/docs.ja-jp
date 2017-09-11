---
title: "方法 : TimeZoneInfo オブジェクトをインスタンス化する"
description: "方法 : TimeZoneInfo オブジェクトをインスタンス化する"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bff137e5-d550-44c3-b460-b3f2dabd4035
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f2584d446c92d2df2f6d74533ef07fe96888d36a
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="da8ac-104">方法 : TimeZoneInfo オブジェクトをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="da8ac-104">How to: instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="da8ac-105">[TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをインスタンス化する最も一般的な方法は、オペレーティング システムからオブジェクトに関する情報を取得することです。</span><span class="sxs-lookup"><span data-stu-id="da8ac-105">The most common way to instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object is to retrieve information about it from the operating system.</span></span> <span data-ttu-id="da8ac-106">このトピックでは、ローカル システムから [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをインスタンス化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="da8ac-106">This topic discusses how to instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object from the local system.</span></span>

## <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="da8ac-107">TimeZoneInfo オブジェクトをインスタンス化するには</span><span class="sxs-lookup"><span data-stu-id="da8ac-107">To instantiate a TimeZoneInfo Object</span></span>

1. <span data-ttu-id="da8ac-108">[TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを宣言します。</span><span class="sxs-lookup"><span data-stu-id="da8ac-108">Declare a [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span>

2. <span data-ttu-id="da8ac-109">`static` (Visual Basic の場合は `Shared`) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="da8ac-109">Call the `static` (`Shared` in Visual Basic) [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) method.</span></span>

3. <span data-ttu-id="da8ac-110">メソッドによってスローされた例外を処理します。</span><span class="sxs-lookup"><span data-stu-id="da8ac-110">Handle any exceptions thrown by the method.</span></span>

## <a name="example"></a><span data-ttu-id="da8ac-111">例</span><span class="sxs-lookup"><span data-stu-id="da8ac-111">Example</span></span>

<span data-ttu-id="da8ac-112">次のコードでは、東部標準時のタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを取得し、現地時刻に対応する東部標準時の時刻を表示します。</span><span class="sxs-lookup"><span data-stu-id="da8ac-112">The following code retrieves a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

```csharp
DateTime timeNow = DateTime.Now;
try
{
   TimeZoneInfo easternZone = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time");
   DateTime easternTimeNow = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, 
                                                   easternZone);
   Console.WriteLine("{0} {1} corresponds to {2} {3}.",
                     timeNow, 
                     TimeZoneInfo.Local.IsDaylightSavingTime(timeNow) ?
                               TimeZoneInfo.Local.DaylightName : 
                               TimeZoneInfo.Local.StandardName,
                     easternTimeNow, 
                     easternZone.IsDaylightSavingTime(easternTimeNow) ?
                                 easternZone.DaylightName : 
                                 easternZone.StandardName);
}
// Handle exception
//
// As an alternative to simply displaying an error message, an alternate Eastern
// Standard Time TimeZoneInfo object could be instantiated here either by restoring
// it from a serialized string or by providing the necessary data to the
// CreateCustomTimeZone method.
catch (InvalidTimeZoneException)
{
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.");
}
catch (SecurityException)
{
   Console.WriteLine("The application lacks permission to read time zone information from the registry.");
}
catch (OutOfMemoryException)
{
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.");
}
// If we weren't passing FindSystemTimeZoneById a literal string, we also 
// would handle an ArgumentNullException.
```

```vb
Dim timeNow As Date = Date.Now
Try
   Dim easternZone As TimeZoneInfo = TimeZoneInfo.FindSystemTimeZoneById("Eastern Standard Time")
   Dim easternTimeNow As Date = TimeZoneInfo.ConvertTime(timeNow, TimeZoneInfo.Local, easternZone)
   Console.WriteLine("{0} {1} corresponds to {2} {3}.", _
                     timeNow, _
                     IIf(TimeZoneInfo.Local.IsDaylightSavingTime(timeNow), _
                         TimeZoneInfo.Local.DaylightName, TimeZoneInfo.Local.StandardName), _
                     easternTimeNow, _
                     IIf(easternZone.IsDaylightSavingTime(easternTimeNow), _
                         easternZone.DaylightName, easternZone.StandardName))
' Handle exception
'
' As an alternative to simply displaying an error message, an alternate Eastern
' Standard Time TimeZoneInfo object could be instantiated here either by restoring
' it from a serialized string or by providing the necessary data to the
' CreateCustomTimeZone method.
Catch e As InvalidTimeZoneException
   Console.WriteLine("The Eastern Standard Time Zone contains invalid or missing data.")   
Catch e As SecurityException
   Console.WriteLine("The application lacks permission to read time zone information from the registry.")
Catch e As OutOfMemoryException
   Console.WriteLine("Not enough memory is available to load information on the Eastern Standard Time zone.")
' If we weren't passing FindSystemTimeZoneById a literal string, we also 
' would handle an ArgumentNullException.
End
``` 

<span data-ttu-id="da8ac-113">[TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) メソッドの唯一のパラメーターは、取得するタイム ゾーンの識別子です。これは、オブジェクトの [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="da8ac-113">The [TimeZoneInfo.FindSystemTimeZoneById](xref:System.TimeZoneInfo.FindSystemTimeZoneById(System.String)) method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's [TimeZoneInfo.Id](xref:System.TimeZoneInfo.Id) property.</span></span> <span data-ttu-id="da8ac-114">タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。</span><span class="sxs-lookup"><span data-stu-id="da8ac-114">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="da8ac-115">ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。</span><span class="sxs-lookup"><span data-stu-id="da8ac-115">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="da8ac-116">ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトの [StandardName](xref:System.TimeZoneInfo.StandardName) プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="da8ac-116">In most cases, its value corresponds to the [StandardName](xref:System.TimeZoneInfo.StandardName) property of a [TimeZoneInfo](xref:System.TimeZoneInfo) object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="da8ac-117">ただし、例外もあります。</span><span class="sxs-lookup"><span data-stu-id="da8ac-117">However, there are exceptions.</span></span> <span data-ttu-id="da8ac-118">有効な識別子を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、対応するタイム ゾーン識別子を記録しておくことです。</span><span class="sxs-lookup"><span data-stu-id="da8ac-118">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="da8ac-119">例については、「[方法 : コンピューター上に存在するタイム ゾーンを列挙する](enumerate-time-zones.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da8ac-119">For an illustration, see [How to: enumerate time zones present on a computer](enumerate-time-zones.md).</span></span> <span data-ttu-id="da8ac-120">「[ローカル システムで定義されているタイム ゾーンの検索](finding-the-time-zones-on-local-system.md)」のトピックには、選択したタイム ゾーン ID の一覧も掲載されています。</span><span class="sxs-lookup"><span data-stu-id="da8ac-120">The [Finding the time zones defined on a local system](finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="da8ac-121">タイム ゾーンが見つかると、メソッドは [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="da8ac-121">If the time zone is found, the method returns its [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span> <span data-ttu-id="da8ac-122">タイム ゾーンが見つかっても、そのデータが破損しているか不完全な場合には、メソッドから [InvalidTimeZoneException](xref:System.InvalidTimeZoneException) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="da8ac-122">If the time zone is found but its data is corrupted or incomplete, the method throws an [InvalidTimeZoneException](xref:System.InvalidTimeZoneException).</span></span> 

## <a name="see-also"></a><span data-ttu-id="da8ac-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="da8ac-123">See Also</span></span>

[<span data-ttu-id="da8ac-124">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="da8ac-124">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="da8ac-125">ローカル システムで定義されているタイム ゾーンの検索</span><span class="sxs-lookup"><span data-stu-id="da8ac-125">Finding the time zones defined on a local system</span></span>](finding-the-time-zones-on-local-system.md)
