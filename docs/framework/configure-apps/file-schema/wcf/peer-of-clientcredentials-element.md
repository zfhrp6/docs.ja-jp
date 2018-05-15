---
title: '&lt;clientCredentials&gt; 要素の &lt;peer&gt;'
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 9d64f682f67dcc7c4f0c0f1600938f8ff9ac0dd6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="91d35-102">&lt;clientCredentials&gt; 要素の &lt;peer&gt;</span><span class="sxs-lookup"><span data-stu-id="91d35-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="91d35-103">ピアツーピア クライアントの認証時に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="91d35-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="91d35-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="91d35-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="91d35-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="91d35-105">\<behaviors></span></span>  
<span data-ttu-id="91d35-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="91d35-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="91d35-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="91d35-107">\<behavior></span></span>  
<span data-ttu-id="91d35-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="91d35-108">\<clientCredentials></span></span>  
<span data-ttu-id="91d35-109">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="91d35-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d35-110">構文</span><span class="sxs-lookup"><span data-stu-id="91d35-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91d35-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="91d35-111">Attributes and Elements</span></span>  
 <span data-ttu-id="91d35-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="91d35-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91d35-113">属性</span><span class="sxs-lookup"><span data-stu-id="91d35-113">Attributes</span></span>  
 <span data-ttu-id="91d35-114">なし。</span><span class="sxs-lookup"><span data-stu-id="91d35-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91d35-115">子要素</span><span class="sxs-lookup"><span data-stu-id="91d35-115">Child Elements</span></span>  
  
|<span data-ttu-id="91d35-116">要素</span><span class="sxs-lookup"><span data-stu-id="91d35-116">Element</span></span>|<span data-ttu-id="91d35-117">説明</span><span class="sxs-lookup"><span data-stu-id="91d35-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91d35-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="91d35-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="91d35-119">ピアツーピア クライアントのメッセージの署名と暗号化に使用する X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="91d35-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="91d35-120">である必要があります。</span><span class="sxs-lookup"><span data-stu-id="91d35-120">.</span></span>|  
|[<span data-ttu-id="91d35-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="91d35-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="91d35-122">ピア クライアントの認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="91d35-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="91d35-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="91d35-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="91d35-124">メッセージ送信者の認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="91d35-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91d35-125">親要素</span><span class="sxs-lookup"><span data-stu-id="91d35-125">Parent Elements</span></span>  
  
|<span data-ttu-id="91d35-126">要素</span><span class="sxs-lookup"><span data-stu-id="91d35-126">Element</span></span>|<span data-ttu-id="91d35-127">説明</span><span class="sxs-lookup"><span data-stu-id="91d35-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91d35-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="91d35-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="91d35-129">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="91d35-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91d35-130">コメント</span><span class="sxs-lookup"><span data-stu-id="91d35-130">Remarks</span></span>  
 <span data-ttu-id="91d35-131">この構成要素は、ピア ノードがメッシュ内の他のノードに対して自身を認証するために使用する資格情報と、ピア ノードが他のピア ノードを認証するために使用する認証設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="91d35-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="91d35-132">詳細については、次を参照してください。[ピア チャネル メッセージ認証](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)と[ピア チャネル アプリケーションのセキュリティで保護する](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)です。</span><span class="sxs-lookup"><span data-stu-id="91d35-132">For more information, see [Peer Channel Message Authentication](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d35-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="91d35-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="91d35-134">ピアツーピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="91d35-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="91d35-135">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="91d35-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="91d35-136">ピア チャネル メッセージの認証</span><span class="sxs-lookup"><span data-stu-id="91d35-136">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="91d35-137">ピア チャネル カスタム認証</span><span class="sxs-lookup"><span data-stu-id="91d35-137">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="91d35-138">セキュリティによるピア チャネル アプリケーションの保護</span><span class="sxs-lookup"><span data-stu-id="91d35-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="91d35-139">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="91d35-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
