---
title: "方法 : マネージ Windows サービスで WCF サービスをホストする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# 方法 : マネージ Windows サービスで WCF サービスをホストする
ここでは、Windows サービスでホストされる [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを作成するために必要な基本手順について説明します。このシナリオは、マネージ Windows サービスのホスト オプションによって有効になります。このサービスは、メッセージがアクティブ化されていない、セキュリティ保護された環境において、インターネット インフォメーション サービス \(IIS\) の外部でホストされ、長時間実行される [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。サービスの有効期限は代わりにオペレーティング システムによって制御されます。このホスト オプションは Windows のすべてのバージョンで使用できます。  
  
 Windows サービスは、Microsoft 管理コンソール \(MMC\) の Microsoft.ManagementConsole.SnapIn を使用して管理し、システムのブート時に自動的に起動するように構成できます。このホスト オプションは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをマネージ Windows サービスとしてホストするアプリケーション ドメイン \(AppDomain\) の登録から構成されているため、サービスのプロセス有効期間は Windows サービスのサービス コントロール マネージャー \(SCM\) によって制御されます。  
  
 サービス コードには、サービス コントラクトのサービス実装、Windows サービス クラス、およびインストーラー クラスが含まれています。サービス実装クラスである `CalculatorService` は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。一方、`CalculatorWindowsService` は Windows サービスです。Windows サービスとして限定するため、このクラスは `ServiceBase` を継承し、`OnStart` メソッドと `OnStop` メソッドを実装しています。`OnStart` では、`CalculatorService` 型の <xref:System.ServiceModel.ServiceHost> が作成され、開かれます。`OnStop` では、このサービスが停止され、破棄されます。ホストはベース アドレスをサービス ホストに提供する必要もあります。サービス ホストは、アプリケーション設定で構成されます。インストーラー クラスは <xref:System.Configuration.Install.Installer> を継承します。このクラスを使用すると、Installutil.exe ツールにより、プログラムを Windows サービスとしてインストールできます。  
  
### サービスを構築してホスティング コードを提供する  
  
1.  "Service" という新しい Visual Studio Console Application プロジェクトを作成します。  
  
2.  Program.cs を Service.cs に変更します。  
  
3.  名前空間を Microsoft.ServiceModel.Samples に変更します。  
  
4.  次のアセンブリへの参照を追加します。  
  
    -   System.ServiceModel.dll  
  
    -   System.ServiceProcess.dll  
  
    -   System.Configuration.Install.dll  
  
5.  次の using ステートメントを Service.cs に追加します。  
  
     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]  
  
6.  次のコードに示すように、`ICalculator` サービス コントラクトを定義します。  
  
     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]  
  
7.  次のコードに示すように、`CalculatorService` というクラスにサービス コントラクトを実装します。  
  
     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]  
  
8.  <xref:System.ServiceProcess.ServiceBase> クラスから継承する `CalculatorWindowsService` という新しいクラスを作成します。`serviceHost` というローカル変数を追加して、<xref:System.ServiceModel.ServiceHost> インスタンスを参照します。`ServiceBase.Run(new CalculatorWindowsService)` を呼び出す `Main` というメソッドを定義します。  
  
     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]  
  
9. 次のコードに示すように、新しい <xref:System.ServiceModel.ServiceHost> インスタンスを作成して開くことによって [OnStart\(String\<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> メソッドをオーバーライドします。  
  
     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]  
  
10. 次のコードに示すように、<xref:System.ServiceModel.ServiceHost> を閉じて <xref:System.ServiceProcess.ServiceBase.OnStop%2A> メソッドをオーバーライドします。  
  
     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]  
  
11. <xref:System.Configuration.Install.Installer> から継承し、`true` に設定された <xref:System.ComponentModel.RunInstallerAttribute> でマークされた `ProjectInstaller` という新しいクラスを作成します。これで、Installutil.exe ツールで Windows サービスをインストールできるようになります。  
  
     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]  
  
12. プロジェクトを作成したときに生成された `Service` クラスを削除します。  
  
13. アプリケーション構成ファイルをプロジェクトに追加します。ファイルの内容を次の構成 XML に置き換えます。  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>    <services>  
          <!-- This section is optional with the new configuration model  
               introduced in .NET Framework 4. -->  
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                   behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
            <endpoint address=""  
                      binding="wsHttpBinding"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceMetadata httpGetEnabled="true"/>  
              <serviceDebug includeExceptionDetailInFaults="False"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     **ソリューション エクスプローラー**で App.config ファイルを右クリックし、**\[プロパティ\]** をクリックします。**\[出力ディレクトリにコピー\]** の下で **\[新しい場合はコピーする\]** を選択します。  
  
     この例では、構成ファイルにエンドポイントを明示的に指定します。エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。この例では、サービスには `true` に設定された <xref:System.ServiceModel.Description.ServiceMetadataBehavior> があるので、サービスで公開メタデータも有効化されています。既定のエンドポイント、バインディング、および動作[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)」および「[WCF サービスの簡略化された構成](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)」を参照してください。  
  
### サービスをインストールして実行する  
  
1.  ソリューションをビルドして `Service.exe` 実行可能ファイルを作成します。  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを開き、プロジェクト ディレクトリに移動します。コマンド プロンプトで「`installutil bin\service.exe`」と入力して、Windows サービスをインストールします。  
  
    > [!NOTE]
    >  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを使用しない場合、`%WinDir%\Microsoft.NET\Framework\v4.0.<current version>` ディレクトリがシステム パスにあることを確認してください。  
  
     コマンド プロンプトで「`services.msc`」と入力してサービス コントロール マネージャー \(SCM\) にアクセスします。Windows サービスは、\[Services\] に "WCFWindowsServiceSample" として表示されます。Windows サービスが実行されている場合、クライアントに応答できるサービスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのみです。サービスを開始するには、SCM でそのサービスを右クリックして \[Start\] をクリックするか、コマンド プロンプトで「**net start WCFWindowsServiceSample**」と入力します。  
  
3.  サービスを変更する場合は、まずそのサービスを停止してからアンインストールする必要があります。サービスを停止するには、SCM でそのサービスを右クリックして \[Stop\] をクリックするか、コマンド プロンプトで「**type net stop WCFWindowsServiceSample**」と入力します。Windows サービスを停止してクライアントを実行すると、クライアントがこのサービスにアクセスしようとしたときに <xref:System.ServiceModel.EndpointNotFoundException> 例外が発生することに注意してください。Windows サービスをアンインストールするには、コマンド プロンプトで「**installutil \/u bin\\service.exe**」と入力します。  
  
## 使用例  
 このトピックで使用されているコードの完全な一覧を次に示します。  
  
 [!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
 [!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]  
  
 "自己ホスト" オプションと同様、Windows サービス ホスト環境では、ホスト コードをアプリケーションの一部として記述する必要があります。サービスはコンソール アプリケーションとして実装され、独自のホスティング コードが指定されます。インターネット インフォメーション サービス \(IIS\) でホストされる Windows プロセス アクティブ化サービス \(WAS\) など、他のホスト環境ではホスティング コードを記述する必要はありません。  
  
## 参照  
 [簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)   
 [マネージ アプリケーションのホスト](../../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md)   
 [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)   
 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)