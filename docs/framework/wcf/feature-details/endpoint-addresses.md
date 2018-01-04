---
title: "エンドポイント アドレス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 94610842cd801a54bba0266a4f658d8a4bb60dcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-addresses"></a><span data-ttu-id="a898d-102">エンドポイント アドレス</span><span class="sxs-lookup"><span data-stu-id="a898d-102">Endpoint Addresses</span></span>
<span data-ttu-id="a898d-103">すべてのエンドポイントにはこれと関連するアドレスがあり、エンドポイントの検索と識別に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-103">Every endpoint has an address associated with it, which is used to locate and identify the endpoint.</span></span> <span data-ttu-id="a898d-104">このアドレスは主にエンドポイントの位置を指定する URI (Uniform Resource Identifier) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-104">This address consists primarily of a Uniform Resource Identifier (URI), which specifies the location of the endpoint.</span></span> <span data-ttu-id="a898d-105">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のプログラミング モデルでは、エンドポイント アドレスは <xref:System.ServiceModel.EndpointAddress> クラスによって表されます。このクラスには、このエンドポイントとメッセージを交換する他のエンドポイントがエンドポイントを認証できるようにする、オプションの <xref:System.ServiceModel.EndpointAddress.Identity%2A> プロパティ、およびサービスに到達するために必要な他の任意の SOAP ヘッダーを定義するオプションの <xref:System.ServiceModel.EndpointAddress.Headers%2A> プロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a898d-105">The endpoint address is represented in the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] programming model by the <xref:System.ServiceModel.EndpointAddress> class, which contains an optional <xref:System.ServiceModel.EndpointAddress.Identity%2A> property that enables the authentication of the endpoint by other endpoints that exchange messages with it, and a set of optional <xref:System.ServiceModel.EndpointAddress.Headers%2A> properties, which define any other SOAP headers required to reach the service.</span></span> <span data-ttu-id="a898d-106">オプションのヘッダーは、サービス エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a898d-106">The optional headers provide additional and more detailed addressing information to identify or interact with the service endpoint.</span></span> <span data-ttu-id="a898d-107">エンドポイントのアドレスは、ネットワーク上では WS-Addressing エンドポイント参照 (EPR) として表されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-107">The address of an endpoint is represented on the wire as a WS-Addressing endpoint reference (EPR).</span></span>  
  
## <a name="uri-structure-of-an-address"></a><span data-ttu-id="a898d-108">アドレスの URI 構造</span><span class="sxs-lookup"><span data-stu-id="a898d-108">URI Structure of an Address</span></span>  
 <span data-ttu-id="a898d-109">ほとんどのトランスポートの URI アドレスは、4 つの部分から構成されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-109">The address URI for most transports has four parts.</span></span> <span data-ttu-id="a898d-110">たとえば、http://www.fabrikam.com:322/mathservice.svc/secureEndpoint という URI は、次の 4 つの部分から構成されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-110">For example, the four parts of the URI http://www.fabrikam.com:322/mathservice.svc/secureEndpoint can be itemized as follows:</span></span>  
  
-   <span data-ttu-id="a898d-111">スキーム : http:</span><span class="sxs-lookup"><span data-stu-id="a898d-111">Scheme: http:</span></span>  
  
-   <span data-ttu-id="a898d-112">コンピューター : www.fabrikam.com</span><span class="sxs-lookup"><span data-stu-id="a898d-112">Machine: www.fabrikam.com</span></span>  
  
-   <span data-ttu-id="a898d-113">(省略可能) ポート : 322</span><span class="sxs-lookup"><span data-stu-id="a898d-113">(optional) Port: 322</span></span>  
  
-   <span data-ttu-id="a898d-114">パス : /mathservice.svc/secureEndpoint</span><span class="sxs-lookup"><span data-stu-id="a898d-114">Path: /mathservice.svc/secureEndpoint</span></span>  
  
## <a name="defining-an-address-for-a-service"></a><span data-ttu-id="a898d-115">サービスのアドレスの定義</span><span class="sxs-lookup"><span data-stu-id="a898d-115">Defining an Address for a Service</span></span>  
 <span data-ttu-id="a898d-116">サービスのエンドポイント アドレスは、コードを使用して命令的に、または構成を通じて宣言的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="a898d-116">The endpoint address for a service can be specified either imperatively using code or declaratively through configuration.</span></span> <span data-ttu-id="a898d-117">設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="a898d-117">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="a898d-118">一般に、サービス エンドポイントの定義にはコードではなく、構成を使用する方がより実用的です。</span><span class="sxs-lookup"><span data-stu-id="a898d-118">Generally, it is more practical to define service endpoints using configuration rather than code.</span></span> <span data-ttu-id="a898d-119">バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="a898d-119">Keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
### <a name="defining-an-address-in-configuration"></a><span data-ttu-id="a898d-120">構成によるアドレス定義</span><span class="sxs-lookup"><span data-stu-id="a898d-120">Defining an Address in Configuration</span></span>  
 <span data-ttu-id="a898d-121">構成ファイルでエンドポイントを定義するには、使用、 [\<エンドポイント >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)要素。</span><span class="sxs-lookup"><span data-stu-id="a898d-121">To define an endpoint in a configuration file, use the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="a898d-122">詳細と例では、次を参照してください。[エンドポイント アドレスを指定する](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)です。</span><span class="sxs-lookup"><span data-stu-id="a898d-122">For details and an example, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
### <a name="defining-an-address-in-code"></a><span data-ttu-id="a898d-123">コードによるアドレス定義</span><span class="sxs-lookup"><span data-stu-id="a898d-123">Defining an Address in Code</span></span>  
 <span data-ttu-id="a898d-124">エンドポイント アドレスは、コードで <xref:System.ServiceModel.EndpointAddress> クラスを使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="a898d-124">An endpoint address can be created in code with the <xref:System.ServiceModel.EndpointAddress> class.</span></span> <span data-ttu-id="a898d-125">詳細と例では、次を参照してください。[エンドポイント アドレスを指定する](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)です。</span><span class="sxs-lookup"><span data-stu-id="a898d-125">For details and an example, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
### <a name="endpoints-in-wsdl"></a><span data-ttu-id="a898d-126">WSDL のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="a898d-126">Endpoints in WSDL</span></span>  
 <span data-ttu-id="a898d-127">エンドポイント アドレスは、対応するエンドポイントの `wsdl:port` 要素内の WS-Addressing EPR 要素として WSDL で表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="a898d-127">An endpoint address can also be represented in WSDL as a WS-Addressing EPR element inside the corresponding endpoint's `wsdl:port` element.</span></span> <span data-ttu-id="a898d-128">EPR には、エンドポイントのアドレスのほかに、アドレスのすべてのプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a898d-128">The EPR contains the endpoint's address as well as any address properties.</span></span> <span data-ttu-id="a898d-129">詳細と例では、次を参照してください。[エンドポイント アドレスを指定する](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)です。</span><span class="sxs-lookup"><span data-stu-id="a898d-129">For details and an example, see [Specifying an Endpoint Address](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span>  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a><span data-ttu-id="a898d-130">複数の IIS バインディングで .NET Framework 3.5 のサポート</span><span class="sxs-lookup"><span data-stu-id="a898d-130">Multiple IIS Binding Support in .NET Framework 3.5</span></span>  
 <span data-ttu-id="a898d-131">インターネット サービス プロバイダーは、多くの場合、サイトの密度を高めて総所有コストを抑えるため、同じサーバーまたはサイト上で複数のアプリケーションをホストしています。</span><span class="sxs-lookup"><span data-stu-id="a898d-131">Internet service providers often host many applications on the same server and site to increase the site density and lower total cost of ownership.</span></span> <span data-ttu-id="a898d-132">通常、これらのアプリケーションは、異なるベース アドレスにバインドされています。</span><span class="sxs-lookup"><span data-stu-id="a898d-132">These applications are typically bound to different base addresses.</span></span> <span data-ttu-id="a898d-133">インターネット インフォメーション サービス (IIS) Web サイトは、複数のアプリケーションを格納できます。</span><span class="sxs-lookup"><span data-stu-id="a898d-133">An Internet Information Services (IIS) Web site can contain multiple applications.</span></span> <span data-ttu-id="a898d-134">サイト内のアプリケーションに、1 つ以上の IIS バインディングからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a898d-134">The applications in a site can be accessed through one or more IIS bindings.</span></span>  
  
 <span data-ttu-id="a898d-135">IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a898d-135">IIS bindings provide two pieces of information: a binding protocol, and binding information.</span></span> <span data-ttu-id="a898d-136">バインディング プロトコルは通信を行うスキームを定義するもので、バインディング情報はサイトにアクセスするために使用する情報です。</span><span class="sxs-lookup"><span data-stu-id="a898d-136">The binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span>  
  
 <span data-ttu-id="a898d-137">IIS バインディングに使用されるコンポーネントの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a898d-137">The following example shows the components that can be present in an IIS binding:</span></span>  
  
-   <span data-ttu-id="a898d-138">バインディング プロトコル : HTTP</span><span class="sxs-lookup"><span data-stu-id="a898d-138">Binding protocol: HTTP</span></span>  
  
-   <span data-ttu-id="a898d-139">バインディング情報 : IP アドレス、ポート、ホスト ヘッダー</span><span class="sxs-lookup"><span data-stu-id="a898d-139">Binding Information: IP Address, Port, Host header</span></span>  
  
 <span data-ttu-id="a898d-140">IIS ではサイトごとに複数の IIS バインディングを指定でき、これによりスキームごとに複数のベース アドレスをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="a898d-140">IIS can specify multiple bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="a898d-141">[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] 以前は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではスキームごとに複数のアドレスがサポートされておらず、複数のアドレスが指定された場合は、アクティブ化の間に <xref:System.ArgumentException> がスローされました。</span><span class="sxs-lookup"><span data-stu-id="a898d-141">Prior to [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] did not support multiple addresses for a schema and, if they were specified, threw a <xref:System.ArgumentException> during activation.</span></span>  
  
 <span data-ttu-id="a898d-142">[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] により、インターネット サービス プロバイダーは同じサイト上の同じスキームに対して別のベース アドレスを使用して複数のアプリケーションをホストできます。</span><span class="sxs-lookup"><span data-stu-id="a898d-142">The [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] enables Internet service providers to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="a898d-143">たとえば、サイトで次のベース アドレスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a898d-143">For example, a site could contain the following base addresses:</span></span>  
  
-   <span data-ttu-id="a898d-144">http://payroll.myorg.com/Service.svc</span><span class="sxs-lookup"><span data-stu-id="a898d-144">http://payroll.myorg.com/Service.svc</span></span>  
  
-   <span data-ttu-id="a898d-145">http://shipping.myorg.com/Service.svc</span><span class="sxs-lookup"><span data-stu-id="a898d-145">http://shipping.myorg.com/Service.svc</span></span>  
  
 <span data-ttu-id="a898d-146">[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] では、構成ファイルの AppDomain レベルでプレフィックス フィルターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a898d-146">With [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], you specify a prefix filter at the AppDomain level in the configuration file.</span></span> <span data-ttu-id="a898d-147">これを行う、 [ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)要素は、プレフィックスの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a898d-147">You do this with the [\<baseAddressPrefixFilters>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) element, which contains a list of prefixes.</span></span> <span data-ttu-id="a898d-148">IIS によって指定される受信ベース アドレスは、オプションのプレフィックス一覧に基づいてフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-148">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list.</span></span> <span data-ttu-id="a898d-149">既定では、プレフィックスを指定しない場合、すべてのアドレスが渡されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-149">By default, when a prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="a898d-150">プレフィックスを指定すると、そのスキームに一致するベース アドレスだけが渡されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-150">Specifying the prefix results in only the matching base address for that scheme to be passed through.</span></span>  
  
 <span data-ttu-id="a898d-151">プレフィックス フィルターを使用する構成コード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a898d-151">The following is an example of configuration code that uses the prefix filters.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="a898d-152">上記の例では、net.tcp://payroll.myorg.com:8000 と http://shipping.myorg.com:8000 が、対応するスキームに対して渡されるベース アドレスです。</span><span class="sxs-lookup"><span data-stu-id="a898d-152">In the preceding example, net.tcp://payroll.myorg.com:8000 and http://shipping.myorg.com:8000 are the only base addresses, for their respective schemes, which are passed through.</span></span>  
  
 <span data-ttu-id="a898d-153">`baseAddressPrefixFilter` では、ワイルカードはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="a898d-153">The `baseAddressPrefixFilter` does not support wildcards.</span></span>  
  
 <span data-ttu-id="a898d-154">IIS が提供するベース アドレスには、`baseAddressPrefixFilters` 一覧に存在しない他のスキームにバインドされたアドレスが指定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="a898d-154">The base addresses supplied by IIS may have addresses bound to other schemes not present in `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="a898d-155">これらのアドレスはフィルターで除外されません。</span><span class="sxs-lookup"><span data-stu-id="a898d-155">These addresses are not filtered out.</span></span>  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a><span data-ttu-id="a898d-156">.NET Framework 4 以降での複数の IIS バインディングのサポート</span><span class="sxs-lookup"><span data-stu-id="a898d-156">Multiple IIS Binding Support in .NET Framework 4 and later</span></span>  
 <span data-ttu-id="a898d-157">.NET 4 以降、<xref:System.ServiceModel.ServiceHostingEnvironment> の <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> 設定を true に設定するだけで、1 つのベース アドレスを選択しなくても、IIS で複数のバインディングのサポートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="a898d-157">Starting in .NET 4, you can enable support for multiple bindings in IIS without having to pick a single base address, by setting <xref:System.ServiceModel.ServiceHostingEnvironment>’s <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> setting to true.</span></span> <span data-ttu-id="a898d-158">このサポートは、HTTP プロトコル スキームに限定されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-158">This support is limited to HTTP protocol schemes.</span></span>  
  
 <span data-ttu-id="a898d-159">MultipleSiteBindingsEnabled を使用する構成コードの例を次に示します[ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)です。</span><span class="sxs-lookup"><span data-stu-id="a898d-159">The following is an example of configuration code that uses multipleSiteBindingsEnabled on [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="a898d-160">複数のサイト バインディングがこの設定を使用して有効になっている場合、HTTP プロトコルと非 HTTP プロトコルの両方について、baseAddressPrefixFilters 設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-160">Any baseAddressPrefixFilters settings are ignored, for both HTTP and non-HTTP protocols, when multiple site bindings are enabled using this setting.</span></span>  
  
 <span data-ttu-id="a898d-161">詳細と例については、次を参照してください。[複数の IIS サイト バインディングをサポートする](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md)と<xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>です。</span><span class="sxs-lookup"><span data-stu-id="a898d-161">For details and examples, see [Supporting Multiple IIS Site Bindings](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md) and <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>.</span></span>  
  
## <a name="extending-addressing-in-wcf-services"></a><span data-ttu-id="a898d-162">WCF サービスによるアドレスの拡張</span><span class="sxs-lookup"><span data-stu-id="a898d-162">Extending Addressing in WCF Services</span></span>  
 <span data-ttu-id="a898d-163">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの既定のアドレス指定モデルでは、エンドポイント アドレス URI を次の目的で使用します。</span><span class="sxs-lookup"><span data-stu-id="a898d-163">The default addressing model of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services uses the endpoint address URI for the following purposes:</span></span>  
  
-   <span data-ttu-id="a898d-164">サービスがリッスンするアドレス、つまりエンドポイントがメッセージをリッスンする位置の指定</span><span class="sxs-lookup"><span data-stu-id="a898d-164">To specify the service listening address, the location at which the endpoint listens for messages,</span></span>  
  
-   <span data-ttu-id="a898d-165">SOAP アドレス フィルター、つまりエンドポイントが SOAP ヘッダーとして待機するアドレスの指定</span><span class="sxs-lookup"><span data-stu-id="a898d-165">To specify the SOAP address filter, the address an endpoint expects as a SOAP header.</span></span>  
  
 <span data-ttu-id="a898d-166">これらの目的で使用する値は個別に指定することができるため、アドレス指定の拡張が可能になり、次に示すような役に立つシナリオに対応します。</span><span class="sxs-lookup"><span data-stu-id="a898d-166">The values for each of these purposes can be specified separately, allowing several extensions of addressing that cover useful scenarios:</span></span>  
  
-   <span data-ttu-id="a898d-167">SOAP 中継局 : クライアントが送信したメッセージは、最終目的地に到達する前にメッセージを処理する 1 つ以上の追加サービスを経由します。</span><span class="sxs-lookup"><span data-stu-id="a898d-167">SOAP intermediaries: a message sent by a client traverses one or more additional services that process the message before it reaches its final destination.</span></span> <span data-ttu-id="a898d-168">SOAP 中継局は、メッセージのキャッシュ、ルーティング、負荷分散、スキーム検証など多様なタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a898d-168">SOAP intermediaries can perform various tasks, such as caching, routing, load-balancing, or schema validation on the messages.</span></span> <span data-ttu-id="a898d-169">このシナリオは、最終的な送信先である論理アドレス (`via`) ではなく、中継局を目的とする独立した物理アドレス (`wsa:To`) にメッセージを送信することによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-169">This scenario is accomplished by sending messages to a separate physical address (`via`) that targets the intermediary rather than just to a logical address (`wsa:To`) that targets the ultimate destination.</span></span>  
  
-   <span data-ttu-id="a898d-170">エンドポイントがリッスンするアドレスはプライベート URI であり、`listenURI` プロパティとは異なる値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-170">The listening address of the endpoint is a private URI and is set to a different value than its `listenURI` property.</span></span>  
  
 <span data-ttu-id="a898d-171">`via` が指定するトランスポート アドレスはメッセージが最初に送信される場所で、この後にメッセージは、`to` パラメーターによって指定された、サービスが存在する別のリモート アドレスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-171">The transport address that the `via` specifies is the location to which a message should initially be sent on its way to some other remote address specified by the `to` parameter at which the service is located.</span></span> <span data-ttu-id="a898d-172">インターネットの場合、`via` URI は、サービスの最終的な <xref:System.ServiceModel.EndpointAddress.Uri%2A> アドレスの `to` プロパティと同じになります。</span><span class="sxs-lookup"><span data-stu-id="a898d-172">In most Internet scenarios, the `via` URI is the same as the <xref:System.ServiceModel.EndpointAddress.Uri%2A> property of the final `to` address of the service.</span></span> <span data-ttu-id="a898d-173">この 2 つのアドレスを区別するのは、手動ルーティングを行う必要がある場合のみです。</span><span class="sxs-lookup"><span data-stu-id="a898d-173">You only distinguish between these two addresses when you must do manual routing.</span></span>  
  
### <a name="addressing-headers"></a><span data-ttu-id="a898d-174">ヘッダーのアドレス指定</span><span class="sxs-lookup"><span data-stu-id="a898d-174">Addressing Headers</span></span>  
 <span data-ttu-id="a898d-175">エンドポイントは、基本となる URI だけでなく、1 つ以上の SOAP ヘッダーによってアドレス指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="a898d-175">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="a898d-176">これが役に立つのは、エンドポイントのクライアントに中継局を指す SOAP ヘッダーを含める必要がある、SOAP 中継局のシナリオの場合です。</span><span class="sxs-lookup"><span data-stu-id="a898d-176">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span>  
  
 <span data-ttu-id="a898d-177">カスタムのアドレス ヘッダーは、コードまたは構成のいずれかを使用して次のように定義できます。</span><span class="sxs-lookup"><span data-stu-id="a898d-177">You can define custom address headers in two ways—by using either code or configuration:</span></span>  
  
-   <span data-ttu-id="a898d-178">コードを使用する場合、カスタムのアドレス ヘッダーは <xref:System.ServiceModel.Channels.AddressHeader> クラスを使用して作成し、<xref:System.ServiceModel.EndpointAddress> の構築時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a898d-178">In code, create custom address headers by using the <xref:System.ServiceModel.Channels.AddressHeader> class, and then used in the construction of an <xref:System.ServiceModel.EndpointAddress>.</span></span>  
  
-   <span data-ttu-id="a898d-179">構成では、カスタム[\<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)の子として指定された、 [\<エンドポイント >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)要素。</span><span class="sxs-lookup"><span data-stu-id="a898d-179">In configuration, custom [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) are specified as children of the [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
 <span data-ttu-id="a898d-180">配置後もヘッダーを変更できるため、コードよりも構成を使用する方法を一般的にお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a898d-180">Configuration is generally preferable to code, as it allows you to change the headers after deployment.</span></span>  
  
### <a name="custom-listening-addresses"></a><span data-ttu-id="a898d-181">カスタム リッスン アドレス</span><span class="sxs-lookup"><span data-stu-id="a898d-181">Custom Listening Addresses</span></span>  
 <span data-ttu-id="a898d-182">リッスンするアドレスには、エンドポイントの URI とは異なる値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="a898d-182">You can set the listening address to a different value than the endpoint’s URI.</span></span> <span data-ttu-id="a898d-183">これは、SOAP アドレスがパブリックな SOAP 中継局として公開される一方、エンドポイントが実際にリッスンするアドレスはプライベートなネットワーク アドレスであるような中継局シナリオの場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="a898d-183">This is useful in intermediary scenarios where the SOAP address to be exposed is that of a public SOAP intermediary, whereas the address where the endpoint actually listens is a private network address.</span></span>  
  
 <span data-ttu-id="a898d-184">カスタム リッスン アドレスは、コードまたは構成のいずれかを使用して指定できます。</span><span class="sxs-lookup"><span data-stu-id="a898d-184">You can specify a custom listening address by using either code or configuration:</span></span>  
  
-   <span data-ttu-id="a898d-185">コードを使用する場合、カスタム リッスン アドレスはエンドポイントの動作コレクションに <xref:System.ServiceModel.Description.ClientViaBehavior> クラスを追加して指定します。</span><span class="sxs-lookup"><span data-stu-id="a898d-185">In code, specify a custom listening address by adding a <xref:System.ServiceModel.Description.ClientViaBehavior> class to the endpoint’s behavior collection.</span></span>  
  
-   <span data-ttu-id="a898d-186">構成では、カスタム リッスン アドレスを指定、`ListenUri`のサービスの属性[\<エンドポイント >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)要素。</span><span class="sxs-lookup"><span data-stu-id="a898d-186">In configuration, specify a custom listening address with the `ListenUri` attribute of the service [\<endpoint>](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017) element.</span></span>  
  
### <a name="custom-soap-address-filter"></a><span data-ttu-id="a898d-187">カスタム SOAP アドレス フィルター</span><span class="sxs-lookup"><span data-stu-id="a898d-187">Custom SOAP Address Filter</span></span>  
 <span data-ttu-id="a898d-188">エンドポイントの SOAP アドレス フィルター (<xref:System.ServiceModel.EndpointAddress.Uri%2A>) を定義するには、<xref:System.ServiceModel.EndpointAddress.Headers%2A> に任意の <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> プロパティを組み合わせて使用します。</span><span class="sxs-lookup"><span data-stu-id="a898d-188">The <xref:System.ServiceModel.EndpointAddress.Uri%2A> is used in conjunction with any <xref:System.ServiceModel.EndpointAddress.Headers%2A> property to define an endpoint’s SOAP address filter (<xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A>).</span></span> <span data-ttu-id="a898d-189">既定では、このフィルターは受信メッセージの `To` メッセージ ヘッダーが、エンドポイントの URI に一致し、必要なすべてのエンドポイント ヘッダーがメッセージ内に存在していることを検証します。</span><span class="sxs-lookup"><span data-stu-id="a898d-189">By default, this filter verifies that an incoming message has a `To` message header that matches the endpoint’s URI and that all of the required endpoint headers are present in the message.</span></span>  
  
 <span data-ttu-id="a898d-190">シナリオによっては、適切な `To` ヘッダーを持つメッセージだけではなく、基になるトランスポートに到着したすべてのメッセージをエンドポイントで受信します。</span><span class="sxs-lookup"><span data-stu-id="a898d-190">In some scenarios, an endpoint receives all messages that arrive on the underlying transport, and not just those with the appropriate `To` header.</span></span> <span data-ttu-id="a898d-191">これを行うには、ユーザーは <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a898d-191">To enable this, the user can use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a898d-192">参照</span><span class="sxs-lookup"><span data-stu-id="a898d-192">See Also</span></span>  
 [<span data-ttu-id="a898d-193">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="a898d-193">Specifying an Endpoint Address</span></span>](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)  
 [<span data-ttu-id="a898d-194">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="a898d-194">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
