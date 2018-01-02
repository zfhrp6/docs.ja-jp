---
title: '&lt;dns&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c7585cfa85d805a3d1454b0c16e38eee297280a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltdnsgt"></a><span data-ttu-id="dcbc0-102">&lt;dns&gt;</span><span class="sxs-lookup"><span data-stu-id="dcbc0-102">&lt;dns&gt;</span></span>
<span data-ttu-id="dcbc0-103">予想されるサーバーの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="dcbc0-104">この ID は、同じ値を持つ DNS がサーバーの証明書に含まれていれば、X509 証明書の認証モードで有効です。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="dcbc0-105">さらに、SPN に同じ値があれば、Windows 認証モードでも有効です。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="dcbc0-106">要素の値の設定の詳細については、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="dcbc0-107">\<id ></span><span class="sxs-lookup"><span data-stu-id="dcbc0-107">\<identity></span></span>  
<span data-ttu-id="dcbc0-108">\<dns ></span><span class="sxs-lookup"><span data-stu-id="dcbc0-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbc0-109">構文</span><span class="sxs-lookup"><span data-stu-id="dcbc0-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcbc0-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="dcbc0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dcbc0-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcbc0-112">属性</span><span class="sxs-lookup"><span data-stu-id="dcbc0-112">Attributes</span></span>  
  
|<span data-ttu-id="dcbc0-113">属性</span><span class="sxs-lookup"><span data-stu-id="dcbc0-113">Attribute</span></span>|<span data-ttu-id="dcbc0-114">説明</span><span class="sxs-lookup"><span data-stu-id="dcbc0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dcbc0-115">value</span><span class="sxs-lookup"><span data-stu-id="dcbc0-115">value</span></span>|<span data-ttu-id="dcbc0-116">証明書の DNS です。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-116">The DNS of the certificate.</span></span> <span data-ttu-id="dcbc0-117">DNS は、IP ベースのネットワーク上でコンピューターを特定するために使用される業界標準のプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="dcbc0-118">ユーザーが表示名をなど覚え[http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929)または[http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165)、207.46.131.137 などの数値ベースのアドレスよりも簡単です。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-118">Users can remember display names, such as [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) or [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcbc0-119">子要素</span><span class="sxs-lookup"><span data-stu-id="dcbc0-119">Child Elements</span></span>  
 <span data-ttu-id="dcbc0-120">なし。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcbc0-121">親要素</span><span class="sxs-lookup"><span data-stu-id="dcbc0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dcbc0-122">要素</span><span class="sxs-lookup"><span data-stu-id="dcbc0-122">Element</span></span>|<span data-ttu-id="dcbc0-123">説明</span><span class="sxs-lookup"><span data-stu-id="dcbc0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcbc0-124">\<id ></span><span class="sxs-lookup"><span data-stu-id="dcbc0-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="dcbc0-125">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dcbc0-126">例</span><span class="sxs-lookup"><span data-stu-id="dcbc0-126">Example</span></span>  
 <span data-ttu-id="dcbc0-127">次の構成コードは、サーバーの認証に使用される X.509 証明書の DNS を指定します。</span><span class="sxs-lookup"><span data-stu-id="dcbc0-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dcbc0-128">参照</span><span class="sxs-lookup"><span data-stu-id="dcbc0-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="dcbc0-129">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="dcbc0-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="dcbc0-130">\<id ></span><span class="sxs-lookup"><span data-stu-id="dcbc0-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
