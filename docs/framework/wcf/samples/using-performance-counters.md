---
title: パフォーマンス カウンターの使用
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 2e25551494a433c53832127fdb0a32cb4eccac47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-performance-counters"></a>パフォーマンス カウンターの使用
このサンプルでは、ユーザー定義のパフォーマンス カウンターを作成する方法と Windows Communication Foundation (WCF) パフォーマンス カウンターにアクセスする方法を示します。 このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルでは、クライアントが `ICalculator` サービスの 4 つのメソッドを呼び出します。 この処理は、ユーザーが中断するまで継続して行われます。 サービスは変更されません。  
  
 パフォーマンス カウンタは、サービスの Web.config ファイルの診断セクションで有効にします。次のサンプル構成を参照してください。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 このタスクを実行することもを使用して、[構成エディター ツール (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)です。  
  
 パフォーマンス カウンタが有効な場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] パフォーマンス カウンタのスイート全体がサービスについて有効です。 .NET Framework は、`ServiceModelService`、`ServiceModelEndpoint`、および `ServiceModelOperation` の 3 つのレベルで、パフォーマンス データを自動的に保持します。 これらの各レベルには、"呼び出し"、"1 秒あたりの呼び出し回数"、"承認されていないセキュリティ呼び出し" などのパフォーマンス カウンタがあります。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
### <a name="to-view-performance-data"></a>パフォーマンス データを表示するには  
  
1.  ツールを起動、パフォーマンス モニター をクリックして**開始**、**を実行しています.**、入力`perfmon` をクリック**ok、**またはコントロール パネルから選択**管理ツール** をダブルクリック**パフォーマンス**です。  
  
    > [!NOTE]
    >  サンプル コードが実行されるまでは、カウンタを追加することはできません。  
  
2.  一覧表示されているパフォーマンス カウンタを削除するには、削除するパフォーマンス カウンタを選択して Del キーを押します。  
  
3.  追加[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]グラフ ウィンドウを右クリックしてカウンター**カウンターの追加**です。 **カウンターの追加**ダイアログ ボックスで、 **ServiceModelOperation 3.0.0.0、ServiceModelEndpoint 3.0.0.0、または ServiceModelService 3.0.0.0**パフォーマンス オブジェクト でドロップダウン リスト ボックス。 表示するカウンタを一覧から選択します。  
  
    > [!NOTE]
    >  コンピューター上で [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが実行されていない場合は、サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] パフォーマンス カウンターは存在しません。  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>構成エディターを使用してカウンターを有効にするには  
  
1.  SvcConfigEditor.exe のインスタンスを開きます。  
  
2.  ファイル メニューをクリックして**開く** をクリックし、 **Config ファイル.**.  
  
3.  サンプル アプリケーションの service フォルダーに移動し、Web.config ファイルを開きます。  
  
4.  をクリックして**診断**構成ツリーにします。  
  
5.  トグル**パフォーマンス カウンター**で、**診断**'All' を表示するウィンドウです。  
  
6.  構成ファイルを保存し、エディターを終了します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>関連項目  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)
