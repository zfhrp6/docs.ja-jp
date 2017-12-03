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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 69b62699f5db0ab11fac3cc4d1ba4e2aa022934d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="090cb-102">&lt;peerTransport&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="090cb-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="090cb-103">このバインドで構成されたピアが送信する、セキュリティで保護されたメッセージのトランスポートの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="090cb-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="090cb-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="090cb-104">\<system.serviceModel></span></span>  
<span data-ttu-id="090cb-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="090cb-105">\<bindings></span></span>  
<span data-ttu-id="090cb-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="090cb-106">\<customBinding></span></span>  
<span data-ttu-id="090cb-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="090cb-107">\<binding></span></span>  
<span data-ttu-id="090cb-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="090cb-108">\<peerTransport></span></span>  
<span data-ttu-id="090cb-109">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="090cb-109">\<security></span></span>  
<span data-ttu-id="090cb-110">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="090cb-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="090cb-111">構文</span><span class="sxs-lookup"><span data-stu-id="090cb-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="090cb-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="090cb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="090cb-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="090cb-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="090cb-114">属性</span><span class="sxs-lookup"><span data-stu-id="090cb-114">Attributes</span></span>  
  
|<span data-ttu-id="090cb-115">属性</span><span class="sxs-lookup"><span data-stu-id="090cb-115">Attribute</span></span>|<span data-ttu-id="090cb-116">説明</span><span class="sxs-lookup"><span data-stu-id="090cb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="090cb-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="090cb-117">credentialType</span></span>|<span data-ttu-id="090cb-118">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="090cb-118">Optional.</span></span> <span data-ttu-id="090cb-119">ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="090cb-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="090cb-120">この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="090cb-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="090cb-121">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="090cb-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="090cb-122">値</span><span class="sxs-lookup"><span data-stu-id="090cb-122">Value</span></span>|<span data-ttu-id="090cb-123">説明</span><span class="sxs-lookup"><span data-stu-id="090cb-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="090cb-124">証明書</span><span class="sxs-lookup"><span data-stu-id="090cb-124">Certificate</span></span>|<span data-ttu-id="090cb-125">ピア チャネル トランスポートの認証には X 509 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="090cb-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="090cb-126">[Password]</span><span class="sxs-lookup"><span data-stu-id="090cb-126">Password</span></span>|<span data-ttu-id="090cb-127">ピア チャネル トランスポートの認証には正しいパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="090cb-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="090cb-128">子要素</span><span class="sxs-lookup"><span data-stu-id="090cb-128">Child Elements</span></span>  
 <span data-ttu-id="090cb-129">なし</span><span class="sxs-lookup"><span data-stu-id="090cb-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="090cb-130">親要素</span><span class="sxs-lookup"><span data-stu-id="090cb-130">Parent Elements</span></span>  
  
|<span data-ttu-id="090cb-131">要素</span><span class="sxs-lookup"><span data-stu-id="090cb-131">Element</span></span>|<span data-ttu-id="090cb-132">説明</span><span class="sxs-lookup"><span data-stu-id="090cb-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="090cb-133">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="090cb-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="090cb-134">ピア トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="090cb-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="090cb-135">コメント</span><span class="sxs-lookup"><span data-stu-id="090cb-135">Remarks</span></span>  
 <span data-ttu-id="090cb-136">この要素は場合のみ設定の mode 属性[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)に設定されている`Transport`または`TransportWithMessageCredential`です。</span><span class="sxs-lookup"><span data-stu-id="090cb-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="090cb-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="090cb-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="090cb-138">トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="090cb-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="090cb-139">トランスポート</span><span class="sxs-lookup"><span data-stu-id="090cb-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="090cb-140">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="090cb-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="090cb-141">バインディング</span><span class="sxs-lookup"><span data-stu-id="090cb-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="090cb-142">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="090cb-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="090cb-143">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="090cb-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="090cb-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="090cb-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
