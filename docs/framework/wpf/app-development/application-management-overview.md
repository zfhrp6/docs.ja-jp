---
title: "アプリケーション管理の概要 | Microsoft Docs"
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
  - "アプリケーション管理 [WPF]"
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
caps.latest.revision: 56
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 52
---
# アプリケーション管理の概要
すべてのアプリケーションは実装と管理に適用する機能を共有されることがよくあります。  このトピックでは作成および管理アプリケーションに <xref:System.Windows.Application> クラスの機能の概要について説明します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
## Application クラス  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では共通のアプリケーション スコープの機能は <xref:System.Windows.Application> のクラスにカプセル化されます。  <xref:System.Windows.Application> のクラスは次の機能が含まれています :  
  
-   アプリケーションの有効期間を追跡し、これと対話する。  
  
-   コマンド ライン パラメーターを取得し、処理する。  
  
-   未処理の例外を検出し、これに応答する。  
  
-   アプリケーション スコープのプロパティとリソースを共有する。  
  
-   スタンドアロン アプリケーションのウィンドウを管理する。  
  
-   ナビゲーションを追跡し管理する。  
  
<a name="The_Application_Class"></a>   
## アプリケーション クラスを使用して一般的なタスクを実行する方法  
 <xref:System.Windows.Application> クラスのすべての詳細を必要としないそれらの実行方法を次の表に <xref:System.Windows.Application> の一般的なタスクの一覧です。  関連 API とトピックを表示することによって詳細およびサンプル コードを参照できます。  
  
|タスク|方法|  
|---------|--------|  
|現在のアプリケーションを表すオブジェクトを取得します。|<xref:System.Windows.Application.Current%2A?displayProperty=fullName> プロパティを使用します。|  
|アプリケーションが起動画面を追加します。|「[スプラッシュ スクリーンを WPF アプリケーションに追加する](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)」を参照してください。|  
|アプリケーションを起動します。|<xref:System.Windows.Application.Run%2A?displayProperty=fullName> メソッドを使用してください。|  
|アプリケーションを停止します。|<xref:System.Windows.Application.Current%2A> オブジェクトの <xref:System.Windows.Application.Shutdown%2A?displayProperty=fullName> メソッドを使用します。|  
|コマンド ラインから引数を取得します。|<xref:System.Windows.Application.Startup?displayProperty=fullName> のイベントを処理し<xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=fullName> のプロパティを使用します。  例については<xref:System.Windows.Application.Startup?displayProperty=fullName> のイベントを参照してください。|  
|アプリケーション終了コードを取得および設定します。|<xref:System.Windows.Application.Exit?displayProperty=fullName> のイベント ハンドラーの <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=fullName> のプロパティを設定するか<xref:System.Windows.Application.Shutdown%2A> のメソッドを呼び出し整数を渡します。|  
|未処理の例外を検出して応答します|<xref:System.Windows.Application.DispatcherUnhandledException> イベントを処理します。|  
|アプリケーション スコープのリソースを取得および設定します。|<xref:System.Windows.Application.Resources%2A?displayProperty=fullName> プロパティを使用します。|  
|アプリケーション スコープのリソース ディクショナリを使用します。|「[アプリケーション スコープのリソース ディクショナリを使用する](../../../../docs/framework/wpf/app-development/how-to-use-an-application-scope-resource-dictionary.md)」を参照してください。|  
|アプリケーション スコープのプロパティを取得および設定します。|<xref:System.Windows.Application.Properties%2A?displayProperty=fullName> プロパティを使用します。|  
|アプリケーションの状態を取得および格納します。|「[アプリケーション セッション全体でアプリケーション スコープのプロパティを永続化および復元する](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md)」を参照してください。|  
|リソース ファイルコンテンツ ファイルおよび起点サイトに関するデータ ファイルなどコード ファイルを管理します。|「[WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)」を参照してください。|  
|スタンドアロン アプリケーションのウィンドウを管理する|「[WPF ウィンドウの概要](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)」を参照してください。|  
|ナビゲーションを追跡および管理します。|「[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)」を参照してください。|  
  
<a name="The_Application_Definition"></a>   
## アプリケーション定義  
 <xref:System.Windows.Application> クラスの機能を利用するにはアプリケーション定義を実装する必要があります。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーション定義は <xref:System.Windows.Application> の派生クラスで、特別な [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] 設定を使用して構成します。  
  
### アプリケーション定義の実装  
 一般的な [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーション定義は、マークアップと分離コードの両方を使用して実装します。  そのため、マークアップを使用して、アプリケーションのプロパティやリソースの設定、イベントの登録を宣言したり、分離コードを使用して、イベントの処理やアプリケーション固有の動作を実装したりすることができます。  
  
 マークアップと分離コードの両方を使用してアプリケーション定義を実装する方法を次の例に示します。  
  
 [!code-xml[ApplicationSnippets#ApplicationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 マークアップ ファイルと分離コード ファイルを連携させるには、次のようにする必要があります。  
  
-   マークアップの `Application` 要素に、`x:Class` 属性を含める必要があります。  アプリケーションのビルド時にマークアップ ファイルに `x:Class` が含まれていると、[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] は、`x:Class` 属性で指定された名前を持つ、<xref:System.Windows.Application> から派生した `partial` クラスを作成します。  そのためには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] スキーマ \(`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`\) に [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間宣言を追加する必要があります。  
  
-   分離コードでは、クラスは、マークアップ内の `x:Class` 属性で指定されている名前を持つ `partial` クラスでなければなりません。また、<xref:System.Windows.Application> から派生する必要があります。  これによって、分離コード ファイルと、アプリケーションのビルド時にマークアップ ファイル用に生成される`partial`クラスとが関連付けられます \(「[WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)」を参照\)。  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を使用して WPF アプリケーション プロジェクトまたは WPF ブラウザー アプリケーション プロジェクトを新しく作成すると、アプリケーション定義が既定で含まれ、マークアップと分離コードの両方を使用して定義されます。  
  
 このコードは、アプリケーション定義を実装するために最低限必要です。  ただし、アプリケーションをビルドして実装する前に、追加の [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 構成をアプリケーション定義に対して行う必要があります。  
  
### MSBuild 用のアプリケーション定義の構成  
 スタンドアロン アプリケーションや [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] を実行できるようにするには、一定レベルのインフラストラクチャの実装が必要です。  このインフラストラクチャの最も重要な部分はエントリ ポイントです。  ユーザーがアプリケーションを起動するとき、オペレーティング システムはエントリ ポイントを呼び出します。これは、オペレーティング システムがアプリケーションを起動するための機能としてよく知られています。  
  
 従来、テクノロジに応じて、このコードの一部または全部を開発者が記述する必要がありました。  しかし、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、アプリケーション定義のマークアップ ファイルを [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` 項目として構成すると、次の [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] プロジェクト ファイルに示すように、このコードが自動生成されます。  
  
```  
<Project   
  DefaultTargets="Build"  
  xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 分離コード ファイルにはコードが含まれているので、通常どおり、[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` 項目としてマークされます。  
  
 これらの [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] 構成をアプリケーション定義のマークアップや分離コード ファイルに適用すると、[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] によって次のようなコードが生成されます。  
  
 [!code-csharp[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode1)]
 [!code-vb[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode1)]  
[!code-csharp[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode2)]
[!code-vb[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode2)]  
  
 生成されるコードにより、アプリケーション定義にインフラストラクチャ コードが追加され、そこに `Main` というエントリ ポイント メソッドが含まれます。  <xref:System.STAThreadAttribute> 属性が `Main` メソッドに適用され、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションのメイン [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] スレッドが [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションに必須の STA スレッドであることを示します。これが呼び出されると、`Main` は `App` の新しいインスタンスを作成し、続いて `InitializeComponent` メソッドを呼び出して、イベントを登録し、マークアップに実装されているプロパティを設定します。  `InitializeComponent` は自動生成されるので、<xref:System.Windows.Controls.Page> および <xref:System.Windows.Window> の実装とは異なり、`InitializeComponent` をアプリケーションから明示的に呼び出す必要はありません。  最後に、<xref:System.Windows.Application.Run%2A> メソッドが呼び出され、アプリケーションを起動します。  
  
<a name="Getting_the_Current_Application"></a>   
## 現在のアプリケーションの取得  
 <xref:System.Windows.Application> クラスの機能がアプリケーション全体で共有されるため<xref:System.AppDomain> に対して <xref:System.Windows.Application> クラスの 1 個のインスタンスは一つだけです。  このことを強制するため、<xref:System.Windows.Application> クラスはシングルトン クラスとして実装されます \(「[Implementing Singleton in C\#](http://go.microsoft.com/fwlink/?LinkId=100567)」を参照\)。つまり、インスタンスを 1 つだけ作成し、`static` <xref:System.Windows.Application.Current%2A> プロパティを使用してインスタンスへの共有アクセスを提供します。  
  
 現在の <xref:System.AppDomain> の <xref:System.Windows.Application> オブジェクトへの参照を取得する方法を次のコードに示します。  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A> は、<xref:System.Windows.Application> クラスのインスタンスへの参照を返します。  <xref:System.Windows.Application> 派生クラスへの参照が必要な場合、<xref:System.Windows.Application.Current%2A> プロパティの値を、次の例に示すようにキャストしなければなりません。  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A> の値は、<xref:System.Windows.Application> オブジェクトが有効である間はいつでも確認できます。  ただし、注意が必要です。  <xref:System.Windows.Application> クラスがインスタンス化されると、<xref:System.Windows.Application> オブジェクトの状態に一貫性が失われる期間が生じます。  この期間中、<xref:System.Windows.Application> は、アプリケーション インフラストラクチャの確立、プロパティの設定、イベントの登録など、コードの実行に必要なさまざまな初期化タスクを実行します。  この期間中に <xref:System.Windows.Application> オブジェクトを使用しようとすると、特に設定中の各種 <xref:System.Windows.Application> プロパティにコードが依存している場合に、コードで予期しない結果が生じる可能性があります。  
  
 <xref:System.Windows.Application> の実質的な有効期間は、初期化作業が完了した時点から始まります。  
  
<a name="Application_Lifetime"></a>   
## アプリケーションの有効期間  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの有効期間は、アプリケーションが起動されたこと、アプリケーションがアクティブ、および非アクティブになったこと、シャットダウンされたことなどを通知するために <xref:System.Windows.Application> で発生するいくつかのイベントによって規定されます。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Splash_Screen"></a>   
### スプラッシュ スクリーン  
 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] 以降では、スタートアップ ウィンドウ \(*スプラッシュ スクリーン*\) で使用されるイメージを指定できます。  <xref:System.Windows.SplashScreen> クラスを使用すると、アプリケーションの読み込みの間、スタートアップ ウィンドウを簡単に表示できます。  <xref:System.Windows.SplashScreen> ウィンドウは、<xref:System.Windows.Application.Run%2A> を呼び出す前に作成されて表示されます。  詳細については、「[アプリケーションの起動時間](../../../../docs/framework/wpf/advanced/application-startup-time.md)」および「[スプラッシュ スクリーンを WPF アプリケーションに追加する](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md)」を参照してください。  
  
<a name="Starting_an_Application"></a>   
### アプリケーションの起動  
 <xref:System.Windows.Application.Run%2A> が呼び出され、アプリケーションが初期化されると、アプリケーションの実行準備が整います。  このタイミングは、<xref:System.Windows.Application.Startup> イベントが発生したときに通知されます。  
  
 [!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind1)]
 [!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind1)]  
[!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind2)]
[!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind2)]  
  
 アプリケーションの有効期間中のこの時点で一般的に行われるのは [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の表示です。  
  
<a name="Showing_a_User_Interface"></a>   
### ユーザー インターフェイスの表示  
 一般的なスタンドアロン [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] アプリケーションは、実行を開始すると <xref:System.Windows.Window> を開きます。  次のコードに示すように、<xref:System.Windows.Application.Startup> イベント ハンドラーはそれを行うことができる場所の 1 つです。  
  
 [!code-xml[AppShowWindowHardSnippets#StartupEventMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  スタンドアロン アプリケーションで最初にインスタンス化される <xref:System.Windows.Window> は、既定でメイン アプリケーション ウィンドウになります。  この <xref:System.Windows.Window> オブジェクトは、<xref:System.Windows.Application.MainWindow%2A?displayProperty=fullName> プロパティによって参照されます。  最初にインスタンス化された <xref:System.Windows.Window> 以外のウィンドウをメイン ウィンドウにする必要がある場合は、<xref:System.Windows.Application.MainWindow%2A> プロパティの値をプログラムで変更できます。  
  
 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] が最初に起動すると、一般的には <xref:System.Windows.Controls.Page> にナビゲートされます。  コードは次のようになります。  
  
 [!code-xml[XBAPAppStartupSnippets#StartupXBAPMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 <xref:System.Windows.Application.Startup> の処理目的が <xref:System.Windows.Window> を開くことまたは <xref:System.Windows.Controls.Page> にナビゲートすることのみの場合は、代わりに `StartupUri` 属性をマークアップに設定できます。  
  
 <xref:System.Windows.Application.StartupUri%2A> をスタンドアロン アプリケーションで使用して <xref:System.Windows.Window> を開く方法を次の例に示します。  
  
 [!code-xml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 <xref:System.Windows.Application.StartupUri%2A> を [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] で使用して <xref:System.Windows.Controls.Page> にナビゲートする方法の例を次に示します。  
  
 [!code-xml[PageSnippets#XBAPStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 このマークアップは、ウィンドウを開くことについて、前のコードと同じ効果があります。  
  
> [!NOTE]
>  ナビゲーションの詳細については、「[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)」を参照してください。  
  
 既定ではないコンストラクターを使用してウィンドウをインスタンス化する必要がある場合、ウィンドウのプロパティやサブプロパティを設定してから表示する必要がある場合、またはアプリケーションの起動時に指定されたコマンド ライン引数を処理する必要がある場合は、<xref:System.Windows.Window> を開くために <xref:System.Windows.Application.Startup> イベントを処理する必要があります。  
  
<a name="Processing_Command_Line_Arguments"></a>   
### コマンド ライン引数の処理  
 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] では、スタンドアロン アプリケーションはコマンド プロンプトまたはデスクトップから起動できます。  どちらの場合でも、アプリケーションにコマンド ライン引数を渡すことができます。単一のコマンド ライン引数 "\/StartMinimized" を指定して起動されるアプリケーションの例を次に示します。  
  
 `wpfapplication.exe /StartMinimized`  
  
 アプリケーションの初期化中に、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] はオペレーティング システムからコマンド ライン引数を取得し、<xref:System.Windows.StartupEventArgs> パラメーターの <xref:System.Windows.StartupEventArgs.Args%2A> プロパティ経由で、<xref:System.Windows.Application.Startup> イベント ハンドラーにそれらの引数を渡します。  コマンド ライン引数を取得および格納するには、次のようなコードを使用します。  
  
 [!code-xml[ApplicationStartupSnippets#HandleStartupXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 このコードは <xref:System.Windows.Application.Startup> を処理し、**\/StartMinimized** コマンド ライン引数が指定されているかどうかを検証します。指定されている場合、<xref:System.Windows.WindowState> が <xref:System.Windows.WindowState> であるメイン ウィンドウを開きます。  <xref:System.Windows.Window.WindowState%2A> プロパティはプログラムで設定する必要があるため、メイン <xref:System.Windows.Window> はコードで明示的に開く必要があります。  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] はコマンド ライン引数の取得や処理ができません。これは、[!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 展開を使用して起動されるためです \(「[WPF アプリケーションの配置](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)」を参照\)。  ただし、起動に使用される URL のクエリ文字列パラメーターは取得して処理できます。  
  
<a name="Application_Activation_and_Deactivation"></a>   
### アプリケーションのアクティブ化および非アクティブ化  
 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] では、ユーザーがアプリケーションを切り替えることができます。Alt キーを押しながら Tab キーを押すのが一般的なやり方です。  アプリケーションを切り替えるには、アプリケーションに、ユーザーが選択できる可視の <xref:System.Windows.Window> が必要がです。  現在選択されている <xref:System.Windows.Window> は*アクティブ ウィンドウ*と呼ばれ \(*前面ウィンドウ*とも呼ばれる\)、これがユーザー入力を受け取る <xref:System.Windows.Window> になります。アクティブ ウィンドウを持つアプリケーションは*アクティブ アプリケーション* \(または*前面アプリケーション*\) と呼ばれます。アプリケーションは、次の場合にアクティブ アプリケーションになります。  
  
-   起動され、<xref:System.Windows.Window> を表示した。  
  
-   ユーザーがそのアプリケーションの <xref:System.Windows.Window> を選択して別のアプリケーションから切り替えた。  
  
 アプリケーションがアクティブになったことを検出するには、<xref:System.Windows.Application.Activated?displayProperty=fullName> イベントを処理します。  
  
 同様に、アプリケーションは次の場合に非アクティブになります。  
  
-   ユーザーが現在のアプリケーションから別のアプリケーションに切り替えた。  
  
-   アプリケーションがシャットダウンされた。  
  
 アプリケーションが非アクティブになったことを検出するには、<xref:System.Windows.Application.Deactivated?displayProperty=fullName> イベントを処理します。  
  
 <xref:System.Windows.Application.Activated> イベントと <xref:System.Windows.Application.Deactivated> イベントを処理してアプリケーションがアクティブかどうかを判断する方法を次のコードに示します。  
  
 [!code-xml[ApplicationActivationSnippets#DetectActivationStateXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 <xref:System.Windows.Window> もアクティブまたは非アクティブにできます。  詳細については、「<xref:System.Windows.Window.Activated?displayProperty=fullName>」および「<xref:System.Windows.Window.Deactivated?displayProperty=fullName>」を参照してください。  
  
> [!NOTE]
>  <xref:System.Windows.Application.Activated?displayProperty=fullName> も <xref:System.Windows.Application.Deactivated?displayProperty=fullName> も [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] に対しては発生しません。  
  
<a name="Application_Shutdown"></a>   
### アプリケーションのシャットダウン  
 アプリケーションの有効期間は、シャットダウンと同時に終了します。シャットダウンは次の理由で発生します。  
  
-   ユーザーがすべての <xref:System.Windows.Window> を閉じた。  
  
-   ユーザーがメイン <xref:System.Windows.Window> を閉じた。  
  
-   ユーザーがログオフまたはシャットダウンして、[!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] を終了した。  
  
-   アプリケーション固有の条件が満たされた。  
  
 アプリケーションのシャットダウンの管理を支援するため、<xref:System.Windows.Application> には <xref:System.Windows.Application.Shutdown%2A> メソッド、<xref:System.Windows.Application.ShutdownMode%2A> プロパティ、<xref:System.Windows.Application.SessionEnding> イベント、および <xref:System.Windows.Application.Exit> イベントが用意されています。  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A> は、<xref:System.Security.Permissions.UIPermission> を持つアプリケーションでのみ呼び出すことができます。  スタンドアロン [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には必ずこのアクセス許可があります。  ただし、インターネット ゾーン部分信頼のセキュリティ サンドボックス内で実行される [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] には含まれません。  
  
#### シャットダウン モード  
 ほとんどのアプリケーションは、すべてのウィンドウが閉じられるか、メイン ウィンドウが閉じられると、シャットダウンします。  ただし、アプリケーションのシャットダウンに他のアプリケーション固有の条件が関係する場合もあります。  アプリケーションのシャットダウン条件は、<xref:System.Windows.Application.ShutdownMode%2A> を次のいずれかの <xref:System.Windows.ShutdownMode> 列挙値で設定できます。  
  
-   <xref:System.Windows.ShutdownMode>  
  
-   <xref:System.Windows.ShutdownMode>  
  
-   <xref:System.Windows.ShutdownMode>  
  
 <xref:System.Windows.Application.ShutdownMode%2A> の既定値は <xref:System.Windows.ShutdownMode> です。これは、アプリケーションの最後のウィンドウが閉じられると自動的にシャットダウンすることを意味します。  一方、メイン ウィンドウが閉じられたときにアプリケーションがシャットダウンするようにする必要がある場合は、<xref:System.Windows.Application.ShutdownMode%2A> を <xref:System.Windows.ShutdownMode> に設定すると、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] が自動的にシャットダウンします。  これを次の例に示します。  
  
 [!code-xml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 アプリケーション固有のシャットダウン条件がある場合は、<xref:System.Windows.Application.ShutdownMode%2A> を <xref:System.Windows.ShutdownMode> に設定します。  この場合は、プログラムで <xref:System.Windows.Application.Shutdown%2A> メソッドを明示的に呼び出してアプリケーションをシャットダウンする必要があります。そうしないと、すべてのウィンドウが閉じた後も、アプリケーションは実行したままになります。  <xref:System.Windows.Application.Shutdown%2A> は、<xref:System.Windows.Application.ShutdownMode%2A> が <xref:System.Windows.ShutdownMode> または <xref:System.Windows.ShutdownMode> の場合、暗黙に呼び出されます。  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A> は [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] から設定できますが、無視されます。[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] は、ブラウザーで他にナビゲートされた場合、または [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] をホストするブラウザーが閉じられた場合に、必ずシャットダウンします。  詳細については、「[ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)」を参照してください。  
  
#### セッションの終了  
 <xref:System.Windows.Application.ShutdownMode%2A> プロパティで記述されたシャットダウン条件は、アプリケーション固有です。  ただし、場合によっては、外部条件の結果としてシャットダウンすることもあります。  一般的な外部条件は、ユーザーが次の操作によって [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] セッションを終了した場合です。  
  
-   ログオフ  
  
-   シャットダウン  
  
-   再起動  
  
-   休止  
  
 [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] セッションの終了を検出するには、次の例に示すように、<xref:System.Windows.Application.SessionEnding> イベントを処理します。  
  
 [!code-xml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 この例では、コードは <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> プロパティ検証して、[!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] セッションの終了方法を判別します。  この値は、ユーザーに対する確認メッセージの表示に使用されます。  ユーザーがセッションの終了を意図していない場合、コードで <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> が `true` に設定されるため、[!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] セッションは終了しません。  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding> は [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] に対しては発生しません。  
  
#### Exit  
 アプリケーションは、シャットダウン時に、アプリケーション状態の保存などの最終処理を必要とする場合があります。  そのような状況のためには、<xref:System.Windows.Application.Exit> イベントを処理できます。  
  
 [!code-xml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml1)]  
[!code-xml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml2)]  
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind1)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind1)]  
[!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind2)]
[!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind2)]  
  
 コード例全体については、「[アプリケーション セッション全体でアプリケーション スコープのプロパティを永続化および復元する](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md)」を参照してください。  
  
 <xref:System.Windows.Application.Exit> は、スタンドアロン アプリケーション、および [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] の両方で処理できます。  [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] では、次の場合に <xref:System.Windows.Application.Exit> が発生します。  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] が外部にナビゲートされた。  
  
-   [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] で、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] をホストしていたタブが閉じられた。  
  
-   ブラウザーが閉じられた。  
  
#### 終了コード  
 ほとんどのアプリケーションは、ユーザー要求に応じてオペレーティング システムから起動されます。  しかし、別のアプリケーションから起動されて特定のタスクを実行するアプリケーションもあります。  起動されたアプリケーションをシャットダウンするときに、起動したアプリケーションがそのシャットダウン理由を必要とする場合があります。  そのような場合に、[!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] ではアプリケーションがシャットダウン時にアプリケーション終了コードを返すことができます。  既定では、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションは終了コード値として 0 を返します。  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でデバッグする場合、アプリケーション終了コードは、アプリケーションのシャットダウン時に、**\[出力\]** ウィンドウに次のようなメッセージと共に表示されます。  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  **\[出力\]** ウィンドウを開くには、**\[表示\]** メニューの **\[出力\]** をクリックします。  
  
 終了コードを変更するには、<xref:System.Windows.Application.Shutdown%28System.Int32%29> オーバーロードを呼び出します。これが、終了コードとして整数値の引数を受け付けます。  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 <xref:System.Windows.Application.Exit> イベントを処理することで、終了コードの値を検出して変更できます。  <xref:System.Windows.Application.Exit> イベント ハンドラーには <xref:System.Windows.ExitEventArgs> が渡され、<xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> プロパティによって終了コードへのアクセスが提供されます。  詳細については、「<xref:System.Windows.Application.Exit>」を参照してください。  
  
> [!NOTE]
>  終了コードは、スタンドアロン アプリケーション、および [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] のいずれでも設定できます。  ただし、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] では終了コード値は無視されます。  
  
<a name="Unhandled_Exceptions"></a>   
### 未処理の例外  
 アプリケーションは、予期しない例外が発生したときなどに、異常条件によりシャットダウンする可能性があります。  この場合、アプリケーションにはその例外を検出して処理するためのコードがありません。  このような例外はハンドルされない例外と呼ばれ、アプリケーションが閉じる前に次の図に示すような通知が表示されます。  
  
 ![ハンドルされない例外通知](../../../../docs/framework/wpf/app-development/media/applicationmanagementoverviewfigure2.png "ApplicationManagementOverviewFigure2")  
  
 ユーザー エクスペリエンスの観点から、アプリケーションではこの既定の動作を使用せず、次の一部またはすべてを行うことをお勧めします。  
  
-   わかりやすい情報を表示する。  
  
-   アプリケーションを続行するよう試みる。  
  
-   開発者向けの詳細な例外情報を [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] イベント ログに記録する。  
  
 このサポートを実装するには、ハンドルされない例外を検出できることが前提となります。ハンドルされない例外を検出するには、発生する <xref:System.Windows.Application.DispatcherUnhandledException> イベントを検出します。  
  
 [!code-xml[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
 [!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind1)]
 [!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind1)]  
[!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind2)]
[!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind2)]  
  
 <xref:System.Windows.Application.DispatcherUnhandledException> イベント ハンドラーには、未処理の例外に関するコンテキスト情報を含む <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> パラメーターが渡されます。この情報には、例外自体 \(<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=fullName>\) も含まれます。  この情報を使用して、例外の処理方法を確認できます。  
  
 <xref:System.Windows.Application.DispatcherUnhandledException> を処理するときは、必ず <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=fullName> プロパティを `true` に設定します。そうしないと、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] はその例外を未処理のままと見なし、先に説明した既定の動作に戻ります。  ハンドルされない例外が発生し、かつ <xref:System.Windows.Application.DispatcherUnhandledException> イベントが処理されないか、イベントが処理されても <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> の設定が `false` である場合、アプリケーションは直ちにシャットダウンします。  また、他の <xref:System.Windows.Application> イベントは発生しません。  したがって、アプリケーションのシャットダウン前に実行する必要があるコードがある場合は、<xref:System.Windows.Application.DispatcherUnhandledException> を処理する必要があります。  
  
 アプリケーションは、ハンドルされない例外の結果、シャットダウンする可能性がありますが、通常は、次のセクションで示すように、ユーザーの要求に呼応する形でシャットダウンします。  
  
<a name="Application_Lifetime_Events"></a>   
### アプリケーションの有効期間イベント  
 スタンドアロン アプリケーションと [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] とで、有効期間が厳密に同じというわけではありません。スタンドアロン アプリケーションの有効期間内の主なイベントとその発生順を次の図に示します。  
  
 ![スタンドアロン アプリケーション &#45; アプリケーション オブジェクト イベント](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview\_ApplicationObjectEvents")  
  
 同様に、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] の有効期間内の主要イベントとその発生順を次の図に示します。  
  
 ![XBAP &#45; アプリケーション オブジェクト イベント](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview\_ApplicationObjectEvents\_xbap")  
  
## 参照  
 <xref:System.Windows.Application>   
 [WPF ウィンドウの概要](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)   
 [ナビゲーションの概要](../../../../docs/framework/wpf/app-development/navigation-overview.md)   
 [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)   
 [WPF におけるパッケージの URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)   
 [Application Model: How\-to Topics](http://msdn.microsoft.com/ja-jp/76771b09-3688-4d1c-8818-9b3f4cf39a30)   
 [アプリケーション開発](../../../../docs/framework/wpf/app-development/index.md)