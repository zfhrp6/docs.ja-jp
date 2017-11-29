---
title: "&lt;peerTransport&gt; の &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 787d4569416203364e04898c6adcd57fb5a7aec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="12a45-102">&lt;peerTransport&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="12a45-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="12a45-103">このバインドで構成されたピアが送信する、セキュリティで保護されたメッセージのトランスポートの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="12a45-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="12a45-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="12a45-104">\<system.serviceModel></span></span>  
<span data-ttu-id="12a45-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="12a45-105">\<bindings></span></span>  
<span data-ttu-id="12a45-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="12a45-106">\<customBinding></span></span>  
<span data-ttu-id="12a45-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="12a45-107">\<binding></span></span>  
<span data-ttu-id="12a45-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="12a45-108">\<peerTransport></span></span>  
<span data-ttu-id="12a45-109">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="12a45-109">\<security></span></span>  
<span data-ttu-id="12a45-110">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="12a45-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a45-111">構文</span><span class="sxs-lookup"><span data-stu-id="12a45-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12a45-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="12a45-112">Attributes and Elements</span></span>  
 <span data-ttu-id="12a45-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="12a45-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12a45-114">属性</span><span class="sxs-lookup"><span data-stu-id="12a45-114">Attributes</span></span>  
  
|<span data-ttu-id="12a45-115">属性</span><span class="sxs-lookup"><span data-stu-id="12a45-115">Attribute</span></span>|<span data-ttu-id="12a45-116">説明</span><span class="sxs-lookup"><span data-stu-id="12a45-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12a45-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="12a45-117">credentialType</span></span>|<span data-ttu-id="12a45-118">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="12a45-118">Optional.</span></span> <span data-ttu-id="12a45-119">ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="12a45-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="12a45-120">この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="12a45-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="12a45-121">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="12a45-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="12a45-122">値</span><span class="sxs-lookup"><span data-stu-id="12a45-122">Value</span></span>|<span data-ttu-id="12a45-123">説明</span><span class="sxs-lookup"><span data-stu-id="12a45-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="12a45-124">証明書</span><span class="sxs-lookup"><span data-stu-id="12a45-124">Certificate</span></span>|<span data-ttu-id="12a45-125">ピア チャネル トランスポートの認証には X 509 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="12a45-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="12a45-126">[Password]</span><span class="sxs-lookup"><span data-stu-id="12a45-126">Password</span></span>|<span data-ttu-id="12a45-127">ピア チャネル トランスポートの認証には正しいパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="12a45-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12a45-128">子要素</span><span class="sxs-lookup"><span data-stu-id="12a45-128">Child Elements</span></span>  
 <span data-ttu-id="12a45-129">なし</span><span class="sxs-lookup"><span data-stu-id="12a45-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12a45-130">親要素</span><span class="sxs-lookup"><span data-stu-id="12a45-130">Parent Elements</span></span>  
  
|<span data-ttu-id="12a45-131">要素</span><span class="sxs-lookup"><span data-stu-id="12a45-131">Element</span></span>|<span data-ttu-id="12a45-132">説明</span><span class="sxs-lookup"><span data-stu-id="12a45-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12a45-133">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="12a45-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="12a45-134">ピア トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="12a45-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12a45-135">コメント</span><span class="sxs-lookup"><span data-stu-id="12a45-135">Remarks</span></span>  
 <span data-ttu-id="12a45-136">この要素は場合のみ設定の mode 属性[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)に設定されている`Transport`または`TransportWithMessageCredential`です。</span><span class="sxs-lookup"><span data-stu-id="12a45-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a45-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="12a45-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="12a45-138">トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="12a45-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="12a45-139">トランスポート</span><span class="sxs-lookup"><span data-stu-id="12a45-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="12a45-140">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="12a45-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="12a45-141">バインディング</span><span class="sxs-lookup"><span data-stu-id="12a45-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="12a45-142">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="12a45-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="12a45-143">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="12a45-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="12a45-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="12a45-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
