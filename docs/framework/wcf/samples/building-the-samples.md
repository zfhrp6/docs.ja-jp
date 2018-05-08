---
title: Windows Communication Foundation サンプルのビルド
ms.date: 03/30/2017
ms.assetid: 2899e7a5-9cb2-4e8d-b8d2-f31391549198
ms.openlocfilehash: 5493972306092fc3309b0993d595f22c74c8603a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="building-the-windows-communication-foundation-samples"></a>Windows Communication Foundation サンプルのビルド
Visual Studio 2010 を使用してまたはを使用して、Windows Communication Foundation (WCF) サンプルをビルドすることができます、 **msbuild**コマンドラインからコマンド。 ここでは、両方の手順について説明します。  
  
> [!NOTE]
>  構築またはのいずれかを実行する前に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]サンプル、確実に実行する、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
### <a name="to-build-the-sample-using-a-command-prompt"></a>コマンド プロンプトを使用してサンプルをビルドするには  
  
1.  管理特権を使用して [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトを開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。  
  
2.  型`msbuild`コマンドライン。 クライアント プログラムが client\bin にビルドされ、サービス プログラムが service\bin にビルドされます。 サービスがインターネット インフォメーション サービス (IIS) によってホストされている場合は、サービス プログラム ファイルがさらに servicemodelsamples ディレクトリと、その \bin サブディレクトリにコピーされます。  
  
> [!NOTE]
>  %systemdrive%\inetpub\wwwroot 上の ACL を、実行中のアカウントに変更権限を付与するように設定する必要があります。 このように設定しない場合、ビルド後のイベントが失敗する場合があります。 代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトを管理者として実行することもできます。  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Visual Studio を使用してサンプルをビルドするには  
  
1.  使用している場合[!INCLUDE[wv](../../../../includes/wv-md.md)]、 [!INCLUDE[lserver](../../../../includes/lserver-md.md)]、Windows 7、または Windows Server 2008 R2、および実行[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]、引き上げられたアクセス許可で Visual Studio を実行する必要があります。 これを行うには、[スタート] メニューのアイコンを右クリックし、をクリックして**管理者として実行**です。  
  
2.  **ファイル**Visual Studio で、メニューをクリックして**開く**、順にクリックして**プロジェクト/ソリューション**です。 サンプルをインストールしたディレクトリの言語固有のサブディレクトリに移動し、Visual Studio でソリューションを開く .sln ファイルのアイコンをダブルクリックします。  
  
3.  **ビルド**メニューの **ソリューションのリビルド**です。 クライアント プログラムが client\bin にビルドされ、サービス プログラムが service\bin にビルドされます。 サービスが IIS によってホストされている場合は、サービス プログラム ファイルがさらに servicemodelsamples ディレクトリと、その \bin サブディレクトリにコピーされます。  
  
> [!NOTE]
>  %systemdrive%\inetpub\wwwroot 上の ACL を、実行中のアカウントに変更権限を付与するように設定する必要があります。 このように設定しない場合、ビルド後のイベントが失敗する場合があります。 代わりに、ACL の設定はそのままにして、SDK コマンド プロンプトまたは Visual Studio を管理者として実行することもできます。 Visual Studio の一部のアクション (デバッガを ASP.Net ワーカー プロセスにアタッチするアクションなど) では、さらに管理特権が必要です。  
  
## <a name="setup-batch-files-and-scripts"></a>セットアップ バッチ ファイルとスクリプト  
 Setup.exe バッチ ファイル、Cleanup.exe バッチ ファイル、およびスクリプトは、Visual Studio コマンド プロンプトから実行する必要があります。 いくつかのセットアップ ファイルとクリーンアップ ファイルは、管理特権が必要なタスクを実行します。したがって、これらのファイルは管理特権で起動する必要があります。  
  
## <a name="important-security-information-about-metadata-endpoints"></a>メタデータ エンドポイントに関する重要なセキュリティ情報  
 機密性の高いサービス メタデータが誤って漏洩を防ぐためには、Windows Communication Foundation (WCF) サービスの既定の構成はメタデータの公開を無効にします。 この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ発行の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール (Svcutil.exe など) を使用して生成できないことも意味します。 サンプルでの試みを容易にするため、ほとんどすべてのサンプルでは、セキュリティ保護されていないメタデータ公開エンドポイントを公開しています。 このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。 サービス メタデータの公開の詳細については、次を参照してください。、[メタデータ公開動作](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)サンプルです。 参照してください、[カスタム セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)メタデータ エンドポイントをセキュリティで保護するサンプルのサンプルです。  
  
## <a name="exception-handling"></a>例外処理  
 通常、コードではサンプルの主題を重視するので、これらのサンプルに例外処理は含まれていません。 例外処理の詳細については、次を参照してください。、[予想例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)サンプルです。  
  
## <a name="regenerating-clients-and-configuration-with-svcutil"></a>Svcutil を使用したクライアントと構成の再生成  
 使用することができます、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)をクライアント コードとサンプルのほとんどの構成を再生成します。 一部のサンプルでは、構成を手動で編集する必要があります。 たとえば、Svcutil.exe を使用して、クライアント証明書の資格情報を使用するサンプルの構成を再生成する場合は、以前に構成された資格情報を手動で指定する必要があります。 一部のサンプルでは、生成コードに影響を与える、Svcutil.exe の特定のオプションを使用します。これらのオプションは、そうした特定のサンプルのトピックで指定されます。  
  
#### <a name="to-regenerate-the-client-and-configuration-files"></a>クライアントと構成ファイルを再生成するには  
  
1.  SDK コマンド プロンプトを開き、サンプルのインストール ディレクトリに存在する言語固有のサブディレクトリに移動します。  
  
2.  サービスが Web ホスト型の場合は、次のコマンドを使用します。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     サービスが自己ホスト型の場合は、次のコマンドを使用します。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /out:generatedClient.cs  
    ```  
  
     置き換えるhttp://localhost:8000/ServiceModelSamples/service.svc/mex自己ホスト型サービスの mex エンドポイントのアドレスを使用します。  
  
     Visual Basic の型でクライアントを生成するには、次のコマンドを使用します。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
     サービスが自己ホスト型の場合は、次のコマンドを使用します。  
  
    ```  
    svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost:8000/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb  
    ```  
  
    > [!NOTE]
    >  スキップするクライアントの構成の生成を追加、 **/noConfig**オプション。  
  
## <a name="see-also"></a>関連項目  
 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)  
 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
