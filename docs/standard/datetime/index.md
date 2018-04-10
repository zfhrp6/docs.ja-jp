---
title: 日付、時刻、およびタイム ゾーン
ms.custom: ''
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 47681f129c428cdae2be5e493fc6ac31719cab28
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="567a4-102">日付、時刻、およびタイム ゾーン</span><span class="sxs-lookup"><span data-stu-id="567a4-102">Dates, times, and time zones</span></span>

<span data-ttu-id="567a4-103">.NET は基本的な <xref:System.DateTime> 構造体だけでなく、タイム ゾーンでの作業をサポートする次のクラスも提供しています。</span><span class="sxs-lookup"><span data-stu-id="567a4-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="567a4-104">システムのローカル タイム ゾーンおよび世界協定時刻 (UTC) ゾーンで作業を行うには、このクラスを使用します。<xref:System.TimeZone> クラスの機能は、<xref:System.TimeZoneInfo> クラスによって大幅に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="567a4-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="567a4-105">このクラスを使用すると、システムに事前に定義されている任意のタイム ゾーンを処理し、新しいタイム ゾーンを作成して、1 つのタイム ゾーンから別のタイム ゾーンに日付/時刻を簡単に変換できます。</span><span class="sxs-lookup"><span data-stu-id="567a4-105">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="567a4-106">新規に開発を行う場合は、<xref:System.TimeZoneInfo> クラスではなく、<xref:System.TimeZone> クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="567a4-106">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="567a4-107">UTC からのオフセット (つまり時差) がわかっている日付および時刻で作業を行う場合は、この構造体を使用します。</span><span class="sxs-lookup"><span data-stu-id="567a4-107">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="567a4-108"><xref:System.DateTimeOffset> 構造体は、日付および時刻の値と、その時刻の UTC からのオフセットを組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="567a4-108">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="567a4-109">UTC との関係により、個々の日付と時刻の値によって具体的な日時が明確に特定されます。</span><span class="sxs-lookup"><span data-stu-id="567a4-109">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="567a4-110">これにより、<xref:System.DateTime> の値よりも、<xref:System.DateTimeOffset> の値の方がコンピューター間で移植しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="567a4-110">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="567a4-111">ドキュメントのこのセクションでは、タイム ゾーンでの作業を行ったり、あるタイム ゾーンから別のタイム ゾーンに日付と時刻を変換できる、タイム ゾーンに対応したアプリケーションを作成するために必要な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="567a4-111">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="567a4-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="567a4-112">In this section</span></span>

<span data-ttu-id="567a4-113">[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md) タイム ゾーンに対応したアプリケーションの作成に関連する用語、概念、問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-113">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="567a4-114">[DateTime、DateTimeOffset、TimeSpan、および TimeZoneInfo の使い分け](../../../docs/standard/datetime/choosing-between-datetime.md) 日付および時刻のデータでの作業を行う場合、どのようなときに <xref:System.DateTime>、<xref:System.DateTimeOffset>、<xref:System.TimeZoneInfo> の型を使用するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-114">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="567a4-115">[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) ローカル システムで検出されたタイム ゾーンを列挙する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-115">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="567a4-116">[方法: コンピューター上に存在するタイム ゾーンを列挙する](../../../docs/standard/datetime/enumerate-time-zones.md) コンピューターのレジストリに定義されているタイム ゾーンを列挙して、ユーザーが一覧から事前定義のタイム ゾーンを選択できるようにするための例を提供します。</span><span class="sxs-lookup"><span data-stu-id="567a4-116">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="567a4-117">[方法: 定義済みの UTC オブジェクトおよびローカル タイム ゾーン オブジェクトにアクセスする](../../../docs/standard/datetime/access-utc-and-local.md) 世界協定時刻とローカル タイム ゾーンにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-117">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="567a4-118">[方法: TimeZoneInfo オブジェクトをインスタンス化する](../../../docs/standard/datetime/instantiate-time-zone-info.md) ローカル システムのレジストリから <xref:System.TimeZoneInfo> オブジェクトをインスタンス化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-118">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="567a4-119">[DateTimeOffset オブジェクトのインスタンス化](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) <xref:System.DateTimeOffset> オブジェクトをインスタンス化する方法、および <xref:System.DateTime> の値を <xref:System.DateTimeOffset> の値に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-119">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="567a4-120">[方法: 調整規則のないタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) 夏時間の調整をサポートしないカスタム タイム ゾーンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-120">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="567a4-121">[方法 : 調整規則のあるタイム ゾーンを作成する](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) 1 つ以上の夏時間調整をサポートするカスタム タイム ゾーンを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-121">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="567a4-122">[タイム ゾーンの保存と復元](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) タイム ゾーン データのシリアル化と逆シリアル化が <xref:System.TimeZoneInfo> でどのようにサポートされるかを説明し、これらの機能を使用できるいくつかのシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="567a4-122">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="567a4-123">[方法 : 埋め込みリソースにタイム ゾーンを保存する](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) カスタム タイム ゾーンを作成し、その情報をリソース ファイルに保存する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-123">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="567a4-124">[方法: 埋め込みリソースからタイム ゾーンを復元する](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) 埋め込みリソース ファイルに保存されているカスタム タイム ゾーンをインスタンス化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-124">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="567a4-125">[日付と時刻を使用した算術演算の実行](../../../docs/standard/datetime/performing-arithmetic-operations.md) <xref:System.DateTime> および <xref:System.DateTimeOffset> の値の加算、減算、比較に関連する問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-125">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="567a4-126">[方法: 日付と時刻の演算でタイム ゾーンを使用する](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) タイム ゾーンの調整規則を反映する日付と時刻の演算を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-126">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="567a4-127">[DateTime と DateTimeOffset 間の変換](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) <xref:System.DateTime> の値と <xref:System.DateTimeOffset> の値の変換方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-127">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="567a4-128">[タイム ゾーン間での時刻の変換](../../../docs/standard/datetime/converting-between-time-zones.md) タイム ゾーン間での時刻の変換方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-128">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="567a4-129">[方法: あいまいな時刻を解決する](../../../docs/standard/datetime/resolve-ambiguous-times.md) 時刻をタイム ゾーンの標準時刻に対応させることで、あいまいな時刻を解決する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-129">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="567a4-130">[方法: ユーザーがあいまいな時刻を解決できるようにする](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) ユーザーがあいまいな現地時刻と世界協定時刻の対応を決定できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="567a4-130">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="567a4-131">参照</span><span class="sxs-lookup"><span data-stu-id="567a4-131">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
