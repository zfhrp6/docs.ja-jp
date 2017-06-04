---
title: "構成とメタデータのサポート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27c240cb-8cab-472c-87f8-c864f4978758
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# 構成とメタデータのサポート
ここでは、バインディングおよびバインド要素用に構成とメタデータのサポートを有効にする方法を説明します。  
  
## 構成とメタデータの概要  
 ここでは、次の作業について説明します。これは、[チャネルの開発](../../../../docs/framework/wcf/extending/developing-channels.md)タスク リストのオプション項目 1.、2. および 4. に当たります。  
  
-   バインド要素の構成ファイル サポートを有効にします。  
  
-   バインディングの構成ファイル サポートを有効にします。  
  
-   バインド要素の WSDL とポリシー アサーションをエクスポートします。  
  
-   バインディングまたはバインド要素に挿入して構成する WSDL とポリシー アサーションを特定します。  
  
 ユーザー定義バインディングおよびバインド要素の作成の詳細については、それぞれ「[ユーザー定義バインディングの作成](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)」および「[BindingElement の作成](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)」を参照してください。  
  
## 構成サポートの追加  
 チャネルに対する構成ファイルのサポートを有効にするには、2 つの構成セクションを実装する必要があります。1 つはバインド要素に対する構成のサポートを有効にする <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=fullName> で、もう 1 つはバインディングに対する構成のサポートを有効にする <xref:System.ServiceModel.Configuration.StandardBindingElement?displayProperty=fullName> と <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602?displayProperty=fullName> です。  
  
 これを行う簡単な方法は、[ConfigurationCodeGenerator](../../../../docs/framework/wcf/samples/configurationcodegenerator.md) サンプル ツールを使用して、バインディングおよびバインド要素の構成コードを生成することです。  
  
### BindingElementExtensionElement の拡張  
 次のコード例は、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) のサンプルから取られています。`UdpTransportElement` は `UdpTransportBindingElement` を構成システムに公開する <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> です。いくつかの基本的なオーバーライドを行うことで、サンプルでは構成セクション名、バインド要素の種類とバインド要素の作成方法が定義されます。その後、次のようにして拡張セクションを構成ファイルに登録できます。  
  
```  
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
  
 この拡張は、UDP をトランスポートとして使用するためにカスタム バインディングから参照されます。  
  
```  
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
  
### バインディングの構成の追加  
 セクション `SampleProfileUdpBindingCollectionElement` は <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> で、`SampleProfileUdpBinding` を構成システムに公開します。実装の大部分は `SampleProfileUdpBindingConfigurationElement` で代行されます。これは <xref:System.ServiceModel.Configuration.StandardBindingElement> の派生です。`SampleProfileUdpBindingConfigurationElement` には `SampleProfileUdpBinding` にあるプロパティに対応するプロパティがあり、`ConfigurationElement` バインディングからマップする関数があります。次のサンプル コードで示すように、最後に、`OnApplyConfiguration` メソッドが `SampleProfileUdpBinding` 内でオーバーライドされます。  
  
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
  
 このハンドラーを構成システムに登録するには、次のセクションを関連する構成ファイルに追加します。  
  
```  
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
  
 これは [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 構成セクションから参照できます。  
  
```  
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
  
## バインド要素のメタデータ サポートの追加  
 チャネルをメタデータ システムに統合するには、ポリシーのインポートとエクスポートの両方がサポートされている必要があります。これにより、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) などのツールでバインド要素のクライアントを生成できます。  
  
### WSDL サポートの追加  
 バインディングのトランスポート バインド要素は、メタデータのアドレス指定情報のインポートとエクスポートを行います。SOAP バインディングを使用する場合は、トランスポート バインド要素によっても、メタデータの正しいトランスポート URI がエクスポートされます。次のコード例は、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) のサンプルから取られています。  
  
#### WSDL エクスポート  
 アドレス指定情報をエクスポートするために、`UdpTransportBindingElement` は <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=fullName> インターフェイスを実装しています。<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A?displayProperty=fullName> メソッドにより、正しいアドレス指定情報が WSDL ポートに追加されます。  
  
```  
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 エンドポイントが SOAP バインディングを使用する場合、<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> メソッドの `UdpTransportBindingElement` の実装でも、次のようにトランスポート URI がエクスポートされます。  
  
```  
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### WSDL インポート  
 WSDL インポート システムを拡張してアドレスのインポートを処理するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。  
  
```  
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
  
 Svcutil.exe を実行する場合、Svcutil.exe に WSDL インポートの拡張を読み込ませるために次の 2 つのオプションがあります。  
  
1.  \/SvcutilConfig:\<ファイル名\> を使用して、Svcutil.exe に構成ファイルを指定します。  
  
2.  Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。  
  
 `UdpBindingElementImporter` 型は <xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=fullName> インターフェイスを実装します。`ImportEndpoint` メソッドは、次のようにして WSDL ポートからアドレスをインポートします。  
  
```  
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### ポリシー サポートの追加  
 カスタム バインド要素では、WSDL バインディング内のポリシー アサーションをエクスポートして、サービス エンドポイントでそのバインド要素の機能を表現します。次のコード例は、[トランスポート: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) のサンプルから取られています。  
  
#### ポリシーのエクスポート  
 `UdpTransportBindingElement` 型はポリシーのエクスポートをサポートするために ``<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> を実装します。その結果、<xref:System.ServiceModel.Description.MetadataExporter?displayProperty=fullName> には、これを含む任意のバインディングでのポリシーの生成時に `UdpTransportBindingElement` が含まれます。  
  
 <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A?displayProperty=fullName> では、UDP のアサーションを追加します。チャネルがマルチキャスト モードである場合は、別のアサーションを追加します。これは、マルチキャスト モードは通信スタックの構築方法に影響を与えるため、両方の側において調整される必要があるためです。  
  
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
  
 カスタム トランスポート バインド要素はアドレス指定の処理を実行するため、`UdpTransportBindingElement` への <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> の実装でも、WS\-Addressing ポリシー アサーションのエクスポートが処理されて、使用されている WS\-Addressing のバージョンが示されます。  
  
```  
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### ポリシーのインポート  
 ポリシー インポート システムを拡張するには、次の構成を Svcutil.exe の構成ファイルに追加する必要があります。Svcutil.exe.config ファイルの次の例を参照してください。  
  
```  
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
  
 次に、登録されたクラス \(`UdpBindingElementImporter`\) から <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName> を実装します。<xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=fullName> で、適切な名前空間にあるアサーションを調べ、トランスポートを生成するためにそのアサーションを処理して、マルチキャストであるかどうかをチェックします。さらに、インポーターが処理するアサーションをバインディング アサーションの一覧から削除します。Svcutil.exe を実行する場合、ここでも、統合用に次の 2 つのオプションがあります。  
  
1.  \/SvcutilConfig:\<ファイル名\> を使用して、Svcutil.exe に構成ファイルを指定します。  
  
2.  Svcutil.exe と同じディレクトリにある Svcutil.exe.config に構成セクションを追加します。  
  
### カスタムの標準バインディング インポーターの追加  
 Svcutil.exe と <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=fullName> 型は、既定でシステム指定のバインディングを識別してインポートします。これ以外の場合、バインディングは、<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName> インスタンスとしてインポートされます。Svcutil.exe と <xref:System.ServiceModel.Description.WsdlImporter> を有効にして `SampleProfileUdpBinding` をインポートする場合、`UdpBindingElementImporter` もカスタムの標準バインディング インポーターとして機能します。  
  
 カスタムの標準バインディング インポーターは、<xref:System.ServiceModel.Description.IWsdlImportExtension?displayProperty=fullName> インターフェイスに `ImportEndpoint` メソッドを実装しており、メタデータからインポートされた <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName> インスタンスを調べて、これが特定の標準バインディングによって生成されたものであるかどうかを判別できます。  
  
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
  
 一般に、カスタムの標準バインディング インポーターを実装すると、インポートしたバインド要素のプロパティを調べて、標準バインディングによって設定されたプロパティのみが変更され、その他のすべてのプロパティは既定のままであることが検証されます。標準バインディング インポーターを実装する場合の基本的な方法は、標準バインディングのインスタンスを作成し、標準バインディングがサポートするバインド要素のプロパティを標準バインディング インスタンスに反映し、標準バインディングのバインド要素とインポートしたバインド要素とを比較します。