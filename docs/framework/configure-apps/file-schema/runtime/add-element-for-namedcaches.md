---
title: "&lt;追加&gt;要素&lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0000e92c89920b05e0ffc93fab58fb0bd6ea6b13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="56e70-102">&lt;追加&gt;要素&lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="56e70-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="56e70-103">追加、`namedCache`エントリを`namedCaches`メモリ キャッシュのコレクション。</span><span class="sxs-lookup"><span data-stu-id="56e70-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="56e70-104">\<system.runtime.caching ></span><span class="sxs-lookup"><span data-stu-id="56e70-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="56e70-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="56e70-105">\<memoryCache></span></span>  
<span data-ttu-id="56e70-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="56e70-106">\<namedCaches></span></span>  
<span data-ttu-id="56e70-107">\<add></span><span class="sxs-lookup"><span data-stu-id="56e70-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e70-108">構文</span><span class="sxs-lookup"><span data-stu-id="56e70-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="56e70-109">型</span><span class="sxs-lookup"><span data-stu-id="56e70-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56e70-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="56e70-110">Attributes and Elements</span></span>  
 <span data-ttu-id="56e70-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="56e70-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56e70-112">属性</span><span class="sxs-lookup"><span data-stu-id="56e70-112">Attributes</span></span>  
  
|<span data-ttu-id="56e70-113">属性</span><span class="sxs-lookup"><span data-stu-id="56e70-113">Attribute</span></span>|<span data-ttu-id="56e70-114">説明</span><span class="sxs-lookup"><span data-stu-id="56e70-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="56e70-115">許容最大サイズ (メガバイト) 単位を指定する整数値のインスタンス、<xref:System.Runtime.Caching.MemoryCache>まで拡大できます。</span><span class="sxs-lookup"><span data-stu-id="56e70-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="56e70-116">既定値は 0、つまり、<xref:System.Runtime.Caching.MemoryCache>クラスのサイズの自動変更ヒューリスティックが既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="56e70-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="56e70-117">キャッシュの名前。</span><span class="sxs-lookup"><span data-stu-id="56e70-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="56e70-118">キャッシュで利用できる物理的にインストールされているコンピューターのメモリの最大パーセンテージを指定する整数 0 ~ 100 の値。</span><span class="sxs-lookup"><span data-stu-id="56e70-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="56e70-119">既定値は 0、つまり、<xref:System.Runtime.Caching.MemoryCache>クラスのサイズの自動変更ヒューリスティックが既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="56e70-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="56e70-120">時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。</span><span class="sxs-lookup"><span data-stu-id="56e70-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="56e70-121">この値は"HH:MM:SS"形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="56e70-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56e70-122">子要素</span><span class="sxs-lookup"><span data-stu-id="56e70-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="56e70-123">親要素</span><span class="sxs-lookup"><span data-stu-id="56e70-123">Parent Elements</span></span>  
  
|<span data-ttu-id="56e70-124">要素</span><span class="sxs-lookup"><span data-stu-id="56e70-124">Element</span></span>|<span data-ttu-id="56e70-125">説明</span><span class="sxs-lookup"><span data-stu-id="56e70-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56e70-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="56e70-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="56e70-127">名前付きの構成設定のコレクションを含んでいます<xref:System.Runtime.Caching.MemoryCache>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="56e70-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56e70-128">コメント</span><span class="sxs-lookup"><span data-stu-id="56e70-128">Remarks</span></span>  
 <span data-ttu-id="56e70-129">`add`要素へのエントリは追加、`namedCaches`メモリ キャッシュのコレクション。</span><span class="sxs-lookup"><span data-stu-id="56e70-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="56e70-130">使用することができます、[オフ](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)要素を使用する前に、`add`というコレクション内のキャッシュのあるものがあることの他の要素。</span><span class="sxs-lookup"><span data-stu-id="56e70-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="56e70-131">この要素は、machine.config ファイルでは、Web.config ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="56e70-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56e70-132">例</span><span class="sxs-lookup"><span data-stu-id="56e70-132">Example</span></span>  
 <span data-ttu-id="56e70-133">次の例は、既定値の設定を定義する方法を示しています。`namedCache`エントリを、`namedCaches`メモリ キャッシュのコレクション。</span><span class="sxs-lookup"><span data-stu-id="56e70-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="56e70-134">参照</span><span class="sxs-lookup"><span data-stu-id="56e70-134">See Also</span></span>  
 [<span data-ttu-id="56e70-135">\<namedCaches > 要素 (キャッシュの設定)</span><span class="sxs-lookup"><span data-stu-id="56e70-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
