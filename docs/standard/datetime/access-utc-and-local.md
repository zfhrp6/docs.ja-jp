---
title: "方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトにアクセス"
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
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 600dbb98264c4750db1ffb98b757ad191eaf4fe5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a><span data-ttu-id="d6224-102">方法: 定義済みの UTC とローカル タイム ゾーン オブジェクトにアクセス</span><span class="sxs-lookup"><span data-stu-id="d6224-102">How to: Access the predefined UTC and local time zone objects</span></span>

<span data-ttu-id="d6224-103"><xref:System.TimeZoneInfo>クラスには、2 つのプロパティが用意されています<xref:System.TimeZoneInfo.Utc%2A>と<xref:System.TimeZoneInfo.Local%2A>、定義済みのタイム ゾーン オブジェクトをコードのアクセス権を付与します。</span><span class="sxs-lookup"><span data-stu-id="d6224-103">The <xref:System.TimeZoneInfo> class provides two properties, <xref:System.TimeZoneInfo.Utc%2A> and <xref:System.TimeZoneInfo.Local%2A>, that give your code access to predefined time zone objects.</span></span> <span data-ttu-id="d6224-104">このトピックでは、これらのプロパティから返される <xref:System.TimeZoneInfo> オブジェクトにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6224-104">This topic discusses how to access the <xref:System.TimeZoneInfo> objects returned by those properties.</span></span>

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a><span data-ttu-id="d6224-105">世界協定時刻 (UTC) の TimeZoneInfo オブジェクトにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="d6224-105">To access the Coordinated Universal Time (UTC) TimeZoneInfo object</span></span>

1. <span data-ttu-id="d6224-106">使用して、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>協定世界時にアクセスするプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d6224-106">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property to access Coordinated Universal Time.</span></span>

2. <span data-ttu-id="d6224-107">割り当てるのではなく、<xref:System.TimeZoneInfo>オブジェクト変数に、プロパティによって返されるオブジェクトに引き続きアクセスを介して世界協定時刻、<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d6224-107">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property.</span></span>

### <a name="to-access-the-local-time-zone"></a><span data-ttu-id="d6224-108">ローカル タイム ゾーンにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="d6224-108">To access the local time zone</span></span>

1. <span data-ttu-id="d6224-109">使用して、 `static` (`Shared` Visual Basic で)<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>ローカル システムのタイム ゾーンにアクセスするプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d6224-109">Use the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property to access the local system time zone.</span></span>

2. <span data-ttu-id="d6224-110">割り当てるのではなく、<xref:System.TimeZoneInfo>オブジェクト変数に、プロパティによって返されるオブジェクトに引き続きアクセスを通じて、ローカル タイム ゾーン、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="d6224-110">Rather than assigning the <xref:System.TimeZoneInfo> object returned by the property to an object variable, continue to access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property.</span></span>

## <a name="example"></a><span data-ttu-id="d6224-111">例</span><span class="sxs-lookup"><span data-stu-id="d6224-111">Example</span></span>

<span data-ttu-id="d6224-112">次のコードでは、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>と<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>プロパティから米国およびカナダ東部標準時ゾーンの時刻の変換をできるだけでなく、タイム ゾーンの名前をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="d6224-112">The following code uses the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> and <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> properties to convert a time from the U.S. and Canadian Eastern Standard time zone, as well as to display the time zone name to the console.</span></span>

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

<span data-ttu-id="d6224-113">を介して、ローカル タイム ゾーンを常にアクセスする必要があります、<xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType>にゾーンのローカル時刻を割り当てるのではなく、プロパティ、<xref:System.TimeZoneInfo>オブジェクト変数です。</span><span class="sxs-lookup"><span data-stu-id="d6224-113">You should always access the local time zone through the <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> property rather than assigning the local time zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="d6224-114">同様に、アクセスすることは常に世界協定時刻で、<xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType>にゾーンの UTC を割り当てるのではなく、プロパティ、<xref:System.TimeZoneInfo>オブジェクト変数です。</span><span class="sxs-lookup"><span data-stu-id="d6224-114">Similarly, you should always access Coordinated Universal Time through the <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> property rather than assigning the UTC zone to a <xref:System.TimeZoneInfo> object variable.</span></span> <span data-ttu-id="d6224-115">これにより、<xref:System.TimeZoneInfo>オブジェクト変数への呼び出しによって無効にされてから、<xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d6224-115">This prevents the <xref:System.TimeZoneInfo> object variable from being invalidated by a call to the <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> method.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="d6224-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d6224-116">Compiling the code</span></span>

<span data-ttu-id="d6224-117">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d6224-117">This example requires:</span></span>

* <span data-ttu-id="d6224-118">される System.Core.dll への参照をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="d6224-118">That a reference to System.Core.dll be added to the project.</span></span>

* <span data-ttu-id="d6224-119"><xref:System>と共に名前空間をインポートする、`using`ステートメント (c# コードで必要です)。</span><span class="sxs-lookup"><span data-stu-id="d6224-119">That the <xref:System> namespace be imported with the `using` statement (required in C# code).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6224-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6224-120">See also</span></span>

<span data-ttu-id="d6224-121">[日付、時刻、およびタイム ゾーン](../../../docs/standard/datetime/index.md)
[ローカル システムで定義されているタイム ゾーンの検索](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[する方法: TimeZoneInfo オブジェクトをインスタンス化](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span><span class="sxs-lookup"><span data-stu-id="d6224-121">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md)</span></span>
