---
title: '&lt;disableFusionUpdatesFromADManager&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8e5e33cd3d250b26f0a83a87c4f7ce438af22e96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745891"
---
# <a name="ltdisablefusionupdatesfromadmanagergt-element"></a><span data-ttu-id="7f74b-102">&lt;disableFusionUpdatesFromADManager&gt;要素</span><span class="sxs-lookup"><span data-stu-id="7f74b-102">&lt;disableFusionUpdatesFromADManager&gt; Element</span></span>
<span data-ttu-id="7f74b-103">アプリケーション ドメインの構成設定をランタイム ホストが上書きする既定の動作を無効化するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f74b-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
 <span data-ttu-id="7f74b-104">\<configuration > 要素</span><span class="sxs-lookup"><span data-stu-id="7f74b-104">\<configuration> Element</span></span>  
<span data-ttu-id="7f74b-105">\<ランタイム > 要素</span><span class="sxs-lookup"><span data-stu-id="7f74b-105">\<runtime> Element</span></span>  
<span data-ttu-id="7f74b-106">\<disableFusionUpdatesFromADManager ></span><span class="sxs-lookup"><span data-stu-id="7f74b-106">\<disableFusionUpdatesFromADManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f74b-107">構文</span><span class="sxs-lookup"><span data-stu-id="7f74b-107">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f74b-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7f74b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7f74b-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7f74b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f74b-110">属性</span><span class="sxs-lookup"><span data-stu-id="7f74b-110">Attributes</span></span>  
  
|<span data-ttu-id="7f74b-111">属性</span><span class="sxs-lookup"><span data-stu-id="7f74b-111">Attribute</span></span>|<span data-ttu-id="7f74b-112">説明</span><span class="sxs-lookup"><span data-stu-id="7f74b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f74b-113">enabled</span><span class="sxs-lookup"><span data-stu-id="7f74b-113">enabled</span></span>|<span data-ttu-id="7f74b-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="7f74b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="7f74b-115">Fusion の設定を上書きする既定の機能が無効になっているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="7f74b-115">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7f74b-116">enabled 属性</span><span class="sxs-lookup"><span data-stu-id="7f74b-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="7f74b-117">値</span><span class="sxs-lookup"><span data-stu-id="7f74b-117">Value</span></span>|<span data-ttu-id="7f74b-118">説明</span><span class="sxs-lookup"><span data-stu-id="7f74b-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7f74b-119">0</span><span class="sxs-lookup"><span data-stu-id="7f74b-119">0</span></span>|<span data-ttu-id="7f74b-120">Fusion の設定を上書きする機能を無効にしないでください。</span><span class="sxs-lookup"><span data-stu-id="7f74b-120">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="7f74b-121">これは、以降で、既定の動作、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="7f74b-121">This is the default behavior, starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
|<span data-ttu-id="7f74b-122">1</span><span class="sxs-lookup"><span data-stu-id="7f74b-122">1</span></span>|<span data-ttu-id="7f74b-123">Fusion の設定を上書きする機能を無効にします。</span><span class="sxs-lookup"><span data-stu-id="7f74b-123">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="7f74b-124">これは、.NET Framework の以前のバージョンの動作に戻ります。</span><span class="sxs-lookup"><span data-stu-id="7f74b-124">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f74b-125">子要素</span><span class="sxs-lookup"><span data-stu-id="7f74b-125">Child Elements</span></span>  
 <span data-ttu-id="7f74b-126">なし。</span><span class="sxs-lookup"><span data-stu-id="7f74b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f74b-127">親要素</span><span class="sxs-lookup"><span data-stu-id="7f74b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7f74b-128">要素</span><span class="sxs-lookup"><span data-stu-id="7f74b-128">Element</span></span>|<span data-ttu-id="7f74b-129">説明</span><span class="sxs-lookup"><span data-stu-id="7f74b-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7f74b-130">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="7f74b-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7f74b-131">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f74b-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f74b-132">コメント</span><span class="sxs-lookup"><span data-stu-id="7f74b-132">Remarks</span></span>  
 <span data-ttu-id="7f74b-133">以降で、 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、既定の動作を許可するのには、<xref:System.AppDomainManager>を使用して構成設定を上書きするオブジェクト、<xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティまたは<xref:System.AppDomainSetup.SetConfigurationBytes%2A>のメソッド、<xref:System.AppDomainSetup>実装に渡されるオブジェクト<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>のサブクラス内のメソッド<xref:System.AppDomainManager>です。</span><span class="sxs-lookup"><span data-stu-id="7f74b-133">Starting with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="7f74b-134">既定のアプリケーション ドメインは、変更する設定は、アプリケーション構成ファイルで指定した設定を上書きします。</span><span class="sxs-lookup"><span data-stu-id="7f74b-134">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="7f74b-135">渡された構成設定が上書きの他のアプリケーション ドメイン、<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>または<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7f74b-135">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="7f74b-136">新しい構成情報を渡すか、null を渡します (`Nothing` Visual Basic で) で渡された構成情報を削除します。</span><span class="sxs-lookup"><span data-stu-id="7f74b-136">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="7f74b-137">両方に構成情報を渡さないでください、<xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティおよび<xref:System.AppDomainSetup.SetConfigurationBytes%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7f74b-137">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="7f74b-138">両方に構成情報を渡す場合、情報を渡す、<xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティが無視されるため、<xref:System.AppDomainSetup.SetConfigurationBytes%2A>メソッドは、アプリケーション構成ファイルから構成情報をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="7f74b-138">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="7f74b-139">使用する場合、<xref:System.AppDomainSetup.ConfigurationFile%2A>プロパティが null を渡す (`Nothing` Visual Basic で) に、<xref:System.AppDomainSetup.SetConfigurationBytes%2A>への呼び出しで指定された構成バイトを取り除く方法、<xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType>または<xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7f74b-139">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="7f74b-140">次の設定を変更する構成情報に加えて、<xref:System.AppDomainSetup>の実装に渡されるオブジェクト、<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>メソッド: <xref:System.AppDomainSetup.ApplicationBase%2A>、 <xref:System.AppDomainSetup.ApplicationName%2A>、 <xref:System.AppDomainSetup.CachePath%2A>、 <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>、 <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>、 <xref:System.AppDomainSetup.DisallowCodeDownload%2A>、 <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>、 <xref:System.AppDomainSetup.DynamicBase%2A>、 <xref:System.AppDomainSetup.LoaderOptimization%2A>、 <xref:System.AppDomainSetup.PrivateBinPath%2A>、 <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>、 <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>、および<xref:System.AppDomainSetup.ShadowCopyFiles%2A>です。</span><span class="sxs-lookup"><span data-stu-id="7f74b-140">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="7f74b-141">使用する代わりに、`<disableFusionUpdatesFromADManager>`要素、ことができますを無効にする既定の動作または環境変数を設定して、レジストリ設定を作成します。</span><span class="sxs-lookup"><span data-stu-id="7f74b-141">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="7f74b-142">レジストリで、という名前の DWORD 値を作成する`COMPLUS_disableFusionUpdatesFromADManager``HKCU\Software\Microsoft\.NETFramework`または`HKLM\Software\Microsoft\.NETFramework`、し、値を 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="7f74b-142">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="7f74b-143">環境変数を設定、コマンドラインで`COMPLUS_disableFusionUpdatesFromADManager`を 1 にします。</span><span class="sxs-lookup"><span data-stu-id="7f74b-143">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f74b-144">例</span><span class="sxs-lookup"><span data-stu-id="7f74b-144">Example</span></span>  
 <span data-ttu-id="7f74b-145">次の例を使用して Fusion の設定を上書きする機能を無効にする方法を示しています、`<disableFusionUpdatesFromADManager>`要素。</span><span class="sxs-lookup"><span data-stu-id="7f74b-145">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f74b-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f74b-146">See Also</span></span>  
 [<span data-ttu-id="7f74b-147">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="7f74b-147">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="7f74b-148">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="7f74b-148">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="7f74b-149">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="7f74b-149">How the Runtime Locates Assemblies</span></span>](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
