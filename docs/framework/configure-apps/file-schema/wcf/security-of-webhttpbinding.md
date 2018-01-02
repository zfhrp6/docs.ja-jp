---
title: "&lt;webHttpBinding&gt; の &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 727cf3d2-6f56-48ad-a59f-ba423edb9c83
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3afd67e7f2d42cec458db7919529e09e4607f1ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltwebhttpbindinggt"></a><span data-ttu-id="b1510-102">&lt;webHttpBinding&gt; の &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="b1510-102">&lt;security&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="b1510-103">構成されるエンドポイントのセキュリティ要件を指定、 [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="b1510-103">Specifies the security requirements for an endpoint configured with a [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="b1510-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="b1510-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b1510-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b1510-105">\<bindings></span></span>  
<span data-ttu-id="b1510-106">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b1510-106">\<webHttpBinding></span></span>  
<span data-ttu-id="b1510-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b1510-107">\<binding></span></span>  
<span data-ttu-id="b1510-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="b1510-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1510-109">構文</span><span class="sxs-lookup"><span data-stu-id="b1510-109">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
    <bindings>  
        <webHttpBinding>  
            <binding name = "string">  
              <security mode="None/Transport/TransportCredentialOnly">  
                                    <transport clientCredentialType =   
                                     "Basic/Certificate/Digest/None/Ntlm/Windows"  
                                     proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                                     realm="string" />  
              </security>  
        </webHttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1510-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b1510-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b1510-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1510-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1510-112">属性</span><span class="sxs-lookup"><span data-stu-id="b1510-112">Attributes</span></span>  
  
|<span data-ttu-id="b1510-113">属性</span><span class="sxs-lookup"><span data-stu-id="b1510-113">Attribute</span></span>|<span data-ttu-id="b1510-114">説明</span><span class="sxs-lookup"><span data-stu-id="b1510-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1510-115">モード</span><span class="sxs-lookup"><span data-stu-id="b1510-115">mode</span></span>|<span data-ttu-id="b1510-116">トランスポート レベルのセキュリティをエンドポイントで使用するか、セキュリティを使用しないかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b1510-116">Specifies whether transport-level security or no security is used by an endpoint.</span></span> <span data-ttu-id="b1510-117">既定値は、`None` です。</span><span class="sxs-lookup"><span data-stu-id="b1510-117">The default is `None`.</span></span> <span data-ttu-id="b1510-118">この属性は <xref:System.ServiceModel.WebHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="b1510-118">This attribute is of type <xref:System.ServiceModel.WebHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b1510-119">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="b1510-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="b1510-120">値</span><span class="sxs-lookup"><span data-stu-id="b1510-120">Value</span></span>|<span data-ttu-id="b1510-121">説明</span><span class="sxs-lookup"><span data-stu-id="b1510-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1510-122">なし</span><span class="sxs-lookup"><span data-stu-id="b1510-122">None</span></span>|<span data-ttu-id="b1510-123">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="b1510-123">Security is disabled.</span></span>|  
|<span data-ttu-id="b1510-124">Transport</span><span class="sxs-lookup"><span data-stu-id="b1510-124">Transport</span></span>|<span data-ttu-id="b1510-125">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="b1510-125">Security is provided using HTTPS.</span></span> <span data-ttu-id="b1510-126">サービスは、SSL 証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1510-126">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="b1510-127">メッセージは、HTTPS およびサービスを使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。</span><span class="sxs-lookup"><span data-stu-id="b1510-127">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="b1510-128">クライアントの認証はによって制御されます、`ClientCredentialType`の属性、 [\<トランスポート >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="b1510-128">The client authentication is controlled through the `ClientCredentialType` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md).</span></span>|  
|<span data-ttu-id="b1510-129">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="b1510-129">TransportCredentialOnly</span></span>|<span data-ttu-id="b1510-130">このモードは、メッセージの整合性と機密性を提供しません。</span><span class="sxs-lookup"><span data-stu-id="b1510-130">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="b1510-131">HTTP ベースのクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="b1510-131">It provides HTTP-based client authentication.</span></span> <span data-ttu-id="b1510-132">このモードを使用するときは、十分に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1510-132">This mode should be used with caution.</span></span> <span data-ttu-id="b1510-133">トランスポート セキュリティが他の方法 (IPSec など) で提供され、クライアント認証だけが [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] インフラストラクチャで提供されている環境で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1510-133">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1510-134">子要素</span><span class="sxs-lookup"><span data-stu-id="b1510-134">Child Elements</span></span>  
  
|<span data-ttu-id="b1510-135">要素</span><span class="sxs-lookup"><span data-stu-id="b1510-135">Element</span></span>|<span data-ttu-id="b1510-136">説明</span><span class="sxs-lookup"><span data-stu-id="b1510-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1510-137">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="b1510-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-webhttpbinding.md)|<span data-ttu-id="b1510-138">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="b1510-138">Defines the transport security settings.</span></span> <span data-ttu-id="b1510-139">この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="b1510-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1510-140">親要素</span><span class="sxs-lookup"><span data-stu-id="b1510-140">Parent Elements</span></span>  
  
|<span data-ttu-id="b1510-141">要素</span><span class="sxs-lookup"><span data-stu-id="b1510-141">Element</span></span>|<span data-ttu-id="b1510-142">説明</span><span class="sxs-lookup"><span data-stu-id="b1510-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1510-143">\<webHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="b1510-143">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|<span data-ttu-id="b1510-144">SOAP メッセージに代わって HTTP 要求に応答する [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web サービスのエンドポイントを構成するために使用するバインド要素。</span><span class="sxs-lookup"><span data-stu-id="b1510-144">A binding element that is used to configure endpoints for [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Web services that respond to HTTP requests instead of SOAP messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1510-145">参照</span><span class="sxs-lookup"><span data-stu-id="b1510-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.WebHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.WebHttpSecurity>  
 [<span data-ttu-id="b1510-146">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="b1510-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="b1510-147">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="b1510-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="b1510-148">バインディング</span><span class="sxs-lookup"><span data-stu-id="b1510-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b1510-149">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="b1510-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="b1510-150">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="b1510-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="b1510-151">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="b1510-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="b1510-152">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="b1510-152">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
