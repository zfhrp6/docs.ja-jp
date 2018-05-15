---
title: '&lt;webHttpBinding&gt; の &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: f150fb19-7de1-44af-81f4-86cad881cd05
ms.openlocfilehash: 17468bc2354dc2865f10384e918ffb821a28f059
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lttransportgt-of-ltwebhttpbindinggt"></a><span data-ttu-id="e4975-102">&lt;webHttpBinding&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="e4975-102">&lt;transport&gt; of &lt;webHttpBinding&gt;</span></span>
<span data-ttu-id="e4975-103">HTTP 要求を受信するように構成されたサービス エンドポイントのトランスポート レベルのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="e4975-103">Defines the transport-level security settings for a service endpoint configured to receive HTTP requests.</span></span>  
  
 <span data-ttu-id="e4975-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e4975-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4975-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e4975-105">\<bindings></span></span>  
<span data-ttu-id="e4975-106">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e4975-106">\<webHttpBinding></span></span>  
<span data-ttu-id="e4975-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="e4975-107">\<binding></span></span>  
<span data-ttu-id="e4975-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="e4975-108">\<security></span></span>  
<span data-ttu-id="e4975-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="e4975-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4975-110">構文</span><span class="sxs-lookup"><span data-stu-id="e4975-110">Syntax</span></span>  
  
```xml  
<webHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</WebHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="e4975-111">型</span><span class="sxs-lookup"><span data-stu-id="e4975-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4975-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e4975-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e4975-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e4975-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4975-114">属性</span><span class="sxs-lookup"><span data-stu-id="e4975-114">Attributes</span></span>  
  
|<span data-ttu-id="e4975-115">属性</span><span class="sxs-lookup"><span data-stu-id="e4975-115">Attribute</span></span>|<span data-ttu-id="e4975-116">説明</span><span class="sxs-lookup"><span data-stu-id="e4975-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="e4975-117">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="e4975-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="e4975-118">この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="e4975-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="e4975-119">ドメイン プロキシに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="e4975-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="e4975-120">この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="e4975-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="e4975-121">ダイジェストまたは基本認証の認証レルムを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e4975-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="e4975-122">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="e4975-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="e4975-123">認証レルムでは、少なくとも、認証を実行するホストの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e4975-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="e4975-124">アクセス権のあるユーザーのコレクションも指定できます。</span><span class="sxs-lookup"><span data-stu-id="e4975-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="e4975-125">ユーザーは、認証レルムを照会して、複数のユーザー名およびパスワードの候補のうち、どれを使用できるかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="e4975-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="e4975-126">この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4975-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="e4975-127">1.Never – ポリシーが適用されることはありません (拡張保護は無効になります)。</span><span class="sxs-lookup"><span data-stu-id="e4975-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="e4975-128">2.WhenSupported – ポリシーが適用されるのは、クライアントが拡張保護をサポートしている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="e4975-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="e4975-129">3.Always – ポリシーは常に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e4975-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="e4975-130">拡張保護をサポートしていないクライアントは認証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="e4975-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e4975-131">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="e4975-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e4975-132">値</span><span class="sxs-lookup"><span data-stu-id="e4975-132">Value</span></span>|<span data-ttu-id="e4975-133">説明</span><span class="sxs-lookup"><span data-stu-id="e4975-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="e4975-134">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="e4975-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="e4975-135">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4975-135">Uses basic authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="e4975-136">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="e4975-136">Uses X.509 certificates to authenticate the client.</span></span>|  
|`Digest`|<span data-ttu-id="e4975-137">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4975-137">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="e4975-138">Windows ドメインのフォールバックとして NTLM 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4975-138">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="e4975-139">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4975-139">Uses integrated Windows authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="e4975-140">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="e4975-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e4975-141">値</span><span class="sxs-lookup"><span data-stu-id="e4975-141">Value</span></span>|<span data-ttu-id="e4975-142">説明</span><span class="sxs-lookup"><span data-stu-id="e4975-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="e4975-143">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="e4975-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="e4975-144">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4975-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="e4975-145">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4975-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="e4975-146">Windows ドメインのフォールバックとして NTLM を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4975-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="e4975-147">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="e4975-147">Uses integrated Windows authentication.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4975-148">子要素</span><span class="sxs-lookup"><span data-stu-id="e4975-148">Child Elements</span></span>  
 <span data-ttu-id="e4975-149">なし。</span><span class="sxs-lookup"><span data-stu-id="e4975-149">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4975-150">親要素</span><span class="sxs-lookup"><span data-stu-id="e4975-150">Parent Elements</span></span>  
  
|<span data-ttu-id="e4975-151">要素</span><span class="sxs-lookup"><span data-stu-id="e4975-151">Element</span></span>|<span data-ttu-id="e4975-152">説明</span><span class="sxs-lookup"><span data-stu-id="e4975-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4975-153">\<security></span><span class="sxs-lookup"><span data-stu-id="e4975-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|<span data-ttu-id="e4975-154">セキュリティ機能を表す、 [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="e4975-154">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4975-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4975-155">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.WebHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WebHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="e4975-156">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="e4975-156">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e4975-157">バインディング</span><span class="sxs-lookup"><span data-stu-id="e4975-157">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e4975-158">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="e4975-158">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e4975-159">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="e4975-159">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e4975-160">\<binding></span><span class="sxs-lookup"><span data-stu-id="e4975-160">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="e4975-161">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="e4975-161">WCF Web HTTP Programming Model</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
