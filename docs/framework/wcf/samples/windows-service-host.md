---
title: "Windows サービス ホスト | Microsoft Docs"
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
helpviewer_keywords: 
  - "NT サービス"
  - "NT サービス ホスト サンプル [Windows Communication Foundation]"
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
caps.latest.revision: 40
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 40
---
# Windows サービス ホスト
このサンプルでは、マネージ Windows サービスでホストされる [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを示します。Windows サービスは、**\[コントロール パネル\]** のサービス アプレットを使用して制御されます。また、システムの再起動後に自動的に開始するように構成できます。このサンプルは、クライアント プログラムと Windows サービス プログラムで構成されています。サービスは .exe プログラムとして実装され、独自のホスティング コードが指定されます。Windows プロセス アクティブ化サービス \(WAS\) やインターネット インフォメーション サービス \(IIS\) などの他のホスト環境では、ホスティング コードを記述する必要はありません。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 このサービスをビルドしたら、他の Windows サービスと同様、Installutil.exe ユーティリティを使用してインストールする必要があります。サービスを変更する場合は、`installutil /u` を使用して、まずそのサービスをアンインストールする必要があります。このサンプルに含まれている Setup.bat ファイルは Windows Service をインストールして起動するコマンド ファイルです。同様にこのサンプルに含まれている Cleanup.bat ファイルは、Windows サービスをシャットダウンしてアンインストールするコマンド ファイルです。Windows サービスが実行されている場合、クライアントに応答できるサービスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのみです。**\[コントロール パネル\]** のサービス アプレットを使用して Windows サービスを停止し、クライアントを実行した場合、クライアントがこのサービスにアクセスしようとすると、<xref:System.ServiceModel.EndpointNotFoundException> 例外が発生します。Windows サービスを再起動してクライアントを再実行した場合は、通信が正常に行われます。  
  
 サービス コードにはインストーラー クラス、ICalculator コントラクトを実装する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス実装クラス、およびランタイム ホストとして機能する Windows サービス クラスが含まれています。インストーラー クラスは <xref:System.Configuration.Install.Installer> を継承します。このクラスを使用すると、Installutil.exe ツールにより、プログラムを NT サービスとしてインストールできます。サービス実装クラス `WcfCalculatorService` は、基本的なサービス コントラクトを実装する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。この [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、`WindowsCalculatorService` と呼ばれる Windows サービス クラス内でホストされます。Windows サービスとして限定するため、このクラスは <xref:System.ServiceProcess.ServiceBase> を継承し、[OnStart\(String\<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop> メソッドを実装しています。[OnStart\(String\<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> では、`WcfCalculatorService` 型の <xref:System.ServiceModel.ServiceHost> オブジェクトが作成され、開かれます。<xref:System.ServiceProcess.ServiceBase.OnStop> では、<xref:System.ServiceModel.ServiceHost> オブジェクトの <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> メソッドが呼び出されて ServiceHost が閉じられます。このホストのベース アドレスは、[\<add\>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) 要素を使用して構成されます。この要素は [\<baseAddresses\>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md) の子で、これは [\<host\>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) 要素の子です。さらに、その親は [\<service\>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) 要素です。  
  
 定義されるエンドポイントは、ベース アドレスおよび [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) を使用します。ベース アドレスの構成と CalculatorService を公開するエンドポイントのサンプルを次に示します。  
  
```  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
```  
  
 このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  ソリューションがビルドされたら、権限のレベルが高い [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトから Setup.bat を実行し、Installutil.exe ツールを使用して Windows サービスをインストールしてください。このサービスは、\[サービス\] に表示されます。  
  
4.  サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
## 参照  
 [AppFabric のホストおよび永続化のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)