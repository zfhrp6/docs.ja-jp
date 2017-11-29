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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04780d51cfd1d1d0049fc608cf7bd304be382b9b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="9d606-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="9d606-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="9d606-103">True に評価されると、フィルターに対してメッセージと、クライアント エンドポイントにメッセージをルーティングを評価するフィルターの一覧を含むルーティング テーブルを表します。</span><span class="sxs-lookup"><span data-stu-id="9d606-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="9d606-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="9d606-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9d606-105">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="9d606-105">\<routing></span></span>  
<span data-ttu-id="9d606-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="9d606-106">\<routingTables></span></span>  
<span data-ttu-id="9d606-107">\<テーブル ></span><span class="sxs-lookup"><span data-stu-id="9d606-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d606-108">構文</span><span class="sxs-lookup"><span data-stu-id="9d606-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9d606-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="9d606-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9d606-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="9d606-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d606-111">属性</span><span class="sxs-lookup"><span data-stu-id="9d606-111">Attributes</span></span>  
  
|<span data-ttu-id="9d606-112">要素</span><span class="sxs-lookup"><span data-stu-id="9d606-112">Element</span></span>|<span data-ttu-id="9d606-113">説明</span><span class="sxs-lookup"><span data-stu-id="9d606-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d606-114">name</span><span class="sxs-lookup"><span data-stu-id="9d606-114">name</span></span>|<span data-ttu-id="9d606-115">この構成要素の一意の名前を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="9d606-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d606-116">子要素</span><span class="sxs-lookup"><span data-stu-id="9d606-116">Child Elements</span></span>  
  
|<span data-ttu-id="9d606-117">要素</span><span class="sxs-lookup"><span data-stu-id="9d606-117">Element</span></span>|<span data-ttu-id="9d606-118">説明</span><span class="sxs-lookup"><span data-stu-id="9d606-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d606-119">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="9d606-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="9d606-120">ルーティング フィルターとターゲット エンドポイントとのマッピング。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9d606-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d606-121">親要素</span><span class="sxs-lookup"><span data-stu-id="9d606-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9d606-122">要素</span><span class="sxs-lookup"><span data-stu-id="9d606-122">Element</span></span>|<span data-ttu-id="9d606-123">説明</span><span class="sxs-lookup"><span data-stu-id="9d606-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d606-124">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="9d606-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="9d606-125">ルーティング テーブルを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="9d606-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d606-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d606-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
