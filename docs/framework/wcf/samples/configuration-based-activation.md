---
title: "構成ベースのアクティブ化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# 構成ベースのアクティブ化
このサンプルでは、.svc ファイルを使用せずに [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをアクティブ化する方法を示します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## サンプルの詳細  
 このサンプルでは、クライアントは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアントで、サービスは IIS によってホストされています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
### .svc ファイルを必要としない、サービスのアクティブ化  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] では、サービスをアクティブ化するために .svc ファイルが必要でした。アプリケーションと共に追加ファイルを配置して管理する必要があったため、このことは管理のオーバーヘッドを増やす原因となりました。[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] リリースでは、アプリケーション構成ファイルを使用してアクティブ化コンポーネントを構成することができます。  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] では、アプリケーション構成ファイルの <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> に、新しい構成要素 <xref:System.ServiceModel.Configuration.ServiceActivationElement> が導入されています。<xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> コレクションは、次のコード例に示すように、サービスのコレクションを受け取ってアクティブ化を行います。  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
  
```  
  
 注目すべき点は、構成が .svc ファイルの構成に非常に似ていることです。導入された追加の属性は、サービスのアドレスを提供する `relativeAddress` です。相対アドレスは、サービスの仮想パスでもあります。ホストは、ファイルの Web.config ファイルが存在する場合に、そのファイルを `virtualPath` の場所から取得します。ファイルが存在しない場合、ホストはその親フォルダーを再帰的に検索します。  
  
> [!NOTE]
>  このサンプルを機能させるには、IIS でホストする必要があります。  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、Service.csproj ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  WCFTestClient.exe を実行してサービスをテストします。  
  
4.  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、%SystemDrive%\\Program Files\\Microsoft Visual Studio 10.0\\Common7\\IDE フォルダーに移動します。  
  
5.  WcfTestClient.exe を実行します。  
  
6.  サービスの MEX アドレスを設定します。  
  
7.  Ctrl と Shift キーを押しながら A キーを押して、サービス アドレスを設定します。  
  
8.  アドレスを http:\/\/localhost\/ServiceModelSamples\/Calculator.svc に設定します。  
  
9. `Add` 操作を実行します。`n1` パラメーターの値を 10 に、`n2` パラメーターの値を 15 に設定します。  
  
10. **\[起動\]** をクリックします。  
  
     予期される結果は 25 です。  
  
#### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  ソリューションがビルドされたら、Setup.bat を実行し、IIS で ServiceModelSamples アプリケーションを設定します。ServiceModelSamples ディレクトリは、IIS アプリケーションとして表示されます。  
  
4.  サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
## 参照  
 [AppFabric のホストおよび永続化のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)