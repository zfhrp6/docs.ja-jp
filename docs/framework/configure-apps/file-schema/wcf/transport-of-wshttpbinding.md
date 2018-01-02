---
title: "&lt;wsHttpBinding&gt; の &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21e38acf-450a-4bda-82b6-de305e1f7cd8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57496371032fd8f07f69bf71cc5c266d977bf57d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltwshttpbindinggt"></a><span data-ttu-id="34bf8-102">&lt;wsHttpBinding&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="34bf8-102">&lt;transport&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="34bf8-103">HTTP トランスポートの認証設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="34bf8-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="34bf8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="34bf8-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="34bf8-105">\<bindings></span></span>  
<span data-ttu-id="34bf8-106">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="34bf8-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="34bf8-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="34bf8-107">\<binding></span></span>  
<span data-ttu-id="34bf8-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="34bf8-108">\<security></span></span>  
<span data-ttu-id="34bf8-109">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="34bf8-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34bf8-110">構文</span><span class="sxs-lookup"><span data-stu-id="34bf8-110">Syntax</span></span>  
  
```xml  
<wsHttpBinding>  
    <binding>  
        <security mode="None|Transport|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport  
            clientCredentialType="Basic|Certificate|Digest|None|Ntlm|Windows"  
            proxyCredentialType="Basic|Digest|None|Ntlm|Windows"  
            realm="string" />  
                <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always" protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                </extendedProtecutionPolicy>  
            </transport>  
        </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="34bf8-111">型</span><span class="sxs-lookup"><span data-stu-id="34bf8-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34bf8-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="34bf8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="34bf8-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34bf8-114">属性</span><span class="sxs-lookup"><span data-stu-id="34bf8-114">Attributes</span></span>  
  
|<span data-ttu-id="34bf8-115">属性</span><span class="sxs-lookup"><span data-stu-id="34bf8-115">Attribute</span></span>|<span data-ttu-id="34bf8-116">説明</span><span class="sxs-lookup"><span data-stu-id="34bf8-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="34bf8-117">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="34bf8-118">この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="34bf8-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="34bf8-119">ドメイン プロキシに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="34bf8-120">この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="34bf8-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="34bf8-121">ダイジェストまたは基本認証の認証レルムを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="34bf8-121">A string that specifies the authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="34bf8-122">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="34bf8-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="34bf8-123">認証レルムでは、少なくとも、認証を実行するホストの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="34bf8-124">アクセス権のあるユーザーのコレクションも指定できます。</span><span class="sxs-lookup"><span data-stu-id="34bf8-124">It can also specify a collection of users that has access.</span></span> <span data-ttu-id="34bf8-125">ユーザーは、認証レルムを照会して、複数のユーザー名およびパスワードの候補のうち、どれを使用できるかを確認することができます。</span><span class="sxs-lookup"><span data-stu-id="34bf8-125">A user can query the authentication realm to ascertain which one of the several possible usernames and passwords can be used.</span></span>|  
|`policyEnforcement`|<span data-ttu-id="34bf8-126">この列挙体は、<xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> を適用するタイミングを指定します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-126">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="34bf8-127">1.Never – ポリシーが適用されることはありません (拡張保護は無効になります)。</span><span class="sxs-lookup"><span data-stu-id="34bf8-127">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="34bf8-128">2.WhenSupported – ポリシーが適用されるのは、クライアントが拡張保護をサポートしている場合のみです。</span><span class="sxs-lookup"><span data-stu-id="34bf8-128">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="34bf8-129">3.Always – ポリシーは常に適用されます。</span><span class="sxs-lookup"><span data-stu-id="34bf8-129">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="34bf8-130">拡張保護をサポートしていないクライアントは認証に失敗します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-130">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="34bf8-131">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="34bf8-131">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="34bf8-132">値</span><span class="sxs-lookup"><span data-stu-id="34bf8-132">Value</span></span>|<span data-ttu-id="34bf8-133">説明</span><span class="sxs-lookup"><span data-stu-id="34bf8-133">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="34bf8-134">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="34bf8-134">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="34bf8-135">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-135">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="34bf8-136">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-136">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="34bf8-137">Windows ドメインのフォールバックとして NTLM 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-137">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="34bf8-138">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-138">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="34bf8-139">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-139">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="34bf8-140">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="34bf8-140">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="34bf8-141">値</span><span class="sxs-lookup"><span data-stu-id="34bf8-141">Value</span></span>|<span data-ttu-id="34bf8-142">説明</span><span class="sxs-lookup"><span data-stu-id="34bf8-142">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="34bf8-143">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="34bf8-143">Security is disabled.</span></span>|  
|`Basic`|<span data-ttu-id="34bf8-144">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-144">Uses basic authentication.</span></span>|  
|`Digest`|<span data-ttu-id="34bf8-145">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-145">Uses digest authentication.</span></span>|  
|`Ntlm`|<span data-ttu-id="34bf8-146">Windows ドメインのフォールバックとして NTLM を使用します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-146">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|`Windows`|<span data-ttu-id="34bf8-147">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-147">Uses integrated Windows authentication.</span></span>|  
|`Certificate`|<span data-ttu-id="34bf8-148">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="34bf8-148">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34bf8-149">子要素</span><span class="sxs-lookup"><span data-stu-id="34bf8-149">Child Elements</span></span>  
 <span data-ttu-id="34bf8-150">なし。</span><span class="sxs-lookup"><span data-stu-id="34bf8-150">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34bf8-151">親要素</span><span class="sxs-lookup"><span data-stu-id="34bf8-151">Parent Elements</span></span>  
  
|<span data-ttu-id="34bf8-152">要素</span><span class="sxs-lookup"><span data-stu-id="34bf8-152">Element</span></span>|<span data-ttu-id="34bf8-153">説明</span><span class="sxs-lookup"><span data-stu-id="34bf8-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34bf8-154">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="34bf8-154">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|<span data-ttu-id="34bf8-155">セキュリティ機能を表す、 [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="34bf8-155">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="34bf8-156">参照</span><span class="sxs-lookup"><span data-stu-id="34bf8-156">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 [<span data-ttu-id="34bf8-157">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="34bf8-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="34bf8-158">バインディング</span><span class="sxs-lookup"><span data-stu-id="34bf8-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="34bf8-159">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="34bf8-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="34bf8-160">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="34bf8-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="34bf8-161">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="34bf8-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
