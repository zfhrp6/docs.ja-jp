---
title: "Windows Communication Foundation のトランスポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9275f1812111365ed6b0fb3be6957cd9ca883fdf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="41b41-102">Windows Communication Foundation のトランスポート</span><span class="sxs-lookup"><span data-stu-id="41b41-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="41b41-103">トランスポート層は、チャネル スタックの最も低いレベルにあります。</span><span class="sxs-lookup"><span data-stu-id="41b41-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="41b41-104">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] で使用される主なトランスポートは、HTTP、HTTPS、TCP、および名前付きパイプです。</span><span class="sxs-lookup"><span data-stu-id="41b41-104">The main transports used in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="41b41-105">このセクションのトピックでは、このようなトランスポートの選択、トランスポートの構成、およびチューニング プロパティの設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b41-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="41b41-106"> には追加のトランスポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="41b41-106"> includes additional transports.</span></span> <span data-ttu-id="41b41-107">トランスポートのメッセージ キュー (MSMQ とも呼ばれます) については、次を参照してください。[キューと信頼できるセッション](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)です。</span><span class="sxs-lookup"><span data-stu-id="41b41-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="41b41-108">ピア ツー ピアのトランスポートの詳細については、次を参照してください。[ピア ツー ピア ネットワー キング](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)です。</span><span class="sxs-lookup"><span data-stu-id="41b41-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41b41-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="41b41-109">In This Section</span></span>  
 [<span data-ttu-id="41b41-110">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="41b41-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="41b41-111">3 つの主なトランスポートについて説明し、そのうちの 1 つを選択する際の考慮事項を示します。</span><span class="sxs-lookup"><span data-stu-id="41b41-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="41b41-112">メッセージ エンコーダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="41b41-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="41b41-113">メッセージ エンコーディングのバインド要素を選択する際に考慮する必要のある要因について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b41-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="41b41-114">メッセージ転送ストリーミング</span><span class="sxs-lookup"><span data-stu-id="41b41-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="41b41-115">ストリーミングが行われるようにトランスポート層を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b41-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="41b41-116">HTTP および HTTPS の構成</span><span class="sxs-lookup"><span data-stu-id="41b41-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="41b41-117">HTTP および HTTPS トランスポート バインド要素の構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b41-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="41b41-118">方法: WCF URL 予約を制限付きの予約に置き換える</span><span class="sxs-lookup"><span data-stu-id="41b41-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="41b41-119">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の URL 制限付き予約の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b41-119">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL restricted reservations.</span></span>  
  
 [<span data-ttu-id="41b41-120">トランスポート クォータ</span><span class="sxs-lookup"><span data-stu-id="41b41-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="41b41-121">トランスポート層で使用できるクォータを設定する際の考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b41-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="41b41-122">Nat とファイアウォールの使用</span><span class="sxs-lookup"><span data-stu-id="41b41-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="41b41-123">ファイアウォールを介してメッセージを送受信する場合や、ネットワーク アドレス交換 (NAT) が存在する場合にトランスポート層を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b41-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="41b41-124">Net.TCP ポート共有</span><span class="sxs-lookup"><span data-stu-id="41b41-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="41b41-125">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の Net.TCP ポート共有コンポーネントの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b41-125">Describes how to use the Net.TCP Port Sharing component of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="41b41-126">参照</span><span class="sxs-lookup"><span data-stu-id="41b41-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="41b41-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="41b41-127">Related Sections</span></span>  
 [<span data-ttu-id="41b41-128">バインディング</span><span class="sxs-lookup"><span data-stu-id="41b41-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="41b41-129">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="41b41-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
