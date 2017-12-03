---
title: "&lt;ws2007HttpBinding&gt; の &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 573b7fb5cf130d0a638326b87ae49f90db881df4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a><span data-ttu-id="2a50e-102">&lt;ws2007HttpBinding&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="2a50e-102">&lt;transport&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="2a50e-103">HTTP トランスポートの認証設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-103">Defines authentication settings for the HTTP transport.</span></span>  
  
 <span data-ttu-id="2a50e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2a50e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2a50e-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="2a50e-105">\<bindings></span></span>  
<span data-ttu-id="2a50e-106">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2a50e-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="2a50e-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="2a50e-107">\<binding></span></span>  
<span data-ttu-id="2a50e-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="2a50e-108">\<security></span></span>  
<span data-ttu-id="2a50e-109">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="2a50e-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a50e-110">構文</span><span class="sxs-lookup"><span data-stu-id="2a50e-110">Syntax</span></span>  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a><span data-ttu-id="2a50e-111">型</span><span class="sxs-lookup"><span data-stu-id="2a50e-111">Type</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a50e-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2a50e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2a50e-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a50e-114">属性</span><span class="sxs-lookup"><span data-stu-id="2a50e-114">Attributes</span></span>  
  
|<span data-ttu-id="2a50e-115">属性</span><span class="sxs-lookup"><span data-stu-id="2a50e-115">Attribute</span></span>|<span data-ttu-id="2a50e-116">説明</span><span class="sxs-lookup"><span data-stu-id="2a50e-116">Description</span></span>|  
|---------------|-----------------|  
|`clientCredentialType`|<span data-ttu-id="2a50e-117">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-117">Specifies the credential used to authenticate the client to the service.</span></span> <span data-ttu-id="2a50e-118">この属性は <xref:System.ServiceModel.HttpClientCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="2a50e-118">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|`proxyCredentialType`|<span data-ttu-id="2a50e-119">ドメイン プロキシに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-119">Specifies the credential used to authenticate the client to a domain proxy.</span></span> <span data-ttu-id="2a50e-120">この属性は <xref:System.ServiceModel.HttpProxyCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="2a50e-120">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|`realm`|<span data-ttu-id="2a50e-121">ダイジェスト認証または基本認証の認証レルム。</span><span class="sxs-lookup"><span data-stu-id="2a50e-121">The authentication realm for digest or basic authentication.</span></span> <span data-ttu-id="2a50e-122">既定値は空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="2a50e-122">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="2a50e-123">認証レルムでは、少なくとも、認証を実行するホストの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-123">An authentication realm specifies at least the name of the host that performs the authentication.</span></span> <span data-ttu-id="2a50e-124">アクセス権のあるユーザーのコレクションも指定できます。</span><span class="sxs-lookup"><span data-stu-id="2a50e-124">It can also specify a collection of users who have access.</span></span> <span data-ttu-id="2a50e-125">ユーザーは、認証レルムを照会して、複数のユーザー名とパスワードの候補のうち、どれを使用できるかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="2a50e-125">A user can query the authentication realm to determine which one of the several possible usernames and passwords can be used.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="2a50e-126">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="2a50e-126">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2a50e-127">値</span><span class="sxs-lookup"><span data-stu-id="2a50e-127">Value</span></span>|<span data-ttu-id="2a50e-128">説明</span><span class="sxs-lookup"><span data-stu-id="2a50e-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a50e-129">なし</span><span class="sxs-lookup"><span data-stu-id="2a50e-129">None</span></span>|<span data-ttu-id="2a50e-130">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="2a50e-130">Security is disabled.</span></span>|  
|<span data-ttu-id="2a50e-131">Basic</span><span class="sxs-lookup"><span data-stu-id="2a50e-131">Basic</span></span>|<span data-ttu-id="2a50e-132">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-132">Uses basic authentication.</span></span>|  
|<span data-ttu-id="2a50e-133">Digest</span><span class="sxs-lookup"><span data-stu-id="2a50e-133">Digest</span></span>|<span data-ttu-id="2a50e-134">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-134">Uses digest authentication.</span></span>|  
|<span data-ttu-id="2a50e-135">Ntlm</span><span class="sxs-lookup"><span data-stu-id="2a50e-135">Ntlm</span></span>|<span data-ttu-id="2a50e-136">Windows ドメインのフォールバックとして NTLM 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-136">Uses NTLM authentication as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="2a50e-137">Windows</span><span class="sxs-lookup"><span data-stu-id="2a50e-137">Windows</span></span>|<span data-ttu-id="2a50e-138">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-138">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="2a50e-139">証明書</span><span class="sxs-lookup"><span data-stu-id="2a50e-139">Certificate</span></span>|<span data-ttu-id="2a50e-140">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-140">Uses X.509 certificates to authenticate the client.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="2a50e-141">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="2a50e-141">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2a50e-142">値</span><span class="sxs-lookup"><span data-stu-id="2a50e-142">Value</span></span>|<span data-ttu-id="2a50e-143">説明</span><span class="sxs-lookup"><span data-stu-id="2a50e-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a50e-144">なし</span><span class="sxs-lookup"><span data-stu-id="2a50e-144">None</span></span>|<span data-ttu-id="2a50e-145">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="2a50e-145">Security is disabled.</span></span>|  
|<span data-ttu-id="2a50e-146">Basic</span><span class="sxs-lookup"><span data-stu-id="2a50e-146">Basic</span></span>|<span data-ttu-id="2a50e-147">基本認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-147">Uses basic authentication.</span></span>|  
|<span data-ttu-id="2a50e-148">Digest</span><span class="sxs-lookup"><span data-stu-id="2a50e-148">Digest</span></span>|<span data-ttu-id="2a50e-149">ダイジェスト認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-149">Uses digest authentication.</span></span>|  
|<span data-ttu-id="2a50e-150">Ntlm</span><span class="sxs-lookup"><span data-stu-id="2a50e-150">Ntlm</span></span>|<span data-ttu-id="2a50e-151">Windows ドメインのフォールバックとして NTLM を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-151">Uses NTLM as a fallback with a Windows domain.</span></span>|  
|<span data-ttu-id="2a50e-152">Windows</span><span class="sxs-lookup"><span data-stu-id="2a50e-152">Windows</span></span>|<span data-ttu-id="2a50e-153">統合 Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-153">Uses integrated Windows authentication.</span></span>|  
|<span data-ttu-id="2a50e-154">証明書</span><span class="sxs-lookup"><span data-stu-id="2a50e-154">Certificate</span></span>|<span data-ttu-id="2a50e-155">X.509 証明書を使用して、クライアントを認証します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-155">Uses X.509 certificates to authenticate the client.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a50e-156">子要素</span><span class="sxs-lookup"><span data-stu-id="2a50e-156">Child Elements</span></span>  
 <span data-ttu-id="2a50e-157">なし</span><span class="sxs-lookup"><span data-stu-id="2a50e-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a50e-158">親要素</span><span class="sxs-lookup"><span data-stu-id="2a50e-158">Parent Elements</span></span>  
  
|<span data-ttu-id="2a50e-159">要素</span><span class="sxs-lookup"><span data-stu-id="2a50e-159">Element</span></span>|<span data-ttu-id="2a50e-160">説明</span><span class="sxs-lookup"><span data-stu-id="2a50e-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a50e-161">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="2a50e-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|<span data-ttu-id="2a50e-162">セキュリティ機能を表す、 [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2a50e-162">Represents the security capabilities of the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a50e-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a50e-163">See Also</span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [<span data-ttu-id="2a50e-164">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="2a50e-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2a50e-165">バインディング</span><span class="sxs-lookup"><span data-stu-id="2a50e-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2a50e-166">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="2a50e-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2a50e-167">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="2a50e-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2a50e-168">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="2a50e-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
