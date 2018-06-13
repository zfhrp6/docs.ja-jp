---
title: '&lt;performanceCounters&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cb4af08095c14c0c748a79f53104d8454d3dcd47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754159"
---
# <a name="ltperformancecountersgt-element"></a><span data-ttu-id="b614e-102">&lt;performanceCounters&gt;要素</span><span class="sxs-lookup"><span data-stu-id="b614e-102">&lt;performanceCounters&gt; Element</span></span>
<span data-ttu-id="b614e-103">パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="b614e-103">Specifies the size of the global memory shared by performance counters.</span></span>  
  
 <span data-ttu-id="b614e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b614e-104">\<configuration></span></span>  
<span data-ttu-id="b614e-105">\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="b614e-105">\<system.diagnostics></span></span>  
<span data-ttu-id="b614e-106">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="b614e-106">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b614e-107">構文</span><span class="sxs-lookup"><span data-stu-id="b614e-107">Syntax</span></span>  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b614e-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b614e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b614e-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b614e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b614e-110">属性</span><span class="sxs-lookup"><span data-stu-id="b614e-110">Attributes</span></span>  
  
|<span data-ttu-id="b614e-111">属性</span><span class="sxs-lookup"><span data-stu-id="b614e-111">Attribute</span></span>|<span data-ttu-id="b614e-112">説明</span><span class="sxs-lookup"><span data-stu-id="b614e-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b614e-113">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="b614e-113">filemappingsize</span></span>|<span data-ttu-id="b614e-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="b614e-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b614e-115">パフォーマンス カウンターが共有するグローバル メモリのバイト単位のサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="b614e-115">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="b614e-116">既定値は 524288 です。</span><span class="sxs-lookup"><span data-stu-id="b614e-116">The default is 524288.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b614e-117">子要素</span><span class="sxs-lookup"><span data-stu-id="b614e-117">Child Elements</span></span>  
 <span data-ttu-id="b614e-118">なし。</span><span class="sxs-lookup"><span data-stu-id="b614e-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b614e-119">親要素</span><span class="sxs-lookup"><span data-stu-id="b614e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b614e-120">要素</span><span class="sxs-lookup"><span data-stu-id="b614e-120">Element</span></span>|<span data-ttu-id="b614e-121">説明</span><span class="sxs-lookup"><span data-stu-id="b614e-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="b614e-122">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="b614e-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b614e-123">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="b614e-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b614e-124">コメント</span><span class="sxs-lookup"><span data-stu-id="b614e-124">Remarks</span></span>  
 <span data-ttu-id="b614e-125">パフォーマンス カウンターでは、メモリ マップト ファイルまたは共有メモリを使用して、パフォーマンス データを公開します。</span><span class="sxs-lookup"><span data-stu-id="b614e-125">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="b614e-126">共有メモリのサイズは、一度に使用できるインスタンスの数を決定します。</span><span class="sxs-lookup"><span data-stu-id="b614e-126">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="b614e-127">共有メモリの 2 種類があります。 グローバル共有メモリと別の共有メモリです。</span><span class="sxs-lookup"><span data-stu-id="b614e-127">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="b614e-128">グローバル共有メモリは、.NET Framework バージョン 1.0 または 1.1 でインストールされているすべてのパフォーマンス カウンターのカテゴリを使用します。</span><span class="sxs-lookup"><span data-stu-id="b614e-128">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="b614e-129">.NET Framework version 2.0 にインストールされているパフォーマンス カウンター カテゴリは、独自のメモリを持つ各パフォーマンス カウンター カテゴリ別の共有メモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="b614e-129">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>  
  
 <span data-ttu-id="b614e-130">グローバル共有メモリのサイズは、構成ファイルでのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="b614e-130">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="b614e-131">既定のサイズは 524, 288 バイト、最大サイズは 33,554, 432 (バイト単位)、最小サイズは 32,768 バイトです。</span><span class="sxs-lookup"><span data-stu-id="b614e-131">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="b614e-132">グローバル共有メモリは、すべてのプロセスとカテゴリが共有しているために、最初の作成者は、サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="b614e-132">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="b614e-133">アプリケーション構成ファイルのサイズを定義する場合、そのサイズは場合にのみ使用アプリケーションが実行するパフォーマンス カウンターの原因となる最初のアプリケーション。</span><span class="sxs-lookup"><span data-stu-id="b614e-133">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="b614e-134">したがって、正しい場所を指定、`filemappingsize`値は、Machine.config ファイルです。</span><span class="sxs-lookup"><span data-stu-id="b614e-134">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="b614e-135">個々 のパフォーマンス カウンターによって、最終的に多数の異なる名前を持つパフォーマンス カウンター インスタンスが作成される場合、グローバル共有メモリがなくなったグローバル共有メモリ内のメモリを解放できません。</span><span class="sxs-lookup"><span data-stu-id="b614e-135">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>  
  
 <span data-ttu-id="b614e-136">別の共有メモリのサイズをレジストリの DWORD FileMappingSize 値キー hkey_local_machine \system\currentcontrolset\services\\*\<カテゴリ名 >* \Performance が参照されています。最初に、構成ファイル内のグローバル共有メモリに指定された値に続きます。</span><span class="sxs-lookup"><span data-stu-id="b614e-136">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="b614e-137">FileMappingSize 値が存在しないかどうかは、別の共有メモリのサイズが 4 分の 1 に設定されている (1/4)、構成ファイルのグローバル設定。</span><span class="sxs-lookup"><span data-stu-id="b614e-137">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b614e-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="b614e-138">See Also</span></span>  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
