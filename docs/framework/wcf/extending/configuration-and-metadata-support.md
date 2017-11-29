---
title: "構成とメタデータのサポート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1d2e0153a9ab8839aed1af948183397f7728e3d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-and-metadata-support"></a><span data-ttu-id="57f45-102">構成とメタデータのサポート</span><span class="sxs-lookup"><span data-stu-id="57f45-102">Configuration and Metadata Support</span></span>
<span data-ttu-id="57f45-103">ここでは、バインディングおよびバインド要素用に構成とメタデータのサポートを有効にする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="57f45-103">This topic describes how to enable configuration and metadata support for bindings and binding elements.</span></span>  
  
## <a name="overview-of-configuration-and-metadata"></a><span data-ttu-id="57f45-104">構成とメタデータの概要</span><span class="sxs-lookup"><span data-stu-id="57f45-104">Overview of Configuration and Metadata</span></span>  
 <span data-ttu-id="57f45-105">省略可能な項目 1、2、および 4 は、次のタスクについて説明で、[開発チャネル](../../../../docs/framework/wcf/extending/developing-channels.md)タスクの一覧です。</span><span class="sxs-lookup"><span data-stu-id="57f45-105">This topic discusses the following tasks, which are optional items 1, 2, and 4 in the [Developing Channels](../../../../docs/framework/wcf/extending/developing-channels.md) task list.</span></span>  
  
-   <span data-ttu-id="57f45-106">バインド要素の構成ファイル サポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="57f45-106">Enabling configuration file support for a binding element.</span></span>  
  
-   <span data-ttu-id="57f45-107">バインディングの構成ファイル サポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="57f45-107">Enabling configuration file support for a binding.</span></span>  
  
-   <span data-ttu-id="57f45-108">バインド要素の WSDL とポリシー アサーションをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="57f45-108">Exporting WSDL and policy assertions for a binding element.</span></span>  
  
-   <span data-ttu-id="57f45-109">バインディングまたはバインド要素に挿入して構成する WSDL とポリシー アサーションを特定します。</span><span class="sxs-lookup"><span data-stu-id="57f45-109">Identifying WSDL and policy assertions to insert and configure your binding or binding element.</span></span>  
  
 <span data-ttu-id="57f45-110">ユーザー定義のバインディングとバインド要素を作成する方法の詳細については、次を参照してください。[ユーザー定義バインディング](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)と[BindingElement の作成](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="57f45-110">For information about creating user-defined bindings and binding elements, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md) and [Creating a BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md), respectively.</span></span>  
  
## <a name="adding-configuration-support"></a><span data-ttu-id="57f45-111">構成サポートの追加</span><span class="sxs-lookup"><span data-stu-id="57f45-111">Adding Configuration Support</span></span>  
 <span data-ttu-id="57f45-112">チャネルに対する構成ファイルのサポートを有効にするには、2 つの構成セクションを実装する必要があります。1 つはバインド要素に対する構成のサポートを有効にする <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> で、もう 1 つはバインディングに対する構成のサポートを有効にする <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> と <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="57f45-112">To enable configuration file support for a channel, you must implement two configuration sections, <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>, which enables configuration support for binding elements, and the <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=nameWithType> and <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=nameWithType>, which enable configuration support for bindings.</span></span>  
  
 <span data-ttu-id="57f45-113">これを行う簡単な方法が使用するには、 [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md)サンプル ツールは、バインディングとバインド要素の構成コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="57f45-113">An easier way to do this is to use the [ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) sample tool to generate configuration code for your bindings and binding elements.</span></span>  
  
### <a name="extending-bindingelementextensionelement"></a><span data-ttu-id="57f45-114">BindingElementExtensionElement の拡張</span><span class="sxs-lookup"><span data-stu-id="57f45-114">Extending BindingElementExtensionElement</span></span>  
 <span data-ttu-id="57f45-115">次のコード例から取得、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="57f45-115">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span> <span data-ttu-id="57f45-116">`UdpTransportElement` は <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> を構成システムに公開する `UdpTransportBindingElement` です。</span><span class="sxs-lookup"><span data-stu-id="57f45-116">The `UdpTransportElement` is a <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="57f45-117">いくつかの基本的なオーバーライドを行うことで、サンプルでは構成セクション名、バインド要素の種類とバインド要素の作成方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="57f45-117">With a few basic overrides, the sample defines the configuration section name, the type of the binding element and how to create the binding element.</span></span> <span data-ttu-id="57f45-118">その後、次のようにして拡張セクションを構成ファイルに登録できます。</span><span class="sxs-lookup"><span data-stu-id="57f45-118">Users can then register the extension section in a configuration file as follows.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
      <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="57f45-119">この拡張は、UDP をトランスポートとして使用するためにカスタム バインディングから参照されます。</span><span class="sxs-lookup"><span data-stu-id="57f45-119">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="adding-configuration-for-a-binding"></a><span data-ttu-id="57f45-120">バインディングの構成の追加</span><span class="sxs-lookup"><span data-stu-id="57f45-120">Adding Configuration for a Binding</span></span>  
 <span data-ttu-id="57f45-121">セクション `SampleProfileUdpBindingCollectionElement` は <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> で、`SampleProfileUdpBinding` を構成システムに公開します。</span><span class="sxs-lookup"><span data-stu-id="57f45-121">The section `SampleProfileUdpBindingCollectionElement` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="57f45-122">実装の大部分は `SampleProfileUdpBindingConfigurationElement` で代行されます。これは <xref:System.ServiceModel.Configuration.StandardBindingElement> の派生です。</span><span class="sxs-lookup"><span data-stu-id="57f45-122">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="57f45-123">`SampleProfileUdpBindingConfigurationElement`でプロパティに対応するプロパティを持つ`SampleProfileUdpBinding`、およびからマップする関数、`ConfigurationElement`バインドします。</span><span class="sxs-lookup"><span data-stu-id="57f45-123">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="57f45-124">次のサンプル コードで示すように、最後に、`OnApplyConfiguration` メソッドが `SampleProfileUdpBinding` 内でオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="57f45-124">Finally, the `OnApplyConfiguration` method is overridden in the `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```  
protected override void OnApplyConfiguration(string configurationName)  
{  
            if (binding == null)  
                throw new ArgumentNullException("binding");  
  
            if (binding.GetType() != typeof(SampleProfileUdpBinding))  
            {  
                throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,  
                    "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",  
                    typeof(SampleProfileUdpBinding).AssemblyQualifiedName,  
                    binding.GetType().AssemblyQualifiedName));  
            }  
            SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;  
  
            udpBinding.OrderedSession = this.OrderedSession;  
            udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;  
            udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;  
            if (this.ClientBaseAddress != null)  
                   udpBinding.ClientBaseAddress = ClientBaseAddress;  
}  
```  
  
 <span data-ttu-id="57f45-125">このハンドラーを構成システムに登録するには、次のセクションを関連する構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="57f45-125">To register this handler with the configuration system, add the following section to the relevant configuration file.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
         <sectionGroup name="bindings">  
                 <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
         </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="57f45-126">参照できる、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)構成セクション。</span><span class="sxs-lookup"><span data-stu-id="57f45-126">It can then be referenced from the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) configuration section.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="adding-metadata-support-for-a-binding-element"></a><span data-ttu-id="57f45-127">バインド要素のメタデータ サポートの追加</span><span class="sxs-lookup"><span data-stu-id="57f45-127">Adding Metadata Support for a Binding Element</span></span>  
 <span data-ttu-id="57f45-128">チャネルをメタデータ システムに統合するには、ポリシーのインポートとエクスポートの両方がサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="57f45-128">To integrate a channel into the metadata system, it must support both the import and export of policy.</span></span> <span data-ttu-id="57f45-129">これによって、ツールなど[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)バインド要素のクライアントを生成します。</span><span class="sxs-lookup"><span data-stu-id="57f45-129">This allows tools such as [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate clients of the binding element.</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="57f45-130">WSDL サポートの追加</span><span class="sxs-lookup"><span data-stu-id="57f45-130">Adding WSDL Support</span></span>  
 <span data-ttu-id="57f45-131">バインディングのトランスポート バインド要素は、メタデータのアドレス指定情報のインポートとエクスポートを行います。</span><span class="sxs-lookup"><span data-stu-id="57f45-131">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="57f45-132">SOAP バインディングを使用する場合は、トランスポート バインド要素によっても、メタデータの正しいトランスポート URI がエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="57f45-132">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span> <span data-ttu-id="57f45-133">次のコード例から取得、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="57f45-133">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="57f45-134">WSDL エクスポート</span><span class="sxs-lookup"><span data-stu-id="57f45-134">WSDL Export</span></span>  
 <span data-ttu-id="57f45-135">アドレス指定情報をエクスポートする、`UdpTransportBindingElement`を実装する、<xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="57f45-135">To export addressing information, the `UdpTransportBindingElement` implements the <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="57f45-136"><xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> メソッドにより、正しいアドレス指定情報が WSDL ポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="57f45-136">The <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=nameWithType> method adds the correct addressing information to the WSDL port.</span></span>  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="57f45-137">エンドポイントが SOAP バインディングを使用する場合、`UdpTransportBindingElement` メソッドの <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> の実装でも、次のようにトランスポート URI がエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="57f45-137">The `UdpTransportBindingElement` implementation of the <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> method also exports a transport URI when the endpoint uses a SOAP binding:</span></span>  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="57f45-138">WSDL インポート</span><span class="sxs-lookup"><span data-stu-id="57f45-138">WSDL Import</span></span>  
 <span data-ttu-id="57f45-139">WSDL インポート システムを拡張してアドレスのインポートを処理するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f45-139">To extend the WSDL import system to handle importing the addresses, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="57f45-140">Svcutil.exe を実行する場合、Svcutil.exe に WSDL インポートの拡張を読み込ませるために次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="57f45-140">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="57f45-141">/SvcutilConfig を使用して構成ファイルに Svcutil.exe:\<ファイル >。</span><span class="sxs-lookup"><span data-stu-id="57f45-141">Point Svcutil.exe to the configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="57f45-142">Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="57f45-142">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="57f45-143">`UdpBindingElementImporter` 型は、<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="57f45-143">The `UdpBindingElementImporter` type implements the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="57f45-144">`ImportEndpoint` メソッドは、次のようにして WSDL ポートからアドレスをインポートします。</span><span class="sxs-lookup"><span data-stu-id="57f45-144">The `ImportEndpoint` method imports the address from the WSDL port:</span></span>  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="57f45-145">ポリシー サポートの追加</span><span class="sxs-lookup"><span data-stu-id="57f45-145">Adding Policy Support</span></span>  
 <span data-ttu-id="57f45-146">カスタム バインド要素では、WSDL バインディング内のポリシー アサーションをエクスポートして、サービス エンドポイントでそのバインド要素の機能を表現します。</span><span class="sxs-lookup"><span data-stu-id="57f45-146">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span> <span data-ttu-id="57f45-147">次のコード例から取得、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="57f45-147">The following example code is taken from the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="57f45-148">ポリシーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="57f45-148">Policy Export</span></span>  
 <span data-ttu-id="57f45-149">`UdpTransportBindingElement`実装を型 '<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType>ポリシーをエクスポートするためのサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="57f45-149">The `UdpTransportBindingElement` type implements``<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> to add support for exporting policy.</span></span> <span data-ttu-id="57f45-150">その結果、<xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> には、これを含む任意のバインディングでのポリシーの生成時に `UdpTransportBindingElement` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="57f45-150">As a result, <xref:System.ServiceModel.Description.MetadataExporter?displayProperty=nameWithType> includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="57f45-151"><xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType> では、UDP のアサーションを追加します。チャネルがマルチキャスト モードである場合は、別のアサーションを追加します。</span><span class="sxs-lookup"><span data-stu-id="57f45-151">In <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=nameWithType>, add an assertion for UDP and another assertion if the channel is in multicast mode.</span></span> <span data-ttu-id="57f45-152">これは、マルチキャスト モードは通信スタックの構築方法に影響を与えるため、両方の側において調整される必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="57f45-152">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```  
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.MulticastAssertion,     UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="57f45-153">カスタム トランスポート バインド要素はアドレス指定の処理を実行するため、<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> への `UdpTransportBindingElement` の実装でも、WS-Addressing ポリシー アサーションのエクスポートが処理されて、使用されている WS-Addressing のバージョンが示されます。</span><span class="sxs-lookup"><span data-stu-id="57f45-153">Because custom transport binding elements are responsible for handling addressing, the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="57f45-154">ポリシーのインポート</span><span class="sxs-lookup"><span data-stu-id="57f45-154">Policy Import</span></span>  
 <span data-ttu-id="57f45-155">ポリシー インポート システムを拡張するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57f45-155">To extend the policy import system, add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="57f45-156">次に、登録されたクラス (<xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType>) から `UdpBindingElementImporter` を実装します。</span><span class="sxs-lookup"><span data-stu-id="57f45-156">Then we implement <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="57f45-157"><xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType> で、適切な名前空間にあるアサーションを調べ、トランスポートを生成するためにそのアサーションを処理して、マルチキャストであるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="57f45-157">In <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, examine the assertions in the appropriate namespace and process the ones for generating the transport and checking if it is multicast.</span></span> <span data-ttu-id="57f45-158">さらに、インポーターが処理するアサーションをバインディング アサーションの一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="57f45-158">In addition, remove the assertions that the importer handles from the list of binding assertions.</span></span> <span data-ttu-id="57f45-159">Svcutil.exe を実行する場合、ここでも、統合用に次の 2 つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="57f45-159">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="57f45-160">/SvcutilConfig を使用して、構成ファイルに Svcutil.exe:\<ファイル >。</span><span class="sxs-lookup"><span data-stu-id="57f45-160">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="57f45-161">Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。</span><span class="sxs-lookup"><span data-stu-id="57f45-161">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="57f45-162">カスタムの標準バインディング インポーターの追加</span><span class="sxs-lookup"><span data-stu-id="57f45-162">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="57f45-163">Svcutil.exe と <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> 型は、既定でシステム指定のバインディングを識別してインポートします。</span><span class="sxs-lookup"><span data-stu-id="57f45-163">Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> type, by default, recognize and import system-provided bindings.</span></span> <span data-ttu-id="57f45-164">これ以外の場合、バインディングは、<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> インスタンスとしてインポートされます。</span><span class="sxs-lookup"><span data-stu-id="57f45-164">Otherwise, the binding gets imported as a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="57f45-165">Svcutil.exe と <xref:System.ServiceModel.Description.WsdlImporter> を有効にして `SampleProfileUdpBinding` をインポートする場合、`UdpBindingElementImporter` もカスタムの標準バインディング インポーターとして機能します。</span><span class="sxs-lookup"><span data-stu-id="57f45-165">To enable Svcutil.exe and the <xref:System.ServiceModel.Description.WsdlImporter> to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="57f45-166">カスタムの標準バインディング インポーターを実装し、`ImportEndpoint`メソッドを<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType>を調べるインターフェイス、<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>インスタンスのかどうかに生成するには特定の標準バインディングによって参照にメタデータからインポートされました。</span><span class="sxs-lookup"><span data-stu-id="57f45-166">A custom standard binding importer implements the `ImportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=nameWithType> interface to examine the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> instance imported from metadata to see if it could have been generated by specific standard binding.</span></span>  
  
```  
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="57f45-167">一般に、カスタムの標準バインディング インポーターを実装すると、インポートしたバインド要素のプロパティを調べて、標準バインディングによって設定されたプロパティのみが変更され、その他のすべてのプロパティは既定のままであることが検証されます。</span><span class="sxs-lookup"><span data-stu-id="57f45-167">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="57f45-168">標準バインディング インポーターを実装する場合の基本的な方法は、標準バインディングのインスタンスを作成し、標準バインディングがサポートするバインド要素のプロパティを標準バインディング インスタンスに反映し、標準バインディングのバインド要素とインポートしたバインド要素とを比較します。</span><span class="sxs-lookup"><span data-stu-id="57f45-168">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>
