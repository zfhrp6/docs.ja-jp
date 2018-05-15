---
title: '&lt;Dns&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 6125bf157d04a1b0298a183465d11a18ac3786f0
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltdnsgt"></a><span data-ttu-id="24e0c-102">&lt;Dns&gt;</span><span class="sxs-lookup"><span data-stu-id="24e0c-102">&lt;dns&gt;</span></span>
<span data-ttu-id="24e0c-103">予想されるサーバーの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="24e0c-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="24e0c-104">この ID は、同じ値を持つ DNS がサーバーの証明書に含まれていれば、X509 証明書の認証モードで有効です。</span><span class="sxs-lookup"><span data-stu-id="24e0c-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="24e0c-105">さらに、SPN に同じ値があれば、Windows 認証モードでも有効です。</span><span class="sxs-lookup"><span data-stu-id="24e0c-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="24e0c-106">要素の値の設定の詳細については、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。</span><span class="sxs-lookup"><span data-stu-id="24e0c-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="24e0c-107">\<identity></span><span class="sxs-lookup"><span data-stu-id="24e0c-107">\<identity></span></span>  
<span data-ttu-id="24e0c-108">\<dns ></span><span class="sxs-lookup"><span data-stu-id="24e0c-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24e0c-109">構文</span><span class="sxs-lookup"><span data-stu-id="24e0c-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24e0c-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="24e0c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="24e0c-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="24e0c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24e0c-112">属性</span><span class="sxs-lookup"><span data-stu-id="24e0c-112">Attributes</span></span>  
  
|<span data-ttu-id="24e0c-113">属性</span><span class="sxs-lookup"><span data-stu-id="24e0c-113">Attribute</span></span>|<span data-ttu-id="24e0c-114">説明</span><span class="sxs-lookup"><span data-stu-id="24e0c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="24e0c-115">value</span><span class="sxs-lookup"><span data-stu-id="24e0c-115">value</span></span>|<span data-ttu-id="24e0c-116">証明書の DNS です。</span><span class="sxs-lookup"><span data-stu-id="24e0c-116">The DNS of the certificate.</span></span> <span data-ttu-id="24e0c-117">DNS は、IP ベースのネットワーク上でコンピューターを特定するために使用される業界標準のプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="24e0c-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="24e0c-118">ユーザーが表示名をなど覚え[ http://go.microsoft.com/fwlink/?prd=10929 ](http://go.microsoft.com/fwlink/?prd=10929)または[ http://go.microsoft.com/fwlink/?LinkID=96165 ](http://go.microsoft.com/fwlink/?LinkID=96165)、207.46.131.137 などの数値ベースのアドレスよりも簡単です。</span><span class="sxs-lookup"><span data-stu-id="24e0c-118">Users can remember display names, such as [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) or [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24e0c-119">子要素</span><span class="sxs-lookup"><span data-stu-id="24e0c-119">Child Elements</span></span>  
 <span data-ttu-id="24e0c-120">なし。</span><span class="sxs-lookup"><span data-stu-id="24e0c-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24e0c-121">親要素</span><span class="sxs-lookup"><span data-stu-id="24e0c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="24e0c-122">要素</span><span class="sxs-lookup"><span data-stu-id="24e0c-122">Element</span></span>|<span data-ttu-id="24e0c-123">説明</span><span class="sxs-lookup"><span data-stu-id="24e0c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="24e0c-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="24e0c-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="24e0c-125">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="24e0c-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="24e0c-126">例</span><span class="sxs-lookup"><span data-stu-id="24e0c-126">Example</span></span>  
 <span data-ttu-id="24e0c-127">次の構成コードは、サーバーの認証に使用される X.509 証明書の DNS を指定します。</span><span class="sxs-lookup"><span data-stu-id="24e0c-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24e0c-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="24e0c-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="24e0c-129">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="24e0c-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="24e0c-130">\<identity></span><span class="sxs-lookup"><span data-stu-id="24e0c-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
