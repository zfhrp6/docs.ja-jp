---
title: "&lt;serviceCredentials&gt; の &lt;clientCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc4b3251a85a6926c93f418c154b4eabbd44092f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltclientcertificategt-of-ltservicecredentialsgt"></a><span data-ttu-id="e9983-102">&lt;serviceCredentials&gt; の &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="e9983-102">&lt;clientCertificate&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="e9983-103">双方向通信パターンでサービスからクライアントへのメッセージの署名および暗号化に使用される X.509 証明書を定義します。</span><span class="sxs-lookup"><span data-stu-id="e9983-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
 <span data-ttu-id="e9983-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e9983-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e9983-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="e9983-105">\<behaviors></span></span>  
<span data-ttu-id="e9983-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e9983-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e9983-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e9983-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="e9983-108">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="e9983-108">\<behavior></span></span>  
<span data-ttu-id="e9983-109">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e9983-109">\<serviceCredentials></span></span>  
<span data-ttu-id="e9983-110">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="e9983-110">\<clientCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9983-111">構文</span><span class="sxs-lookup"><span data-stu-id="e9983-111">Syntax</span></span>  
  
```xml  
<clientCertificate>  
 <certificate/>  
 <authentication/>  
</clientCertificate>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9983-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e9983-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e9983-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9983-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9983-114">属性</span><span class="sxs-lookup"><span data-stu-id="e9983-114">Attributes</span></span>  
 <span data-ttu-id="e9983-115">なし。</span><span class="sxs-lookup"><span data-stu-id="e9983-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9983-116">子要素</span><span class="sxs-lookup"><span data-stu-id="e9983-116">Child Elements</span></span>  
  
|<span data-ttu-id="e9983-117">要素</span><span class="sxs-lookup"><span data-stu-id="e9983-117">Element</span></span>|<span data-ttu-id="e9983-118">説明</span><span class="sxs-lookup"><span data-stu-id="e9983-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9983-119">\<認証 ></span><span class="sxs-lookup"><span data-stu-id="e9983-119">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)|<span data-ttu-id="e9983-120">クライアント証明書の認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="e9983-120">Specifies authentication options for the client certificate.</span></span>|  
|[<span data-ttu-id="e9983-121">\<証明書 ></span><span class="sxs-lookup"><span data-stu-id="e9983-121">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)|<span data-ttu-id="e9983-122">使用する証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9983-122">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9983-123">親要素</span><span class="sxs-lookup"><span data-stu-id="e9983-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e9983-124">要素</span><span class="sxs-lookup"><span data-stu-id="e9983-124">Element</span></span>|<span data-ttu-id="e9983-125">説明</span><span class="sxs-lookup"><span data-stu-id="e9983-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9983-126">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e9983-126">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="e9983-127">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="e9983-127">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9983-128">コメント</span><span class="sxs-lookup"><span data-stu-id="e9983-128">Remarks</span></span>  
 <span data-ttu-id="e9983-129">この要素は、サービスがクライアントと安全に通信するために、サービスが前もってクライアントの証明書を持っている必要がある場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="e9983-129">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="e9983-130">このような状況は、双方向通信パターンを使用する場合に生じます。</span><span class="sxs-lookup"><span data-stu-id="e9983-130">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="e9983-131">より一般的な要求/応答パターンでは、クライアントは自身の証明書を要求に含め、サービスはそれを使用してクライアントへの応答を暗号化し、署名します。</span><span class="sxs-lookup"><span data-stu-id="e9983-131">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="e9983-132">一方、双方向通信パターンでは、サービスにはクライアントからの要求が来ないので、クライアントの証明書をあらかじめ取得することで、クライアント宛のメッセージのセキュリティを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9983-132">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="e9983-133">このため、クライアントの証明書を帯域外のネゴシエーションで取得し、この要素を使用して証明書を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9983-133">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="e9983-134">双方向サービスの詳細については、次を参照してください。[する方法: 双方向コントラクトを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9983-134">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="e9983-135">この要素で設定される証明書は、`MutualCertificateDuplex` メッセージ セキュリティ認証モードで構成されているバインディングのみを対象に、クライアントへのメッセージを暗号化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9983-135">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9983-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9983-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>  
 [<span data-ttu-id="e9983-137">方法: 双方向コントラクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9983-137">How to: Create a Duplex Contract</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="e9983-138">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="e9983-138">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="e9983-139">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="e9983-139">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
