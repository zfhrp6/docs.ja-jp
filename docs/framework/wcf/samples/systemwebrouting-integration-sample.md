---
title: SystemWebRouting 統合サンプル
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 52b908d354771cb2b351e339881647462340b716
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806527"
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting 統合サンプル
このサンプルでは、<xref:System.Web.Routing> 名前空間のクラスとのホスト層の統合を示します。 <xref:System.Web.Routing> 名前空間のクラスを使用すると、物理リソースに直接対応しない URL をアプリケーションで使用できます。 Web のルーティングを使用するには、実際の WCF サービスにバックアップし、マップされている http 仮想アドレスを作成する開発者ができるようにします。 これは、物理ファイルやリソースを配置せずに WCF サービスをホストする必要がある場合、または .html や .aspx などのファイルがない URL を使用してサービスにアクセスする必要がある場合に役立ちます。 このサンプルでは、<xref:System.Web.Routing.RouteTable> クラスを使用して、global.asax で定義された実行中のサービスにマップされる仮想 URI を作成する方法を示します。 

> [!NOTE]
>  <xref:System.Web.Routing> 名前空間のクラスは、HTTP でホストされるサービスに対してのみ機能します。  
  
この例では、WCF を使用して、2 つの RSS フィードを作成します。、`movies`フィードと`channels`フィード。 拡張機能が含まれていないおよびに登録されているサービスをアクティブ化する Url、`Application_Start`のメソッド、`Global`から派生したクラス、<xref:System.Web.HttpApplication>クラスです。  
  
> [!NOTE]
>  このサンプルでは、インターネット インフォメーション サービス (IIS) 7.0 のみは機能し、その後、IIS 6.0 とメソッドを使用して、さまざまな拡張機能のない Url をサポートするためです。  

#### <a name="to-download-this-sample"></a>このサンプルをダウンロードするには
  
このサンプルは、既にコンピューターにインストールできます。 続行する前に、次の (既定の) ディレクトリを確認してください。  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  Visual Studio を使用して、WebRoutingIntegration.sln ファイルを開きます。  
  
2.  ソリューションを実行して Web 開発サーバーを起動するには、F5 キーを押します。  
  
     サンプルのディレクトリの一覧が表示されます。 ファイル拡張子が .svc のファイルがないことに注意してください。  
  
3.  アドレス バーに追加`movies`url、そのためことを読み取りますhttp://localhost:[ポート]/映画 ENTER キーを押します。  
  
     movies フィードがブラウザーに表示されます。  
  
4.  アドレス バーに追加`channels`URL にこれは読み取りhttp://localhost:[ポート]/チャネルし、ENTER キーを押します。  
  
     channels フィードがブラウザーに表示されます。  
  
5.  Alt キーを押しながら F4 キーを押して Web ブラウザーを閉じます。  
  
     開発サーバーがまだ終了していない場合、通知エリア アイコンを右クリックし **停止**です。  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>このサンプルを使用するには (IIS でホストする場合)  
  
1.  Visual Studio を使用して、WebRoutingIntegration.sln ファイルを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。  
  
3.  インターネット インフォメーション サービス (IIS) マネージャーで Web アプリケーションを作成します。  
  
    1.  IIS マネージャーで、右クリックして、**既定の Web サイト**選択**アプリケーションを追加**です。  
  
    2.  **エイリアス**、入力`WebRoutingIntegration`です。  
  
    3.  **物理パス**プロジェクト内の Service フォルダーを選択します。  
  
    4.  **[OK]** を押します。  
  
4.  Web アプリケーションを右クリックしてアプリケーションを起動**アプリケーションの管理**し**参照**です。  
  
5.  アドレス バーに追加`movies`URL にこれは読み取りhttp://localhost:[ポート]/映画 ENTER キーを押します。  
  
     movies フィードがブラウザーに表示されます。  
  
6.  アドレス バーに追加`channels`URL にこれは読み取りhttp://localhost:[ポート]/チャネルし、ENTER キーを押します。  
  
     channels フィードがブラウザーに表示されます。  
  
7.  Alt キーを押しながら F4 キーを押して Web ブラウザーを閉じます。  
  
 このサンプルは、HTTP でホストされたサービスの要求をルーティングするために、<xref:System.Web.Routing> 名前空間のクラスを使用してホスト層を構成できることを示しています。  
  
> [!NOTE]
>  アプリケーション プールの既定のバージョンを更新する必要があります[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]バージョン 2 に設定されている場合。  
  
## <a name="see-also"></a>関連項目  
 [AppFabric ホスティングと永続性のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)
