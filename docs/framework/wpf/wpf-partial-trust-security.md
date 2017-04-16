---
title: "WPF 部分信頼セキュリティ | Microsoft Docs"
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
  - "デバッグ (部分信頼アプリケーションを)"
  - "検出 (アクセス許可を)"
  - "機能セキュリティ要件"
  - "管理 (アクセス許可を)"
  - "部分信頼アプリケーション, デバッグ"
  - "部分信頼セキュリティ"
  - "のアクセス許可, 検出"
  - "のアクセス許可, 管理"
  - "Internet Explorer のセキュリティ設定"
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
caps.latest.revision: 40
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 36
---
# WPF 部分信頼セキュリティ
<a name="introduction"></a> 一般に、悪質な被害を防止するため、インターネット アプリケーションによる重要なシステム リソースへの直接アクセスは制限する必要があります。  既定では、[!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)] およびクライアント側のスクリプト言語は、重要なシステム リソースにはアクセスできません。  [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] ブラウザー ホスト アプリケーションは、ブラウザーから起動できるため、同様に、一連の制限に従う必要があります。  この制限を適用するために、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] と [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] の両方に依存します \(「[WPF のセキュリティ方針 \- プラットフォーム セキュリティ](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)」を参照\)。  既定では、ブラウザー ホスト アプリケーションは、インターネット、ローカル イントラネット、ローカル コンピューターのどこから起動されたかに関係なく、インターネット ゾーン [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] のアクセス許可セットを要求します。  無制限ではないアクセス許可の元で実行するアプリケーションは、部分信頼で実行しているものと見なされます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、さまざまなサポートを提供し、最大限の機能を部分信頼で安全に使用できることを実現します。また、[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] と共に、部分信頼のプログラミングへの追加サポートを提供します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [WPF 機能の部分信頼サポート](#WPF_Feature_Partial_Trust_Support)  
  
-   [部分信頼のプログラミング](#Partial_Trust_Programming)  
  
-   [アクセス許可の管理](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## WPF 機能の部分信頼サポート  
 次の表は、インターネット ゾーン アクセス許可セットの制限内で、安全に使用できる [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] の高レベル機能の一覧です。  
  
 表 1 : 部分信頼で安全な WPF 機能  
  
|機能エリア|機能|  
|-----------|--------|  
|\[全般\]|ブラウザー ウィンドウ<br /><br /> 起点サイト アクセス<br /><br /> IsolatedStorage \(512 KB 制限\)<br /><br /> UIAutomation プロバイダー<br /><br /> コマンド実行<br /><br /> 入力方式エディター \(IME\)<br /><br /> タブレット スタイラスとインク<br /><br /> マウス キャプチャと移動イベントを使用してシミュレートされたドラッグ\/ドロップ<br /><br /> OpenFileDialog<br /><br /> XAML 逆シリアル化 \(XamlReader.Load 経由\)|  
|Web 統合|ブラウザー ダウンロード ダイアログ<br /><br /> トップレベル ユーザーが実行するナビゲーション<br /><br /> mailto: リンク<br /><br /> Uniform Resource Identifier パラメーター<br /><br /> HTTPWebRequest<br /><br /> IFRAME でホストされた WPF コンテンツ<br /><br /> フレームを使用した同一サイトの HTML ページのホスト<br /><br /> WebBrowser を使用した同一サイトの HTML ページのホスト<br /><br /> Web サービス \(ASMX\)<br /><br /> Web サービス \(Windows Communication Foundation を使用\)<br /><br /> スクリプト<br /><br /> ドキュメント オブジェクト モデル|  
|ビジュアル|2D と 3D<br /><br /> アニメーション<br /><br /> メディア \(起点サイトおよびドメイン間\)<br /><br /> イメージング\/オーディオ\/ビデオ|  
|読み取り|FlowDocument<br /><br /> XPS ドキュメント<br /><br /> 埋め込みフォントとシステム フォント<br /><br /> CFF フォントと TrueType フォント|  
|編集|スペル チェック<br /><br /> RichTextBox<br /><br /> プレーンテキストおよびインク クリップボード サポート<br /><br /> ユーザーが実行する貼り付け<br /><br /> 選択した内容のコピー|  
|コントロール|コントロール全般|  
  
 この表は、高レベルの [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 機能を示しています。  詳細情報に関して [!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)] では、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] の各メンバーが必要とするアクセス許可について文書化しています。  また、以下の機能については、特別な考慮事項など、部分信頼での実行に関するさらに詳細な情報があります。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] \(「[XAML の概要 \(WPF\)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照\)。  
  
-   ポップアップ \(<xref:System.Windows.Controls.Primitives.Popup?displayProperty=fullName> を参照\)  
  
-   ドラッグ アンド ドロップ \(「[ドラッグ アンド ドロップの概要](../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)」を参照\)。  
  
-   クリップボード \(<xref:System.Windows.Clipboard?displayProperty=fullName> を参照\)  
  
-   イメージング \(<xref:System.Windows.Controls.Image?displayProperty=fullName> を参照\)  
  
-   シリアル化 \(<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName>、<xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=fullName> を参照\)  
  
-   ファイルを開くダイアログ ボックス \(<xref:Microsoft.Win32.OpenFileDialog?displayProperty=fullName> を参照\)。  
  
 次の表は、インターネット ゾーン アクセス許可セットの制限内では、安全に実行できない [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] 機能の一覧です。  
  
 表 2 : 部分信頼で安全でない WPF 機能  
  
|機能エリア|機能|  
|-----------|--------|  
|\[全般\]|ウィンドウ \(アプリケーションで定義したウィンドウおよびダイアログ ボックス\)<br /><br /> SaveFileDialog<br /><br /> ファイル システム<br /><br /> レジストリへのアクセス<br /><br /> ドラッグ アンド ドロップ<br /><br /> XAML シリアル化 \(XamlWriter.Save 経由\)<br /><br /> UIAutomation クライアント<br /><br /> ソース ウィンドウ アクセス \(HwndHost\)<br /><br /> 完全な音声サポート<br /><br /> Windows フォームの相互運用性|  
|ビジュアル|ビットマップ効果<br /><br /> イメージ エンコード|  
|編集|リッチ テキスト形式のクリップボード<br /><br /> 完全な XAML サポート|  
  
<a name="Partial_Trust_Programming"></a>   
## 部分信頼のプログラミング  
 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] アプリケーションでは、コードが既定のアクセス許可セットを越える場合、セキュリティ ゾーンによって動作が異なります。  ユーザーがアプリケーションをインストールしようとすると警告が表示されることもあります。  ユーザーは、インストールを続行するか取り消すかを選択できます。  次の表は、各セキュリティ ゾーンのアプリケーション動作と、完全信頼を受け取るアプリケーションで行う必要のある操作を示しています。  
  
|セキュリティ ゾーン|\[動作\]|完全信頼を受け取るための操作|  
|----------------|------------|--------------------|  
|ローカル コンピューター|完全信頼を自動的に受け取る|アクションは必要ありません。|  
|イントラネットおよび信頼されたサイト|完全信頼のプロンプトを表示|ユーザーへのプロンプトにソースが表示されるように、証明書を使用して XBAP を署名します。|  
|インターネット|"信頼されていません" というメッセージが表示され、失敗する|証明書を使用して XBAP に署名します。|  
  
> [!NOTE]
>  前の表で説明した動作は、ClickOnce 信頼済み配置モデルに従っていない完全信頼の XBAP の動作です。  
  
 一般に、設定されているアクセス許可を超える可能性のあるコードは、スタンドアロン アプリケーションとブラウザー ホスト アプリケーションの間で共有される通常のコードと考えられます。  [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] と [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] には、このシナリオを処理するためのいくつかの手法が用意されています。  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### CAS を使用したアクセス許可の検出  
 状況によっては、ライブラリ アセンブリで共有されるコードを、スタンドアロン アプリケーションと [!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] の両方で使用することができます。  この場合、コードは、アプリケーションに付与されているアクセス許可セットの制限よりも高い許可を要求する機能を実行する可能性があります。  アプリケーションは、[!INCLUDE[TLA#tla_winfx](../../../includes/tlasharptla-winfx-md.md)] セキュリティを使用して、特定のアクセス許可を得ているかどうかを検出できます。  特に、必要なアクセス許可のインスタンスで <xref:System.Security.CodeAccessPermission.Demand%2A> メソッドを呼び出して、特定のアクセス許可を持っているかどうかをテストすることができます。  これを次の例に示します。このコードでは、ローカル ディスクにファイルを保存できるかどうかを照会します。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 アプリケーションに必要なアクセス許可がない場合、<xref:System.Security.CodeAccessPermission.Demand%2A> の呼び出しによって、セキュリティ例外がスローされます。  それ以外の場合は、アクセス許可が付与されます。  `IsPermissionGranted` は、この動作をカプセル化し、必要に応じて `true` または `false` を返します。  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### 機能の正常な低下  
 コードに必要なアクセス許可があるかどうかを検出できることは、別のゾーンから実行できるコードにとって重要です。  ゾーンが 1 つであることを検出している間に、可能であれば、ユーザーに代替手段を提供する方がより望ましいでしょう。  たとえば、完全信頼アプリケーションを使用すると、通常、ユーザーは任意の場所にファイルを作成できますが、部分信頼アプリケーションでは、ファイルを作成できるのは分離ストレージだけです。  ファイルを作成するコードが、完全信頼 \(スタンドアロン\) アプリケーションと部分信頼 \(ブラウザー ホスト\) アプリケーションとで共有されるアセンブリ内にある場合、ユーザーが両方のアプリケーションでファイルを作成できるようにするには、適切な場所にファイルを作成する前に、この共有されるコードが、部分信頼で実行されているのか完全信頼で実行されているのかを検出する必要があります。  次のコードで両方の例を示します。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 多くの場合、部分信頼の代替を見つける必要があります。  
  
 イントラネットなどの制御された環境では、カスタム マネージ フレームワークを、クライアント ベース全体にわたって、[!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)] にインストールすることができます。  このライブラリは、完全信頼を必要とするコードを実行することができ、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> を使用することで、部分信頼だけを付与されているアプリケーションからも参照できます \(詳細については、「[セキュリティ](../../../docs/framework/wpf/security-wpf.md)」および「[WPF のセキュリティ方針 \- プラットフォーム セキュリティ](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)」を参照してください\)。  
  
<a name="Browser_Host_Detection"></a>   
### ブラウザー ホストの検出  
 [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] を使用したアクセス許可の確認は、アクセス許可ごとの確認が必要な場合に適した手法です。  ただし、この手法は、通常の処理の一部として例外をキャッチすることに依存し、一般には推奨されません。また、パフォーマンスの問題を抱える可能性があります。  代わりに、[!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)] がインターネット ゾーンのサンドボックス内でのみ実行される場合、<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=fullName> プロパティを使用することができ、これは [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] に true を返します。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> は、アプリケーションがブラウザーで実行されているかどうかを区別するだけで、実行中のアプリケーションに付与されているアクセス許可セットについての区別はしません。  
  
<a name="Managing_Permissions"></a>   
## アクセス許可の管理  
 既定では、[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、部分信頼 \(既定のインターネット ゾーン アクセス許可セット\) で実行されます。  ただし、アプリケーションの要求に応じて、アクセス許可セットを既定から変更することができます。  たとえば、[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)] がローカル イントラネットから起動される場合、より高いアクセス許可セットを利用できます。これを次の表に示します。  
  
 表 3 : ローカル イントラネットのアクセス許可とインターネットのアクセス許可  
  
|Permission|属性|ローカル イントラネット|インターネット|  
|----------------|--------|------------------|-------------|  
|DNS|アクセス DNS サーバー|○|Ｘ|  
|環境変数|Read|○|Ｘ|  
|ファイル ダイアログ|\[Open\]|○|○|  
|ファイル ダイアログ|制限なし|○|Ｘ|  
|分離ストレージ|ユーザーによるアセンブリの分離|○|Ｘ|  
|分離ストレージ|不明な分離|○|○|  
|分離ストレージ|無制限のユーザー クォータ|○|Ｘ|  
|メディア|安全なオーディオ、ビデオ、イメージ|○|○|  
|印刷|既定の印刷|○|Ｘ|  
|印刷|安全な印刷|○|○|  
|リフレクション|出力|○|Ｘ|  
|セキュリティ|マネージ コードの実行|○|○|  
|セキュリティ|付与されたアクセス許可の Assert|○|Ｘ|  
|ユーザー インターフェイス|制限なし|○|Ｘ|  
|ユーザー インターフェイス|安全なトップレベル ウィンドウ|○|○|  
|ユーザー インターフェイス|独自のクリップボード|○|○|  
|Web ブラウザー|HTML への安全なフレーム ナビゲーション|○|○|  
  
> [!NOTE]
>  切り取りと貼り付けは、ユーザーが開始する部分信頼でのみ許可されます。  
  
 アクセス許可を増やす必要がある場合は、プロジェクト設定と ClickOnce アプリケーション マニフェストを変更する必要があります。  詳細については、「[WPF XAML ブラウザー アプリケーションの概要](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)」を参照してください。  次のドキュメントが役に立つこともあります。  
  
-   [Mage.exe \(マニフェストの生成および編集ツール\)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
-   [MageUI.exe \(マニフェスト生成および編集ツールのグラフィカル クライアント\)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
-   [ClickOnce アプリケーションのセキュリティ](../Topic/Securing%20ClickOnce%20Applications.md).  
  
 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] が完全信頼を必要とする場合、同じツールを使用して要求されたアクセス許可を強化できます。  ただし、[!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] は、イントラネットのローカル コンピューター上にインストールされ、ローカル コンピューターから起動されるか、ブラウザーの信頼されたサイトまたは許可されたサイトのリストに含まれる URL から起動する場合にのみ、完全信頼を受け取ります。  アプリケーションがイントラネットまたは信頼されたサイトからインストールされる場合、アクセス許可が昇格されたことを通知する標準の ClickOnce プロンプトがユーザーに表示されます。  ユーザーは、インストールを続行するか取り消すかを選択できます。  
  
 または、任意のセキュリティ ゾーンで完全信頼配置用の ClickOnce 信頼済み配置モデルを使用することもできます。  詳細については、「[信頼されたアプリケーションの配置の概要](../Topic/Trusted%20Application%20Deployment%20Overview.md)」および「[セキュリティ](../../../docs/framework/wpf/security-wpf.md)」を参照してください。  
  
## 参照  
 [セキュリティ](../../../docs/framework/wpf/security-wpf.md)   
 [WPF のセキュリティ方針 \- プラットフォーム セキュリティ](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)   
 [WPF のセキュリティ方針 \- セキュリティ エンジニアリング](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)