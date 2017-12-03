---
title: "探索プロキシをテストする方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55a7fe72b34fc8c099d921e7e295c184817825a3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="5523c-102">探索プロキシをテストする方法</span><span class="sxs-lookup"><span data-stu-id="5523c-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="5523c-103">これは、探索プロキシの実装方法に関する 4 つのトピックのうちの 4 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="5523c-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="5523c-104">前のトピックで[する方法: を探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)、実装する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クライアント アプリケーションを探索プロキシを使用してサービスを検索してから、サービス。</span><span class="sxs-lookup"><span data-stu-id="5523c-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="5523c-105">このトピックでは、探索プロキシ、サービス、およびクライアント アプリケーションが予期したとおりに動作することを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5523c-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="5523c-106">探索プロキシの実行</span><span class="sxs-lookup"><span data-stu-id="5523c-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="5523c-107">管理者としてコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5523c-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="5523c-108">"このプログラムの機能のいくつかが Windows ファイアウォールでブロックされています" という内容のダイアログが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="5523c-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="5523c-109">このメッセージを表示する場合にクリックして、**ブロックを解除する**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5523c-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="5523c-110">コマンド プロンプトから、探索プロキシ DiscoveryProxy.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="5523c-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="5523c-111">「`Proxy started. Hit Enter to exit`」というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5523c-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="5523c-112">探索サービスの実行</span><span class="sxs-lookup"><span data-stu-id="5523c-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="5523c-113">管理者としてコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5523c-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="5523c-114">コマンド プロンプトから、探索サービス Service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="5523c-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="5523c-115">DiscoveryProxy.exe は、次のテキストを表示する必要があります:`******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******`です。</span><span class="sxs-lookup"><span data-stu-id="5523c-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="5523c-116">クライアント アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="5523c-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="5523c-117">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="5523c-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="5523c-118">コマンド プロンプトから、client.exe アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="5523c-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="5523c-119">数秒後に、クライアント アプリケーションにより「サービス エンドポイント に接続しています」というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5523c-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="5523c-120">次に、service.exe により「Greeting request received, I will respond」というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5523c-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="5523c-121">その後、client.exe により「Hello Client!」というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="5523c-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="5523c-122">アプリケーションのシャットダウン</span><span class="sxs-lookup"><span data-stu-id="5523c-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="5523c-123">クライアント アプリケーションをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="5523c-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="5523c-124">サービスをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="5523c-124">Shut down the service.</span></span> <span data-ttu-id="5523c-125">探索プロキシにより、次のテキストが表示されます。`******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`</span><span class="sxs-lookup"><span data-stu-id="5523c-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="5523c-126">探索プロキシをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="5523c-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5523c-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="5523c-127">See Also</span></span>  
 [<span data-ttu-id="5523c-128">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="5523c-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="5523c-129">方法: 探索プロキシの実装</span><span class="sxs-lookup"><span data-stu-id="5523c-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="5523c-130">方法: 探索プロキシで登録される探索可能なサービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="5523c-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="5523c-131">方法: 探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装</span><span class="sxs-lookup"><span data-stu-id="5523c-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
