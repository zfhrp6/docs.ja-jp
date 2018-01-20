---
title: "&lt;performanceCounter&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: c50bf9e882ade86e70db217a75fef2a893c45572
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltperformancecountergt-element-network-settings"></a><span data-ttu-id="92585-102">&lt;performanceCounter&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="92585-102">&lt;performanceCounter&gt; Element (Network Settings)</span></span>
<span data-ttu-id="92585-103">有効またはネットワークのパフォーマンス カウンターを無効にします。</span><span class="sxs-lookup"><span data-stu-id="92585-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="92585-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="92585-104">\<configuration></span></span>  
<span data-ttu-id="92585-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="92585-105">\<system.net></span></span>  
<span data-ttu-id="92585-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="92585-106">\<settings></span></span>  
<span data-ttu-id="92585-107">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="92585-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92585-108">構文</span><span class="sxs-lookup"><span data-stu-id="92585-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92585-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="92585-109">Attributes and Elements</span></span>  
 <span data-ttu-id="92585-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="92585-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92585-111">属性</span><span class="sxs-lookup"><span data-stu-id="92585-111">Attributes</span></span>  
  
|<span data-ttu-id="92585-112">属性</span><span class="sxs-lookup"><span data-stu-id="92585-112">Attribute</span></span>|<span data-ttu-id="92585-113">説明</span><span class="sxs-lookup"><span data-stu-id="92585-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="92585-114">ネットワークのパフォーマンス カウンターが有効になっているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="92585-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="92585-115">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="92585-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92585-116">子要素</span><span class="sxs-lookup"><span data-stu-id="92585-116">Child Elements</span></span>  
 <span data-ttu-id="92585-117">なし。</span><span class="sxs-lookup"><span data-stu-id="92585-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92585-118">親要素</span><span class="sxs-lookup"><span data-stu-id="92585-118">Parent Elements</span></span>  
  
|<span data-ttu-id="92585-119">要素</span><span class="sxs-lookup"><span data-stu-id="92585-119">Element</span></span>|<span data-ttu-id="92585-120">説明</span><span class="sxs-lookup"><span data-stu-id="92585-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92585-121">settings</span><span class="sxs-lookup"><span data-stu-id="92585-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="92585-122"><xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。</span><span class="sxs-lookup"><span data-stu-id="92585-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92585-123">コメント</span><span class="sxs-lookup"><span data-stu-id="92585-123">Remarks</span></span>  
 <span data-ttu-id="92585-124">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="92585-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="92585-125">ネットワーク パフォーマンス カウンターは、使用される構成ファイルで有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="92585-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="92585-126">すべてのネットワーク パフォーマンス カウンターは、構成ファイル内の 1 つの設定で有効または無効にされます。</span><span class="sxs-lookup"><span data-stu-id="92585-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="92585-127">ネットワーク パフォーマンス カウンターを個別に有効または無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="92585-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="92585-128">特定のネットワークのパフォーマンス カウンターの詳細については、次を参照してください。[ネットワーク パフォーマンス カウンター](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)です。</span><span class="sxs-lookup"><span data-stu-id="92585-128">For more information on the specific networking performance counters, see [Networking Performance Counters](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span></span>  
  
 <span data-ttu-id="92585-129">既定値は、そのネットワークのパフォーマンス カウンターが無効です。</span><span class="sxs-lookup"><span data-stu-id="92585-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="92585-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、**有効になっている**該当する構成ファイルからの属性です。</span><span class="sxs-lookup"><span data-stu-id="92585-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92585-131">例</span><span class="sxs-lookup"><span data-stu-id="92585-131">Example</span></span>  
 <span data-ttu-id="92585-132">次の例は、構成する方法を示します、<xref:System.Net>および関連名前空間をネットワークのパフォーマンス カウンターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="92585-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92585-133">参照</span><span class="sxs-lookup"><span data-stu-id="92585-133">See Also</span></span>  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="92585-134">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="92585-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="92585-135">ネットワーク パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="92585-135">Networking Performance Counters</span></span>](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
