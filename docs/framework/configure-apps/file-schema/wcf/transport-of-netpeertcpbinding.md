---
title: "&lt;netPeerTcpBinding&gt; の &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60880461a3d71e64be2b3b74b1a236625426c2b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="7a0e6-102">&lt;netPeerTcpBinding&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="7a0e6-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="7a0e6-103">使用する場合は、トランスポート レベルのセキュリティの設定を指定、 [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a0e6-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="7a0e6-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7a0e6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7a0e6-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="7a0e6-105">\<bindings></span></span>  
<span data-ttu-id="7a0e6-106">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="7a0e6-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="7a0e6-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="7a0e6-107">\<binding></span></span>  
<span data-ttu-id="7a0e6-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="7a0e6-108">\<security></span></span>  
<span data-ttu-id="7a0e6-109">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="7a0e6-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a0e6-110">構文</span><span class="sxs-lookup"><span data-stu-id="7a0e6-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a0e6-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7a0e6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7a0e6-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a0e6-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a0e6-113">属性</span><span class="sxs-lookup"><span data-stu-id="7a0e6-113">Attributes</span></span>  
  
|<span data-ttu-id="7a0e6-114">属性</span><span class="sxs-lookup"><span data-stu-id="7a0e6-114">Attribute</span></span>|<span data-ttu-id="7a0e6-115">説明</span><span class="sxs-lookup"><span data-stu-id="7a0e6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a0e6-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="7a0e6-116">credentialType</span></span>|<span data-ttu-id="7a0e6-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="7a0e6-117">Optional.</span></span> <span data-ttu-id="7a0e6-118">ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="7a0e6-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="7a0e6-119">この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="7a0e6-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="7a0e6-120">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="7a0e6-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="7a0e6-121">値</span><span class="sxs-lookup"><span data-stu-id="7a0e6-121">Value</span></span>|<span data-ttu-id="7a0e6-122">説明</span><span class="sxs-lookup"><span data-stu-id="7a0e6-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7a0e6-123">証明書</span><span class="sxs-lookup"><span data-stu-id="7a0e6-123">Certificate</span></span>|<span data-ttu-id="7a0e6-124">ピア チャネル トランスポートの認証には X 509 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="7a0e6-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="7a0e6-125">[Password]</span><span class="sxs-lookup"><span data-stu-id="7a0e6-125">Password</span></span>|<span data-ttu-id="7a0e6-126">ピア チャネル トランスポートの認証には正しいパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="7a0e6-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a0e6-127">子要素</span><span class="sxs-lookup"><span data-stu-id="7a0e6-127">Child Elements</span></span>  
 <span data-ttu-id="7a0e6-128">なし</span><span class="sxs-lookup"><span data-stu-id="7a0e6-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a0e6-129">親要素</span><span class="sxs-lookup"><span data-stu-id="7a0e6-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7a0e6-130">要素</span><span class="sxs-lookup"><span data-stu-id="7a0e6-130">Element</span></span>|<span data-ttu-id="7a0e6-131">説明</span><span class="sxs-lookup"><span data-stu-id="7a0e6-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a0e6-132">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="7a0e6-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="7a0e6-133">セキュリティ設定を定義、 [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="7a0e6-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a0e6-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a0e6-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="7a0e6-135">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="7a0e6-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="7a0e6-136">バインディング</span><span class="sxs-lookup"><span data-stu-id="7a0e6-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7a0e6-137">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="7a0e6-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7a0e6-138">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="7a0e6-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="7a0e6-139">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="7a0e6-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
