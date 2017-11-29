---
title: "&lt;bindingRedirect&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/bindingRedirect
- http://schemas.microsoft.com/.NetConfiguration/v2.0#bindingRedirect
helpviewer_keywords:
- <bindingRedirect> element
- container tags, <bindingRedirect> element
- bindingRedirect element
ms.assetid: 67784ecd-9663-434e-bd6a-26975e447ac0
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3bc8abc019ddb271c8c1246b280be754585bfd61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingredirectgt-element"></a><span data-ttu-id="f75c9-102">&lt;bindingRedirect&gt;要素</span><span class="sxs-lookup"><span data-stu-id="f75c9-102">&lt;bindingRedirect&gt; Element</span></span>
<span data-ttu-id="f75c9-103">1 つのアセンブリ バージョンを別のバージョンにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="f75c9-103">Redirects one assembly version to another.</span></span>  
  
 <span data-ttu-id="f75c9-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f75c9-104">\<configuration></span></span>  
<span data-ttu-id="f75c9-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="f75c9-105">\<runtime></span></span>  
<span data-ttu-id="f75c9-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="f75c9-106">\<assemblyBinding></span></span>  
<span data-ttu-id="f75c9-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="f75c9-107">\<dependentAssembly></span></span>  
<span data-ttu-id="f75c9-108">\<bindingRedirect ></span><span class="sxs-lookup"><span data-stu-id="f75c9-108">\<bindingRedirect></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f75c9-109">構文</span><span class="sxs-lookup"><span data-stu-id="f75c9-109">Syntax</span></span>  
  
```xml  
   <bindingRedirect    
oldVersion="existing assembly version"  
newVersion="new assembly version"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f75c9-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f75c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f75c9-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f75c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f75c9-112">属性</span><span class="sxs-lookup"><span data-stu-id="f75c9-112">Attributes</span></span>  
  
|<span data-ttu-id="f75c9-113">属性</span><span class="sxs-lookup"><span data-stu-id="f75c9-113">Attribute</span></span>|<span data-ttu-id="f75c9-114">説明</span><span class="sxs-lookup"><span data-stu-id="f75c9-114">Description</span></span>|  
|---------------|-----------------|  
|`oldVersion`|<span data-ttu-id="f75c9-115">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f75c9-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="f75c9-116">初めに要求されていたアセンブリのバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="f75c9-116">Specifies the version of the assembly that was originally requested.</span></span> <span data-ttu-id="f75c9-117">アセンブリ バージョン番号の形式が*major.minor.build.revision*です。</span><span class="sxs-lookup"><span data-stu-id="f75c9-117">The format of an assembly version number is *major.minor.build.revision*.</span></span> <span data-ttu-id="f75c9-118">このバージョン番号の各部分で有効値は、0 ～ 65535 です。</span><span class="sxs-lookup"><span data-stu-id="f75c9-118">Valid values for each part of this version number are 0 to 65535.</span></span><br /><br /> <span data-ttu-id="f75c9-119">バージョン範囲は、次の形式でも指定できます。</span><span class="sxs-lookup"><span data-stu-id="f75c9-119">You can also specify a range of versions in the following format:</span></span><br /><br /> <span data-ttu-id="f75c9-120">*n.n.n.n - n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="f75c9-120">*n.n.n.n - n.n.n.n*</span></span>|  
|`newVersion`|<span data-ttu-id="f75c9-121">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f75c9-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="f75c9-122">形式で要求されていたバージョンの代わりに使用するアセンブリのバージョンを指定します: *n.n.n.n*</span><span class="sxs-lookup"><span data-stu-id="f75c9-122">Specifies the version of the assembly to use instead of the originally requested version in the format: *n.n.n.n*</span></span><br /><br /> <span data-ttu-id="f75c9-123">この値では `oldVersion` より前のバージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f75c9-123">This value can specify an earlier version than `oldVersion`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f75c9-124">子要素</span><span class="sxs-lookup"><span data-stu-id="f75c9-124">Child Elements</span></span>  
  
|<span data-ttu-id="f75c9-125">要素</span><span class="sxs-lookup"><span data-stu-id="f75c9-125">Element</span></span>|<span data-ttu-id="f75c9-126">説明</span><span class="sxs-lookup"><span data-stu-id="f75c9-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f75c9-127">なし</span><span class="sxs-lookup"><span data-stu-id="f75c9-127">None</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="f75c9-128">親要素</span><span class="sxs-lookup"><span data-stu-id="f75c9-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f75c9-129">要素</span><span class="sxs-lookup"><span data-stu-id="f75c9-129">Element</span></span>|<span data-ttu-id="f75c9-130">説明</span><span class="sxs-lookup"><span data-stu-id="f75c9-130">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="f75c9-131">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f75c9-131">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="f75c9-132">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="f75c9-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="f75c9-133">各アセンブリのバインディング ポリシーとアセンブリの場所をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="f75c9-133">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="f75c9-134">アセンブリごとに 1 つの dependentAssembly 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="f75c9-134">Use one dependentAssembly element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="f75c9-135">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f75c9-135">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f75c9-136">コメント</span><span class="sxs-lookup"><span data-stu-id="f75c9-136">Remarks</span></span>  
 <span data-ttu-id="f75c9-137">厳密な名前付きアセンブリに対して .NET Framework アプリケーションを構築すると、実行時に新しいバージョンが利用できる場合でも、既定で、アプリケーションの構築時に使用したアセンブリのバージョンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="f75c9-137">When you build a .NET Framework application against a strong-named assembly, the application uses that version of the assembly at run time by default, even if a new version is available.</span></span> <span data-ttu-id="f75c9-138">ただし、新しいバージョンのアセンブリで実行するようにもアプリケーションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="f75c9-138">However, you can configure the application to run against a newer version of the assembly.</span></span> <span data-ttu-id="f75c9-139">ランタイムがこれらのファイルを使用して、使用するアセンブリ バージョンを決定する方法の詳細については、「[ランタイム アセンブリを検索する方法](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)です。</span><span class="sxs-lookup"><span data-stu-id="f75c9-139">For details on how the runtime uses these files to determine which assembly version to use, see [How the Runtime Locates Assemblies](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="f75c9-140">複数の `bindingRedirect` 要素を `dependentAssembly` 要素に含めることによって、複数のアセンブリ バージョンをリダイレクトできます。</span><span class="sxs-lookup"><span data-stu-id="f75c9-140">You can redirect more than one assembly version by including multiple `bindingRedirect` elements in a `dependentAssembly` element.</span></span> <span data-ttu-id="f75c9-141">また、アセンブリの新しいバージョンから古いバージョンにリダイレクトすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f75c9-141">You can also redirect from a newer version to an older version of the assembly.</span></span>  
  
 <span data-ttu-id="f75c9-142">アプリケーション構成ファイルで明示的にアセンブリ バインディングをリダイレクトするには、セキュリティ アクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="f75c9-142">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="f75c9-143">これは、.NET Framework アセンブリおよびサードパーティ製アセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="f75c9-143">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="f75c9-144">許可を設定して、<xref:System.Security.Permissions.SecurityPermissionFlag>フラグを<xref:System.Security.Permissions.SecurityPermission>です。</span><span class="sxs-lookup"><span data-stu-id="f75c9-144">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="f75c9-145">詳細については、次を参照してください。[アセンブリ バインディング リダイレクトのセキュリティのアクセス許可](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)です。</span><span class="sxs-lookup"><span data-stu-id="f75c9-145">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f75c9-146">例</span><span class="sxs-lookup"><span data-stu-id="f75c9-146">Example</span></span>  
 <span data-ttu-id="f75c9-147">あるアセンブリ バージョンを別のバージョンにリダイレクトする例を示します。</span><span class="sxs-lookup"><span data-stu-id="f75c9-147">The following example shows how to redirect one assembly version to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f75c9-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="f75c9-148">See Also</span></span>  
 [<span data-ttu-id="f75c9-149">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="f75c9-149">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="f75c9-150">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="f75c9-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="f75c9-151">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="f75c9-151">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
