---
title: "方法 : WCF アクティブ化コンポーネントをインストールして設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78c63fe58872097058292a8b100b376959a2a0b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>方法 : WCF アクティブ化コンポーネントをインストールして設定する
ここでは、HTTP ネットワーク プロトコルでは通信しない [!INCLUDE[wv](../../../../includes/wv-md.md)] サービスをホストするように Windows プロセス アクティブ化サービス (WAS: Windows Process Activation Service) を [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に構成するために必要な手順について説明します。 以降の各セクションで、この構成に関する手順について概説します。  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アクティブ化コンポーネントをインストール (またはそのインストールを確認) します。  
  
-   非 HTTP プロトコルをサポートようにする WAS を構成します。 次の手順では、TCP アクティベーション用に [!INCLUDE[wv](../../../../includes/wv-md.md)] を構成します。  
  
 インストールと構成が、確認後、[する方法: WAS で WCF サービスをホスト](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)を作成する手順については、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WAS を使用する非 HTTP エンドポイントを公開するサービスです。  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a>WCF 非 HTTP アクティブ化コンポーネントをインストールするには  
  
1.  クリックして、**開始**ボタンをクリックし、をクリックして**コントロール パネルの** です。  
  
2.  をクリックして**プログラム**、クリックして**プログラムと機能**します。  
  
3.  **タスク** メニューのをクリックして**Windows の機能のオンまたはオフ**です。  
  
4.  [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] ノードを検索し、それを選択して展開します。  
  
5.  選択、 **WCF 非 Http アクティブ化コンポーネント**ボックスし、設定を保存します。  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a>TCP アクティベーションをサポートするように WAS を構成するには  
  
1.  net.tcp アクティベーションをサポートするには、既定の Web サイトをあらかじめ net.tcp ポートにバインドしておく必要があります。 これは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] 管理ツール セットと共にインストールされる Appcmd.exe を使用して行います。 管理者レベルのコマンド プロンプト ウィンドウで、次のコマンドを実行します。  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  このコマンドはテキスト 1 行です。 このコマンドは、net.tcp サイト バインディングを、TCP ポート 808 で任意のホスト名をリッスンする既定の Web サイトに追加します。  
  
2.  サイト内のすべてのアプリケーションが同じ net.tcp バインディングを共有しますが、net.tcp サポートの有効化はアプリケーションごとに指定できます。 アプリケーションで net.tcp を有効にするには、管理者レベルのコマンド プロンプトから、次のコマンドを実行します。  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  このコマンドはテキスト 1 行です。 このコマンドにより、/\<*WCF アプリケーション*> 両方 http://localhost を使用してアクセスされるアプリケーションの*/\<WCF アプリケーション >*と net.tcp://localhost/*\<WCF アプリケーション >*です。  
  
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
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>有効なプロトコルの一覧から net.tcp を削除するには  
  
1.  有効なプロトコルの一覧から net.tcp を削除するには、管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  このコマンドはテキスト 1 行です。  
  
### <a name="to-remove-the-nettcp-site-binding"></a>net.tcp サイト バインディングを削除するには  
  
1.  net.tcp サイト バインディングを削除するには、管理者レベルのコマンド プロンプト ウィンドウで次のコマンドを実行します。  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  このコマンドはテキスト 1 行です。  
  
## <a name="see-also"></a>参照  
 [TCP アクティベーション](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [MSMQ アクティベーション](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [NamedPipe アクティベーション](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [Windows Server App Fabric のホスティング機能](http://go.microsoft.com/fwlink/?LinkId=201276)
