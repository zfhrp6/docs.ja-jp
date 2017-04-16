---
title: "Windows Communication Foundation サンプルの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# Windows Communication Foundation サンプルの実行
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルは、単一コンピューター構成または複数コンピューター構成で実行できます。  サンプルは、単一コンピューターでそのまま実行できます。  複数コンピューター構成で実行するには、サンプルの構成ファイルの設定を変更する必要があります。  単一コンピューターおよび複数コンピューターの構成でサンプルを実行する手順を、次に示します。  インターネット インフォメーション サービス \(IIS\) でホストされるサービスと自己ホスト型のサービスのサンプルとでは、手順が異なります。  ほとんどのサンプルは IIS でホストされます。サンプルのホスト方法を判断するには、サンプルの Readme 情報を参照してください。  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] では、IIS でホストされていないサンプルには、リスナーを Http.sys に登録するための管理特権が必要です。  Httpcfg.exe を使用して、サービスのリッスン アドレスをサービスが実行されているアカウントに登録するか、管理者権限で実行されているコマンド プロンプトでサービスを起動します。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サンプルをビルドまたは実行する前に、「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」に記述されている手順が完了していることを確認してください。  
  
### サンプルを同じコンピューターで実行するには  
  
1.  サービスが IIS でホストされている場合は、ブラウザーにアドレス http:\/\/localhost\/servicemodelsamples\/service.svc を入力して、サービスにアクセスできることを確認します。  これに応答して、確認ページが表示されます。  確認ページが表示されない場合は、「[Troubleshooting Tips](http://msdn.microsoft.com/ja-jp/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
2.  サービスが自己ホスト型の場合は、言語固有のフォルダーの下の \\service\\bin にある Service.exe を実行します。  サービス アクティビティがサービス コンソール ウィンドウに表示されます。  
  
3.  言語固有のフォルダーの下の \\client\\bin\\ にある Client.exe を実行します。  クライアント アクティビティがクライアント コンソール ウィンドウに表示されます。  
  
4.  クライアントとサービス間で通信できない場合は、「[Troubleshooting Tips](http://msdn.microsoft.com/ja-jp/8787c877-5e96-42da-8214-fa737a38f10b)」を参照してください。  
  
### サンプルを複数コンピューターで実行するには  
  
1.  サービスが IIS でホストされている場合 :  
  
    1.  サービス コンピューターで、ServiceModelSamples という仮想ディレクトリを作成します。  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」に含まれている Setupvroot.bat バッチ ファイルを使用して、ディスク ディレクトリと仮想ディレクトリを作成できます。  
  
    2.  サービス プログラム ファイルを %SystemDrive%\\Inetpub\\wwwroot\\servicemodelsamples からサービス コンピューターの ServiceModelSamples 仮想ディレクトリにコピーします。  このファイルが \\bin ディレクトリにあることを確認します。  
  
    3.  ブラウザーを使用して、サービスにクライアント コンピューターからアクセスできるかどうかをテストします。  
  
     サービスが自己ホスト型の場合、次の手順を実行します。  
  
    1.  サービス コンピューターで、サービス ファイルを保持するディレクトリを作成します。  
  
    2.  サービス プログラム ファイルを、言語固有のフォルダーにある \\service\\bin\\ フォルダーからサービス コンピューターにコピーします。  
  
    3.  サービスの構成ファイルで、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。  アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。  
  
    4.  コマンド プロンプトから Service.exe を起動します。  
  
2.  クライアント プログラム ファイルを、言語固有のフォルダーにある \\client\\bin\\ フォルダーからクライアント コンピューターにコピーします。  
  
3.  エンドポイント アドレスを設定します。  
  
    1.  サービスの実行に使用されているのがドメイン アカウントではない場合、クライアント構成ファイルを開き、エンドポイント定義のアドレス値をサービスの新しいアドレスに変更します。  アドレスの "localhost" への参照をすべて完全修飾ドメイン名に置き換えます。  
  
    2.  サービスの実行に使用されているのがドメイン アカウントの場合、サービスに対して Svcutil.exe を実行し、クライアントの構成を再生成します。  Svcutil.exe の実行[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」を参照してください。  サンプルの構成ファイルではなく、生成されたファイルを使用します。  生成された構成ファイルには、追加の ID 情報があります \(また、サービス エンドポイントへの接続に必要なすべての設定が、既定の設定であるにもかかわらず含まれています\)。  ID [!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)」および「[\<identity\>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)」を参照してください。  
  
4.  クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。  
  
### サービスをデバッグするには  
  
1.  \(クライアントとサービスの両方で\) **\[Build\]** メニューを使用するか、または Ctrl キーと Shift キーを押しながら B キーを押して、ソリューションをビルドします。  
  
2.  サービスが IIS でホストされている場合 :  
  
    1.  サービスをアクティブ化します。ブラウザーにアドレス http:\/\/localhost\/servicemodelsamples\/service.svc を入力します。  
  
    2.  ソリューションで、**\[Debug\]** メニューの **\[Attach to Process\]** をクリックします。  
  
    3.  **\[Show processes from all users\]** チェック ボックスをオンにします。  
  
    4.  デバッグ対象のホスト ワーカー プロセス W3wp.exe を選択します \(Windows XP では ASPNet\_wp.exe を選択します\)。  
  
3.  これで、サービス内にブレークポイントを設定し、例外に対してブレークポイントを有効にできます。  
  
4.  クライアントのプロジェクト項目を右クリックし、**\[デバッグ\]**、**\[新しいインスタンスを開始\]** の順にクリックします。  
  
### サンプルの実行後にクリーンアップするには  
  
-   サービスがセキュリティの目的で IIS でホストされている場合、サンプルの使用が終わったら、このセットアップで付与された仮想ディレクトリの定義とアクセス許可を削除してください。  
  
## 参照  
 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)   
 [Running the Samples in a Workgroup and Across Machines](http://msdn.microsoft.com/ja-jp/a451a525-e7ce-452d-9da9-620221260113)   
 [Troubleshooting Tips](http://msdn.microsoft.com/ja-jp/8787c877-5e96-42da-8214-fa737a38f10b)