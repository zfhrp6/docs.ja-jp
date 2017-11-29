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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bccfc95313ae3ae4a692be2165dc694783a460e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="90468-102">&lt;カスタム&gt;</span><span class="sxs-lookup"><span data-stu-id="90468-102">&lt;custom&gt;</span></span>
<span data-ttu-id="90468-103">ユーザー設定のピア リゾルバー サービスの設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="90468-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="90468-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="90468-104">\<system.serviceModel></span></span>  
<span data-ttu-id="90468-105">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="90468-105">\<bindings></span></span>  
<span data-ttu-id="90468-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="90468-106">\<netPeerBinding></span></span>  
<span data-ttu-id="90468-107">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="90468-107">\<binding></span></span>  
<span data-ttu-id="90468-108">\<競合回避モジュール ></span><span class="sxs-lookup"><span data-stu-id="90468-108">\<resolver></span></span>  
<span data-ttu-id="90468-109">\<カスタム ></span><span class="sxs-lookup"><span data-stu-id="90468-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90468-110">構文</span><span class="sxs-lookup"><span data-stu-id="90468-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90468-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="90468-111">Attributes and Elements</span></span>  
 <span data-ttu-id="90468-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="90468-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90468-113">属性</span><span class="sxs-lookup"><span data-stu-id="90468-113">Attributes</span></span>  
  
|<span data-ttu-id="90468-114">属性</span><span class="sxs-lookup"><span data-stu-id="90468-114">Attribute</span></span>|<span data-ttu-id="90468-115">説明</span><span class="sxs-lookup"><span data-stu-id="90468-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="90468-116">カスタム ピア リゾルバー サービスをホストするピア ノードのエンドポイント アドレスを指定する URI。</span><span class="sxs-lookup"><span data-stu-id="90468-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="90468-117">カスタム ピア リゾルバー サービスの種類を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="90468-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90468-118">子要素</span><span class="sxs-lookup"><span data-stu-id="90468-118">Child Elements</span></span>  
  
|<span data-ttu-id="90468-119">要素</span><span class="sxs-lookup"><span data-stu-id="90468-119">Element</span></span>|<span data-ttu-id="90468-120">説明</span><span class="sxs-lookup"><span data-stu-id="90468-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90468-121">\<id ></span><span class="sxs-lookup"><span data-stu-id="90468-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="90468-122">この要素を使用して構成されたカスタム ピア リゾルバーの ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="90468-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="90468-123">この要素は <xref:System.ServiceModel.Configuration.IdentityElement> 型です。</span><span class="sxs-lookup"><span data-stu-id="90468-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="90468-124">\<ヘッダー ></span><span class="sxs-lookup"><span data-stu-id="90468-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="90468-125">カスタム ピア リゾルバーによって処理される SOAP メッセージに使用するアドレス ヘッダーのコレクション。</span><span class="sxs-lookup"><span data-stu-id="90468-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90468-126">親要素</span><span class="sxs-lookup"><span data-stu-id="90468-126">Parent Elements</span></span>  
  
|<span data-ttu-id="90468-127">要素</span><span class="sxs-lookup"><span data-stu-id="90468-127">Element</span></span>|<span data-ttu-id="90468-128">説明</span><span class="sxs-lookup"><span data-stu-id="90468-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90468-129">\<競合回避モジュール ></span><span class="sxs-lookup"><span data-stu-id="90468-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="90468-130">ピア メッシュ ID を解決してメッシュに参加する複数ノードを表すピア ノード アドレスのセットを取得するために使用されるピア リゾルバー。</span><span class="sxs-lookup"><span data-stu-id="90468-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90468-131">コメント</span><span class="sxs-lookup"><span data-stu-id="90468-131">Remarks</span></span>  
 <span data-ttu-id="90468-132">この要素は、サービスをホストするピアのエンドポイント アドレスや特定のバインディング設定など、カスタム ピア リゾルバー サービスの基本設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="90468-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="90468-133">カスタム競合回避モジュールを作成する方法の詳細については、次を参照してください。 [PeerChannel アプリケーションにカスタム競合回避モジュールを追加する](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)です。</span><span class="sxs-lookup"><span data-stu-id="90468-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90468-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="90468-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="90468-135">ピア リゾルバー</span><span class="sxs-lookup"><span data-stu-id="90468-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="90468-136">PeerChannel アプリケーションにカスタム競合回避モジュールを追加します。</span><span class="sxs-lookup"><span data-stu-id="90468-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
