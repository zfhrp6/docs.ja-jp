---
title: "&lt;gcConcurrent&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c7ab16546ae85d1161f9e1323d74f17253edb7e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltgcconcurrentgt-element"></a><span data-ttu-id="ffd03-102">&lt;gcConcurrent&gt;要素</span><span class="sxs-lookup"><span data-stu-id="ffd03-102">&lt;gcConcurrent&gt; Element</span></span>
<span data-ttu-id="ffd03-103">共通言語ランタイムがガベージ コレクションを別のスレッドで実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ffd03-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>  
  
 <span data-ttu-id="ffd03-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ffd03-104">\<configuration></span></span>  
<span data-ttu-id="ffd03-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="ffd03-105">\<runtime></span></span>  
<span data-ttu-id="ffd03-106">\<gcConcurrent ></span><span class="sxs-lookup"><span data-stu-id="ffd03-106">\<gcConcurrent></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffd03-107">構文</span><span class="sxs-lookup"><span data-stu-id="ffd03-107">Syntax</span></span>  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffd03-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ffd03-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ffd03-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ffd03-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffd03-110">属性</span><span class="sxs-lookup"><span data-stu-id="ffd03-110">Attributes</span></span>  
  
|<span data-ttu-id="ffd03-111">属性</span><span class="sxs-lookup"><span data-stu-id="ffd03-111">Attribute</span></span>|<span data-ttu-id="ffd03-112">説明</span><span class="sxs-lookup"><span data-stu-id="ffd03-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ffd03-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ffd03-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ffd03-114">ランタイムがガベージ コレクションを並列に実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ffd03-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ffd03-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="ffd03-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ffd03-116">値</span><span class="sxs-lookup"><span data-stu-id="ffd03-116">Value</span></span>|<span data-ttu-id="ffd03-117">説明</span><span class="sxs-lookup"><span data-stu-id="ffd03-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ffd03-118">ガベージ コレクションを並列に実行しません。</span><span class="sxs-lookup"><span data-stu-id="ffd03-118">Does not run garbage collection concurrently.</span></span>|  
|`true`|<span data-ttu-id="ffd03-119">ガベージ コレクションを並列に実行します。</span><span class="sxs-lookup"><span data-stu-id="ffd03-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="ffd03-120">既定値です。</span><span class="sxs-lookup"><span data-stu-id="ffd03-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ffd03-121">子要素</span><span class="sxs-lookup"><span data-stu-id="ffd03-121">Child Elements</span></span>  
 <span data-ttu-id="ffd03-122">なし。</span><span class="sxs-lookup"><span data-stu-id="ffd03-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffd03-123">親要素</span><span class="sxs-lookup"><span data-stu-id="ffd03-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ffd03-124">要素</span><span class="sxs-lookup"><span data-stu-id="ffd03-124">Element</span></span>|<span data-ttu-id="ffd03-125">説明</span><span class="sxs-lookup"><span data-stu-id="ffd03-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ffd03-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ffd03-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ffd03-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ffd03-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffd03-128">コメント</span><span class="sxs-lookup"><span data-stu-id="ffd03-128">Remarks</span></span>  
 <span data-ttu-id="ffd03-129">.NET Framework 4 より前の場合、ワークステーション ガベージ コレクションは、同時実行ガベージ コレクションをサポートしており、別個のスレッドでバックグラウンドでガベージ コレクションを実行していました。</span><span class="sxs-lookup"><span data-stu-id="ffd03-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="ffd03-130">.NET Framework 4 では同時実行ガベージ コレクションはバックグラウンド GC に置き換えられており、これも別個のスレッドでバックグラウンドでガベージ コレクションを実行していました。</span><span class="sxs-lookup"><span data-stu-id="ffd03-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="ffd03-131">.NET Framework 4.5 以降では、バックグラウンド コレクションをサーバー ガベージ コレクションで使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ffd03-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="ffd03-132">`<gcConcurrent>` 要素は、ランタイムが同時実行ガベージ コレクションを実行するかバックグラウンド ガベージ コレクションを実行するか (使用可能な場合)、またはフォアグラウンドでガベージ コレクションを実行するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="ffd03-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it is available, or whether it performs garbage collection in the foreground.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ffd03-133">.NET Framework 4 以降では、同時実行ガベージ コレクションはバックグラウンド ガベージ コレクションに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="ffd03-133">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="ffd03-134">条項*同時*と*バック グラウンド*.NET Framework のドキュメントで同じ意味で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ffd03-134">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="ffd03-135">バックグラウンド ガベージ コレクションを無効にするには、この記事説明されているように `<gcConcurrent>` 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffd03-135">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>  
  
 <span data-ttu-id="ffd03-136">既定では、ランタイムは同時実行ガベージ コレクションまたはバックグラウンド ガベージ コレクションを使用します。これは待機時間について最適化されています。</span><span class="sxs-lookup"><span data-stu-id="ffd03-136">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="ffd03-137">アプリケーションでユーザーとのやり取りが多い場合は、同時実行ガベージ コレクションを有効にして、ガベージ コレクションを実行するためのアプリケーションの停止時間を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="ffd03-137">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="ffd03-138">`<gcConcurrent>` 要素の `enabled` 属性を `false` に設定すると、ランタイムは非同時実行ガベージ コレクションを使用します。これはスループットについて最適化されています。</span><span class="sxs-lookup"><span data-stu-id="ffd03-138">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="ffd03-139">次の構成ファイルはバック グラウンド ガベージ コレクションを無効にします。</span><span class="sxs-lookup"><span data-stu-id="ffd03-139">The following configuration file disables background garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ffd03-140">マシン構成ファイルに `<gcConcurrentSetting>` 設定が存在する場合、すべての .NET Framework アプリケーションの既定値を定義します。</span><span class="sxs-lookup"><span data-stu-id="ffd03-140">If there is a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="ffd03-141">マシン構成ファイルの設定は、アプリケーション構成ファイルの設定を上書きします。</span><span class="sxs-lookup"><span data-stu-id="ffd03-141">The machine configuration file setting overrides the application configuration file setting.</span></span>  
  
 <span data-ttu-id="ffd03-142">詳細とバック グラウンド ガベージ コレクションの同時実行については、「同時実行ガベージ コレクション」セクションを参照して、[ガベージ コレクションの基礎](../../../../../docs/standard/garbage-collection/fundamentals.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="ffd03-142">For more information on concurrent and background garbage collection, see the "Concurrent garbage collection" section in the [Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffd03-143">例</span><span class="sxs-lookup"><span data-stu-id="ffd03-143">Example</span></span>  
 <span data-ttu-id="ffd03-144">同時実行ガベージ コレクションを有効にする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="ffd03-144">The following example enables concurrent garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffd03-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffd03-145">See Also</span></span>  
 [<span data-ttu-id="ffd03-146">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ffd03-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ffd03-147">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="ffd03-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ffd03-148">ガベージ コレクションの基礎</span><span class="sxs-lookup"><span data-stu-id="ffd03-148">Fundamentals of Garbage Collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md)
