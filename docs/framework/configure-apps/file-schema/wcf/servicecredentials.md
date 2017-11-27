---
title: '&lt;serviceCredentials&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bef277ebd2bd80d51380ae9786b290e7d05a0f0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicecredentialsgt"></a><span data-ttu-id="e7173-102">&lt;serviceCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="e7173-102">&lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="e7173-103">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-103">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="e7173-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e7173-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e7173-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="e7173-105">\<behaviors></span></span>  
<span data-ttu-id="e7173-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e7173-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e7173-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="e7173-107">\<behavior></span></span>  
<span data-ttu-id="e7173-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="e7173-108">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7173-109">構文</span><span class="sxs-lookup"><span data-stu-id="e7173-109">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">  
   <clientCertificate>  
   </clientCertificate>  
   <issuedTokenAuthentication>  
   </issuedTokenAuthentication>  
   <peer>  
   </peer>  
   <secureConversationAuthentication>  
   </secureConversationAuthentication>  
   <serviceCertificate>  
   </serviceCertificate>  
   <userNameAuthentication>  
   </userNameAuthentication>  
   <windowsAuthentication>  
   </windowsAuthentication>  
</serviceCredentials>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7173-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e7173-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e7173-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7173-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7173-112">属性</span><span class="sxs-lookup"><span data-stu-id="e7173-112">Attributes</span></span>  
  
|<span data-ttu-id="e7173-113">属性</span><span class="sxs-lookup"><span data-stu-id="e7173-113">Attribute</span></span>|<span data-ttu-id="e7173-114">説明</span><span class="sxs-lookup"><span data-stu-id="e7173-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e7173-115">この設定要素の種類を指定する文字列です。</span><span class="sxs-lookup"><span data-stu-id="e7173-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7173-116">子要素</span><span class="sxs-lookup"><span data-stu-id="e7173-116">Child Elements</span></span>  
  
|<span data-ttu-id="e7173-117">要素</span><span class="sxs-lookup"><span data-stu-id="e7173-117">Element</span></span>|<span data-ttu-id="e7173-118">説明</span><span class="sxs-lookup"><span data-stu-id="e7173-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7173-119">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="e7173-119">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="e7173-120">クライアント証明書を帯域外で使用できるときに使用される証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="e7173-121">この要素は、クライアント証明書の検証設定も指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="e7173-122">この要素は <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="e7173-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="e7173-123">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e7173-123">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="e7173-124">このサービス用に現在発行されているトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="e7173-125">この要素は <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="e7173-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="e7173-126">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="e7173-126">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="e7173-127">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="e7173-128">この要素は <xref:System.ServiceModel.Configuration.PeerCredentialElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="e7173-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="e7173-129">\<secureConversationAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e7173-129">\<secureConversationAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="e7173-130">セキュリティで保護されたメッセージ交換の現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="e7173-131">この要素は <xref:System.ServiceModel.Configuration.SecureConversationServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="e7173-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="e7173-132">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="e7173-132">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|<span data-ttu-id="e7173-133">サービスが自身を識別するために使用する証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="e7173-134">この要素は <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="e7173-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="e7173-135">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e7173-135">\<userNameAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)|<span data-ttu-id="e7173-136">ユーザー名とパスワードの検証の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="e7173-137">この要素は <xref:System.ServiceModel.Configuration.UserNameServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="e7173-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="e7173-138">\<windowsAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e7173-138">\<windowsAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="e7173-139">Windows 資格情報の検証の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="e7173-140">この要素は <xref:System.ServiceModel.Configuration.WindowsServiceElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="e7173-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7173-141">親要素</span><span class="sxs-lookup"><span data-stu-id="e7173-141">Parent Elements</span></span>  
  
|<span data-ttu-id="e7173-142">要素</span><span class="sxs-lookup"><span data-stu-id="e7173-142">Element</span></span>|<span data-ttu-id="e7173-143">説明</span><span class="sxs-lookup"><span data-stu-id="e7173-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7173-144">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="e7173-144">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e7173-145">動作の要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7173-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7173-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7173-146">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
 [<span data-ttu-id="e7173-147">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="e7173-147">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
