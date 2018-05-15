---
title: '&lt;codeBase&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3b614546e8ed23cc1a5e169a33fb5878695037ae
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltcodebasegt-element"></a><span data-ttu-id="8fbaf-102">&lt;codeBase&gt;要素</span><span class="sxs-lookup"><span data-stu-id="8fbaf-102">&lt;codeBase&gt; Element</span></span>
<span data-ttu-id="8fbaf-103">共通言語ランタイムがアセンブリを検索する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-103">Specifies where the common language runtime can find an assembly.</span></span>  
  
 <span data-ttu-id="8fbaf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8fbaf-104">\<configuration></span></span>  
<span data-ttu-id="8fbaf-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="8fbaf-105">\<runtime></span></span>  
<span data-ttu-id="8fbaf-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="8fbaf-106">\<assemblyBinding></span></span>  
<span data-ttu-id="8fbaf-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="8fbaf-107">\<dependentAssembly></span></span>  
<span data-ttu-id="8fbaf-108">\<codeBase ></span><span class="sxs-lookup"><span data-stu-id="8fbaf-108">\<codeBase></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fbaf-109">構文</span><span class="sxs-lookup"><span data-stu-id="8fbaf-109">Syntax</span></span>  
  
```xml  
   <codeBase    
version="Assembly version"  
href="URL of assembly"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fbaf-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="8fbaf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8fbaf-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fbaf-112">属性</span><span class="sxs-lookup"><span data-stu-id="8fbaf-112">Attributes</span></span>  
  
|<span data-ttu-id="8fbaf-113">属性</span><span class="sxs-lookup"><span data-stu-id="8fbaf-113">Attribute</span></span>|<span data-ttu-id="8fbaf-114">説明</span><span class="sxs-lookup"><span data-stu-id="8fbaf-114">Description</span></span>|  
|---------------|-----------------|  
|`href`|<span data-ttu-id="8fbaf-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="8fbaf-116">ランタイムがアセンブリの指定されたバージョンを検索する場所の URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|  
|`version`|<span data-ttu-id="8fbaf-117">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="8fbaf-118">コードベースを適用するアセンブリのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="8fbaf-119">アセンブリ バージョン番号の形式が*major.minor.build.revision*です。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|  
  
## <a name="version-attribute"></a><span data-ttu-id="8fbaf-120">バージョン属性</span><span class="sxs-lookup"><span data-stu-id="8fbaf-120">version Attribute</span></span>  
  
|<span data-ttu-id="8fbaf-121">[値]</span><span class="sxs-lookup"><span data-stu-id="8fbaf-121">Value</span></span>|<span data-ttu-id="8fbaf-122">説明</span><span class="sxs-lookup"><span data-stu-id="8fbaf-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8fbaf-123">バージョン番号の各部分の有効な値は、0 ~ 65535 です。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="8fbaf-124">該当なし。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-124">Not applicable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fbaf-125">子要素</span><span class="sxs-lookup"><span data-stu-id="8fbaf-125">Child Elements</span></span>  
 <span data-ttu-id="8fbaf-126">なし。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8fbaf-127">親要素</span><span class="sxs-lookup"><span data-stu-id="8fbaf-127">Parent Elements</span></span>  
  
|<span data-ttu-id="8fbaf-128">要素</span><span class="sxs-lookup"><span data-stu-id="8fbaf-128">Element</span></span>|<span data-ttu-id="8fbaf-129">説明</span><span class="sxs-lookup"><span data-stu-id="8fbaf-129">Description</span></span>|  
|-------------|-----------------|  
|`buildproviders`|<span data-ttu-id="8fbaf-130">カスタム リソース ファイルをコンパイルするためのビルド プロバイダーのコレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="8fbaf-131">ビルド プロバイダーの数は任意です。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-131">You can have any number of build providers.</span></span>|  
|`compilation`|<span data-ttu-id="8fbaf-132">ASP.NET で使用されるすべてのコンパイルの設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-132">Configures all the compilation settings that ASP.NET uses.</span></span>|  
|`configuration`|<span data-ttu-id="8fbaf-133">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.web`|<span data-ttu-id="8fbaf-134">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-134">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fbaf-135">コメント</span><span class="sxs-lookup"><span data-stu-id="8fbaf-135">Remarks</span></span>  
 <span data-ttu-id="8fbaf-136">ランタイムを使用するため、  **\<codeBase >** 発行者ポリシー ファイルまたはマシン構成ファイルで設定をファイルする必要がありますも、アセンブリ バージョンをリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="8fbaf-137">アプリケーション構成ファイルは、アセンブリのバージョンをリダイレクトすることがなく、コードベースの設定を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="8fbaf-138">使用するアセンブリ バージョンを決定した後は、ランタイムは、バージョンを決定するファイルのコードベースの設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="8fbaf-139">コードベースが示されていない場合、ランタイムは、通常の方法で、アセンブリをプローブします。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>  
  
 <span data-ttu-id="8fbaf-140">アセンブリに厳密な名前がある場合、コードベース設定できる任意の場所、ローカル イントラネットまたはインターネット上です。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="8fbaf-141">アセンブリがプライベート アセンブリの場合は、コードベースの設定は、アプリケーションのディレクトリに対する相対パスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>  
  
 <span data-ttu-id="8fbaf-142">厳密な名前を指定せず、アセンブリのバージョンは無視され、ローダーの最初の外観を使用して\<codebase > 内部\<dependentAssembly >。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="8fbaf-143">別のアセンブリへのバインディングをリダイレクトする、アプリケーション構成ファイルにエントリがある場合、アセンブリのバージョンは、バインド要求と一致しない場合でもはリダイレクトが優先されます。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesnt match the binding request.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fbaf-144">例</span><span class="sxs-lookup"><span data-stu-id="8fbaf-144">Example</span></span>  
 <span data-ttu-id="8fbaf-145">次の例では、ランタイムがアセンブリを検索する場所を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8fbaf-145">The following example shows how to specify where the runtime can find an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fbaf-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fbaf-146">See Also</span></span>  
 [<span data-ttu-id="8fbaf-147">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="8fbaf-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="8fbaf-148">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="8fbaf-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="8fbaf-149">アセンブリの場所の指定</span><span class="sxs-lookup"><span data-stu-id="8fbaf-149">Specifying an Assembly's Location</span></span>](../../../../../docs/framework/configure-apps/specify-assembly-location.md)  
 [<span data-ttu-id="8fbaf-150">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="8fbaf-150">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
