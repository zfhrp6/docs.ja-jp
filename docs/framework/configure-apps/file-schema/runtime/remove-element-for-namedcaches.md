---
title: "&lt;削除&gt;要素&lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b360b206586b263627ab6f6b7e0309f3055f38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="18a0d-102">&lt;削除&gt;要素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="18a0d-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="18a0d-103">名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="18a0d-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="18a0d-104">\<system.runtime.caching ></span><span class="sxs-lookup"><span data-stu-id="18a0d-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="18a0d-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="18a0d-105">\<memoryCache></span></span>  
<span data-ttu-id="18a0d-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="18a0d-106">\<namedCaches></span></span>  
<span data-ttu-id="18a0d-107">\<削除 ></span><span class="sxs-lookup"><span data-stu-id="18a0d-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18a0d-108">構文</span><span class="sxs-lookup"><span data-stu-id="18a0d-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="18a0d-109">型</span><span class="sxs-lookup"><span data-stu-id="18a0d-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18a0d-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="18a0d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="18a0d-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="18a0d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18a0d-112">属性</span><span class="sxs-lookup"><span data-stu-id="18a0d-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="18a0d-113">子要素</span><span class="sxs-lookup"><span data-stu-id="18a0d-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="18a0d-114">親要素</span><span class="sxs-lookup"><span data-stu-id="18a0d-114">Parent Elements</span></span>  
  
|<span data-ttu-id="18a0d-115">要素</span><span class="sxs-lookup"><span data-stu-id="18a0d-115">Element</span></span>|<span data-ttu-id="18a0d-116">説明</span><span class="sxs-lookup"><span data-stu-id="18a0d-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18a0d-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="18a0d-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="18a0d-118">名前付きの構成設定のコレクションを含んでいます<xref:System.Runtime.Caching.MemoryCache>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="18a0d-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18a0d-119">コメント</span><span class="sxs-lookup"><span data-stu-id="18a0d-119">Remarks</span></span>  
 <span data-ttu-id="18a0d-120">`remove`要素を削除して、`namedCache`メモリ キャッシュの名前付きキャッシュのコレクションから入力します。</span><span class="sxs-lookup"><span data-stu-id="18a0d-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18a0d-121">参照</span><span class="sxs-lookup"><span data-stu-id="18a0d-121">See Also</span></span>  
 [<span data-ttu-id="18a0d-122">\<namedCaches > 要素 (キャッシュの設定)</span><span class="sxs-lookup"><span data-stu-id="18a0d-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
