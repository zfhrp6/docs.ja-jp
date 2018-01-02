---
title: "&lt;タイムアウト&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04003584cf12355116d32cccffdcb2b9990b1b85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="841f4-102">&lt;タイムアウト&gt;</span><span class="sxs-lookup"><span data-stu-id="841f4-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="841f4-103">サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="841f4-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="841f4-104">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="841f4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="841f4-105">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="841f4-105">\<client></span></span>  
<span data-ttu-id="841f4-106">\<エンドポイント ></span><span class="sxs-lookup"><span data-stu-id="841f4-106">\<endpoint></span></span>  
<span data-ttu-id="841f4-107">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="841f4-107">\<host></span></span>  
<span data-ttu-id="841f4-108">\<タイムアウト ></span><span class="sxs-lookup"><span data-stu-id="841f4-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="841f4-109">構文</span><span class="sxs-lookup"><span data-stu-id="841f4-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="841f4-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="841f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="841f4-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="841f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="841f4-112">属性</span><span class="sxs-lookup"><span data-stu-id="841f4-112">Attributes</span></span>  
  
|<span data-ttu-id="841f4-113">属性</span><span class="sxs-lookup"><span data-stu-id="841f4-113">Attribute</span></span>|<span data-ttu-id="841f4-114">説明</span><span class="sxs-lookup"><span data-stu-id="841f4-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="841f4-115">サービス ホストを閉じるまでに待機できる期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="841f4-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="841f4-116">サービス ホストを開くまでに待機できる期間を指定する <xref:System.TimeSpan> 値。</span><span class="sxs-lookup"><span data-stu-id="841f4-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="841f4-117">子要素</span><span class="sxs-lookup"><span data-stu-id="841f4-117">Child Elements</span></span>  
 <span data-ttu-id="841f4-118">なし。</span><span class="sxs-lookup"><span data-stu-id="841f4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="841f4-119">親要素</span><span class="sxs-lookup"><span data-stu-id="841f4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="841f4-120">要素</span><span class="sxs-lookup"><span data-stu-id="841f4-120">Element</span></span>|<span data-ttu-id="841f4-121">説明</span><span class="sxs-lookup"><span data-stu-id="841f4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="841f4-122">\<ホスト ></span><span class="sxs-lookup"><span data-stu-id="841f4-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="841f4-123">サービス ホストの設定を指定する構成要素です。</span><span class="sxs-lookup"><span data-stu-id="841f4-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="841f4-124">参照</span><span class="sxs-lookup"><span data-stu-id="841f4-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="841f4-125">ホスティング</span><span class="sxs-lookup"><span data-stu-id="841f4-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
