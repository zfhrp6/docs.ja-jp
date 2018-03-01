---
title: "Windows Communication Foundation エンドポイント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0725c4f4275853cce958072a57d7f6ca4059e8cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="24b0c-102">Windows Communication Foundation エンドポイント</span><span class="sxs-lookup"><span data-stu-id="24b0c-102">Windows Communication Foundation Endpoints</span></span>
<span data-ttu-id="24b0c-103">すべての通信、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]サービスが使用して行われる、*エンドポイント*サービス。</span><span class="sxs-lookup"><span data-stu-id="24b0c-103">All communication with a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="24b0c-104">エンドポイントは、クライアントが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスによって提供される機能にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="24b0c-104">Endpoints provide clients access to the functionality that a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service offers.</span></span>  
  
 <span data-ttu-id="24b0c-105">エンドポイントを作成する方法の詳細については、次を参照してください。[エンドポイントの作成の概要](../../../docs/framework/wcf/endpoint-creation-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="24b0c-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> <span data-ttu-id="24b0c-106">エンドポイントは次の要素から成ります。</span><span class="sxs-lookup"><span data-stu-id="24b0c-106">Each endpoint contains:</span></span>  
  
-   <span data-ttu-id="24b0c-107">そのエンドポイントの場所を示すアドレス。</span><span class="sxs-lookup"><span data-stu-id="24b0c-107">An address that indicates where to find the endpoint.</span></span>  
  
-   <span data-ttu-id="24b0c-108">クライアントがエンドポイントと通信する方法を指定するバインディング。</span><span class="sxs-lookup"><span data-stu-id="24b0c-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
-   <span data-ttu-id="24b0c-109">利用可能なメソッドを指定するためのコントラクト。</span><span class="sxs-lookup"><span data-stu-id="24b0c-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="24b0c-110">エンドポイントを構成する個々の要素を指定する方法については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24b0c-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
-   [<span data-ttu-id="24b0c-111">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="24b0c-111">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
  
-   [<span data-ttu-id="24b0c-112">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="24b0c-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
  
-   [<span data-ttu-id="24b0c-113">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="24b0c-113">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="24b0c-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="24b0c-114">In This Section</span></span>  
 [<span data-ttu-id="24b0c-115">エンドポイントの作成の概要</span><span class="sxs-lookup"><span data-stu-id="24b0c-115">Endpoint Creation Overview</span></span>](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 <span data-ttu-id="24b0c-116">エンドポイントの構造を説明し、構成やコード内にエンドポイントを定義する方法と、ランタイムによって提供される既定のエンドポイント、バインディング、および動作の使用方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="24b0c-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="24b0c-117">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="24b0c-117">Specifying an Endpoint Address</span></span>](../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 <span data-ttu-id="24b0c-118">エンドポイントを通して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスと通信する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="24b0c-118">Describes how communication with a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="24b0c-119">方法 : 構成にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="24b0c-119">How to: Create a Service Endpoint in Configuration</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="24b0c-120">構成でサービス エンドポイントを作成する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="24b0c-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="24b0c-121">方法 : コード内にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="24b0c-121">How to: Create a Service Endpoint in Code</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="24b0c-122">コードでサービス エンドポイントを作成する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="24b0c-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="24b0c-123">メタデータ エンドポイントを公開する</span><span class="sxs-lookup"><span data-stu-id="24b0c-123">Publishing Metadata Endpoints</span></span>](../../../docs/framework/wcf/publishing-metadata-endpoints.md)  
 <span data-ttu-id="24b0c-124">構成およびコードでメタデータ エンドポイントを公開することによりってメタデータを公開する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="24b0c-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="24b0c-125">参照</span><span class="sxs-lookup"><span data-stu-id="24b0c-125">Reference</span></span>  
 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="24b0c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="24b0c-126">Related Sections</span></span>  
 [<span data-ttu-id="24b0c-127">基本的なプログラミング ライフサイクル</span><span class="sxs-lookup"><span data-stu-id="24b0c-127">Basic Programming Lifecycle</span></span>](../../../docs/framework/wcf/basic-programming-lifecycle.md)
