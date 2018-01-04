---
title: "Windows Communication Foundation セキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
caps.latest.revision: "21"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2f2314c8def27bac9e64685d2af3cdd7639332f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="4c2b7-102">Windows Communication Foundation セキュリティ</span><span class="sxs-lookup"><span data-stu-id="4c2b7-102">Windows Communication Foundation Security</span></span>
<span data-ttu-id="4c2b7-103">このセクションの各トピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のセキュリティ機能、およびこれらの機能を使用してメッセージをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-103">The topics in this section describe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] security features and how to use them to help secure messages.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4c2b7-104">Windows Server AppFabric とセキュリティを参照してください[Windows Server AppFabric のセキュリティ モデル。](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span><span class="sxs-lookup"><span data-stu-id="4c2b7-104"> Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c2b7-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4c2b7-105">In This Section</span></span>  
 [<span data-ttu-id="4c2b7-106">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="4c2b7-106">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 <span data-ttu-id="4c2b7-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-107">Describes the security features in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="4c2b7-108">セキュリティの概念</span><span class="sxs-lookup"><span data-stu-id="4c2b7-108">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 <span data-ttu-id="4c2b7-109">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティで使用される基本的な用語と概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-109">Describes the basic terminology and concepts used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security.</span></span>  
  
 [<span data-ttu-id="4c2b7-110">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="4c2b7-110">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
 <span data-ttu-id="4c2b7-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で構成できるシナリオとトポロジについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-111">Describes scenarios and topologies you can configure with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="4c2b7-112">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="4c2b7-112">Security Behaviors</span></span>](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 <span data-ttu-id="4c2b7-113">資格情報の設定など、セキュリティに影響する WCF の動作に関する概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="4c2b7-114">バインディングとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="4c2b7-114">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 <span data-ttu-id="4c2b7-115">カスタム セキュリティ バインディングの作成方法を示すトピックなど、バインディングをセキュリティの観点から説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="4c2b7-116">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="4c2b7-116">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="4c2b7-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティ機能を使用して、メッセージをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-117">Describes how to secure messages using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security features.</span></span>  
  
 [<span data-ttu-id="4c2b7-118">認証</span><span class="sxs-lookup"><span data-stu-id="4c2b7-118">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
 <span data-ttu-id="4c2b7-119">一般的な認証タスクを示します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="4c2b7-120">承認</span><span class="sxs-lookup"><span data-stu-id="4c2b7-120">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
 <span data-ttu-id="4c2b7-121">セキュリティ実装を使用した一般的な承認シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="4c2b7-122">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="4c2b7-122">Federation and Issued Tokens</span></span>](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 <span data-ttu-id="4c2b7-123">フェデレーションの基本事項と、フェデレーション サーバーと通信するクライアントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="4c2b7-124">部分信頼</span><span class="sxs-lookup"><span data-stu-id="4c2b7-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)  
 <span data-ttu-id="4c2b7-125">部分的な信頼のシナリオを実行する方法と、部分的な信頼を実行するときの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の制限について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-125">Describes how to run partially-trusted scenarios and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="4c2b7-126">監査</span><span class="sxs-lookup"><span data-stu-id="4c2b7-126">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 <span data-ttu-id="4c2b7-127">セキュリティ イベントを監査する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="4c2b7-128">セキュリティ ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="4c2b7-128">Security Guidance and Best Practices</span></span>](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)  
 <span data-ttu-id="4c2b7-129">セキュリティで保護された [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションの作成に関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="4c2b7-129">Guidelines for creating secure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4c2b7-130">参照</span><span class="sxs-lookup"><span data-stu-id="4c2b7-130">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="4c2b7-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c2b7-131">Related Sections</span></span>  
 [<span data-ttu-id="4c2b7-132">WCF 機能の詳細</span><span class="sxs-lookup"><span data-stu-id="4c2b7-132">WCF Feature Details</span></span>](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [<span data-ttu-id="4c2b7-133">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="4c2b7-133">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [<span data-ttu-id="4c2b7-134">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="4c2b7-134">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="4c2b7-135">概念</span><span class="sxs-lookup"><span data-stu-id="4c2b7-135">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="4c2b7-136">参照</span><span class="sxs-lookup"><span data-stu-id="4c2b7-136">See Also</span></span>  
 [<span data-ttu-id="4c2b7-137">アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="4c2b7-137">Configuring Your Application</span></span>](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
