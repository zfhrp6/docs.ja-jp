---
title: "&lt;netNamedPipeBinding&gt; の &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: efb6289c63cdc98402336949ef5916e7568775a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="71829-102">&lt;netNamedPipeBinding&gt; の &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="71829-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="71829-103">バインディングのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="71829-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="71829-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="71829-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="71829-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="71829-105">\<bindings></span></span>  
<span data-ttu-id="71829-106">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="71829-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="71829-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="71829-107">\<binding></span></span>  
<span data-ttu-id="71829-108">\<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="71829-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71829-109">構文</span><span class="sxs-lookup"><span data-stu-id="71829-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71829-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="71829-110">Attributes and Elements</span></span>  
 <span data-ttu-id="71829-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="71829-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71829-112">属性</span><span class="sxs-lookup"><span data-stu-id="71829-112">Attributes</span></span>  
  
|<span data-ttu-id="71829-113">属性</span><span class="sxs-lookup"><span data-stu-id="71829-113">Attribute</span></span>|<span data-ttu-id="71829-114">説明</span><span class="sxs-lookup"><span data-stu-id="71829-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71829-115">モード</span><span class="sxs-lookup"><span data-stu-id="71829-115">mode</span></span>|<span data-ttu-id="71829-116">このバインディングに適用されるセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="71829-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="71829-117">以下の値が有効です。</span><span class="sxs-lookup"><span data-stu-id="71829-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="71829-118">-なし: 無効になりますセキュリティ。</span><span class="sxs-lookup"><span data-stu-id="71829-118">-   None: This disables security.</span></span><br /><span data-ttu-id="71829-119">-トランスポート: セキュリティは、基になるトランスポート ベースのセキュリティを使用して提供します。</span><span class="sxs-lookup"><span data-stu-id="71829-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="71829-120">このモードでの保護レベルを制御できます。</span><span class="sxs-lookup"><span data-stu-id="71829-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="71829-121">-既定値は、トランスポートです。</span><span class="sxs-lookup"><span data-stu-id="71829-121">-   The default value is Transport.</span></span> <span data-ttu-id="71829-122">この属性は <xref:System.ServiceModel.NetNamedPipeSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="71829-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71829-123">子要素</span><span class="sxs-lookup"><span data-stu-id="71829-123">Child Elements</span></span>  
  
|<span data-ttu-id="71829-124">要素</span><span class="sxs-lookup"><span data-stu-id="71829-124">Element</span></span>|<span data-ttu-id="71829-125">説明</span><span class="sxs-lookup"><span data-stu-id="71829-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71829-126">transport</span><span class="sxs-lookup"><span data-stu-id="71829-126">transport</span></span>|<span data-ttu-id="71829-127">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="71829-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="71829-128">この要素は <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="71829-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71829-129">親要素</span><span class="sxs-lookup"><span data-stu-id="71829-129">Parent Elements</span></span>  
  
|<span data-ttu-id="71829-130">要素</span><span class="sxs-lookup"><span data-stu-id="71829-130">Element</span></span>|<span data-ttu-id="71829-131">説明</span><span class="sxs-lookup"><span data-stu-id="71829-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71829-132">バインド</span><span class="sxs-lookup"><span data-stu-id="71829-132">binding</span></span>|<span data-ttu-id="71829-133">バインド要素、 [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="71829-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71829-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="71829-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="71829-135">サービスとクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="71829-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="71829-136">資格情報の種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="71829-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="71829-137">バインディング</span><span class="sxs-lookup"><span data-stu-id="71829-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="71829-138">システム指定のバインディングを構成します。</span><span class="sxs-lookup"><span data-stu-id="71829-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="71829-139">バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには</span><span class="sxs-lookup"><span data-stu-id="71829-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="71829-140">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="71829-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
