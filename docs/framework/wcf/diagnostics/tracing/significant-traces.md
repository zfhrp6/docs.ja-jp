---
title: "重要なトレース"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 58322a472a59ee9d3ac9451ff1f20ed95405ac54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="significant-traces"></a><span data-ttu-id="c678a-102">重要なトレース</span><span class="sxs-lookup"><span data-stu-id="c678a-102">Significant Traces</span></span>
<span data-ttu-id="c678a-103">ここでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] によって出力される主要なトレースの一部を示します。</span><span class="sxs-lookup"><span data-stu-id="c678a-103">This topic lists some of the major traces emitted by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="significant-traces"></a><span data-ttu-id="c678a-104">重要なトレース</span><span class="sxs-lookup"><span data-stu-id="c678a-104">Significant Traces</span></span>  
  
|<span data-ttu-id="c678a-105">トレース</span><span class="sxs-lookup"><span data-stu-id="c678a-105">Trace</span></span>|<span data-ttu-id="c678a-106">説明</span><span class="sxs-lookup"><span data-stu-id="c678a-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c678a-107">Message Log トレース</span><span class="sxs-lookup"><span data-stu-id="c678a-107">Message log trace</span></span>|<span data-ttu-id="c678a-108">このトレースは、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース ソースが有効な場合に、メッセージ ログ機能によって `System.ServiceModel.MessageLogging` メッセージがログに記録されるときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-108">The trace is emitted when a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message is logged by the message logging feature when the `System.ServiceModel.MessageLogging` trace source is enabled.</span></span> <span data-ttu-id="c678a-109">このトレースをクリックすると、メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-109">Clicking this trace displays the message.</span></span> <span data-ttu-id="c678a-110">メッセージには、構成可能なログ ポイントが 4 つ (`ServiceLevelSendRequest`、`TransportSend`、`TransportReceive`、`ServiceLevelReceiveRequest`) あり、これらは、メッセージ ログ トレースの Message Source 属性にも示されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-110">There are four configurable logging points for a message: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, also indicated by the Message Source attribute in the message log trace.</span></span>|  
|<span data-ttu-id="c678a-111">Message Received トレース</span><span class="sxs-lookup"><span data-stu-id="c678a-111">Message received trace</span></span>|<span data-ttu-id="c678a-112">このトレースは、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース ソースが情報レベルまたは詳細レベルで有効な場合に、`System.ServiceModel` メッセージが受信されるときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-112">This trace is emitted when a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message is received if the `System.ServiceModel` trace source is enabled at information or verbose level.</span></span> <span data-ttu-id="c678a-113">このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。</span><span class="sxs-lookup"><span data-stu-id="c678a-113">This trace is necessary to see the message correlation arrow in the activity graph view.</span></span>|  
|<span data-ttu-id="c678a-114">Message Sent トレース</span><span class="sxs-lookup"><span data-stu-id="c678a-114">Message sent trace</span></span>|<span data-ttu-id="c678a-115">このトレースは [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] トレース ソースが Information レベルか Verbose レベルで有効な場合に、`System.ServiceModel` メッセージが送信されるときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-115">This trace is emitted when a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message is sent if the `System.ServiceModel` trace source is enabled at information or verbose level.</span></span> <span data-ttu-id="c678a-116">このトレースはアクティビティのグラフ ビューでメッセージの相関矢印を表示するために必要です。</span><span class="sxs-lookup"><span data-stu-id="c678a-116">This trace is necessary to see the message correlation arrow in the activity graph view.</span></span>|  
|<span data-ttu-id="c678a-117">Get ChannelEndpointElement</span><span class="sxs-lookup"><span data-stu-id="c678a-117">Get ChannelEndpointElement</span></span>|<span data-ttu-id="c678a-118">このトレースは、情報レベルで Construct チャネル ファクトリに出力されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-118">This trace is emitted in Construct channel factory, at information level.</span></span> <span data-ttu-id="c678a-119">このトレースには、クライアントが対話しているエンドポイントの説明 (リモート アドレス、バインディング、コントラクト名など) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-119">It provides a description of the endpoint the client is talking to (remote address, binding, contract name).</span></span>|  
|<span data-ttu-id="c678a-120">Get ServiceElement</span><span class="sxs-lookup"><span data-stu-id="c678a-120">Get ServiceElement</span></span>|<span data-ttu-id="c678a-121">このトレースは、情報レベルで Construct サービス ホストに出力されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-121">This trace is emitted in Construct service host, at Information level.</span></span> <span data-ttu-id="c678a-122">サービス コントラクトとバインディングの説明が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-122">It provides a description of the service contract and binding.</span></span>|  
|<span data-ttu-id="c678a-123">SocketConnection Create</span><span class="sxs-lookup"><span data-stu-id="c678a-123">SocketConnection create</span></span>|<span data-ttu-id="c678a-124">このトレースは、クライアントによって実行される最初の "プロセス" アクションおよびサービスの "バイトを受信" アクティビティで出力されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-124">This trace is emitted in the first Process action performed by the client and in the Receive bytes activity on the service.</span></span> <span data-ttu-id="c678a-125">ローカルとリモートの IP アドレスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c678a-125">It provides the local and remote IP addresses.</span></span> <span data-ttu-id="c678a-126">情報レベルで出力されます。</span><span class="sxs-lookup"><span data-stu-id="c678a-126">It is emitted at Information level.</span></span>|
