---
title: "探索プロキシの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ddea7bf69f697c5b9ecd9d41021bff2407522a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-a-discovery-proxy"></a><span data-ttu-id="e7a97-102">探索プロキシの実装</span><span class="sxs-lookup"><span data-stu-id="e7a97-102">Implementing a Discovery Proxy</span></span>
<span data-ttu-id="e7a97-103">ここでは、探索プロキシの実装に必要な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7a97-103">This section describes the steps required to implement a discovery proxy.</span></span> <span data-ttu-id="e7a97-104">探索プロキシは、サービスのリポジトリを格納するスタンドアロンのサービスです。</span><span class="sxs-lookup"><span data-stu-id="e7a97-104">A discovery proxy is a standalone service that contains a repository of services.</span></span> <span data-ttu-id="e7a97-105">クライアントは探索プロキシに対し、そのプロキシで認識される探索可能なサービスを問い合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="e7a97-105">Clients can query a discovery proxy to find discoverable services that the proxy is aware of.</span></span> <span data-ttu-id="e7a97-106">プロキシにサービスを登録する方法は、実装手段によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e7a97-106">How a proxy is populated with services is up to the implementer.</span></span> <span data-ttu-id="e7a97-107">たとえば、探索プロキシが既存のサービス リポジトリに接続でき、その情報を探索可能にできる場合、管理者は管理 API を使用して探索可能なサービスをプロキシに追加することができます。または、探索プロキシにアナウンス機能を使用し、内部キャッシュを更新できます。</span><span class="sxs-lookup"><span data-stu-id="e7a97-107">For example, a discovery proxy can connect to an existing service repository and make that information discoverable, an administrator can use a management API to add discoverable services to a proxy, or a discovery proxy can use the announcement functionality to update its internal cache.</span></span>  
  
 <span data-ttu-id="e7a97-108">WCF 実装は、プロキシを簡単にビルドできる基本クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="e7a97-108">The WCF implementation provides base classes that allow you to easily build a proxy.</span></span> <span data-ttu-id="e7a97-109">これらの API を利用して、既存のリポジトリの上に探索プロキシをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="e7a97-109">You can utilize these APIs to build a Discovery Proxy on top of your existing repository.</span></span>  
  
 <span data-ttu-id="e7a97-110">ここで実装される探索プロキシは、探索可能にしてクライアントからエンドポイントを検索できるという点で、他の WCF サービスと似ています。</span><span class="sxs-lookup"><span data-stu-id="e7a97-110">The discovery proxy implemented here is like any other WCF services, in that you can also make the discovery proxy discoverable and have the clients locate its endpoints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7a97-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e7a97-111">In This Section</span></span>  
 [<span data-ttu-id="e7a97-112">方法: 探索プロキシの実装</span><span class="sxs-lookup"><span data-stu-id="e7a97-112">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 <span data-ttu-id="e7a97-113">探索プロキシを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7a97-113">Describes how to implement a discovery proxy.</span></span>  
  
 [<span data-ttu-id="e7a97-114">方法: 探索プロキシで登録される探索可能なサービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="e7a97-114">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 <span data-ttu-id="e7a97-115">探索プロキシに登録する、探索可能な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7a97-115">Describes how to implement a discoverable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that registers with the discovery proxy.</span></span>  
  
 [<span data-ttu-id="e7a97-116">方法: 探索プロキシを使用してサービスを検索するクライアント アプリケーションの実装</span><span class="sxs-lookup"><span data-stu-id="e7a97-116">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 <span data-ttu-id="e7a97-117">探索プロキシを使用してサービスを検索する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アプリケーションの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7a97-117">Describes how to implement a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application that uses the discovery proxy to search for a service.</span></span>  
  
 [<span data-ttu-id="e7a97-118">方法: 探索プロキシのテスト</span><span class="sxs-lookup"><span data-stu-id="e7a97-118">How to: Test the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 <span data-ttu-id="e7a97-119">前の 3 つのトピックに記述されたコードのテスト方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7a97-119">Describes how to test the code written in the previous three topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a97-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7a97-120">See Also</span></span>  
 [<span data-ttu-id="e7a97-121">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="e7a97-121">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [<span data-ttu-id="e7a97-122">方法: プログラムによって探索可能性を WCF サービスとクライアントを追加</span><span class="sxs-lookup"><span data-stu-id="e7a97-122">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
