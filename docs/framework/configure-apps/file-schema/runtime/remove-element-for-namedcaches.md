---
title: '&lt;削除&gt;要素&lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6ffaea24910a6b8f4a120d6b72219bff592fab17
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="6cd4b-102">&lt;削除&gt;要素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="6cd4b-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="6cd4b-103">名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="6cd4b-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="6cd4b-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="6cd4b-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="6cd4b-105">\<memoryCache></span></span>  
<span data-ttu-id="6cd4b-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="6cd4b-106">\<namedCaches></span></span>  
<span data-ttu-id="6cd4b-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="6cd4b-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd4b-108">構文</span><span class="sxs-lookup"><span data-stu-id="6cd4b-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="6cd4b-109">型</span><span class="sxs-lookup"><span data-stu-id="6cd4b-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cd4b-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6cd4b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6cd4b-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cd4b-112">属性</span><span class="sxs-lookup"><span data-stu-id="6cd4b-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="6cd4b-113">子要素</span><span class="sxs-lookup"><span data-stu-id="6cd4b-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="6cd4b-114">親要素</span><span class="sxs-lookup"><span data-stu-id="6cd4b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6cd4b-115">要素</span><span class="sxs-lookup"><span data-stu-id="6cd4b-115">Element</span></span>|<span data-ttu-id="6cd4b-116">説明</span><span class="sxs-lookup"><span data-stu-id="6cd4b-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cd4b-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="6cd4b-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="6cd4b-118">名前付きの構成設定のコレクションを含んでいます<xref:System.Runtime.Caching.MemoryCache>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cd4b-119">コメント</span><span class="sxs-lookup"><span data-stu-id="6cd4b-119">Remarks</span></span>  
 <span data-ttu-id="6cd4b-120">`remove`要素を削除して、`namedCache`メモリ キャッシュの名前付きキャッシュのコレクションから入力します。</span><span class="sxs-lookup"><span data-stu-id="6cd4b-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd4b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="6cd4b-121">See Also</span></span>  
 [<span data-ttu-id="6cd4b-122">\<namedCaches > 要素 (キャッシュの設定)</span><span class="sxs-lookup"><span data-stu-id="6cd4b-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
