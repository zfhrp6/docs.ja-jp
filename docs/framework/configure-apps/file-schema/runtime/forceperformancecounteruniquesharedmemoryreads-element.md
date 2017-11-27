---
title: "&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c90799ed2db061e8f42cde79804789eb8d2da0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a><span data-ttu-id="ffc88-102">&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt;要素</span><span class="sxs-lookup"><span data-stu-id="ffc88-102">&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; Element</span></span>
<span data-ttu-id="ffc88-103">PerfCounter.dll が、.NET Framework バージョン 1.1 のアプリケーションの CategoryOptions レジストリ設定を使用してするかどうかを指定して、カテゴリ別の共有メモリとグローバル メモリのどちらからパフォーマンス カウンター データを読み込むかを決定します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="ffc88-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ffc88-104">\<configuration></span></span>  
<span data-ttu-id="ffc88-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="ffc88-105">\<runtime></span></span>  
<span data-ttu-id="ffc88-106">\<forcePerformanceCounterUniqueSharedMemoryReads ></span><span class="sxs-lookup"><span data-stu-id="ffc88-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffc88-107">構文</span><span class="sxs-lookup"><span data-stu-id="ffc88-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ffc88-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ffc88-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ffc88-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ffc88-110">属性</span><span class="sxs-lookup"><span data-stu-id="ffc88-110">Attributes</span></span>  
  
|<span data-ttu-id="ffc88-111">属性</span><span class="sxs-lookup"><span data-stu-id="ffc88-111">Attribute</span></span>|<span data-ttu-id="ffc88-112">説明</span><span class="sxs-lookup"><span data-stu-id="ffc88-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ffc88-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ffc88-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ffc88-114">PerfCounter.dll がカテゴリ別の共有メモリまたは使用するグローバル メモリからパフォーマンス カウンター データを読み込むかどうかを決定する CategoryOptions レジストリ設定を使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ffc88-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="ffc88-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ffc88-116">値</span><span class="sxs-lookup"><span data-stu-id="ffc88-116">Value</span></span>|<span data-ttu-id="ffc88-117">説明</span><span class="sxs-lookup"><span data-stu-id="ffc88-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ffc88-118">PerfCounter.dll が、CategoryOptions を使用しないレジストリ設定ではこれが既定値です。</span><span class="sxs-lookup"><span data-stu-id="ffc88-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="ffc88-119">PerfCounter.dll は CategoryOptions レジストリ設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ffc88-120">子要素</span><span class="sxs-lookup"><span data-stu-id="ffc88-120">Child Elements</span></span>  
 <span data-ttu-id="ffc88-121">なし。</span><span class="sxs-lookup"><span data-stu-id="ffc88-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ffc88-122">親要素</span><span class="sxs-lookup"><span data-stu-id="ffc88-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ffc88-123">要素</span><span class="sxs-lookup"><span data-stu-id="ffc88-123">Element</span></span>|<span data-ttu-id="ffc88-124">説明</span><span class="sxs-lookup"><span data-stu-id="ffc88-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ffc88-125">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ffc88-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ffc88-126">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ffc88-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ffc88-127">コメント</span><span class="sxs-lookup"><span data-stu-id="ffc88-127">Remarks</span></span>  
 <span data-ttu-id="ffc88-128">前に .NET Framework のバージョンでは、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、読み込まれた PerfCounter.dll のバージョンが、プロセスに読み込まれたランタイムに対応します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-128">In versions of the .NET Framework before the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="ffc88-129">コンピューターが両方の .NET Framework version 1.1 を持っているかどうか、[!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)]インストールされている、.NET Framework 1.1 アプリケーションは PerfCounter.dll の .NET Framework 1.1 バージョンを読み込むとします。</span><span class="sxs-lookup"><span data-stu-id="ffc88-129">If a computer had both the .NET Framework version 1.1 and the [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="ffc88-130">以降で、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]PerfCounter.dll の最新のインストールされているバージョンが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="ffc88-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="ffc88-131">つまり、.NET Framework 1.1 アプリケーションが読み込むこと、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]バージョン PerfCounter.dll の場合、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]コンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="ffc88-131">This means that a .NET Framework 1.1 application will load the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] version of PerfCounter.dll if the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] is installed on the computer.</span></span>  
  
 <span data-ttu-id="ffc88-132">以降で、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]PerfCounter.dll がカテゴリ別の共有メモリまたはグローバル共有メモリから読み取る必要があります、かどうかを確認するには、各プロバイダーの CategoryOptions レジストリ エントリをチェックするパフォーマンス カウンターを使用するときにします。</span><span class="sxs-lookup"><span data-stu-id="ffc88-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="ffc88-133">.NET Framework 1.1 PerfCounter.dll 読み取れないレジストリのエントリがカテゴリ別の共有メモリです。 認識されません。これは、常に、グローバル共有メモリから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="ffc88-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="ffc88-134">旧バージョンとの互換性のため、 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] .NET Framework 1.1 アプリケーションで実行されるときに PerfCounter.dll が CategoryOptions レジストリ エントリを確認しません。</span><span class="sxs-lookup"><span data-stu-id="ffc88-134">For backward compatibility, the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="ffc88-135">.NET Framework 1.1 PerfCounter.dll と同じように、グローバル共有メモリは単に使用します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="ffc88-136">ただし、指示することで、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]を有効にすると、レジストリ設定を確認する PerfCounter.dll、`<forcePerformanceCounterUniqueSharedMemoryReads>`要素。</span><span class="sxs-lookup"><span data-stu-id="ffc88-136">However, you can instruct the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ffc88-137">有効にすると、`<forcePerformanceCounterUniqueSharedMemoryReads>`要素とは限りませんが、カテゴリ別の共有メモリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ffc88-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="ffc88-138">設定が有効な`true`CategoryOptions レジストリ設定を参照する PerfCounter.dll でのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="ffc88-139">CategoryOptions の既定の設定がカテゴリ別の共有メモリを使用するにはただし、グローバル共有メモリを使用することを示すために CategoryOptions を変更できます。</span><span class="sxs-lookup"><span data-stu-id="ffc88-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="ffc88-140">CategoryOptions 設定を格納するレジストリ キーは hkey_local_machine \system\currentcontrolset\services\\< categoryName\>\Performance です。</span><span class="sxs-lookup"><span data-stu-id="ffc88-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="ffc88-141">既定では、CategoryOptions は 3 に設定、PerfCounter.dll に指示するカテゴリに固有の共有メモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="ffc88-142">CategoryOptions が 0 に設定されている場合、PerfCounter.dll はグローバル共有メモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="ffc88-143">作成中のインスタンスの名前が再利用されるインスタンスと同一である場合にのみ、インスタンス データを再利用されます。</span><span class="sxs-lookup"><span data-stu-id="ffc88-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="ffc88-144">すべてのバージョンは、カテゴリに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ffc88-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="ffc88-145">CategoryOptions が 1 に設定されている場合、グローバル共有メモリを使用するが、カテゴリ名が再利用される、カテゴリと同じ長さである場合は、インスタンス データを再利用されることができます。</span><span class="sxs-lookup"><span data-stu-id="ffc88-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="ffc88-146">0 と 1 の設定は、メモリ リークとパフォーマンス カウンターのメモリの不足する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ffc88-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffc88-147">例</span><span class="sxs-lookup"><span data-stu-id="ffc88-147">Example</span></span>  
 <span data-ttu-id="ffc88-148">次の例では、PerfCounter.dll がカテゴリ別の共有メモリを使用する必要があるかどうかを決定する CategoryOptions レジストリ エントリを参照することを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ffc88-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffc88-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffc88-149">See Also</span></span>  
 [<span data-ttu-id="ffc88-150">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ffc88-150">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="ffc88-151">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="ffc88-151">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
