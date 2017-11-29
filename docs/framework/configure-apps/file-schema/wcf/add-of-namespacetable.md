---
title: "&lt;namespaceTable&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f08f4b46c6e6290602fc78a2f06954b9cf0b07d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="c9852-102">&lt;namespaceTable&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="c9852-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="c9852-103">名前空間とプレフィックスのマッピングを含む構成要素を表します。これは、ルーティングの XPath フィルターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9852-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="c9852-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="c9852-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c9852-105">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="c9852-105">\<routing></span></span>  
<span data-ttu-id="c9852-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="c9852-106">\<namespaceTable></span></span>  
<span data-ttu-id="c9852-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c9852-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9852-108">構文</span><span class="sxs-lookup"><span data-stu-id="c9852-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9852-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c9852-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c9852-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c9852-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9852-111">属性</span><span class="sxs-lookup"><span data-stu-id="c9852-111">Attributes</span></span>  
  
|<span data-ttu-id="c9852-112">属性</span><span class="sxs-lookup"><span data-stu-id="c9852-112">Attribute</span></span>|<span data-ttu-id="c9852-113">説明</span><span class="sxs-lookup"><span data-stu-id="c9852-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9852-114">namespace</span><span class="sxs-lookup"><span data-stu-id="c9852-114">namespace</span></span>|<span data-ttu-id="c9852-115">名前空間を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="c9852-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="c9852-116">prefix</span><span class="sxs-lookup"><span data-stu-id="c9852-116">prefix</span></span>|<span data-ttu-id="c9852-117">この名前空間のプレフィックスを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="c9852-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9852-118">子要素</span><span class="sxs-lookup"><span data-stu-id="c9852-118">Child Elements</span></span>  
 <span data-ttu-id="c9852-119">なし。</span><span class="sxs-lookup"><span data-stu-id="c9852-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9852-120">親要素</span><span class="sxs-lookup"><span data-stu-id="c9852-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c9852-121">要素</span><span class="sxs-lookup"><span data-stu-id="c9852-121">Element</span></span>|<span data-ttu-id="c9852-122">説明</span><span class="sxs-lookup"><span data-stu-id="c9852-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9852-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="c9852-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="c9852-124">名前空間とプレフィックスのマッピングを含む要素セットを定義する構成セクションを表します。これは、ルーティングの XPath フィルターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c9852-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9852-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9852-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
