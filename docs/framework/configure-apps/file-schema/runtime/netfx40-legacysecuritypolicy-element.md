---
title: "&lt;NetFx40_LegacySecurityPolicy&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 636b7020a8728978ea13529382a822d99cd36f74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx40legacysecuritypolicygt-element"></a><span data-ttu-id="11e8a-102">&lt;NetFx40_LegacySecurityPolicy&gt;要素</span><span class="sxs-lookup"><span data-stu-id="11e8a-102">&lt;NetFx40_LegacySecurityPolicy&gt; Element</span></span>
<span data-ttu-id="11e8a-103">ランタイムがレガシ コード アクセス セキュリティ (CAS) ポリシーを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="11e8a-103">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>  
  
 <span data-ttu-id="11e8a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="11e8a-104">\<configuration></span></span>  
<span data-ttu-id="11e8a-105">\<ランタイム ></span><span class="sxs-lookup"><span data-stu-id="11e8a-105">\<runtime></span></span>  
<span data-ttu-id="11e8a-106">< NetFx40_LegacySecurityPolicy ></span><span class="sxs-lookup"><span data-stu-id="11e8a-106"><NetFx40_LegacySecurityPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11e8a-107">構文</span><span class="sxs-lookup"><span data-stu-id="11e8a-107">Syntax</span></span>  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11e8a-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="11e8a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="11e8a-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="11e8a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11e8a-110">属性</span><span class="sxs-lookup"><span data-stu-id="11e8a-110">Attributes</span></span>  
  
|<span data-ttu-id="11e8a-111">属性</span><span class="sxs-lookup"><span data-stu-id="11e8a-111">Attribute</span></span>|<span data-ttu-id="11e8a-112">説明</span><span class="sxs-lookup"><span data-stu-id="11e8a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="11e8a-113">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="11e8a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="11e8a-114">ランタイムがレガシ CAS ポリシーを使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="11e8a-114">Specifies whether the runtime uses legacy CAS policy.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="11e8a-115">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="11e8a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="11e8a-116">値</span><span class="sxs-lookup"><span data-stu-id="11e8a-116">Value</span></span>|<span data-ttu-id="11e8a-117">説明</span><span class="sxs-lookup"><span data-stu-id="11e8a-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="11e8a-118">ランタイムは、従来の CAS ポリシーを使用しません。</span><span class="sxs-lookup"><span data-stu-id="11e8a-118">The runtime does not use legacy CAS policy.</span></span> <span data-ttu-id="11e8a-119">既定値です。</span><span class="sxs-lookup"><span data-stu-id="11e8a-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="11e8a-120">ランタイムは、従来の CAS ポリシーを使用します。</span><span class="sxs-lookup"><span data-stu-id="11e8a-120">The runtime uses legacy CAS policy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11e8a-121">子要素</span><span class="sxs-lookup"><span data-stu-id="11e8a-121">Child Elements</span></span>  
 <span data-ttu-id="11e8a-122">なし。</span><span class="sxs-lookup"><span data-stu-id="11e8a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="11e8a-123">親要素</span><span class="sxs-lookup"><span data-stu-id="11e8a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="11e8a-124">要素</span><span class="sxs-lookup"><span data-stu-id="11e8a-124">Element</span></span>|<span data-ttu-id="11e8a-125">説明</span><span class="sxs-lookup"><span data-stu-id="11e8a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="11e8a-126">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="11e8a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="11e8a-127">ランタイム初期化オプションに関する情報を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="11e8a-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11e8a-128">コメント</span><span class="sxs-lookup"><span data-stu-id="11e8a-128">Remarks</span></span>  
 <span data-ttu-id="11e8a-129">.NET Framework バージョン 3.5 と以前のバージョンでは、CAS ポリシーは常に有効にします。</span><span class="sxs-lookup"><span data-stu-id="11e8a-129">In the .NET Framework version 3.5 and earlier versions, CAS policy is always in effect.</span></span> <span data-ttu-id="11e8a-130">[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、CAS ポリシーを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="11e8a-130">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], CAS policy must be enabled.</span></span>  
  
 <span data-ttu-id="11e8a-131">CAS ポリシーは、バージョン固有です。</span><span class="sxs-lookup"><span data-stu-id="11e8a-131">CAS policy is version-specific.</span></span> <span data-ttu-id="11e8a-132">.NET Framework の以前のバージョンに存在するカスタムの CAS ポリシーを再度指定する必要があります、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="11e8a-132">Custom CAS policies that exist in earlier versions of the .NET Framework must be respecified in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="11e8a-133">適用する、`<NetFx40_LegacySecurityPolicy>`要素を[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]アセンブリには影響しません[セキュリティ透過的なコード](../../../../../docs/framework/misc/security-transparent-code.md); 透過性規則を引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="11e8a-133">Applying the `<NetFx40_LegacySecurityPolicy>` element to a [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] assembly does not affect [security-transparent code](../../../../../docs/framework/misc/security-transparent-code.md); the transparency rules still apply.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="11e8a-134">適用する、`<NetFx40_LegacySecurityPolicy>`要素につながる重大なパフォーマンスの低下によって作成されたネイティブ イメージ アセンブリを[ネイティブ イメージ ジェネレーター (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md)でインストールされていない、[グローバル アセンブリ キャッシュ](../../../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="11e8a-134">Applying the `<NetFx40_LegacySecurityPolicy>` element can result in significant performance penalties for native image assemblies created by the [Native Image Generator (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) that are not installed in the [global assembly cache](../../../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="11e8a-135">ランタイムの機能を利用し、できないに属性が適用されるときに、ネイティブ イメージとして、アセンブリを読み込むことが原因でパフォーマンスの低下が発生、結果的に読み込まれたと - just-in-time アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="11e8a-135">The performance degradation is caused by the inability of the runtime to load the assemblies as native images when the attribute is applied, resulting in their being loaded as just-in-time assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11e8a-136">ターゲット .NET Framework のバージョンよりも前に指定するかどうか、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]プロジェクトには、Visual Studio プロジェクト用の設定が、CAS ポリシーが有効になります、そのバージョンの指定したカスタムの CAS ポリシーを含むです。</span><span class="sxs-lookup"><span data-stu-id="11e8a-136">If you specify a target .NET Framework version that is earlier than the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in the project settings for your Visual Studio project, CAS policy will be enabled, including any custom CAS policies you specified for that version.</span></span> <span data-ttu-id="11e8a-137">ただし、することはできません new を使用する[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]型およびメンバー。</span><span class="sxs-lookup"><span data-stu-id="11e8a-137">However, you will not be able to use new [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] types and members.</span></span> <span data-ttu-id="11e8a-138">使用して、.NET Framework の以前のバージョンを指定することも、 [ \<supportedRuntime > 要素](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)でスタートアップ設定スキーマで、[アプリケーション構成ファイル](../../../../../docs/framework/configure-apps/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="11e8a-138">You can also specify an earlier version of the .NET Framework by using the [\<supportedRuntime> element](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) in the startup settings schema in your [application configuration file](../../../../../docs/framework/configure-apps/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11e8a-139">構成ファイルの構文は、大文字小文字を区別します。</span><span class="sxs-lookup"><span data-stu-id="11e8a-139">Configuration file syntax is case-sensitive.</span></span> <span data-ttu-id="11e8a-140">構文と例のセクションに示されている構文を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11e8a-140">You should use the syntax as provided in the Syntax and Example sections.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="11e8a-141">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="11e8a-141">Configuration File</span></span>  
 <span data-ttu-id="11e8a-142">この要素は、アプリケーション構成ファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="11e8a-142">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11e8a-143">例</span><span class="sxs-lookup"><span data-stu-id="11e8a-143">Example</span></span>  
 <span data-ttu-id="11e8a-144">次の例では、アプリケーションのレガシーの CAS ポリシーを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="11e8a-144">The following example shows how to enable legacy CAS policy for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11e8a-145">参照</span><span class="sxs-lookup"><span data-stu-id="11e8a-145">See Also</span></span>  
 [<span data-ttu-id="11e8a-146">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="11e8a-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="11e8a-147">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="11e8a-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
