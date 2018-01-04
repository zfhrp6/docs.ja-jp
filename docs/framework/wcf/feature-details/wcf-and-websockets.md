---
title: "WCF と WebSocket"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e84bf7a94a6a6fa980e223daf0a6c7aaf489bb6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="c7e58-102">WCF と WebSocket</span><span class="sxs-lookup"><span data-stu-id="c7e58-102">WCF and WebSockets</span></span>
<span data-ttu-id="c7e58-103">.NET Framework 4.5 では、Windows Communication Foundation の WebSocket のサポートが導入されています。</span><span class="sxs-lookup"><span data-stu-id="c7e58-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="c7e58-104">Websocket は、標準的な HTTP ポート 80 と 443 を介した双方向通信を有効にする効率的な標準ベース テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="c7e58-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="c7e58-105">標準 HTTP ポートを使用することで、Websocket は中継局を通じて Web 全体で通信できます。</span><span class="sxs-lookup"><span data-stu-id="c7e58-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="c7e58-106">2 つの新しい標準バインディングが WebSocket トランスポート経由の通信をサポートするために追加されました。</span><span class="sxs-lookup"><span data-stu-id="c7e58-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="c7e58-107"><xref:System.ServiceModel.NetHttpBinding> および <xref:System.ServiceModel.NetHttpsBinding>。</span><span class="sxs-lookup"><span data-stu-id="c7e58-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="c7e58-108">Websocket 固有の設定を構成できます、<xref:System.ServiceModel.Channels.HttpTransportBindingElement>にアクセスして、<xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c7e58-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="c7e58-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c7e58-109">In This Section</span></span>  
 [<span data-ttu-id="c7e58-110">NetHttpBinding の使用</span><span class="sxs-lookup"><span data-stu-id="c7e58-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="c7e58-111"><xref:System.ServiceModel.NetHttpBinding> とその構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7e58-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="c7e58-112">WebSockets 上で通信する WCF サービスを作成する用法</span><span class="sxs-lookup"><span data-stu-id="c7e58-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="c7e58-113">Websocket 経由で通信する WCF サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c7e58-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c7e58-114">参照</span><span class="sxs-lookup"><span data-stu-id="c7e58-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7e58-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7e58-115">Related Sections</span></span>
