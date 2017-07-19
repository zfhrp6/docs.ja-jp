---
title: "SystemWebRouting 統合サンプル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# SystemWebRouting 統合サンプル
このサンプルでは、<xref:System.Web.Routing> 名前空間のクラスとのホスト層の統合を示します。  <xref:System.Web.Routing> 名前空間のクラスを使用すると、物理リソースに直接対応しない URL をアプリケーションで使用できます。  開発者は Web ルーティングを使用することで、後で実際の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスにマップされる HTTP の仮想アドレスを作成できます。  これは、物理ファイルやリソースを配置せずに WCF サービスをホストする必要がある場合、または .html や .aspx などのファイルがない URL を使用してサービスにアクセスする必要がある場合に役立ちます。  このサンプルでは、<xref:System.Web.Routing.RouteTable> クラスを使用して、global.asax で定義された実行中のサービスにマップされる仮想 URI を作成する方法を示します。  この例では、`movies` フィードと `channels` フィードという、WCF を使用して作成された 2 つの RSS フィードを使用します。  サービスをアクティブ化する URL に拡張子がなく、<xref:System.Web.HttpApplication.Application_Start%2A> メソッドで登録されています。  
  
> [!NOTE]
>  <xref:System.Web.Routing> 名前空間のクラスは、HTTP でホストされるサービスに対してのみ機能します。  
  
> [!NOTE]
>  このサンプルは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] でのみ機能します。[!INCLUDE[iis60](../../../../includes/iis60-md.md)] では、拡張子がない URL を別の方法でサポートしています。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### このサンプルを使用するには  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、WebRoutingIntegration.sln ファイルを開きます。  
  
2.  ソリューションを実行して Web 開発サーバーを起動するには、F5 キーを押します。  
  
     サンプルのディレクトリの一覧が表示されます。  ファイル拡張子が .svc のファイルがないことに注意してください。  
  
3.  アドレス バーで、URL が http:\/\/localhost:\[port\]\/movies の形式になるように `movies` を追加し、Enter キーを押します。  
  
     movies フィードがブラウザーに表示されます。  
  
4.  アドレス バーで、URL が http:\/\/localhost:\[port\]\/channels の形式になるように `channels` を追加し、Enter キーを押します。  
  
     channels フィードがブラウザーに表示されます。  
  
5.  Alt キーを押しながら F4 キーを押して Web ブラウザーを閉じます。  
  
     開発サーバーが終了しない場合は、通知領域アイコンを右クリックし、**\[停止\]** をクリックします。  
  
#### このサンプルを使用するには \(IIS でホストする場合\)  
  
1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、WebRoutingIntegration.sln ファイルを開きます。  
  
2.  Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。  
  
3.  インターネット インフォメーション サービス \(IIS\) マネージャーで Web アプリケーションを作成します。  
  
    1.  IIS マネージャーで、**\[既定の Web サイト\]** を右クリックし、**\[アプリケーションの追加\]** をクリックします。  
  
    2.  **\[エイリアス\]** に「`WebRoutingIntegration`」と入力します。  
  
    3.  **\[物理パス\]** で、プロジェクト内の Service フォルダーを選択します。  
  
    4.  **\[OK\]** をクリックします。  
  
4.  Web アプリケーションを右クリックし、**\[アプリケーションの管理\]**、**\[参照\]** の順にクリックして、アプリケーションを開始します。  
  
5.  アドレス バーで、URL が http:\/\/localhost:\[port\]\/movies の形式になるように `movies` を追加し、Enter キーを押します。  
  
     movies フィードがブラウザーに表示されます。  
  
6.  アドレス バーで、URL が http:\/\/localhost:\[port\]\/channels の形式になるように `channels` を追加し、Enter キーを押します。  
  
     channels フィードがブラウザーに表示されます。  
  
7.  Alt キーを押しながら F4 キーを押して Web ブラウザーを閉じます。  
  
 このサンプルは、HTTP でホストされたサービスの要求をルーティングするために、<xref:System.Web.Routing> 名前空間のクラスを使用してホスト層を構成できることを示しています。  
  
> [!NOTE]
>  既定のアプリケーション プールのバージョンが 2 に設定されている場合は、[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] に更新してください。  
  
## 参照  
 [AppFabric のホストおよび永続化のサンプル](http://go.microsoft.com/fwlink/?LinkId=193961)