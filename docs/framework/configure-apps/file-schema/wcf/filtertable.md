---
title: '&lt;filterTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cf87cc74c7bb5d495584407c803dacc7b94f195
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="d21c7-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="d21c7-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="d21c7-103">True に評価されると、フィルターに対してメッセージと、クライアント エンドポイントにメッセージをルーティングを評価するフィルターの一覧を含むルーティング テーブルを表します。</span><span class="sxs-lookup"><span data-stu-id="d21c7-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="d21c7-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d21c7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d21c7-105">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="d21c7-105">\<routing></span></span>  
<span data-ttu-id="d21c7-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="d21c7-106">\<routingTables></span></span>  
<span data-ttu-id="d21c7-107">\<テーブル ></span><span class="sxs-lookup"><span data-stu-id="d21c7-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d21c7-108">構文</span><span class="sxs-lookup"><span data-stu-id="d21c7-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d21c7-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d21c7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d21c7-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d21c7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d21c7-111">属性</span><span class="sxs-lookup"><span data-stu-id="d21c7-111">Attributes</span></span>  
  
|<span data-ttu-id="d21c7-112">要素</span><span class="sxs-lookup"><span data-stu-id="d21c7-112">Element</span></span>|<span data-ttu-id="d21c7-113">説明</span><span class="sxs-lookup"><span data-stu-id="d21c7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d21c7-114">name</span><span class="sxs-lookup"><span data-stu-id="d21c7-114">name</span></span>|<span data-ttu-id="d21c7-115">この構成要素の一意の名前を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="d21c7-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d21c7-116">子要素</span><span class="sxs-lookup"><span data-stu-id="d21c7-116">Child Elements</span></span>  
  
|<span data-ttu-id="d21c7-117">要素</span><span class="sxs-lookup"><span data-stu-id="d21c7-117">Element</span></span>|<span data-ttu-id="d21c7-118">説明</span><span class="sxs-lookup"><span data-stu-id="d21c7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d21c7-119">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="d21c7-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="d21c7-120">ルーティング フィルターとターゲット エンドポイントとのマッピング。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d21c7-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d21c7-121">親要素</span><span class="sxs-lookup"><span data-stu-id="d21c7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d21c7-122">要素</span><span class="sxs-lookup"><span data-stu-id="d21c7-122">Element</span></span>|<span data-ttu-id="d21c7-123">説明</span><span class="sxs-lookup"><span data-stu-id="d21c7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d21c7-124">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="d21c7-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d21c7-125">ルーティング テーブルを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="d21c7-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d21c7-126">参照</span><span class="sxs-lookup"><span data-stu-id="d21c7-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
