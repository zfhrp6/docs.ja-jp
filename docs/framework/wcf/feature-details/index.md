---
title: WCF 機能の詳細
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- features [WCF]
- WCF, features
- Windows Communication Foundation, features
ms.assetid: 9b4368ca-0bd3-40dc-a539-bcd5779cee5f
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2aa8adc0ce197c3776b8314009fcaa061bed884d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-feature-details"></a><span data-ttu-id="5c39d-102">WCF 機能の詳細</span><span class="sxs-lookup"><span data-stu-id="5c39d-102">WCF Feature Details</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="5c39d-103"> では、アプリケーションのメッセージング機能を広範囲に制御できます。</span><span class="sxs-lookup"><span data-stu-id="5c39d-103"> allows extensive control over the messaging functions of an application.</span></span> <span data-ttu-id="5c39d-104">このセクションの各トピックでは、使用できる機能について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-104">The topics in this section go into detail about the available features.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5c39d-105">基本的なプログラミングを参照してください[基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c39d-105"> basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5c39d-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5c39d-106">In This Section</span></span>  
 [<span data-ttu-id="5c39d-107">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="5c39d-107">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 <span data-ttu-id="5c39d-108">ワークフロー サービスを作成および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-108">Describes how to create and configure workflow services.</span></span>  
  
 [<span data-ttu-id="5c39d-109">エンドポイント : アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="5c39d-109">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 <span data-ttu-id="5c39d-110">サービスのさまざまな側面を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-110">Describes how to control multiple aspects of your service.</span></span>  
  
 [<span data-ttu-id="5c39d-111">データ転送とシリアル化</span><span class="sxs-lookup"><span data-stu-id="5c39d-111">Data Transfer and Serialization</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)  
 <span data-ttu-id="5c39d-112">相互運用性または将来の互換性を実現するために、データのシリアル化を調整する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-112">Describes how serialization of data can be tailored for interoperation or future compatibility.</span></span>  
  
 [<span data-ttu-id="5c39d-113">セッション、インスタンス化、および同時実行</span><span class="sxs-lookup"><span data-stu-id="5c39d-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 <span data-ttu-id="5c39d-114">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のインスタンス化モードとセッション モードについて説明し、アプリケーションに適したモードを選択する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-114">Describes the instancing and session modes of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and how to select the right mode for your application.</span></span>  
  
 [<span data-ttu-id="5c39d-115">トランスポート</span><span class="sxs-lookup"><span data-stu-id="5c39d-115">Transports</span></span>](../../../../docs/framework/wcf/feature-details/transports.md)  
 <span data-ttu-id="5c39d-116">チャネル スタックの最も低いレベルにあるトランスポート層を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-116">Describes how to configure the transport layer, the lowest level of the channel stack.</span></span>  
  
 [<span data-ttu-id="5c39d-117">キューと信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="5c39d-117">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)  
 <span data-ttu-id="5c39d-118">キューについて説明します。キューは、送信元アプリケーションが送ったメッセージを受信側アプリケーションに代わって保存しておき、後で受信側アプリケーションに転送します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-118">Describes queues, which store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span>  
  
 [<span data-ttu-id="5c39d-119">トランザクション</span><span class="sxs-lookup"><span data-stu-id="5c39d-119">Transactions</span></span>](../../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)  
 <span data-ttu-id="5c39d-120">必要に応じてロールバックできるトランザクション操作を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-120">Explains how to create transacted operations that can be rolled back if needed.</span></span>  
  
 [<span data-ttu-id="5c39d-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5c39d-121">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 <span data-ttu-id="5c39d-122">機密性と整合性を備えたアプリケーションを作成するうえで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティがどのように役立つかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-122">Describes how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security helps you to create applications that have confidentiality and integrity.</span></span> <span data-ttu-id="5c39d-123">監査機能として、認証と承認を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5c39d-123">Authentication and authorization are also available, as are auditing features.</span></span>  
  
 [<span data-ttu-id="5c39d-124">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="5c39d-124">Peer-to-Peer Networking</span></span>](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 <span data-ttu-id="5c39d-125">ビア サービスとクライアントを作成する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-125">Details how to create peer services and clients.</span></span>  
  
 [<span data-ttu-id="5c39d-126">メタデータ</span><span class="sxs-lookup"><span data-stu-id="5c39d-126">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 <span data-ttu-id="5c39d-127">メタデータのアーキテクチャと形式について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-127">Describes metadata architecture and formats.</span></span>  
  
 [<span data-ttu-id="5c39d-128">クライアント</span><span class="sxs-lookup"><span data-stu-id="5c39d-128">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 <span data-ttu-id="5c39d-129">サービスにアクセスするさまざまなクライアントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-129">Describes how to create a variety of clients that access services.</span></span>  
  
 [<span data-ttu-id="5c39d-130">ホスティング</span><span class="sxs-lookup"><span data-stu-id="5c39d-130">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 <span data-ttu-id="5c39d-131">ホストについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-131">Describes hosting.</span></span> <span data-ttu-id="5c39d-132">サービスは、別のアプリケーションまたは自己ホストを使用してホストできます。</span><span class="sxs-lookup"><span data-stu-id="5c39d-132">A service can be hosted by another application, or it can be self-hosted.</span></span>  
  
 [<span data-ttu-id="5c39d-133">相互運用性と統合</span><span class="sxs-lookup"><span data-stu-id="5c39d-133">Interoperability and Integration</span></span>](../../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)  
 <span data-ttu-id="5c39d-134">COM+ でホストされるコンポーネント ベースのアプリケーション ロジックに多くの投資を行っている場合に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を使用して既存のロジックを修正することなく拡張する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-134">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to extend your existing logic rather than having to rewrite it if you have a substantial investment in component-based application logic hosted in COM+.</span></span>  
  
 [<span data-ttu-id="5c39d-135">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="5c39d-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 <span data-ttu-id="5c39d-136">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web プログラミング モデルについて説明します。このモデルを使用すると、開発者は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス操作を SOAP 以外のエンドポイントに公開できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5c39d-136">Describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming Model that allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span>  
  
 [<span data-ttu-id="5c39d-137">WCF 配信</span><span class="sxs-lookup"><span data-stu-id="5c39d-137">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 <span data-ttu-id="5c39d-138">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスから配信フィードを容易に公開できるようにするためのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-138">Describes support to easily expose syndication feeds from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 [<span data-ttu-id="5c39d-139">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="5c39d-139">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 <span data-ttu-id="5c39d-140">ASP.NET AJAX (Asynchronous JavaScript and XML) と、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが AJAX クライアントに操作を公開できるようにする JSON (JavaScript Object Notation) データ形式のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-140">Describes support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format to allow [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services to expose operations to AJAX clients.</span></span>  
  
 [<span data-ttu-id="5c39d-141">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="5c39d-141">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 <span data-ttu-id="5c39d-142">WS-Discovery プロトコルを使用して、相互運用可能な方法で実行時にサービスを探索可能にするためのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-142">Describes support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span>  
  
 [<span data-ttu-id="5c39d-143">ルーティング</span><span class="sxs-lookup"><span data-stu-id="5c39d-143">Routing</span></span>](../../../../docs/framework/wcf/feature-details/routing.md)  
 <span data-ttu-id="5c39d-144">ルーティング サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5c39d-144">Describes the routing service.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5c39d-145">参照</span><span class="sxs-lookup"><span data-stu-id="5c39d-145">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.ServiceModel.Routing>  
  
## <a name="related-sections"></a><span data-ttu-id="5c39d-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c39d-146">Related Sections</span></span>  
 [<span data-ttu-id="5c39d-147">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="5c39d-147">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
