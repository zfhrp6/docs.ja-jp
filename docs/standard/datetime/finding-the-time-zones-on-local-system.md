---
title: ローカル システムで定義されているタイム ゾーンの検索
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb4196ff53a5c26be7c46a8168a30044836af2cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572763"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a><span data-ttu-id="399ad-102">ローカル システムで定義されているタイム ゾーンの検索</span><span class="sxs-lookup"><span data-stu-id="399ad-102">Finding the time zones defined on a local system</span></span>

<span data-ttu-id="399ad-103"><xref:System.TimeZoneInfo> クラスは、パブリック コンストラクターを公開しません。</span><span class="sxs-lookup"><span data-stu-id="399ad-103">The <xref:System.TimeZoneInfo> class does not expose a public constructor.</span></span> <span data-ttu-id="399ad-104">そのため、`new` キーワードを使用して新しい <xref:System.TimeZoneInfo> オブジェクトを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="399ad-104">As a result, the `new` keyword cannot be used to create a new <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="399ad-105"><xref:System.TimeZoneInfo> オブジェクトをインスタンス化するには、代わりに、定義済みのタイム ゾーンの情報をレジストリから取得するか、カスタム タイム ゾーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="399ad-105">Instead, <xref:System.TimeZoneInfo> objects are instantiated either by retrieving information on predefined time zones from the registry or by creating a custom time zone.</span></span> <span data-ttu-id="399ad-106">このトピックでは、レジストリに格納されているデータからタイム ゾーンをインスタンス化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="399ad-106">This topic discusses instantiating a time zone from data stored in the registry.</span></span> <span data-ttu-id="399ad-107">また、<xref:System.TimeZoneInfo> クラスの `static` (Visual Basic では `shared`) プロパティを使用すると、世界協定時刻 (UTC: Coordinated Universal Time) およびローカル タイム ゾーンにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="399ad-107">In addition, `static` (`shared` in Visual Basic) properties of the <xref:System.TimeZoneInfo> class provide access to Coordinated Universal Time (UTC) and the local time zone.</span></span>

> [!NOTE]
> <span data-ttu-id="399ad-108">レジストリで定義されていないタイム ゾーンの場合は、<xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> メソッドのオーバーロードを呼び出すことによりカスタム タイム ゾーンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="399ad-108">For time zones that are not defined in the registry, you can create custom time zones by calling the overloads of the <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> method.</span></span> <span data-ttu-id="399ad-109">については、カスタム タイム ゾーンを作成する、[する方法: 調整規則のないタイム ゾーンを作成](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md)と[する方法: 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="399ad-109">Creating a custom time zone is discussed in the [How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) and [How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) topics.</span></span> <span data-ttu-id="399ad-110">さらに、<xref:System.TimeZoneInfo.FromSerializedString%2A> メソッドを使用して、シリアル化された文字列から復元することにより、<xref:System.TimeZoneInfo> オブジェクトをインスタンス化することもできます。</span><span class="sxs-lookup"><span data-stu-id="399ad-110">In addition, you can instantiate a <xref:System.TimeZoneInfo> object by restoring it from a serialized string with the <xref:System.TimeZoneInfo.FromSerializedString%2A> method.</span></span> <span data-ttu-id="399ad-111">シリアル化と逆シリアル化、<xref:System.TimeZoneInfo>オブジェクトは、後ほど、[する方法: 埋め込みリソースにタイム ゾーンを保存](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)と[する方法: 埋め込みリソースからタイム ゾーンを復元](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="399ad-111">Serializing and deserializing a <xref:System.TimeZoneInfo> object is discussed in the [How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) and [How to: Restore Time Zones from an Embedded Resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) topics.</span></span>

## <a name="accessing-individual-time-zones"></a><span data-ttu-id="399ad-112">個別のタイム ゾーンへのアクセス</span><span class="sxs-lookup"><span data-stu-id="399ad-112">Accessing individual time zones</span></span>

<span data-ttu-id="399ad-113"><xref:System.TimeZoneInfo> クラスには、UTC 時刻とローカル タイム ゾーンを表す 2 つの定義済みタイム ゾーン オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="399ad-113">The <xref:System.TimeZoneInfo> class provides two predefined time zone objects that represent the UTC time and the local time zone.</span></span> <span data-ttu-id="399ad-114">これらは、それぞれ <xref:System.TimeZoneInfo.Utc%2A> プロパティと <xref:System.TimeZoneInfo.Local%2A> プロパティから取得できます。</span><span class="sxs-lookup"><span data-stu-id="399ad-114">They are available from the <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A> properties, respectively.</span></span> <span data-ttu-id="399ad-115">UTC またはローカル タイム ゾーンへのアクセス方法の詳細については、次を参照してください。[する方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトをアクセス](../../../docs/standard/datetime/access-utc-and-local.md)です。</span><span class="sxs-lookup"><span data-stu-id="399ad-115">For instructions on accessing the UTC or local time zones, see [How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md).</span></span>

<span data-ttu-id="399ad-116">また、レジストリで定義されているタイム ゾーンを表す <xref:System.TimeZoneInfo> オブジェクトをインスタンス化することもできます。</span><span class="sxs-lookup"><span data-stu-id="399ad-116">You can also instantiate a <xref:System.TimeZoneInfo> object that represents any time zone defined in the registry.</span></span> <span data-ttu-id="399ad-117">特定のタイム ゾーン オブジェクトをインスタンス化する方法の詳細については、次を参照してください。[する方法: TimeZoneInfo オブジェクトをインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)です。</span><span class="sxs-lookup"><span data-stu-id="399ad-117">For instructions on instantiating a specific time zone object, see [How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md).</span></span>

## <a name="time-zone-identifiers"></a><span data-ttu-id="399ad-118">タイム ゾーン id</span><span class="sxs-lookup"><span data-stu-id="399ad-118">Time zone identifiers</span></span>

<span data-ttu-id="399ad-119">タイム ゾーン ID は、タイム ゾーンを一意に識別するキー フィールドです。</span><span class="sxs-lookup"><span data-stu-id="399ad-119">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="399ad-120">ほとんどのキーは比較的短いですが、タイム ゾーン ID はいくぶん長めです。</span><span class="sxs-lookup"><span data-stu-id="399ad-120">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="399ad-121">ほとんどの場合、ID の値は、タイム ゾーンの標準時刻の名前を表すために使用される <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> プロパティに対応します。</span><span class="sxs-lookup"><span data-stu-id="399ad-121">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> property, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="399ad-122">ただし、例外もあります。</span><span class="sxs-lookup"><span data-stu-id="399ad-122">However, there are exceptions.</span></span> <span data-ttu-id="399ad-123">有効な ID を確実に指定する最良の方法は、システムで使用できるタイム ゾーンを列挙し、それに対応するタイム ゾーン ID を記録することです。</span><span class="sxs-lookup"><span data-stu-id="399ad-123">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note their associated identifiers.</span></span>

## <a name="see-also"></a><span data-ttu-id="399ad-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="399ad-124">See also</span></span>

<span data-ttu-id="399ad-125">[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[する方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトをアクセス](../../../docs/standard/datetime/access-utc-and-local.md)
[する方法: TimeZoneInfo オブジェクトをインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[タイム ゾーン間で時刻の変換](../../../docs/standard/datetime/converting-between-time-zones.md)</span><span class="sxs-lookup"><span data-stu-id="399ad-125">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)
[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md)</span></span>
