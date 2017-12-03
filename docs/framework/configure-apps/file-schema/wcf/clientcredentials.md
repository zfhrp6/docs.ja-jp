---
title: '&lt;clientCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 834853d8a922148d2810cd391a64a281f2f9ae3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltclientcredentialsgt"></a><span data-ttu-id="9bc63-102">&lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="9bc63-102">&lt;clientCredentials&gt;</span></span>
<span data-ttu-id="9bc63-103">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="9bc63-103">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="9bc63-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9bc63-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9bc63-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="9bc63-105">\<behaviors></span></span>  
<span data-ttu-id="9bc63-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9bc63-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="9bc63-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="9bc63-107">\<behavior></span></span>  
<span data-ttu-id="9bc63-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="9bc63-108">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bc63-109">構文</span><span class="sxs-lookup"><span data-stu-id="9bc63-109">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"  
      supportInteractive="Boolean" >  
   <clientCertificate>  
   </clientCertificate>  
   <digest>  
   </digest>  
   <isuedToken>  
   </isuedToken>  
   <peer>  
   </peer>  
   <serviceCertificate>  
   </serviceCertificate>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</clientCredentials>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bc63-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9bc63-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9bc63-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9bc63-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bc63-112">属性</span><span class="sxs-lookup"><span data-stu-id="9bc63-112">Attributes</span></span>  
  
|<span data-ttu-id="9bc63-113">属性</span><span class="sxs-lookup"><span data-stu-id="9bc63-113">Attribute</span></span>|<span data-ttu-id="9bc63-114">説明</span><span class="sxs-lookup"><span data-stu-id="9bc63-114">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="9bc63-115">実行時にクライアントの資格情報を選択する際に、対話型ユーザーを含めるかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="9bc63-115">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="9bc63-116">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="9bc63-116">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="9bc63-117">この設定要素の種類を指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="9bc63-117">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bc63-118">子要素</span><span class="sxs-lookup"><span data-stu-id="9bc63-118">Child Elements</span></span>  
  
|<span data-ttu-id="9bc63-119">要素</span><span class="sxs-lookup"><span data-stu-id="9bc63-119">Element</span></span>|<span data-ttu-id="9bc63-120">説明</span><span class="sxs-lookup"><span data-stu-id="9bc63-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bc63-121">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="9bc63-121">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="9bc63-122">サービスに対するクライアントの認証に使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="9bc63-122">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="9bc63-123">この要素は <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="9bc63-123">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="9bc63-124">\<httpDigest ></span><span class="sxs-lookup"><span data-stu-id="9bc63-124">\<httpDigest></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/httpdigest-element.md)|<span data-ttu-id="9bc63-125">サービスに対するクライアントの認証に使用されるダイジェストを指定します。</span><span class="sxs-lookup"><span data-stu-id="9bc63-125">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="9bc63-126">この要素は <xref:System.ServiceModel.Configuration.HttpDigestClientElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="9bc63-126">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="9bc63-127">\<issuedToken ></span><span class="sxs-lookup"><span data-stu-id="9bc63-127">\<issuedToken></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|<span data-ttu-id="9bc63-128">セキュリティ トークン サービス (STS) に対するクライアントの認証に使用されるカスタム トークンの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="9bc63-128">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="9bc63-129">この要素は <xref:System.ServiceModel.Configuration.IssuedTokenClientElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="9bc63-129">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="9bc63-130">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="9bc63-130">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="9bc63-131">現在のピア資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="9bc63-131">Specifies a current peer credential.</span></span> <span data-ttu-id="9bc63-132">この要素は <xref:System.ServiceModel.Configuration.PeerCredentialElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="9bc63-132">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="9bc63-133">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="9bc63-133">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="9bc63-134">クライアントに対するサービスの認証に使用される証明書を指定し、証明書オプションを設定するための構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="9bc63-134">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="9bc63-135">この証明書は、クライアントに対するサービスの帯域外に提供される必要があります。</span><span class="sxs-lookup"><span data-stu-id="9bc63-135">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="9bc63-136">この要素は <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="9bc63-136">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="9bc63-137">\<windows ></span><span class="sxs-lookup"><span data-stu-id="9bc63-137">\<windows></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md)|<span data-ttu-id="9bc63-138">Windows 資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="9bc63-138">Specifies a Windows credential.</span></span> <span data-ttu-id="9bc63-139">既定値は、現在のスレッドの資格情報です。</span><span class="sxs-lookup"><span data-stu-id="9bc63-139">The default is the credential of the current thread.</span></span> <span data-ttu-id="9bc63-140">この要素は <xref:System.ServiceModel.Configuration.WindowsClientElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="9bc63-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9bc63-141">親要素</span><span class="sxs-lookup"><span data-stu-id="9bc63-141">Parent Elements</span></span>  
  
|<span data-ttu-id="9bc63-142">要素</span><span class="sxs-lookup"><span data-stu-id="9bc63-142">Element</span></span>|<span data-ttu-id="9bc63-143">説明</span><span class="sxs-lookup"><span data-stu-id="9bc63-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bc63-144">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="9bc63-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="9bc63-145">エンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="9bc63-145">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bc63-146">コメント</span><span class="sxs-lookup"><span data-stu-id="9bc63-146">Remarks</span></span>  
 <span data-ttu-id="9bc63-147">クライアント資格情報は、相互認証が必要な場合にサービスに対するクライアントの認証に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9bc63-147">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="9bc63-148">また、この構成セクションを使用して、クライアントがサービスの証明書によってサービスへのメッセージをセキュリティで保護する必要がある場合に使用するサービス証明書を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="9bc63-148">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc63-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bc63-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 [<span data-ttu-id="9bc63-150">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="9bc63-150">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="9bc63-151">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="9bc63-151">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
