---
title: '&lt;wsDualHttpBinding&gt; の &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 734b6d0625cfda79b600a0920ab39bda25ee2e8b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750493"
---
# <a name="ltsecuritygt-of-ltwsdualhttpbindinggt"></a><span data-ttu-id="6b619-102">&lt;wsDualHttpBinding&gt; の &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="6b619-102">&lt;security&gt; of &lt;wsDualHttpBinding&gt;</span></span>
<span data-ttu-id="6b619-103">セキュリティ機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b619-103">Defines the security capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>  
  
 <span data-ttu-id="6b619-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6b619-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b619-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="6b619-105">\<bindings></span></span>  
<span data-ttu-id="6b619-106">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6b619-106">\<wsDualHttpBinding></span></span>  
<span data-ttu-id="6b619-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="6b619-107">\<binding></span></span>  
<span data-ttu-id="6b619-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="6b619-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b619-109">構文</span><span class="sxs-lookup"><span data-stu-id="6b619-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None">  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b619-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6b619-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6b619-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6b619-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b619-112">属性</span><span class="sxs-lookup"><span data-stu-id="6b619-112">Attributes</span></span>  
  
|<span data-ttu-id="6b619-113">属性</span><span class="sxs-lookup"><span data-stu-id="6b619-113">Attribute</span></span>|<span data-ttu-id="6b619-114">説明</span><span class="sxs-lookup"><span data-stu-id="6b619-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b619-115">モード</span><span class="sxs-lookup"><span data-stu-id="6b619-115">mode</span></span>|<span data-ttu-id="6b619-116">-省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6b619-116">-   Optional.</span></span> <span data-ttu-id="6b619-117">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6b619-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6b619-118">既定値は `Message` です。</span><span class="sxs-lookup"><span data-stu-id="6b619-118">The default value is `Message`.</span></span> <span data-ttu-id="6b619-119">この属性は <xref:System.ServiceModel.WSDualHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="6b619-119">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6b619-120">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="6b619-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="6b619-121">値</span><span class="sxs-lookup"><span data-stu-id="6b619-121">Value</span></span>|<span data-ttu-id="6b619-122">説明</span><span class="sxs-lookup"><span data-stu-id="6b619-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b619-123">なし</span><span class="sxs-lookup"><span data-stu-id="6b619-123">None</span></span>|<span data-ttu-id="6b619-124">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="6b619-124">Security is disabled.</span></span>|  
|<span data-ttu-id="6b619-125">メッセージ</span><span class="sxs-lookup"><span data-stu-id="6b619-125">Message</span></span>|<span data-ttu-id="6b619-126">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="6b619-126">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b619-127">子要素</span><span class="sxs-lookup"><span data-stu-id="6b619-127">Child Elements</span></span>  
  
|<span data-ttu-id="6b619-128">要素</span><span class="sxs-lookup"><span data-stu-id="6b619-128">Element</span></span>|<span data-ttu-id="6b619-129">説明</span><span class="sxs-lookup"><span data-stu-id="6b619-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b619-130">\<message></span><span class="sxs-lookup"><span data-stu-id="6b619-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wsdualhttpbinding.md)|<span data-ttu-id="6b619-131">メッセージ レベル セキュリティの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6b619-131">Defines the settings for the message-level security.</span></span> <span data-ttu-id="6b619-132">この要素は <xref:System.ServiceModel.MessageSecurityOverHttp> 型です。</span><span class="sxs-lookup"><span data-stu-id="6b619-132">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6b619-133">親要素</span><span class="sxs-lookup"><span data-stu-id="6b619-133">Parent Elements</span></span>  
  
|<span data-ttu-id="6b619-134">要素</span><span class="sxs-lookup"><span data-stu-id="6b619-134">Element</span></span>|<span data-ttu-id="6b619-135">説明</span><span class="sxs-lookup"><span data-stu-id="6b619-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b619-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="6b619-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="6b619-137">すべてのバインド機能を定義、 [ \<wsDualHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="6b619-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b619-138">コメント</span><span class="sxs-lookup"><span data-stu-id="6b619-138">Remarks</span></span>  
 <span data-ttu-id="6b619-139">二重バインディングでは、クライアントの IP アドレスをサービスに公開します。</span><span class="sxs-lookup"><span data-stu-id="6b619-139">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="6b619-140">クライアントは、セキュリティを使用して信頼するサービスに対して接続のみを可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b619-140">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b619-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b619-141">See Also</span></span>  
 <xref:System.ServiceModel.WSDualHttpSecurity>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="6b619-142">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="6b619-142">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="6b619-143">バインディング</span><span class="sxs-lookup"><span data-stu-id="6b619-143">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6b619-144">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="6b619-144">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6b619-145">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="6b619-145">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="6b619-146">\<binding></span><span class="sxs-lookup"><span data-stu-id="6b619-146">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
