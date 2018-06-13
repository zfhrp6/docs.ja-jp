---
title: '&lt;entries&gt; の &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: a6960c16c84c13d905f0993ee3cfc1cf67df07fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744981"
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="cbece-102">&lt;entries&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="cbece-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="cbece-103">以前に定義されたクライアント エンドポイントにフィルターをマップするルーティング エントリを表します。</span><span class="sxs-lookup"><span data-stu-id="cbece-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="cbece-104">このフィルターに一致するメッセージは、この宛先に送信されます。</span><span class="sxs-lookup"><span data-stu-id="cbece-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="cbece-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="cbece-105">\<system.serviceModel></span></span>  
<span data-ttu-id="cbece-106">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="cbece-106">\<routing></span></span>  
<span data-ttu-id="cbece-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="cbece-107">\<routingTables></span></span>  
<span data-ttu-id="cbece-108">\<テーブル ></span><span class="sxs-lookup"><span data-stu-id="cbece-108">\<table></span></span>  
<span data-ttu-id="cbece-109">\<エントリ ></span><span class="sxs-lookup"><span data-stu-id="cbece-109">\<entries></span></span>  
<span data-ttu-id="cbece-110">\<add></span><span class="sxs-lookup"><span data-stu-id="cbece-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbece-111">構文</span><span class="sxs-lookup"><span data-stu-id="cbece-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbece-112">属性および要素</span><span class="sxs-lookup"><span data-stu-id="cbece-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cbece-113">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="cbece-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbece-114">属性</span><span class="sxs-lookup"><span data-stu-id="cbece-114">Attributes</span></span>  
  
|<span data-ttu-id="cbece-115">属性</span><span class="sxs-lookup"><span data-stu-id="cbece-115">Attribute</span></span>|<span data-ttu-id="cbece-116">説明</span><span class="sxs-lookup"><span data-stu-id="cbece-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbece-117">backupList</span><span class="sxs-lookup"><span data-stu-id="cbece-117">backupList</span></span>|<span data-ttu-id="cbece-118">エンドポイントのバックアップ リストへの参照を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="cbece-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="cbece-119">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="cbece-119">endpoint</span></span>|<span data-ttu-id="cbece-120">`filterName` 属性で指定されたフィルターに一致するメッセージを受信するクライアント エンドポイントへの参照を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="cbece-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="cbece-121">filterName</span><span class="sxs-lookup"><span data-stu-id="cbece-121">filterName</span></span>|<span data-ttu-id="cbece-122">フィルター要素への参照を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="cbece-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="cbece-123">priority</span><span class="sxs-lookup"><span data-stu-id="cbece-123">priority</span></span>|<span data-ttu-id="cbece-124">このエントリの優先順位を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="cbece-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="cbece-125">ルーティング テーブルのエントリは、優先順位に基づいて評価されます。0 が最下位の優先順位です。</span><span class="sxs-lookup"><span data-stu-id="cbece-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="cbece-126">特定の優先順位について、すべてのエントリが同時に評価されます。現在の優先順位について一致するエントリが見つからない場合は、次の優先順位が評価されます。</span><span class="sxs-lookup"><span data-stu-id="cbece-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="cbece-127">この値はオプションです。</span><span class="sxs-lookup"><span data-stu-id="cbece-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbece-128">子要素</span><span class="sxs-lookup"><span data-stu-id="cbece-128">Child Elements</span></span>  
 <span data-ttu-id="cbece-129">なし。</span><span class="sxs-lookup"><span data-stu-id="cbece-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cbece-130">親要素</span><span class="sxs-lookup"><span data-stu-id="cbece-130">Parent Elements</span></span>  
  
|<span data-ttu-id="cbece-131">要素</span><span class="sxs-lookup"><span data-stu-id="cbece-131">Element</span></span>|<span data-ttu-id="cbece-132">説明</span><span class="sxs-lookup"><span data-stu-id="cbece-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbece-133">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="cbece-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="cbece-134">ルーティング マッピング エントリを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="cbece-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbece-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="cbece-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
