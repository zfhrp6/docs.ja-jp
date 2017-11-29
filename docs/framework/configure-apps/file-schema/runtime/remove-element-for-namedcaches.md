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
ms.openlocfilehash: 6170b59e87948225708c9e697cba1542d756d2f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="29361-102">&lt;削除&gt;要素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="29361-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="29361-103">名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="29361-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="29361-104">\<system.runtime.caching ></span><span class="sxs-lookup"><span data-stu-id="29361-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="29361-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="29361-105">\<memoryCache></span></span>  
<span data-ttu-id="29361-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="29361-106">\<namedCaches></span></span>  
<span data-ttu-id="29361-107">\<削除 ></span><span class="sxs-lookup"><span data-stu-id="29361-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29361-108">構文</span><span class="sxs-lookup"><span data-stu-id="29361-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="29361-109">型</span><span class="sxs-lookup"><span data-stu-id="29361-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29361-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="29361-110">Attributes and Elements</span></span>  
 <span data-ttu-id="29361-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="29361-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29361-112">属性</span><span class="sxs-lookup"><span data-stu-id="29361-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="29361-113">子要素</span><span class="sxs-lookup"><span data-stu-id="29361-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="29361-114">親要素</span><span class="sxs-lookup"><span data-stu-id="29361-114">Parent Elements</span></span>  
  
|<span data-ttu-id="29361-115">要素</span><span class="sxs-lookup"><span data-stu-id="29361-115">Element</span></span>|<span data-ttu-id="29361-116">説明</span><span class="sxs-lookup"><span data-stu-id="29361-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29361-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="29361-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="29361-118">名前付きの構成設定のコレクションを含んでいます<xref:System.Runtime.Caching.MemoryCache>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="29361-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29361-119">コメント</span><span class="sxs-lookup"><span data-stu-id="29361-119">Remarks</span></span>  
 <span data-ttu-id="29361-120">`remove`要素を削除して、`namedCache`メモリ キャッシュの名前付きキャッシュのコレクションから入力します。</span><span class="sxs-lookup"><span data-stu-id="29361-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29361-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="29361-121">See Also</span></span>  
 [<span data-ttu-id="29361-122">\<namedCaches > 要素 (キャッシュの設定)</span><span class="sxs-lookup"><span data-stu-id="29361-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
