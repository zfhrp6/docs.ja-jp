---
title: Windows Communication Foundation バインディング
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF]
ms.assetid: 845df323-be53-4848-92ef-ba67a406484d
ms.openlocfilehash: 188d132a4695bec0725efbaae3e4ed4d2cb17c3b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803596"
---
# <a name="windows-communication-foundation-bindings"></a><span data-ttu-id="0c05a-102">Windows Communication Foundation バインディング</span><span class="sxs-lookup"><span data-stu-id="0c05a-102">Windows Communication Foundation Bindings</span></span>
<span data-ttu-id="0c05a-103">バインディングは、Windows Communication Foundation (WCF) サービス エンドポイントが他のエンドポイントと通信する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c05a-103">Bindings specify how a Windows Communication Foundation (WCF) service endpoint communicates with other endpoints.</span></span> <span data-ttu-id="0c05a-104">バインディングでは、まず、使用するトランスポート (HTTP や TCP など) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c05a-104">At its most basic, a binding must specify the transport (for example, HTTP or TCP) to use.</span></span> <span data-ttu-id="0c05a-105">セキュリティやトランザクションのサポートなど、その他の特性もバインディングによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="0c05a-105">You can also set other characteristics, such as security and transaction support, through bindings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c05a-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0c05a-106">In This Section</span></span>  
 [<span data-ttu-id="0c05a-107">WCF のバインディングの概要</span><span class="sxs-lookup"><span data-stu-id="0c05a-107">WCF Bindings Overview</span></span>](../../../docs/framework/wcf/bindings-overview.md)  
 <span data-ttu-id="0c05a-108">WCF バインディングの概要については、システムを提供するバインディングと定義または変更する方法です。</span><span class="sxs-lookup"><span data-stu-id="0c05a-108">Overview of what WCF bindings do, what bindings the system provides, and how you can define or modify them.</span></span>  
  
 [<span data-ttu-id="0c05a-109">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="0c05a-109">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 <span data-ttu-id="0c05a-110">WCF に付属のバインドの一覧です。</span><span class="sxs-lookup"><span data-stu-id="0c05a-110">A list of bindings included with WCF.</span></span> <span data-ttu-id="0c05a-111">これらのバインディングは、ほとんどのセキュリティ要件およびメッセージ パターン要件を満たします。</span><span class="sxs-lookup"><span data-stu-id="0c05a-111">These bindings cover the majority of security and message pattern requirements.</span></span>  
  
 [<span data-ttu-id="0c05a-112">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="0c05a-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 <span data-ttu-id="0c05a-113">WCF バインディングには、クライアントがサービス エンドポイントへの接続に使用する必要がある重要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c05a-113">A WCF binding contains important information that clients must use to connect to service endpoints.</span></span>  
  
 [<span data-ttu-id="0c05a-114">サービスのバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="0c05a-114">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 <span data-ttu-id="0c05a-115">管理者やインストール担当者は、構成を使用してサービス エンドポイントのバインディングをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="0c05a-115">Configuration enables administrators and installers to customize the bindings for service endpoints.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0c05a-116">参照</span><span class="sxs-lookup"><span data-stu-id="0c05a-116">Reference</span></span>  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="0c05a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c05a-117">Related Sections</span></span>  
 [<span data-ttu-id="0c05a-118">エンドポイント : アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="0c05a-118">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
  
 [<span data-ttu-id="0c05a-119">バインディング</span><span class="sxs-lookup"><span data-stu-id="0c05a-119">Bindings</span></span>](../../../docs/framework/wcf/feature-details/bindings.md)  
  
## <a name="see-also"></a><span data-ttu-id="0c05a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c05a-120">See Also</span></span>  
 [<span data-ttu-id="0c05a-121">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="0c05a-121">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
