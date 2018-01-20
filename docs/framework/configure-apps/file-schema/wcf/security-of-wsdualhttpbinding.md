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
ms.workload: dotnet
ms.openlocfilehash: 6680d01b068a6ac1c4f9abcda69779c9cd0786a0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="6591a-102">&lt;wsDualHttpBinding&gt; の &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="6591a-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="6591a-103">セキュリティ機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="6591a-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="6591a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6591a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6591a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6591a-105">\<bindings></span></span>  
<span data-ttu-id="6591a-106">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="6591a-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="6591a-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="6591a-107">\<binding></span></span>  
<span data-ttu-id="6591a-108">\<security></span><span class="sxs-lookup"><span data-stu-id="6591a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6591a-109">構文</span><span class="sxs-lookup"><span data-stu-id="6591a-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6591a-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6591a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6591a-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6591a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6591a-112">属性</span><span class="sxs-lookup"><span data-stu-id="6591a-112">Attributes</span></span>  
  
|<span data-ttu-id="6591a-113">属性</span><span class="sxs-lookup"><span data-stu-id="6591a-113">Attribute</span></span>|<span data-ttu-id="6591a-114">説明</span><span class="sxs-lookup"><span data-stu-id="6591a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6591a-115">モード</span><span class="sxs-lookup"><span data-stu-id="6591a-115">mode</span></span>|<span data-ttu-id="6591a-116">-省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6591a-116">-   Optional.</span></span> <span data-ttu-id="6591a-117">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6591a-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6591a-118">既定値は `Message` です。</span><span class="sxs-lookup"><span data-stu-id="6591a-118">The default value is `Message`.</span></span> <span data-ttu-id="6591a-119">この属性は <xref:System.ServiceModel.WSDualHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="6591a-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6591a-120">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="6591a-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="6591a-121">値</span><span class="sxs-lookup"><span data-stu-id="6591a-121">Value</span></span>|<span data-ttu-id="6591a-122">説明</span><span class="sxs-lookup"><span data-stu-id="6591a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6591a-123">なし</span><span class="sxs-lookup"><span data-stu-id="6591a-123">None</span></span>|<span data-ttu-id="6591a-124">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="6591a-124">Security is disabled.</span></span>|  
|<span data-ttu-id="6591a-125">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6591a-125">Message</span></span>|<span data-ttu-id="6591a-126">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="6591a-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6591a-127">子要素</span><span class="sxs-lookup"><span data-stu-id="6591a-127">Child Elements</span></span>  
  
|<span data-ttu-id="6591a-128">要素</span><span class="sxs-lookup"><span data-stu-id="6591a-128">Element</span></span>|<span data-ttu-id="6591a-129">説明</span><span class="sxs-lookup"><span data-stu-id="6591a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6591a-130">\<message></span><span class="sxs-lookup"><span data-stu-id="6591a-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="6591a-131">メッセージ レベル セキュリティの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6591a-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="6591a-132">この要素は <xref:System.ServiceModel.MessageSecurityOverHttp> 型です。</span><span class="sxs-lookup"><span data-stu-id="6591a-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6591a-133">親要素</span><span class="sxs-lookup"><span data-stu-id="6591a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="6591a-134">要素</span><span class="sxs-lookup"><span data-stu-id="6591a-134">Element</span></span>|<span data-ttu-id="6591a-135">説明</span><span class="sxs-lookup"><span data-stu-id="6591a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6591a-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="6591a-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6591a-137">すべてのバインド機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="6591a-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6591a-138">コメント</span><span class="sxs-lookup"><span data-stu-id="6591a-138">Remarks</span></span>  
 <span data-ttu-id="6591a-139">二重バインディングでは、クライアントの IP アドレスをサービスに公開します。</span><span class="sxs-lookup"><span data-stu-id="6591a-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="6591a-140">クライアントは、セキュリティを使用して信頼するサービスに対して接続のみを可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6591a-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6591a-141">参照</span><span class="sxs-lookup"><span data-stu-id="6591a-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="6591a-142">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="6591a-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="6591a-143">バインディング</span><span class="sxs-lookup"><span data-stu-id="6591a-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6591a-144">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="6591a-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6591a-145">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="6591a-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6591a-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="6591a-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
