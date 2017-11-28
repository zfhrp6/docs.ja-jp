---
title: "&lt;netHttpBinding&gt; の &lt;security"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63d65ea50babd0cd4aa7ee92cdd6d2b281dcbc26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="417ae-102">&lt;netHttpBinding&gt; の &lt;security</span><span class="sxs-lookup"><span data-stu-id="417ae-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="417ae-103">セキュリティ機能を定義、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="417ae-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="417ae-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="417ae-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="417ae-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="417ae-105">\<bindings></span></span>  
<span data-ttu-id="417ae-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="417ae-106">\<netHttpBinding></span></span>  
<span data-ttu-id="417ae-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="417ae-107">\<binding></span></span>  
<span data-ttu-id="417ae-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="417ae-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="417ae-109">構文</span><span class="sxs-lookup"><span data-stu-id="417ae-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="417ae-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="417ae-110">Attributes and Elements</span></span>  
 <span data-ttu-id="417ae-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="417ae-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="417ae-112">属性</span><span class="sxs-lookup"><span data-stu-id="417ae-112">Attributes</span></span>  
  
|<span data-ttu-id="417ae-113">属性</span><span class="sxs-lookup"><span data-stu-id="417ae-113">Attribute</span></span>|<span data-ttu-id="417ae-114">説明</span><span class="sxs-lookup"><span data-stu-id="417ae-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="417ae-115">モード</span><span class="sxs-lookup"><span data-stu-id="417ae-115">mode</span></span>|<span data-ttu-id="417ae-116">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="417ae-116">Optional.</span></span> <span data-ttu-id="417ae-117">使用されるセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="417ae-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="417ae-118">既定値は、`None` です。</span><span class="sxs-lookup"><span data-stu-id="417ae-118">The default is `None`.</span></span> <span data-ttu-id="417ae-119">この属性は型<!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`です。</span><span class="sxs-lookup"><span data-stu-id="417ae-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="417ae-120">mode 属性</span><span class="sxs-lookup"><span data-stu-id="417ae-120">mode Attribute</span></span>  
  
|<span data-ttu-id="417ae-121">値</span><span class="sxs-lookup"><span data-stu-id="417ae-121">Value</span></span>|<span data-ttu-id="417ae-122">説明</span><span class="sxs-lookup"><span data-stu-id="417ae-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="417ae-123">なし</span><span class="sxs-lookup"><span data-stu-id="417ae-123">None</span></span>|<span data-ttu-id="417ae-124">メッセージの数は、転送中にセキュリティ保護されていません。</span><span class="sxs-lookup"><span data-stu-id="417ae-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="417ae-125">Transport</span><span class="sxs-lookup"><span data-stu-id="417ae-125">Transport</span></span>|<span data-ttu-id="417ae-126">セキュリティは、HTTPS トランスポートを使用して提供されます。</span><span class="sxs-lookup"><span data-stu-id="417ae-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="417ae-127">SOAP メッセージは、HTTPS を使用したセキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="417ae-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="417ae-128">サービスは、サービスの X.509 証明書を使用してクライアントに認証されます。</span><span class="sxs-lookup"><span data-stu-id="417ae-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="417ae-129">クライアントは、提供される ClientCredentialType を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="417ae-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="417ae-130">メッセージ</span><span class="sxs-lookup"><span data-stu-id="417ae-130">Message</span></span>|<span data-ttu-id="417ae-131">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="417ae-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="417ae-132">既定では、本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="417ae-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="417ae-133">このバインディングの場合、サーバー証明書をクライアントの帯域外で提供するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="417ae-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="417ae-134">このバインディングの唯一の有効な `ClientCredentialType` は、`Certificate` です。</span><span class="sxs-lookup"><span data-stu-id="417ae-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="417ae-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="417ae-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="417ae-136">整合性、機密性、およびサーバー認証は、トランスポート セキュリティによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="417ae-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="417ae-137">クライアント認証は、SOAP メッセージ セキュリティで提供されます。</span><span class="sxs-lookup"><span data-stu-id="417ae-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="417ae-138">このモードは、ユーザーがユーザー名およびパスワードを使用して認証し、メッセージ転送をセキュリティで保護するために既存の HTTP が配置されている場合に関連します。</span><span class="sxs-lookup"><span data-stu-id="417ae-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="417ae-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="417ae-139">TransportCredentialOnly</span></span>|<span data-ttu-id="417ae-140">このモードは、メッセージの整合性と機密性を提供しません。</span><span class="sxs-lookup"><span data-stu-id="417ae-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="417ae-141">http ベースのクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="417ae-141">It provides http-based client authentication.</span></span> <span data-ttu-id="417ae-142">このモードを使用するときは、十分に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="417ae-142">This mode should be used with caution.</span></span> <span data-ttu-id="417ae-143">トランスポート セキュリティが他の方法 (IPSec など) で提供され、クライアント認証だけが [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] インフラストラクチャで提供されている環境で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="417ae-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="417ae-144">子要素</span><span class="sxs-lookup"><span data-stu-id="417ae-144">Child Elements</span></span>  
  
|<span data-ttu-id="417ae-145">要素</span><span class="sxs-lookup"><span data-stu-id="417ae-145">Element</span></span>|<span data-ttu-id="417ae-146">説明</span><span class="sxs-lookup"><span data-stu-id="417ae-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="417ae-147">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="417ae-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="417ae-148">基本 HTTP サービスのトランスポート セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="417ae-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="417ae-149">この要素は、<xref:System.ServiceModel.HttpTransportSecurity> に対応しています。</span><span class="sxs-lookup"><span data-stu-id="417ae-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="417ae-150">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="417ae-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="417ae-151">基本 HTTP サービスのメッセージ セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="417ae-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="417ae-152">この要素に対応<!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> -->`System.ServiceModel.NetHttpMessageSecurity`です。</span><span class="sxs-lookup"><span data-stu-id="417ae-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="417ae-153">親要素</span><span class="sxs-lookup"><span data-stu-id="417ae-153">Parent Elements</span></span>  
  
|<span data-ttu-id="417ae-154">要素</span><span class="sxs-lookup"><span data-stu-id="417ae-154">Element</span></span>|<span data-ttu-id="417ae-155">説明</span><span class="sxs-lookup"><span data-stu-id="417ae-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="417ae-156">バインド</span><span class="sxs-lookup"><span data-stu-id="417ae-156">binding</span></span>|<span data-ttu-id="417ae-157">バインド要素、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="417ae-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="417ae-158">コメント</span><span class="sxs-lookup"><span data-stu-id="417ae-158">Remarks</span></span>  
 <span data-ttu-id="417ae-159">既定では、SOAP メッセージはセキュリティで保護されず、クライアントは認証されません。</span><span class="sxs-lookup"><span data-stu-id="417ae-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="417ae-160">この要素を使用すると、`netHttpBinding` 要素に追加のセキュリティ設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="417ae-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="417ae-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="417ae-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <span data-ttu-id="417ae-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span><span class="sxs-lookup"><span data-stu-id="417ae-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span></span>    
 [<span data-ttu-id="417ae-163">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="417ae-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="417ae-164">資格情報の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="417ae-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="417ae-165">バインディング</span><span class="sxs-lookup"><span data-stu-id="417ae-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="417ae-166">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="417ae-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="417ae-167">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="417ae-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="417ae-168">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="417ae-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
