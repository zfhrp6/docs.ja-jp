---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 7bdc76ba7a8e2927b93fa0207f48cc569279482f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="5e103-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="5e103-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="5e103-103">True に評価されると、フィルターに対してメッセージと、クライアント エンドポイントにメッセージをルーティングを評価するフィルターの一覧を含むルーティング テーブルを表します。</span><span class="sxs-lookup"><span data-stu-id="5e103-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="5e103-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5e103-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5e103-105">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="5e103-105">\<routing></span></span>  
<span data-ttu-id="5e103-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="5e103-106">\<routingTables></span></span>  
<span data-ttu-id="5e103-107">\<テーブル ></span><span class="sxs-lookup"><span data-stu-id="5e103-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e103-108">構文</span><span class="sxs-lookup"><span data-stu-id="5e103-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5e103-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="5e103-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5e103-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="5e103-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e103-111">属性</span><span class="sxs-lookup"><span data-stu-id="5e103-111">Attributes</span></span>  
  
|<span data-ttu-id="5e103-112">要素</span><span class="sxs-lookup"><span data-stu-id="5e103-112">Element</span></span>|<span data-ttu-id="5e103-113">説明</span><span class="sxs-lookup"><span data-stu-id="5e103-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e103-114">name</span><span class="sxs-lookup"><span data-stu-id="5e103-114">name</span></span>|<span data-ttu-id="5e103-115">この構成要素の一意の名前を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="5e103-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e103-116">子要素</span><span class="sxs-lookup"><span data-stu-id="5e103-116">Child Elements</span></span>  
  
|<span data-ttu-id="5e103-117">要素</span><span class="sxs-lookup"><span data-stu-id="5e103-117">Element</span></span>|<span data-ttu-id="5e103-118">説明</span><span class="sxs-lookup"><span data-stu-id="5e103-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e103-119">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="5e103-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="5e103-120">ルーティング フィルターとターゲット エンドポイントとのマッピング。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5e103-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e103-121">親要素</span><span class="sxs-lookup"><span data-stu-id="5e103-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5e103-122">要素</span><span class="sxs-lookup"><span data-stu-id="5e103-122">Element</span></span>|<span data-ttu-id="5e103-123">説明</span><span class="sxs-lookup"><span data-stu-id="5e103-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e103-124">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="5e103-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="5e103-125">ルーティング テーブルを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="5e103-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e103-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e103-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
