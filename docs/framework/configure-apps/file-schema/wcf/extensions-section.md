---
title: '&lt;extensions&gt; セクション'
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 09cabfc6c03602c3b6de343a29b5b25755f2cf0f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltextensionsgt-section"></a><span data-ttu-id="e220c-102">&lt;extensions&gt; セクション</span><span class="sxs-lookup"><span data-stu-id="e220c-102">&lt;extensions&gt; section</span></span>
<span data-ttu-id="e220c-103">この構成セクションには、拡張のコレクションが含まれています。この拡張のコレクションによってユーザーは、ユーザー定義のバインディング、動作、およびその他の拡張機能を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e220c-103">This configuration section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>  
  
<span data-ttu-id="e220c-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e220c-104">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e220c-105">構文</span><span class="sxs-lookup"><span data-stu-id="e220c-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <extensions>  
    <bindingExtensions>  
    </bindingExtensions>  
    <behaviorExtensions>  
    </behaviorExtensions>  
    <bindingElementExtensions>  
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e220c-106">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e220c-106">Attributes and Elements</span></span>  
 <span data-ttu-id="e220c-107">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e220c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e220c-108">属性</span><span class="sxs-lookup"><span data-stu-id="e220c-108">Attributes</span></span>  
 <span data-ttu-id="e220c-109">なし。</span><span class="sxs-lookup"><span data-stu-id="e220c-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e220c-110">子要素</span><span class="sxs-lookup"><span data-stu-id="e220c-110">Child Elements</span></span>  
  
|<span data-ttu-id="e220c-111">要素</span><span class="sxs-lookup"><span data-stu-id="e220c-111">Element</span></span>|<span data-ttu-id="e220c-112">説明</span><span class="sxs-lookup"><span data-stu-id="e220c-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e220c-113">\<behaviorExtensions ></span><span class="sxs-lookup"><span data-stu-id="e220c-113">\<behaviorExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|<span data-ttu-id="e220c-114">このセクションには、動作拡張を指定する子要素が含まれています。この動作拡張により、ユーザーはサービスまたはエンドポイントの動作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="e220c-114">This section contains child elements that specify behavior extensions, which enable the user to customize service or endpoint behaviors.</span></span>|  
|[<span data-ttu-id="e220c-115">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="e220c-115">\<bindingElementExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|<span data-ttu-id="e220c-116">このセクションは、コンピューターまたはアプリケーションの構成ファイルからカスタム バインド要素を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e220c-116">This section enables the use of a custom binding element from a machine or application configuration file.</span></span>|  
|[<span data-ttu-id="e220c-117">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="e220c-117">\<bindingExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|<span data-ttu-id="e220c-118">このセクションには、バインディング拡張を指定する子要素が含まれています。このバインディング拡張によって、ユーザーはバインディングをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="e220c-118">This section contains child elements that specify binding extensions, which enable the user to customize bindings.</span></span>|  
|[<span data-ttu-id="e220c-119">\<endpointExtensions ></span><span class="sxs-lookup"><span data-stu-id="e220c-119">\<endpointExtensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|<span data-ttu-id="e220c-120">このセクションには、標準エンドポイントを登録する子要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e220c-120">This section contains child elements that registers standard endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e220c-121">親要素</span><span class="sxs-lookup"><span data-stu-id="e220c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e220c-122">要素</span><span class="sxs-lookup"><span data-stu-id="e220c-122">Element</span></span>|<span data-ttu-id="e220c-123">説明</span><span class="sxs-lookup"><span data-stu-id="e220c-123">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e220c-124">system.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e220c-124">system.ServiceModel</span></span>|<span data-ttu-id="e220c-125">すべての WCF 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="e220c-125">The root element of all WCF configuration elements.</span></span>|
