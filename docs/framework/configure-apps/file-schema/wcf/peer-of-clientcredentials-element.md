---
title: "&lt;clientCredentials&gt; 要素の &lt;peer&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f26321afdbe53c4ab3750eae4a7a730bcb5ae4e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="5a3eb-102">&lt;clientCredentials&gt; 要素の &lt;peer&gt;</span><span class="sxs-lookup"><span data-stu-id="5a3eb-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="5a3eb-103">ピアツーピア クライアントの認証時に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="5a3eb-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a3eb-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-105">\<behaviors></span></span>  
<span data-ttu-id="5a3eb-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="5a3eb-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-107">\<behavior></span></span>  
<span data-ttu-id="5a3eb-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-108">\<clientCredentials></span></span>  
<span data-ttu-id="5a3eb-109">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3eb-110">構文</span><span class="sxs-lookup"><span data-stu-id="5a3eb-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a3eb-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5a3eb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5a3eb-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a3eb-113">属性</span><span class="sxs-lookup"><span data-stu-id="5a3eb-113">Attributes</span></span>  
 <span data-ttu-id="5a3eb-114">なし。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a3eb-115">子要素</span><span class="sxs-lookup"><span data-stu-id="5a3eb-115">Child Elements</span></span>  
  
|<span data-ttu-id="5a3eb-116">要素</span><span class="sxs-lookup"><span data-stu-id="5a3eb-116">Element</span></span>|<span data-ttu-id="5a3eb-117">説明</span><span class="sxs-lookup"><span data-stu-id="5a3eb-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a3eb-118">\<証明書 ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="5a3eb-119">ピアツーピア クライアントのメッセージの署名と暗号化に使用する X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="5a3eb-120">。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-120">.</span></span>|  
|[<span data-ttu-id="5a3eb-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="5a3eb-122">ピア クライアントの認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="5a3eb-123">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="5a3eb-124">メッセージ送信者の認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a3eb-125">親要素</span><span class="sxs-lookup"><span data-stu-id="5a3eb-125">Parent Elements</span></span>  
  
|<span data-ttu-id="5a3eb-126">要素</span><span class="sxs-lookup"><span data-stu-id="5a3eb-126">Element</span></span>|<span data-ttu-id="5a3eb-127">説明</span><span class="sxs-lookup"><span data-stu-id="5a3eb-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a3eb-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="5a3eb-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="5a3eb-129">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a3eb-130">コメント</span><span class="sxs-lookup"><span data-stu-id="5a3eb-130">Remarks</span></span>  
 <span data-ttu-id="5a3eb-131">この構成要素は、ピア ノードがメッシュ内の他のノードに対して自身を認証するために使用する資格情報と、ピア ノードが他のピア ノードを認証するために使用する認証設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="5a3eb-132">詳細については、次を参照してください。[ピア チャネル メッセージ認証](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)と[ピア チャネル アプリケーションのセキュリティで保護する](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a3eb-132">For more information, see [Peer Channel Message Authentication](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a3eb-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a3eb-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="5a3eb-134">ピア ツー ピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="5a3eb-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="5a3eb-135">クライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="5a3eb-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="5a3eb-136">ピア チャネル メッセージの認証</span><span class="sxs-lookup"><span data-stu-id="5a3eb-136">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="5a3eb-137">ピア チャネル カスタム認証</span><span class="sxs-lookup"><span data-stu-id="5a3eb-137">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="5a3eb-138">ピア チャネル アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="5a3eb-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="5a3eb-139">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="5a3eb-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
