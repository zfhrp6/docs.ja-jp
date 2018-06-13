---
title: '方法: 調整規則のないタイム ゾーンを作成'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], adjustment rule
- time zones [.NET Framework], creating
- adjustment rule [.NET Framework]
ms.assetid: a6af8647-7893-4f29-95a9-d94c65a6e8dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 214e3bca811f87f4b8367b459564449d16e7c289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572903"
---
# <a name="how-to-create-time-zones-without-adjustment-rules"></a><span data-ttu-id="e946c-102">方法: 調整規則のないタイム ゾーンを作成</span><span class="sxs-lookup"><span data-stu-id="e946c-102">How to: Create time zones without adjustment rules</span></span>

<span data-ttu-id="e946c-103">アプリケーションで必要とされる正確なタイム ゾーン情報は、いくつかの原因の特定のシステムに存在していない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e946c-103">The precise time zone information that is required by an application may not be present on a particular system for several reasons:</span></span>

* <span data-ttu-id="e946c-104">タイム ゾーンはローカル システムのレジストリで定義されていません。</span><span class="sxs-lookup"><span data-stu-id="e946c-104">The time zone has never been defined in the local system's registry.</span></span>

* <span data-ttu-id="e946c-105">タイム ゾーンに関するデータが変更されたか、レジストリから削除されました。</span><span class="sxs-lookup"><span data-stu-id="e946c-105">Data about the time zone has been modified or removed from the registry.</span></span>

* <span data-ttu-id="e946c-106">タイム ゾーンが存在しますが、過去の特定の期間のタイム ゾーンの調整に関する正確な情報はありません。</span><span class="sxs-lookup"><span data-stu-id="e946c-106">The time zone exists but does not have accurate information about time zone adjustments for a particular historic period.</span></span>

<span data-ttu-id="e946c-107">このような場合を呼び出すことができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドをアプリケーションに必要なタイム ゾーンを定義します。</span><span class="sxs-lookup"><span data-stu-id="e946c-107">In these cases, you can call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method to define the time zone required by your application.</span></span> <span data-ttu-id="e946c-108">このメソッドのオーバー ロードを使用して、調整規則の有無は、タイム ゾーンを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e946c-108">You can use the overloads of this method to create a time zone with or without adjustment rules.</span></span> <span data-ttu-id="e946c-109">タイム ゾーンが夏時間をサポートする場合は、いずれかの固定または浮動小数点の調整ルールの調整を定義できます。</span><span class="sxs-lookup"><span data-stu-id="e946c-109">If the time zone supports daylight saving time, you can define adjustments with either fixed or floating adjustment rules.</span></span> <span data-ttu-id="e946c-110">(これらの用語の定義、「タイム ゾーンの用語」のセクションを参照してください。[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="e946c-110">(For definitions of these terms, see the "Time Zone Terminology" section in [Time zone overview](../../../docs/standard/datetime/time-zone-overview.md).)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e946c-111">呼び出して作成されたカスタムのタイム ゾーン、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドは、レジストリに追加されません。</span><span class="sxs-lookup"><span data-stu-id="e946c-111">Custom time zones created by calling the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method are not added to the registry.</span></span> <span data-ttu-id="e946c-112">代わりに、によって返されるオブジェクトの参照を介してのみアクセスすることができます、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>メソッドの呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="e946c-112">Instead, they can be accessed only through the object reference returned by the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method call.</span></span>

<span data-ttu-id="e946c-113">このトピックでは、調整規則のないタイム ゾーンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e946c-113">This topic shows how to create a time zone without adjustment rules.</span></span> <span data-ttu-id="e946c-114">夏時間の調整規則をサポートするタイム ゾーンを作成するを参照してください。[する方法: 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)です。</span><span class="sxs-lookup"><span data-stu-id="e946c-114">To create a time zone that supports daylight saving time adjustment rules, see [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).</span></span>

### <a name="to-create-a-time-zone-without-adjustment-rules"></a><span data-ttu-id="e946c-115">調整規則のないタイム ゾーンを作成するには</span><span class="sxs-lookup"><span data-stu-id="e946c-115">To create a time zone without adjustment rules</span></span>

1. <span data-ttu-id="e946c-116">タイム ゾーンの表示名を定義します。</span><span class="sxs-lookup"><span data-stu-id="e946c-116">Define the time zone's display name.</span></span>

   <span data-ttu-id="e946c-117">表示名に依存して標準形式にタイム ゾーンのオフセット世界協定時刻 (UTC) からかっこで囲まれて、その後に、1 つまたは複数のタイム ゾーン、または 1 つの都市以上、cou のタイム ゾーンを識別する文字列ntries またはタイム ゾーン内の領域。</span><span class="sxs-lookup"><span data-stu-id="e946c-117">The display name follows a fairly standard format in which the time zone's offset from Coordinated Universal Time (UTC) is enclosed in parentheses and is followed by a string that identifies the time zone, one or more of the cities in the time zone, or one or more of the countries or regions in the time zone.</span></span>

2. <span data-ttu-id="e946c-118">タイム ゾーンの標準時の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="e946c-118">Define the name of the time zone's standard time.</span></span> <span data-ttu-id="e946c-119">通常、この文字列は、タイム ゾーンの識別子としても使用します。</span><span class="sxs-lookup"><span data-stu-id="e946c-119">Typically, this string is also used as the time zone's identifier.</span></span>

3. <span data-ttu-id="e946c-120">タイム ゾーンの標準の名前とは異なる id を使用する場合は、タイム ゾーン id を定義します。</span><span class="sxs-lookup"><span data-stu-id="e946c-120">If you want to use a different identifier than the time zone's standard name, define the time zone identifier.</span></span>

4. <span data-ttu-id="e946c-121">インスタンスを作成、 <xref:System.TimeSpan> UTC からのタイム ゾーンのオフセットを定義するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e946c-121">Instantiate a <xref:System.TimeSpan> object that defines the time zone's offset from UTC.</span></span> <span data-ttu-id="e946c-122">タイム ゾーンの時刻 (utc) より後に、正の値のオフセットを持っています。</span><span class="sxs-lookup"><span data-stu-id="e946c-122">Time zones with times that are later than UTC have a positive offset.</span></span> <span data-ttu-id="e946c-123">タイム ゾーンの時刻は UTC よりも前に、負のオフセットを持っています。</span><span class="sxs-lookup"><span data-stu-id="e946c-123">Time zones with times that are earlier than UTC have a negative offset.</span></span>

5. <span data-ttu-id="e946c-124">呼び出す、<xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType>新しいタイム ゾーンをインスタンス化するメソッド。</span><span class="sxs-lookup"><span data-stu-id="e946c-124">Call the <xref:System.TimeZoneInfo.CreateCustomTimeZone%28System.String%2CSystem.TimeSpan%2CSystem.String%2CSystem.String%29?displayProperty=nameWithType> method to instantiate the new time zone.</span></span>

## <a name="example"></a><span data-ttu-id="e946c-125">例</span><span class="sxs-lookup"><span data-stu-id="e946c-125">Example</span></span>

<span data-ttu-id="e946c-126">次の例では、調整規則がない、南極のモーソンをカスタム タイム ゾーンを定義します。</span><span class="sxs-lookup"><span data-stu-id="e946c-126">The following example defines a custom time zone for Mawson, Antarctica, which has no adjustment rules.</span></span>

[!code-csharp[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#1)]
[!code-vb[System.TimeZone2.CreateTimeZone#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#1)]

<span data-ttu-id="e946c-127">割り当てられた文字列、<xref:System.TimeZoneInfo.DisplayName%2A>プロパティ (utc) からのタイム ゾーンのオフセットがタイム ゾーンのわかりやすい説明によってその後に、標準形式に依存します。</span><span class="sxs-lookup"><span data-stu-id="e946c-127">The string assigned to the <xref:System.TimeZoneInfo.DisplayName%2A> property follows a standard format in which the time zone's offset from UTC is followed by a friendly description of the time zone.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="e946c-128">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e946c-128">Compiling the code</span></span>

<span data-ttu-id="e946c-129">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e946c-129">This example requires:</span></span>

* <span data-ttu-id="e946c-130">される System.Core.dll への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="e946c-130">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="e946c-131">次の名前空間は、インポートします。</span><span class="sxs-lookup"><span data-stu-id="e946c-131">That the following namespaces be imported:</span></span>

  [!code-csharp[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/cs/System.TimeZone2.CreateTimeZone.cs#6)]
  [!code-vb[System.TimeZone2.CreateTimeZone#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.CreateTimeZone/vb/System.TimeZone2.CreateTimeZone.vb#6)]

## <a name="see-also"></a><span data-ttu-id="e946c-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="e946c-132">See also</span></span>

<span data-ttu-id="e946c-133">[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)
[する方法: 調整規則のあるタイム ゾーンを作成します。](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span><span class="sxs-lookup"><span data-stu-id="e946c-133">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md)
[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)</span></span>
