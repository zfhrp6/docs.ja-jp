---
title: "構成ファイルを使用してサービスを構成する方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11229a5677341db05223116c932f13b1f567e712
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="9b885-102">構成ファイルを使用してサービスを構成する方法</span><span class="sxs-lookup"><span data-stu-id="9b885-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="9b885-103">構成ファイルを使用して [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスを構成すると、デザイン時ではなく配置時にエンドポイントとサービス動作のデータを指定できるという柔軟性が生まれます。</span><span class="sxs-lookup"><span data-stu-id="9b885-103">Configuring a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="9b885-104">ここでは使用可能な主要な技術について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b885-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="9b885-105">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスは、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の構成技術を使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-105">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service is configurable using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] configuration technology.</span></span> <span data-ttu-id="9b885-106">通常、XML 要素は、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスをホストするインターネット インフォメーション サービス (IIS) サイトの Web.config ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="9b885-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="9b885-107">この要素によって、コンピューターごとにエンドポイント アドレス (サービスと通信するために使用する実際のアドレス) などの詳細情報を変更できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="9b885-108">また、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] には、システム指定の要素がいくつか用意されており、これらの要素によって、サービスの最も基本的な機能を簡単に選択できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-108">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="9b885-109">[!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]以降では、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] には、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 構成要件を簡略化する新しい既定の構成モデルが付属しています。</span><span class="sxs-lookup"><span data-stu-id="9b885-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] comes with a new default configuration model that simplifies [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration requirements.</span></span> <span data-ttu-id="9b885-110">特定のサービスに対し [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 構成を指定しないと、ランタイムは自動的にいくつかの標準エンドポイントおよびバインディング/動作でサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="9b885-110">If you do not provide any [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="9b885-111">実際、 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションのプログラミングにおいては、構成ファイルの記述が作業の大きな部分を占めます。</span><span class="sxs-lookup"><span data-stu-id="9b885-111">In practice, writing configuration is a major part of programming [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications.</span></span>  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="9b885-112">[のサービスのバインドを構成する](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b885-112"> [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> [!INCLUDE[crlist](../../../includes/crlist-md.md)]<span data-ttu-id="9b885-113"> については、「 [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="9b885-113"> of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9b885-114"> については、「 [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) 」および「 [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9b885-114"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b885-115">2 つの異なるバージョンのサービスが配置される side-by-side のシナリオを配置する場合、構成ファイルで参照されるアセンブリの部分名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b885-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="9b885-116">これは構成ファイルがすべてのバージョンのサービスで共有されて、異なるバージョンの .NET Framework で実行される可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="9b885-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="9b885-117">System.Configuration: Web.config と App.config</span><span class="sxs-lookup"><span data-stu-id="9b885-117">System.Configuration: Web.config and App.config</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="9b885-118"> では、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]の System.Configuration 構成システムを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b885-118"> uses the System.Configuration configuration system of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="9b885-119">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]でサービスを構成するとき、Web.config ファイルまたは App.config ファイルのいずれかを使用して、設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b885-119">When configuring a service in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="9b885-120">選択する構成ファイル名は、サービスに選択したホスト環境によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9b885-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="9b885-121">サービスのホストに IIS を使用している場合は、Web.config ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b885-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="9b885-122">他のホスト環境を使用している場合、App.config ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b885-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="9b885-123">[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]では、App.config という名前のファイルを使用して、最終の構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9b885-123">In [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="9b885-124">構成で実際に使用される最終的な名前は、アセンブリ名によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9b885-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="9b885-125">たとえば、アセンブリ名が "Cohowinery.exe" の場合、最終の構成ファイルの名前は "Cohowinery.exe.config" になります。</span><span class="sxs-lookup"><span data-stu-id="9b885-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="9b885-126">ただし、変更する必要があるのは App.config ファイルだけです。</span><span class="sxs-lookup"><span data-stu-id="9b885-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="9b885-127">このファイルで行った変更は、コンパイル時に自動的に最終のアプリケーション構成ファイルに反映されます。</span><span class="sxs-lookup"><span data-stu-id="9b885-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="9b885-128">App.config ファイルを使用しているとき、アプリケーションが開始され、構成が適用されると、構成システムは App.config ファイルを Machine.config ファイルの内容とマージします。</span><span class="sxs-lookup"><span data-stu-id="9b885-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="9b885-129">このしくみによって、Machine.config ファイルにはコンピューター全体の設定を定義できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="9b885-130">App.config ファイルは、Machine.config ファイルの設定をオーバーライドするために使用できます。また、Machine.config ファイルにある設定をロックしてこの設定が使用されるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9b885-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="9b885-131">Web.config の場合、構成システムは、アプリケーション ディレクトリまでのすべてのディレクトリにある Web.config ファイルを、適用される構成にマージします。</span><span class="sxs-lookup"><span data-stu-id="9b885-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="9b885-132">構成と設定の優先順位[!INCLUDE[crabout](../../../includes/crabout-md.md)] 、 <xref:System.Configuration> 名前空間のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b885-132">[!INCLUDE[crabout](../../../includes/crabout-md.md)] configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="9b885-133">構成ファイルの主要セクション</span><span class="sxs-lookup"><span data-stu-id="9b885-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="9b885-134">構成ファイルの主要セクションには、次の要素があります。</span><span class="sxs-lookup"><span data-stu-id="9b885-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!—- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
>  <span data-ttu-id="9b885-135">バインディングと動作のセクションは省略可能であり、必要な場合のみ追加されます。</span><span class="sxs-lookup"><span data-stu-id="9b885-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="9b885-136">\<Services > 要素</span><span class="sxs-lookup"><span data-stu-id="9b885-136">The \<services> Element</span></span>  
 <span data-ttu-id="9b885-137">`services` 要素には、アプリケーションによってホストされるすべてのサービスの仕様が入ります。</span><span class="sxs-lookup"><span data-stu-id="9b885-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="9b885-138">[!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]の簡略化された構成モデル以降の場合、このセクションは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="9b885-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="9b885-139">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="9b885-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="9b885-140">\<Service > 要素</span><span class="sxs-lookup"><span data-stu-id="9b885-140">The \<service> Element</span></span>  
 <span data-ttu-id="9b885-141">各サービスには次の属性があります。</span><span class="sxs-lookup"><span data-stu-id="9b885-141">Each service has these attributes:</span></span>  
  
-   <span data-ttu-id="9b885-142">`name`。</span><span class="sxs-lookup"><span data-stu-id="9b885-142">`name`.</span></span> <span data-ttu-id="9b885-143">- サービス コントラクトの実装を提供する型を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b885-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="9b885-144">これは、名前空間、期間、および型名を構成する完全修飾名です。</span><span class="sxs-lookup"><span data-stu-id="9b885-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="9b885-145">たとえば、 `"MyNameSpace.myServiceType"`などです。</span><span class="sxs-lookup"><span data-stu-id="9b885-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
-   <span data-ttu-id="9b885-146">`behaviorConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="9b885-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="9b885-147">- `behavior` 要素に存在するいずれかの `behaviors` 要素の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b885-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="9b885-148">指定された動作は、サービスが偽装を許可するかどうかなどのアクションを制御します。</span><span class="sxs-lookup"><span data-stu-id="9b885-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="9b885-149">その値が空の名前であるか、または `behaviorConfiguration` が指定されていない場合、サービスの動作の既定のセットがサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="9b885-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
-   [<span data-ttu-id="9b885-150">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="9b885-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="9b885-151">\<Endpoint > 要素</span><span class="sxs-lookup"><span data-stu-id="9b885-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="9b885-152">各エンドポイントには、次の属性で表されるアドレス、バインディング、およびコントラクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="9b885-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
-   <span data-ttu-id="9b885-153">`address`。</span><span class="sxs-lookup"><span data-stu-id="9b885-153">`address`.</span></span> <span data-ttu-id="9b885-154">サービスの URI (Uniform Resource Identifier) を指定します。絶対アドレスまたはサービスのベース アドレスからの相対アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="9b885-155">空の文字列を設定した場合、サービスの <xref:System.ServiceModel.ServiceHost> を作成するときに指定したベース アドレスでエンドポイントを使用できることを示します。</span><span class="sxs-lookup"><span data-stu-id="9b885-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
-   <span data-ttu-id="9b885-156">`binding`。</span><span class="sxs-lookup"><span data-stu-id="9b885-156">`binding`.</span></span> <span data-ttu-id="9b885-157">- 通常、 <xref:System.ServiceModel.WSHttpBinding>などのシステム指定のバインディングを指定しますが、ユーザー定義バインディングを指定することも可能です。</span><span class="sxs-lookup"><span data-stu-id="9b885-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="9b885-158">指定するバインディングによって、トランスポートの種類、使用するセキュリティとエンコーディング、および信頼できるセッション、トランザクション、またはストリーミングがサポートされるかどうか、または有効かどうかが決まります。</span><span class="sxs-lookup"><span data-stu-id="9b885-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
-   <span data-ttu-id="9b885-159">`bindingConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="9b885-159">`bindingConfiguration`.</span></span> <span data-ttu-id="9b885-160">バインディングの既定値を変更する必要がある場合、 `binding` 要素の該当する `bindings` 要素を構成することによって変更できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="9b885-161">この属性には、既定値の変更に使用される `name` 要素の `binding` 属性と同じ値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b885-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="9b885-162">名前を指定しない場合、またはバインディングに `bindingConfiguration` を指定しない場合、バインディングの種類の既定のバインディングは、エンドポイントで使用されます。</span><span class="sxs-lookup"><span data-stu-id="9b885-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
-   <span data-ttu-id="9b885-163">`contract`。</span><span class="sxs-lookup"><span data-stu-id="9b885-163">`contract`.</span></span> <span data-ttu-id="9b885-164">コントラクトを定義するインターフェイスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9b885-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="9b885-165">これは `name` 要素の `service` 属性で指定された共通言語ランタイム (CLR) 型で実装されたインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="9b885-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
-   [<span data-ttu-id="9b885-166">\<endpoint > 要素のリファレンス</span><span class="sxs-lookup"><span data-stu-id="9b885-166">\<endpoint> element reference</span></span>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="9b885-167">\<バインド > 要素</span><span class="sxs-lookup"><span data-stu-id="9b885-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="9b885-168">`bindings` 要素には、任意のサービスで定義される任意のエンドポイントによって使用できるすべてのバインディングに関する仕様が入ります。</span><span class="sxs-lookup"><span data-stu-id="9b885-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="9b885-169">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9b885-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="9b885-170">\<バインディング > 要素</span><span class="sxs-lookup"><span data-stu-id="9b885-170">The \<binding> Element</span></span>  
 <span data-ttu-id="9b885-171">`binding`に含まれる要素の`bindings`要素は、システム指定のバインディングのいずれかを指定できます (を参照してください[システム指定のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)) またはカスタム バインディング (を参照してください[カスタム バインド](../../../docs/framework/wcf/extending/custom-bindings.md))。</span><span class="sxs-lookup"><span data-stu-id="9b885-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="9b885-172">`binding` 要素には、バインディングを `name` 要素の `bindingConfiguration` 属性で指定されたエンドポイントと関連付ける `endpoint` 属性があります。</span><span class="sxs-lookup"><span data-stu-id="9b885-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="9b885-173">名前を指定しない場合、バインディングは、バインディングの既定の種類に対応します。</span><span class="sxs-lookup"><span data-stu-id="9b885-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9b885-174"> については、「 [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)。</span><span class="sxs-lookup"><span data-stu-id="9b885-174"> configuring services and clients, see [Configuring Windows Communication Foundation Applications](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).</span></span>  
  
 [<span data-ttu-id="9b885-175">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9b885-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="9b885-176">\<動作 > 要素</span><span class="sxs-lookup"><span data-stu-id="9b885-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="9b885-177">これは、サービスの動作を定義する `behavior` 要素のコンテナー要素です。</span><span class="sxs-lookup"><span data-stu-id="9b885-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="9b885-178">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="9b885-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="9b885-179">\<動作 > 要素</span><span class="sxs-lookup"><span data-stu-id="9b885-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="9b885-180">各 `behavior` 要素は、`name` 属性によって識別され、<`throttling`> などのシステム指定の動作またはカスタム動作のいずれかを定義します。</span><span class="sxs-lookup"><span data-stu-id="9b885-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="9b885-181">名前を指定しない場合、動作要素は、既定のサービスまたはエンドポイント動作に対応します。</span><span class="sxs-lookup"><span data-stu-id="9b885-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="9b885-182">\<動作 ></span><span class="sxs-lookup"><span data-stu-id="9b885-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="9b885-183">バインディングと動作の構成を使用する方法</span><span class="sxs-lookup"><span data-stu-id="9b885-183">How to Use Binding and Behavior Configurations</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="9b885-184"> では、構成で参照システムを使用することによって、エンドポイント間で構成を簡単に共有できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-184"> makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="9b885-185">構成値を直接エンドポイントに割り当てるのではなく、バインディング関連の構成値を `bindingConfiguration` セクションの `<binding>` 要素にグループ化します。</span><span class="sxs-lookup"><span data-stu-id="9b885-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="9b885-186">バインディング構成とは、バインディングの設定の名前付きグループです。</span><span class="sxs-lookup"><span data-stu-id="9b885-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="9b885-187">エンドポイントは、名前によって `bindingConfiguration` を参照できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!—- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="9b885-188">`name` の `bindingConfiguration` は、 `<binding>` 要素で設定します。</span><span class="sxs-lookup"><span data-stu-id="9b885-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="9b885-189">`name`バインドの種類のスコープ内で一意の文字列にする必要があります: ここでは、 [< basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、または空の値を既定のバインディングを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b885-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="9b885-190">エンドポイントは、 `bindingConfiguration` 属性をこの文字列に設定することによって構成にリンクします。</span><span class="sxs-lookup"><span data-stu-id="9b885-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="9b885-191">`behaviorConfiguration` は、次のサンプルに示すように、同じ方法で実装されます。</span><span class="sxs-lookup"><span data-stu-id="9b885-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="9b885-192">サービスの動作の既定のセットは、サービスに追加されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b885-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="9b885-193">このシステムでは、設定を再定義することなく、エンドポイント間で共通の構成を共有できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="9b885-194">コンピューター全体のスコープが必要な場合は、バインディングまたは動作の構成を Machine.config に作成します。構成設定は、すべての App.config ファイルで操作できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="9b885-195">[Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) を使用すると、構成を簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="9b885-196">動作のマージ</span><span class="sxs-lookup"><span data-stu-id="9b885-196">Behavior Merge</span></span>  
 <span data-ttu-id="9b885-197">動作のマージ機能を使用すると、共通動作のセットを常に使用する場合に動作の管理が容易になります。</span><span class="sxs-lookup"><span data-stu-id="9b885-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="9b885-198">この機能では、さまざまなレベルの構成階層で動作を指定し、サービスが複数レベルの構成階層から動作を継承することができます。</span><span class="sxs-lookup"><span data-stu-id="9b885-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="9b885-199">このしくみを説明するため、IIS に次の仮想ディレクトリ レイアウトが存在するとします。</span><span class="sxs-lookup"><span data-stu-id="9b885-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 <span data-ttu-id="9b885-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span><span class="sxs-lookup"><span data-stu-id="9b885-200">~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc</span></span>  
  
 <span data-ttu-id="9b885-201">また ~\Web.config ファイルに次の内容が含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="9b885-201">And your ~\Web.config file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="9b885-202">さらに ~\Child\Web.config にある子 Web.config に次の内容が含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="9b885-202">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="9b885-203">~\Child\Service.svc にあるサービスは、serviceDebug 動作と serviceMetadata 動作の両方を持つ場合と同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="9b885-203">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="9b885-204">~\Service.svc にあるサービスは、serviceDebug 動作のみを持ちます。</span><span class="sxs-lookup"><span data-stu-id="9b885-204">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="9b885-205">これによって、同じ名前の 2 つの動作コレクション (この例では空の文字列) がマージされます。</span><span class="sxs-lookup"><span data-stu-id="9b885-205">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="9b885-206">使用して、動作コレクションをクリアすることも、\<オフ > タグを使用してコレクションから個々 の動作を削除、\<削除 > タグです。</span><span class="sxs-lookup"><span data-stu-id="9b885-206">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="9b885-207">たとえば、次の 2 つの構成は serviceMetadata 動作のみを持つ子サービスになります。</span><span class="sxs-lookup"><span data-stu-id="9b885-207">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="9b885-208">動作のマージは、上に示した名前なし動作コレクションだけでなく、名前付き動作コレクションにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="9b885-208">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="9b885-209">動作のマージは、IIS ホスト環境で機能し、Web.config ファイルがルートの Web.config ファイルおよび machine.config と階層的にマージされます。ただし、動作のマージはアプリケーション環境でも機能し、machine.config を App.config ファイルとマージできます。</span><span class="sxs-lookup"><span data-stu-id="9b885-209">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="9b885-210">動作のマージは、構成内のエンドポイント動作とサービス動作の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9b885-210">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="9b885-211">親動作コレクションに既に存在する動作が子動作コレクションにも含まれている場合、子動作が親をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="9b885-211">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="9b885-212">親動作コレクションであれば`<serviceMetadata httpGetEnabled="False" />`あり、子動作コレクション`<serviceMetadata httpGetEnabled="True" />`、子動作が、動作コレクションで親動作をオーバーライドし、httpGetEnabled が"true"です。</span><span class="sxs-lookup"><span data-stu-id="9b885-212">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b885-213">参照</span><span class="sxs-lookup"><span data-stu-id="9b885-213">See Also</span></span>  
 [<span data-ttu-id="9b885-214">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="9b885-214">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)  
 [<span data-ttu-id="9b885-215">Windows Communication Foundation アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="9b885-215">Configuring Windows Communication Foundation Applications</span></span>](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)  
 [<span data-ttu-id="9b885-216">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="9b885-216">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
 [<span data-ttu-id="9b885-217">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="9b885-217">\<binding></span></span>](../../../docs/framework/misc/binding.md)
