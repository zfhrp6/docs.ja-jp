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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 181e6a9458754934d6b3b27a31c2cf2dd3455f52
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="54e27-102">&lt;netPeerTcpBinding&gt; の &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="54e27-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="54e27-103">使用する場合は、トランスポート レベルのセキュリティの設定を指定、 [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="54e27-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="54e27-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="54e27-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="54e27-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="54e27-105">\<bindings></span></span>  
<span data-ttu-id="54e27-106">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="54e27-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="54e27-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="54e27-107">\<binding></span></span>  
<span data-ttu-id="54e27-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="54e27-108">\<security></span></span>  
<span data-ttu-id="54e27-109">\<トランスポート ></span><span class="sxs-lookup"><span data-stu-id="54e27-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54e27-110">構文</span><span class="sxs-lookup"><span data-stu-id="54e27-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54e27-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="54e27-111">Attributes and Elements</span></span>  
 <span data-ttu-id="54e27-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="54e27-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54e27-113">属性</span><span class="sxs-lookup"><span data-stu-id="54e27-113">Attributes</span></span>  
  
|<span data-ttu-id="54e27-114">属性</span><span class="sxs-lookup"><span data-stu-id="54e27-114">Attribute</span></span>|<span data-ttu-id="54e27-115">説明</span><span class="sxs-lookup"><span data-stu-id="54e27-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54e27-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="54e27-116">credentialType</span></span>|<span data-ttu-id="54e27-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="54e27-117">Optional.</span></span> <span data-ttu-id="54e27-118">ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="54e27-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="54e27-119">この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。</span><span class="sxs-lookup"><span data-stu-id="54e27-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="54e27-120">credentialType 属性</span><span class="sxs-lookup"><span data-stu-id="54e27-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="54e27-121">値</span><span class="sxs-lookup"><span data-stu-id="54e27-121">Value</span></span>|<span data-ttu-id="54e27-122">説明</span><span class="sxs-lookup"><span data-stu-id="54e27-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="54e27-123">証明書</span><span class="sxs-lookup"><span data-stu-id="54e27-123">Certificate</span></span>|<span data-ttu-id="54e27-124">ピア チャネル トランスポートの認証には X 509 証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="54e27-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="54e27-125">[Password]</span><span class="sxs-lookup"><span data-stu-id="54e27-125">Password</span></span>|<span data-ttu-id="54e27-126">ピア チャネル トランスポートの認証には正しいパスワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="54e27-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54e27-127">子要素</span><span class="sxs-lookup"><span data-stu-id="54e27-127">Child Elements</span></span>  
 <span data-ttu-id="54e27-128">なし</span><span class="sxs-lookup"><span data-stu-id="54e27-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54e27-129">親要素</span><span class="sxs-lookup"><span data-stu-id="54e27-129">Parent Elements</span></span>  
  
|<span data-ttu-id="54e27-130">要素</span><span class="sxs-lookup"><span data-stu-id="54e27-130">Element</span></span>|<span data-ttu-id="54e27-131">説明</span><span class="sxs-lookup"><span data-stu-id="54e27-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54e27-132">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="54e27-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="54e27-133">セキュリティ設定を定義、 [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="54e27-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54e27-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="54e27-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="54e27-135">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="54e27-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="54e27-136">バインディング</span><span class="sxs-lookup"><span data-stu-id="54e27-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="54e27-137">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="54e27-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="54e27-138">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="54e27-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="54e27-139">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="54e27-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
