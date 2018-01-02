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
ms.workload: dotnet
ms.openlocfilehash: 8bb0fbce0d7b45fd051db187cd6d7e920b08cab3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="cbf00-102">&lt;peerTransport&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="cbf00-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="cbf00-103">このバインドで構成されたピアが送信する、セキュリティで保護されたメッセージのトランスポートの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbf00-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="cbf00-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="cbf00-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cbf00-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="cbf00-105">\<bindings></span></span>  
<span data-ttu-id="cbf00-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cbf00-106">\<customBinding></span></span>  
<span data-ttu-id="cbf00-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="cbf00-107">\<binding></span></span>  
<span data-ttu-id="cbf00-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="cbf00-108">\<peerTransport></span></span>  
<span data-ttu-id="cbf00-109">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="cbf00-109">\<security></span></span>  
<span data-ttu-id="cbf00-110">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="cbf00-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbf00-111">構文</span><span class="sxs-lookup"><span data-stu-id="cbf00-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbf00-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cbf00-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cbf00-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cbf00-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbf00-114">属性</span><span class="sxs-lookup"><span data-stu-id="cbf00-114">Attributes</span></span>  
  
|<span data-ttu-id="cbf00-115">属性</span><span class="sxs-lookup"><span data-stu-id="cbf00-115">Attribute</span></span>|<span data-ttu-id="cbf00-116">説明</span><span class="sxs-lookup"><span data-stu-id="cbf00-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbf00-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="cbf00-117">credentialType</span></span>|<span data-ttu-id="cbf00-118">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="cbf00-118">Optional.</span></span> <span data-ttu-id="cbf00-119">ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbf00-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="cbf00-120">この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="cbf00-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="cbf00-121">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="cbf00-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="cbf00-122">値</span><span class="sxs-lookup"><span data-stu-id="cbf00-122">Value</span></span>|<span data-ttu-id="cbf00-123">説明</span><span class="sxs-lookup"><span data-stu-id="cbf00-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cbf00-124">証明書</span><span class="sxs-lookup"><span data-stu-id="cbf00-124">Certificate</span></span>|<span data-ttu-id="cbf00-125">ピア チャネル トランスポートの認証には X 509 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="cbf00-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="cbf00-126">[Password]</span><span class="sxs-lookup"><span data-stu-id="cbf00-126">Password</span></span>|<span data-ttu-id="cbf00-127">ピア チャネル トランスポートの認証には正しいパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="cbf00-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbf00-128">子要素</span><span class="sxs-lookup"><span data-stu-id="cbf00-128">Child Elements</span></span>  
 <span data-ttu-id="cbf00-129">なし</span><span class="sxs-lookup"><span data-stu-id="cbf00-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbf00-130">親要素</span><span class="sxs-lookup"><span data-stu-id="cbf00-130">Parent Elements</span></span>  
  
|<span data-ttu-id="cbf00-131">要素</span><span class="sxs-lookup"><span data-stu-id="cbf00-131">Element</span></span>|<span data-ttu-id="cbf00-132">説明</span><span class="sxs-lookup"><span data-stu-id="cbf00-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbf00-133">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="cbf00-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="cbf00-134">ピア トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="cbf00-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbf00-135">コメント</span><span class="sxs-lookup"><span data-stu-id="cbf00-135">Remarks</span></span>  
 <span data-ttu-id="cbf00-136">この要素は場合のみ設定の mode 属性[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)に設定されている`Transport`または`TransportWithMessageCredential`です。</span><span class="sxs-lookup"><span data-stu-id="cbf00-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf00-137">参照</span><span class="sxs-lookup"><span data-stu-id="cbf00-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="cbf00-138">トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cbf00-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="cbf00-139">トランスポート</span><span class="sxs-lookup"><span data-stu-id="cbf00-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="cbf00-140">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="cbf00-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="cbf00-141">バインディング</span><span class="sxs-lookup"><span data-stu-id="cbf00-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cbf00-142">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="cbf00-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="cbf00-143">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="cbf00-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="cbf00-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cbf00-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
