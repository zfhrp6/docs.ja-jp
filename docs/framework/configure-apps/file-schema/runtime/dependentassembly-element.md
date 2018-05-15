---
title: '&lt;dependentAssembly&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54036baee6fc2d7af49e818a1c112dec8eac80aa
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltdependentassemblygt-element"></a><span data-ttu-id="791e5-102">&lt;dependentAssembly&gt;要素</span><span class="sxs-lookup"><span data-stu-id="791e5-102">&lt;dependentAssembly&gt; Element</span></span>
<span data-ttu-id="791e5-103">各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="791e5-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="791e5-104">1 つを使用して`dependentAssembly`各アセンブリの要素。</span><span class="sxs-lookup"><span data-stu-id="791e5-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
 <span data-ttu-id="791e5-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="791e5-105">\<configuration></span></span>  
<span data-ttu-id="791e5-106">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="791e5-106">\<runtime></span></span>  
<span data-ttu-id="791e5-107">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="791e5-107">\<assemblyBinding></span></span>  
<span data-ttu-id="791e5-108">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="791e5-108">\<dependentAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="791e5-109">構文</span><span class="sxs-lookup"><span data-stu-id="791e5-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="791e5-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="791e5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="791e5-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="791e5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="791e5-112">属性</span><span class="sxs-lookup"><span data-stu-id="791e5-112">Attributes</span></span>  
 <span data-ttu-id="791e5-113">なし。</span><span class="sxs-lookup"><span data-stu-id="791e5-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="791e5-114">子要素</span><span class="sxs-lookup"><span data-stu-id="791e5-114">Child Elements</span></span>  
  
|<span data-ttu-id="791e5-115">要素</span><span class="sxs-lookup"><span data-stu-id="791e5-115">Element</span></span>|<span data-ttu-id="791e5-116">説明</span><span class="sxs-lookup"><span data-stu-id="791e5-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="791e5-117">アセンブリに関する識別情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="791e5-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="791e5-118">この要素は、それぞれに含める必要がある`dependentAssembly`要素。</span><span class="sxs-lookup"><span data-stu-id="791e5-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="791e5-119">コンピューターにインストールされていない場合に、ランタイムでの共有アセンブリに検索できるを指定します。</span><span class="sxs-lookup"><span data-stu-id="791e5-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="791e5-120">1 つのアセンブリ バージョンを別のバージョンにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="791e5-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="791e5-121">ランタイムがこのアセンブリに発行者ポリシーを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="791e5-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="791e5-122">親要素</span><span class="sxs-lookup"><span data-stu-id="791e5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="791e5-123">要素</span><span class="sxs-lookup"><span data-stu-id="791e5-123">Element</span></span>|<span data-ttu-id="791e5-124">説明</span><span class="sxs-lookup"><span data-stu-id="791e5-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="791e5-125">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="791e5-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="791e5-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="791e5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="791e5-127">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="791e5-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="791e5-128">例</span><span class="sxs-lookup"><span data-stu-id="791e5-128">Example</span></span>  
 <span data-ttu-id="791e5-129">次の例では、2 つのアセンブリのアセンブリ情報をカプセル化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="791e5-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="791e5-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="791e5-130">See Also</span></span>  
 [<span data-ttu-id="791e5-131">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="791e5-131">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="791e5-132">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="791e5-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="791e5-133">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="791e5-133">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
