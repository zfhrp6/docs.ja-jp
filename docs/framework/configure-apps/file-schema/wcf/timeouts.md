---
title: '&lt;タイムアウト&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 1f0638f85177d2acb6f61e3246a1a5ee9a4e2f5c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="90940-102">&lt;タイムアウト&gt;</span><span class="sxs-lookup"><span data-stu-id="90940-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="90940-103">サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="90940-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="90940-104">\<system.ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="90940-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="90940-105">\<client></span><span class="sxs-lookup"><span data-stu-id="90940-105">\<client></span></span>  
<span data-ttu-id="90940-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="90940-106">\<endpoint></span></span>  
<span data-ttu-id="90940-107">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="90940-107">\<host></span></span>  
<span data-ttu-id="90940-108">\<タイムアウト ></span><span class="sxs-lookup"><span data-stu-id="90940-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90940-109">構文</span><span class="sxs-lookup"><span data-stu-id="90940-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90940-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="90940-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90940-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="90940-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90940-112">属性</span><span class="sxs-lookup"><span data-stu-id="90940-112">Attributes</span></span>  
  
|<span data-ttu-id="90940-113">属性</span><span class="sxs-lookup"><span data-stu-id="90940-113">Attribute</span></span>|<span data-ttu-id="90940-114">説明</span><span class="sxs-lookup"><span data-stu-id="90940-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="90940-115">サービス ホストを閉じるまでに待機できる期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="90940-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="90940-116">サービス ホストを開くまでに待機できる期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="90940-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90940-117">子要素</span><span class="sxs-lookup"><span data-stu-id="90940-117">Child Elements</span></span>  
 <span data-ttu-id="90940-118">なし。</span><span class="sxs-lookup"><span data-stu-id="90940-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90940-119">親要素</span><span class="sxs-lookup"><span data-stu-id="90940-119">Parent Elements</span></span>  
  
|<span data-ttu-id="90940-120">要素</span><span class="sxs-lookup"><span data-stu-id="90940-120">Element</span></span>|<span data-ttu-id="90940-121">説明</span><span class="sxs-lookup"><span data-stu-id="90940-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90940-122">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="90940-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="90940-123">サービス ホストの設定を指定する構成要素です。</span><span class="sxs-lookup"><span data-stu-id="90940-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90940-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="90940-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="90940-125">ホスティング</span><span class="sxs-lookup"><span data-stu-id="90940-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
