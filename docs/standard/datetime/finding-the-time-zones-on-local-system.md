---
title: "ローカル システムで定義されているタイム ゾーンの検索"
description: "ローカル システムで定義されているタイム ゾーンの検索"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/15/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3a6ee323-f3cf-486d-aa0c-103931f1eba9
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: e61017e2a0e26295c3be7e8265674b1a5d2ae5a3
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="57f3f-104">ローカル システムで定義されているタイム ゾーンの検索</span><span class="sxs-lookup"><span data-stu-id="57f3f-104">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="57f3f-105">[System.TimeZoneInfo](xref:System.TimeZoneInfo) クラスは、パブリック コンストラクターを公開しません。</span><span class="sxs-lookup"><span data-stu-id="57f3f-105">The [System.TimeZoneInfo](xref:System.TimeZoneInfo) class does not expose a public constructor.</span></span> <span data-ttu-id="57f3f-106">そのため、`new` キーワードを使用して新しい [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="57f3f-106">As a result, the `new` keyword cannot be used to create a new [TimeZoneInfo](xref:System.TimeZoneInfo) object.</span></span> <span data-ttu-id="57f3f-107">[TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをインスタンス化するには、代わりに、定義済みのタイム ゾーンの情報をオペレーティング システムから取得します。</span><span class="sxs-lookup"><span data-stu-id="57f3f-107">Instead, [TimeZoneInfo](xref:System.TimeZoneInfo) objects are instantiated by retrieving information on predefined time zones from the operating system.</span></span> <span data-ttu-id="57f3f-108">このトピックでは、オペレーティング システムによって格納されているデータからタイム ゾーンをインスタンス化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="57f3f-108">This topic discusses instantiating a time zone from data stored by the operating system.</span></span> <span data-ttu-id="57f3f-109">また、[TimeZoneInfo](xref:System.TimeZoneInfo) クラスの `static` (Visual Basic では `Shared`) プロパティを使用すると、世界協定時刻 (UTC: Coordinated Universal Time) およびローカル タイム ゾーンにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="57f3f-109">In addition, `static` (`Shared` in Visual Basic) properties of the [TimeZoneInfo](xref:System.TimeZoneInfo) class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="57f3f-110">個別のタイム ゾーンへのアクセス</span><span class="sxs-lookup"><span data-stu-id="57f3f-110">Accessing Individual Time Zones</span></span>

<span data-ttu-id="57f3f-111">[TimeZoneInfo](xref:System.TimeZoneInfo) クラスには、UTC 時刻とローカル タイム ゾーンを表す&2; つの定義済みタイム ゾーン オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="57f3f-111">The [TimeZoneInfo](xref:System.TimeZoneInfo) class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="57f3f-112">これらは、それぞれ [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) プロパティと [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) プロパティから取得できます。</span><span class="sxs-lookup"><span data-stu-id="57f3f-112">They are available from the [TimeZoneInfo.Utc](xref:System.TimeZoneInfo.Utc) and [TimeZoneInfo.Local](xref:System.TimeZoneInfo.Local) properties, respectively.</span></span> <span data-ttu-id="57f3f-113">UTC またはローカル タイム ゾーンにアクセスする方法については、「[方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](access-utc-and-local.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f3f-113">For instructions on accessing the UTC or local time zones, see [How to: access the predefined UTC and local time zone objects](access-utc-and-local.md).</span></span> 

<span data-ttu-id="57f3f-114">また、オペレーティング システムで定義されているタイム ゾーンを表す [TimeZoneInfo](xref:System.TimeZoneInfo) オブジェクトをインスタンス化することもできます。</span><span class="sxs-lookup"><span data-stu-id="57f3f-114">You can also instantiate a [TimeZoneInfo](xref:System.TimeZoneInfo) object that represents any time zone defined by the operating system.</span></span> <span data-ttu-id="57f3f-115">特定のタイム ゾーン オブジェクトをインスタンス化する方法については、「[方法: TimeZoneInfo オブジェクトをインスタンス化する](instantiate-time-zone-info.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f3f-115">For instructions on instantiating a specific time zone object, see [How to: instantiate a TimeZoneInfo object](instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="57f3f-116">タイム ゾーン ID</span><span class="sxs-lookup"><span data-stu-id="57f3f-116">Time Zone Identifiers</span></span>

<span data-ttu-id="57f3f-117">タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。</span><span class="sxs-lookup"><span data-stu-id="57f3f-117">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="57f3f-118">ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。</span><span class="sxs-lookup"><span data-stu-id="57f3f-118">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="57f3f-119">ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="57f3f-119">In most cases, its value corresponds to the [TimeZoneInfo.StandardName](xref:System.TimeZoneInfo.StandardName) property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="57f3f-120">ただし、例外もあります。</span><span class="sxs-lookup"><span data-stu-id="57f3f-120">However, there are exceptions.</span></span> <span data-ttu-id="57f3f-121">有効な ID を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、それに対応するタイム ゾーン ID を記録することです。</span><span class="sxs-lookup"><span data-stu-id="57f3f-121">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span> <span data-ttu-id="57f3f-122">タイム ゾーンを列挙する方法については、「[方法: コンピューター上に存在するタイム ゾーンを列挙する](enumerate-time-zones.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f3f-122">For instructions on enumerating time zones, see [How to: enumerate time zones present on a computer](enumerate-time-zones.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57f3f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="57f3f-123">See Also</span></span>

[<span data-ttu-id="57f3f-124">日付、時刻およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="57f3f-124">Dates, times, and time zones</span></span>](index.md)

[<span data-ttu-id="57f3f-125">方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする</span><span class="sxs-lookup"><span data-stu-id="57f3f-125">How to: access the predefined UTC and local time zone objects</span></span>](access-utc-and-local.md)

[<span data-ttu-id="57f3f-126">方法: TimeZoneInfo オブジェクトをインスタンス化する</span><span class="sxs-lookup"><span data-stu-id="57f3f-126">How to: instantiate a TimeZoneInfo object</span></span>](instantiate-time-zone-info.md)

[<span data-ttu-id="57f3f-127">方法: コンピューター上に存在するタイム ゾーンを列挙する</span><span class="sxs-lookup"><span data-stu-id="57f3f-127">How to: enumerate time zones present on a computer</span></span>](enumerate-time-zones.md)

[<span data-ttu-id="57f3f-128">タイム ゾーン間での時刻の変換</span><span class="sxs-lookup"><span data-stu-id="57f3f-128">Converting times between time zones</span></span>](converting-between-time-zones.md)
