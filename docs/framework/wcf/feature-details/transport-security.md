---
title: "トランスポート セキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 364326e2ded11f7174adc891a5fd9bcdd3c98334
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security"></a><span data-ttu-id="fe890-102">トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fe890-102">Transport Security</span></span>
<span data-ttu-id="fe890-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のトランスポート セキュリティは、選択したバインディングに依存します。</span><span class="sxs-lookup"><span data-stu-id="fe890-103">Transport security in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] depends on the binding selected.</span></span> <span data-ttu-id="fe890-104">バインディングが実装するトランスポートによって実際のセキュリティ機構が決まります。</span><span class="sxs-lookup"><span data-stu-id="fe890-104">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="fe890-105">このセクションの各トピックでは、実装される機構とそのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fe890-105">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fe890-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fe890-106">In This Section</span></span>  
 [<span data-ttu-id="fe890-107">トランスポート セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="fe890-107">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="fe890-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のトランスポート セキュリティの基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="fe890-108">Explains the basics of transport security in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="fe890-109">HTTP トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fe890-109">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)  
 <span data-ttu-id="fe890-110">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が SSL (Secure Sockets Layer)、つまり HTTPS を実装するしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fe890-110">Explains how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="fe890-111">HTTP 認証の理解</span><span class="sxs-lookup"><span data-stu-id="fe890-111">Understanding HTTP Authentication</span></span>](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)  
 <span data-ttu-id="fe890-112">HTTP 認証方式 (基本、ダイジェスト、NTLM (NT LAN Manager) など) について説明します。</span><span class="sxs-lookup"><span data-stu-id="fe890-112">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="fe890-113">トランスポート セキュリティでの偽装の使用</span><span class="sxs-lookup"><span data-stu-id="fe890-113">Using Impersonation with Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 <span data-ttu-id="fe890-114">トランスポート セキュリティ モードで使用できる 5 つの偽装レベルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fe890-114">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="fe890-115">方法 : SSL 証明書を使用してポートを構成する</span><span class="sxs-lookup"><span data-stu-id="fe890-115">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="fe890-116">SSL (トランスポート) セキュリティを実現するために、X.509 証明書を使用してコンピューターのポートを構成する際の基本事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="fe890-116">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fe890-117">参照</span><span class="sxs-lookup"><span data-stu-id="fe890-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="fe890-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe890-118">Related Sections</span></span>  
 [<span data-ttu-id="fe890-119">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="fe890-119">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="fe890-120">参照</span><span class="sxs-lookup"><span data-stu-id="fe890-120">See Also</span></span>  
 [<span data-ttu-id="fe890-121">WCF セキュリティのプログラミング</span><span class="sxs-lookup"><span data-stu-id="fe890-121">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
