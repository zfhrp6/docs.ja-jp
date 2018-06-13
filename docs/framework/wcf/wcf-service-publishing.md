---
title: WCF サービス発行
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: 258c7e65b69648477e58880f35b100a9378dc9c0
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806462"
---
# <a name="wcf-service-publishing"></a>WCF サービス発行
実際にテスト目的で実稼働環境へのアプリケーションを配置する WCF サービス ホストおよび WCF テスト クライアントによって提供される初期の開発環境からの Windows Communication Foundation (WCF) サービスの公開、使用できます。 最終的な配置計画を確定する前に、Windows Communication Foundation (WCF) サービスの公開を使用して、WCF サービスが正しく動作し、発行する準備ができていることを確認します。 テストのさまざまなターゲットの場所に、WCF サービス ライブラリを展開することもできます。  
  
## <a name="supported-services-and-target-locations"></a>サポートされているサービスとターゲットの場所  
 WCF サービス発行は、WCF サービス ライブラリ テンプレートと、以下にそれらの対応する項目テンプレートのセットから作成された WCF サービスの公開をサポートしています。  
  
-   WCF サービス ライブラリ テンプレートと項目テンプレート。  
  
-   配信サービス ライブラリ  
  
 これらのサービス テンプレートを検索するを選択する**ファイル** -> **新しいプロジェクト** -> **Visual Basic**または**Visual c#**  ->  **WCF**です。 この場所 (WCF ワークフロー サービス アプリケーションと WCF サービス アプリケーションを含む) では、他の WCF テンプレートの使用を発行できます[ワンクリックで web アプリケーションの発行](https://msdn.microsoft.com/library/dd465337\(v=vs.110\).aspx)です。  
  
 サービスは、次のターゲットの場所に発行できます。  
  
-   ローカル IIS  
  
-   ファイル システム  
  
-   FTP サイト  
  
## <a name="using-wcf-service-publishing"></a>WCF サービス発行の使用  
 サービス実装を配置するには、次の手順を実行します。  
  
1.  管理者特権で Visual Studio を開きます (実行可能ファイルを右クリックし、"管理者として実行 を使用して起動する)。  IIS 7.0 を使用しているか、後で、「IIS メタベースおよび IIS6 構成との互換性」を使用してコンポーネントをインストールしたことを確認してください"' にする Windows の機能のオンまたはオフ"コントロール パネルの します。  
  
2.  サービス プロジェクトを開き、選択**ビルド**->**発行\<プロジェクト名 >** メイン メニュー でプロジェクトを右クリックしてまたは**ソリューション エクスプ ローラー** をクリック**発行**です。  
  
3.  **発行**ウィンドウが表示されます。 クリックして、**しています**. サービスの配置先にするターゲットの場所を指定します。 ローカルの IIS、ファイル システム、または FTP サイトにアプリケーションを配置するを選択することができます。 ローカル IIS にアプリケーションを配置する場合、web サイトを選択してクリックして、その下にある web アプリケーションを作成、、**新しい Web アプリケーションの作成**右上隅にあるアイコン。  
  
4.  クリックした後**発行**メイン ウィンドウで、Visual Studio が、指定したターゲットの場所にアプリケーションが配置され、Web.config、.svc、およびアセンブリ ファイルをコピー先のディレクトリにコピーします。 である必要があります。 .Svc ファイルの名前は"projectname.servicename.svc"です。 サービスが正常に発行されると、「ハイパーリンクへの接続」のような Visual Studio の出力 ウィンドウでホットリンクを見つけることができますhttp://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName ..."です。 Ctrl キーを押しながらリンクをクリックすると、Visual Studio の内側にブラウザー ページが開き、サービス ディレクトリ構造が表示されます。  
  
     サイトを参照できない場合、IIS でディレクトリ ブラウザーが有効になっていない可能性があります。 有効にする「ものをしようとする」セクションで説明するヒントに従ってください。 また、直接入力できます"ハイパーリンク"http://localhost/WebApplicationFolderName" http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc"をサービスのページを表示します。  
  
 使用することができます**発行**をアセンブリ、構成、およびターゲットの場所にプロジェクトで定義されているすべてのサービスの .svc ファイルをコピーするかどうかを指定し、転送先に既存のファイルを上書きします。  
  
 ローカルの IIS にアプリケーションを配置すると、IIS セットアップに関連するエラーが発生することがあります。 IIS が正しくインストールされていることを確認してください。 「ハイパーリンク」を入力するhttp://localhost" http://localhost"ブラウザー チェックでかどうか、IIS の既定のページが表示されます。  場合によっては、問題を IIS に ASP.NET または WCF 適切に登録して発生もあります。 Visual Studio コマンド プロンプトを開くと、コマンド"aspnet_regiis.exe-ir"を実行すると、ASP.NET 登録に関する問題を修正または WCF 登録に関する問題を修正する"ServiceModelReg.exe – ia"コマンドを実行できます。  
  
## <a name="files-generated-for-publishing"></a>発行用に生成されるファイル  
 次のファイルが、ツールによって生成された WCF サービス ライブラリは、Web ホストされることができます、前に: アセンブリ ファイル、Web.config ファイル、および .svc ファイル。 生成されたファイルは、すべてターゲットの場所にコピーされます。 その後でサービスが発行されます。  
  
### <a name="assembly-files"></a>アセンブリ ファイル  
 WCF サービスを発行するときにこのツールを使用して、サービスは最初に自動的に構築し、ビルド後のサービス プロジェクトでアセンブリ ファイルが生成します。  
  
### <a name="svc-file"></a>.SVC ファイル  
 公開操作では、ファイルが存在するか、バージョンの有効性を確保するかどうかに、WCF サービスごとに *.svc ファイルが生成されます。 2 つの異なる種類の svc ファイルがある: WCF サービス ライブラリおよび配信サービス ライブラリ、および順次とステート マシン ワークフロー サービス ライブラリのもう 1 つです。 生成された\*.svc ファイルは、ターゲットの場所のルート フォルダーにコピーします。  
  
### <a name="webconfig-file"></a>Web.config ファイル  
 サービス プロジェクトが特定のターゲットの場所に発行されるたびに、Web.config ファイルが作成されます。  
  
 生成された Web.config ファイルには、Web ホスティング、および WCF サービス ライブラリは、次の変更を App.config の内容に役立つ Web セクションが含まれます。  
  
-   ベース アドレスが除外されています。  
  
-   ターゲット プラットフォームのトレース設定を保持するために、`<diagnostics>` 要素の設定が除外されています。  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>IIS への非 HTTP バインドを使用した WCF サービスの公開  
 非 HTTP バインドを IIS で WCF サービスを公開した後で、IIS7.0 を使用している場合。 事前の構成を行う必要があります。 詳細についてにあるトピックを参照してください[Windows Process Activation Service でのホスティング](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)です。  
  
## <a name="security"></a>セキュリティ  
 IIS は管理者アカウントで実行する必要があるため、ローカル IIS に発行するには、管理特権が必要です。 管理者特権のないユーザーが WCF サービス発行が開いた場合は IIS はターゲットの場所として使用できません。 ファイル システム、または FTP サイトへの発行は、管理者特権のない動作します。  
  
## <a name="see-also"></a>関連項目  
 [WCF Visual Studio テンプレート](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
