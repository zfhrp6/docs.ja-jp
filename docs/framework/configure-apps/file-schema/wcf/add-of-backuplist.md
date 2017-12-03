---
title: "&lt;backupList&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b93b442d21d34eea5031cea565bdcf62139abc81
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="423d8-102">&lt;backupList&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="423d8-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="423d8-103">バックアップ エンドポイント要素を定義する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="423d8-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="423d8-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="423d8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="423d8-105">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="423d8-105">\<routing></span></span>  
<span data-ttu-id="423d8-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="423d8-106">\<backupLists></span></span>  
<span data-ttu-id="423d8-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="423d8-107">\<backupList></span></span>  
<span data-ttu-id="423d8-108">\<add></span><span class="sxs-lookup"><span data-stu-id="423d8-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="423d8-109">構文</span><span class="sxs-lookup"><span data-stu-id="423d8-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="423d8-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="423d8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="423d8-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="423d8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="423d8-112">属性</span><span class="sxs-lookup"><span data-stu-id="423d8-112">Attributes</span></span>  
  
|<span data-ttu-id="423d8-113">属性</span><span class="sxs-lookup"><span data-stu-id="423d8-113">Attribute</span></span>|<span data-ttu-id="423d8-114">説明</span><span class="sxs-lookup"><span data-stu-id="423d8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="423d8-115">name</span><span class="sxs-lookup"><span data-stu-id="423d8-115">name</span></span>|<span data-ttu-id="423d8-116">バックアップ エンドポイントの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="423d8-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="423d8-117">子要素</span><span class="sxs-lookup"><span data-stu-id="423d8-117">Child Elements</span></span>  
 <span data-ttu-id="423d8-118">なし。</span><span class="sxs-lookup"><span data-stu-id="423d8-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="423d8-119">親要素</span><span class="sxs-lookup"><span data-stu-id="423d8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="423d8-120">要素</span><span class="sxs-lookup"><span data-stu-id="423d8-120">Element</span></span>|<span data-ttu-id="423d8-121">説明</span><span class="sxs-lookup"><span data-stu-id="423d8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="423d8-122">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="423d8-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="423d8-123">プライマリ エンドポイントに到達できない場合に使用するルーティング サービスを希望するエンドポイントの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="423d8-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="423d8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="423d8-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
