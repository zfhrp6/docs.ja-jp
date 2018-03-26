---
title: SystemWebRouting 統合サンプル
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de8869956a59cb47623dbc4d84763e19d6f181bf
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="systemwebrouting-integration-sample"></a>SystemWebRouting 統合サンプル
このサンプルでは、<xref:System.Web.Routing> 名前空間のクラスとのホスト層の統合を示します。 <xref:System.Web.Routing> 名前空間のクラスを使用すると、物理リソースに直接対応しない URL をアプリケーションで使用できます。 開発者は Web ルーティングを使用することで、後で実際の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスにマップされる HTTP の仮想アドレスを作成できます。 これは、物理ファイルやリソースを配置せずに WCF サービスをホストする必要がある場合、または .html や .aspx などのファイルがない URL を使用してサービスにアクセスする必要がある場合に役立ちます。 このサンプルでは、<xref:System.Web.Routing.RouteTable> クラスを使用して、global.asax で定義された実行中のサービスにマップされる仮想 URI を作成する方法を示します。 

> [!NOTE]
>  <xref:System.Web.Routing> 名前空間のクラスは、HTTP でホストされるサービスに対してのみ機能します。  
  
この例では、WCF を使用して、2 つの RSS フィードを作成します。、`movies`フィードと`channels`フィード。 拡張機能が含まれていないおよびに登録されているサービスをアクティブ化する Url、`Application_Start`のメソッド、`Global`から派生したクラス、<xref:System.Web.HttpApplication>クラスです。  
  
> [!NOTE]
>  このサンプルでは、インターネット インフォメーション サービス (IIS) 7.0 のみは機能し、その後、IIS 6.0 とメソッドを使用して、さまざまな拡張機能のない Url をサポートするためです。  

#### <a name="to-download-this-sample"></a>このサンプルをダウンロードするには
  
このサンプルは、既にコンピューターにインストールできます。 続行する前に、次の (既定の) ディレクトリを確認してください。  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>このサンプルを使用するには  
  
1.  Visual Studio を使用して、WebRoutingIntegration.sln ファイルを開きます。  
  
2.  ソリューションを実行して Web 開発サーバーを起動するには、F5 キーを押します。  
  
     サンプルのディレクトリの一覧が表示されます。 ファイル拡張子が .svc のファイルがないことに注意してください。  
  
3.  アドレス バーに追加`movies`url、そのためことを読み取ります http://localhost:[port]/映画 ENTER キーを押します。  
  
     movies フィードがブラウザーに表示されます。  
  
4.  アドレス バーで、URL が http://localhost:[port]/channels の形式になるように `channels` を追加し、Enter キーを押します。  
  
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
  
    4.  Press **OK**.  
  
4.  Web アプリケーションを右クリックしてアプリケーションを起動**アプリケーションの管理**し**参照**です。  
  
5.  アドレス バーで、URL が http://localhost:[port]/movies の形式になるように `movies` を追加し、Enter キーを押します。  
  
     movies フィードがブラウザーに表示されます。  
  
6.  アドレス バーで、URL が http://localhost:[port]/channels の形式になるように `channels` を追加し、Enter キーを押します。  
  
     channels フィードがブラウザーに表示されます。  
  
7.  Alt キーを押しながら F4 キーを押して Web ブラウザーを閉じます。  
  
 このサンプルは、HTTP でホストされたサービスの要求をルーティングするために、<xref:System.Web.Routing> 名前空間のクラスを使用してホスト層を構成できることを示しています。  
  
> [!NOTE]
>  アプリケーション プールの既定のバージョンを更新する必要があります[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]バージョン 2 に設定されている場合。  
  
## <a name="see-also"></a>参照  
 [AppFabric ホスティングと永続性のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)
