---
title: "&lt;serviceMetadata&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# &lt;serviceMetadata&gt;
サービス メタデータと関連情報の公開を指定します。  
  
## 構文  
  
```  
  
<serviceMetadata   
    externalMetadataLocation="String"  
    httpGetBinding=”String”  
    httpGetBindingConfiguration=”String”  
    httpGetEnabled="Boolean"   
    httpGetUrl="String"  
    httpsGetBinding=”String”  
    httpsGetBindingConfiguration=”String”  
    httpsGetEnabled="Boolean"   
    httpsGetUrl="String"  
    policyVersion="Policy12/Policy15"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|externalMetadataLocation|WSDL ファイルの位置を含む URI。これは、自動生成される WSDL の代わりに、WSDL 要求および MEX 要求に応答してユーザーに返されます。  この属性が設定されていない場合は、既定の WSDL が返されます。  既定値は空の文字列です。|  
|httpGetBinding|HTTP GET 経由でメタデータを取得する場合に使用するバインディングの種類を指定する文字列。  この設定は省略可能です。  指定しない場合、既定のバインディングが使用されます。<br /><br /> <xref:System.ServiceModel.Channels.IReplyChannel> をサポートする内部バインディング要素を使用したバインディングでのみサポートされます。  さらに、バインディングの <xref:System.ServiceModel.Channels.MessageVersion%2A> プロパティが <xref:System.ServiceModel.Channels.MessageVersion.None%2A> である必要があります。|  
|httpGetBindingConfiguration|このバインディングの追加の構成情報を参照する `httpGetBinding` 属性に指定されるバインディングの名前を設定する文字列。  同じ名前を `<bindings>` セクションに定義する必要があります。|  
|httpGetEnabled|HTTP\/Get 要求を使用した取得用にサービス メタデータを公開するかどうかを指定するブール値。  既定値は、`false` です。<br /><br /> httpGetUrl 属性が指定されていない場合、メタデータが公開されるアドレスは、サービス アドレスに "?wsdl" を加えたものになります。  たとえば、サービス アドレスが "http:\/\/localhost:8080\/CalculatorService" の場合、HTTP\/Get メタデータ アドレスは、"http:\/\/localhost:8080\/CalculatorService?wsdl" になります。<br /><br /> このプロパティが `false` の場合、あるいはサービスのアドレスが HTTP または HTTPS に基づいていない場合、"?wsdl" は無視されます。|  
|httpGetUrl|HTTP\/Get 要求を使用した取得用にメタデータが公開されるアドレスを指定する URI。  相対 URI を指定した場合、サービスのベース アドレスに対する相対として処理されます。|  
|httpsGetBinding|HTTPS GET 経由でメタデータを取得する場合に使用するバインディングの種類を指定する文字列。  この設定は省略可能です。  指定しない場合、既定のバインディングが使用されます。<br /><br /> <xref:System.ServiceModel.Channels.IReplyChannel> をサポートする内部バインディング要素を使用したバインディングでのみサポートされます。  さらに、バインディングの <xref:System.ServiceModel.Channels.MessageVersion%2A> プロパティが <xref:System.ServiceModel.Channels.MessageVersion.None%2A> である必要があります。|  
|httpsGetBindingConfiguration|このバインディングの追加の構成情報を参照する `httpsGetBinding` 属性に指定されるバインディングの名前を設定する文字列。  同じ名前を `<bindings>` セクションに定義する必要があります。|  
|httpsGetEnabled|HTTPS\/Get 要求を使用した取得用にサービス メタデータを公開するかどうかを指定するブール値。  既定値は、`false` です。<br /><br /> httpsGetUrl 属性が指定されていない場合、メタデータが公開されるアドレスは、サービス アドレスに "?wsdl" を加えたものになります。  たとえば、サービス アドレスが "https:\/\/localhost:8080\/CalculatorService" の場合、HTTP\/Get メタデータ アドレスは、"https:\/\/localhost:8080\/CalculatorService?wsdl" になります。<br /><br /> このプロパティが `false` の場合、あるいはサービスのアドレスが HTTP または HTTPS に基づいていない場合、"?wsdl" は無視されます。|  
|httpsGetUrl|HTTPS\/Get 要求を使用した取得用にメタデータが公開されるアドレスを指定する URI。|  
|policyVersion|使用する WS\-Policy 仕様のバージョンを指定する文字列。  この属性は <xref:System.ServiceModel.Description.PolicyVersion> 型です。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<behavior\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|動作の要素を指定します。|  
  
## 解説  
 この構成要素を使用すると、サービスのメタデータ公開機能を制御できます。  サービスのメタデータには機密情報が含まれる可能性がありますが、意図的ではない開示を回避するために、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスの既定の構成では、メタデータは公開されないようになっています。  この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ公開の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール \(Svcutil.exe など\) を使用して生成できないことも意味します。  この構成要素を使用すると、サービスのこの公開動作を有効にできます。  
  
 この動作を構成する詳細なコード例については、「[メタデータ公開動作](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)」を参照してください。  
  
 オプションの `httpGetBinding` 属性および `httpsGetBinding` 属性を使用すると、HTTP GET または HTTPS GET を介してメタデータを取得するバインディングを構成できます。  これらの属性を指定しない場合、メタデータの取得には、適切な既定のバインディグ \(HTTP の場合は `HttpTransportBindingElement`、HTTPS の場合は `HttpsTransportBindingElement`\) が使用されます。  これらの属性は、組み込みの WCF バインディングでは使用できないことに注意してください。  <xref:System.ServiceModel.Channels.IReplyChannel> をサポートする内部バインディング要素を使用したバインディングでのみサポートされます。  さらに、バインディングの <xref:System.ServiceModel.Channels.MessageVersion%2A> プロパティが <xref:System.ServiceModel.Channels.MessageVersion.None%2A> である必要があります。  
  
 サービスが悪意のあるユーザーに公開されないようにするために、SSL over HTTP \(HTTPS\) 機構を使用して転送をセキュリティで保護できます。  転送を保護するには、まず、サービスをホストしているコンピューターの特定のポートに適切な X.509 証明書をバインドする必要があります。  \([!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)] [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。\) 次に、この要素をサービス構成に追加し、`httpsGetEnabled` 属性を `true` に設定します。  最後に、次の例に示すように、`httpsGetUrl` 属性をサービス メタデータ エンドポイントの URL に設定します。  
  
```  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"   
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## 使用例  
 次の例では、\<serviceMetadata\> 要素を使用してメタデータを公開するサービスを構成します。  さらに、`IMetadataExchange` コントラクトを WS\-MetadataExchange \(MEX\) プロトコルの実装として公開するエンドポイントも構成します。  この例では、`mexHttpBinding` を使用します。これは使いやすい標準バインドで、セキュリティ モードが `None` に設定されている `wsHttpBinding` と同等です。  エンドポイントには、相対アドレスの "mex" が使用されています。このアドレスがサービスのベース アドレスに対して解決されると、エンドポイントのアドレスは http:\/\/localhost\/servicemodelsamples\/service.svc\/mex になります。  
  
```  
<configuration>  
<system.serviceModel>  
  <services>  
    <service   
        name="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc  -->  
      <endpoint address=""  
                binding="wsHttpBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      <!-- the mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex   
           To expose the IMetadataExchange contract, you   
           must enable the serviceMetadata behavior as demonstrated below -->  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange" />  
    </service>  
  </services>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
        <!-- The serviceMetadata behavior publishes metadata through   
             the IMetadataExchange contract. When this behavior is   
             present, you can expose this contract through an endpoint   
             as shown above. Setting httpGetEnabled to true publishes   
             the service's WSDL at the <baseaddress>?wsdl  
             eg. http://localhost/servicemodelsamples/service.svc?wsdl -->  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  
</system.serviceModel>  
  
</configuration>  
```  
  
## 参照  
 <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>   
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>   
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)   
 [メタデータ公開動作](../../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)