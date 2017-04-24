---
title: "アプリケーション開発 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アプリケーション開発 [WPF], 概要"
  - "WPF, アプリケーション開発の概要"
ms.assetid: 2996ce5e-81e9-49ae-881b-952db3dd1b7e
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# アプリケーション開発
<a name="introduction"></a> [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] は、次のような種類のアプリケーションやサービスを開発するために使用できるプレゼンテーション フレームワークです。  
  
-   スタンドアロン アプリケーション \(クライアント コンピューターにインストールし、そこから実行できる実行可能アセンブリとしてビルドされた従来スタイルの [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] アプリケーション\)。  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] \([!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] や Mozilla Firefox などの Web ブラウザーによってホストされ、実行可能アセンブリとしてビルドされた移動可能ページで構成されるアプリケーション\)。  
  
-   カスタム コントロール ライブラリ \(再利用可能なコントロールを含む非実行可能アセンブリ\)。  
  
-   クラス ライブラリ \(再利用可能なクラスを含む非実行可能アセンブリ\)。  
  
> [!NOTE]
>  Windows サービスで WPF 型を使用することは避けることを強くお勧めします。  Windows サービスでこれらの機能を使用すると、期待どおりの動作が得られない場合があります。  
  
 このような一連のアプリケーションをビルドするために、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は多数のサービスを実装しています。  このトピックでは、これらのサービスの概要を説明し、詳細情報へのリンクを示します。  
  
   
  
<a name="Application_Management"></a>   
## アプリケーション管理  
 実行可能 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションは、一般に次のコアな機能セットを必要とします。  
  
-   共通アプリケーション インフラストラクチャを作成し、これを管理する \(エントリ ポイント メソッドと、システム メッセージおよび入力メッセージを受け取るための Windows メッセージ ループの作成を含む\)。  
  
-   アプリケーションの有効期間を追跡し、これと相互作用する。  
  
-   コマンド ライン パラメーターを取得し、処理する。  
  
-   アプリケーション スコープのプロパティと [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] リソースを共有する。  
  
-   未処理の例外を検出し、これを処理する。  
  
-   終了コードを返す。  
  
-   スタンドアロン アプリケーションのウィンドウを管理する。  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] や、ナビゲーション ウィンドウとフレームを持つスタンドアロン アプリケーションで、ナビゲーションを追跡する。  
  
 これらの機能は、<xref:System.Windows.Application> クラスによって実装されます。このクラスをアプリケーションに追加するには、*アプリケーション定義*を使用します。  
  
 詳細については、「[アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)」を参照してください。  
  
<a name="WPF_Application_Resource__Content__and_Data_Files"></a>   
## WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、埋め込みリソースを扱う [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] のコア サポートを拡張して、リソース、コンテンツ、データの 3 種類の非実行可能データ ファイルのサポートを追加します。詳細については、「[WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)」を参照してください。  
  
 WPF 非実行可能データ ファイル サポートの重要なコンポーネントは、一意の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を使用してこれらのファイルを識別し、読み込む機能です。詳細については、「[WPF におけるパッケージの URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)」を参照してください。  
  
<a name="Windows_and_Dialog_Boxes"></a>   
## ウィンドウとダイアログ ボックス  
 ユーザーは、ウィンドウをとおして [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] スタンドアロン アプリケーションとやり取りします。  ウィンドウの目的は、アプリケーションのコンテンツをホストし、コンテンツとやり取りするためにユーザーが利用できるアプリケーション機能を公開することです。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、ウィンドウは <xref:System.Windows.Window> クラスにカプセル化されます。このクラスは、次の機能を備えています。  
  
-   ウィンドウを作成し、表示する。  
  
-   所有者と所有先ウィンドウの関係を確立する。  
  
-   ウィンドウの外観を構成する \(サイズ、位置、アイコン、タイトル バーのテキスト、境界など\)。  
  
-   ウィザードの有効期間を追跡し、これと相互作用する。  
  
 詳細については、「[WPF ウィンドウの概要](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)」を参照してください。  
  
 <xref:System.Windows.Window> は、ダイアログ ボックスと呼ばれる特別な種類のウィンドウを作成できます。  モーダル ダイアログ ボックスとモードレス ダイアログ ボックスの両方の種類のダイアログ ボックスを作成できます。  
  
 使いやすさ、再利用性の利点、およびアプリケーション全体の操作性の統一のために、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、[!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] のコモン ダイアログ ボックスから <xref:Microsoft.Win32.OpenFileDialog>、<xref:Microsoft.Win32.SaveFileDialog>、および <xref:System.Windows.Controls.PrintDialog> の 3 つを公開しています。  
  
 メッセージ ボックスは、重要な情報をテキストでユーザーに表示し、単純な \[はい\]、\[いいえ\]、\[OK\]、\[キャンセル\] の応答を求めるために使用する特別なダイアログ ボックスです。  メッセージ ボックスを作成して表示するには、<xref:System.Windows.MessageBox> クラスを使用します。  
  
 詳細については、「[ダイアログ ボックスの概要](../../../../docs/framework/wpf/app-development/dialog-boxes-overview.md)」を参照してください。  
  
<a name="Navigation"></a>   
## Navigation  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ページ \(<xref:System.Windows.Controls.Page>\) とハイパーリンク \(<xref:System.Windows.Documents.Hyperlink>\) を使用する Web スタイルのナビゲーションをサポートしています。  ナビゲーションは、次のようなさまざまな方法で実装できます。  
  
-   Web ブラウザーでホストされるスタンドアロンのページ。  
  
-   Web ブラウザーでホストされる [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] にコンパイルされるページ。  
  
-   スタンドアロン アプリケーションにコンパイルされ、ナビゲーション ウィンドウ \(<xref:System.Windows.Navigation.NavigationWindow>\) によってホストされるページ。  
  
-   フレーム \(<xref:System.Windows.Controls.Frame>\) によってホストされるページ。フレームは、スタンドアロン ページか、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] またはスタンドアロン アプリケーションにコンパイルされたページにホストされることがあります。  
  
 ナビゲーションに役立つように、次の機能が [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] に実装されます。  
  
-   アプリケーション内ナビゲーションをサポートするために <xref:System.Windows.Controls.Frame>、<xref:System.Windows.Navigation.NavigationWindow>、および [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] で使用される、ナビゲーション要求処理用の共有ナビゲーション エンジンである <xref:System.Windows.Navigation.NavigationService>。  
  
-   ナビゲーションを開始するために使用するナビゲーション メソッド。  
  
-   ナビゲーションの有効期間を追跡し、これと相互作用するために使用するナビゲーション イベント。  
  
-   履歴を使用した前方や後方へのナビゲーションの記録。履歴の情報は、調べたり操作したりすることもできます。  
  
 詳細については、「[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、構造化ナビゲーションと呼ばれる特別な種類のナビゲーションもサポートしています。  構造化ナビゲーションは、呼び出し元関数との一貫性が保たれた、構造化されて予測の可能な形式でデータを返す 1 つ以上のページを呼び出すために使用できます。  この機能は <xref:System.Windows.Navigation.PageFunction%601> クラスに依存します。このクラスの詳細については、「[構造化ナビゲーションの概要](../../../../docs/framework/wpf/app-development/structured-navigation-overview.md)」を参照してください。  また、<xref:System.Windows.Navigation.PageFunction%601> は、複雑なナビゲーション トポロジの作成を簡略化するためにも役立ちます。詳細については、「[ナビゲーション トポロジの概要](../../../../docs/framework/wpf/app-development/navigation-topologies-overview.md)」を参照してください。  
  
<a name="Hosting"></a>   
## ホスト  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、[!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)] または Firefox でホストできます。  ホストのモデルによって考慮事項や制約が異なります。詳細については、「[ホスト](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)」を参照してください。  
  
<a name="Build_and_Deploy"></a>   
## ビルドと配置  
 単純な [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションはコマンド ライン コンパイラを使用してコマンド プロンプトでビルドできますが、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] と [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] が統合されることで、開発とビルドのプロセスを簡略化するための追加サポートを使用できます。  詳細については、「[WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)」を参照してください。  
  
 ビルドするアプリケーションの種類によって、選択する配置オプションが異なります。  詳細については、「[WPF アプリケーションの配置](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)」を参照してください。  
  
<a name="related_topics"></a>   
## 関連トピック  
  
|Title|Description|  
|-----------|-----------------|  
|[アプリケーション管理の概要](../../../../docs/framework/wpf/app-development/application-management-overview.md)|アプリケーションの有効期間、ウィンドウ、アプリケーション リソース、ナビゲーションの管理など、<xref:System.Windows.Application> クラスの概要について説明します。|  
|[WPF のウィンドウ](../../../../docs/framework/wpf/app-development/windows-in-wpf-applications.md)|<xref:System.Windows.Window> クラスおよびダイアログ ボックスの使い方など、アプリケーション内のウィンドウ管理の詳細について説明します。|  
|[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)|アプリケーション内のページ間でのナビゲーション管理の概要について説明します。|  
|[ホスト](../../../../docs/framework/wpf/app-development/hosting-wpf-applications.md)|[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] の概要について説明します。|  
|[ビルドと配置](../../../../docs/framework/wpf/app-development/building-and-deploying-wpf-applications.md)|WPF アプリケーションをビルドして配置する方法について説明します。|  
|[Visual Studio 2015 での WPF の概要](../../../../docs/framework/wpf/getting-started/introduction-to-wpf-in-vs.md)|WPF の主な機能について説明します。|  
|[チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)|ページ ナビゲーション、レイアウト、コントロール、イメージ、スタイル、バインディングを使用する WPF アプリケーションの作成方法を示すチュートリアルです。|