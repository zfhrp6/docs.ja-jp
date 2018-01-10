---
title: "タイム ゾーン間での時刻の変換"
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
- times [.NET Framework], converting
- time zones [.NET Framework], conversions
- UTC times, converting
- converting times
- local time conversions
ms.assetid: a51e1a3b-c983-4320-b31a-1f9fa3cf824a
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eabe0c1511e6fd42798f1a879e9e8d526d543a29
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="converting-times-between-time-zones"></a><span data-ttu-id="bb4a3-102">タイム ゾーン間での時刻の変換</span><span class="sxs-lookup"><span data-stu-id="bb4a3-102">Converting times between time zones</span></span>

<span data-ttu-id="bb4a3-103">日時を使用するすべてのアプリケーションで、タイム ゾーン間の違いを処理することの重要性が高まっています。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-103">It is becoming increasingly important for any application that works with dates and times to handle differences between time zones.</span></span> <span data-ttu-id="bb4a3-104">アプリケーション不要になったと仮定するすべての時刻で表現できるローカル時刻は、時間がから利用可能な<xref:System.DateTime>構造体。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-104">An application can no longer assume that all times can be expressed in the local time, which is the time available from the <xref:System.DateTime> structure.</span></span> <span data-ttu-id="bb4a3-105">たとえば、米国東部の現在の時刻を表示する Web ページには、東アジアの顧客に対する信頼性を欠いています。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-105">For example, a Web page that displays the current time in the eastern part of the United States will lack credibility to a customer in eastern Asia.</span></span> <span data-ttu-id="bb4a3-106">このトピックは、時間を別の 1 つのタイム ゾーンに変換する方法と、変換する方法について説明します。<xref:System.DateTimeOffset>タイム ゾーンに対応が限られている値。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-106">This topic explains how to convert times from one time zone to another, as well as how to convert <xref:System.DateTimeOffset> values that have limited time zone awareness.</span></span>

## <a name="converting-to-coordinated-universal-time"></a><span data-ttu-id="bb4a3-107">世界協定時刻への変換</span><span class="sxs-lookup"><span data-stu-id="bb4a3-107">Converting to Coordinated Universal Time</span></span>

<span data-ttu-id="bb4a3-108">世界協定時刻 (UTC) は、高精度の原子時標準です。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-108">Coordinated Universal Time (UTC) is a high-precision, atomic time standard.</span></span> <span data-ttu-id="bb4a3-109">世界のタイム ゾーンは、UTC からの正または負のオフセットとして表現されます。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-109">The world’s time zones are expressed as positive or negative offsets from UTC.</span></span> <span data-ttu-id="bb4a3-110">したがって、UTC はタイム ゾーンの影響を受けない、またはタイム ゾーンに依存しない種類の時刻を提供します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-110">Thus, UTC provides a kind of time-zone free or time-zone neutral time.</span></span> <span data-ttu-id="bb4a3-111">コンピューター間の日時の移植性が重要となる場合には、UTC 時刻の使用が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-111">The use of UTC time is recommended when a date and time's portability across computers is important.</span></span> <span data-ttu-id="bb4a3-112">(詳細および日付と時刻を使用して他のベスト プラクティスでは、次を参照してください[.NET Framework の DateTime を使用したベスト プラクティスのコーディング](https://msdn.microsoft.com/library/ms973825.aspx)。)。個別のタイム ゾーンを UTC に変換すると、時間の比較が容易になります。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-112">(For details and other best practices using dates and times, see [Coding best practices using DateTime in the .NET Framework](https://msdn.microsoft.com/library/ms973825.aspx).) Converting individual time zones to UTC makes time comparisons easy.</span></span>

> [!NOTE]
> <span data-ttu-id="bb4a3-113">シリアル化することも、<xref:System.DateTimeOffset>時間で明確に単一のポイントを表す構造体。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-113">You can also serialize a <xref:System.DateTimeOffset> structure to unambiguously represent a single point in time.</span></span> <span data-ttu-id="bb4a3-114"><xref:System.DateTimeOffset>オブジェクト値を格納します日付と時刻 (utc) からのオフセットと共に、常に特定の時点の間のリレーションシップに対してな UTC です。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-114">Because <xref:System.DateTimeOffset> objects store a date and time value along with its offset from UTC, they always represent a particular point in time in relationship to UTC.</span></span>

<span data-ttu-id="bb4a3-115">呼び出して、時刻を UTC に変換する最も簡単な方法は、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-115">The easiest way to convert a time to UTC is to call the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bb4a3-116">メソッドによって実行される正確な変換は、の値によって異なります、`dateTime`パラメーターの<xref:System.DateTime.Kind%2A>プロパティは、次の表に示すようです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-116">The exact conversion performed by the method depends on the value of the `dateTime` parameter's <xref:System.DateTime.Kind%2A> property, as the following table shows.</span></span>

| `DateTime.Kind`            | <span data-ttu-id="bb4a3-117">変換</span><span class="sxs-lookup"><span data-stu-id="bb4a3-117">Conversion</span></span>                                                                     |
| -------------------------- | ------------------------------------------------------------------------------ |
| `DateTimeKind.Local`       | <span data-ttu-id="bb4a3-118">現地時刻を UTC に変換します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-118">Converts local time to UTC.</span></span>                                                    |
| `DateTimeKind.Unspecified` | <span data-ttu-id="bb4a3-119">`dateTime` パラメーターが現地時刻であることを前提とし、現地時刻を UTC に変換します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-119">Assumes the `dateTime` parameter is local time and converts local time to UTC.</span></span> |
| `DateTimeKind.Utc`         | <span data-ttu-id="bb4a3-120">`dateTime` パラメーターを変更せずに返します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-120">Returns the `dateTime` parameter unchanged.</span></span>                                    |

<span data-ttu-id="bb4a3-121">次のコードは、現在の現地時刻を UTC に変換し、コンソールに結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-121">The following code converts the current local time to UTC and displays the result to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#6)]
[!code-vb[System.TimeZone2.Concepts#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#6)]

> [!NOTE]
> <span data-ttu-id="bb4a3-122"><xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>メソッドは必ずしも結果も返りませんと同じでは、<xref:System.TimeZone.ToUniversalTime%2A?displayProperty=nameWithType>と<xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-122">The <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> method does not necessarily produce results that are identical to the <xref:System.TimeZone.ToUniversalTime%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToUniversalTime%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="bb4a3-123">タイム ゾーンが複数の調整規則を含む場合は、ホスト システムのローカル<xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType>特定の日付と時刻に適切なルールが適用されます。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-123">If the host system's local time zone includes multiple adjustment rules, <xref:System.TimeZoneInfo.ConvertTimeToUtc%28System.DateTime%29?displayProperty=nameWithType> applies the appropriate rule to a particular date and time.</span></span> <span data-ttu-id="bb4a3-124">他の 2 つのメソッドは、常に最新の調整規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-124">The other two methods always apply the latest adjustment rule.</span></span>

<span data-ttu-id="bb4a3-125">ローカル時刻または UTC で日付と時刻の値を表していない場合、<xref:System.DateTime.ToUniversalTime%2A>メソッドは誤った結果を返す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-125">If the date and time value does not represent either the local time or UTC, the <xref:System.DateTime.ToUniversalTime%2A> method will likely return an erroneous result.</span></span> <span data-ttu-id="bb4a3-126">ただし、使用することができます、<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>指定されたタイム ゾーンから日付と時刻に変換します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-126">However, you can use the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> method to convert the date and time from a specified time zone.</span></span> <span data-ttu-id="bb4a3-127">(詳細については取得する、<xref:System.TimeZoneInfo>を変換先タイム ゾーンを表すオブジェクトを参照してください[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md))。次のコードでは、<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType>東部標準時を UTC に変換します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-127">(For details on retrieving a <xref:System.TimeZoneInfo> object that represents the destination time zone, see [Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md).) The following code uses the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A?displayProperty=nameWithType> method to convert Eastern Standard Time to UTC.</span></span>

[!code-csharp[System.TimeZone2.Concepts#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#7)]
[!code-vb[System.TimeZone2.Concepts#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#7)]

<span data-ttu-id="bb4a3-128">このメソッドはスローなお、<xref:System.ArgumentException>場合、<xref:System.DateTime>オブジェクトの<xref:System.DateTime.Kind%2A>プロパティおよびタイム ゾーンが一致しません。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-128">Note that this method throws an <xref:System.ArgumentException> if the <xref:System.DateTime> object's <xref:System.DateTime.Kind%2A> property and the time zone are mismatched.</span></span> <span data-ttu-id="bb4a3-129">一致しない場合は、<xref:System.DateTime.Kind%2A>プロパティは<xref:System.DateTimeKind?displayProperty=nameWithType>ですが、<xref:System.TimeZoneInfo>オブジェクトは、ローカル タイム ゾーンを表していません場合、または、<xref:System.DateTime.Kind%2A>プロパティは<xref:System.DateTimeKind?displayProperty=nameWithType>ですが、<xref:System.TimeZoneInfo>オブジェクトが等しくない<xref:System.DateTimeKind?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-129">A mismatch occurs if the <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind?displayProperty=nameWithType> but the <xref:System.TimeZoneInfo> object does not represent the local time zone, or if the <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind?displayProperty=nameWithType> but the <xref:System.TimeZoneInfo> object does not equal <xref:System.DateTimeKind?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bb4a3-130">これらのメソッドのすべてにかかる<xref:System.DateTime>値をパラメーターと戻り値として、<xref:System.DateTime>値。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-130">All of these methods take <xref:System.DateTime> values as parameters and return a <xref:System.DateTime> value.</span></span> <span data-ttu-id="bb4a3-131"><xref:System.DateTimeOffset> 、値、<xref:System.DateTimeOffset>構造体には、<xref:System.DateTimeOffset.ToUniversalTime%2A>日付と現在のインスタンスの時刻を UTC に変換するメソッドをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-131">For <xref:System.DateTimeOffset> values, the <xref:System.DateTimeOffset> structure has a <xref:System.DateTimeOffset.ToUniversalTime%2A> instance method that converts the date and time of the current instance to UTC.</span></span> <span data-ttu-id="bb4a3-132">次の例では、<xref:System.DateTimeOffset.ToUniversalTime%2A>現地時間と他のいくつかの時刻を世界協定時刻 (UTC) に変換します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-132">The following example calls the <xref:System.DateTimeOffset.ToUniversalTime%2A> method to convert a local time and several other times to Coordinated Universal Time (UTC).</span></span>

[!code-csharp[System.DateTimeOffset.Methods#16](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/cs/Methods.cs#16)]
[!code-vb[System.DateTimeOffset.Methods#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Methods/vb/Methods.vb#16)]

## <a name="converting-utc-to-a-designated-time-zone"></a><span data-ttu-id="bb4a3-133">UTC から指定したタイム ゾーンへの変換</span><span class="sxs-lookup"><span data-stu-id="bb4a3-133">Converting UTC to a designated time zone</span></span>

<span data-ttu-id="bb4a3-134">UTC を現地時刻に変換するには、「に変換する (utc) から現地時刻」次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-134">To convert UTC to local time, see the "Converting UTC to Local Time" section that follows.</span></span> <span data-ttu-id="bb4a3-135">(Utc) を指定する任意のタイム ゾーンの時刻に変換する呼び出し、<xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-135">To convert UTC to the time in any time zone that you designate, call the <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> method.</span></span> <span data-ttu-id="bb4a3-136">このメソッドは、次の 2 つのパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-136">The method takes two parameters:</span></span>

* <span data-ttu-id="bb4a3-137">変換対象の UTC。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-137">The UTC to convert.</span></span> <span data-ttu-id="bb4a3-138">これは、必要があります、<xref:System.DateTime>値が<xref:System.DateTime.Kind%2A>プロパティに設定されている`Unspecified`または`Utc`です。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-138">This must be a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is set to `Unspecified` or `Utc`.</span></span>

* <span data-ttu-id="bb4a3-139">UTC の変換先のタイム ゾーン。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-139">The time zone to convert the UTC to.</span></span>

<span data-ttu-id="bb4a3-140">次のコードは、UTC を中部標準時に変換します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-140">The following code converts UTC to Central Standard Time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#8)]
[!code-vb[System.TimeZone2.Concepts#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#8)]

## <a name="converting-utc-to-local-time"></a><span data-ttu-id="bb4a3-141">UTC から現地時刻への変換</span><span class="sxs-lookup"><span data-stu-id="bb4a3-141">Converting UTC to local time</span></span>

<span data-ttu-id="bb4a3-142">UTC を現地時刻に変換する呼び出し、<xref:System.DateTime.ToLocalTime%2A>のメソッド、<xref:System.DateTime>オブジェクトに変換する時刻をします。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-142">To convert UTC to local time, call the <xref:System.DateTime.ToLocalTime%2A> method of the <xref:System.DateTime> object whose time you want to convert.</span></span> <span data-ttu-id="bb4a3-143">メソッドの正確な動作は、オブジェクトの値によって異なります。<xref:System.DateTime.Kind%2A>プロパティは、次の表に示すようです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-143">The exact behavior of the method depends on the value of the object’s <xref:System.DateTime.Kind%2A> property, as the following table shows.</span></span>

| `DateTime.Kind`            | <span data-ttu-id="bb4a3-144">変換</span><span class="sxs-lookup"><span data-stu-id="bb4a3-144">Conversion</span></span>                                                                               |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| `DateTimeKind.Local`       | <span data-ttu-id="bb4a3-145">返します、<xref:System.DateTime>変更されていない値です。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-145">Returns the <xref:System.DateTime> value unchanged.</span></span>                                      |
| `DateTimeKind.Unspecified` | <span data-ttu-id="bb4a3-146">いるものと、<xref:System.DateTime>値は utc し、現地時刻を UTC に変換します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-146">Assumes that the <xref:System.DateTime> value is UTC and converts the UTC to local time.</span></span> |
| `DateTimeKind.Utc`         | <span data-ttu-id="bb4a3-147">変換、<xref:System.DateTime>を現地時刻の値。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-147">Converts the <xref:System.DateTime> value to local time.</span></span>                                 |

> [!NOTE]
> <span data-ttu-id="bb4a3-148"><xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType>メソッドの動作と同じように、`DateTime.ToLocalTime`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-148">The <xref:System.TimeZone.ToLocalTime%2A?displayProperty=nameWithType> method behaves identically to the `DateTime.ToLocalTime` method.</span></span> <span data-ttu-id="bb4a3-149">かかる、単一のパラメーターに変換する日付と時刻の値であります。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-149">It takes a single parameter, which is the date and time value to convert.</span></span>

<span data-ttu-id="bb4a3-150">使用して、ローカル時刻に、指定のタイム ゾーンの時刻を変換することも、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-150">You can also convert the time in any designated time zone to local time by using the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.ConvertTime%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bb4a3-151">この手法は、次のセクションで説明しています。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-151">This technique is discussed in the next section.</span></span>

## <a name="converting-between-any-two-time-zones"></a><span data-ttu-id="bb4a3-152">任意の 2 つのタイム ゾーン間での変換</span><span class="sxs-lookup"><span data-stu-id="bb4a3-152">Converting between any two time zones</span></span>

<span data-ttu-id="bb4a3-153">次の 2 つのいずれかを使用して、2 つのタイム ゾーン間で変換できる`static`(`Shared` Visual Basic で) のメソッド、<xref:System.TimeZoneInfo>クラス。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-153">You can convert between any two time zones by using either of the following two `static` (`Shared` in Visual Basic) methods of the <xref:System.TimeZoneInfo> class:</span></span>

* <xref:System.TimeZoneInfo.ConvertTime%2A>

  <span data-ttu-id="bb4a3-154">このメソッドのパラメーターは、変換する日付と時刻の値、`TimeZoneInfo`日付と時刻の値のタイム ゾーンを表すオブジェクト、および`TimeZoneInfo`に日付と時刻の値を変換先タイム ゾーンを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-154">This method's parameters are the date and time value to convert, a `TimeZoneInfo` object that represents the time zone of the date and time value, and a `TimeZoneInfo` object that represents the time zone to convert the date and time value to.</span></span>

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>

  <span data-ttu-id="bb4a3-155">このメソッドのパラメーターに日付と時刻の値を変換する日付と時刻の値に変換する、日付や時刻の値のタイム ゾーンの識別子およびタイム ゾーンの識別子です。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-155">This method's parameters are the date and time value to convert, the identifier of the date and time value's time zone, and the identifier of the time zone to convert the date and time value to.</span></span>

<span data-ttu-id="bb4a3-156">どちらの方法を必要とする、<xref:System.DateTime.Kind%2A>に変換する日付と時刻の値のプロパティと<xref:System.TimeZoneInfo>そのタイム ゾーンを表すオブジェクトまたはタイム ゾーンの識別子が互いに対応します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-156">Both methods require that the <xref:System.DateTime.Kind%2A> property of the date and time value to convert and the <xref:System.TimeZoneInfo> object or time zone identifier that represents its time zone correspond to one another.</span></span> <span data-ttu-id="bb4a3-157">それ以外の場合、<xref:System.ArgumentException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-157">Otherwise, an <xref:System.ArgumentException> is thrown.</span></span> <span data-ttu-id="bb4a3-158">たとえば場合、`Kind`日付と時刻の値のプロパティが`DateTimeKind.Local`場合、に、例外がスローされます、`TimeZoneInfo`メソッドにパラメーターとして渡されたオブジェクトは等しくありません`TimeZoneInfo.Local`です。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-158">For example, if the `Kind` property of the date and time value is `DateTimeKind.Local`, an exception is thrown if the `TimeZoneInfo` object passed as a parameter to the method is not equal to `TimeZoneInfo.Local`.</span></span> <span data-ttu-id="bb4a3-159">メソッドにパラメーターとして渡された識別子と等しくない場合にも、例外がスロー`TimeZoneInfo.Local.Id`です。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-159">An exception is also thrown if the identifier passed as a parameter to the method is not equal to `TimeZoneInfo.Local.Id`.</span></span>

<span data-ttu-id="bb4a3-160">次の例では、<xref:System.TimeZoneInfo.ConvertTime%2A>ハワイ標準時からを現地時刻に変換します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-160">The following example uses the <xref:System.TimeZoneInfo.ConvertTime%2A> method to convert from Hawaiian Standard Time to local time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#9](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#9)]
[!code-vb[System.TimeZone2.Concepts#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#9)]

## <a name="converting-datetimeoffset-values"></a><span data-ttu-id="bb4a3-161">DateTimeOffset 値の変換</span><span class="sxs-lookup"><span data-stu-id="bb4a3-161">Converting DateTimeOffset values</span></span>

<span data-ttu-id="bb4a3-162">日付と時刻の値によって表される<xref:System.DateTimeOffset>オブジェクトが完全にタイム ゾーンではない時にそのタイム ゾーンのオブジェクトは、関連付けを解除するためには注意がインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-162">Date and time values represented by <xref:System.DateTimeOffset> objects are not fully time-zone aware because the object is disassociated from its time zone at the time it is instantiated.</span></span> <span data-ttu-id="bb4a3-163">ただし、アプリケーションでは多くの場合、特定のタイム ゾーンの時刻ではなく、単に UTC からの 2 つの異なるオフセットに基づいて日時を変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-163">However, in many cases an application simply needs to convert a date and time based on two different offsets from UTC rather than on the time in particular time zones.</span></span> <span data-ttu-id="bb4a3-164">この変換を実行するには、現在のインスタンスを呼び出すことができます<xref:System.DateTimeOffset.ToOffset%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-164">To perform this conversion, you can call the current instance's <xref:System.DateTimeOffset.ToOffset%2A> method.</span></span> <span data-ttu-id="bb4a3-165">メソッドの 1 つのパラメーターは、新しい日付と時刻の値を返すメソッドのオフセットです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-165">The method's single parameter is the offset of the new date and time value that the method is to return.</span></span>

<span data-ttu-id="bb4a3-166">たとえば、Web ページに対するユーザー要求の日時が既知であり、MM/dd/yyyy hh:mm:ss zzzz の形式で文字列としてシリアル化される場合、次の `ReturnTimeOnServer` メソッドは、この日時値を Web サーバー上の日時に変換します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-166">For example, if the date and time of a user request for a Web page is known and is serialized as a string in the format MM/dd/yyyy hh:mm:ss zzzz, the following `ReturnTimeOnServer` method converts this date and time value to the date and time on the Web server.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/TimeConversions.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions.vb#1)] 

<span data-ttu-id="bb4a3-167">このメソッドが、UTC よりも 5 時間遅いタイム ゾーンの日時を表す文字列 "9/1/2007 5:32:07 -05:00" を渡された場合、米国の太平洋標準時ゾーンにあるサーバー用に 9/1/2007 3:32:07 AM -07:00 を太平洋標準時ゾーンでの実行例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-167">If the method is passed the string "9/1/2007 5:32:07 -05:00", which represents the date and time in a time zone five hours earlier than UTC, it returns 9/1/2007 3:32:07 AM -07:00 for a server located in the U.S. Pacific Standard Time zone.</span></span>

<span data-ttu-id="bb4a3-168"><xref:System.TimeZoneInfo>クラスには、オーバー ロードも含まれています、<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>でタイム ゾーンの変換を実行するメソッド<xref:System.DateTimeOffset.ToOffset(System.TimeSpan)>値。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-168">The <xref:System.TimeZoneInfo> class also includes an overload of the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method that performs time zone conversions with <xref:System.DateTimeOffset.ToOffset(System.TimeSpan)> values.</span></span> <span data-ttu-id="bb4a3-169">メソッドのパラメーターは、<xref:System.DateTimeOffset>値と時刻の変換先タイム ゾーンへの参照。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-169">The method's parameters are a <xref:System.DateTimeOffset> value and a reference to the time zone to which the time is to be converted.</span></span> <span data-ttu-id="bb4a3-170">メソッドの呼び出しが返されます、<xref:System.DateTimeOffset>値。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-170">The method call returns a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="bb4a3-171">たとえば、`ReturnTimeOnServer`メソッド、前の例では呼び出しを次のように書き換えることができます、<xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb4a3-171">For example, the `ReturnTimeOnServer` method in the previous example could be rewritten as follows to call the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29> method.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/cs/timeconversions2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual.OffsetConversions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.OffsetConversions/vb/TimeConversions2.vb#2)]

## <a name="see-also"></a><span data-ttu-id="bb4a3-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb4a3-172">See also</span></span>

<span data-ttu-id="bb4a3-173"><xref:System.TimeZoneInfo>[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)</span><span class="sxs-lookup"><span data-stu-id="bb4a3-173"><xref:System.TimeZoneInfo> [Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)</span></span>
