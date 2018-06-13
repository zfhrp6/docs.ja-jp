---
title: '&lt;publisherPolicy&gt;要素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/publisherPolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#publisherPolicy
helpviewer_keywords:
- publisherPolicy element
- container tags, <publisherPolicy> element
- <publisherPolicy> element
ms.assetid: 4613407e-d0a8-4ef2-9f81-a6acb9fdc7d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cc3b7220fe34f5dc049a3da71b160a88f82fdb1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746099"
---
# <a name="ltpublisherpolicygt-element"></a><span data-ttu-id="97efe-102">&lt;publisherPolicy&gt;要素</span><span class="sxs-lookup"><span data-stu-id="97efe-102">&lt;publisherPolicy&gt; Element</span></span>
<span data-ttu-id="97efe-103">ランタイムが発行元ポリシーを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="97efe-103">Specifies whether the runtime applies publisher policy.</span></span>  
  
 <span data-ttu-id="97efe-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="97efe-104">\<configuration></span></span>  
<span data-ttu-id="97efe-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="97efe-105">\<runtime></span></span>  
<span data-ttu-id="97efe-106">\<assemblyBinding></span><span class="sxs-lookup"><span data-stu-id="97efe-106">\<assemblyBinding></span></span>  
<span data-ttu-id="97efe-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="97efe-107">\<dependentAssembly></span></span>  
<span data-ttu-id="97efe-108">\<publisherPolicy ></span><span class="sxs-lookup"><span data-stu-id="97efe-108">\<publisherPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97efe-109">構文</span><span class="sxs-lookup"><span data-stu-id="97efe-109">Syntax</span></span>  
  
```xml  
<publisherPolicy apply="yes|no"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97efe-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="97efe-110">Attributes and Elements</span></span>  
 <span data-ttu-id="97efe-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="97efe-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97efe-112">属性</span><span class="sxs-lookup"><span data-stu-id="97efe-112">Attributes</span></span>  
  
|<span data-ttu-id="97efe-113">属性</span><span class="sxs-lookup"><span data-stu-id="97efe-113">Attribute</span></span>|<span data-ttu-id="97efe-114">説明</span><span class="sxs-lookup"><span data-stu-id="97efe-114">Description</span></span>|  
|---------------|-----------------|  
|`apply`|<span data-ttu-id="97efe-115">発行者ポリシーを適用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="97efe-115">Specifies whether to apply publisher policy.</span></span>|  
  
## <a name="apply-attribute"></a><span data-ttu-id="97efe-116">属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="97efe-116">apply Attribute</span></span>  
  
|<span data-ttu-id="97efe-117">[値]</span><span class="sxs-lookup"><span data-stu-id="97efe-117">Value</span></span>|<span data-ttu-id="97efe-118">説明</span><span class="sxs-lookup"><span data-stu-id="97efe-118">Description</span></span>|  
|-----------|-----------------|  
|`yes`|<span data-ttu-id="97efe-119">発行者ポリシーを適用します。</span><span class="sxs-lookup"><span data-stu-id="97efe-119">Applies publisher policy.</span></span> <span data-ttu-id="97efe-120">これは、既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="97efe-120">This is the default setting.</span></span>|  
|`no`|<span data-ttu-id="97efe-121">発行者ポリシーは適用されません。</span><span class="sxs-lookup"><span data-stu-id="97efe-121">Does not apply publisher policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97efe-122">子要素</span><span class="sxs-lookup"><span data-stu-id="97efe-122">Child Elements</span></span>  
 <span data-ttu-id="97efe-123">なし。</span><span class="sxs-lookup"><span data-stu-id="97efe-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97efe-124">親要素</span><span class="sxs-lookup"><span data-stu-id="97efe-124">Parent Elements</span></span>  
  
|<span data-ttu-id="97efe-125">要素</span><span class="sxs-lookup"><span data-stu-id="97efe-125">Element</span></span>|<span data-ttu-id="97efe-126">説明</span><span class="sxs-lookup"><span data-stu-id="97efe-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="97efe-127">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="97efe-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="97efe-128">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="97efe-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97efe-129">コメント</span><span class="sxs-lookup"><span data-stu-id="97efe-129">Remarks</span></span>  
 <span data-ttu-id="97efe-130">コンポーネントの開発元は、アセンブリの新しいバージョンをリリースするとき仕入先はこれで、古いバージョンを使用するアプリケーションが新しいバージョンを使用するため、発行者ポリシーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="97efe-130">When a component vendor releases a new version of an assembly, the vendor can include a publisher policy so applications that use the old version now use the new version.</span></span> <span data-ttu-id="97efe-131">特定のアセンブリの発行者ポリシーを適用するかどうかを指定するには、配置、  **\<publisherPolicy >** 内の要素、  **\<dependentAssembly >** 要素。</span><span class="sxs-lookup"><span data-stu-id="97efe-131">To specify whether to apply publisher policy for a particular assembly, put the **\<publisherPolicy>** element in the **\<dependentAssembly>** element.</span></span>  
  
 <span data-ttu-id="97efe-132">既定の設定、**適用**属性は**はい**です。</span><span class="sxs-lookup"><span data-stu-id="97efe-132">The default setting for the **apply** attribute is **yes**.</span></span> <span data-ttu-id="97efe-133">設定、**適用**属性を**ありません**以前のどのオーバーライド**はい**アセンブリに対して既に設定します。</span><span class="sxs-lookup"><span data-stu-id="97efe-133">Setting the **apply** attribute to **no** overrides any previous **yes** settings for an assembly.</span></span>  
  
 <span data-ttu-id="97efe-134">アクセス許可は、アプリケーションを使用して発行者ポリシーを明示的に無視する必要、 [ \<publisherPolicy 適用 ="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)アプリケーション構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="97efe-134">Permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span> <span data-ttu-id="97efe-135">許可を設定して、<xref:System.Security.Permissions.SecurityPermissionFlag>フラグを<xref:System.Security.Permissions.SecurityPermission>です。</span><span class="sxs-lookup"><span data-stu-id="97efe-135">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="97efe-136">詳細については、次を参照してください。[アセンブリ バインディング リダイレクトのセキュリティのアクセス許可](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)です。</span><span class="sxs-lookup"><span data-stu-id="97efe-136">For more information, see [Assembly Binding Redirection Security Permission](../../../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97efe-137">例</span><span class="sxs-lookup"><span data-stu-id="97efe-137">Example</span></span>  
 <span data-ttu-id="97efe-138">次の例が、アセンブリの発行者ポリシーをオフに`myAssembly`です。</span><span class="sxs-lookup"><span data-stu-id="97efe-138">The following example turns off publisher policy for the assembly, `myAssembly`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97efe-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="97efe-139">See Also</span></span>  
 [<span data-ttu-id="97efe-140">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="97efe-140">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="97efe-141">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="97efe-141">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="97efe-142">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="97efe-142">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="97efe-143">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="97efe-143">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
