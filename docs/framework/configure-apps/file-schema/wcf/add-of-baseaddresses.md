---
title: '&lt;baseAddresses&gt; の &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: 3f1b7e8f1f4ab8542270d459ce5020ce4320eea9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754146"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="5e789-102">&lt;baseAddresses&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="5e789-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="5e789-103">サービス ホストによって使用されるベース アドレスを指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="5e789-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="5e789-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5e789-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e789-105">\<client></span><span class="sxs-lookup"><span data-stu-id="5e789-105">\<client></span></span>  
<span data-ttu-id="5e789-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="5e789-106">\<endpoint></span></span>  
<span data-ttu-id="5e789-107">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="5e789-107">\<host></span></span>  
<span data-ttu-id="5e789-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="5e789-108">\<baseAddresses></span></span>  
<span data-ttu-id="5e789-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="5e789-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e789-110">構文</span><span class="sxs-lookup"><span data-stu-id="5e789-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="5e789-111">型</span><span class="sxs-lookup"><span data-stu-id="5e789-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e789-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5e789-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5e789-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e789-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e789-114">属性</span><span class="sxs-lookup"><span data-stu-id="5e789-114">Attributes</span></span>  
  
|<span data-ttu-id="5e789-115">属性</span><span class="sxs-lookup"><span data-stu-id="5e789-115">Attribute</span></span>|<span data-ttu-id="5e789-116">説明</span><span class="sxs-lookup"><span data-stu-id="5e789-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="5e789-117">サービス ホストによって使用されるベース アドレスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="5e789-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e789-118">子要素</span><span class="sxs-lookup"><span data-stu-id="5e789-118">Child Elements</span></span>  
 <span data-ttu-id="5e789-119">なし。</span><span class="sxs-lookup"><span data-stu-id="5e789-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e789-120">親要素</span><span class="sxs-lookup"><span data-stu-id="5e789-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5e789-121">要素</span><span class="sxs-lookup"><span data-stu-id="5e789-121">Element</span></span>|<span data-ttu-id="5e789-122">説明</span><span class="sxs-lookup"><span data-stu-id="5e789-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e789-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="5e789-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="5e789-124">`baseAddress` 要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="5e789-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e789-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e789-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="5e789-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="5e789-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
