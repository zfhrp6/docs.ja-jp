---
title: "方法 : WCF アクティブ化コンポーネントをインストールして設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "HTTP アクティベーション [WCF]"
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# 方法 : WCF アクティブ化コンポーネントをインストールして設定する
ここでは、HTTP ネットワーク プロトコルでは通信しない [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをホストするように Windows プロセス アクティブ化サービス \(WAS: Windows Process Activation Service\) を [!INCLUDE[wv](../../../../includes/wv-md.md)] に構成するために必要な手順について説明します。以降の各セクションで、この構成に関する手順について概説します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アクティブ化コンポーネントをインストール \(またはそのインストールを確認\) します。  
  
-   非 HTTP プロトコルをサポートようにする WAS を構成します。次の手順では、TCP アクティベーション用に [!INCLUDE[wv](../../../../includes/wv-md.md)] を構成します。  
  
 WAS をインストールして構成したら、「[方法 : WAS で WCF サービスをホストする](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)」の手順を参照して、WAS を使用する非 HTTP エンドポイントを公開する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを作成します。  
  
### WCF 非 HTTP アクティブ化コンポーネントをインストールするには  
  
1.  **\[スタート\]** ボタンをクリックし、**\[コントロール パネル\]** をクリックします。  
  
2.  **\[プログラム\]** をクリックし、**\[プログラムと機能\]** をクリックします。  
  
3.  **\[タスク\]** メニューの **\[Windows の機能を有効化または無効化\]** をクリックします。  
  
4.  [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] ノードを検索し、それを選択して展開します。  
  
5.  **\[WCF Non\-Http Activation Components\]** ボックスをオンにして、設定を保存します。  
  
### TCP アクティベーションをサポートするように WAS を構成するには  
  
1.  net.tcp アクティベーションをサポートするには、既定の Web サイトをあらかじめ net.tcp ポートにバインドしておく必要があります。これは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] 管理ツール セットと共にインストールされる Appcmd.exe を使用して行います。管理者レベルのコマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  このコマンドはテキスト 1 行です。このコマンドは、net.tcp サイト バインディングを、TCP ポート 808 で任意のホスト名をリッスンする既定の Web サイトに追加します。  
  
2.  サイト内のすべてのアプリケーションが同じ net.tcp バインディングを共有しますが、net.tcp サポートの有効化はアプリケーションごとに指定できます。アプリケーションで net.tcp を有効にするには、管理者レベルのコマンド プロンプトから、次のコマンドを実行します。  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  このコマンドはテキスト 1 行です。このコマンドにより、\/\<*WCF Application*\> アプリケーションには、http:\/\/localhost*\/\<WCF Application\>* および net.tcp:\/\/localhost\/*\<WCF Application\>* のどちらからでもアクセスできるようになります。  
  
     このサンプル用に追加した net.tcp サイト バインディングを削除します。  
  
     便宜上次の 2 つの手順が、サンプル ディレクトリにある RemoveNetTcpSiteBinding.cmd というバッチ ファイルに実装されています。  
  
    1.  管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行して、有効なプロトコルの一覧から net.tcp を削除します。  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  このコマンドはテキスト 1 行です。  
  
    2.  権限のレベルが高いコマンド プロンプト ウィンドウで次のコマンドを実行して、net.tcp サイト バインディングを削除します。  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  このコマンドはテキスト 1 行です。  
  
### 有効なプロトコルの一覧から net.tcp を削除するには  
  
1.  有効なプロトコルの一覧から net.tcp を削除するには、管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  このコマンドはテキスト 1 行です。  
  
### net.tcp サイト バインディングを削除するには  
  
1.  net.tcp サイト バインディングを削除するには、管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  このコマンドはテキスト 1 行です。  
  
## 参照  
 [TCP アクティベーション](../../../../docs/framework/wcf/samples/tcp-activation.md)   
 [MSMQ アクティベーション](../../../../docs/framework/wcf/samples/msmq-activation.md)   
 [NamedPipe アクティベーション](../../../../docs/framework/wcf/samples/namedpipe-activation.md)   
 [AppFabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)