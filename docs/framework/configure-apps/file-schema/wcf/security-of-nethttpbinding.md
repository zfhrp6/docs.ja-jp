---
title: '&lt;netHttpBinding&gt; の &lt;security'
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 71157413ba10aa6b45006235d3de69628fce75f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="c9ddb-102">&lt;netHttpBinding&gt; の &lt;security</span><span class="sxs-lookup"><span data-stu-id="c9ddb-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="c9ddb-103">セキュリティ機能を定義、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="c9ddb-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c9ddb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9ddb-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="c9ddb-105">\<bindings></span></span>  
<span data-ttu-id="c9ddb-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c9ddb-106">\<netHttpBinding></span></span>  
<span data-ttu-id="c9ddb-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="c9ddb-107">\<binding></span></span>  
<span data-ttu-id="c9ddb-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="c9ddb-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ddb-109">構文</span><span class="sxs-lookup"><span data-stu-id="c9ddb-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9ddb-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c9ddb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c9ddb-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9ddb-112">属性</span><span class="sxs-lookup"><span data-stu-id="c9ddb-112">Attributes</span></span>  
  
|<span data-ttu-id="c9ddb-113">属性</span><span class="sxs-lookup"><span data-stu-id="c9ddb-113">Attribute</span></span>|<span data-ttu-id="c9ddb-114">説明</span><span class="sxs-lookup"><span data-stu-id="c9ddb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9ddb-115">モード</span><span class="sxs-lookup"><span data-stu-id="c9ddb-115">mode</span></span>|<span data-ttu-id="c9ddb-116">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-116">Optional.</span></span> <span data-ttu-id="c9ddb-117">使用されるセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="c9ddb-118">既定値は、`None` です。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-118">The default is `None`.</span></span> <span data-ttu-id="c9ddb-119">この属性は型<!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`です。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="c9ddb-120">mode 属性</span><span class="sxs-lookup"><span data-stu-id="c9ddb-120">mode Attribute</span></span>  
  
|<span data-ttu-id="c9ddb-121">値</span><span class="sxs-lookup"><span data-stu-id="c9ddb-121">Value</span></span>|<span data-ttu-id="c9ddb-122">説明</span><span class="sxs-lookup"><span data-stu-id="c9ddb-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9ddb-123">なし</span><span class="sxs-lookup"><span data-stu-id="c9ddb-123">None</span></span>|<span data-ttu-id="c9ddb-124">メッセージの数は、転送中にセキュリティ保護されていません。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="c9ddb-125">Transport</span><span class="sxs-lookup"><span data-stu-id="c9ddb-125">Transport</span></span>|<span data-ttu-id="c9ddb-126">セキュリティは、HTTPS トランスポートを使用して提供されます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="c9ddb-127">SOAP メッセージは、HTTPS を使用したセキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="c9ddb-128">サービスは、サービスの X.509 証明書を使用してクライアントに認証されます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="c9ddb-129">クライアントは、提供される ClientCredentialType を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="c9ddb-130">メッセージ</span><span class="sxs-lookup"><span data-stu-id="c9ddb-130">Message</span></span>|<span data-ttu-id="c9ddb-131">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="c9ddb-132">既定では、本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="c9ddb-133">このバインディングの場合、サーバー証明書をクライアントの帯域外で提供するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="c9ddb-134">このバインディングの唯一の有効な `ClientCredentialType` は、`Certificate` です。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="c9ddb-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c9ddb-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="c9ddb-136">整合性、機密性、およびサーバー認証は、トランスポート セキュリティによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="c9ddb-137">クライアント認証は、SOAP メッセージ セキュリティで提供されます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="c9ddb-138">このモードは、ユーザーがユーザー名およびパスワードを使用して認証し、メッセージ転送をセキュリティで保護するために既存の HTTP が配置されている場合に関連します。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="c9ddb-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="c9ddb-139">TransportCredentialOnly</span></span>|<span data-ttu-id="c9ddb-140">このモードは、メッセージの整合性と機密性を提供しません。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="c9ddb-141">http ベースのクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-141">It provides http-based client authentication.</span></span> <span data-ttu-id="c9ddb-142">このモードを使用するときは、十分に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-142">This mode should be used with caution.</span></span> <span data-ttu-id="c9ddb-143">トランスポート セキュリティが他の方法 (IPSec など) で提供され、クライアント認証だけが [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] インフラストラクチャで提供されている環境で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9ddb-144">子要素</span><span class="sxs-lookup"><span data-stu-id="c9ddb-144">Child Elements</span></span>  
  
|<span data-ttu-id="c9ddb-145">要素</span><span class="sxs-lookup"><span data-stu-id="c9ddb-145">Element</span></span>|<span data-ttu-id="c9ddb-146">説明</span><span class="sxs-lookup"><span data-stu-id="c9ddb-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9ddb-147">\<transport></span><span class="sxs-lookup"><span data-stu-id="c9ddb-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="c9ddb-148">基本 HTTP サービスのトランスポート セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="c9ddb-149">この要素は、<xref:System.ServiceModel.HttpTransportSecurity> に対応しています。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="c9ddb-150">\<message></span><span class="sxs-lookup"><span data-stu-id="c9ddb-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="c9ddb-151">基本 HTTP サービスのメッセージ セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="c9ddb-152">この要素に対応<!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> -->`System.ServiceModel.NetHttpMessageSecurity`です。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9ddb-153">親要素</span><span class="sxs-lookup"><span data-stu-id="c9ddb-153">Parent Elements</span></span>  
  
|<span data-ttu-id="c9ddb-154">要素</span><span class="sxs-lookup"><span data-stu-id="c9ddb-154">Element</span></span>|<span data-ttu-id="c9ddb-155">説明</span><span class="sxs-lookup"><span data-stu-id="c9ddb-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9ddb-156">バインド</span><span class="sxs-lookup"><span data-stu-id="c9ddb-156">binding</span></span>|<span data-ttu-id="c9ddb-157">バインド要素、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9ddb-158">コメント</span><span class="sxs-lookup"><span data-stu-id="c9ddb-158">Remarks</span></span>  
 <span data-ttu-id="c9ddb-159">既定では、SOAP メッセージはセキュリティで保護されず、クライアントは認証されません。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="c9ddb-160">この要素を使用すると、`netHttpBinding` 要素に追加のセキュリティ設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="c9ddb-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ddb-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9ddb-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>    
 [<span data-ttu-id="c9ddb-162">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="c9ddb-162">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="c9ddb-163">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="c9ddb-163">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="c9ddb-164">バインディング</span><span class="sxs-lookup"><span data-stu-id="c9ddb-164">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c9ddb-165">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="c9ddb-165">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c9ddb-166">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="c9ddb-166">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="c9ddb-167">\<binding></span><span class="sxs-lookup"><span data-stu-id="c9ddb-167">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
