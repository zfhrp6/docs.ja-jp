---
title: "メタデータ公開動作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "メタデータ公開動作のサンプル [Windows Communication Foundation]"
  - "サービスの動作, メタデータ公開のサンプル"
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# メタデータ公開動作
メタデータ公開動作のサンプルでは、サービスのメタデータ公開機能を制御する方法を示します。サービスのメタデータには機密情報が含まれる可能性がありますが、意図的ではない開示を回避するために、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスの既定の構成では、メタデータは公開されないように設定されています。この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ公開の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール \(Svcutil.exe など\) を使用して生成できないことも意味します。  
  
> [!IMPORTANT]
>  このサンプルではわかりやすくするために、セキュリティで保護されていないメタデータ公開エンドポイントを作成する方法を示します。こうしたエンドポイントは、認証されていない匿名の利用者が利用できる可能性があります。これらのエンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに公開することが適切かどうか確認する必要があります。メタデータ エンドポイントをセキュリティ保護するサンプルについては、「[カスタム セキュア メタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)」のサンプルを参照してください。  
  
 このサンプルは、`ICalculator` サービス コントラクトを実装する「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。この例では、クライアントはコンソール アプリケーション \(.exe\) で、サービスはインターネット インフォメーション サービス \(IIS\) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービスでメタデータを公開するには、サービス上に <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を構成する必要があります。この動作が存在する場合は、エンドポイントを構成してメタデータを公開し、<xref:System.ServiceModel.Description.IMetadataExchange> コントラクトを WS\-MetadataExchange \(MEX\) プロトコルの実装として公開できます。便宜上、このコントラクトには、構成名を略した "IMetadataExchange" という名前が付けられています。このサンプルでは、`mexHttpBinding` を使用します。これは使いやすい標準バインディングで、セキュリティ モードが `None` に設定されている `wsHttpBinding` と同等です。エンドポイントには、相対アドレスの "mex" が使用されています。このアドレスがサービスのベース アドレスに対して解決されると、エンドポイントのアドレスは http:\/\/localhost\/servicemodelsamples\/service.svc\/mex になります。この動作の構成を次に示します。  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 MEX エンドポイントを次に示します。  
  
```  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 このサンプルでは、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true` に設定します。これにより、HTTP GET を使用してサービスのメタデータも公開されます。HTTP GET メタデータのエンドポイントを有効にするには、サービスに HTTP ベース アドレスが設定されている必要があります。クエリ文字列 `?wsdl` は、メタデータにアクセスするサービスのベース アドレスで使用されます。たとえば、Web ブラウザでサービスの WSDL を表示するには、アドレス http:\/\/localhost\/servicemodelsamples\/service.svc?wsdl を使用します。または、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> を `true` に設定してこの動作を使用することにより、HTTPS を通じてメタデータを公開することもできます。これには、HTTPS ベース アドレスが必要です。  
  
 サービスの MEX エンドポイントにアクセスするには、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用します。  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 これにより、サービスのメタデータに基づくクライアントが生成されます。  
  
 HTTP GET を使用してサービスのメタデータにアクセスするには、ブラウザで http:\/\/localhost\/servicemodelsamples\/service.svc?wsdl を指定します。  
  
 この動作を削除してサービスを開こうとすると、例外が発生します。動作がない場合にこのエラーが発生するのは、`IMetadataExchange` コントラクトを使用して構成されたエンドポイントに実装が存在しないからです。  
  
 `HttpGetEnabled` を `false` に設定すると、サービスのメタデータが表示される代わりに CalculatorService ヘルプ ページが表示されます。  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  単一コンピューター構成か複数コンピューター構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## 参照