---
title: "&lt;serviceCredentials&gt; の &lt;peer&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a3af8c07e86b7ccdf5443a666626b523914a2c45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="96f30-102">&lt;serviceCredentials&gt; の &lt;peer&gt;</span><span class="sxs-lookup"><span data-stu-id="96f30-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="96f30-103">ピア ノードの現在の資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="96f30-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="96f30-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="96f30-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="96f30-105">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="96f30-105">\<behaviors></span></span>  
<span data-ttu-id="96f30-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="96f30-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="96f30-107">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="96f30-107">\<behavior></span></span>  
<span data-ttu-id="96f30-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="96f30-108">\<serviceCredentials></span></span>  
<span data-ttu-id="96f30-109">\<ピア ></span><span class="sxs-lookup"><span data-stu-id="96f30-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f30-110">構文</span><span class="sxs-lookup"><span data-stu-id="96f30-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96f30-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="96f30-111">Attributes and Elements</span></span>  
 <span data-ttu-id="96f30-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="96f30-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96f30-113">属性</span><span class="sxs-lookup"><span data-stu-id="96f30-113">Attributes</span></span>  
 <span data-ttu-id="96f30-114">なし。</span><span class="sxs-lookup"><span data-stu-id="96f30-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96f30-115">子要素</span><span class="sxs-lookup"><span data-stu-id="96f30-115">Child Elements</span></span>  
  
|<span data-ttu-id="96f30-116">要素</span><span class="sxs-lookup"><span data-stu-id="96f30-116">Element</span></span>|<span data-ttu-id="96f30-117">説明</span><span class="sxs-lookup"><span data-stu-id="96f30-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96f30-118">\<証明書 ></span><span class="sxs-lookup"><span data-stu-id="96f30-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="96f30-119">ピアツーピア サービスのメッセージの署名と暗号化に使用する X.509 証明書を指定します。</span><span class="sxs-lookup"><span data-stu-id="96f30-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="96f30-120">。</span><span class="sxs-lookup"><span data-stu-id="96f30-120">.</span></span>|  
|[<span data-ttu-id="96f30-121">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="96f30-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="96f30-122">メッセージ送信者の認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="96f30-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="96f30-123">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="96f30-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="96f30-124">ピア サービスの認証オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="96f30-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96f30-125">親要素</span><span class="sxs-lookup"><span data-stu-id="96f30-125">Parent Elements</span></span>  
  
|<span data-ttu-id="96f30-126">要素</span><span class="sxs-lookup"><span data-stu-id="96f30-126">Element</span></span>|<span data-ttu-id="96f30-127">説明</span><span class="sxs-lookup"><span data-stu-id="96f30-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96f30-128">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="96f30-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="96f30-129">サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="96f30-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96f30-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="96f30-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="96f30-131">ピア ツー ピア ネットワーク</span><span class="sxs-lookup"><span data-stu-id="96f30-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="96f30-132">ピア チャネル メッセージの認証</span><span class="sxs-lookup"><span data-stu-id="96f30-132">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="96f30-133">ピア チャネル カスタム認証</span><span class="sxs-lookup"><span data-stu-id="96f30-133">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="96f30-134">ピア チャネル アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="96f30-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="96f30-135">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="96f30-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
