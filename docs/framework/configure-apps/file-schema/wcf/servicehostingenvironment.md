---
title: '&lt;serviceHostingEnvironment&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5770cb8fd68eb68145f3f7fbcf197302883efe9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicehostingenvironmentgt"></a><span data-ttu-id="d7d21-102">&lt;serviceHostingEnvironment&gt;</span><span class="sxs-lookup"><span data-stu-id="d7d21-102">&lt;serviceHostingEnvironment&gt;</span></span>
<span data-ttu-id="d7d21-103">この要素は、環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。</span><span class="sxs-lookup"><span data-stu-id="d7d21-103">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="d7d21-104">この要素が空の場合は、既定の型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-104">If this element is empty, the default type is used.</span></span> <span data-ttu-id="d7d21-105">この要素は、アプリケーション レベルまたはコンピューター レベルの構成ファイルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-105">This element can only be used at the application or machine level configuration files.</span></span>  
  
 <span data-ttu-id="d7d21-106">\<システムです。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d7d21-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="d7d21-107">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="d7d21-107">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7d21-108">構文</span><span class="sxs-lookup"><span data-stu-id="d7d21-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean" 
                           minFreeMemoryPercentageToActivateService="Integer" 
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String" service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String" transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7d21-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d7d21-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d7d21-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7d21-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7d21-111">属性</span><span class="sxs-lookup"><span data-stu-id="d7d21-111">Attributes</span></span>  
  
|<span data-ttu-id="d7d21-112">属性</span><span class="sxs-lookup"><span data-stu-id="d7d21-112">Attribute</span></span>|<span data-ttu-id="d7d21-113">説明</span><span class="sxs-lookup"><span data-stu-id="d7d21-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7d21-114">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="d7d21-114">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="d7d21-115">ASP.NET の互換モードが現在のアプリケーションに対して有効になっているかどうかを示すブール値。</span><span class="sxs-lookup"><span data-stu-id="d7d21-115">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="d7d21-116">既定値は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="d7d21-116">The default is `false`.</span></span><br /><br /> <span data-ttu-id="d7d21-117">この属性が `true` に設定されている場合、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスに対する要求は ASP.NET HTTP パイプラインを通過し、HTTP プロトコル以外を介した通信は禁止されます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-117">When this attribute is set to `true`, requests to [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="d7d21-118">詳細については、次を参照してください。 [WCF サービスと ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)です。</span><span class="sxs-lookup"><span data-stu-id="d7d21-118">For more information, see [WCF Services and ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="d7d21-119">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="d7d21-119">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="d7d21-120">[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスをアクティブにする前に、システムに必要な最小限の空きメモリの容量を指定する整数。</span><span class="sxs-lookup"><span data-stu-id="d7d21-120">An integer that specifies the minimum amount of free memory that should be available to the system, before a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service can be activated.</span></span> <span data-ttu-id="d7d21-121">**注意:**の web.config ファイルで、部分信頼と共にこの属性を指定する、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]サービスになります、<xref:System.Security.SecurityException>サービスを実行するとします。</span><span class="sxs-lookup"><span data-stu-id="d7d21-121">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="d7d21-122">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="d7d21-122">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="d7d21-123">1 つのサイトで複数の IIS バインディングが有効になっているかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="d7d21-123">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="d7d21-124">IIS は、仮想ディレクトリを含む仮想アプリケーションのコンテナーとしての Web サイトで構成されています。</span><span class="sxs-lookup"><span data-stu-id="d7d21-124">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="d7d21-125">サイト内のアプリケーションに、1 つ以上の IIS バインディングからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-125">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="d7d21-126">IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d7d21-126">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="d7d21-127">バインディング プロトコルは通信を行うスキームを定義するもので、バインディング情報はサイトにアクセスするために使用する情報です。</span><span class="sxs-lookup"><span data-stu-id="d7d21-127">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="d7d21-128">バインディング プロトコルの例には HTTP があり、一方、バインディング情報には IP アドレス、ポート、ホスト ヘッダーなどを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-128">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="d7d21-129">IIS ではサイトごとに複数の IIS バインディングを指定でき、これによりスキームごとに複数のベース アドレスをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-129">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="d7d21-130">ただし、サイトでホストされている [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスでは、1 つのスキームあたり 1 つのみの baseAddress へのバインディングが許可されています。</span><span class="sxs-lookup"><span data-stu-id="d7d21-130">However, a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="d7d21-131">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスに対し、1 つのサイトで複数の IIS バインディングを有効にするには、この属性を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d7d21-131">To enable multiple IIS bindings per site for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service, set this attribute to `true`.</span></span> <span data-ttu-id="d7d21-132">複数のサイト バインディングは HTTP プロトコルに対してのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d7d21-132">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="d7d21-133">構成ファイル内のエンドポイントのアドレスには完全な URI を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7d21-133">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7d21-134">子要素</span><span class="sxs-lookup"><span data-stu-id="d7d21-134">Child Elements</span></span>  
  
|<span data-ttu-id="d7d21-135">要素</span><span class="sxs-lookup"><span data-stu-id="d7d21-135">Element</span></span>|<span data-ttu-id="d7d21-136">説明</span><span class="sxs-lookup"><span data-stu-id="d7d21-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7d21-137">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="d7d21-137">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="d7d21-138">サービス ホストによって使用されるベース アドレスのプレフィックス フィルターを指定する構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="d7d21-138">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="d7d21-139">\<serviceActivations ></span><span class="sxs-lookup"><span data-stu-id="d7d21-139">\<serviceActivations></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|<span data-ttu-id="d7d21-140">アクティベーション設定を記述する構成セクション。</span><span class="sxs-lookup"><span data-stu-id="d7d21-140">A configuration section that describes activation settings.</span></span>|  
|[<span data-ttu-id="d7d21-141">\<transportConfigurationTypes ></span><span class="sxs-lookup"><span data-stu-id="d7d21-141">\<transportConfigurationTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|<span data-ttu-id="d7d21-142">特定のトランスポートの型を識別する構成要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="d7d21-142">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7d21-143">親要素</span><span class="sxs-lookup"><span data-stu-id="d7d21-143">Parent Elements</span></span>  
  
|<span data-ttu-id="d7d21-144">要素</span><span class="sxs-lookup"><span data-stu-id="d7d21-144">Element</span></span>|<span data-ttu-id="d7d21-145">説明</span><span class="sxs-lookup"><span data-stu-id="d7d21-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7d21-146">serviceModel</span><span class="sxs-lookup"><span data-stu-id="d7d21-146">serviceModel</span></span>|<span data-ttu-id="d7d21-147">すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。</span><span class="sxs-lookup"><span data-stu-id="d7d21-147">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7d21-148">コメント</span><span class="sxs-lookup"><span data-stu-id="d7d21-148">Remarks</span></span>  
 <span data-ttu-id="d7d21-149">既定では、WCF サービスは、ホストされるアプリケーション ドメイン (AppDomain) で ASP.NET と並行で実行します。</span><span class="sxs-lookup"><span data-stu-id="d7d21-149">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="d7d21-150">WCF と ASP.NET が同じ AppDomain で共存できても、既定では WCF 要求は ASP.NET HTTP パイプラインでは処理されません。</span><span class="sxs-lookup"><span data-stu-id="d7d21-150">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="d7d21-151">結果として、ASP.NET アプリケーション プラットフォームのいくつかの要素は、WCF サービスでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="d7d21-151">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="d7d21-152">これらの要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d7d21-152">These include</span></span>  
  
-   <span data-ttu-id="d7d21-153">ASP.NET ファイル/URL 承認</span><span class="sxs-lookup"><span data-stu-id="d7d21-153">ASP.NET File/URL Authorization</span></span>  
  
-   <span data-ttu-id="d7d21-154">ASP.NET の偽装</span><span class="sxs-lookup"><span data-stu-id="d7d21-154">ASP.NET Impersonation</span></span>  
  
-   <span data-ttu-id="d7d21-155">クッキー ベースのセッションの状態</span><span class="sxs-lookup"><span data-stu-id="d7d21-155">Cookie-based Session State</span></span>  
  
-   <span data-ttu-id="d7d21-156">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="d7d21-156">HttpContext.Current</span></span>  
  
-   <span data-ttu-id="d7d21-157">カスタム HttpModule を経由するパイプライン拡張</span><span class="sxs-lookup"><span data-stu-id="d7d21-157">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="d7d21-158">WCF サービスが ASP.NET のコンテキストで機能し、HTTP 経由でのみ通信する必要がある場合は、WCF の ASP.NET 互換モードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-158">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="d7d21-159">このモードは、`aspNetCompatibilityEnabled` 属性がアプリケーション レベルで `true` に設定されている場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="d7d21-159">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="d7d21-160">サービス実装では、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> クラスを使用して互換モードで実行できる機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d7d21-160">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="d7d21-161">互換モードが有効な場合、</span><span class="sxs-lookup"><span data-stu-id="d7d21-161">When the compatibility mode is enabled,</span></span>  
  
-   <span data-ttu-id="d7d21-162">ASP.NET ファイル/URL 承認が、WCF 承認の前に強制的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-162">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="d7d21-163">承認決定は、要求のトランスポート レベルの ID に基づいています。</span><span class="sxs-lookup"><span data-stu-id="d7d21-163">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="d7d21-164">メッセージ レベルでの ID は、無視されます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-164">Identities at the message level are ignored.</span></span>  
  
-   <span data-ttu-id="d7d21-165">WCF サービス操作は、ASP.NET の偽装コンテキストで実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="d7d21-165">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="d7d21-166">ASP.NET の偽装と WCF の偽装の両方が特定のサービスで有効な場合は、WCF の偽装コンテキストが適用されます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-166">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
-   <span data-ttu-id="d7d21-167">HttpContext.Current を WCF サービス コードから使用できるため、サービスは非 HTTP エンドポイントを公開しません。</span><span class="sxs-lookup"><span data-stu-id="d7d21-167">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
-   <span data-ttu-id="d7d21-168">WCF 要求は、ASP.NET パイプラインによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-168">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="d7d21-169">受信要求を処理するように構成された HttpModules は、WCF 要求も処理できます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-169">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="d7d21-170">これらには、ASP.NET プラットフォーム コンポーネント (<xref:System.Web.SessionState.SessionStateModule> など) とカスタム サードパーティ モジュールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d7d21-170">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7d21-171">例</span><span class="sxs-lookup"><span data-stu-id="d7d21-171">Example</span></span>  
 <span data-ttu-id="d7d21-172">次のコード サンプルは、ASP 互換モードを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d7d21-172">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="d7d21-173">コード</span><span class="sxs-lookup"><span data-stu-id="d7d21-173">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7d21-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7d21-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="d7d21-175">ホスティング</span><span class="sxs-lookup"><span data-stu-id="d7d21-175">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [<span data-ttu-id="d7d21-176">WCF サービスと ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d7d21-176">WCF Services and ASP.NET</span></span>](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
