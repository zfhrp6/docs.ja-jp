---
title: "&lt;appDomainResourceMonitoring&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- appDomainResourceMonitoring element
- <appDomainResourceMonitoring> element
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58caa7458d96ca7bb9088b607a83b2d6be667cae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltappdomainresourcemonitoringgt-element"></a><span data-ttu-id="3b1e2-102">&lt;appDomainResourceMonitoring&gt;要素</span><span class="sxs-lookup"><span data-stu-id="3b1e2-102">&lt;appDomainResourceMonitoring&gt; Element</span></span>
<span data-ttu-id="3b1e2-103">プロセスのライフサイクルにおいて、プロセスのすべてのアプリケーション ドメインの統計を収集するようにランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-103">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="3b1e2-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3b1e2-104">\<configuration></span></span>  
<span data-ttu-id="3b1e2-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="3b1e2-105">\<runtime></span></span>  
<span data-ttu-id="3b1e2-106">\<appDomainResourceMonitoring ></span><span class="sxs-lookup"><span data-stu-id="3b1e2-106">\<appDomainResourceMonitoring></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b1e2-107">構文</span><span class="sxs-lookup"><span data-stu-id="3b1e2-107">Syntax</span></span>  
  
```xml  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b1e2-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3b1e2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3b1e2-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b1e2-110">属性</span><span class="sxs-lookup"><span data-stu-id="3b1e2-110">Attributes</span></span>  
  
|<span data-ttu-id="3b1e2-111">属性</span><span class="sxs-lookup"><span data-stu-id="3b1e2-111">Attribute</span></span>|<span data-ttu-id="3b1e2-112">説明</span><span class="sxs-lookup"><span data-stu-id="3b1e2-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3b1e2-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b1e2-114">ランタイムがアプリケーション ドメインのリソースの監視に関する統計を収集するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-114">Specifies whether the runtime collects statistics for application domain resource monitoring.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3b1e2-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="3b1e2-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3b1e2-116">値</span><span class="sxs-lookup"><span data-stu-id="3b1e2-116">Value</span></span>|<span data-ttu-id="3b1e2-117">説明</span><span class="sxs-lookup"><span data-stu-id="3b1e2-117">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="3b1e2-118">アプリケーション ドメインのリソース監視の統計情報が収集されます。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-118">Statistics for application domain resource monitoring are collected.</span></span>|  
|`false`|<span data-ttu-id="3b1e2-119">アプリケーション ドメインのリソース監視の統計情報が収集されません。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-119">Statistics for application domain resource monitoring are not collected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b1e2-120">子要素</span><span class="sxs-lookup"><span data-stu-id="3b1e2-120">Child Elements</span></span>  
 <span data-ttu-id="3b1e2-121">なし。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b1e2-122">親要素</span><span class="sxs-lookup"><span data-stu-id="3b1e2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3b1e2-123">要素</span><span class="sxs-lookup"><span data-stu-id="3b1e2-123">Element</span></span>|<span data-ttu-id="3b1e2-124">説明</span><span class="sxs-lookup"><span data-stu-id="3b1e2-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3b1e2-125">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3b1e2-126">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b1e2-127">コメント</span><span class="sxs-lookup"><span data-stu-id="3b1e2-127">Remarks</span></span>  
 <span data-ttu-id="3b1e2-128">ホストしている、管理対象のアプリケーション ドメイン クラスを通じて利用できるがアプリケーション ドメインのリソース監視[ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)インターフェイス、およびイベント トレース for Windows (ETW)。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-128">Application domain resource monitoring is available through the managed application domain class, the hosting [ICLRAppDomainResourceMonitor](../../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) interface, and event tracing for Windows (ETW).</span></span> <span data-ttu-id="3b1e2-129">監視を有効にすると、すべてのアプリケーション ドメイン、プロセスの有効期間のプロセスの統計が収集されます。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-129">When monitoring is enabled, statistics are collected for all application domains in the process for the life of the process.</span></span>  
  
 <span data-ttu-id="3b1e2-130">マネージ コードからの監視を有効にするには、<xref:System.AppDomain.MonitoringIsEnabled%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-130">To enable monitoring from managed code, use the <xref:System.AppDomain.MonitoringIsEnabled%2A> property.</span></span>  
  
 <span data-ttu-id="3b1e2-131">この構成要素はでのみ使用できますが、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]およびそれ以降。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-131">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b1e2-132">例</span><span class="sxs-lookup"><span data-stu-id="3b1e2-132">Example</span></span>  
 <span data-ttu-id="3b1e2-133">次の例では、アプリケーション ドメインのリソース監視を有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3b1e2-133">The following example shows how to enable application domain resource monitoring.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b1e2-134">参照</span><span class="sxs-lookup"><span data-stu-id="3b1e2-134">See Also</span></span>  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="3b1e2-135">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="3b1e2-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="3b1e2-136">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="3b1e2-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
