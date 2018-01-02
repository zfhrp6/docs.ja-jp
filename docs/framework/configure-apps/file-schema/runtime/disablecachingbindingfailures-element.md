---
title: "&lt;disableCachingBindingFailures&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCachingBindingFailures
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCachingBindingFailures
helpviewer_keywords:
- assemblies [.NET Framework],caching binding failures
- caching assembly binding failures
- <disableCachingBindingFailures> element
- disableCachingBindingFailures element
ms.assetid: bf598873-83b7-48de-8955-00b0504fbad0
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd86bc2f58bc216f741c32a51925d3f4f8ef47df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltdisablecachingbindingfailuresgt-element"></a><span data-ttu-id="f3bfd-102">&lt;disableCachingBindingFailures&gt;要素</span><span class="sxs-lookup"><span data-stu-id="f3bfd-102">&lt;disableCachingBindingFailures&gt; Element</span></span>
<span data-ttu-id="f3bfd-103">バインディングを調査して、アセンブリが見つからなかったために発生するエラーのキャッシュを無効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-103">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>  
  
 <span data-ttu-id="f3bfd-104">\<configuration > 要素</span><span class="sxs-lookup"><span data-stu-id="f3bfd-104">\<configuration> Element</span></span>  
<span data-ttu-id="f3bfd-105">\<ランタイム > 要素</span><span class="sxs-lookup"><span data-stu-id="f3bfd-105">\<runtime> Element</span></span>  
<span data-ttu-id="f3bfd-106">\<disableCachingBindingFailures ></span><span class="sxs-lookup"><span data-stu-id="f3bfd-106">\<disableCachingBindingFailures></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3bfd-107">構文</span><span class="sxs-lookup"><span data-stu-id="f3bfd-107">Syntax</span></span>  
  
```xml  
<disableCachingBindingFailures enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3bfd-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f3bfd-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f3bfd-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3bfd-110">属性</span><span class="sxs-lookup"><span data-stu-id="f3bfd-110">Attributes</span></span>  
  
|<span data-ttu-id="f3bfd-111">属性</span><span class="sxs-lookup"><span data-stu-id="f3bfd-111">Attribute</span></span>|<span data-ttu-id="f3bfd-112">説明</span><span class="sxs-lookup"><span data-stu-id="f3bfd-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3bfd-113">enabled</span><span class="sxs-lookup"><span data-stu-id="f3bfd-113">enabled</span></span>|<span data-ttu-id="f3bfd-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="f3bfd-115">バインディングを調査して、アセンブリが見つからなかったために発生するエラーのキャッシュを無効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-115">Specifies whether to disable the caching of binding failures that occur because the assembly was not found by probing.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f3bfd-116">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="f3bfd-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="f3bfd-117">値</span><span class="sxs-lookup"><span data-stu-id="f3bfd-117">Value</span></span>|<span data-ttu-id="f3bfd-118">説明</span><span class="sxs-lookup"><span data-stu-id="f3bfd-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3bfd-119">0</span><span class="sxs-lookup"><span data-stu-id="f3bfd-119">0</span></span>|<span data-ttu-id="f3bfd-120">バインディングを調査して、アセンブリが見つからなかったために発生するエラーのキャッシュを無効にできません。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-120">Do not disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="f3bfd-121">これは、.NET Framework version 2.0 以降の既定のバインディングの動作です。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-121">This is the default binding behavior starting with the .NET Framework version 2.0.</span></span>|  
|<span data-ttu-id="f3bfd-122">1</span><span class="sxs-lookup"><span data-stu-id="f3bfd-122">1</span></span>|<span data-ttu-id="f3bfd-123">バインディングを調査して、アセンブリが見つからなかったために発生するエラーのキャッシュを無効にします。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-123">Disable the caching of binding failures that occur because the assembly was not found by probing.</span></span> <span data-ttu-id="f3bfd-124">この設定は、.NET Framework version 1.1 のバインドの動作に戻ります。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-124">This setting reverts to the binding behavior of the .NET Framework version 1.1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3bfd-125">子要素</span><span class="sxs-lookup"><span data-stu-id="f3bfd-125">Child Elements</span></span>  
 <span data-ttu-id="f3bfd-126">なし。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3bfd-127">親要素</span><span class="sxs-lookup"><span data-stu-id="f3bfd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f3bfd-128">要素</span><span class="sxs-lookup"><span data-stu-id="f3bfd-128">Element</span></span>|<span data-ttu-id="f3bfd-129">説明</span><span class="sxs-lookup"><span data-stu-id="f3bfd-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f3bfd-130">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f3bfd-131">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3bfd-132">コメント</span><span class="sxs-lookup"><span data-stu-id="f3bfd-132">Remarks</span></span>  
 <span data-ttu-id="f3bfd-133">以降、.NET Framework version 2.0 では、アセンブリの読み込みの既定の動作をすべてのバインディングと読み込みエラーをキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-133">Starting with the .NET Framework version 2.0, the default behavior for loading assemblies is to cache all binding and loading failures.</span></span> <span data-ttu-id="f3bfd-134">つまり、アセンブリの読み込みに失敗した場合、同じアセンブリの読み込みに後続の要求は即座に失敗しようとするアセンブリの検索をします。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-134">That is, if an attempt to load an assembly fails, subsequent requests to load the same assembly fail immediately, without any attempt to locate the assembly.</span></span> <span data-ttu-id="f3bfd-135">この要素は、そのアセンブリが調査パスに見つからなかったために発生するエラーをバインドするための既定の動作を無効にします。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-135">This element disables that default behavior for binding failures that occur because the assembly could not be found in the probing path.</span></span> <span data-ttu-id="f3bfd-136">このようなエラーをスロー<xref:System.IO.FileNotFoundException>です。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-136">These failures throw <xref:System.IO.FileNotFoundException>.</span></span>  
  
 <span data-ttu-id="f3bfd-137">一部のバインドと障害の読み込みは、この要素の影響は受けませんされ、常にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-137">Some binding and loading failures are not affected by this element, and are always cached.</span></span> <span data-ttu-id="f3bfd-138">アセンブリが見つかりましたが、読み込むことができないために、このようなエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-138">These failures occur because the assembly was found but could not be loaded.</span></span> <span data-ttu-id="f3bfd-139">スロー<xref:System.BadImageFormatException>または<xref:System.IO.FileLoadException>です。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-139">They throw <xref:System.BadImageFormatException> or <xref:System.IO.FileLoadException>.</span></span> <span data-ttu-id="f3bfd-140">次の一覧には、このようなエラーの例いくつかにはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-140">The following list includes some examples of such failures.</span></span>  
  
-   <span data-ttu-id="f3bfd-141">読み込もうとした場合は、ファイルが有効なアセンブリではない、適切なアセンブリに無効なファイルが置き換えられた場合でも、後続のアセンブリの読み込みは失敗します。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-141">If you attempt to load a file is not a valid assembly, subsequent attempts to load the assembly will fail even if the bad file is replaced with the correct assembly.</span></span>  
  
-   <span data-ttu-id="f3bfd-142">ファイル システムによってロックされているアセンブリをロードしようとすると、アセンブリが、ファイル システムによってリリースされた後でも後続のアセンブリの読み込みは失敗します。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-142">If you attempt to load an assembly that is locked by the file system, subsequent attempts to load the assembly will fail even after the assembly is released by the file system.</span></span>  
  
-   <span data-ttu-id="f3bfd-143">ロードしようとしているアセンブリの 1 つまたは複数のバージョンは、プローブ パスですが、要求している特定のバージョンはそれらの間にない場合、調査パスに正しいバージョンが移動された場合でもそのバージョンの読み込みに後続の試行は失敗します。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-143">If one or more versions of the assembly that you are attempting to load is in the probing path, but the specific version you are requesting is not among them, subsequent attempts to load that version will fail even if the correct version is moved into the probing path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3bfd-144">例</span><span class="sxs-lookup"><span data-stu-id="f3bfd-144">Example</span></span>  
 <span data-ttu-id="f3bfd-145">次の例では、アセンブリ バインディング エラーを調査して、アセンブリが見つからなかったために発生するのキャッシュを無効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f3bfd-145">The following example shows how to disable the caching of assembly binding failures that occur because the assembly was not found by probing.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCachingBindingFailures enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3bfd-146">参照</span><span class="sxs-lookup"><span data-stu-id="f3bfd-146">See Also</span></span>  
 [<span data-ttu-id="f3bfd-147">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="f3bfd-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="f3bfd-148">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="f3bfd-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f3bfd-149">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="f3bfd-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
