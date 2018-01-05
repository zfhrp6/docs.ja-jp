---
title: "DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け"
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
- DateTimeOffset structure
- TimeZoneInfo class
- time zones [.NET Framework], common uses
- date and time classes [.NET Framework]
- time zones [.NET Framework], type options
- DateTime structure
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f9a91f7a00f72917ca5c469f51fd0aa11e24e125
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-datetime-datetimeoffset-timespan-and-timezoneinfo"></a><span data-ttu-id="c0904-102">DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け</span><span class="sxs-lookup"><span data-stu-id="c0904-102">Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>

<span data-ttu-id="c0904-103">日時情報を使用する .NET アプリケーションは非常に多様であり、その情報をさまざまな方法で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0904-103">.NET applications that use date and time information are very diverse and can use that information in several ways.</span></span> <span data-ttu-id="c0904-104">より一般的な日時情報の用途には、次の 1 つ以上が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c0904-104">The more common uses of date and time information include one or more of the following:</span></span>

* <span data-ttu-id="c0904-105">日付のみを反映する (時刻情報は重要ではない)。</span><span class="sxs-lookup"><span data-stu-id="c0904-105">To reflect a date only, so that time information is not important.</span></span>

* <span data-ttu-id="c0904-106">時刻のみを反映する (日付情報は重要ではない)。</span><span class="sxs-lookup"><span data-stu-id="c0904-106">To reflect a time only, so that date information is not important.</span></span>

* <span data-ttu-id="c0904-107">特定の時刻と場所に関連付けられていない抽象日時を反映する (たとえば、国際的チェーンのほとんどのストアは週中の午前 9:00 にオープンする)。</span><span class="sxs-lookup"><span data-stu-id="c0904-107">To reflect an abstract date and time that is not tied to a specific time and place (for example, most stores in an international chain open on weekdays at 9:00 A.M.).</span></span>

* <span data-ttu-id="c0904-108">.NET の外部ソースから日付と時刻の情報を取得するには、通常の日付と時刻の情報が格納に、単純なデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="c0904-108">To retrieve date and time information from sources outside of .NET, typically where date and time information is stored in a simple data type.</span></span>

* <span data-ttu-id="c0904-109">単一の時点を一意かつ明確に識別する。</span><span class="sxs-lookup"><span data-stu-id="c0904-109">To uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="c0904-110">ホスト システムでのみ日付と時刻を明確にする必要があるアプリケーションもあれば、システム全体で明確にする必要があるアプリケーションもあります (つまり、1 つのシステムでシリアル化される日付は有意に逆シリアル化し、世界中のどの場所においても別のシステムで使用できます)。</span><span class="sxs-lookup"><span data-stu-id="c0904-110">Some applications require that a date and time be unambiguous only on the host system; others require that it be unambiguous across systems (that is, a date serialized on one system can be meaningfully deserialized and used on another system anywhere in the world).</span></span>

* <span data-ttu-id="c0904-111">関連する複数の時刻を保持する (要求元の現地時刻やサーバーの Web 要求受信時刻など)。</span><span class="sxs-lookup"><span data-stu-id="c0904-111">To preserve multiple related times (such as the requestor's local time and the server's time of receipt for a Web request).</span></span>

* <span data-ttu-id="c0904-112">日付と時刻の演算を実行する (これにより、おそらく単一時点が一意かつ明確に識別される)。</span><span class="sxs-lookup"><span data-stu-id="c0904-112">To perform date and time arithmetic, possibly with a result that uniquely and unambiguously identifies a single point in time.</span></span>

<span data-ttu-id="c0904-113">.NET を含む、 <xref:System.DateTime>、 <xref:System.DateTimeOffset>、 <xref:System.TimeSpan>、および<xref:System.TimeZoneInfo>型、すべての日付と時刻を使用するアプリケーションの構築に使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0904-113">.NET includes the <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, and <xref:System.TimeZoneInfo> types, all of which can be used to build applications that work with dates and times.</span></span>

> [!NOTE]
> <span data-ttu-id="c0904-114">このトピックには 4 番目の型の <xref:System.TimeZone>については説明されません。その機能は、 <xref:System.TimeZoneInfo> クラスに完全に組み込まれているからです。</span><span class="sxs-lookup"><span data-stu-id="c0904-114">This topic does not discuss a fourth type, <xref:System.TimeZone>, because its functionality is almost entirely incorporated in the <xref:System.TimeZoneInfo> class.</span></span> <span data-ttu-id="c0904-115">開発者は可能な限り、 <xref:System.TimeZoneInfo> クラスの代わりに <xref:System.TimeZone> クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0904-115">Whenever possible, developers should use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

## <a name="the-datetime-structure"></a><span data-ttu-id="c0904-116">DateTime 構造体</span><span class="sxs-lookup"><span data-stu-id="c0904-116">The DateTime structure</span></span>

<span data-ttu-id="c0904-117"><xref:System.DateTime> 値は、特定の日付と時刻を定義します。</span><span class="sxs-lookup"><span data-stu-id="c0904-117">A <xref:System.DateTime> value defines a particular date and time.</span></span> <span data-ttu-id="c0904-118">含まれている、<xref:System.DateTime.Kind%2A>を提供するプロパティに関する限られた情報、タイム ゾーンには日付と時刻が属するです。</span><span class="sxs-lookup"><span data-stu-id="c0904-118">It includes a <xref:System.DateTime.Kind%2A> property that provides limited information about the time zone to which that date and time belongs.</span></span> <span data-ttu-id="c0904-119"><xref:System.DateTimeKind>によって返される値、<xref:System.DateTime.Kind%2A>プロパティを示すかどうか、<xref:System.DateTime>値は現地時刻を表します (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>)、世界協定時刻 (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>)、または指定されていない時刻 (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="c0904-119">The <xref:System.DateTimeKind> value returned by the <xref:System.DateTime.Kind%2A> property indicates whether the <xref:System.DateTime> value represents the local time (<xref:System.DateTimeKind.Local?displayProperty=nameWithType>), Coordinated Universal Time (UTC) (<xref:System.DateTimeKind.Utc?displayProperty=nameWithType>), or an unspecified time (<xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>).</span></span>

<span data-ttu-id="c0904-120"><xref:System.DateTime> 構造体は、次の操作を実行するアプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="c0904-120">The <xref:System.DateTime> structure is suitable for applications that do the following:</span></span>

* <span data-ttu-id="c0904-121">日付のみを使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="c0904-121">Work with dates only.</span></span>

* <span data-ttu-id="c0904-122">時刻のみを使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="c0904-122">Work with times only.</span></span>

* <span data-ttu-id="c0904-123">抽象日時を使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="c0904-123">Work with abstract dates and times.</span></span>

* <span data-ttu-id="c0904-124">タイム ゾーン情報がない日時を使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="c0904-124">Work with dates and times for which time zone information is missing.</span></span>

* <span data-ttu-id="c0904-125">UTC 日時のみを使用するアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="c0904-125">Work with UTC dates and times only.</span></span>

* <span data-ttu-id="c0904-126">SQL データベースなどの .NET では、外部ソースから日時情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="c0904-126">Retrieve date and time information from sources outside of .NET, such as SQL databases.</span></span> <span data-ttu-id="c0904-127">通常、これらのソースは、 <xref:System.DateTime> 構造体と互換性のある単純な形式で日時情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="c0904-127">Typically, these sources store date and time information in a simple format that is compatible with the <xref:System.DateTime> structure.</span></span>

* <span data-ttu-id="c0904-128">日付と時刻の演算を実行しますが、これは一般的な結果に関するものです。</span><span class="sxs-lookup"><span data-stu-id="c0904-128">Perform date and time arithmetic, but are concerned with general results.</span></span> <span data-ttu-id="c0904-129">たとえば、6 カ月を特定の日付と時刻に加算する加算演算では、多くの場合、結果を夏時間に合わせて調整するかどうかは重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="c0904-129">For example, in an addition operation that adds six months to a particular date and time, it is often not important whether the result is adjusted for daylight saving time.</span></span>

<span data-ttu-id="c0904-130">特定の <xref:System.DateTime> 値が UTC を表さない場合、通常、その日付と時刻の値は、あいまいであるか、その移植性に限定されます。</span><span class="sxs-lookup"><span data-stu-id="c0904-130">Unless a particular <xref:System.DateTime> value represents UTC, that date and time value is often ambiguous or limited in its portability.</span></span> <span data-ttu-id="c0904-131">たとえば、 <xref:System.DateTime> 値が現地時刻を表す場合、そのローカル タイム ゾーン内で移植することができます (つまり、同じタイム ゾーンにある別のシステムで値が逆シリアル化されると、その値は明確に単一時点を識別します)。</span><span class="sxs-lookup"><span data-stu-id="c0904-131">For example, if a <xref:System.DateTime> value represents the local time, it is portable within that local time zone (that is, if the value is deserialized on another system in the same time zone, that value still unambiguously identifies a single point in time).</span></span> <span data-ttu-id="c0904-132">ローカル タイム ゾーン外では、その <xref:System.DateTime> 値は複数の意味を持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="c0904-132">Outside the local time zone, that <xref:System.DateTime> value can have multiple interpretations.</span></span> <span data-ttu-id="c0904-133">値の <xref:System.DateTime.Kind%2A> プロパティが <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> の場合、移植性は低くなります。同じタイム ゾーン内であいまいになり、最初にシリアル化したのと同じシステムにおいてさえもあいまいになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c0904-133">If the value's <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType>, it is even less portable: it is now ambiguous within the same time zone and possibly even on the same system on which it was first serialized.</span></span> <span data-ttu-id="c0904-134"><xref:System.DateTime> 値が UTC を表す場合のみ、値が使用されるシステムまたはタイム ゾーンに関係なく、その値は明確に単一時点を識別します。</span><span class="sxs-lookup"><span data-stu-id="c0904-134">Only if a <xref:System.DateTime> value represents UTC does that value unambiguously identify a single point in time regardless of the system or time zone in which the value is used.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0904-135"><xref:System.DateTime> データを保存または共有する際、UTC を使用する必要があり、<xref:System.DateTime> 値の <xref:System.DateTime.Kind%2A> プロパティを <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0904-135">When saving or sharing <xref:System.DateTime> data, UTC should be used and the <xref:System.DateTime> value's <xref:System.DateTime.Kind%2A> property should be set to <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.</span></span>

## <a name="the-datetimeoffset-structure"></a><span data-ttu-id="c0904-136">DateTimeOffset 構造体</span><span class="sxs-lookup"><span data-stu-id="c0904-136">The DateTimeOffset structure</span></span>

<span data-ttu-id="c0904-137"><xref:System.DateTimeOffset> 構造体は、日付と時刻の値、およびその値と UTC との差異を示すオフセットを表します。</span><span class="sxs-lookup"><span data-stu-id="c0904-137">The <xref:System.DateTimeOffset> structure represents a date and time value, together with an offset that indicates how much that value differs from UTC.</span></span> <span data-ttu-id="c0904-138">そのため、値は常に明確に単一時点を識別します。</span><span class="sxs-lookup"><span data-stu-id="c0904-138">Thus, the value always unambiguously identifies a single point in time.</span></span>

<span data-ttu-id="c0904-139"><xref:System.DateTimeOffset> 型には、 <xref:System.DateTime> 型のすべての機能に加え、タイム ゾーンの処理機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c0904-139">The <xref:System.DateTimeOffset> type includes all of the functionality of the <xref:System.DateTime> type along with time zone awareness.</span></span> <span data-ttu-id="c0904-140">これにより、次のようなアプリケーションに適してします。</span><span class="sxs-lookup"><span data-stu-id="c0904-140">This makes it suitable for applications that do the following:</span></span>

* <span data-ttu-id="c0904-141">単一の時点を一意かつ明確に識別する。</span><span class="sxs-lookup"><span data-stu-id="c0904-141">Uniquely and unambiguously identify a single point in time.</span></span> <span data-ttu-id="c0904-142"><xref:System.DateTimeOffset> 型を使用して、「現在」の意味を明確に定義し、トランザクションの時刻を記録し、システム イベントまたはアプリケーション イベントの時刻を記録し、ファイル作成時刻とファイル変更時刻を記録することができます。</span><span class="sxs-lookup"><span data-stu-id="c0904-142">The <xref:System.DateTimeOffset> type can be used to unambiguously define the meaning of "now", to log transaction times, to log the times of system or application events, and to record file creation and modification times.</span></span>

* <span data-ttu-id="c0904-143">一般的な日付と時刻の演算を実行する。</span><span class="sxs-lookup"><span data-stu-id="c0904-143">Perform general date and time arithmetic.</span></span>

* <span data-ttu-id="c0904-144">その時刻が 2 つの別々の値または構造体の 2 つのメンバーである場合、関連する複数の時刻を保持する。</span><span class="sxs-lookup"><span data-stu-id="c0904-144">Preserve multiple related times, as long as those times are stored as two separate values or as two members of a structure.</span></span>

> [!NOTE]
> <span data-ttu-id="c0904-145"><xref:System.DateTimeOffset> 値のこの用途は、 <xref:System.DateTime> 値の用途と比べてはるかに一般的です。</span><span class="sxs-lookup"><span data-stu-id="c0904-145">These uses for <xref:System.DateTimeOffset> values are much more common than those for <xref:System.DateTime> values.</span></span> <span data-ttu-id="c0904-146">その結果、 <xref:System.DateTimeOffset> はアプリケーション開発の既定の日付時刻型と見なされます。</span><span class="sxs-lookup"><span data-stu-id="c0904-146">As a result, <xref:System.DateTimeOffset> should be considered the default date and time type for application development.</span></span>

<span data-ttu-id="c0904-147"><xref:System.DateTimeOffset> 値は特定のタイム ゾーンと関連付けられていませんが、さまざまなタイム ゾーンから派生することができます。</span><span class="sxs-lookup"><span data-stu-id="c0904-147">A <xref:System.DateTimeOffset> value is not tied to a particular time zone, but can originate from any of a variety of time zones.</span></span> <span data-ttu-id="c0904-148">これを説明するために、いくつかの <xref:System.DateTimeOffset> 値 (ローカルの太平洋標準時を含む) が属することができるタイム ゾーンの一覧を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="c0904-148">To illustrate this, the following example lists the time zones to which a number of <xref:System.DateTimeOffset> values (including a local Pacific Standard Time) can belong.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
[!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]

<span data-ttu-id="c0904-149">この例の日付と時刻の値はそれぞれ少なくとも 3 つの異なるタイム ゾーンに属することができることを出力は示しています。</span><span class="sxs-lookup"><span data-stu-id="c0904-149">The output shows that each date and time value in this example can belong to at least three different time zones.</span></span> <span data-ttu-id="c0904-150"><xref:System.DateTimeOffset> 値の 6/10/2007 は、日付と時刻の値が夏時間を表す場合、UTC のそのオフセットは必ずしも元のタイム ゾーンの基本 UTC オフセット、またはその表示名から見つかる UTC のオフセットと一致しないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="c0904-150">The <xref:System.DateTimeOffset> value of 6/10/2007 shows that if a date and time value represents a daylight saving time, its offset from UTC does not even necessarily correspond to the originating time zone's base UTC offset or to the offset from UTC found in its display name.</span></span> <span data-ttu-id="c0904-151">これは、単一の <xref:System.DateTimeOffset> 値はそのタイム ゾーンと密接に関連していないために夏時間との間のタイム ゾーンの遷移を反映することができないことを意味しています。</span><span class="sxs-lookup"><span data-stu-id="c0904-151">This means that, because a single <xref:System.DateTimeOffset> value is not tightly coupled with its time zone, it cannot reflect a time zone's transition to and from daylight saving time.</span></span> <span data-ttu-id="c0904-152">これは特に、日付と時刻の演算を使用して <xref:System.DateTimeOffset> 値を操作する際に問題となる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c0904-152">This can be particularly problematic when date and time arithmetic is used to manipulate a <xref:System.DateTimeOffset> value.</span></span> <span data-ttu-id="c0904-153">(タイム ゾーンの調整規則を考慮に入れた日付と時刻の演算を実行する方法については、「 [Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md)」をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="c0904-153">(For a discussion of how to perform date and time arithmetic in a way that takes account of a time zone's adjustment rules, see [Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md).)</span></span>

## <a name="the-timespan-structure"></a><span data-ttu-id="c0904-154">TimeSpan 構造体</span><span class="sxs-lookup"><span data-stu-id="c0904-154">The TimeSpan structure</span></span>

<span data-ttu-id="c0904-155"><xref:System.TimeSpan> 構造体は、時間間隔を表します。</span><span class="sxs-lookup"><span data-stu-id="c0904-155">The <xref:System.TimeSpan> structure represents a time interval.</span></span> <span data-ttu-id="c0904-156">その 2 つの一般的な用途は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c0904-156">Its two typical uses are:</span></span>

* <span data-ttu-id="c0904-157">2 つの日付と時刻の値の間の時間を反映する。</span><span class="sxs-lookup"><span data-stu-id="c0904-157">Reflecting the time interval between two date and time values.</span></span> <span data-ttu-id="c0904-158">たとえば、ある値から <xref:System.DateTime> 値を減算すると、 <xref:System.TimeSpan> 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="c0904-158">For example, subtracting one <xref:System.DateTime> value from another returns a <xref:System.TimeSpan> value.</span></span>

* <span data-ttu-id="c0904-159">経過時間を測定する。</span><span class="sxs-lookup"><span data-stu-id="c0904-159">Measuring elapsed time.</span></span> <span data-ttu-id="c0904-160">たとえば、<xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType>プロパティから返される、<xref:System.TimeSpan>値の 1 つを呼び出してから経過した時間間隔を反映する、<xref:System.Diagnostics.Stopwatch>経過時間の測定を開始するメソッド。</span><span class="sxs-lookup"><span data-stu-id="c0904-160">For example, the <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=nameWithType> property returns a <xref:System.TimeSpan> value that reflects the time interval that has elapsed since the call to one of the <xref:System.Diagnostics.Stopwatch> methods that begins to measure elapsed time.</span></span>

<span data-ttu-id="c0904-161">値が特定時刻への参照がない値が時間を反映する際、 <xref:System.TimeSpan> 値の代わりに <xref:System.DateTime> 値を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c0904-161">A <xref:System.TimeSpan> value can also be used as a replacement for a <xref:System.DateTime> value when that value reflects a time without reference to a particular time of day.</span></span> <span data-ttu-id="c0904-162">この使用法がに似ていますが、<xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType>と<xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType>プロパティで、返す、<xref:System.TimeSpan>日付への参照なしの時刻を表す値です。</span><span class="sxs-lookup"><span data-stu-id="c0904-162">This usage is similar to the <xref:System.DateTime.TimeOfDay%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=nameWithType> properties, which return a <xref:System.TimeSpan> value that represents the time without reference to a date.</span></span> <span data-ttu-id="c0904-163">たとえば、 <xref:System.TimeSpan> 構造体を使用して、ストアの開店時刻または閉店時刻を反映したり、標準イベントが発生したときの時刻を表したりするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0904-163">For example, the <xref:System.TimeSpan> structure can be used to reflect a store's daily opening or closing time, or it can be used to represent the time at which any regular event occurs.</span></span>

<span data-ttu-id="c0904-164">以下の例では、開店時刻と閉店時刻用の `StoreInfo` オブジェクト、およびストアのタイム ゾーンを表す <xref:System.TimeSpan> オブジェクトを含む <xref:System.TimeZoneInfo> 構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="c0904-164">The following example defines a `StoreInfo` structure that includes <xref:System.TimeSpan> objects for store opening and closing times, as well as a <xref:System.TimeZoneInfo> object that represents the store's time zone.</span></span> <span data-ttu-id="c0904-165">構造体には、 `IsOpenNow` 、 `IsOpenAt`という 2 つのメソッドも含まれます。これは、ローカル タイム ゾーンにいると想定されるユーザーによって指定された時刻にストアがオープンするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c0904-165">The structure also includes two methods, `IsOpenNow` and `IsOpenAt`, that indicates whether the store is open at a time specified by the user, who is assumed to be in the local time zone.</span></span>

[!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
[!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]

<span data-ttu-id="c0904-166">`StoreInfo` 構造体をクライアント コードで次のように使用できます。</span><span class="sxs-lookup"><span data-stu-id="c0904-166">The `StoreInfo` structure can then be used by client code like the following.</span></span>

[!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
[!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]

## <a name="the-timezoneinfo-class"></a><span data-ttu-id="c0904-167">TimeZoneInfo クラス</span><span class="sxs-lookup"><span data-stu-id="c0904-167">The TimeZoneInfo class</span></span>

<span data-ttu-id="c0904-168"><xref:System.TimeZoneInfo> class represents any of the Earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone.</span><span class="sxs-lookup"><span data-stu-id="c0904-168">The <xref:System.TimeZoneInfo> class represents any of the Earth's time zones, and enables the conversion of any date and time in one time zone to its equivalent in another time zone.</span></span> <span data-ttu-id="c0904-169"><xref:System.TimeZoneInfo> クラスにより、日付と時刻を使用して、どの日付と時刻の値も明確に単一時点を識別できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="c0904-169">The <xref:System.TimeZoneInfo> class makes it possible to work with dates and times so that any date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="c0904-170"><xref:System.TimeZoneInfo> クラスを拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="c0904-170">The <xref:System.TimeZoneInfo> class is also extensible.</span></span> <span data-ttu-id="c0904-171">Windows システムで提供され、レジストリで定義されているタイム ゾーン情報に依存していますが、カスタムのタイム ゾーンの作成もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c0904-171">Although it depends on time zone information provided for Windows systems and defined in the registry, it supports the creation of custom time zones.</span></span> <span data-ttu-id="c0904-172">また、タイム ゾーン情報のシリアル化と逆シリアル化もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c0904-172">It also supports the serialization and deserialization of time zone information.</span></span>

<span data-ttu-id="c0904-173">場合によっては、 <xref:System.TimeZoneInfo> クラスをフル活用するために、開発作業をさらに実行する必要が生じることもあります。</span><span class="sxs-lookup"><span data-stu-id="c0904-173">In some cases, taking full advantage of the <xref:System.TimeZoneInfo> class may require further development work.</span></span> <span data-ttu-id="c0904-174">日付と時刻の値がタイム ゾーンを属していることがさらに機能を含む密結合されていない場合は、必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0904-174">If date and time values are not tightly coupled with the time zones to which they belong, further work is required.</span></span> <span data-ttu-id="c0904-175">日付とその関連タイム ゾーンの時刻をリンクするメカニズムを提供するアプリケーション、しない限り、そのタイム ゾーンから解除するには、特定の日付と時刻の値に簡単です。</span><span class="sxs-lookup"><span data-stu-id="c0904-175">Unless your application provides some mechanism for linking a date and time with its associated time zone, it's easy for a particular date and time value to become disassociated from its time zone.</span></span> <span data-ttu-id="c0904-176">この情報をリンクする 1 つの方法は、日付と時刻の値とその関連タイム ゾーン オブジェクトの両方を含むクラスまたは構造体を定義するという方法です。</span><span class="sxs-lookup"><span data-stu-id="c0904-176">One method of linking this information is to define a class or structure that contains both the date and time value and its associated time zone object.</span></span>

<span data-ttu-id="c0904-177">日付と時刻のオブジェクトをインスタンスするときにその日付と時刻の値が属するタイム ゾーンがわかっている場合のみ、.NET でタイム ゾーンのサポートを利用できます。</span><span class="sxs-lookup"><span data-stu-id="c0904-177">Taking advantage of time zone support in .NET is possible only if the time zone to which a date and time value belongs is known when that date and time object is instantiated.</span></span> <span data-ttu-id="c0904-178">特に Web またはネットワーク アプリケーションでは、これは該当しません。</span><span class="sxs-lookup"><span data-stu-id="c0904-178">This is often not the case, particularly in Web or network applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0904-179">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0904-179">See also</span></span>

[<span data-ttu-id="c0904-180">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="c0904-180">Dates, times, and time zones</span></span>](../../../docs/standard/datetime/index.md)
