---
title: "基本的な WCF プログラミング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- basic programming [WCF]
- WCF [WCF], basic programming
- WCF [WCF], programming
- Windows Communication Foundation [WCF], basic programming
- Windows Communication Foundation [WCF], programming
ms.assetid: 3ae3d498-f43c-4ecc-8cc0-6cbe36b62593
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fa43705fd20a60512ca4c460bb3048220aa1e193
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="basic-wcf-programming"></a><span data-ttu-id="cb61d-102">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="cb61d-102">Basic WCF Programming</span></span>
<span data-ttu-id="cb61d-103">ここでは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] アプリケーションを作成するときの基本を示します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-103">This section presents the fundamentals for creating [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb61d-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="cb61d-104">In This Section</span></span>  
 [<span data-ttu-id="cb61d-105">基本的なプログラミング ライフサイクル</span><span class="sxs-lookup"><span data-stu-id="cb61d-105">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 <span data-ttu-id="cb61d-106">設計、ビルド、展開から成る [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスおよびクライアント アプリケーションのライフサイクルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-106">Describes the lifecycle of designing, building, and deploying [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service and client applications.</span></span>  
  
 [<span data-ttu-id="cb61d-107">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="cb61d-107">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 <span data-ttu-id="cb61d-108">サービス コントラクトの設計および実装方法、メッセージ交換パターンの選択方法、エラー コントラクトの指定方法、およびその他のサービスの基本的な側面について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-108">Describes how to design and implement a service contract, choose a message exchange pattern, specify a fault contract, and other basic aspects of services.</span></span>  
  
 [<span data-ttu-id="cb61d-109">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="cb61d-109">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)  
 <span data-ttu-id="cb61d-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを構成して、コントラクト要件のサポート、ローカル ランタイム動作のカスタマイズ、およびサービスを公開するアドレスの指定を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-110">Describes how to configure a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service to support the contract requirements, customize local runtime behavior, and indicate the address to publish the service.</span></span>  
  
 [<span data-ttu-id="cb61d-111">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="cb61d-111">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
 <span data-ttu-id="cb61d-112">アプリケーションでサービスをホストするときの基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-112">Describes the basics of hosting services in an application.</span></span>  
  
 [<span data-ttu-id="cb61d-113">クライアントを構築する</span><span class="sxs-lookup"><span data-stu-id="cb61d-113">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 <span data-ttu-id="cb61d-114">サービスからのメタデータの取得、取得したメタデータの [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント コードへの変換、セキュリティ問題の処理、および [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントのビルド、構成、ホスティングを行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-114">Describes how to obtain metadata from services, convert that into [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client code, handle security issues, and build, configure, and host an [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span>  
  
 [<span data-ttu-id="cb61d-115">拡張機能の概要</span><span class="sxs-lookup"><span data-stu-id="cb61d-115">Introduction to Extensibility</span></span>](../../../docs/framework/wcf/introduction-to-extensibility.md)  
 <span data-ttu-id="cb61d-116">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を拡張してカスタム ソリューションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-116">Describes how to extend [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] to create custom solutions.</span></span>  
  
 [<span data-ttu-id="cb61d-117">WCF トラブルシューティング クイックスタート</span><span class="sxs-lookup"><span data-stu-id="cb61d-117">WCF Troubleshooting Quickstart</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)  
 <span data-ttu-id="cb61d-118">最も起こりやすい問題の一部を挙げ、その問題の解決方法とその問題の詳細情報を掲載している場所について説明します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-118">Describes some of the most common issues that occur, what you can do to solve them, and where to locate more information about the issue.</span></span>  
  
 [<span data-ttu-id="cb61d-119">WCF と ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="cb61d-119">WCF and ASP.NET Web API</span></span>](../../../docs/framework/wcf/wcf-and-aspnet-web-api.md)  
 <span data-ttu-id="cb61d-120">2 つのテクノロジ、そのテクノロジの相互関係、およびそのテクノロジを使用するタイミングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-120">Discusses the two technologies, how they relate to each other, and when to use them.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cb61d-121">参照</span><span class="sxs-lookup"><span data-stu-id="cb61d-121">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a><span data-ttu-id="cb61d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="cb61d-122">Related Sections</span></span>  
 [<span data-ttu-id="cb61d-123">システム要件</span><span class="sxs-lookup"><span data-stu-id="cb61d-123">System Requirements</span></span>](../../../docs/framework/wcf/wcf-system-requirements.md)  
  
 [<span data-ttu-id="cb61d-124">概念</span><span class="sxs-lookup"><span data-stu-id="cb61d-124">Conceptual Overview</span></span>](../../../docs/framework/wcf/conceptual-overview.md)  
  
 [<span data-ttu-id="cb61d-125">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="cb61d-125">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
  
 [<span data-ttu-id="cb61d-126">ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="cb61d-126">Guidelines and Best Practices</span></span>](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
  
 [<span data-ttu-id="cb61d-127">Windows Communication Foundation ツール</span><span class="sxs-lookup"><span data-stu-id="cb61d-127">Windows Communication Foundation Tools</span></span>](../../../docs/framework/wcf/tools.md)  
  
 [<span data-ttu-id="cb61d-128">Windows Communication Foundation サンプル</span><span class="sxs-lookup"><span data-stu-id="cb61d-128">Windows Communication Foundation Samples</span></span>](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [<span data-ttu-id="cb61d-129">はじめに</span><span class="sxs-lookup"><span data-stu-id="cb61d-129">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
  
 [<span data-ttu-id="cb61d-130">IIS ホストのインライン コードを使用します。</span><span class="sxs-lookup"><span data-stu-id="cb61d-130">IIS Hosting Using Inline Code</span></span>](../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)  
  
 [<span data-ttu-id="cb61d-131">自己ホストします。</span><span class="sxs-lookup"><span data-stu-id="cb61d-131">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
