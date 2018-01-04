---
title: "マネージ アプリケーションのホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c74f95fba492b677d3b1702d090c7a055bc5f1ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-in-a-managed-application"></a><span data-ttu-id="feddb-102">マネージ アプリケーションのホスト</span><span class="sxs-lookup"><span data-stu-id="feddb-102">Hosting in a Managed Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="feddb-103"> サービスは、任意の [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションでホストできます。</span><span class="sxs-lookup"><span data-stu-id="feddb-103"> services can be hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application.</span></span> <span data-ttu-id="feddb-104">自己ホスト型サービスは、展開を要するインフラストラクチャが最も少ないので、最も柔軟なホスト オプションです。</span><span class="sxs-lookup"><span data-stu-id="feddb-104">Self-hosting services is the most flexible hosting option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="feddb-105">ただし、マネージ アプリケーションは、インターネット インフォメーション サービス (IIS) や Windows サービスなど、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の他のホスト オプションが備えている高度なホスト機能と管理機能を提供しないので、堅牢さに最も乏しいホスト オプションでもあります。</span><span class="sxs-lookup"><span data-stu-id="feddb-105">However, it is also the least robust hosting option, because managed applications do not provide the advanced hosting and management features of other hosting options in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as Internet Information Services (IIS) and Windows services.</span></span>  
  
 <span data-ttu-id="feddb-106">自己ホスト型サービスを作成するには、メッセージをリッスンするサービスを開始する <xref:System.ServiceModel.ServiceHost>のインスタンスを作成して開きます。</span><span class="sxs-lookup"><span data-stu-id="feddb-106">To create a self-hosted service, create and open an instance of the <xref:System.ServiceModel.ServiceHost>, which starts a service listening for messages.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="feddb-107">[する方法: マネージ アプリケーションで WCF サービスをホスト](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)です。</span><span class="sxs-lookup"><span data-stu-id="feddb-107"> [How to: Host a WCF Service in a Managed Application](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="feddb-108">コントラクトを定義、コントラクトを実装およびマネージ アプリケーション内部のサービスをホストする方法の完全な例については、[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)と[自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)です。</span><span class="sxs-lookup"><span data-stu-id="feddb-108">For a complete example on how to define a contract, implement the contract, and host a service inside of a managed application see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md) and the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md).</span></span>  
  
 <span data-ttu-id="feddb-109">以下に、このホスト オプションを使用する一般的なシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="feddb-109">The following sections describe common scenarios that use this hosting option.</span></span>  
  
## <a name="console-applications"></a><span data-ttu-id="feddb-110">コンソール アプリケーション</span><span class="sxs-lookup"><span data-stu-id="feddb-110">Console Applications</span></span>  
 <span data-ttu-id="feddb-111">自己ホストによって可能になる一般的なシナリオは、コンソール アプリケーション内部で実行する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="feddb-111">Common scenarios that self-hosting enables are [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running inside console applications.</span></span> <span data-ttu-id="feddb-112">コンソール アプリケーション内部の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストすることは、一般的にサービスの開発フェーズで有用です。</span><span class="sxs-lookup"><span data-stu-id="feddb-112">Hosting a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service inside a console application is typically useful during the development phase of the service.</span></span> <span data-ttu-id="feddb-113">コンソール アプリケーションにより、アプリケーション内部で起こっている状況を見極めるための情報のデバッグやトレースが容易になり、新しい場所にアプリケーションをコピーして移動することも簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="feddb-113">This makes them easy to debug, easy to get trace information from to find out what is happening inside of the application, and easy to move around by copying them to new locations.</span></span>  
  
## <a name="rich-client-applications"></a><span data-ttu-id="feddb-114">リッチ クライアント アプリケーション</span><span class="sxs-lookup"><span data-stu-id="feddb-114">Rich Client Applications</span></span>  
 <span data-ttu-id="feddb-115">自己ホストによって可能になるもう 1 つの一般的なシナリオは、リッチ クライアント アプリケーションです。これには、 [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] または Windows フォーム (WinForms) に基づいて作成されたリッチ クライアント アプリケーションなどがあります。</span><span class="sxs-lookup"><span data-stu-id="feddb-115">Other common scenarios that self-hosting enables are rich client applications, such as those based on [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] or Windows Forms (WinForms).</span></span> <span data-ttu-id="feddb-116">このホスト オプションを使用すると、 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] や WinForms アプリケーションなど、外部と通信を行うリッチ クライアント アプリケーションの作成も容易になります。</span><span class="sxs-lookup"><span data-stu-id="feddb-116">This hosting option also makes it easy for rich client applications, such as [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] and WinForms applications, to communicate with the outside world.</span></span> <span data-ttu-id="feddb-117">たとえば、ユーザー インターフェイスに [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] を使用しながら、他のクライアントからの接続を許容して情報を共有するために [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをホストするピア ツー ピア コラボレーションのクライアントなどです。</span><span class="sxs-lookup"><span data-stu-id="feddb-117">For example, a peer-to-peer collaboration client that uses [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] for its user interface and also hosts a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that allows other clients to connect to it and share information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feddb-118">参照</span><span class="sxs-lookup"><span data-stu-id="feddb-118">See Also</span></span>  
 [<span data-ttu-id="feddb-119">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="feddb-119">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="feddb-120">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="feddb-120">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
