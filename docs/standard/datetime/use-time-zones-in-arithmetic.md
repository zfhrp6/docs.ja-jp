---
title: '方法: 日付と時刻の演算でタイム ゾーンを使用します。'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], adding and subtracting
ms.assetid: 83dd898d-1338-415d-8cd6-445377ab7871
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f9d326750cdef96be1aa6055d46b4ac08ec7a0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-time-zones-in-date-and-time-arithmetic"></a><span data-ttu-id="1f6dc-102">方法: 日付と時刻の演算でタイム ゾーンを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-102">How to: Use time zones in date and time arithmetic</span></span>

<span data-ttu-id="1f6dc-103">通常とを実行して日付時刻の算術演算を使用して<xref:System.DateTime>または<xref:System.DateTimeOffset>結果の値は、タイム ゾーン調整規則が反映されません。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-103">Ordinarily, when you perform date and time arithmetic using <xref:System.DateTime> or <xref:System.DateTimeOffset> values, the result does not reflect any time zone adjustment rules.</span></span> <span data-ttu-id="1f6dc-104">日付と時刻の値のタイム ゾーンが明確に識別する場合でもこれが true (場合など、<xref:System.DateTime.Kind%2A>プロパティに設定されている<xref:System.DateTimeKind.Local>)。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-104">This is true even when the time zone of the date and time value is clearly identifiable (for example, when the <xref:System.DateTime.Kind%2A> property is set to <xref:System.DateTimeKind.Local>).</span></span> <span data-ttu-id="1f6dc-105">このトピックでは、特定のタイム ゾーンに属している日付と時刻の値に対する算術演算を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-105">This topic shows how to perform arithmetic operations on date and time values that belong to a particular time zone.</span></span> <span data-ttu-id="1f6dc-106">算術演算の結果には、タイム ゾーンの調整規則が反映されます。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-106">The results of the arithmetic operations will reflect the time zone's adjustment rules.</span></span>

### <a name="to-apply-adjustment-rules-to-date-and-time-arithmetic"></a><span data-ttu-id="1f6dc-107">日付と時刻の演算に調整規則を適用するには</span><span class="sxs-lookup"><span data-stu-id="1f6dc-107">To apply adjustment rules to date and time arithmetic</span></span>

1. <span data-ttu-id="1f6dc-108">なんらかの方法を実装して、日付と時刻の値と、その値が属するタイム ゾーンを密接に結び付けます。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-108">Implement some method of closely coupling a date and time value with the time zone to which it belongs.</span></span> <span data-ttu-id="1f6dc-109">たとえば、日付と時刻の値とそのタイム ゾーンの両方を含む構造体を宣言します。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-109">For example, declare a structure that includes both the date and time value and its time zone.</span></span> <span data-ttu-id="1f6dc-110">次の例にリンクするこの方法を使用して、<xref:System.DateTime>そのタイム ゾーンを持つ値です。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-110">The following example uses this approach to link a <xref:System.DateTime> value with its time zone.</span></span>

   [!code-csharp[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#6)]
   [!code-vb[System.DateTimeOffset.Conceptual#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#6)]

2. <span data-ttu-id="1f6dc-111">呼び出して、時刻を世界協定時刻 (UTC) を変換、<xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>メソッドまたは<xref:System.TimeZoneInfo.ConvertTime%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-111">Convert a time to Coordinated Universal Time (UTC) by calling either the <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> method or the <xref:System.TimeZoneInfo.ConvertTime%2A> method.</span></span>

3. <span data-ttu-id="1f6dc-112">UTC 時刻で算術演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-112">Perform the arithmetic operation on the UTC time.</span></span>

4. <span data-ttu-id="1f6dc-113">時間を UTC から呼び出すことによって、元の時刻のタイム ゾーンに変換、<xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-113">Convert the time from UTC to the original time's associated time zone by calling the <xref:System.TimeZoneInfo.ConvertTime%28System.DateTime%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span>

## <a name="example"></a><span data-ttu-id="1f6dc-114">例</span><span class="sxs-lookup"><span data-stu-id="1f6dc-114">Example</span></span>

<span data-ttu-id="1f6dc-115">次の例では、中部標準時の 2008 年 3 月 9 日午前 1 時 30 分に、2 時間 30 分を</span><span class="sxs-lookup"><span data-stu-id="1f6dc-115">The following example adds two hours and thirty minutes to March 9, 2008, at 1:30 A.M.</span></span> <span data-ttu-id="1f6dc-116">加えます。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-116">Central Standard Time.</span></span> <span data-ttu-id="1f6dc-117">夏時間へのタイム ゾーンの切り替えは、30 分後の 2008 年 3 月 9 日午前 2 時に</span><span class="sxs-lookup"><span data-stu-id="1f6dc-117">The time zone's transition to daylight saving time occurs thirty minutes later, at 2:00 A.M.</span></span> <span data-ttu-id="1f6dc-118">発生します。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-118">on March 9, 2008.</span></span> <span data-ttu-id="1f6dc-119">この例は前に示した 4 つの手順に従うため、結果は正しい時刻である 2008 年 3 月 9 日午前 5 時に</span><span class="sxs-lookup"><span data-stu-id="1f6dc-119">Because the example follows the four steps listed in the previous section, it correctly reports the resulting time as 5:00 A.M.</span></span> <span data-ttu-id="1f6dc-120">前のコードと似ています。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-120">on March 9, 2008.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual8.cs#8)]
[!code-vb[System.DateTimeOffset.Conceptual#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual8.vb#8)]

<span data-ttu-id="1f6dc-121">両方<xref:System.DateTime>と<xref:System.DateTimeOffset>値関連付けが解除され、タイム ゾーンが属している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-121">Both <xref:System.DateTime> and <xref:System.DateTimeOffset> values are disassociated from any time zone to which they might belong.</span></span> <span data-ttu-id="1f6dc-122">タイム ゾーンの調整規則が自動的に適用されるような方法で日付と時刻の演算を実行するには、日付と時刻の値の属するタイム ゾーンがすぐに識別できる状態でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-122">To perform date and time arithmetic in a way that automatically applies a time zone's adjustment rules, the time zone to which any date and time value belongs must be immediately identifiable.</span></span> <span data-ttu-id="1f6dc-123">つまり、日時と関連付けられているタイム ゾーンを密に結合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-123">This means that a date and time and its associated time zone must be tightly coupled.</span></span> <span data-ttu-id="1f6dc-124">これは、次のようないくつかの方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-124">There are several ways to do this, which include the following:</span></span>

* <span data-ttu-id="1f6dc-125">アプリケーションで使用されるすべての時刻が、特定のタイム ゾーンに属するものと仮定します。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-125">Assume that all times used in an application belong to a particular time zone.</span></span> <span data-ttu-id="1f6dc-126">この方法は、適切な場合もありますが、柔軟性が限られ、移植性が制限される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-126">Although appropriate in some cases, this approach offers limited flexibility and possibly limited portability.</span></span>

* <span data-ttu-id="1f6dc-127">日時と関連付けられているタイム ゾーンを型のフィールドとして組み込むことで、両者を密に結合する型を定義します。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-127">Define a type that tightly couples a date and time with its associated time zone by including both as fields of the type.</span></span> <span data-ttu-id="1f6dc-128">コード例ではこの方法を使用して、日時とタイム ゾーンを 2 つのメンバー フィールドに格納する構造体を定義しています。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-128">This approach is used in the code example, which defines a structure to store the date and time and the time zone in two member fields.</span></span>

<span data-ttu-id="1f6dc-129">例での算術演算を実行する方法を示しています<xref:System.DateTime>値を結果にタイム ゾーン調整規則が適用されるようにします。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-129">The example illustrates how to perform arithmetic operations on <xref:System.DateTime> values so that time zone adjustment rules are applied to the result.</span></span> <span data-ttu-id="1f6dc-130">ただし、<xref:System.DateTimeOffset>値を簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-130">However, <xref:System.DateTimeOffset> values can be used just as easily.</span></span> <span data-ttu-id="1f6dc-131">どの例では元のコード可能性がありますを使用する次の例を示しています<xref:System.DateTimeOffset>の代わりに<xref:System.DateTime>値。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-131">The following example illustrates how the code in the original example might be adapted to use <xref:System.DateTimeOffset> instead of <xref:System.DateTime> values.</span></span>

[!code-csharp[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual6.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual6.vb#7)]

<span data-ttu-id="1f6dc-132">この追加を実行するだけの場合、<xref:System.DateTimeOffset>最初 UTC に変換する、結果、適切な時点の反映しますが、そのオフセットは反映されませんを指定されたタイム ゾーンの時点のなしの値します。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-132">Note that if this addition is simply performed on the <xref:System.DateTimeOffset> value without first converting it to UTC, the result reflects the correct point in time but its offset does not reflect that of the designated time zone for that time.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="1f6dc-133">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="1f6dc-133">Compiling the code</span></span>

<span data-ttu-id="1f6dc-134">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-134">This example requires:</span></span>

* <span data-ttu-id="1f6dc-135">される System.Core.dll への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-135">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="1f6dc-136"><xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要です)。</span><span class="sxs-lookup"><span data-stu-id="1f6dc-136">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="1f6dc-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f6dc-137">See also</span></span>

<span data-ttu-id="1f6dc-138">[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[日付と時刻の算術演算を実行します。](../../../docs/standard/datetime/performing-arithmetic-operations.md)</span><span class="sxs-lookup"><span data-stu-id="1f6dc-138">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md)</span></span>
