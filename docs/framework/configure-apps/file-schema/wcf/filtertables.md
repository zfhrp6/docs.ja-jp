---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 966556a1a8bde72e33640dcc6fd37ae7a044ceef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="b52d3-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="b52d3-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="b52d3-103">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納するルーティング テーブルを定義する構成セクションを表します。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b52d3-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="b52d3-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b52d3-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b52d3-105">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="b52d3-105">\<routing></span></span>  
<span data-ttu-id="b52d3-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="b52d3-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b52d3-107">構文</span><span class="sxs-lookup"><span data-stu-id="b52d3-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b52d3-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b52d3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b52d3-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b52d3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b52d3-110">属性</span><span class="sxs-lookup"><span data-stu-id="b52d3-110">Attributes</span></span>  
 <span data-ttu-id="b52d3-111">なし。</span><span class="sxs-lookup"><span data-stu-id="b52d3-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b52d3-112">子要素</span><span class="sxs-lookup"><span data-stu-id="b52d3-112">Child Elements</span></span>  
  
|<span data-ttu-id="b52d3-113">要素</span><span class="sxs-lookup"><span data-stu-id="b52d3-113">Element</span></span>|<span data-ttu-id="b52d3-114">説明</span><span class="sxs-lookup"><span data-stu-id="b52d3-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b52d3-115">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="b52d3-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="b52d3-116">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納するルーティング テーブル。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b52d3-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b52d3-117">親要素</span><span class="sxs-lookup"><span data-stu-id="b52d3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b52d3-118">要素</span><span class="sxs-lookup"><span data-stu-id="b52d3-118">Element</span></span>|<span data-ttu-id="b52d3-119">説明</span><span class="sxs-lookup"><span data-stu-id="b52d3-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b52d3-120">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="b52d3-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="b52d3-121">ルーティング フィルターおよびルーティング テーブルを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="b52d3-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b52d3-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b52d3-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
