---
title: "&lt;defaultHttpCachePolicy&gt;要素 (ネットワーク設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 048d9a373c77e530bd352b3caa0e122b3833a5c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a><span data-ttu-id="848fc-102">&lt;defaultHttpCachePolicy&gt;要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="848fc-102">&lt;defaultHttpCachePolicy&gt; Element (Network Settings)</span></span>
<span data-ttu-id="848fc-103">かどうか HTTP キャッシュがアクティブであり、既定のキャッシュ ポリシーの説明について説明します。</span><span class="sxs-lookup"><span data-stu-id="848fc-103">Describes whether HTTP caching is active and describes the default caching policy.</span></span>  
  
 <span data-ttu-id="848fc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="848fc-104">\<configuration></span></span>  
<span data-ttu-id="848fc-105">\<system.net ></span><span class="sxs-lookup"><span data-stu-id="848fc-105">\<system.net></span></span>  
<span data-ttu-id="848fc-106">\<requestCaching ></span><span class="sxs-lookup"><span data-stu-id="848fc-106">\<requestCaching></span></span>  
<span data-ttu-id="848fc-107">\<defaultHttpCachePolicy ></span><span class="sxs-lookup"><span data-stu-id="848fc-107">\<defaultHttpCachePolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="848fc-108">構文</span><span class="sxs-lookup"><span data-stu-id="848fc-108">Syntax</span></span>  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="848fc-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="848fc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="848fc-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="848fc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="848fc-111">属性</span><span class="sxs-lookup"><span data-stu-id="848fc-111">Attributes</span></span>  
  
|<span data-ttu-id="848fc-112">属性</span><span class="sxs-lookup"><span data-stu-id="848fc-112">Attribute</span></span>|<span data-ttu-id="848fc-113">説明</span><span class="sxs-lookup"><span data-stu-id="848fc-113">Description</span></span>|  
|---------------|-----------------|  
|`maximumAge`|<span data-ttu-id="848fc-114">期限切れとしてキャッシュされたオブジェクトがマークされるまで、最大の時間間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="848fc-114">Specifies the maximum time interval before a cached object is marked as expired.</span></span>|  
|`maximumStale`|<span data-ttu-id="848fc-115">期限切れとしてキャッシュされたオブジェクトがマークされるまでの鮮度の計算時間を経過時間の最大値を指定します。</span><span class="sxs-lookup"><span data-stu-id="848fc-115">Specifies the maximum time past the computed freshness time before a cached object is marked as expired.</span></span>|  
|`minimumFresh`|<span data-ttu-id="848fc-116">最新と見なされるには、キャッシュされたオブジェクトの最短時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="848fc-116">Specifies the minimum time for a cached object to be considered fresh.</span></span>|  
|`policyLevel`|<span data-ttu-id="848fc-117">キャッシュ ポリシーが自動かどうかや、キャッシュをバイパスするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="848fc-117">Specifies whether the caching policy is automatic, or whether the cache is bypassed.</span></span> <span data-ttu-id="848fc-118">既定値は `BypassCache` です。</span><span class="sxs-lookup"><span data-stu-id="848fc-118">The default value is `BypassCache`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="848fc-119">子要素</span><span class="sxs-lookup"><span data-stu-id="848fc-119">Child Elements</span></span>  
 <span data-ttu-id="848fc-120">なし</span><span class="sxs-lookup"><span data-stu-id="848fc-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="848fc-121">親要素</span><span class="sxs-lookup"><span data-stu-id="848fc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="848fc-122">要素</span><span class="sxs-lookup"><span data-stu-id="848fc-122">Element</span></span>|<span data-ttu-id="848fc-123">説明</span><span class="sxs-lookup"><span data-stu-id="848fc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="848fc-124">requestCaching</span><span class="sxs-lookup"><span data-stu-id="848fc-124">requestCaching</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|<span data-ttu-id="848fc-125">ネットワーク要求のキャッシュ メカニズムを制御します。</span><span class="sxs-lookup"><span data-stu-id="848fc-125">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="848fc-126">コメント</span><span class="sxs-lookup"><span data-stu-id="848fc-126">Remarks</span></span>  
 <span data-ttu-id="848fc-127">値、`policyLevel`属性があるか、`BypassCache`または`Default`です。</span><span class="sxs-lookup"><span data-stu-id="848fc-127">The value for the `policyLevel` attribute is either `BypassCache` or `Default`.</span></span>  
  
 <span data-ttu-id="848fc-128">値を`maximumAge`、 `maximumStale`、および`minimumFresh`要素の形式のいずれか、明示的な時間間隔は、 *d*.*hh*:*mm*:*ss* (日、時間、分、および秒) または定数`minValue`または`maxValue` をクリックします。</span><span class="sxs-lookup"><span data-stu-id="848fc-128">Values for the `maximumAge`, `maximumStale`, and `minimumFresh` elements are either an explicit time interval with a format of *d*.*hh*:*mm*:*ss* (days, hours, minutes, and seconds), or the constants `minValue` or `maxValue`, as appropriate.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="848fc-129">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="848fc-129">Configuration Files</span></span>  
 <span data-ttu-id="848fc-130">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="848fc-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="848fc-131">例</span><span class="sxs-lookup"><span data-stu-id="848fc-131">Example</span></span>  
 <span data-ttu-id="848fc-132">次の例では、6 時間、2 日間の最大有効期間の時間と 4 時間の最大古い時間の最小の新しい時間を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="848fc-132">The following example shows how to specify a minimum fresh time of six hours, a maximum age time of two days, and a maximum stale time of four hours.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="848fc-133">参照</span><span class="sxs-lookup"><span data-stu-id="848fc-133">See Also</span></span>  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [<span data-ttu-id="848fc-134">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="848fc-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
