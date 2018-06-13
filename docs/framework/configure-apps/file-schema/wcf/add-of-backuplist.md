---
title: '&lt;backupList&gt; の &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: bc5939fc-314a-4ea4-a533-c96958da7173
ms.openlocfilehash: 7e7361b24c0444b5f3d51a6f5bf079d5eb2dee18
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745553"
---
# <a name="ltaddgt-of-ltbackuplistgt"></a><span data-ttu-id="e45ee-102">&lt;backupList&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="e45ee-102">&lt;add&gt; of &lt;backupList&gt;</span></span>
<span data-ttu-id="e45ee-103">バックアップ エンドポイント要素を定義する構成要素を表します。</span><span class="sxs-lookup"><span data-stu-id="e45ee-103">Represents a configuration element that defines a backup endpoint element.</span></span>  
  
 <span data-ttu-id="e45ee-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e45ee-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e45ee-105">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="e45ee-105">\<routing></span></span>  
<span data-ttu-id="e45ee-106">\<backupLists ></span><span class="sxs-lookup"><span data-stu-id="e45ee-106">\<backupLists></span></span>  
<span data-ttu-id="e45ee-107">\<backupList ></span><span class="sxs-lookup"><span data-stu-id="e45ee-107">\<backupList></span></span>  
<span data-ttu-id="e45ee-108">\<add></span><span class="sxs-lookup"><span data-stu-id="e45ee-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45ee-109">構文</span><span class="sxs-lookup"><span data-stu-id="e45ee-109">Syntax</span></span>  
  
```xml  
   <routing>  <backupLists>    <backupList name="String">      <add endpointName="String" />    </backupList>    </backupLists></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e45ee-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e45ee-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e45ee-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e45ee-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e45ee-112">属性</span><span class="sxs-lookup"><span data-stu-id="e45ee-112">Attributes</span></span>  
  
|<span data-ttu-id="e45ee-113">属性</span><span class="sxs-lookup"><span data-stu-id="e45ee-113">Attribute</span></span>|<span data-ttu-id="e45ee-114">説明</span><span class="sxs-lookup"><span data-stu-id="e45ee-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e45ee-115">name</span><span class="sxs-lookup"><span data-stu-id="e45ee-115">name</span></span>|<span data-ttu-id="e45ee-116">バックアップ エンドポイントの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="e45ee-116">A string that specifies the name of the backup endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e45ee-117">子要素</span><span class="sxs-lookup"><span data-stu-id="e45ee-117">Child Elements</span></span>  
 <span data-ttu-id="e45ee-118">なし。</span><span class="sxs-lookup"><span data-stu-id="e45ee-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e45ee-119">親要素</span><span class="sxs-lookup"><span data-stu-id="e45ee-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e45ee-120">要素</span><span class="sxs-lookup"><span data-stu-id="e45ee-120">Element</span></span>|<span data-ttu-id="e45ee-121">説明</span><span class="sxs-lookup"><span data-stu-id="e45ee-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e45ee-122">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="e45ee-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e45ee-123">プライマリ エンドポイントに到達できない場合に使用するルーティング サービスを希望するエンドポイントの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e45ee-123">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e45ee-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e45ee-124">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.BackupEndpointElement?displayProperty=nameWithType> 
