---
title: '&lt;pnrpPeerResolver&gt;'
ms.date: 03/30/2017
ms.assetid: c1b34f3b-68e5-4911-a367-de49fb61dbc6
ms.openlocfilehash: f0874d38c3432f066d1bec5cc84f53e1f3730180
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltpnrppeerresolvergt"></a><span data-ttu-id="3034a-102">&lt;pnrpPeerResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="3034a-102">&lt;pnrpPeerResolver&gt;</span></span>
<span data-ttu-id="3034a-103">リゾルバーとして PNRP (Peer Name Resolution Protocol) リゾルバーを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="3034a-103">Specifies that the PNRP (Peer Name Resolution Protocol) resolver is to be used as a resolver.</span></span> <span data-ttu-id="3034a-104">PNRP は既定のリゾルバーであるため、この要素は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3034a-104">This element is optional because PNRP is the default resolver.</span></span>  
  
 <span data-ttu-id="3034a-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3034a-105">\<system.serviceModel></span></span>  
<span data-ttu-id="3034a-106">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3034a-106">\<bindings></span></span>  
<span data-ttu-id="3034a-107">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3034a-107">\<customBinding></span></span>  
<span data-ttu-id="3034a-108">\<binding></span><span class="sxs-lookup"><span data-stu-id="3034a-108">\<binding></span></span>  
<span data-ttu-id="3034a-109">\<pnrpResolver ></span><span class="sxs-lookup"><span data-stu-id="3034a-109">\<pnrpResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3034a-110">構文</span><span class="sxs-lookup"><span data-stu-id="3034a-110">Syntax</span></span>  
  
```xml  
<pnrpResolver resolverType="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3034a-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3034a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3034a-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3034a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3034a-113">属性</span><span class="sxs-lookup"><span data-stu-id="3034a-113">Attributes</span></span>  
  
|<span data-ttu-id="3034a-114">属性</span><span class="sxs-lookup"><span data-stu-id="3034a-114">Attribute</span></span>|<span data-ttu-id="3034a-115">説明</span><span class="sxs-lookup"><span data-stu-id="3034a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3034a-116">resolverType</span><span class="sxs-lookup"><span data-stu-id="3034a-116">resolverType</span></span>|<span data-ttu-id="3034a-117">使用されるリゾルバーを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="3034a-117">A string that specifies the resolver to be used.</span></span> <span data-ttu-id="3034a-118">この属性は省略できます。</span><span class="sxs-lookup"><span data-stu-id="3034a-118">This attribute is optional.</span></span> <span data-ttu-id="3034a-119">設定されていない場合、または空の文字列に設定されている場合は、PNRP が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3034a-119">If it is not set, or if it is set to an empty string, PNRP is used.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3034a-120">子要素</span><span class="sxs-lookup"><span data-stu-id="3034a-120">Child Elements</span></span>  
 <span data-ttu-id="3034a-121">なし</span><span class="sxs-lookup"><span data-stu-id="3034a-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3034a-122">親要素</span><span class="sxs-lookup"><span data-stu-id="3034a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3034a-123">要素</span><span class="sxs-lookup"><span data-stu-id="3034a-123">Element</span></span>|<span data-ttu-id="3034a-124">説明</span><span class="sxs-lookup"><span data-stu-id="3034a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3034a-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="3034a-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3034a-126">カスタム バインドのすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="3034a-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3034a-127">例</span><span class="sxs-lookup"><span data-stu-id="3034a-127">Example</span></span>  
  
```xml  
<pnrpResolver resolverType="" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="3034a-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="3034a-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PnrpPeerResolverElement>  
 <xref:System.ServiceModel.Channels.PnrpPeerResolverBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="3034a-129">バインディング</span><span class="sxs-lookup"><span data-stu-id="3034a-129">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3034a-130">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="3034a-130">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="3034a-131">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="3034a-131">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="3034a-132">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3034a-132">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="3034a-133">ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="3034a-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
