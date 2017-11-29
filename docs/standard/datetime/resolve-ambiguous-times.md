---
title: "方法: あいまいな時刻を解決するには"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3706747848dbcd29d4ed2e81d5b7447a127a653
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-ambiguous-times"></a><span data-ttu-id="f7cd0-102">方法: あいまいな時刻を解決するには</span><span class="sxs-lookup"><span data-stu-id="f7cd0-102">How to: Resolve ambiguous times</span></span>

<span data-ttu-id="f7cd0-103">あいまいな時刻とは、複数の世界協定時刻 (UTC) にマップされる時刻です。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-103">An ambiguous time is a time that maps to more than one Coordinated Universal Time (UTC).</span></span> <span data-ttu-id="f7cd0-104">これは、あるタイム ゾーンの夏時間から標準時間に移行する際など、時計の時刻を前に戻すときに発生します。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-104">It occurs when the clock time is adjusted back in time, such as during the transition from a time zone's daylight saving time to its standard time.</span></span> <span data-ttu-id="f7cd0-105">あいまいな時刻を処理する場合は、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-105">When handling an ambiguous time, you can do one of the following:</span></span>

* <span data-ttu-id="f7cd0-106">時刻が UTC にどのようにマップされるかを想定します。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-106">Make an assumption about how the time maps to UTC.</span></span> <span data-ttu-id="f7cd0-107">たとえば、あいまいな時刻は常にタイム ゾーンの標準時刻で表されると想定できます。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-107">For example, you can assume that an ambiguous time is always expressed in the time zone's standard time.</span></span>

* <span data-ttu-id="f7cd0-108">あいまいな時刻が、ユーザーによって入力されたデータ項目である場合は、あいまいさの解決をユーザーに任せることができます。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-108">If the ambiguous time is an item of data entered by the user, you can leave it to the user to resolve the ambiguity.</span></span>

<span data-ttu-id="f7cd0-109">このトピックでは、タイム ゾーンの標準時を表すと仮定すると、あいまいな時刻を解決する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-109">This topic shows how to resolve an ambiguous time by assuming that it represents the time zone's standard time.</span></span>

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a><span data-ttu-id="f7cd0-110">あいまいな時刻をタイム ゾーンの標準時刻にマップするには</span><span class="sxs-lookup"><span data-stu-id="f7cd0-110">To map an ambiguous time to a time zone's standard time</span></span>

1. <span data-ttu-id="f7cd0-111">呼び出す、<xref:System.TimeZoneInfo.IsAmbiguousTime%2A>時刻があいまいかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-111">Call the <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> method to determine whether the time is ambiguous.</span></span>

2. <span data-ttu-id="f7cd0-112">時刻があいまいな場合は、減算、時刻から、<xref:System.TimeSpan>タイム ゾーンのによって返されるオブジェクト<xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-112">If the time is ambiguous, subtract the time from the <xref:System.TimeSpan> object returned by the time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property.</span></span>

3. <span data-ttu-id="f7cd0-113">呼び出す、 `static` (`Shared` Visual Basic .NET で)<xref:System.DateTime.SpecifyKind%2A>値を設定する (utc) 日付と時刻のメソッド<xref:System.DateTime.Kind%2A>プロパティを<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-113">Call the `static` (`Shared` in Visual Basic .NET) <xref:System.DateTime.SpecifyKind%2A> method to set the UTC date and time value's <xref:System.DateTime.Kind%2A> property to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="f7cd0-114">例</span><span class="sxs-lookup"><span data-stu-id="f7cd0-114">Example</span></span>

<span data-ttu-id="f7cd0-115">次の例では、ローカル タイム ゾーンの標準時刻を表すと仮定すると、あいまいな時刻を UTC に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-115">The following example illustrates how to convert an ambiguous time to UTC by assuming that it represents the local time zone's standard time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

<span data-ttu-id="f7cd0-116">例では、という名前のメソッドから成る`ResolveAmbiguousTime`を決定するかどうか、<xref:System.DateTime>に渡された値があいまいです。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-116">The example consists of a method named `ResolveAmbiguousTime` that determines whether the <xref:System.DateTime> value passed to it is ambiguous.</span></span> <span data-ttu-id="f7cd0-117">値があいまいなメソッドを返します、<xref:System.DateTime>を対応する UTC 時刻を表す値です。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-117">If the value is ambiguous, the method returns a <xref:System.DateTime> value that represents the corresponding UTC time.</span></span> <span data-ttu-id="f7cd0-118">このメソッドでは、この変換を処理のローカル タイム ゾーンの値を減算して<xref:System.TimeZoneInfo.BaseUtcOffset%2A>現地時刻からのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-118">The method handles this conversion by subtracting the value of the local time zone's <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property from the local time.</span></span>

<span data-ttu-id="f7cd0-119">あいまいな時刻を呼び出すことによって処理される通常は、<xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A>の配列を取得する方法を<xref:System.TimeSpan>あいまいな時刻の可能な UTC を格納するオブジェクトをオフセットします。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-119">Ordinarily, an ambiguous time is handled by calling the <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> method to retrieve an array of <xref:System.TimeSpan> objects that contain the ambiguous time's possible UTC offsets.</span></span> <span data-ttu-id="f7cd0-120">しかし、この例は、あいまいな時刻は常にタイム ゾーンの標準時刻にマップされるという想定に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-120">However, this example makes the arbitrary assumption that an ambiguous time should always be mapped to the time zone's standard time.</span></span> <span data-ttu-id="f7cd0-121"><xref:System.TimeZoneInfo.BaseUtcOffset%2A>プロパティは、UTC とタイム ゾーンの標準時刻のオフセットを返します。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-121">The <xref:System.TimeZoneInfo.BaseUtcOffset%2A> property returns the offset between UTC and a time zone's standard time.</span></span>

<span data-ttu-id="f7cd0-122">この例では、ローカル タイム ゾーンへのすべての参照はを通じて行われます、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティ以外のローカル時刻ゾーンをオブジェクト変数に割り当てることはありません。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-122">In this example, all references to the local time zone are made through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property; the local time zone is never assigned to an object variable.</span></span> <span data-ttu-id="f7cd0-123">これは、ためにの推奨される方法への呼び出し、<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>メソッドには、ローカル タイム ゾーンに割り当てられているすべてのオブジェクトが無効にします。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-123">This is a recommended practice because a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method invalidates any objects that the local time zone is assigned to.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="f7cd0-124">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f7cd0-124">Compiling the code</span></span>

<span data-ttu-id="f7cd0-125">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-125">This example requires:</span></span>

* <span data-ttu-id="f7cd0-126">される System.Core.dll への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-126">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="f7cd0-127"><xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要です)。</span><span class="sxs-lookup"><span data-stu-id="f7cd0-127">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7cd0-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7cd0-128">See also</span></span>

<span data-ttu-id="f7cd0-129">[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[する方法: あいまいな時刻を解決することができます](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span><span class="sxs-lookup"><span data-stu-id="f7cd0-129">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)</span></span>
