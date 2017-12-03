---
title: "&lt;clientCredentials&gt; 要素の &lt;serviceCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3fbb3ef0fddd287fa3feb30732b26c651ac0067
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="7f331-102">&lt;clientCredentials&gt; 要素の &lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="7f331-102">&lt;serviceCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="7f331-103">クライアントに対してサービスを認証する際に使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f331-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="7f331-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7f331-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f331-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="7f331-105">\<behaviors></span></span>  
<span data-ttu-id="7f331-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7f331-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="7f331-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="7f331-107">\<behavior></span></span>  
<span data-ttu-id="7f331-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="7f331-108">\<clientCredentials></span></span>  
<span data-ttu-id="7f331-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="7f331-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f331-110">構文</span><span class="sxs-lookup"><span data-stu-id="7f331-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f331-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7f331-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7f331-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f331-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f331-113">属性</span><span class="sxs-lookup"><span data-stu-id="7f331-113">Attributes</span></span>  
 <span data-ttu-id="7f331-114">なし。</span><span class="sxs-lookup"><span data-stu-id="7f331-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7f331-115">子要素</span><span class="sxs-lookup"><span data-stu-id="7f331-115">Child Elements</span></span>  
  
|<span data-ttu-id="7f331-116">要素</span><span class="sxs-lookup"><span data-stu-id="7f331-116">Element</span></span>|<span data-ttu-id="7f331-117">説明</span><span class="sxs-lookup"><span data-stu-id="7f331-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f331-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="7f331-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="7f331-119">ネゴシエーション プロトコル経由でサービスまたは STS が証明書を提供しないときに使用される X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f331-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="7f331-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="7f331-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="7f331-121">認証用の (範囲指定された) 特定のサービスにより提供される X.509 証明書のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="7f331-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="7f331-122">このコレクションは一般に、フェデレーション シナリオでセキュリティ トークン サービスのサービス証明書を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7f331-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="7f331-123">\<認証 ></span><span class="sxs-lookup"><span data-stu-id="7f331-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="7f331-124">クライアントで使用されるサービス証明書の認証動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f331-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7f331-125">親要素</span><span class="sxs-lookup"><span data-stu-id="7f331-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7f331-126">要素</span><span class="sxs-lookup"><span data-stu-id="7f331-126">Element</span></span>|<span data-ttu-id="7f331-127">説明</span><span class="sxs-lookup"><span data-stu-id="7f331-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f331-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="7f331-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="7f331-129">サービスに対するクライアント自身の認証のためにクライアントによって使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f331-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f331-130">コメント</span><span class="sxs-lookup"><span data-stu-id="7f331-130">Remarks</span></span>  
 <span data-ttu-id="7f331-131">この構成要素は、SSL 認証を使用してサービスから提示された証明書を検証するためにクライアントが使用する設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f331-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="7f331-132">また、このクラスには、メッセージ セキュリティを使用してサービスへのメッセージを暗号化するためにクライアントで明示的に構成される、サービスの証明書も含まれます。</span><span class="sxs-lookup"><span data-stu-id="7f331-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="7f331-133">属性、`serviceCertificate`要素は同一の属性を[ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f331-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f331-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f331-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [<span data-ttu-id="7f331-135">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="7f331-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="7f331-136">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="7f331-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="7f331-137">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="7f331-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="7f331-138">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="7f331-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
