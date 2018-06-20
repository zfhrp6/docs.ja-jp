---
title: クライアント構成
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: 26557b6cbbe33626152878eccab62de11d22660d
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207418"
---
# <a name="client-configuration"></a><span data-ttu-id="b4dbd-102">クライアント構成</span><span class="sxs-lookup"><span data-stu-id="b4dbd-102">Client Configuration</span></span>
<span data-ttu-id="b4dbd-103">Windows Communication Foundation (WCF) クライアントの構成を使用するには、アドレス、バインディング、動作、およびコントラクト、サービス エンドポイントに接続するクライアントを使用して、クライアント エンドポイントの"ABC"プロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-103">You can use the Windows Communication Foundation (WCF) client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="b4dbd-104">[\<クライアント >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md)要素には、 [\<エンドポイント >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)要素の属性を持つエンドポイントの abc プロパティの構成に使用します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-104">The [\<client>](../../../../docs/framework/configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="b4dbd-105">これらの属性については、このトピックの「エンドポイントの構成」で説明します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-105">These attributes are discussed in the "Configuring Endpoints" section of this topic.</span></span>  
  
 <span data-ttu-id="b4dbd-106">[\<エンドポイント >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017)要素も含まれています、 [\<メタデータ >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)要素のインポートとエクスポートのメタデータの設定を指定するために使用する[ \<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)カスタムのアドレス ヘッダーのコレクションを格納する要素と[ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素を他のエンドポイントによるエンドポイントの認証を有効にします。メッセージを交換します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-106">The [\<endpoint>](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element also contains a [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata , a [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="b4dbd-107">[\<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)と[ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素の一部である、<xref:System.ServiceModel.EndpointAddress>で説明されているが、[アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-107">The [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span> <span data-ttu-id="b4dbd-108">メタデータ拡張の使用法に関するトピックへのリンクは、このトピックの「メタデータの構成」にあります。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-108">Links to topics that explain the use of metadata extensions are provided in the Configuring Metadata sub-section of this topic.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="b4dbd-109">エンドポイントの構成</span><span class="sxs-lookup"><span data-stu-id="b4dbd-109">Configuring Endpoints</span></span>  
 <span data-ttu-id="b4dbd-110">クライアントの構成が 1 つ指定するクライアントを許可するように設計されていますか、それぞれ独自の名前、複数のエンドポイント アドレス、およびコントラクトを各参照と、 [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)と[ \<ビヘイビアー >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)そのエンドポイントを構成するために使用するクライアント構成内の要素。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-110">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="b4dbd-111">クライアント構成ファイルに名前を付ける"App.config"これは、WCF ランタイムものと想定する名前であるためです。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-111">The client configuration file should be named "App.config" because this is the name that the WCF runtime expects.</span></span> <span data-ttu-id="b4dbd-112">クライアント構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-112">The following example shows a client configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
// Add another endpoint by adding another <endpoint> element.  
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"   
                 bypassProxyOnLocal="false"   
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"   
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
        //Configure this binding here.  
        </binding>  
          </wsHttpBinding>  
        </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b4dbd-113">省略可能な `name` 属性は、特定のコントラクトのエンドポイントを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-113">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="b4dbd-114">この属性は、サービスへのチャネルの作成時に、クライアント構成のどのエンドポイントをターゲットとし、読み込む必要があるかを指定するために、<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> または <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> が使用します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-114">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="b4dbd-115">エンドポイント構成名としてワイルドカード "\*" を使用できます。これは、使用できるエンドポイント構成が 1 つだけ存在する場合はファイル内のエンドポイント構成を読み込み、それ以外の場合は例外をスローするように <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> メソッドに指示します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-115">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="b4dbd-116">この属性が省略されている場合、指定されたコントラクトの種類に関連する既定のエンドポイントとして、対応するエンドポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-116">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="b4dbd-117">`name` 属性の既定値は、他の名前と同様に一致する空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-117">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="b4dbd-118">すべてのエンドポイントには、エンドポイントを検索および識別するために、アドレスが関連付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-118">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="b4dbd-119">`address` 属性は、エンドポイントの場所を示す URL を指定するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-119">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="b4dbd-120">ただし、サービス エンドポイントのアドレスは、コードで指定することもできます。その場合は、URI (Uniform Resource Identifier) を作成し、<xref:System.ServiceModel.ServiceHost> メソッドのいずれかを使用して、この URI を <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> に追加します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-120">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="b4dbd-121">詳細については、次を参照してください。[アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-121">For more information, see [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).</span></span> <span data-ttu-id="b4dbd-122">概要が示されているように、 [\<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)と[ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素の一部である、 <xref:System.ServiceModel.EndpointAddress> 」でも説明、および、 [アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)トピックです。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-122">As the introduction indicates, the [\<headers>](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="b4dbd-123">`binding` 属性は、エンドポイントがサービスに接続する際に使用するバインディングの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-123">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="b4dbd-124">参照できるようにするには、種類は登録された構成セクションを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-124">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="b4dbd-125">これは、前の例で、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)セクションでは、エンドポイントを使用することを示します、<xref:System.ServiceModel.WSHttpBinding>です。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-125">In the previous example, this is the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="b4dbd-126">ただし、エンドポイントが使用できる、指定された種類のバインディングが複数存在することもあります。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-126">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="b4dbd-127">これらのそれぞれが独自[\<バインディング >](../../../../docs/framework/misc/binding.md)要素内部の要素 (バインド) の種類。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-127">Each of these has its own [\<binding>](../../../../docs/framework/misc/binding.md) element within the (binding) type element.</span></span> <span data-ttu-id="b4dbd-128">`bindingconfiguration` 属性は、同じ種類のバインディングを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-128">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="b4dbd-129">その値と対応している、`name`の属性、 [\<バインディング >](../../../../docs/framework/misc/binding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-129">Its value is matched with the `name` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span> <span data-ttu-id="b4dbd-130">クライアントを構成する方法の詳細について構成を使用するバインディングを参照してください[する方法: 構成でクライアント バインディングを指定](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-130">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="b4dbd-131">`behaviorConfiguration`を指定する属性が使用される[\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)の[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)エンドポイントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-131">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="b4dbd-132">その値と対応している、`name`の属性、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)要素。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-132">Its value is matched with the `name` attribute of the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="b4dbd-133">クライアントの動作を指定する構成を使用しての例は、次を参照してください。[クライアントの動作を構成する](../../../../docs/framework/wcf/configuring-client-behaviors.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-133">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../../../../docs/framework/wcf/configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="b4dbd-134">`contract` 属性は、エンドポイントが公開するコントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-134">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="b4dbd-135">この値は、<xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> の <xref:System.ServiceModel.ServiceContractAttribute> にマップされます。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-135">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="b4dbd-136">既定値は、サービスを実装するクラスの完全な型名です。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-136">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="b4dbd-137">メタデータの構成</span><span class="sxs-lookup"><span data-stu-id="b4dbd-137">Configuring Metadata</span></span>  
 <span data-ttu-id="b4dbd-138">[\<メタデータ >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)要素を使用して拡張機能をインポートするメタデータを登録するための設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-138">The [\<metadata>](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="b4dbd-139">メタデータ システムの拡張の詳細については、次を参照してください。[メタデータ システムの拡張](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)です。</span><span class="sxs-lookup"><span data-stu-id="b4dbd-139">For more information about extending the metadata system, see [Extending the Metadata System](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4dbd-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="b4dbd-140">See Also</span></span>  
 [<span data-ttu-id="b4dbd-141">エンドポイント : アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="b4dbd-141">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="b4dbd-142">クライアントの動作の構成</span><span class="sxs-lookup"><span data-stu-id="b4dbd-142">Configuring Client Behaviors</span></span>](../../../../docs/framework/wcf/configuring-client-behaviors.md)
