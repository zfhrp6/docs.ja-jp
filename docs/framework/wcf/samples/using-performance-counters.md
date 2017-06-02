---
title: "パフォーマンス カウンターの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
caps.latest.revision: 31
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 31
---
# パフォーマンス カウンターの使用
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] パフォーマンス カウンタにアクセスする方法と、ユーザー定義のパフォーマンス カウンタを作成する方法を示します。このサンプルは、「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、クライアントが `ICalculator` サービスの 4 つのメソッドを呼び出します。この処理は、ユーザーが中断するまで継続して行われます。サービスは変更されません。  
  
 パフォーマンス カウンタは、サービスの Web.config ファイルの診断セクションで有効にします。次のサンプル構成を参照してください。  
  
```  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 このタスクは、[構成エディター ツール \(SvcConfigEditor.exe\)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) を使用して実行することもできます。  
  
 パフォーマンス カウンタが有効な場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] パフォーマンス カウンタのスイート全体がサービスについて有効です。.NET Framework は、`ServiceModelService`、`ServiceModelEndpoint`、および `ServiceModelOperation` の 3 つのレベルで、パフォーマンス データを自動的に保持します。これらの各レベルには、"呼び出し"、"1 秒あたりの呼び出し回数"、"承認されていないセキュリティ呼び出し" などのパフォーマンス カウンタがあります。  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
### パフォーマンス データを表示するには  
  
1.  **\[スタート\]** ボタンをクリックし、**\[ファイル名を指定して実行\]** をクリックして「`perfmon`」と入力してから **\[OK\]** をクリックするか、または、\[コントロール パネル\] の **\[管理ツール\]** を開き、**\[パフォーマンス\]** をダブルクリックして、パフォーマンス モニタ ツールを開始します。  
  
    > [!NOTE]
    >  サンプル コードが実行されるまでは、カウンタを追加することはできません。  
  
2.  一覧表示されているパフォーマンス カウンタを削除するには、削除するパフォーマンス カウンタを選択して Del キーを押します。  
  
3.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] カウンタを追加するには、グラフ ウィンドウを右クリックし、**\[カウンタの追加\]** をクリックします。**\[カウンタの追加\]** ダイアログ ボックスで、\[パフォーマンス オブジェクト\] ボックスの一覧から **\[ServiceModelOperation 3.0.0.0\]、\[ServiceModelEndpoint 3.0.0.0\]、または \[ServiceModelService 3.0.0.0\]** を選択します。表示するカウンタを一覧から選択します。  
  
    > [!NOTE]
    >  コンピューター上で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが実行されていない場合は、サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] パフォーマンス カウンターは存在しません。  
  
### 構成エディターを使用してカウンターを有効にするには  
  
1.  SvcConfigEditor.exe のインスタンスを開きます。  
  
2.  \[ファイル\] メニューの **\[開く\]** をクリックし、**\[構成ファイル...\]** をクリックします。  
  
3.  サンプル アプリケーションの service フォルダーに移動し、Web.config ファイルを開きます。  
  
4.  構成ツリーの **\[診断\]** をクリックします。  
  
5.  **\[診断\]** ウィンドウの  **\[パフォーマンス カウンター\]** の表示を "すべて" に切り替えます。  
  
6.  構成ファイルを保存し、エディターを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## 参照  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)