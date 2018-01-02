---
title: "&lt;endpointBehaviors&gt; の &lt;behavior&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aed43e76b817c9a2eded6c1e5daee183625ecc0d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltbehaviorgt-of-ltendpointbehaviorsgt"></a><span data-ttu-id="c2609-102">&lt;endpointBehaviors&gt; の &lt;behavior&gt;</span><span class="sxs-lookup"><span data-stu-id="c2609-102">&lt;behavior&gt; of &lt;endpointBehaviors&gt;</span></span>
<span data-ttu-id="c2609-103">エンドポイントの動作設定のコレクションを含む `behavior` 要素。</span><span class="sxs-lookup"><span data-stu-id="c2609-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="c2609-104">各動作には、それぞれの `name` によってインデックスが付けられます。</span><span class="sxs-lookup"><span data-stu-id="c2609-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="c2609-105">エンドポイントは、この名前を使用して各動作にリンクできます。</span><span class="sxs-lookup"><span data-stu-id="c2609-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="c2609-106">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c2609-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c2609-107">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2609-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="c2609-108">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c2609-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="c2609-109">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="c2609-109">\<behaviors></span></span>  
<span data-ttu-id="c2609-110">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c2609-110">\<endpointBehaviors></span></span>  
<span data-ttu-id="c2609-111">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="c2609-111">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2609-112">構文</span><span class="sxs-lookup"><span data-stu-id="c2609-112">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <endpointBehaviors>  
       <behavior name="String" />  
    </endpointBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2609-113">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c2609-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c2609-114">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c2609-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2609-115">属性</span><span class="sxs-lookup"><span data-stu-id="c2609-115">Attributes</span></span>  
  
|<span data-ttu-id="c2609-116">属性</span><span class="sxs-lookup"><span data-stu-id="c2609-116">Attribute</span></span>|<span data-ttu-id="c2609-117">説明</span><span class="sxs-lookup"><span data-stu-id="c2609-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2609-118">name</span><span class="sxs-lookup"><span data-stu-id="c2609-118">name</span></span>|<span data-ttu-id="c2609-119">動作の構成名を含む一意の文字列。</span><span class="sxs-lookup"><span data-stu-id="c2609-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="c2609-120">この値は、要素の識別文字列として機能するため、一意のユーザー定義の文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2609-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="c2609-121">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 以降では、バインディングおよび動作に名前を付ける必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c2609-121">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c2609-122">既定の構成と無名のバインディングおよび動作の詳細については、次を参照してください。[簡略化された構成](../../../../../docs/framework/wcf/simplified-configuration.md)と[WCF サービスの構成を簡略化](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="c2609-122">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2609-123">子要素</span><span class="sxs-lookup"><span data-stu-id="c2609-123">Child Elements</span></span>  
  
|<span data-ttu-id="c2609-124">要素</span><span class="sxs-lookup"><span data-stu-id="c2609-124">Element</span></span>|<span data-ttu-id="c2609-125">説明</span><span class="sxs-lookup"><span data-stu-id="c2609-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2609-126">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="c2609-126">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="c2609-127">サービスに対するクライアントの認証に使用される資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2609-127">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[<span data-ttu-id="c2609-128">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="c2609-128">\<callbackDebug></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/callbackdebug.md)|<span data-ttu-id="c2609-129">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] コールバック オブジェクトのサービス デバッグを指定します。</span><span class="sxs-lookup"><span data-stu-id="c2609-129">Specifies service debugging for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] callback object.</span></span>|  
|[<span data-ttu-id="c2609-130">\<callbackTimeouts ></span><span class="sxs-lookup"><span data-stu-id="c2609-130">\<callbackTimeouts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/callbacktimeouts.md)|<span data-ttu-id="c2609-131">クライアント コールバックのタイムアウトを指定します。</span><span class="sxs-lookup"><span data-stu-id="c2609-131">Specifies the timeout for the client callback.</span></span>|  
|[<span data-ttu-id="c2609-132">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="c2609-132">\<clientVia></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientvia.md)|<span data-ttu-id="c2609-133">メッセージの経路を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2609-133">Specifies the route a message should take.</span></span>|  
|[<span data-ttu-id="c2609-134">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c2609-134">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer.md)|<span data-ttu-id="c2609-135">DataContractSerializer 用の構成データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c2609-135">Contains configuration data for the DataContractSerializer.</span></span>|  
|[<span data-ttu-id="c2609-136">\<dispatcherSynchronization ></span><span class="sxs-lookup"><span data-stu-id="c2609-136">\<dispatcherSynchronization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/dispatchersynchronization.md)|<span data-ttu-id="c2609-137">サービスが非同期に応答を返すことができるようにするエンドポイントの動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2609-137">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[<span data-ttu-id="c2609-138">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="c2609-138">\<enableWebScript></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)|<span data-ttu-id="c2609-139">ASP.NET AJAX Web ページからサービスを使用できるようにするエンドポイントの動作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c2609-139">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="c2609-140">動作は、いずれかと組み合わせてのみ使用する必要があります、 \<webHttpBinding > 標準バインディングまたは\<webMessageEncoding > バインド要素。</span><span class="sxs-lookup"><span data-stu-id="c2609-140">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[<span data-ttu-id="c2609-141">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="c2609-141">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="c2609-142">エンドポイントのさまざまな探索設定を指定します (探索可能性、スコープ、メタデータに対するカスタム拡張など)。</span><span class="sxs-lookup"><span data-stu-id="c2609-142">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[<span data-ttu-id="c2609-143">\<soapProcessing ></span><span class="sxs-lookup"><span data-stu-id="c2609-143">\<soapProcessing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md)|<span data-ttu-id="c2609-144">異なるバインディングの種類およびメッセージ バージョンの間でメッセージのマーシャリングに使用されるクライアント エンドポイントの動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="c2609-144">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[<span data-ttu-id="c2609-145">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="c2609-145">\<synchronousReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/synchronousreceive-element.md)|<span data-ttu-id="c2609-146">サービスまたはクライアント アプリケーションでメッセージを受信する場合のランタイム動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2609-146">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="c2609-147">属性や子要素はありません。</span><span class="sxs-lookup"><span data-stu-id="c2609-147">It does not have any attributes or child elements.</span></span>|  
|[<span data-ttu-id="c2609-148">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="c2609-148">\<transactedBatching></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transactedbatching.md)|<span data-ttu-id="c2609-149">受信操作でトランザクション バッチがサポートされるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c2609-149">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[<span data-ttu-id="c2609-150">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="c2609-150">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)|<span data-ttu-id="c2609-151">構成によってエンドポイントに WebHttpBehavior を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2609-151">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="c2609-152">この動作と組み合わせて使用すると、 \<webHttpBinding > 標準バインディングの Web プログラミング モデルを有効に、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サービス。</span><span class="sxs-lookup"><span data-stu-id="c2609-152">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2609-153">親要素</span><span class="sxs-lookup"><span data-stu-id="c2609-153">Parent Elements</span></span>  
  
|<span data-ttu-id="c2609-154">要素</span><span class="sxs-lookup"><span data-stu-id="c2609-154">Element</span></span>|<span data-ttu-id="c2609-155">説明</span><span class="sxs-lookup"><span data-stu-id="c2609-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2609-156">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c2609-156">\<endpointBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|<span data-ttu-id="c2609-157">エンドポイント動作要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="c2609-157">A collection of endpoint behavior elements.</span></span>|
