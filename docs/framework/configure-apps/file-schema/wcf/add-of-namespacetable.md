---
title: '&lt;namespaceTable&gt; の &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 5ae672f12a2ef58efc9738624c113855e59e02b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a><span data-ttu-id="4955a-102">&lt;namespaceTable&gt; の &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="4955a-102">&lt;add&gt; of &lt;namespaceTable&gt;</span></span>
<span data-ttu-id="4955a-103">名前空間とプレフィックスのマッピングを含む構成要素を表します。これは、ルーティングの XPath フィルターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="4955a-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="4955a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4955a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4955a-105">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="4955a-105">\<routing></span></span>  
<span data-ttu-id="4955a-106">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="4955a-106">\<namespaceTable></span></span>  
<span data-ttu-id="4955a-107">\<add></span><span class="sxs-lookup"><span data-stu-id="4955a-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4955a-108">構文</span><span class="sxs-lookup"><span data-stu-id="4955a-108">Syntax</span></span>  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4955a-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="4955a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4955a-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="4955a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4955a-111">属性</span><span class="sxs-lookup"><span data-stu-id="4955a-111">Attributes</span></span>  
  
|<span data-ttu-id="4955a-112">属性</span><span class="sxs-lookup"><span data-stu-id="4955a-112">Attribute</span></span>|<span data-ttu-id="4955a-113">説明</span><span class="sxs-lookup"><span data-stu-id="4955a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4955a-114">namespace</span><span class="sxs-lookup"><span data-stu-id="4955a-114">namespace</span></span>|<span data-ttu-id="4955a-115">名前空間を示す文字列。</span><span class="sxs-lookup"><span data-stu-id="4955a-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="4955a-116">prefix</span><span class="sxs-lookup"><span data-stu-id="4955a-116">prefix</span></span>|<span data-ttu-id="4955a-117">この名前空間のプレフィックスを示す文字列。</span><span class="sxs-lookup"><span data-stu-id="4955a-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4955a-118">子要素</span><span class="sxs-lookup"><span data-stu-id="4955a-118">Child Elements</span></span>  
 <span data-ttu-id="4955a-119">なし。</span><span class="sxs-lookup"><span data-stu-id="4955a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4955a-120">親要素</span><span class="sxs-lookup"><span data-stu-id="4955a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="4955a-121">要素</span><span class="sxs-lookup"><span data-stu-id="4955a-121">Element</span></span>|<span data-ttu-id="4955a-122">説明</span><span class="sxs-lookup"><span data-stu-id="4955a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4955a-123">\<namespaceTable ></span><span class="sxs-lookup"><span data-stu-id="4955a-123">\<namespaceTable></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|<span data-ttu-id="4955a-124">名前空間とプレフィックスのマッピングを含む要素セットを定義する構成セクションを表します。これは、ルーティングの XPath フィルターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="4955a-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4955a-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="4955a-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
