---
title: "探索ルーター サービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 663ece44a18ae073412376bc11a1d70927740e8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="discovery-router-service"></a><span data-ttu-id="934d3-102">探索ルーター サービス</span><span class="sxs-lookup"><span data-stu-id="934d3-102">Discovery Router Service</span></span>
<span data-ttu-id="934d3-103">このサンプルでは、探索メッセージを別のエンドポイントに転送する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="934d3-103">This sample demonstrates how to forward discovery messages to another endpoint.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="934d3-104">使用例</span><span class="sxs-lookup"><span data-stu-id="934d3-104">Demonstrates</span></span>  
 <span data-ttu-id="934d3-105">探索ルーティング</span><span class="sxs-lookup"><span data-stu-id="934d3-105">Discovery Routing</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="934d3-106">説明</span><span class="sxs-lookup"><span data-stu-id="934d3-106">Discussion</span></span>  
 <span data-ttu-id="934d3-107">探索ルーティングは、プロキシがサービスを認識しないが、別のプロキシのことは認識する場合に、クライアントがプロキシを使用してそのようなサービスを検索するシナリオで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="934d3-107">Discovery routing is useful in a scenario in which a client is looking for a service using a proxy and the proxy is unaware of such a service, but knows of another proxy.</span></span> <span data-ttu-id="934d3-108">このプロキシは、探索パケットをこのクライアントから 2 番目のプロキシに転送できます。</span><span class="sxs-lookup"><span data-stu-id="934d3-108">This proxy can forward the discovery packet from this client to the second proxy.</span></span> <span data-ttu-id="934d3-109">2 番目のプロキシはサービスを検索し、応答を元のクライアントに返します。</span><span class="sxs-lookup"><span data-stu-id="934d3-109">The second proxy can look for the service and return the responses to the original client.</span></span>  
  
 <span data-ttu-id="934d3-110">このサンプルでは、クライアントはメッセージを探索ルーティング コンポーネントに送信します。</span><span class="sxs-lookup"><span data-stu-id="934d3-110">In this sample, a client sends a message to a discovery routing component.</span></span> <span data-ttu-id="934d3-111">このメッセージは、探索ルーター上の特定のエンドポイントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="934d3-111">This message is sent to a specific endpoint on the discovery router.</span></span> <span data-ttu-id="934d3-112">その後、このルーターはメッセージを UDP マルチキャスト エンドポイントに転送します。</span><span class="sxs-lookup"><span data-stu-id="934d3-112">The router then forwards the message to a UDP multicast endpoint.</span></span> <span data-ttu-id="934d3-113">プローブ メッセージはマルチキャスト エンドポイントに送信され、UDP マルチキャスト アドレスをリッスンするサービスは、その探索ルーターに応答します。</span><span class="sxs-lookup"><span data-stu-id="934d3-113">The probe message goes out to the multicast endpoint and a service listening on a UDP multicast address responds to that discovery router.</span></span> <span data-ttu-id="934d3-114">探索ルーターは応答を収集し、クライアントにその応答を返します。</span><span class="sxs-lookup"><span data-stu-id="934d3-114">The discovery router collects the responses and sends them back to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="934d3-115">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="934d3-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="934d3-116">このサンプルをビルドします。</span><span class="sxs-lookup"><span data-stu-id="934d3-116">Build the sample.</span></span>  
  
2.  <span data-ttu-id="934d3-117">DiscoveryRouter 実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="934d3-117">Run the DiscoveryRouter executable.</span></span>  
  
3.  <span data-ttu-id="934d3-118">ビルド ディレクトリからサービス実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="934d3-118">Run the service executable from the build directory.</span></span>  
  
4.  <span data-ttu-id="934d3-119">クライアント実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="934d3-119">Run the client executable.</span></span> <span data-ttu-id="934d3-120">クライアントでサービスが検索されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="934d3-120">Note that the client locates the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="934d3-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="934d3-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="934d3-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="934d3-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="934d3-123">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="934d3-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="934d3-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="934d3-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
