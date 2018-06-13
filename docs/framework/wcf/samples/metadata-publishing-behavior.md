---
title: メタデータ公開動作
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 547ff9fcaca8b9af7a7559a11ef4c4a8b5996174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505522"
---
# <a name="metadata-publishing-behavior"></a>メタデータ公開動作
メタデータ公開動作のサンプルでは、サービスのメタデータ公開機能を制御する方法を示します。 機密性の高いサービス メタデータが誤って漏洩を防ぐためには、Windows Communication Foundation (WCF) サービスの既定の構成はメタデータの公開を無効にします。 この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ発行の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール (Svcutil.exe など) を使用して生成できないことも意味します。  
  
> [!IMPORTANT]
>  このサンプルでは、わかりやすくするために、セキュリティで保護されていないメタデータ公開エンドポイントを作成する方法を示します。 このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。 参照してください、[カスタム セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)メタデータ エンドポイントをセキュリティで保護するサンプルのサンプルです。  
  
 サンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)を実装する、`ICalculator`サービス コントラクト。 この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービスでメタデータを公開するには、サービス上に <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を構成する必要があります。 この動作が存在する場合は、エンドポイントを構成してメタデータを公開し、<xref:System.ServiceModel.Description.IMetadataExchange> コントラクトを WS-MetadataExchange (MEX) プロトコルの実装として公開できます。 便宜上、このコントラクトには、構成名を略した "IMetadataExchange" という名前が付けられています。 このサンプルでは、`mexHttpBinding` を使用します。これは使いやすい標準バインディングで、セキュリティ モードが `wsHttpBinding` に設定されている `None` と同等です。 相対アドレスの"mex"が使用されるエンドポイントには、どのに対して解決とサービスのベース アドレスのエンドポイント アドレスhttp://localhost/servicemodelsamples/service.svc/mexです。 この動作の構成を次に示します。  
  
```xml  
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
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 このサンプルでは、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true` に設定します。これにより、HTTP GET を使用してサービスのメタデータも公開されます。 HTTP GET メタデータのエンドポイントを有効にするには、サービスに HTTP ベース アドレスが設定されている必要があります。 クエリ文字列 `?wsdl` は、メタデータにアクセスするサービスのベース アドレスで使用されます。 たとえば、Web ブラウザーでサービスの WSDL を表示するとアドレスを使用する、http://localhost/servicemodelsamples/service.svc?wsdlです。 または、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> を `true` に設定してこの動作を使用することにより、HTTPS を通じてメタデータを公開することもできます。 これには、HTTPS ベース アドレスが必要です。  
  
 サービスの MEX エンドポイントの使用にアクセスする、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 これにより、サービスのメタデータに基づくクライアントが生成されます。  
  
 HTTP GET を使用して、サービスのメタデータにアクセスするには、ブラウザーをポイントhttp://localhost/servicemodelsamples/service.svc?wsdlです。  
  
 この動作を削除してサービスを開こうとすると、例外が発生します。 動作がない場合にこのエラーが発生するのは、`IMetadataExchange` コントラクトを使用して構成されたエンドポイントに実装が存在しないからです。  
  
 `HttpGetEnabled` を `false` に設定すると、サービスのメタデータが表示される代わりに CalculatorService ヘルプ ページが表示されます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a>関連項目
