---
title: '&lt;pnrpPeerResolver&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cd93bdadec120050813fcc1097d3041d6be94f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="30c1d-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="30c1d-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="30c1d-103">リゾルバーとして PNRP (Peer Name Resolution Protocol) リゾルバーを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="30c1d-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="30c1d-104">PNRP は既定のリゾルバーであるため、この要素は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="30c1d-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="30c1d-105">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="30c1d-105">\<system.serviceModel></span></span>  
<span data-ttu-id="30c1d-106">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="30c1d-106">\<bindings></span></span>  
<span data-ttu-id="30c1d-107">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30c1d-107">\<customBinding></span></span>  
<span data-ttu-id="30c1d-108">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="30c1d-108">\<binding></span></span>  
<span data-ttu-id="30c1d-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="30c1d-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30c1d-110">構文</span><span class="sxs-lookup"><span data-stu-id="30c1d-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30c1d-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="30c1d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="30c1d-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="30c1d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30c1d-113">属性</span><span class="sxs-lookup"><span data-stu-id="30c1d-113">Attributes</span></span>  
  
|<span data-ttu-id="30c1d-114">属性</span><span class="sxs-lookup"><span data-stu-id="30c1d-114">Attribute</span></span>|<span data-ttu-id="30c1d-115">説明</span><span class="sxs-lookup"><span data-stu-id="30c1d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30c1d-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="30c1d-116">resolverType</span></span>|<span data-ttu-id="30c1d-117">使用されるリゾルバーを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="30c1d-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="30c1d-118">この属性は省略できます。</span><span class="sxs-lookup"><span data-stu-id="30c1d-118">This attribute is optional.</span></span> <span data-ttu-id="30c1d-119">設定されていない場合、または空の文字列に設定されている場合は、PNRP が使用されます。</span><span class="sxs-lookup"><span data-stu-id="30c1d-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30c1d-120">子要素</span><span class="sxs-lookup"><span data-stu-id="30c1d-120">Child Elements</span></span>  
 <span data-ttu-id="30c1d-121">なし</span><span class="sxs-lookup"><span data-stu-id="30c1d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30c1d-122">親要素</span><span class="sxs-lookup"><span data-stu-id="30c1d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="30c1d-123">要素</span><span class="sxs-lookup"><span data-stu-id="30c1d-123">Element</span></span>|<span data-ttu-id="30c1d-124">説明</span><span class="sxs-lookup"><span data-stu-id="30c1d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30c1d-125">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="30c1d-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="30c1d-126">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="30c1d-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="30c1d-127">例</span><span class="sxs-lookup"><span data-stu-id="30c1d-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="30c1d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="30c1d-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="30c1d-129">バインディング</span><span class="sxs-lookup"><span data-stu-id="30c1d-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="30c1d-130">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="30c1d-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="30c1d-131">カスタム バインド</span><span class="sxs-lookup"><span data-stu-id="30c1d-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="30c1d-132">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="30c1d-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="30c1d-133">ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="30c1d-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
