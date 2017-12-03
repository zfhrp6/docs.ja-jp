---
title: "クライアント構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35dc7ad932ea114e2751fa86ceb757dc795795f5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="client-configuration"></a>クライアント構成
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアント構成は、クライアント エンドポイントのアドレス (Address)、バインディング (Binding)、動作 (Behavior)、およびコントラクト (Contract) の各プロパティ (頭文字を取って "ABC" プロパティと呼ばれます) を指定するために使用されます。また、これらのプロパティは、クライアントがサービス エンドポイントに接続するために使用されます。 [\<クライアント >](../../../../docs/framework/configure-apps/file-schema/wcf/client.md)要素には、 [\<エンドポイント >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)要素の属性を持つエンドポイントの abc プロパティの構成に使用します。 これらの属性については、このトピックの「エンドポイントの構成」で説明します。  
  
 [\<エンドポイント >](http://msdn.microsoft.com/en-us/13aa23b7-2f08-4add-8dbf-a99f8127c017)要素も含まれています、 [\<メタデータ >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)要素のインポートとエクスポートのメタデータの設定を指定するために使用する[ \<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)カスタムのアドレス ヘッダーのコレクションを格納する要素と[ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素を他のエンドポイントによるエンドポイントの認証を有効にします。メッセージを交換します。 [\<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)と[ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素の一部である、<xref:System.ServiceModel.EndpointAddress>で説明されているが、[アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)トピックです。 メタデータ拡張の使用法に関するトピックへのリンクは、このトピックの「メタデータの構成」にあります。  
  
## <a name="configuring-endpoints"></a>エンドポイントの構成  
 クライアントの構成が 1 つ指定するクライアントを許可するように設計されていますか、それぞれ独自の名前、複数のエンドポイント アドレス、およびコントラクトを各参照と、 [\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)と[ \<ビヘイビアー >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)そのエンドポイントを構成するために使用するクライアント構成内の要素。 クライアント構成ファイルには、"App.config" という名前を付ける必要があります。これは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイムが想定している名前です。 クライアント構成ファイルの例を次に示します。  
  
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
  
 省略可能な `name` 属性は、特定のコントラクトのエンドポイントを一意に識別します。 この属性は、サービスへのチャネルの作成時に、クライアント構成のどのエンドポイントをターゲットとし、読み込む必要があるかを指定するために、<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> または <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> が使用します。 エンドポイント構成名としてワイルドカード "*" を使用できます。これは、使用できるエンドポイント構成が 1 つだけ存在する場合はファイル内のエンドポイント構成を読み込み、それ以外の場合は例外をスローするように <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> メソッドに指示します。 この属性が省略されている場合、指定されたコントラクトの種類に関連する既定のエンドポイントとして、対応するエンドポイントが使用されます。 `name` 属性の既定値は、他の名前と同様に一致する空の文字列です。  
  
 すべてのエンドポイントには、エンドポイントを検索および識別するために、アドレスが関連付けられている必要があります。 `address` 属性は、エンドポイントの場所を示す URL を指定するために使用できます。 ただし、サービス エンドポイントのアドレスは、コードで指定することもできます。その場合は、URI (Uniform Resource Identifier) を作成し、<xref:System.ServiceModel.ServiceHost> メソッドのいずれかを使用して、この URI を <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> に追加します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)です。 概要が示されているように、 [\<ヘッダー >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)と[ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)要素の一部である、 <xref:System.ServiceModel.EndpointAddress> 」でも説明、および、 [アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)トピックです。  
  
 `binding` 属性は、エンドポイントがサービスに接続する際に使用するバインディングの種類を示します。 参照できるようにするには、種類は登録された構成セクションを持っている必要があります。 これは、前の例で、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)セクションでは、エンドポイントを使用することを示します、<xref:System.ServiceModel.WSHttpBinding>です。 ただし、エンドポイントが使用できる、指定された種類のバインディングが複数存在することもあります。 これらのそれぞれが独自[\<バインディング >](../../../../docs/framework/misc/binding.md)要素内部の要素 (バインド) の種類。 `bindingconfiguration` 属性は、同じ種類のバインディングを識別するために使用されます。 その値と対応している、`name`の属性、 [\<バインディング >](../../../../docs/framework/misc/binding.md)要素。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]クライアントを構成する方法の構成を使用したバインディングを参照してください[する方法: 構成でクライアント バインディングを指定](../../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)です。  
  
 `behaviorConfiguration`を指定する属性が使用される[\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)の[ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)エンドポイントを使用する必要があります。 その値と対応している、`name`の属性、 [\<動作 >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)要素。 クライアントの動作を指定する構成を使用しての例は、次を参照してください。[クライアントの動作を構成する](../../../../docs/framework/wcf/configuring-client-behaviors.md)です。  
  
 `contract` 属性は、エンドポイントが公開するコントラクトを指定します。 この値は、<xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> の <xref:System.ServiceModel.ServiceContractAttribute> にマップされます。 既定値は、サービスを実装するクラスの完全な型名です。  
  
### <a name="configuring-metadata"></a>メタデータの構成  
 [\<メタデータ >](../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)要素を使用して拡張機能をインポートするメタデータを登録するための設定を指定します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]メタデータ システムの拡張を参照してください[メタデータ システムの拡張](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)です。  
  
## <a name="see-also"></a>関連項目  
 [エンドポイント: アドレス、バインディング、およびコントラクト](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [クライアントの動作の構成](../../../../docs/framework/wcf/configuring-client-behaviors.md)
