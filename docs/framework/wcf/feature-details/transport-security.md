---
title: トランスポート セキュリティ
ms.date: 03/30/2017
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e7f804d34a47c5508839636a6fe5045ebce3972e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498216"
---
# <a name="transport-security"></a><span data-ttu-id="2faf2-102">トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2faf2-102">Transport Security</span></span>
<span data-ttu-id="2faf2-103">Windows Communication Foundation (WCF) でのトランスポート セキュリティは、選択したバインディングによって異なります。</span><span class="sxs-lookup"><span data-stu-id="2faf2-103">Transport security in Windows Communication Foundation (WCF) depends on the binding selected.</span></span> <span data-ttu-id="2faf2-104">バインディングが実装するトランスポートによって実際のセキュリティ機構が決まります。</span><span class="sxs-lookup"><span data-stu-id="2faf2-104">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="2faf2-105">このセクションの各トピックでは、実装される機構とそのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2faf2-105">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2faf2-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2faf2-106">In This Section</span></span>  
 [<span data-ttu-id="2faf2-107">トランスポート セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="2faf2-107">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="2faf2-108">WCF でのトランスポート セキュリティの基礎を説明します。</span><span class="sxs-lookup"><span data-stu-id="2faf2-108">Explains the basics of transport security in WCF.</span></span>  
  
 [<span data-ttu-id="2faf2-109">HTTP トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="2faf2-109">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)  
 <span data-ttu-id="2faf2-110">WCF が、SSL (HTTPS) の Secure Sockets Layer を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2faf2-110">Explains how WCF implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="2faf2-111">HTTP 認証の理解</span><span class="sxs-lookup"><span data-stu-id="2faf2-111">Understanding HTTP Authentication</span></span>](../../../../docs/framework/wcf/feature-details/understanding-http-authentication.md)  
 <span data-ttu-id="2faf2-112">HTTP 認証方式 (基本、ダイジェスト、NTLM (NT LAN Manager) など) について説明します。</span><span class="sxs-lookup"><span data-stu-id="2faf2-112">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="2faf2-113">トランスポート セキュリティでの偽装の使用</span><span class="sxs-lookup"><span data-stu-id="2faf2-113">Using Impersonation with Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/using-impersonation-with-transport-security.md)  
 <span data-ttu-id="2faf2-114">トランスポート セキュリティ モードで使用できる 5 つの偽装レベルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2faf2-114">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="2faf2-115">方法 : SSL 証明書を使用してポートを構成する</span><span class="sxs-lookup"><span data-stu-id="2faf2-115">How to: Configure a Port with an SSL Certificate</span></span>](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="2faf2-116">SSL (トランスポート) セキュリティを実現するために、X.509 証明書を使用してコンピューターのポートを構成する際の基本事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="2faf2-116">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2faf2-117">参照</span><span class="sxs-lookup"><span data-stu-id="2faf2-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="2faf2-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2faf2-118">Related Sections</span></span>  
 [<span data-ttu-id="2faf2-119">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="2faf2-119">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="2faf2-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="2faf2-120">See Also</span></span>  
 [<span data-ttu-id="2faf2-121">WCF セキュリティのプログラミング</span><span class="sxs-lookup"><span data-stu-id="2faf2-121">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
