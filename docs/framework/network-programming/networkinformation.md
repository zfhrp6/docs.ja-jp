---
title: NetworkInformation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 897f094f512e423f055f0abea04d5403552ba31c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="networkinformation"></a><span data-ttu-id="93c3a-102">NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="93c3a-102">NetworkInformation</span></span>
<span data-ttu-id="93c3a-103"><xref:System.Net.NetworkInformation> 名前空間を使用すると、ネットワーク イベント、変更、統計、プロパティについての情報を収集できます。</span><span class="sxs-lookup"><span data-stu-id="93c3a-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="93c3a-104">また、<xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> クラスを使用して、リモート ホストに到達可能かどうかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="93c3a-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="93c3a-105">ネットワークの可用性とイベント</span><span class="sxs-lookup"><span data-stu-id="93c3a-105">Network Availability and Events</span></span>  
 <span data-ttu-id="93c3a-106"><xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> クラスを使用して、ネットワークのアドレスまたは可用性が変更されたかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="93c3a-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="93c3a-107">このクラスを使用するには、変更を処理するイベント ハンドラーを作成し、それを <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> または <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler> に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="93c3a-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="93c3a-108">詳細については、「[方法: ネットワークの可用性とアドレスの変更を検出する](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93c3a-108">For more information, see [How to: Detect Network Availability and Address Changes](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="93c3a-109">ネットワークの統計情報とプロパティ</span><span class="sxs-lookup"><span data-stu-id="93c3a-109">Network Statistics and Properties</span></span>  
 <span data-ttu-id="93c3a-110">インターフェイスまたはプロトコルを使用して、ネットワークの統計情報とプロパティを収集できます。</span><span class="sxs-lookup"><span data-stu-id="93c3a-110">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="93c3a-111"><xref:System.Net.NetworkInformation.NetworkInterface>、<xref:System.Net.NetworkInformation.NetworkInterfaceType>、<xref:System.Net.NetworkInformation.PhysicalAddress> の各クラスは、特定のネットワーク インターフェイスについての情報を提供します。一方、<xref:System.Net.NetworkInformation.IPInterfaceProperties>、<xref:System.Net.NetworkInformation.IPGlobalProperties>、<xref:System.Net.NetworkInformation.IPGlobalStatistics>、<xref:System.Net.NetworkInformation.TcpStatistics>、<xref:System.Net.NetworkInformation.UdpStatistics> の各クラスは、レイヤー 3 とレイヤー 4 のパケットについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="93c3a-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="93c3a-112">詳細については、「[方法: インターフェイス情報とプロトコル情報を取得する](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93c3a-112">For more information, see [How to: Get Interface and Protocol Information](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="93c3a-113">リモート ホストに到達可能かどうかの確認</span><span class="sxs-lookup"><span data-stu-id="93c3a-113">Determine if a Remote Host is Reachable</span></span>  
 <span data-ttu-id="93c3a-114"><xref:System.Net.NetworkInformation.Ping> クラスを使用して、リモート ホストがネットワークで稼働しているかどうか、また到達可能かどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="93c3a-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="93c3a-115">詳細については、「[方法: ホストに対して ping を実行](../../../docs/framework/network-programming/how-to-ping-a-host.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93c3a-115">For more information, see [How to: Ping a Host](../../../docs/framework/network-programming/how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c3a-116">参照</span><span class="sxs-lookup"><span data-stu-id="93c3a-116">See Also</span></span>  
 [<span data-ttu-id="93c3a-117">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="93c3a-117">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="93c3a-118">ネットワーク情報テクノロジのサンプル</span><span class="sxs-lookup"><span data-stu-id="93c3a-118">Network Information Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179564)  
 [<span data-ttu-id="93c3a-119">NetStat ツール テクノロジのサンプル</span><span class="sxs-lookup"><span data-stu-id="93c3a-119">NetStat Tool Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179562)  
 [<span data-ttu-id="93c3a-120">ping クライアント テクノロジのサンプル</span><span class="sxs-lookup"><span data-stu-id="93c3a-120">Ping Client Technology Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179565)
