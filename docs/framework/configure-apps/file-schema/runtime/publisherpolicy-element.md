---
title: "&lt;publisherPolicy&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 654887c870a7f620c52fa402d6324de39fdb2feb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="c4b47-102">&lt;publisherPolicy&gt;要素</span><span class="sxs-lookup"><span data-stu-id="c4b47-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="c4b47-103">ランタイムが発行元ポリシーを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4b47-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="c4b47-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c4b47-104">\<configuration></span></span>  
<span data-ttu-id="c4b47-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="c4b47-105">\<runtime></span></span>  
<span data-ttu-id="c4b47-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="c4b47-106">\<assemblyBinding></span></span>  
<span data-ttu-id="c4b47-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="c4b47-107">\<dependentAssembly></span></span>  
<span data-ttu-id="c4b47-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="c4b47-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b47-109">構文</span><span class="sxs-lookup"><span data-stu-id="c4b47-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4b47-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="c4b47-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c4b47-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="c4b47-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4b47-112">属性</span><span class="sxs-lookup"><span data-stu-id="c4b47-112">Attributes</span></span>  
  
|<span data-ttu-id="c4b47-113">属性</span><span class="sxs-lookup"><span data-stu-id="c4b47-113">Attribute</span></span>|<span data-ttu-id="c4b47-114">説明</span><span class="sxs-lookup"><span data-stu-id="c4b47-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="c4b47-115">発行者ポリシーを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4b47-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="c4b47-116">属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="c4b47-116">apply Attribute</span></span>  
  
|<span data-ttu-id="c4b47-117">値</span><span class="sxs-lookup"><span data-stu-id="c4b47-117">Value</span></span>|<span data-ttu-id="c4b47-118">説明</span><span class="sxs-lookup"><span data-stu-id="c4b47-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="c4b47-119">発行者ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="c4b47-119">Applies publisher policy.</span></span> <span data-ttu-id="c4b47-120">これは、既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="c4b47-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="c4b47-121">発行者ポリシーは適用されません。</span><span class="sxs-lookup"><span data-stu-id="c4b47-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c4b47-122">子要素</span><span class="sxs-lookup"><span data-stu-id="c4b47-122">Child Elements</span></span>  
 <span data-ttu-id="c4b47-123">なし。</span><span class="sxs-lookup"><span data-stu-id="c4b47-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4b47-124">親要素</span><span class="sxs-lookup"><span data-stu-id="c4b47-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c4b47-125">要素</span><span class="sxs-lookup"><span data-stu-id="c4b47-125">Element</span></span>|<span data-ttu-id="c4b47-126">説明</span><span class="sxs-lookup"><span data-stu-id="c4b47-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c4b47-127">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="c4b47-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c4b47-128">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c4b47-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4b47-129">コメント</span><span class="sxs-lookup"><span data-stu-id="c4b47-129">Remarks</span></span>  
 <span data-ttu-id="c4b47-130">コンポーネントの開発元は、アセンブリの新しいバージョンをリリースするとき仕入先はこれで、古いバージョンを使用するアプリケーションが新しいバージョンを使用するため、発行者ポリシーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c4b47-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="c4b47-131">特定のアセンブリの発行者ポリシーを適用するかどうかを指定するには、配置、  **\<publisherPolicy >**内の要素、  **\<dependentAssembly >**要素。</span><span class="sxs-lookup"><span data-stu-id="c4b47-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="c4b47-132">既定の設定、**適用**属性は**はい**です。</span><span class="sxs-lookup"><span data-stu-id="c4b47-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="c4b47-133">設定、**適用**属性を**ありません**以前のどのオーバーライド**はい**アセンブリに対して既に設定します。</span><span class="sxs-lookup"><span data-stu-id="c4b47-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="c4b47-134">アクセス許可は、アプリケーションを使用して発行者ポリシーを明示的に無視する必要、 [ \<publisherPolicy 適用 ="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)アプリケーション構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="c4b47-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="c4b47-135">許可を設定して、<xref:System.Security.Permissions.SecurityPermissionFlag>フラグを<xref:System.Security.Permissions.SecurityPermission>です。</span><span class="sxs-lookup"><span data-stu-id="c4b47-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="c4b47-136">詳細については、次を参照してください。[アセンブリ バインディング リダイレクトのセキュリティのアクセス許可](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)です。</span><span class="sxs-lookup"><span data-stu-id="c4b47-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4b47-137">例</span><span class="sxs-lookup"><span data-stu-id="c4b47-137">Example</span></span>  
 <span data-ttu-id="c4b47-138">次の例が、アセンブリの発行者ポリシーをオフに`myAssembly`です。</span><span class="sxs-lookup"><span data-stu-id="c4b47-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                                    publicKeyToken="32ab4ba45e0a69a1"  
                                    culture="neutral" />  
            <publisherPolicy apply="no"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4b47-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="c4b47-139">See Also</span></span>  
 [<span data-ttu-id="c4b47-140">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="c4b47-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="c4b47-141">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="c4b47-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="c4b47-142">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="c4b47-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="c4b47-143">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="c4b47-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
