---
title: "&lt;identity&gt; の &lt;certificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4aeccaf7-8f23-495c-aa5f-5bd8b5d4a10c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c1fb253ed166b4e8106f68bf2782cf215541294
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificategt-for-ltidentitygt"></a><span data-ttu-id="74458-102">&lt;identity&gt; の &lt;certificate&gt;</span><span class="sxs-lookup"><span data-stu-id="74458-102">&lt;certificate&gt; for &lt;identity&gt;</span></span>
<span data-ttu-id="74458-103">クライアントに対するサービスの検証に使用される X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="74458-103">Specifies an X.509 certificate used to validate a server to a client.</span></span>  
  
 <span data-ttu-id="74458-104">要素の値の設定の詳細については、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。</span><span class="sxs-lookup"><span data-stu-id="74458-104">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="74458-105">\<id ></span><span class="sxs-lookup"><span data-stu-id="74458-105">\<identity></span></span>  
<span data-ttu-id="74458-106">\<証明書 ></span><span class="sxs-lookup"><span data-stu-id="74458-106">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74458-107">構文</span><span class="sxs-lookup"><span data-stu-id="74458-107">Syntax</span></span>  
  
```xml  
<certificate encodedValue = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74458-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="74458-108">Attributes and Elements</span></span>  
 <span data-ttu-id="74458-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="74458-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74458-110">属性</span><span class="sxs-lookup"><span data-stu-id="74458-110">Attributes</span></span>  
  
|<span data-ttu-id="74458-111">属性</span><span class="sxs-lookup"><span data-stu-id="74458-111">Attribute</span></span>|<span data-ttu-id="74458-112">説明</span><span class="sxs-lookup"><span data-stu-id="74458-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74458-113">encodedValue</span><span class="sxs-lookup"><span data-stu-id="74458-113">encodedValue</span></span>|<span data-ttu-id="74458-114">証明書の Base64 エンコーディングです。</span><span class="sxs-lookup"><span data-stu-id="74458-114">A Base64 encoding of the certificate.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74458-115">子要素</span><span class="sxs-lookup"><span data-stu-id="74458-115">Child Elements</span></span>  
 <span data-ttu-id="74458-116">なし。</span><span class="sxs-lookup"><span data-stu-id="74458-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="74458-117">親要素</span><span class="sxs-lookup"><span data-stu-id="74458-117">Parent Elements</span></span>  
  
|<span data-ttu-id="74458-118">要素</span><span class="sxs-lookup"><span data-stu-id="74458-118">Element</span></span>|<span data-ttu-id="74458-119">説明</span><span class="sxs-lookup"><span data-stu-id="74458-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74458-120">\<id ></span><span class="sxs-lookup"><span data-stu-id="74458-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="74458-121">クライアントで認証するサービスの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="74458-121">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="74458-122">例</span><span class="sxs-lookup"><span data-stu-id="74458-122">Example</span></span>  
 <span data-ttu-id="74458-123">次のコードは、クライアントに対するサーバーの検証に使用される証明書のエンコードされた表現を指定します。</span><span class="sxs-lookup"><span data-stu-id="74458-123">The following code specifies the encoded representation of a certificate used to validate a server to a client.</span></span>  
  
```xml  
<identity>  
  <certificate encodedValue = " MIIBxjCCAXSgAwIBAgIQmXJgyu9tro1M98GifjtuoDAJBgUrDgMCHQUAMBYxFDASBgNVBAMTC1Jvb3QgQWdlbmN5MB4XDTA2MDUxNzIxNDQyNVoXDTM5MTIzMTIzNTk1OVowKTEQMA4GA1UEChMHQ29udG9zbzEVMBMGA1UEAxMMaWRlbnRpdHkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQDBmivcb8hYbh11hqVoDuB7zmJ2y230f" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="74458-124">参照</span><span class="sxs-lookup"><span data-stu-id="74458-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.EndpointIdentity>  
 [<span data-ttu-id="74458-125">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="74458-125">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="74458-126">\<id ></span><span class="sxs-lookup"><span data-stu-id="74458-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
