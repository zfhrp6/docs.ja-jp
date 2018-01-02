---
title: "&lt;カスタム&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bcab1e8361448abfe14db8ac38a924c656b9065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="41bcc-102">&lt;カスタム&gt;</span><span class="sxs-lookup"><span data-stu-id="41bcc-102">&lt;custom&gt;</span></span>
<span data-ttu-id="41bcc-103">ユーザー設定のピア リゾルバー サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="41bcc-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="41bcc-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="41bcc-104">\<system.serviceModel></span></span>  
<span data-ttu-id="41bcc-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="41bcc-105">\<bindings></span></span>  
<span data-ttu-id="41bcc-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="41bcc-106">\<netPeerBinding></span></span>  
<span data-ttu-id="41bcc-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="41bcc-107">\<binding></span></span>  
<span data-ttu-id="41bcc-108">\<競合回避モジュール ></span><span class="sxs-lookup"><span data-stu-id="41bcc-108">\<resolver></span></span>  
<span data-ttu-id="41bcc-109">\<カスタム ></span><span class="sxs-lookup"><span data-stu-id="41bcc-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41bcc-110">構文</span><span class="sxs-lookup"><span data-stu-id="41bcc-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41bcc-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="41bcc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="41bcc-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="41bcc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41bcc-113">属性</span><span class="sxs-lookup"><span data-stu-id="41bcc-113">Attributes</span></span>  
  
|<span data-ttu-id="41bcc-114">属性</span><span class="sxs-lookup"><span data-stu-id="41bcc-114">Attribute</span></span>|<span data-ttu-id="41bcc-115">説明</span><span class="sxs-lookup"><span data-stu-id="41bcc-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="41bcc-116">カスタム ピア リゾルバー サービスをホストするピア ノードのエンドポイント アドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="41bcc-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="41bcc-117">カスタム ピア リゾルバー サービスの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="41bcc-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41bcc-118">子要素</span><span class="sxs-lookup"><span data-stu-id="41bcc-118">Child Elements</span></span>  
  
|<span data-ttu-id="41bcc-119">要素</span><span class="sxs-lookup"><span data-stu-id="41bcc-119">Element</span></span>|<span data-ttu-id="41bcc-120">説明</span><span class="sxs-lookup"><span data-stu-id="41bcc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41bcc-121">\<id ></span><span class="sxs-lookup"><span data-stu-id="41bcc-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="41bcc-122">この要素を使用して構成されたカスタム ピア リゾルバーの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="41bcc-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="41bcc-123">この要素は <xref:System.ServiceModel.Configuration.IdentityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="41bcc-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="41bcc-124">\<ヘッダー ></span><span class="sxs-lookup"><span data-stu-id="41bcc-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="41bcc-125">カスタム ピア リゾルバーによって処理される SOAP メッセージに使用するアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="41bcc-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41bcc-126">親要素</span><span class="sxs-lookup"><span data-stu-id="41bcc-126">Parent Elements</span></span>  
  
|<span data-ttu-id="41bcc-127">要素</span><span class="sxs-lookup"><span data-stu-id="41bcc-127">Element</span></span>|<span data-ttu-id="41bcc-128">説明</span><span class="sxs-lookup"><span data-stu-id="41bcc-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41bcc-129">\<競合回避モジュール ></span><span class="sxs-lookup"><span data-stu-id="41bcc-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="41bcc-130">ピア メッシュ ID を解決してメッシュに参加する複数ノードを表すピア ノード アドレスのセットを取得するために使用されるピア リゾルバー。</span><span class="sxs-lookup"><span data-stu-id="41bcc-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41bcc-131">コメント</span><span class="sxs-lookup"><span data-stu-id="41bcc-131">Remarks</span></span>  
 <span data-ttu-id="41bcc-132">この要素は、サービスをホストするピアのエンドポイント アドレスや特定のバインディング設定など、カスタム ピア リゾルバー サービスの基本設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="41bcc-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="41bcc-133">カスタム競合回避モジュールを作成する方法の詳細については、次を参照してください。 [PeerChannel アプリケーションにカスタム競合回避モジュールを追加する](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)です。</span><span class="sxs-lookup"><span data-stu-id="41bcc-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41bcc-134">参照</span><span class="sxs-lookup"><span data-stu-id="41bcc-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="41bcc-135">ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="41bcc-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="41bcc-136">PeerChannel アプリケーションにカスタム競合回避モジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="41bcc-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
