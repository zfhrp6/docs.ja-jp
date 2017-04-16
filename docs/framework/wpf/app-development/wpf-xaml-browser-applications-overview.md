---
title: "WPF XAML ブラウザー アプリケーションの概要 | Microsoft Docs"
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
  - "ブラウザーによってホストされるアプリケーション [WPF]"
  - "WPF XAML ブラウザー アプリケーション (XBAP)"
  - "XAML ブラウザー アプリケーション (XBAP)"
  - "XBAP, XAML ブラウザー アプリケーション"
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
caps.latest.revision: 47
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 47
---
# WPF XAML ブラウザー アプリケーションの概要
<a name="introduction"></a> [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] は、Web アプリケーションとリッチ クライアント アプリケーションの両方の機能を組み合わせます。  Web アプリケーションと同様、XBAP は Web サーバーに配置して、Internet Explorer または Firefox から開始できます。  また、リッチ クライアント アプリケーションと同じように、XBAP は [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の機能を活用できます。  XBAP の開発方法もリッチ クライアントの開発に似ています。  このトピックでは、XBAP 開発の高度な概略を示し、XBAP 開発が標準的なリッチ クライアント開発と異なる点について説明します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [新しい XAML ブラウザー アプリケーション \(XBAP\) の作成](#creating_a_new_xaml_browser_application_xbap)  
  
-   [XBAP の配置](#deploying_a_xbap)  
  
-   [ホスト Web ページとの通信](#communicating_with_the_host_web_page)  
  
-   [XBAP セキュリティの考慮事項](#xbap_security_considerations)  
  
-   [XBAP 起動時のパフォーマンスに関する考慮事項](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## 新しい XAML ブラウザー アプリケーション \(XBAP\) の作成  
 新しい XBAP プロジェクトを作成する最も簡単な方法は、[!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)] を使用することです。  新しいプロジェクトを作成するときは、テンプレートのリストから **\[WPF ブラウザー アプリケーション\]** をクリックします。  詳細については、「[方法 : 新しい WPF ブラウザー アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/ja-jp/72ef4d90-e163-42a1-8df0-ea7ccfd1901f)」を参照してください。  
  
 XBAP プロジェクトを実行すると、スタンドアロン ウィンドウではなくブラウザー ウィンドウで開かれます。  XBAP を [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] でデバッグする場合、アプリケーションはインターネット ゾーン アクセス許可付きで実行されるため、そのアクセス許可を超えるとセキュリティ例外がスローされます。  詳細については、「[セキュリティ](../../../../docs/framework/wpf/security-wpf.md)」および「[WPF 部分信頼セキュリティ](../../../../docs/framework/wpf/wpf-partial-trust-security.md)」を参照してください。  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] を使用して開発していない場合やプロジェクト ファイルについて詳しく知りたい場合は、「[WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)」を参照してください。  
  
<a name="deploying_a_xbap"></a>   
## XBAP の配置  
 XBAP をビルドすると、次の 3 つのファイルが生成されます。  
  
|File|Description|  
|----------|-----------------|  
|実行可能ファイル \(.exe\)|コンパイル済みのコードが含まれます。拡張子は .exe です。|  
|アプリケーション マニフェスト \(.manifest\)|これにはアプリケーションに関連付けられたメタデータが含まれ、拡張子は .manifest です。|  
|配置マニフェスト \(.xbap\)|[!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] がアプリケーションの配置に使用する情報が含まれます。このファイルの拡張子は .xbap です。|  
  
 XBAP は Web サーバー \([!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] 以降のバージョンなど\) に配置します。  [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] を Web サーバーにインストールする必要はありませんが、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] 型とファイル名拡張子を登録する必要はあります。  詳細については、「[WPF アプリケーションを配置するように IIS 5.0 および IIS 6.0 を構成する](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md)」を参照してください。  
  
 XBAP を配置用に準備するには、.exe および関連付けられたマニフェストを Web サーバーにコピーします。  配置マニフェスト \(拡張子が .xbap のファイル\) を開くためのハイパーリンクを含む HTML ページを作成します。  ユーザーが .xbap ファイルへのリンクをクリックすると、[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] がアプリケーションのダウンロードと開始を自動的に処理します。  次のプログラム例では、XBAP を指し示すハイパーリンクを含む HTML ページを示しています。  
  
```  
<html>   
  <head></head>  
  <body>   
    <a href="XbapEx.xbap">Click this link to launch the application</a>  
  </body>   
</html>  
  
```  
  
 XBAP は、Web ページのフレーム内にホストすることもできます。  1 つまたは複数のフレームを持つ Web ページを作成します。  配置マニフェスト ファイルに対するフレームのソース プロパティを設定します。  ホストする Web ページと XBAP との間で、組み込まれた機構を使用して通信を行う場合は、アプリケーションをフレーム内にホストする必要があります。  次のプログラム例では、2 つのフレームを持つ HTML ページ \(2 つ目のフレームのソースが XBAP に設定されています\) を示しています。  
  
```  
<html>   
  <head>A page with frames.</head>  
    <frameset cols="50%,50%">   
      <frame src="introduction.htm" >   
      <frame src="XbapEx.xbap" >   
  </frameset>   
</html>  
```  
  
### キャッシュされた XBAP の削除  
 XBAP をビルドし直して開始した後に、旧バージョンの XBAP が開かれることがあります。  たとえば、この動作は XBAP アセンブリのバージョン番号が静的である場合に、XBAP をコマンド ラインから開始すると起こることがあります。  この場合、キャッシュされているバージョン \(それまで開始されていたバージョン\) と新しいバージョンとでバージョン番号が変わらないので、XBAP の新しいバージョンはダウンロードされません。  代わりに、キャッシュされたバージョンが読み込まれます。  
  
 このような場合は、**Mage** コマンド \(Visual Studio または [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)] と共にインストールされる\) をコマンド プロンプトで使用して、キャッシュされているバージョンを削除できます。  次のコマンドでアプリケーション キャッシュを消去します。  
  
 `Mage.exe -cc`  
  
 このコマンドを実行すると、最新バージョンの XBAP が開かれるようになります。  アプリケーションを [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でデバッグするときは、XBAP の最新バージョンを開始する必要があります。一般的に、配置バージョン番号は、ビルドするたびに更新することをお勧めします。  Mage.exe の詳細については、「[Mage.exe \(マニフェストの生成および編集ツール\)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)」を参照してください。  
  
<a name="communicating_with_the_host_web_page"></a>   
## ホスト Web ページとの通信  
 アプリケーションが HTML フレーム内でホストされている場合、XBAP を含む Web ページと通信することができます。  この処理は、<xref:System.Windows.Interop.BrowserInteropHelper> の <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> プロパティを取得することで実行できます。  このプロパティは、HTML ウィンドウを表すスクリプト オブジェクトを返します。  [window オブジェクト](http://go.microsoft.com/fwlink/?LinkId=160274)上のプロパティ、メソッドおよびイベントへは、標準のドット構文を使ってアクセスできます。  スクリプト メソッドおよびグローバル変数にアクセスすることもできます。  次の例は、スクリプト オブジェクトを取得してブラウザーを閉じる方法を示しています。  
  
 [!code-csharp[XbapBrowserInterop#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### HostScript を使用する XBAP のデバッグ  
 XBAP で <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> オブジェクトを使用して HTML ウィンドウと通信する場合に、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] でアプリケーションを実行およびデバッグするには、2 つの設定を指定する必要があります。  つまり、アプリケーションから元のサイトにアクセスできる必要があると同時に、そのアプリケーションを XBAP を含む HTML ページで開始する必要があるということです。  これら 2 つの設定を確認する方法を次の手順で説明します。  
  
1.  Visual Studio でプロジェクトのプロパティを開きます。  
  
2.  **\[セキュリティ\]** タブの **\[詳細設定\]** をクリックします。  
  
     \[セキュリティの詳細設定\] ダイアログ ボックスが表示されます。  
  
3.  **\[アプリケーション アクセスをその元のサイトに与える\]** チェック ボックスがオンになっていることを確認し、**\[OK\]** をクリックします。  
  
4.  **\[デバッグ\]** タブで、**\[ブラウザーを開始時に使用する URL\]** をクリックし、XBAP を含む HTML ページの URL を指定します。  
  
5.  Internet Explorer で、**\[ツール\]** をクリックし、**\[インターネット オプション\]** をクリックします。  
  
     \[インターネット オプション\] ダイアログ ボックスが表示されます。  
  
6.  **\[詳細設定\]** タブをクリックします。  
  
7.  **\[セキュリティ\]** の下にある **\[設定\]** ボックスで、**\[マイ コンピューターのファイルでのアクティブ コンテンツの実行を許可する\]** チェック ボックスをオンにします。  
  
8.  **\[OK\]** をクリックします。  
  
     変更は、Internet Explorer を再起動すると有効になります。  
  
> [!CAUTION]
>  Internet Explorer でアクティブ コンテンツを有効にすると、コンピューターが危険にさらされるおそれがあります。  詳細については、「[Internet Explorer のセキュリティとプライバシーの機能](http://go.microsoft.com/fwlink/?LinkId=179286)」を参照してください。  Internet Explorer のセキュリティ設定を変更したくない場合は、HTML ページをサーバーから起動して、[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] デバッガーをプロセスにアタッチできます。  
  
<a name="xbap_security_considerations"></a>   
## XBAP セキュリティの考慮事項  
 XBAP は通常、インターネット ゾーン アクセス許可セットに制限された部分信頼セキュリティ サンドボックス内で実行する必要があります。  したがって、実装ではインターネット ゾーン内でサポートされている [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素のサブセットをサポートするか、またはアプリケーションのアクセス許可を昇格させる必要があります。  詳細については、「[セキュリティ](../../../../docs/framework/wpf/security-wpf.md)」を参照してください。  
  
 <xref:System.Windows.Controls.WebBrowser> コントロールをアプリケーションで使用する場合、内部的には WPF によってネイティブ WebBrowser ActiveX コントロールがインスタンス化されます。  アプリケーションが Internet Explorer で実行している部分信頼の XBAP である場合、ActiveX コントロールは Internet Explorer プロセスの専用スレッドで実行されます。  このため、次の制限が適用されます。  
  
-   <xref:System.Windows.Controls.WebBrowser> コントロールでは、セキュリティ上の制限などのホスト ブラウザーに似た動作を提供する必要があります。  このようなセキュリティ上の制限は、Internet Explorer のセキュリティ設定を使用して制御できます。  詳細については、「[セキュリティ](../../../../docs/framework/wpf/security-wpf.md)」を参照してください。  
  
-   XBAP がドメインをまたいで HTML ページにロードされると、例外がスローされます。  
  
-   入力が WPF <xref:System.Windows.Controls.WebBrowser> とは別のスレッドで行われるため、キーボード入力を受け取ることができず、IME の状態が共有されません。  
  
-   ActiveX コントロールが他のスレッド上で実行されるため、ナビゲーションのタイミングまたは順序が異なることがあります。  たとえば、ページへの移動が、別のナビゲーション要求の開始によって取り消されない場合があります。  
  
-   WPF アプリケーションが独立したスレッドで実行されるため、カスタムの ActiveX コントロールに通信上の問題が発生することがあります。  
  
-   <xref:System.Windows.Interop.HwndHost.MessageHook> は発生しません。<xref:System.Windows.Interop.HwndHost> が他のスレッドまたはプロセスで実行中のウィンドウをサブクラス化できないためです。  
  
### 完全信頼の XBAP の作成  
 XBAP で完全信頼が必要な場合、プロジェクトを変更してこのアクセス許可を有効にできます。  完全信頼を有効にする手順を次に示します。  
  
1.  Visual Studio でプロジェクトのプロパティを開きます。  
  
2.  **\[セキュリティ\]** タブで、**\[これは完全に信頼するアプリケーションです\]** をクリックします。  
  
 この設定により、次の変更が実行されます。  
  
-   プロジェクト ファイル内の `<TargetZone>` 要素の値が `Custom` に変更される。  
  
-   アプリケーション マニフェスト \(app.manifest\) の `Unrestricted="true"` 属性が `PermissionSet` 要素に追加される。  
  
    ```  
    <PermissionSet class="System.Security.PermissionSet"   
        version="1"   
        ID="Custom"   
        SameSite="site"   
        Unrestricted="true"   
    />  
    ```  
  
### 完全信頼の XBAP の配置  
 ClickOnce 信頼済み配置モデルに従っていない完全信頼の XBAP を配置した場合、ユーザーがアプリケーションを実行したときの動作は、セキュリティ ゾーンに依存します。  ユーザーがアプリケーションをインストールしようとすると警告が表示されることもあります。  ユーザーは、インストールを続行するか取り消すかを選択できます。  次の表は、各セキュリティ ゾーンのアプリケーション動作と、完全信頼を受け取るアプリケーションで行う必要のある操作を示しています。  
  
|セキュリティ ゾーン|\[動作\]|完全信頼を受け取るための操作|  
|----------------|------------|--------------------|  
|ローカル コンピューター|完全信頼を自動的に受け取る|アクションは必要ありません。|  
|イントラネットおよび信頼されたサイト|完全信頼のプロンプトを表示|ユーザーへのプロンプトにソースが表示されるように、証明書を使用して XBAP を署名します。|  
|インターネット|"信頼されていません" というメッセージが表示され、失敗する|証明書を使用して XBAP に署名します。|  
  
> [!NOTE]
>  前の表で説明した動作は、ClickOnce 信頼済み配置モデルに従っていない完全信頼の XBAP の動作です。  
  
 完全信頼の XBAP を配置する場合は、ClickOnce 信頼済み配置モデルを使用することをお勧めします。  このモデルにより、セキュリティ ゾーンに関係なく XBAP に完全信頼を自動的に付与できるため、ユーザーにプロンプトが表示されることはありません。  このモデルの一部としては、信頼された発行元からの証明書を使用してアプリケーションを署名する必要があります。  細については、「[信頼されたアプリケーションの配置の概要](../Topic/Trusted%20Application%20Deployment%20Overview.md)」および「[Introduction to Code Signing \(コード署名の概要\)](http://go.microsoft.com/fwlink/?LinkId=166327)」を参照してください。  
  
<a name="xbap_start_time_performance_considerations"></a>   
## XBAP 起動時のパフォーマンスに関する考慮事項  
 XBAP のパフォーマンスにとって重要な側面は、その起動時にあります。  最初に読み込む WPF アプリケーションが XBAP である場合は、*コールド スタート*時間が 10 秒以上かかる可能性があります。  これは、進行状況ページは WPF によってレンダリングされますが、アプリケーションを表示するには CLR と WPF の両方をコールド スタートする必要があるためです。  
  
 [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)] 以降、XBAP のコールド スタート時間は、アンマネージ進行状況ページを配置サイクルの初期に表示することで短縮されています。進行状況ページは、ネイティブ ホスティング コードによって表示され、HTML でレンダリングされるので、ほぼアプリケーションの起動直後に表示されます。  
  
 さらに、[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] のダウンロード シーケンスの同時実行の改良によって、開始時間は最大 10% 短縮されます。  [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] がマニフェストをダウンロードして評価した後、アプリケーションのダウンロードが開始され、プログレス バーの更新が開始されます。  
  
## 参照  
 [Visual Studio を構成して Web サービスを呼び出す XAML ブラウザー アプリケーションをデバッグする](../../../../docs/framework/wpf/app-development/configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)   
 [WPF アプリケーションの配置](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)