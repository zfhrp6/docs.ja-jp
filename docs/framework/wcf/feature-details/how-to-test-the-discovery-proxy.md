---
title: 探索プロキシをテストする方法
ms.date: 03/30/2017
ms.assetid: d96e3fa2-3c42-4e5d-8244-2694081bdc32
ms.openlocfilehash: 35edbd03e912ae2d9c491afb28dee1c4a3055d14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491223"
---
# <a name="how-to-test-the-discovery-proxy"></a><span data-ttu-id="ed568-102">探索プロキシをテストする方法</span><span class="sxs-lookup"><span data-stu-id="ed568-102">How to: Test the Discovery Proxy</span></span>
<span data-ttu-id="ed568-103">これは、探索プロキシの実装方法に関する 4 つのトピックのうちの 4 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="ed568-103">This is the fourth of four topics that shows how to implement a discovery proxy.</span></span> <span data-ttu-id="ed568-104">前のトピックで[する方法: を探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)、探索プロキシを使用してサービスを検索し、サービスを呼び出す、WCF クライアント アプリケーションを実装しています。</span><span class="sxs-lookup"><span data-stu-id="ed568-104">In the previous topic, [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md), you implemented a WCF client application that uses the discovery proxy to find a service and then calls the service.</span></span> <span data-ttu-id="ed568-105">このトピックでは、探索プロキシ、サービス、およびクライアント アプリケーションが予期したとおりに動作することを確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed568-105">This topic describes how to verify the discovery proxy, the service, and the client application work as expected.</span></span>  
  
### <a name="run-the-discovery-proxy"></a><span data-ttu-id="ed568-106">探索プロキシの実行</span><span class="sxs-lookup"><span data-stu-id="ed568-106">Run the Discovery Proxy</span></span>  
  
1.  <span data-ttu-id="ed568-107">管理者としてコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="ed568-107">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="ed568-108">"このプログラムの機能のいくつかが Windows ファイアウォールでブロックされています" という内容のダイアログが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ed568-108">You may see a dialog that says: Windows Firewall has blocked some features of this program.</span></span> <span data-ttu-id="ed568-109">このメッセージを表示する場合にクリックして、**ブロックを解除する**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed568-109">If you see this message, click the **Unblock** button.</span></span>  
  
3.  <span data-ttu-id="ed568-110">コマンド プロンプトから、探索プロキシ DiscoveryProxy.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="ed568-110">Within the command prompt, run the discovery proxy, DiscoveryProxy.exe.</span></span>  
  
4.  <span data-ttu-id="ed568-111">「`Proxy started. Hit Enter to exit`」というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed568-111">The application should display the following text: `Proxy started. Hit Enter to exit`.</span></span>  
  
### <a name="run-the-discoverable-service"></a><span data-ttu-id="ed568-112">探索サービスの実行</span><span class="sxs-lookup"><span data-stu-id="ed568-112">Run the Discoverable Service</span></span>  
  
1.  <span data-ttu-id="ed568-113">管理者としてコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="ed568-113">Open a command prompt as an administrator.</span></span>  
  
2.  <span data-ttu-id="ed568-114">コマンド プロンプトから、探索サービス Service.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="ed568-114">Within the command prompt, run the Service.exe discoverable service.</span></span>  
  
3.  <span data-ttu-id="ed568-115">DiscoveryProxy.exe は、次のテキストを表示する必要があります:`******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******`です。</span><span class="sxs-lookup"><span data-stu-id="ed568-115">The DiscoveryProxy.exe should display the following text: `******* Adding the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 3.******* Done *******` .</span></span>  
  
### <a name="run-the-client-application"></a><span data-ttu-id="ed568-116">クライアント アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="ed568-116">Run the Client Application</span></span>  
  
1.  <span data-ttu-id="ed568-117">コマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="ed568-117">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="ed568-118">コマンド プロンプトから、client.exe アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed568-118">Within the command prompt, run the client.exe application.</span></span>  
  
3.  <span data-ttu-id="ed568-119">数秒後に、クライアント アプリケーションにより「サービス エンドポイント に接続しています」というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed568-119">After a few seconds the client application displays the following text: Connecting to [Service-Endpoint].</span></span>  
  
4.  <span data-ttu-id="ed568-120">次に、service.exe により「Greeting request received, I will respond」というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed568-120">The service.exe should then display the following text: Greeting request received, I will respond.</span></span>  
  
5.  <span data-ttu-id="ed568-121">その後、client.exe により「Hello Client!」というテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed568-121">The client.exe should then display the following text: Hello Client!</span></span>  
  
### <a name="shut-down-the-applications"></a><span data-ttu-id="ed568-122">アプリケーションのシャットダウン</span><span class="sxs-lookup"><span data-stu-id="ed568-122">Shut Down the Applications</span></span>  
  
1.  <span data-ttu-id="ed568-123">クライアント アプリケーションをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="ed568-123">Shut down the client application.</span></span>  
  
2.  <span data-ttu-id="ed568-124">サービスをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="ed568-124">Shut down the service.</span></span> <span data-ttu-id="ed568-125">探索プロキシにより、次のテキストが表示されます。`******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`</span><span class="sxs-lookup"><span data-stu-id="ed568-125">The discovery proxy displays the following text: `******* Removing the following service: ** [Service Contract Name] ** [Service Endpoint Addr] 2.3.******* Done *******`.</span></span>  
  
3.  <span data-ttu-id="ed568-126">探索プロキシをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="ed568-126">Shut down the discovery proxy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed568-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed568-127">See Also</span></span>  
 [<span data-ttu-id="ed568-128">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="ed568-128">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="ed568-129">探索プロキシを実装する方法</span><span class="sxs-lookup"><span data-stu-id="ed568-129">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [<span data-ttu-id="ed568-130">探索プロキシで登録される探索可能なサービスの実装方法</span><span class="sxs-lookup"><span data-stu-id="ed568-130">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 [<span data-ttu-id="ed568-131">探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装方法</span><span class="sxs-lookup"><span data-stu-id="ed568-131">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
