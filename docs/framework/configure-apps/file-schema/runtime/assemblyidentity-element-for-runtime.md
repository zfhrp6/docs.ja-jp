---
title: '&lt;assemblyIdentity&gt;要素&lt;ランタイム&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5d985d1620b7dec324c0113bcd5652cede044950
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a><span data-ttu-id="d1fe0-102">&lt;assemblyIdentity&gt;要素&lt;ランタイム&gt;</span><span class="sxs-lookup"><span data-stu-id="d1fe0-102">&lt;assemblyIdentity&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="d1fe0-103">アセンブリに関する識別情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-103">Contains identifying information about the assembly.</span></span>  
  
 <span data-ttu-id="d1fe0-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d1fe0-104">\<configuration></span></span>  
<span data-ttu-id="d1fe0-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="d1fe0-105">\<runtime></span></span>  
<span data-ttu-id="d1fe0-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="d1fe0-106">\<assemblyBinding></span></span>  
<span data-ttu-id="d1fe0-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="d1fe0-107">\<dependentAssembly></span></span>  
<span data-ttu-id="d1fe0-108">\<assemblyIdentity ></span><span class="sxs-lookup"><span data-stu-id="d1fe0-108">\<assemblyIdentity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1fe0-109">構文</span><span class="sxs-lookup"><span data-stu-id="d1fe0-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1fe0-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d1fe0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d1fe0-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1fe0-112">属性</span><span class="sxs-lookup"><span data-stu-id="d1fe0-112">Attributes</span></span>  
  
|<span data-ttu-id="d1fe0-113">属性</span><span class="sxs-lookup"><span data-stu-id="d1fe0-113">Attribute</span></span>|<span data-ttu-id="d1fe0-114">説明</span><span class="sxs-lookup"><span data-stu-id="d1fe0-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="d1fe0-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="d1fe0-116">アセンブリの名前</span><span class="sxs-lookup"><span data-stu-id="d1fe0-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="d1fe0-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d1fe0-118">言語および国/地域のアセンブリを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="d1fe0-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d1fe0-120">アセンブリの厳密な名前を指定する 16 進値。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="d1fe0-121">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d1fe0-122">1 つの値"x86"、"amd64"、"msil"または"ia64"プロセッサ固有のコードを格納するアセンブリのプロセッサ アーキテクチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="d1fe0-123">値小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-123">The values are not case-sensitive.</span></span> <span data-ttu-id="d1fe0-124">属性でその他の値、全体が割り当てられているかどうかは`<assemblyIdentity>`要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="d1fe0-125">「<xref:System.Reflection.ProcessorArchitecture>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="d1fe0-126">processorArchitecture 属性</span><span class="sxs-lookup"><span data-stu-id="d1fe0-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="d1fe0-127">[値]</span><span class="sxs-lookup"><span data-stu-id="d1fe0-127">Value</span></span>|<span data-ttu-id="d1fe0-128">説明</span><span class="sxs-lookup"><span data-stu-id="d1fe0-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="d1fe0-129">64 ビットの AMD プロセッサのみです。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-129">A 64-bit AMD processor only.</span></span>|  
|`ia64`|<span data-ttu-id="d1fe0-130">64 ビット Intel プロセッサのみです。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-130">A 64-bit Intel processor only.</span></span>|  
|`msil`|<span data-ttu-id="d1fe0-131">プロセッサとワードあたりのビット数に関して Neutral</span><span class="sxs-lookup"><span data-stu-id="d1fe0-131">Neutral with respect to processor and bits-per-word</span></span>|  
|`x86`|<span data-ttu-id="d1fe0-132">32 ビット Intel プロセッサで、ネイティブまたは Windows on Windows (WOW) 環境を 64 ビット プラットフォームでします。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-132">A 32-bit Intel processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1fe0-133">子要素</span><span class="sxs-lookup"><span data-stu-id="d1fe0-133">Child Elements</span></span>  
 <span data-ttu-id="d1fe0-134">なし。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1fe0-135">親要素</span><span class="sxs-lookup"><span data-stu-id="d1fe0-135">Parent Elements</span></span>  
  
|<span data-ttu-id="d1fe0-136">要素</span><span class="sxs-lookup"><span data-stu-id="d1fe0-136">Element</span></span>|<span data-ttu-id="d1fe0-137">説明</span><span class="sxs-lookup"><span data-stu-id="d1fe0-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="d1fe0-138">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="d1fe0-139">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="d1fe0-140">各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="d1fe0-141">1 つを使用して`<dependentAssembly>`各アセンブリの要素。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="d1fe0-142">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1fe0-143">コメント</span><span class="sxs-lookup"><span data-stu-id="d1fe0-143">Remarks</span></span>  
 <span data-ttu-id="d1fe0-144">各 **\<dependentAssembly >** 要素が 1 つあります **\<assemblyIdentity >** 子要素です。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="d1fe0-145">場合、`processorArchitecture`属性が含まれている、`<assemblyIdentity>`要素が、対応するプロセッサ アーキテクチャを持つアセンブリにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="d1fe0-146">場合、`processorArchitecture`属性が存在しない、`<assemblyIdentity>`要素は、すべてのプロセッサ アーキテクチャを持つアセンブリに適用できます。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="d1fe0-147">次の例を対象とする 2 つの 2 つの異なるプロセッサ アーキテクチャ、およびバージョンのないが維持されて同期された 2 つのアセンブリと同じ名前の構成ファイルを示します。X86 でアプリケーションを実行するときに、最初のプラットフォーム`<assemblyIdentity>`要素が適用され、その他は無視されます。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="d1fe0-148">アプリケーションは、x86 または ia64 以外のプラットフォームで実行する場合は両方とも無視されます。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="d1fe0-149">構成ファイルが含まれている場合、`<assemblyIdentity>`要素なしで`processorArchitecture`属性があり、プラットフォーム、せず、要素に一致する要素を含まない、`processorArchitecture`属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1fe0-150">例</span><span class="sxs-lookup"><span data-stu-id="d1fe0-150">Example</span></span>  
 <span data-ttu-id="d1fe0-151">次の例では、アセンブリに関する情報を提供する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d1fe0-151">The following example shows how to provide information about an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1fe0-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1fe0-152">See Also</span></span>  
 [<span data-ttu-id="d1fe0-153">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="d1fe0-153">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="d1fe0-154">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="d1fe0-154">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d1fe0-155">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="d1fe0-155">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
