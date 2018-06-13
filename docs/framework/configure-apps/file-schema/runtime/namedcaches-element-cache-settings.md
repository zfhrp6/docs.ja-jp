---
title: '&lt;namedCaches&gt;要素 (キャッシュの設定)'
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fac50aedbb11eba40482fab71c912f587d85f855
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744656"
---
# <a name="ltnamedcachesgt-element-cache-settings"></a><span data-ttu-id="77dac-102">&lt;namedCaches&gt;要素 (キャッシュの設定)</span><span class="sxs-lookup"><span data-stu-id="77dac-102">&lt;namedCaches&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="77dac-103">名前付きの構成設定のコレクションを指定<xref:System.Runtime.Caching.MemoryCache>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="77dac-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="77dac-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>プロパティは、1 つ以上の構成設定のコレクションを参照`namedCaches`構成ファイルの要素。</span><span class="sxs-lookup"><span data-stu-id="77dac-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="77dac-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="77dac-105">\<configuration></span></span>  
<span data-ttu-id="77dac-106">\< system.runtime.caching ></span><span class="sxs-lookup"><span data-stu-id="77dac-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="77dac-107">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="77dac-107">\<memoryCache></span></span>  
<span data-ttu-id="77dac-108">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="77dac-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77dac-109">構文</span><span class="sxs-lookup"><span data-stu-id="77dac-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="77dac-110">型</span><span class="sxs-lookup"><span data-stu-id="77dac-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77dac-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="77dac-111">Attributes and Elements</span></span>  
 <span data-ttu-id="77dac-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="77dac-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77dac-113">属性</span><span class="sxs-lookup"><span data-stu-id="77dac-113">Attributes</span></span>  
  
|<span data-ttu-id="77dac-114">属性</span><span class="sxs-lookup"><span data-stu-id="77dac-114">Attribute</span></span>|<span data-ttu-id="77dac-115">説明</span><span class="sxs-lookup"><span data-stu-id="77dac-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="77dac-116">メガバイト単位で、最大許容サイズを指定する整数値のインスタンス、<xref:System.Runtime.Caching.MemoryCache>まで拡大できます。</span><span class="sxs-lookup"><span data-stu-id="77dac-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="77dac-117">既定値は 0、つまりのサイズの自動変更のヒューリスティック、<xref:System.Runtime.Caching.MemoryCache>クラスは、既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="77dac-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="77dac-118">キャッシュの名前。</span><span class="sxs-lookup"><span data-stu-id="77dac-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="77dac-119">キャッシュで利用できる物理的にインストールされているコンピューターのメモリの最大パーセンテージを指定する整数 0 ~ 100 の値。</span><span class="sxs-lookup"><span data-stu-id="77dac-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="77dac-120">既定値は 0、つまりのサイズの自動変更のヒューリスティック、<xref:System.Runtime.Caching.MemoryCache>クラスは、既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="77dac-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="77dac-121">時間間隔を示す値。この値を超えると、キャッシュの実装によりキャッシュ インスタンスに設定されている絶対およびパーセントのメモリ制限と現在のメモリ負荷が比較されます。</span><span class="sxs-lookup"><span data-stu-id="77dac-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="77dac-122">この値は"HH:MM:SS"形式で入力します。</span><span class="sxs-lookup"><span data-stu-id="77dac-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77dac-123">子要素</span><span class="sxs-lookup"><span data-stu-id="77dac-123">Child Elements</span></span>  
  
|<span data-ttu-id="77dac-124">要素</span><span class="sxs-lookup"><span data-stu-id="77dac-124">Element</span></span>|<span data-ttu-id="77dac-125">説明</span><span class="sxs-lookup"><span data-stu-id="77dac-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77dac-126">\<add></span><span class="sxs-lookup"><span data-stu-id="77dac-126">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|<span data-ttu-id="77dac-127">名前付きキャッシュを、メモリ キャッシュの `namedCaches` コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="77dac-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="77dac-128">\<clear></span><span class="sxs-lookup"><span data-stu-id="77dac-128">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|<span data-ttu-id="77dac-129">メモリ キャッシュの `namedCaches` コレクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="77dac-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="77dac-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="77dac-130">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|<span data-ttu-id="77dac-131">名前付きキャッシュ エントリを、メモリ キャッシュの `namedCaches` コレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="77dac-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="77dac-132">親要素</span><span class="sxs-lookup"><span data-stu-id="77dac-132">Parent Elements</span></span>  
  
|<span data-ttu-id="77dac-133">要素</span><span class="sxs-lookup"><span data-stu-id="77dac-133">Element</span></span>|<span data-ttu-id="77dac-134">説明</span><span class="sxs-lookup"><span data-stu-id="77dac-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77dac-135">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="77dac-135">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="77dac-136"><xref:System.Runtime.Caching.MemoryCache> クラスに基づくキャッシュを構成するために使用される要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="77dac-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77dac-137">コメント</span><span class="sxs-lookup"><span data-stu-id="77dac-137">Remarks</span></span>  
 <span data-ttu-id="77dac-138">Web.config ファイルのメモリ キャッシュ構成セクションを含めることができます`add`、 `remove`、および`clear`の属性を`namedCaches`コレクション。</span><span class="sxs-lookup"><span data-stu-id="77dac-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="77dac-139">各`namedCaches`によってエントリを一意に識別、`name`属性。</span><span class="sxs-lookup"><span data-stu-id="77dac-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="77dac-140">アプリケーション構成ファイル内の情報を参照することによって、メモリのキャッシュ エントリのインスタンスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="77dac-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="77dac-141">既定では、既定のキャッシュ インスタンスの構成ファイルにエントリがあります。</span><span class="sxs-lookup"><span data-stu-id="77dac-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="77dac-142">既定のキャッシュ インスタンスは、インスタンスから返される、<xref:System.Runtime.Caching.MemoryCache.Default%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="77dac-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="77dac-143">Name 属性を"default"を設定した場合、要素は、既定のメモリ キャッシュ インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="77dac-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77dac-144">例</span><span class="sxs-lookup"><span data-stu-id="77dac-144">Example</span></span>  
 <span data-ttu-id="77dac-145">次の例は、既定のキャッシュ エントリ名に設定して、キャッシュの名前を設定する方法を示しています、`name`属性を"default"です。</span><span class="sxs-lookup"><span data-stu-id="77dac-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="77dac-146">`cacheMemoryLimitMegabytes` 属性および `physicalMemoryPercentage` 属性はゼロに設定されます。</span><span class="sxs-lookup"><span data-stu-id="77dac-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="77dac-147">これらの属性を 0 に設定することを意味のサイズの自動変更のヒューリスティック、<xref:System.Runtime.Caching.MemoryCache>クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="77dac-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="77dac-148">キャッシュの実装では、現在のメモリ負荷を絶対指定とパーセンテージに基づくメモリ制限の 2 分ごとと比較します。</span><span class="sxs-lookup"><span data-stu-id="77dac-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="77dac-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="77dac-149">See Also</span></span>  
 [<span data-ttu-id="77dac-150">\<memoryCache > 要素 (キャッシュの設定)</span><span class="sxs-lookup"><span data-stu-id="77dac-150">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
