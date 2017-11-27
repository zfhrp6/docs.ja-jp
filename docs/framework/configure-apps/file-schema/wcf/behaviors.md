---
title: "&lt;動作&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b38b27a7b196026e2ff873c7748ed46b96ba9b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbehaviorsgt"></a><span data-ttu-id="c65e7-102">&lt;動作&gt;</span><span class="sxs-lookup"><span data-stu-id="c65e7-102">&lt;behaviors&gt;</span></span>
<span data-ttu-id="c65e7-103">この要素は、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="c65e7-103">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="c65e7-104">各コレクションは、エンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="c65e7-104">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="c65e7-105">各動作要素は、その一意の `name` 属性で識別されます。</span><span class="sxs-lookup"><span data-stu-id="c65e7-105">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="c65e7-106">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c65e7-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c65e7-107">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="c65e7-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="c65e7-108">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c65e7-108">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65e7-109">構文</span><span class="sxs-lookup"><span data-stu-id="c65e7-109">Syntax</span></span>  
  
```xml  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
   <endpointBehaviors>  
   </endpointBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c65e7-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c65e7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c65e7-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c65e7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c65e7-112">属性</span><span class="sxs-lookup"><span data-stu-id="c65e7-112">Attributes</span></span>  
 <span data-ttu-id="c65e7-113">なし</span><span class="sxs-lookup"><span data-stu-id="c65e7-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c65e7-114">子要素</span><span class="sxs-lookup"><span data-stu-id="c65e7-114">Child Elements</span></span>  
  
|<span data-ttu-id="c65e7-115">要素</span><span class="sxs-lookup"><span data-stu-id="c65e7-115">Element</span></span>|<span data-ttu-id="c65e7-116">説明</span><span class="sxs-lookup"><span data-stu-id="c65e7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c65e7-117">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c65e7-117">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="c65e7-118">この構成セクションは、特定のエンドポイントに対して定義されたすべての動作を表します。</span><span class="sxs-lookup"><span data-stu-id="c65e7-118">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[<span data-ttu-id="c65e7-119">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c65e7-119">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|<span data-ttu-id="c65e7-120">この構成セクションは、特定のサービスに対して定義されたすべての動作を表します。</span><span class="sxs-lookup"><span data-stu-id="c65e7-120">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c65e7-121">親要素</span><span class="sxs-lookup"><span data-stu-id="c65e7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c65e7-122">要素</span><span class="sxs-lookup"><span data-stu-id="c65e7-122">Element</span></span>|<span data-ttu-id="c65e7-123">説明</span><span class="sxs-lookup"><span data-stu-id="c65e7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c65e7-124">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c65e7-124">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="c65e7-125">すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="c65e7-125">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c65e7-126">コメント</span><span class="sxs-lookup"><span data-stu-id="c65e7-126">Remarks</span></span>  
 <span data-ttu-id="c65e7-127">`<remove>` 要素を使用して、コレクションから特定の動作を削除できます。</span><span class="sxs-lookup"><span data-stu-id="c65e7-127">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="c65e7-128">これを行うには、`name` 要素の `<remove>` 属性に、削除する動作の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c65e7-128">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="c65e7-129">また、`<clear>` 要素を使用してコレクションの内容をすべて消去し、動作コレクションの初期値を確実に空にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c65e7-129">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65e7-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="c65e7-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="c65e7-131">構成して、ランタイムのビヘイビアーの使用を拡張します。</span><span class="sxs-lookup"><span data-stu-id="c65e7-131">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 [<span data-ttu-id="c65e7-132">クライアントの動作の構成</span><span class="sxs-lookup"><span data-stu-id="c65e7-132">Configuring Client Behaviors</span></span>](../../../../../docs/framework/wcf/configuring-client-behaviors.md)  
 [<span data-ttu-id="c65e7-133">クライアントのランタイム動作の指定</span><span class="sxs-lookup"><span data-stu-id="c65e7-133">Specifying Client Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [<span data-ttu-id="c65e7-134">サービスのランタイム動作の指定</span><span class="sxs-lookup"><span data-stu-id="c65e7-134">Specifying Service Run-Time Behavior</span></span>](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)  
 [<span data-ttu-id="c65e7-135">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="c65e7-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
