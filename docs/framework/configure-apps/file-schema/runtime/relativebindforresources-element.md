---
title: '&lt;relativeBindForResources&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ae5d1ca6403d84c9828dcf9550e9fbf40b28e1b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltrelativebindforresourcesgt-element"></a><span data-ttu-id="3b07a-102">&lt;relativeBindForResources&gt;要素</span><span class="sxs-lookup"><span data-stu-id="3b07a-102">&lt;relativeBindForResources&gt; Element</span></span>
<span data-ttu-id="3b07a-103">サテライト アセンブリのプローブを最適化します。</span><span class="sxs-lookup"><span data-stu-id="3b07a-103">Optimizes the probe for satellite assemblies.</span></span>  
  
 <span data-ttu-id="3b07a-104">\<configuration > 要素</span><span class="sxs-lookup"><span data-stu-id="3b07a-104">\<configuration> Element</span></span>  
<span data-ttu-id="3b07a-105">\<ランタイム > 要素</span><span class="sxs-lookup"><span data-stu-id="3b07a-105">\<runtime> Element</span></span>  
<span data-ttu-id="3b07a-106">\<relativeBindForResources > 要素</span><span class="sxs-lookup"><span data-stu-id="3b07a-106">\<relativeBindForResources> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b07a-107">構文</span><span class="sxs-lookup"><span data-stu-id="3b07a-107">Syntax</span></span>  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b07a-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="3b07a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3b07a-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b07a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b07a-110">属性</span><span class="sxs-lookup"><span data-stu-id="3b07a-110">Attributes</span></span>  
  
|<span data-ttu-id="3b07a-111">属性</span><span class="sxs-lookup"><span data-stu-id="3b07a-111">Attribute</span></span>|<span data-ttu-id="3b07a-112">説明</span><span class="sxs-lookup"><span data-stu-id="3b07a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3b07a-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="3b07a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b07a-114">共通言語ランタイムが、サテライト アセンブリのプローブを最適化するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="3b07a-114">Specifies whether the common language runtime optimizes the probe for satellite assemblies.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3b07a-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="3b07a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3b07a-116">値</span><span class="sxs-lookup"><span data-stu-id="3b07a-116">Value</span></span>|<span data-ttu-id="3b07a-117">説明</span><span class="sxs-lookup"><span data-stu-id="3b07a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3b07a-118">ランタイムでは、サテライト アセンブリのプローブは最適化されません。</span><span class="sxs-lookup"><span data-stu-id="3b07a-118">The runtime does not optimize the probe for satellite assemblies.</span></span> <span data-ttu-id="3b07a-119">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="3b07a-119">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="3b07a-120">ランタイムは、サテライト アセンブリのプローブを最適化します。</span><span class="sxs-lookup"><span data-stu-id="3b07a-120">The runtime optimizes the probe for satellite assemblies.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b07a-121">子要素</span><span class="sxs-lookup"><span data-stu-id="3b07a-121">Child Elements</span></span>  
 <span data-ttu-id="3b07a-122">なし。</span><span class="sxs-lookup"><span data-stu-id="3b07a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b07a-123">親要素</span><span class="sxs-lookup"><span data-stu-id="3b07a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3b07a-124">要素</span><span class="sxs-lookup"><span data-stu-id="3b07a-124">Element</span></span>|<span data-ttu-id="3b07a-125">説明</span><span class="sxs-lookup"><span data-stu-id="3b07a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3b07a-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="3b07a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3b07a-127">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="3b07a-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b07a-128">コメント</span><span class="sxs-lookup"><span data-stu-id="3b07a-128">Remarks</span></span>  
 <span data-ttu-id="3b07a-129">一般に、リソース マネージャー プローブのリソースについては、『 の説明に従って、[パッケージと展開のリソース](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="3b07a-129">In general, Resource Manager probes for resources, as documented in the [Packaging and Deploying Resources](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.</span></span> <span data-ttu-id="3b07a-130">つまり、リソース マネージャーは、特定のローカライズされたバージョンのリソースにプローブ、ときにその可能性があります、グローバル アセンブリ キャッシュ ファイルの場所、サテライト アセンブリのファイルの場所はアプリケーションのコード ベース、クエリ Windows インストーラーにカルチャ固有のフォルダーおよびを発生させる、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベント。</span><span class="sxs-lookup"><span data-stu-id="3b07a-130">This means that when Resource Manager probes for a particular localized version of a resource, it may look in the global assembly cache, look in a culture-specific folder in the application's code base, query Windows Installer for satellite assemblies, and raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span> <span data-ttu-id="3b07a-131">`<relativeBindForResources>`要素は、リソース マネージャーがサテライト アセンブリをプローブする方法を最適化します。</span><span class="sxs-lookup"><span data-stu-id="3b07a-131">The `<relativeBindForResources>` element optimizes the way in which Resource Manager probes for satellite assemblies.</span></span> <span data-ttu-id="3b07a-132">これにより、次の条件下でリソースの調査時にパフォーマンスが向上することができます。</span><span class="sxs-lookup"><span data-stu-id="3b07a-132">It can improve performance when probing for resources under the following conditions:</span></span>  
  
-   <span data-ttu-id="3b07a-133">サテライト アセンブリを展開する際、コードのアセンブリと同じ場所にします。</span><span class="sxs-lookup"><span data-stu-id="3b07a-133">When the satellite assembly is deployed in the same location as the code assembly.</span></span> <span data-ttu-id="3b07a-134">つまり、コードのアセンブリがグローバル アセンブリ キャッシュにインストールされている場合、サテライト アセンブリもインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b07a-134">In other words, if the code assembly is installed in the global assembly cache, the satellite assemblies must also be installed there.</span></span> <span data-ttu-id="3b07a-135">コードのアセンブリがアプリケーションのコード ベースでインストールされている場合、サテライト アセンブリは、コード ベースのカルチャに固有のフォルダーにもインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b07a-135">If the code assembly is installed in the application's code base, the satellite assemblies must also be installed in a culture-specific folder in the code base.</span></span>  
  
-   <span data-ttu-id="3b07a-136">Windows インストーラーが実行されていないまたはほとんど使用されないがサテライト アセンブリのオンデマンドでインストールします。</span><span class="sxs-lookup"><span data-stu-id="3b07a-136">When Windows Installer is not used or is used only rarely for on-demand installation of satellite assemblies.</span></span>  
  
-   <span data-ttu-id="3b07a-137">アプリケーション コードが処理しない場合、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベント。</span><span class="sxs-lookup"><span data-stu-id="3b07a-137">When application code does not handle the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
 <span data-ttu-id="3b07a-138">設定、`enabled`の属性、`<relativeBindForResources>`要素を`true`サテライト アセンブリのリソース マネージャーのプローブを次のように最適化されます。</span><span class="sxs-lookup"><span data-stu-id="3b07a-138">Setting the `enabled` attribute of the `<relativeBindForResources>` element to `true` optimizes Resource Manager's probe for satellite assemblies as follows:</span></span>  
  
-   <span data-ttu-id="3b07a-139">サテライト アセンブリを探すために、コードの親アセンブリの場所を使用します。</span><span class="sxs-lookup"><span data-stu-id="3b07a-139">It uses the location of the parent code assembly to probe for the satellite assembly.</span></span>  
  
-   <span data-ttu-id="3b07a-140">サテライト アセンブリの Windows インストーラーをクエリにはできません。</span><span class="sxs-lookup"><span data-stu-id="3b07a-140">It does not query Windows Installer for satellite assemblies.</span></span>  
  
-   <span data-ttu-id="3b07a-141">発生しない、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベント。</span><span class="sxs-lookup"><span data-stu-id="3b07a-141">It does not raise the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b07a-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b07a-142">See Also</span></span>  
 [<span data-ttu-id="3b07a-143">リソースのパッケージ化と配置</span><span class="sxs-lookup"><span data-stu-id="3b07a-143">Packaging and Deploying Resources</span></span>](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [<span data-ttu-id="3b07a-144">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="3b07a-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="3b07a-145">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="3b07a-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
