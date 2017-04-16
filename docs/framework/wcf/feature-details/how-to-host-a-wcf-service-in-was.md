---
title: "方法 : WAS で WCF サービスをホストする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# 方法 : WAS で WCF サービスをホストする
ここでは、Windows プロセス アクティブ化サービス (WAS) でホストされる [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを作成するために必要な基本手順について説明します。 WAS は、HTTP 以外のトランスポート プロトコルで動作するインターネット インフォメーション サービス (IIS) 機能を一般化した新しいプロセス アクティブ化サービスです。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、リスナー アダプター インターフェイスを使用して、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされる HTTP 以外のプロトコル (TCP、名前付きパイプ、メッセージ キューなど) を介して受信されるアクティブ化要求を伝達します。  
  
 このホスト オプションでは、WAS アクティブ化コンポーネントのインストールと構成が正しく行われている必要がありますが、アプリケーションの一部としてホスト コードを記述する必要はありません。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]インストールと、WAS の構成を参照してください。[方法: WCF アクティブ化コンポーネントの構成のインストールおよび](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)です。  
  
> [!WARNING]
>  Web サーバーの要求処理パイプラインをクラシック モードに設定すると、WAS のアクティブ化がサポートされません。 WAS のアクティブ化を使用する場合は、Web サーバーの要求処理パイプラインを統合モードに設定する必要があります。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが WAS でホストされている場合、標準バインディングは通常の方法で使用されます。 ただしを使用する場合、 <xref:System.ServiceModel.NetTcpBinding>と<xref:System.ServiceModel.NetNamedPipeBinding> WAS でホストされるサービスを構成する、制限を遵守する必要があります。 つまり、異なるエンドポイントが同じトランスポートを使用する場合、次の&7; つのプロパティでバインディング設定が一致する必要があります。  
  
-   ConnectionBufferSize  
  
-   ChannelInitializationTimeout  
  
-   MaxPendingConnections  
  
-   MaxOutputDelay  
  
-   MaxPendingAccepts  
  
-   ConnectionPoolSettings.IdleTimeout  
  
-   ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint  
  
 それ以外の場合、まず初期化されているエンドポイント常に、これらのプロパティの値を決定し、後で追加したエンドポイントをスローする<xref:System.ServiceModel.ServiceActivationException>これらの設定と一致しない場合。  
  
 この例のソースのコピーを次を参照してください。 [TCP のアクティブ化](../../../../docs/framework/wcf/samples/tcp-activation.md)します。  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a>WAS でホストされる基本サービスを作成するには  
  
1.  サービスの種類にサービス コントラクトを定義します。  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2.  サービス クラスにサービス コントラクトを実装します。 アドレス情報とバインディング情報はサービスの実装内では指定されないことに注意してください。 同様に、コードは構成ファイルから情報を取得する必要はありません。  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3.  定義する Web.config ファイルを作成、 <xref:System.ServiceModel.NetTcpBinding>で使用するバインディングを`CalculatorService`エンドポイント。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4.  次のコードを含む Service.svc ファイルを作成します。  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  IIS 仮想ディレクトリに Service.svc ファイルを配置します。  
  
### <a name="to-create-a-client-to-use-the-service"></a>サービスを使用するクライアントを作成するには  
  
1.  使用[ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を使用してサービス メタデータからコードを生成します。  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  生成されたクライアントには、クライアントの実装時に満たされなければならないサービス コントラクトを定義する `ICalculator` インターフェイスが含まれます。  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3.  生成されたクライアント アプリケーションは `ClientCalculator` も実装します。 このサービスの実装では、アドレス情報とバインディング情報が指定されないことに注意してください。 同様に、コードは構成ファイルから情報を取得する必要はありません。  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4.  使用するクライアントの構成、 <xref:System.ServiceModel.NetTcpBinding>も Svcutil.exe によって生成されます。 Visual Studio を使用する場合は、このファイルの名前は App.config ファイル内で指定する必要があります。  
  
     [!code[C_HowTo_HostInWAS#2211](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]  
  
5.  アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6.  クライアントをコンパイルして実行します。  
  
## <a name="see-also"></a>関連項目  
 [TCP のアクティブ化](../../../../docs/framework/wcf/samples/tcp-activation.md)   
 [Windows Server App Fabric の機能をホストしています。](http://go.microsoft.com/fwlink/?LinkId=201276)