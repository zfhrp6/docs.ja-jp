---
title: "Windows Communication Foundation サンプルのビルド | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
caps.latest.revision: 33
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 33
---
# Windows Communication Foundation サンプルのビルド
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルは、Visual Studio 2010 を使用したり、コマンド ラインで **msbuild** コマンドを使用したりしてビルドできます。ここでは、両方の手順について説明します。  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サンプルをビルドまたは実行する前に、「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」に記述されている手順が完了していることを確認してください。  
  
### コマンド プロンプトを使用してサンプルをビルドするには  
  
1.  管理特権を使用して [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。  
  
2.  コマンド プロンプトで `msbuild` と入力します。クライアント プログラムが client\\bin にビルドされ、サービス プログラムが service\\bin にビルドされます。サービスがインターネット インフォメーション サービス \(IIS\) によってホストされている場合は、サービス プログラム ファイルがさらに servicemodelsamples ディレクトリと、その \\bin サブディレクトリにコピーされます。  
  
> [!NOTE]
>  %systemdrive%\\inetpub\\wwwroot 上の ACL を、実行中のアカウントに変更権限を付与するように設定する必要があります。このように設定しない場合、ビルド後のイベントが失敗する場合があります。代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトを管理者として実行することもできます。  
  
### Visual Studio を使用してサンプルをビルドするには  
  
1.  [!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[lserver](../../../../includes/lserver-md.md)]、Windows 7、または Windows Server 2008 R2 を使用し、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を実行する場合は、より高いレベルのアクセス許可を使用して [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] を実行する必要があります。これを行うには、\[スタート\] メニューのアイコンを右クリックし、**\[管理者として実行\]** をクリックします。  
  
2.  [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] で、**\[ファイル\]** メニューの **\[開く\]** をクリックし、**\[プロジェクト\/ソリューション\]** をクリックします。サンプルをインストールしたディレクトリの下の言語固有のサブディレクトリに移動し、.sln ファイルのアイコンをダブルクリックして、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でソリューションを開きます。  
  
3.  **\[ビルド\]** メニューの **\[ソリューションのリビルド\]** をクリックします。クライアント プログラムが client\\bin にビルドされ、サービス プログラムが service\\bin にビルドされます。サービスが IIS によってホストされている場合は、サービス プログラム ファイルがさらに servicemodelsamples ディレクトリと、その \\bin サブディレクトリにコピーされます。  
  
> [!NOTE]
>  %systemdrive%\\inetpub\\wwwroot 上の ACL を、実行中のアカウントに変更権限を付与するように設定する必要があります。このように設定しない場合、ビルド後のイベントが失敗する場合があります。代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトまたは Visual Studio を管理者として実行することもできます。Visual Studio の一部のアクション \(デバッガを ASP.Net ワーカー プロセスにアタッチするアクションなど\) では、さらに管理特権が必要です。  
  
## セットアップ バッチ ファイルとスクリプト  
 Setup.exe バッチ ファイル、Cleanup.exe バッチ ファイル、およびスクリプトは、Visual Studio コマンド プロンプトから実行する必要があります。いくつかのセットアップ ファイルとクリーンアップ ファイルは、管理特権が必要なタスクを実行します。したがって、これらのファイルは管理特権で起動する必要があります。  
  
## メタデータ エンドポイントに関する重要なセキュリティ情報  
 サービスのメタデータには機密情報が含まれる可能性がありますが、意図的ではない開示を回避するために、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスの既定の構成では、メタデータは公開されないように設定されています。この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ公開の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール \(Svcutil.exe など\) を使用して生成できないことも意味します。サンプルでの試みを容易にするため、ほとんどすべてのサンプルでは、セキュリティ保護されていないメタデータ公開エンドポイントを公開しています。このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。サービス メタデータの公開[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[メタデータ公開動作](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)」のサンプルを参照してください。メタデータ エンドポイントをセキュリティ保護するサンプルについては、「[カスタム セキュア メタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)」のサンプルを参照してください。  
  
## 例外処理  
 通常、コードではサンプルの主題を重視するので、これらのサンプルに例外処理は含まれていません。例外処理[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[予期される例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)」のサンプルを参照してください。  
  
## Svcutil を使用したクライアントと構成の再生成  
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用すると、ほとんどのサンプルのクライアント コードと構成を生成できます。一部のサンプルでは、構成を手動で編集する必要があります。たとえば、Svcutil.exe を使用して、クライアント証明書の資格情報を使用するサンプルの構成を再生成する場合は、以前に構成された資格情報を手動で指定する必要があります。一部のサンプルでは、生成コードに影響を与える、Svcutil.exe の特定のオプションを使用します。これらのオプションは、そうした特定のサンプルのトピックで指定されます。  
  
#### クライアントと構成ファイルを再生成するには  
  
1.  SDK コマンド プロンプトを開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。  
  
2.  サービスが Web ホスト型の場合は、次のコマンドを使用します。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     サービスが自己ホスト型の場合は、次のコマンドを使用します。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     http:\/\/localhost:8000\/ServiceModelSamples\/service.svc\/mex を、自己ホスト型サービスの MEX エンドポイントのアドレスに置き換えます。  
  
     Visual Basic の型でクライアントを生成するには、次のコマンドを使用します。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
  
    ```  
  
     サービスが自己ホスト型の場合は、次のコマンドを使用します。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  クライアント構成の生成をスキップするには、**\/noConfig** オプションを追加します。  
  
## 参照  
 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)   
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)