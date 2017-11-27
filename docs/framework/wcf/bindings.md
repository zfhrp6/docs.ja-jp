---
title: "Windows Communication Foundation バインディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bindings [WCF]
ms.assetid: 845df323-be53-4848-92ef-ba67a406484d
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b458c0491ec91cd528b40fb19e93b7948f8c059a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communication-foundation-bindings"></a><span data-ttu-id="349ee-102">Windows Communication Foundation バインディング</span><span class="sxs-lookup"><span data-stu-id="349ee-102">Windows Communication Foundation Bindings</span></span>
<span data-ttu-id="349ee-103">バインディングは、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービス エンドポイントが他のエンドポイントと通信する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="349ee-103">Bindings specify how a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service endpoint communicates with other endpoints.</span></span> <span data-ttu-id="349ee-104">バインディングでは、まず、使用するトランスポート (HTTP や TCP など) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="349ee-104">At its most basic, a binding must specify the transport (for example, HTTP or TCP) to use.</span></span> <span data-ttu-id="349ee-105">セキュリティやトランザクションのサポートなど、その他の特性もバインディングによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="349ee-105">You can also set other characteristics, such as security and transaction support, through bindings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="349ee-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="349ee-106">In This Section</span></span>  
 [<span data-ttu-id="349ee-107">WCF のバインディングの概要</span><span class="sxs-lookup"><span data-stu-id="349ee-107">WCF Bindings Overview</span></span>](../../../docs/framework/wcf/bindings-overview.md)  
 <span data-ttu-id="349ee-108">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のバインディングの機能、システム指定のバインディング、およびバインディングを定義または変更する方法の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="349ee-108">Overview of what [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bindings do, what bindings the system provides, and how you can define or modify them.</span></span>  
  
 [<span data-ttu-id="349ee-109">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="349ee-109">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 <span data-ttu-id="349ee-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] に用意されているバインディングの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="349ee-110">A list of bindings included with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="349ee-111">これらのバインディングは、ほとんどのセキュリティ要件およびメッセージ パターン要件を満たします。</span><span class="sxs-lookup"><span data-stu-id="349ee-111">These bindings cover the majority of security and message pattern requirements.</span></span>  
  
 [<span data-ttu-id="349ee-112">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="349ee-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 <span data-ttu-id="349ee-113">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] バインディングには、サービス エンドポイントに接続するためにクライアントが使用しなければならない重要な情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="349ee-113">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] binding contains important information that clients must use to connect to service endpoints.</span></span>  
  
 [<span data-ttu-id="349ee-114">サービスのバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="349ee-114">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 <span data-ttu-id="349ee-115">管理者やインストール担当者は、構成を使用してサービス エンドポイントのバインディングをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="349ee-115">Configuration enables administrators and installers to customize the bindings for service endpoints.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="349ee-116">参照</span><span class="sxs-lookup"><span data-stu-id="349ee-116">Reference</span></span>  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="349ee-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="349ee-117">Related Sections</span></span>  
 [<span data-ttu-id="349ee-118">エンドポイント: アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="349ee-118">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
  
 [<span data-ttu-id="349ee-119">バインディング</span><span class="sxs-lookup"><span data-stu-id="349ee-119">Bindings</span></span>](../../../docs/framework/wcf/feature-details/bindings.md)  
  
## <a name="see-also"></a><span data-ttu-id="349ee-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="349ee-120">See Also</span></span>  
 [<span data-ttu-id="349ee-121">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="349ee-121">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
