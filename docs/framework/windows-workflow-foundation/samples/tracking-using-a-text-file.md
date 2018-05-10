---
title: テキスト ファイルを使用した追跡
ms.date: 03/30/2017
ms.assetid: 56a82682-73c2-4b91-a206-4d8bb12c561b
ms.openlocfilehash: aa59ab8304c68873c938f42fc585be883b234ecc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="tracking-using-a-text-file"></a>テキスト ファイルを使用した追跡
このサンプルでは、カスタム追跡参加要素を作成することで、Windows Workflow Foundation (WF) の追跡を拡張する方法を示します。 追跡参加要素は、出力された追跡レコードをランタイムから受け取る .NET Framework クラスです。 追跡参加要素を作成して、シナリオに必要な出力先に追跡イベントを転送することができます。 たとえば、ETW (Event Tracing for Windows) 追跡参加要素は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の一部として提供されています。 このサンプルの追跡参加要素は、レコードを XML 形式でテキスト ファイルに書き込みます。  
  
## <a name="sample-details"></a>サンプルの詳細  
 追跡参加要素の有用性と信頼性を最適化するには、いくつかの追加手順を完了して追跡参加要素をランタイムに適切に接続する必要があります。 ベスト プラクティスに準拠する追跡参加要素を作成するためにこのサンプルで使用するクラスを次の表に示します。  
  
|クラス|説明|  
|-----------|-----------------|  
|`TextFileTrackingExtensionElement`|<xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を使用して、テキスト ファイルの追跡参加要素の構成に使用される構成セクションを定義します。 これにより、ユーザーは、標準の .NET Framework 構成ファイルを使用してログ ファイルの出力先を指定できます。|  
|`TextFileTrackingBehavior`|WCF での動作を拡張機能をランタイムに挿入できるようにします。 この動作によって、サービスの開始時に追跡参加要素がサービスに追加されます。|  
|`TextFileTrackingParticipant`|実行時に追跡参加要素を受け取って XML としてログ ファイルに格納する追跡参加要素。|  
  
## <a name="behavior-extension-elements-configuration"></a>動作拡張要素の構成  
 .NET Framework 構成ファイルを使用して前に記述した動作拡張要素を利用するには、もう 1 つの手順が必要です。 拡張機能を使用する構成ファイルに次の構成を挿入する必要があります。  
  
```xml  
<system.serviceModel>  
    <extensions>  
      <behaviorExtensions>  
        <add name="textFileTracking" type="Microsoft.Samples.TextFileTracking.TextFileTrackingExtensionElement, WFStockPriceApplication, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </behaviorExtensions>  
    </extensions>  
…  
  </system.serviceModel>  
```  
  
> [!NOTE]
>  動作拡張要素の構成の詳細な使用例については、サンプルの Web.config ファイルを参照してください。  
  
## <a name="custom-tracking-records"></a>カスタム追跡レコード  
 GetStockPrices.cs ファイルでは、<xref:System.Activities.CodeActivity> 内からカスタム追跡レコードを作成する方法を示します。 サンプルの実行時にこのレコードを調べてください。  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、WFStockPriceApplication.sln ソリューション ファイルを開きます。  
  
2.  ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。  
  
3.  ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。  
  
     ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。  
  
4.  ブラウザーで、StockPriceService.xamlx をクリックします。  
  
5.  ブラウザーで、表示、 **StockPriceService**ページで、ローカル サービスの wsdl アドレスが含まれています。 このアドレスをコピーします。  
  
     ローカル サービスの wsdl アドレスの例はhttp://localhost:53797/StockPriceService.xamlx?wsdlします。  
  
6.  [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] を使用して、[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] フォルダー (既定のインストール フォルダーは %SystemDrive%\Program Files\Microsoft Visual Studio 10.0) に移動します。 Common7\IDE\ サブフォルダーを見つけます。  
  
7.  WcfTestClient.exe ファイルをダブルクリックして、WCF テスト クライアントを起動します。  
  
8.  WCF テスト クライアントで、次のように選択します**サービスを追加しています...** **ファイル**メニュー。  
  
9. コピーした URL をテキスト ボックスに貼り付けます。  
  
10. をクリックして**OK**ダイアログ ボックスを閉じます。  
  
11. WCF テスト クライアントを使用してサービスをテストします。  
  
    1.  WCF テスト クライアントでダブルクリック**GetStockPrice()** 下にある、 **IStockPriceService**ノード。  
  
         **GetStockPrice()** メソッドは、1 つのパラメーターと共に右ペインに表示されます。  
  
    2.  パラメーターの値として「Contoso」と入力します。  
  
    3.  をクリックして**呼び出す**です。  
  
12. アプリケーション データ ディレクトリにあるログ ファイル (%APPDATA%\trackingRecords.log) で追跡イベントを確認します。  
  
    > [!NOTE]
    >  %Appdata% %SystemDrive%\Users に解決される環境変数である\\< ユーザー名\>\AppData\Roaming [!INCLUDE[wv](../../../../includes/wv-md.md)]、 [!INCLUDE[lserver](../../../../includes/lserver-md.md)]、または Windows Server 2008。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\TextFileTracking`  
  
## <a name="see-also"></a>関連項目  
 [AppFabric の監視のサンプル](http://go.microsoft.com/fwlink/?LinkId=193959)
