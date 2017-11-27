---
title: '&lt;system.serviceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 563825a92dbdeb90cd17d107795525686b7b4080
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemservicemodelgt"></a><span data-ttu-id="85fe0-102">&lt;system.serviceModel&gt;</span><span class="sxs-lookup"><span data-stu-id="85fe0-102">&lt;system.serviceModel&gt;</span></span>
<span data-ttu-id="85fe0-103">この構成セクションは、すべての [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel 構成要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-103">This configuration section contains all the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85fe0-104">構文</span><span class="sxs-lookup"><span data-stu-id="85fe0-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
  </behaviors>  
  <bindings>  
  </bindings>  
  <client>  
  </client>  
  <comContracts>  
  </comContracts>  
  <commonBehaviors>  
  </commonBehaviors>  
  <diagnostics>  
  </diagnostics>  
  <extensions>  
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>  
  <serviceHostingEnvironment>  
  </serviceHostingEnvironment>  
  <services>  
  </services>
  <standardEndpoints>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85fe0-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="85fe0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="85fe0-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85fe0-107">属性</span><span class="sxs-lookup"><span data-stu-id="85fe0-107">Attributes</span></span>  
 <span data-ttu-id="85fe0-108">なし</span><span class="sxs-lookup"><span data-stu-id="85fe0-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="85fe0-109">子要素</span><span class="sxs-lookup"><span data-stu-id="85fe0-109">Child Elements</span></span>  
  
|<span data-ttu-id="85fe0-110">要素</span><span class="sxs-lookup"><span data-stu-id="85fe0-110">Element</span></span>|<span data-ttu-id="85fe0-111">説明</span><span class="sxs-lookup"><span data-stu-id="85fe0-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85fe0-112">\<ビヘイビアー ></span><span class="sxs-lookup"><span data-stu-id="85fe0-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="85fe0-113">このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="85fe0-114">各コレクションは、エンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="85fe0-115">各動作要素は、その一意の `name` 属性で識別されます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="85fe0-116">\<バインド ></span><span class="sxs-lookup"><span data-stu-id="85fe0-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="85fe0-117">このセクションには、標準バインディングおよびカスタム バインディングのコレクションが保持されます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="85fe0-118">各エントリは、その一意の `name` により識別されます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="85fe0-119">サービスは、`name` を使用してバインディングをリンクすることにより、バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="85fe0-120">\<クライアント ></span><span class="sxs-lookup"><span data-stu-id="85fe0-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="85fe0-121">このセクションは、クライアントがサービスの接続に使用するエンドポイントの一覧を含みます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="85fe0-122">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="85fe0-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="85fe0-123">このセクションは、WCF と COM 相互運用が有効な COM コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="85fe0-124">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="85fe0-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="85fe0-125">このセクションは、machine.config ファイルでだけ定義できます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="85fe0-126">このセクションは、`endpointBehaviors` と`serviceBehaviors` という 2 つの子コレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="85fe0-127">各コレクションは、コンピューター上の [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] のすべてのエンドポイントとサービスによって使用されるそれぞれの動作要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-127">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="85fe0-128">両方で、動作が定義されている場合`<commonBehaviors>`と`<behaviors>`セクションではの動作、\<動作 > セクションが優先します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="85fe0-129">\<拡張機能 ></span><span class="sxs-lookup"><span data-stu-id="85fe0-129">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="85fe0-130">このセクションには、拡張のコレクションが含まれています。これにより、ユーザー定義のバインディング、動作、およびその他の拡張機能を作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="85fe0-130">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="85fe0-131">\<診断 ></span><span class="sxs-lookup"><span data-stu-id="85fe0-131">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="85fe0-132">このセクションには、WCF の診断機能の設定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="85fe0-133">ユーザーはトレース、パフォーマンス カウンター、および WMI プロバイダーを有効または無効にしたり、カスタム メッセージ フィルターを追加したりできます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="85fe0-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="85fe0-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="85fe0-135">このセクションでは、トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) と WCF バインディング間の既定のプロトコル マッピングのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="85fe0-136">\<ルーティング ></span><span class="sxs-lookup"><span data-stu-id="85fe0-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="85fe0-137">このセクションは、受信メッセージの評価に使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> の種類を定義するルーティング フィルター セットと、フィルターが一致するときにメッセージを送信するターゲット エンドポイントを指定するルーティング テーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-137">This section defines a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="85fe0-138">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="85fe0-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="85fe0-139">このセクションは、環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="85fe0-140">このセクションが空の場合は、既定の型が使用されます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="85fe0-141">\<サービス ></span><span class="sxs-lookup"><span data-stu-id="85fe0-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="85fe0-142">このセクションには、サービスのコレクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="85fe0-142">The section contains a collection of services.</span></span> <span data-ttu-id="85fe0-143">アセンブリで定義された各サービスの場合、この要素は、サービスの設定を指定する `service` 要素を含みます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="85fe0-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="85fe0-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="85fe0-145">このセクションは、再使用可能な構成済みのエンドポイントである標準エンドポイントのコレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="85fe0-146">標準エンドポイントは、固定値に設定されたアドレス、バインディング、およびコントラクトの 1 つ以上の属性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="85fe0-147">たとえば、探索エンドポイントでは、コントラクトが固定されています。</span><span class="sxs-lookup"><span data-stu-id="85fe0-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="85fe0-148">標準エンドポイントを使用して、カスタム バインドの定義と同様に新しいプロパティを指定して、サービス エンドポイントを拡張することもできます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85fe0-149">親要素</span><span class="sxs-lookup"><span data-stu-id="85fe0-149">Parent Elements</span></span>  
  
|<span data-ttu-id="85fe0-150">要素</span><span class="sxs-lookup"><span data-stu-id="85fe0-150">Element</span></span>|<span data-ttu-id="85fe0-151">説明</span><span class="sxs-lookup"><span data-stu-id="85fe0-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85fe0-152">\<configuration></span><span class="sxs-lookup"><span data-stu-id="85fe0-152">\<configuration></span></span>|<span data-ttu-id="85fe0-153">.NET 構成ファイルのすべての構成要素のルート要素。</span><span class="sxs-lookup"><span data-stu-id="85fe0-153">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85fe0-154">コメント</span><span class="sxs-lookup"><span data-stu-id="85fe0-154">Remarks</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="85fe0-155"> は、他の製品の構成セクションに要素を追加しません。</span><span class="sxs-lookup"><span data-stu-id="85fe0-155"> does not add elements to the configuration sections of other products.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="85fe0-156"> サービスは、構成ファイルの `services` セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-156"> services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="85fe0-157">アセンブリには、任意の数のサービスを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-157">An assembly can contain any number of services.</span></span> <span data-ttu-id="85fe0-158">各サービスには、独自の `service` 設定セクションがあります。</span><span class="sxs-lookup"><span data-stu-id="85fe0-158">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="85fe0-159">セクションとその内容は、サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-159">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="85fe0-160">サービスの `name` 属性だけが必須項目です。</span><span class="sxs-lookup"><span data-stu-id="85fe0-160">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="85fe0-161">既定では、サービスの名前は、サービスの実装に使用される、基になる CLR 型を示します。ただし、<xref:System.ServiceModel.ServiceContractAttribute> の ConfigurationName プロパティを変更して、CLR 型要件をオーバーライドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-161">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="85fe0-162">`behaviorConfiguration` 属性は省略できます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-162">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="85fe0-163">サービスが使用するサービス動作を識別します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-163">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="85fe0-164">この属性で指定された動作は、同じ構成ファイルの範囲内に定義されたサービス動作にリンクしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="85fe0-164">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="85fe0-165">各サービスでは、`endpoint` 要素で定義された 1 つまたは複数のエンドポイントが公開されます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-165">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="85fe0-166">各エンドポイントには、独自のアドレスおよびバインディングがあります。</span><span class="sxs-lookup"><span data-stu-id="85fe0-166">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="85fe0-167">構成ファイル内で使用されるすべてのバインディングは、そのファイルのスコープ内で定義される必要があります。</span><span class="sxs-lookup"><span data-stu-id="85fe0-167">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="85fe0-168">バインディングは、`name` 属性と `bindingConfiguration` 属性の組み合わせによってエンドポイントにリンクされます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-168">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="85fe0-169">`binding` 属性は、バインディングが定義されているセクションで定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-169">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="85fe0-170">`bindingConfiguration` 属性は、バインディング セクション内で使用される構成済みバインディングを定義します。</span><span class="sxs-lookup"><span data-stu-id="85fe0-170">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="85fe0-171">バインディング セクションでは、複数の構成済みバインディングを定義できます。</span><span class="sxs-lookup"><span data-stu-id="85fe0-171">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85fe0-172">例</span><span class="sxs-lookup"><span data-stu-id="85fe0-172">Example</span></span>  
 <span data-ttu-id="85fe0-173">これは、WCF 構成ファイルの例です。</span><span class="sxs-lookup"><span data-stu-id="85fe0-173">This is an example of a WCF configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
           <!-- List of Behaviors -->  
        </behaviors>  
        <client>  
           <!-- List of Endpoints -->  
        </client>  
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
        </diagnostics>  
        <serviceHostingEnvironment>  
           <!-- List of entries -->  
        </serviceHostingEnvironment>  
        <comContracts>  
           <!-- List of COM+ Contracts -->  
        </comContracts>          
        <services>  
           <!-- List of Services -->  
        </services>  
        <bindings>  
           <!-- List of Bindings -->  
        </bindings>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="85fe0-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="85fe0-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
