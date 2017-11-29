---
title: '&lt;filterTables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75e06b0258f2e4f65d441c25b5081cf7a6627518
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="e1857-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="e1857-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="e1857-103">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納するルーティング テーブルを定義する構成セクションを表します。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1857-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="e1857-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="e1857-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e1857-105">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="e1857-105">\<routing></span></span>  
<span data-ttu-id="e1857-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="e1857-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1857-107">構文</span><span class="sxs-lookup"><span data-stu-id="e1857-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e1857-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e1857-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e1857-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1857-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1857-110">属性</span><span class="sxs-lookup"><span data-stu-id="e1857-110">Attributes</span></span>  
 <span data-ttu-id="e1857-111">なし。</span><span class="sxs-lookup"><span data-stu-id="e1857-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e1857-112">子要素</span><span class="sxs-lookup"><span data-stu-id="e1857-112">Child Elements</span></span>  
  
|<span data-ttu-id="e1857-113">要素</span><span class="sxs-lookup"><span data-stu-id="e1857-113">Element</span></span>|<span data-ttu-id="e1857-114">説明</span><span class="sxs-lookup"><span data-stu-id="e1857-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1857-115">\<フィルター ></span><span class="sxs-lookup"><span data-stu-id="e1857-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="e1857-116">ルーティング フィルターとターゲット エンドポイントとのマッピングを格納するルーティング テーブル。フィルターが一致したときにメッセージを送信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e1857-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e1857-117">親要素</span><span class="sxs-lookup"><span data-stu-id="e1857-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e1857-118">要素</span><span class="sxs-lookup"><span data-stu-id="e1857-118">Element</span></span>|<span data-ttu-id="e1857-119">説明</span><span class="sxs-lookup"><span data-stu-id="e1857-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1857-120">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="e1857-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e1857-121">ルーティング フィルターおよびルーティング テーブルを含む構成セクション。</span><span class="sxs-lookup"><span data-stu-id="e1857-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1857-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1857-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
