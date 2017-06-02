---
title: "SQL 追跡 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# SQL 追跡
このサンプルでは、追跡レコードを SQL データベースに書き込むカスタム SQL 追跡参加要素を作成する方法を示します。[!INCLUDE[wf](../../../../includes/wf-md.md)] には、ワークフロー インスタンスの実行を視覚的に示すワークフロー追跡機能が用意されています。追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。ワークフロー追跡機能[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、[ワークフロー追跡とトレース](../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)を参照してください。  
  
#### このサンプルを使用するには  
  
1.  SQL Server 2008、SQL Server 2008 Express、またはそれ以降のバージョンがインストールされていることを確認します。サンプルと共にパッケージ化されているスクリプトは、SQL Express インスタンスをローカル コンピューターで使用していることが前提になります。別のインスタンスがある場合は、データベース関連のスクリプトを変更してからサンプルを実行してください。  
  
2.  Scripts ディレクトリ \(\\WF\\Basic\\Tracking\\SqlTracking\\CS\\Scripts\) 内で Trackingsetup.cmd を実行して SQL Server 追跡データベースを作成します。これによって、TrackingSample という名前のデータベースが作成されます。  
  
    > [!NOTE]
    >  このスクリプトでは、SQL Express の既定のインスタンスにデータベースが作成されます。別のデータベース インスタンスにインストールする場合は、Trackingsetup.cmd スクリプトを編集してください。  
  
3.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で SqlTrackingSample.sln を開きます。  
  
4.  Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
5.  F5 キーを押してアプリケーションを実行します。  
  
     ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。  
  
6.  ブラウザーで、StockPriceService.xamlx をクリックします。  
  
7.  ブラウザーに、\[StockPriceService\] ページが表示され、ローカル サービスの WSDL アドレスが示されます。このアドレスをコピーします。  
  
     ローカル サービスの WSDL アドレスは、http:\/\/localhost:65193\/StockPriceService.xamlx?wsdl などになります。  
  
8.  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、WCF テスト クライアント \(WcfTestClient.exe\) を実行します。このテスト クライアントは Microsoft Visual Studio 10.0\\Common7\\IDE ディレクトリにあります。  
  
9. WCF テスト クライアントで、**\[ファイル\]** メニューの **\[サービスの追加\]** をクリックします。テキスト ボックスにローカル サービスのアドレスを貼り付けます。**\[OK\]** をクリックしてダイアログ ボックスを閉じます。  
  
10. WCF テスト クライアントで、**\[GetStockPrice\]** をダブルクリックします。これで、1 つのパラメーターを使用する `GetStockPrice` 操作が開きます。「`Contoso`」という値を入力し、**\[呼び出し\]** をクリックします。  
  
11. 出力された追跡レコードが SQL データベースに書き込まれます。追跡レコードを表示するには、SQL Management Studio で TrackingSample データベースを開き、テーブルに移動します。SQL Server Management Studio [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[SQL Server Management Studio の概要](http://go.microsoft.com/fwlink/?LinkId=165645)」を参照してください。SQL Server 2008 Management Studio Express は、[ここ](http://go.microsoft.com/fwlink/?LinkId=180520)からダウンロードできます。テーブルで選択クエリを実行すると、それぞれのテーブルに格納されている追跡レコード内のデータが表示されます。  
  
#### サンプルをアンインストールするには  
  
1.  サンプル ディレクトリ \(\\WF\\Basic\\Tracking\\SqlTracking\) で Trackingcleanup.cmd スクリプトを実行します。  
  
    > [!NOTE]
    >  Trackingcleanup.cmd は、ローカル コンピューターの SQL Express 内にあるデータベースを削除しようとします。別の SQL Server インスタンスを使用している場合は、Trackingcleanup.cmd を編集します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## 参照  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)