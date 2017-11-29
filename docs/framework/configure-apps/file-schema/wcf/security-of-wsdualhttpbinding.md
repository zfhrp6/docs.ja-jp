---
title: "&lt;wsDualHttpBinding&gt; の &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 72d1c451efe267d098ef4d529194905ee14d6ae3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="61d19-102">&lt;wsDualHttpBinding&gt; の &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="61d19-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="61d19-103">セキュリティ機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="61d19-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="61d19-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="61d19-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="61d19-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="61d19-105">\<bindings></span></span>  
<span data-ttu-id="61d19-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="61d19-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="61d19-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="61d19-107">\<binding></span></span>  
<span data-ttu-id="61d19-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="61d19-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61d19-109">構文</span><span class="sxs-lookup"><span data-stu-id="61d19-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61d19-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="61d19-110">Attributes and Elements</span></span>  
 <span data-ttu-id="61d19-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="61d19-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61d19-112">属性</span><span class="sxs-lookup"><span data-stu-id="61d19-112">Attributes</span></span>  
  
|<span data-ttu-id="61d19-113">属性</span><span class="sxs-lookup"><span data-stu-id="61d19-113">Attribute</span></span>|<span data-ttu-id="61d19-114">説明</span><span class="sxs-lookup"><span data-stu-id="61d19-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61d19-115">モード</span><span class="sxs-lookup"><span data-stu-id="61d19-115">mode</span></span>|<span data-ttu-id="61d19-116">-省略可能です。</span><span class="sxs-lookup"><span data-stu-id="61d19-116">-   Optional.</span></span> <span data-ttu-id="61d19-117">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="61d19-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="61d19-118">既定値は `Message` です。</span><span class="sxs-lookup"><span data-stu-id="61d19-118">The default value is `Message`.</span></span> <span data-ttu-id="61d19-119">この属性は <xref:System.ServiceModel.WSDualHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="61d19-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="61d19-120">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="61d19-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="61d19-121">値</span><span class="sxs-lookup"><span data-stu-id="61d19-121">Value</span></span>|<span data-ttu-id="61d19-122">説明</span><span class="sxs-lookup"><span data-stu-id="61d19-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="61d19-123">なし</span><span class="sxs-lookup"><span data-stu-id="61d19-123">None</span></span>|<span data-ttu-id="61d19-124">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="61d19-124">Security is disabled.</span></span>|  
|<span data-ttu-id="61d19-125">メッセージ</span><span class="sxs-lookup"><span data-stu-id="61d19-125">Message</span></span>|<span data-ttu-id="61d19-126">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="61d19-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61d19-127">子要素</span><span class="sxs-lookup"><span data-stu-id="61d19-127">Child Elements</span></span>  
  
|<span data-ttu-id="61d19-128">要素</span><span class="sxs-lookup"><span data-stu-id="61d19-128">Element</span></span>|<span data-ttu-id="61d19-129">説明</span><span class="sxs-lookup"><span data-stu-id="61d19-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61d19-130">\<メッセージ ></span><span class="sxs-lookup"><span data-stu-id="61d19-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="61d19-131">メッセージ レベル セキュリティの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="61d19-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="61d19-132">この要素は <xref:System.ServiceModel.MessageSecurityOverHttp> 型です。</span><span class="sxs-lookup"><span data-stu-id="61d19-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61d19-133">親要素</span><span class="sxs-lookup"><span data-stu-id="61d19-133">Parent Elements</span></span>  
  
|<span data-ttu-id="61d19-134">要素</span><span class="sxs-lookup"><span data-stu-id="61d19-134">Element</span></span>|<span data-ttu-id="61d19-135">説明</span><span class="sxs-lookup"><span data-stu-id="61d19-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61d19-136">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="61d19-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="61d19-137">すべてのバインド機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="61d19-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61d19-138">コメント</span><span class="sxs-lookup"><span data-stu-id="61d19-138">Remarks</span></span>  
 <span data-ttu-id="61d19-139">二重バインディングでは、クライアントの IP アドレスをサービスに公開します。</span><span class="sxs-lookup"><span data-stu-id="61d19-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="61d19-140">クライアントは、セキュリティを使用して信頼するサービスに対して接続のみを可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="61d19-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61d19-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="61d19-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="61d19-142">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="61d19-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="61d19-143">バインディング</span><span class="sxs-lookup"><span data-stu-id="61d19-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="61d19-144">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="61d19-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="61d19-145">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="61d19-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="61d19-146">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="61d19-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
