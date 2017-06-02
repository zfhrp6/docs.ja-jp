---
title: "Windows Communication Foundation サンプルの 1 回限りのセットアップの手順 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5848ffd-3eb5-432d-812e-bd948ccb6bca
caps.latest.revision: 83
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 83
---
# Windows Communication Foundation サンプルの 1 回限りのセットアップの手順
ほとんどの [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルは、インターネット インフォメーション サービス \(IIS\) でホストされ、共通の仮想ディレクトリから実行されます。この 1 回限りのセットアップの手順では、ディスク上にフォルダーを作成します。また、**ServiceModelSamples** という名前の仮想ディレクトリを IIS に追加します。  
  
 **ServiceModelSamples** 仮想ディレクトリは、IIS でホストされるサービスを使用するすべてのサンプルのビルドと実行に使用されます。サンプルの実行に必要な仮想ディレクトリはこれだけです。サンプルをビルドすると、この仮想ディレクトリにある、以前に配置されたサービスがすべて置き換えられます。この仮想ディレクトリには最近ビルドされたサンプルだけが配置されるため、そのサンプルしか使用できません。  
  
> [!NOTE]
>  すべてのコマンドは、ローカル管理者アカウントで実行する必要があります。Windows 7、[!INCLUDE[windowsver](../../../../includes/windowsver-md.md)]、または Windows Server 2008 R2 を使用している場合は、コマンド プロンプトも管理者権限で実行する必要があります。これには、コマンド プロンプトのアイコンを右クリックし、**\[管理者として実行\]** をクリックします。このトピックで使用するすべてのコマンドは、適切なパスが設定されているコマンド プロンプトで実行する必要があります。このようにするための最も簡単な方法は、Visual Studio コマンド プロンプトを使用する方法です。Visual Studio コマンド プロンプトを開くには、**\[スタート\]** ボタンをクリックして **\[すべてのプログラム\]** をポイントし、下方向へスクロールして **\[Visual Studio 2010\]**、**\[Visual Studio Tools\]** の順にクリックします。次に、**\[Visual Studio コマンド プロンプト \(2010\)\]** を右クリックして、**\[管理者として実行\]** をクリックします。Visual Studio Express Editions のいずれかがインストールされている場合は、このコマンド プロンプトを使用できません。この場合、システム パスに "C:\\Windows\\Microsoft.Net\\Framework\\v4.0" を追加する必要があります。  
  
### WCF サンプルの 1 回限りのセットアップの手順  
  
1.  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] がセットアップされていることを確認します。[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] のセットアップ方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[インターネット インフォメーション サービスのホスティング手順](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)」を参照してください。  
  
2.  [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] がインストールされていることを確認します。**\\Windows\\Microsoft.NET\\Framework** ディレクトリに、v4.0 以降があることを確認します。  
  
3.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] がインストールされておらず、オペレーティング システムが Windows Server 2008 SP2 以降でない場合は、[修正プログラム 251798](http://go.microsoft.com/fwlink/?LinkId=184693) をインストールします。  
  
4.  次のコマンドを実行します。これらのコマンドを実行しなければならない理由については、「[IIS Hosted Service Fails](http://msdn.microsoft.com/ja-jp/ee5499fc-1b10-4cda-a9b1-13dba70f05f8)」を参照してください。  
  
    > [!WARNING]
    >  IIS を再インストールした場合は、次のコマンドを再実行します。  
  
    ```  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\aspnet_regiis" –i –enable  
    "%WINDIR%\Microsoft.Net\Framework\v4.0.30319\ServiceModelReg.exe" -r  
    ```  
  
    > [!WARNING]
    >  コマンド `aspnet_regiis –i –enable` を実行すると、[!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] を使用して、既定のアプリケーション プールが実行されます。このとき、同じコンピューター上の他のアプリケーションで非互換性の問題が発生することがあります。  
  
5.  「[ファイアウォール手順](../../../../docs/framework/wcf/samples/firewall-instructions.md)」に従って、サンプルで使用するポートを有効にします。  
  
6.  既定のディレクトリ \(**\<InstallDrive\>InstallDrive:\\WF\_WCF\_Samples**\) を確認してください。サンプルが既にインストールされている場合は、これが既定のディレクトリです。  
  
7.  サンプルがインストールされていない場合は、[Visual C\#](http://go.microsoft.com/fwlink/?LinkId=190939) または [Visual Basic](http://go.microsoft.com/fwlink/?LinkID=193373) のサンプルのダウンロード場所からインストールします。  
  
8.  サンプルをインストールした後、\<InstallDrive\>:**\\WF\_WCF\_Samples\\WCF\\Setup\\** に移動します。  
  
9. **Setupvroot.bat** バッチ ファイルを実行します。次の手順が実行されます。  
  
    -   ServiceModelSamples という名前の仮想ディレクトリが IIS に作成されます。  
  
    -   %SystemDrive%\\Inetpub\\wwwroot\\ServiceModelSamples and %SystemDrive%\\Inetpub\\wwwroot\\ServiceModelSamples\\bin という名前の新しいディスク ディレクトリが作成されます。  
  
     これらのディレクトリを手動でセットアップする場合は、「[仮想ディレクトリのセットアップ手順](../../../../docs/framework/wcf/samples/virtual-directory-setup-instructions.md)」を参照してください。この手順で行ったすべての変更を元に戻すには、サンプルの使用が終わった後で cleanupvroot.bat を実行します。  
  
    > [!NOTE]
    >  cleanupvroot.bat を実行しない限り、この手順を実行するのは、1 台のコンピューターで 1 回だけです。  
  
10. サンプルおよび Network Service ユーザーのビルドに使用するアカウントに対し、%SystemDrive%\\inetpub\\wwwroot の変更権限を付与する必要があります。ビルドの実行時に、Web ホストの一部のサンプルがコンパイル済みバイナリを前述の場所にコピーしようとする場合があり、適切な権限が設定されていないと、ビルドは破損します。代わりに、アクセス許可の設定はそのままにして、SDK コマンド プロンプトまたは Visual Studio コマンド プロンプト \(2012\) を管理者として実行するか、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を管理者として実行し、サンプルをビルドすることもできます。  
  
    > [!NOTE]
    >  この手順を完了していない場合は、ビルドの実行時に IIS でホストされているすべてのサンプルでエラーが発生します。アクセス許可が正しく設定されていることを確認するか、SDK コマンド プロンプトと Visual Studio コマンド プロンプト \(2012\) を管理者として実行してください。  
  
11. コンピューター上に C:\\logs ディレクトリを作成します \(一部のサンプルで必要になることがあります\)。このフォルダーに対する書き込みアクセスが適切なアカウントに付与されていることを確認してください。このアカウントは、Windows 7、[!INCLUDE[wv](../../../../includes/wv-md.md)]、Windows Server 2008 R2 では **Network Service**、[!INCLUDE[lserver](../../../../includes/lserver-md.md)] では NT Authority\\Network Service、[!INCLUDE[wxp](../../../../includes/wxp-md.md)] および [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では ASPNET です。  
  
12. Setupcerttool.bat ファイルを実行します。このファイルは、\<InstallPath\>\\WF\_WCF\_Samples\\WCF\\Setup\\ フォルダーにあります。このスクリプトでは、次のタスクが実行されます。  
  
    -   FindPrivateKey ツールをビルドします。  
  
    -   %ProgramFiles%\\ServiceModelSampleTools という名前のディレクトリを作成します。  
  
    -   新しい FindPrivateKey ツールをこのディレクトリにコピーします。  
  
     このツールは、証明書を使用して IIS でホストされるサンプルで必要です。  
  
    > [!NOTE]
    >  セキュリティの目的で、サンプルの使用が終わったら、このセットアップ手順で付与された仮想ディレクトリの定義とアクセス許可を必ず削除してください。削除するには、Cleanupvroot.bat という名前のバッチ ファイルを実行します。  
  
13. 自己ホスト型の \(IIS でホストされていない\) サンプルでは、リッスンを行うコンピューター上で HTTP アドレスを登録するためのアクセス許可が必要です。HTTP 名前空間予約のアクセス許可は、サンプルの実行に使用されるユーザー アカウントから提供されます。既定では、管理者アカウントには、任意の HTTP アドレスを登録するためのアクセス許可があります。管理者以外のアカウントの場合は、サンプルで使用される HTTP 名前空間へのアクセス許可が付与される必要があります。名前空間予約の構成方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[HTTP および HTTPS の構成](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)」を参照してください。  
  
14. 一部のサンプルにはメッセージ キューが必要です。インストールの処理手順については、「[メッセージ キュー \(MSMQ\) のインストール](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)」を参照してください。  
  
    > [!NOTE]
    >  メッセージ キューが必要なサンプルを実行する場合は、MSMQ サービスを事前に開始しておいてください。  
  
15. 一部のサンプルには証明書が必要です。「[インターネット インフォメーション サービス \(IIS\) サーバー証明書インストール手順](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)」を参照してください。  
  
## 参照