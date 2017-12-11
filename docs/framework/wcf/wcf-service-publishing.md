---
title: "WCF サービス発行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 526544118432eb263cc856931d9f4943b9918d93
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-service-publishing"></a>WCF サービス発行
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービス発行は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ホストと [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] テスト クライアントで構成される初期の開発環境から、テストの目的でアプリケーションを実際に実稼働環境に配置する場合に役立ちます。 最終的な配置計画を確定する前に、[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービス発行を使用して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスが正しく動作し、発行の準備ができていることを確認できます。 また、テスト用のさまざまなターゲットの場所に [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリを配置することもできます。  
  
## <a name="supported-services-and-target-locations"></a>サポートされているサービスとターゲットの場所  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス発行は、一連の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ テンプレートと、それらに対応する項目テンプレートから作成された、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスの発行をサポートしています。これには以下が含まれます。  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリ テンプレートと項目テンプレート  
  
-   配信サービス ライブラリ  
  
 これらのサービス テンプレートを検索するを選択する**ファイル** -> **新しいプロジェクト** -> **Visual Basic**または**Visual c#**  ->  **WCF**です。 この場所 (WCF ワークフロー サービス アプリケーションと WCF サービス アプリケーションを含む) では、他の WCF テンプレートの使用を発行できます[ワンクリックで web アプリケーションの発行](https://msdn.microsoft.com/en-us/library/dd465337\(v=vs.110\).aspx)です。  
  
 サービスは、次のターゲットの場所に発行できます。  
  
-   ローカル IIS  
  
-   ファイル システム  
  
-   FTP サイト  
  
## <a name="using-wcf-service-publishing"></a>WCF サービス発行の使用  
 サービス実装を配置するには、次の手順を実行します。  
  
1.  管理者特権で Visual Studio を開きます (実行可能ファイルを右クリックし、"管理者として実行 を使用して起動する)。  IIS 7.0 を使用しているか、後で、「IIS メタベースおよび IIS6 構成との互換性」を使用してコンポーネントをインストールしたことを確認してください"' にする Windows の機能のオンまたはオフ"コントロール パネルの します。  
  
2.  サービス プロジェクトを開き、選択**ビルド**->**発行\<プロジェクト名 >** メイン メニュー でプロジェクトを右クリックしてまたは**ソリューション エクスプ ローラー** をクリック**発行**です。  
  
3.  **発行**ウィンドウが表示されます。 クリックして、**しています.**. サービスの配置先にするターゲットの場所を指定します。 ローカルの IIS、ファイル システム、または FTP サイトにアプリケーションを配置するを選択することができます。 ローカル IIS にアプリケーションを配置する場合、web サイトを選択してクリックして、その下にある web アプリケーションを作成、、**新しい Web アプリケーションの作成**右上隅にあるアイコン。  
  
4.  クリックした後**発行**メイン ウィンドウで、Visual Studio が、指定したターゲットの場所にアプリケーションが配置され、Web.config、.svc、およびアセンブリ ファイルをコピー先のディレクトリにコピーします。 。 .Svc ファイルの名前は"projectname.servicename.svc"です。 サービスが正常にパブリッシュされた後、Visual Studio の出力 ウィンドウで、「ハイパーリンク"http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName... に接続する」のようなホットリンクが表示されます。 Ctrl キーを押しながらリンクをクリックすると、Visual Studio の内側にブラウザー ページが開き、サービス ディレクトリ構造が表示されます。  
  
     サイトを参照できない場合、IIS でディレクトリ ブラウザーが有効になっていない可能性があります。 有効にする「ものをしようとする」セクションで説明するヒントに従ってください。 代わりに、直接入力できます"ハイパーリンク"http://localhost/WebApplicationFolderName"http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc"をサービスのページを表示します。  
  
 使用することができます**発行**をアセンブリ、構成、およびターゲットの場所にプロジェクトで定義されているすべてのサービスの .svc ファイルをコピーするかどうかを指定し、転送先に既存のファイルを上書きします。  
  
 ローカルの IIS にアプリケーションを配置すると、IIS セットアップに関連するエラーが発生することがあります。 IIS が正しくインストールされていることを確認してください。 お使いのブラウザーに"ハイパーリンク"http://localhost"http://localhost"を入力し、IIS の既定のページに表示されているかどうかをチェックできます。  ASP.NET または [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] が IIS に適切に登録されていないために問題が発生する場合もあります。 Visual Studio コマンド プロンプトを開くと、コマンド"aspnet_regiis.exe-ir"を実行すると、ASP.NET 登録に関する問題を修正または WCF 登録に関する問題を修正する"ServiceModelReg.exe – ia"コマンドを実行できます。  
  
## <a name="files-generated-for-publishing"></a>発行用に生成されるファイル  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリを Web でホストできるようになる前に、アセンブリ ファイル、Web.config ファイル、および .svc ファイルがツールによって生成されます。 生成されたファイルは、すべてターゲットの場所にコピーされます。 その後でサービスが発行されます。  
  
### <a name="assembly-files"></a>アセンブリ ファイル  
 このツールを使用して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを発行すると、まずサービスが自動的にビルドされ、サービス プロジェクトでアセンブリ ファイルが生成されます。  
  
### <a name="svc-file"></a>.SVC ファイル  
 発行操作を行うと、*.svc ファイルが存在するかどうかにかかわらず、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスごとに *.svc ファイルが生成され、バージョンの有効性が確認されます。 svc ファイルには、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリおよび配信サービス ライブラリ用と、シーケンシャル ワークフロー サービス ライブラリおよびステート マシン ワークフロー サービス ライブラリ用の 2 種類があります。 生成された\*.svc ファイルは、ターゲットの場所のルート フォルダーにコピーします。  
  
### <a name="webconfig-file"></a>Web.config ファイル  
 サービス プロジェクトが特定のターゲットの場所に発行されるたびに、Web.config ファイルが作成されます。  
  
 生成された Web.config ファイルには、Web ホストに役立つ Web セクションと、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス ライブラリの App.config の内容に次の変更を加えたものが含まれています。  
  
-   ベース アドレスが除外されています。  
  
-   ターゲット プラットフォームのトレース設定を保持するために、`<diagnostics>` 要素の設定が除外されています。  
  
## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a>IIS への非 HTTP バインドを使用した WCF サービスの公開  
 IIS7.0 以降を使用している場合、非 HTTP バインドを使用した [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービスを IIS に公開することができます。 事前の構成を行う必要があります。 詳細についてにあるトピックを参照してください[Windows Process Activation Service でのホスティング](../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)です。  
  
## <a name="security"></a>セキュリティ  
 IIS は管理者アカウントで実行する必要があるため、ローカル IIS に発行するには、管理特権が必要です。 管理特権のないユーザーが [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] サービス発行を開いた場合、IIS はターゲットの場所として使用できません。 ファイル システム、または FTP サイトへの発行は、管理者特権のない動作します。  
  
## <a name="see-also"></a>関連項目  
 [WCF Visual Studio テンプレート](../../../docs/framework/wcf/wcf-vs-templates.md)  
 [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
 [WCF のテスト用クライアント (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
