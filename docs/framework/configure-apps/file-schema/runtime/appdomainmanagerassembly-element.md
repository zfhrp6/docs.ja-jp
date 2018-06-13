---
title: '&lt;appDomainManagerAssembly&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7656f4819e8ed6d8c1c87eabcbd5862929d47cdc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744851"
---
# <a name="ltappdomainmanagerassemblygt-element"></a><span data-ttu-id="91b1e-102">&lt;appDomainManagerAssembly&gt;要素</span><span class="sxs-lookup"><span data-stu-id="91b1e-102">&lt;appDomainManagerAssembly&gt; Element</span></span>
<span data-ttu-id="91b1e-103">プロセスにおける既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを提供するアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="91b1e-103">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>  
  
 <span data-ttu-id="91b1e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="91b1e-104">\<configuration></span></span>  
<span data-ttu-id="91b1e-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="91b1e-105">\<runtime></span></span>  
<span data-ttu-id="91b1e-106">\<appDomainManagerAssembly ></span><span class="sxs-lookup"><span data-stu-id="91b1e-106">\<appDomainManagerAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91b1e-107">構文</span><span class="sxs-lookup"><span data-stu-id="91b1e-107">Syntax</span></span>  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91b1e-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="91b1e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="91b1e-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="91b1e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91b1e-110">属性</span><span class="sxs-lookup"><span data-stu-id="91b1e-110">Attributes</span></span>  
  
|<span data-ttu-id="91b1e-111">属性</span><span class="sxs-lookup"><span data-stu-id="91b1e-111">Attribute</span></span>|<span data-ttu-id="91b1e-112">説明</span><span class="sxs-lookup"><span data-stu-id="91b1e-112">Description</span></span>|  
|---------------|-----------------|  
|`value`|<span data-ttu-id="91b1e-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="91b1e-113">Required attribute.</span></span> <span data-ttu-id="91b1e-114">プロセスの既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを提供するアセンブリの表示名を指定します。</span><span class="sxs-lookup"><span data-stu-id="91b1e-114">Specifies the display name of the assembly that provides the application domain manager for the default application domain in the process.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91b1e-115">子要素</span><span class="sxs-lookup"><span data-stu-id="91b1e-115">Child Elements</span></span>  
 <span data-ttu-id="91b1e-116">なし。</span><span class="sxs-lookup"><span data-stu-id="91b1e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91b1e-117">親要素</span><span class="sxs-lookup"><span data-stu-id="91b1e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="91b1e-118">要素</span><span class="sxs-lookup"><span data-stu-id="91b1e-118">Element</span></span>|<span data-ttu-id="91b1e-119">説明</span><span class="sxs-lookup"><span data-stu-id="91b1e-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="91b1e-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="91b1e-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="91b1e-121">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91b1e-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91b1e-122">コメント</span><span class="sxs-lookup"><span data-stu-id="91b1e-122">Remarks</span></span>  
 <span data-ttu-id="91b1e-123">アプリケーション ドメイン マネージャーの種類を指定するには、この両方の要素を指定する必要があります、 [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)要素。</span><span class="sxs-lookup"><span data-stu-id="91b1e-123">To specify the type of the application domain manager, you must specify both this element and the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element.</span></span> <span data-ttu-id="91b1e-124">これらの要素のいずれかが指定されていない場合、その他は無視されます。</span><span class="sxs-lookup"><span data-stu-id="91b1e-124">If either of these elements is not specified, the other is ignored.</span></span>  
  
 <span data-ttu-id="91b1e-125">既定のアプリケーション ドメインが読み込まれるときに<xref:System.TypeLoadException>が、指定したアセンブリが存在しない場合、またはアセンブリに指定された型が含まれていない場合にスローされます、 [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)要素であるとプロセスは、起動に失敗します。</span><span class="sxs-lookup"><span data-stu-id="91b1e-125">When the default application domain is loaded, <xref:System.TypeLoadException> is thrown if the specified assembly does not exist or if the assembly does not contain the type specified by the [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) element; and the process fails to start.</span></span> <span data-ttu-id="91b1e-126">アセンブリが見つかりましたが、バージョン情報が一致しない場合、<xref:System.IO.FileLoadException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="91b1e-126">If the assembly is found but the version information does not match, a <xref:System.IO.FileLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="91b1e-127">既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーの種類を指定すると、既定のアプリケーション ドメインから作成された他のアプリケーション ドメインは、アプリケーション ドメイン マネージャーの型を継承します。</span><span class="sxs-lookup"><span data-stu-id="91b1e-127">When you specify the application domain manager type for the default application domain, other application domains created from the default application domain inherit the application domain manager type.</span></span> <span data-ttu-id="91b1e-128">使用して、<xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>と<xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>プロパティを新しいアプリケーション ドメインの別のアプリケーション ドメイン マネージャーの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="91b1e-128">Use the <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> and <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> properties to specify a different application domain manager type for a new application domain.</span></span>  
  
 <span data-ttu-id="91b1e-129">アプリケーション ドメイン マネージャーの種類を指定するには、アプリケーションに完全な信頼が必要です。</span><span class="sxs-lookup"><span data-stu-id="91b1e-129">Specifying the application domain manager type requires the application to have full trust.</span></span> <span data-ttu-id="91b1e-130">(たとえば、デスクトップで実行されているアプリケーションが完全な信頼。)アプリケーションには、完全な信頼がない場合、<xref:System.TypeLoadException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="91b1e-130">(For example, an application running on the desktop has full trust.) If the application does not have full trust, a <xref:System.TypeLoadException> is thrown.</span></span>  
  
 <span data-ttu-id="91b1e-131">アセンブリの表示名の形式の場合、次を参照してください。、<xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="91b1e-131">For the format of the assembly display name, see the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="91b1e-132">この構成要素はでのみ使用できますが、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]およびそれ以降。</span><span class="sxs-lookup"><span data-stu-id="91b1e-132">This configuration element is available only in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91b1e-133">例</span><span class="sxs-lookup"><span data-stu-id="91b1e-133">Example</span></span>  
 <span data-ttu-id="91b1e-134">次の例は、プロセスの既定のアプリケーション ドメインのアプリケーション ドメイン マネージャーを指定する方法を示しています、`MyMgr`に入力、`AdMgrExample`アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="91b1e-134">The following example shows how to specify that the application domain manager for the default application domain of a process is the `MyMgr` type in the `AdMgrExample` assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="91b1e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="91b1e-135">See Also</span></span>  
 <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>  
 <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="91b1e-136">\<appDomainManagerType > 要素</span><span class="sxs-lookup"><span data-stu-id="91b1e-136">\<appDomainManagerType> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
 [<span data-ttu-id="91b1e-137">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="91b1e-137">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="91b1e-138">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="91b1e-138">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="91b1e-139">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="91b1e-139">SetAppDomainManagerType Method</span></span>](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
