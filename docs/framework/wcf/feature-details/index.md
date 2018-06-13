---
title: WCF 機能の詳細
ms.date: 03/30/2017
helpviewer_keywords:
- features [WCF]
- WCF, features
- Windows Communication Foundation, features
ms.assetid: 9b4368ca-0bd3-40dc-a539-bcd5779cee5f
ms.openlocfilehash: c97bd891f0bbb58f8b267296b9b53e00a5486622
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494710"
---
# <a name="wcf-feature-details"></a><span data-ttu-id="c9efc-102">WCF 機能の詳細</span><span class="sxs-lookup"><span data-stu-id="c9efc-102">WCF Feature Details</span></span>
<span data-ttu-id="c9efc-103">Windows Communication Foundation (WCF) では、アプリケーションのメッセージング機能の広範な制御をできます。</span><span class="sxs-lookup"><span data-stu-id="c9efc-103">Windows Communication Foundation (WCF) allows extensive control over the messaging functions of an application.</span></span> <span data-ttu-id="c9efc-104">このセクションの各トピックでは、使用できる機能について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-104">The topics in this section go into detail about the available features.</span></span> <span data-ttu-id="c9efc-105">基本的なプログラミングの詳細については、次を参照してください。[基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9efc-105">For more information about basic programming, see [Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9efc-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c9efc-106">In This Section</span></span>  
 [<span data-ttu-id="c9efc-107">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="c9efc-107">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 <span data-ttu-id="c9efc-108">ワークフロー サービスを作成および構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-108">Describes how to create and configure workflow services.</span></span>  
  
 [<span data-ttu-id="c9efc-109">エンドポイント : アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="c9efc-109">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 <span data-ttu-id="c9efc-110">サービスのさまざまな側面を制御する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-110">Describes how to control multiple aspects of your service.</span></span>  
  
 [<span data-ttu-id="c9efc-111">データ転送とシリアル化</span><span class="sxs-lookup"><span data-stu-id="c9efc-111">Data Transfer and Serialization</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)  
 <span data-ttu-id="c9efc-112">相互運用性または将来の互換性を実現するために、データのシリアル化を調整する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-112">Describes how serialization of data can be tailored for interoperation or future compatibility.</span></span>  
  
 [<span data-ttu-id="c9efc-113">セッション、インスタンス化、および同時実行</span><span class="sxs-lookup"><span data-stu-id="c9efc-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 <span data-ttu-id="c9efc-114">WCF と、アプリケーションに適したモードを選択する方法のインスタンス化とセッション モードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-114">Describes the instancing and session modes of WCF and how to select the right mode for your application.</span></span>  
  
 [<span data-ttu-id="c9efc-115">トランスポート</span><span class="sxs-lookup"><span data-stu-id="c9efc-115">Transports</span></span>](../../../../docs/framework/wcf/feature-details/transports.md)  
 <span data-ttu-id="c9efc-116">チャネル スタックの最も低いレベルにあるトランスポート層を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-116">Describes how to configure the transport layer, the lowest level of the channel stack.</span></span>  
  
 [<span data-ttu-id="c9efc-117">キューと信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="c9efc-117">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)  
 <span data-ttu-id="c9efc-118">キューについて説明します。キューは、送信元アプリケーションが送ったメッセージを受信側アプリケーションに代わって保存しておき、後で受信側アプリケーションに転送します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-118">Describes queues, which store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span>  
  
 [<span data-ttu-id="c9efc-119">トランザクション</span><span class="sxs-lookup"><span data-stu-id="c9efc-119">Transactions</span></span>](../../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)  
 <span data-ttu-id="c9efc-120">必要に応じてロールバックできるトランザクション操作を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-120">Explains how to create transacted operations that can be rolled back if needed.</span></span>  
  
 [<span data-ttu-id="c9efc-121">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="c9efc-121">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)  
 <span data-ttu-id="c9efc-122">WCF セキュリティは、機密性と整合性のあるアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-122">Describes how WCF security helps you to create applications that have confidentiality and integrity.</span></span> <span data-ttu-id="c9efc-123">監査機能として、認証と承認を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9efc-123">Authentication and authorization are also available, as are auditing features.</span></span>  
  
 [<span data-ttu-id="c9efc-124">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="c9efc-124">Peer-to-Peer Networking</span></span>](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 <span data-ttu-id="c9efc-125">ビア サービスとクライアントを作成する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-125">Details how to create peer services and clients.</span></span>  
  
 [<span data-ttu-id="c9efc-126">メタデータ</span><span class="sxs-lookup"><span data-stu-id="c9efc-126">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 <span data-ttu-id="c9efc-127">メタデータのアーキテクチャと形式について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-127">Describes metadata architecture and formats.</span></span>  
  
 [<span data-ttu-id="c9efc-128">クライアント</span><span class="sxs-lookup"><span data-stu-id="c9efc-128">Clients</span></span>](../../../../docs/framework/wcf/feature-details/clients.md)  
 <span data-ttu-id="c9efc-129">サービスにアクセスするさまざまなクライアントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-129">Describes how to create a variety of clients that access services.</span></span>  
  
 [<span data-ttu-id="c9efc-130">ホスティング</span><span class="sxs-lookup"><span data-stu-id="c9efc-130">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 <span data-ttu-id="c9efc-131">ホストについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-131">Describes hosting.</span></span> <span data-ttu-id="c9efc-132">サービスは、別のアプリケーションまたは自己ホストを使用してホストできます。</span><span class="sxs-lookup"><span data-stu-id="c9efc-132">A service can be hosted by another application, or it can be self-hosted.</span></span>  
  
 [<span data-ttu-id="c9efc-133">相互運用性と統合</span><span class="sxs-lookup"><span data-stu-id="c9efc-133">Interoperability and Integration</span></span>](../../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)  
 <span data-ttu-id="c9efc-134">WCF を使用して、既存のロジックを COM + でホストされるコンポーネント ベースのアプリケーション ロジックにかなりの投資がある場合は、これを修正することがなく拡張する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-134">Describes how to use WCF to extend your existing logic rather than having to rewrite it if you have a substantial investment in component-based application logic hosted in COM+.</span></span>  
  
 [<span data-ttu-id="c9efc-135">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="c9efc-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 <span data-ttu-id="c9efc-136">WCF Web プログラミング モデルにより、開発者は WCF サービス操作を SOAP 以外のエンドポイントを公開することについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-136">Describes the WCF Web Programming Model that allows developers to expose WCF service operations to non-SOAP endpoints.</span></span>  
  
 [<span data-ttu-id="c9efc-137">WCF 配信</span><span class="sxs-lookup"><span data-stu-id="c9efc-137">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)  
 <span data-ttu-id="c9efc-138">WCF サービスから配信フィードを簡単に公開するサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-138">Describes support to easily expose syndication feeds from a WCF service.</span></span>  
  
 [<span data-ttu-id="c9efc-139">AJAX の統合と JSON のサポート</span><span class="sxs-lookup"><span data-stu-id="c9efc-139">AJAX Integration and JSON Support</span></span>](../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 <span data-ttu-id="c9efc-140">ASP.NET Asynchronous JavaScript および XML (AJAX) と JavaScript Object Notation (JSON) データ形式のために WCF サービスを AJAX クライアントに操作を公開するサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-140">Describes support for ASP.NET Asynchronous JavaScript and XML (AJAX) and the JavaScript Object Notation (JSON) data format to allow WCF services to expose operations to AJAX clients.</span></span>  
  
 [<span data-ttu-id="c9efc-141">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="c9efc-141">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 <span data-ttu-id="c9efc-142">WS-Discovery プロトコルを使用して、相互運用可能な方法で実行時にサービスを探索可能にするためのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-142">Describes support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span>  
  
 [<span data-ttu-id="c9efc-143">ルーティング</span><span class="sxs-lookup"><span data-stu-id="c9efc-143">Routing</span></span>](../../../../docs/framework/wcf/feature-details/routing.md)  
 <span data-ttu-id="c9efc-144">ルーティング サービスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c9efc-144">Describes the routing service.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c9efc-145">参照</span><span class="sxs-lookup"><span data-stu-id="c9efc-145">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.ServiceModel.Routing>  
  
## <a name="related-sections"></a><span data-ttu-id="c9efc-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9efc-146">Related Sections</span></span>  
 [<span data-ttu-id="c9efc-147">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="c9efc-147">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
