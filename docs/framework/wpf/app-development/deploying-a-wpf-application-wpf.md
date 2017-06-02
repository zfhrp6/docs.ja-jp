---
title: "WPF アプリケーションの配置 (WPF) | Microsoft Docs"
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
  - "配置 [WPF], アプリケーション"
  - "WPF アプリケーション, 配置"
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
caps.latest.revision: 27
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# WPF アプリケーションの配置 (WPF)
ビルドが終了した [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アプリケーションは配置する必要があります。  [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] および [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] には、いくつかの配置テクノロジがあります。  [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの配置に使用する配置テクノロジは、アプリケーションの種類によって決まります。  このトピックでは、配置テクノロジの概要と [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションで必要とされる配置の要件に関連して配置テクノロジがどのように使用されるかについて説明します。  
  
   
  
<a name="Deployment_Technologies"></a>   
## 配置テクノロジ  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] および [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] には、次の配置テクノロジがあります。  
  
-   XCopy による配置。  
  
-   [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]による配置。  
  
-   [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] 配置。  
  
<a name="XCopy_Deployment"></a>   
### XCopy による配置  
 XCopy による配置は、XCopy コマンド ライン プログラムを使用して、ある場所から別の場所へファイルをコピーする配置です。  XCopy による配置は、次のような状況に適しています。  
  
-   単独で使用でき、  実行するためにクライアントを更新する必要がないアプリケーションの場合。  
  
-   アプリケーション ファイルをある場所から別の場所、たとえば、ビルド場所 \(ローカル ディスクや [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] ファイル共有など\) から公開場所 \(Web サイトや [!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] ファイル共有など\) へ移動する必要がある場合。  
  
-   シェル統合 \(\[スタート\] メニュー ショートカットやデスクトップ アイコンなど\) を必要としないアプリケーションの場合。  
  
 XCopy は単純な配置シナリオには適していますが、複雑な配置が必要なシナリオには十分に対応できません。  特に、配置を高い信頼性で管理するためにスクリプトを作成、実行、および維持しようとすると、多くの場合に XCopy の使用はオーバーヘッドを招きます。  また、XCopy ではバージョン管理、アンインストール、およびロールバックがサポートされません。  
  
<a name="Windows_Installer"></a>   
### Windows インストーラー  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]を使用すると、クライアントに簡単に配布して実行できる自己完結型実行プログラムとしてアプリケーションをパッケージ化できます。  また、[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]は、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] と共にインストールされ、デスクトップ、\[スタート\] メニュー、および \[プログラム\] コントロール パネルとの統合を可能にします。  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]を使用するとアプリケーションを簡単にインストールまたはアンインストールできますが、インストールされたアプリケーションをバージョン管理の観点から最新の状態に保つ機能は提供されません。  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]の詳細については、「[Windows Installer Deployment](http://msdn.microsoft.com/ja-jp/121be21b-b916-43e2-8f10-8b080516d2a0)」を参照してください。  
  
<a name="ClickOnce_Deployment"></a>   
### ClickOnce の配置  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] を使用すると、非 Web アプリケーションを Web スタイル アプリケーションと同じように配置できます。つまり、アプリケーションは、Web サーバーまたはファイル サーバーに公開され、これらのサーバーから配置されます。  [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] は、[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]を使用してインストールされたアプリケーションが取得するクライアント側の機能を完全にはサポートしませんが、次の機能を備えています。  
  
-   \[スタート\] メニューおよび \[プログラム\] コントロール パネルとの統合。  
  
-   バージョン管理、ロールバック、およびアンインストール。  
  
-   アプリケーションを常に配置場所から起動する、オンライン インストール モード。  
  
-   新しいバージョンがリリースされたときの自動更新。  
  
-   ファイル拡張子の登録。  
  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] の詳細については、「[ClickOnce のセキュリティと配置](../Topic/ClickOnce%20Security%20and%20Deployment.md)」を参照してください。  
  
<a name="Deploying_WPF_Applications"></a>   
## WPF アプリケーションの配置  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの配置オプションは、アプリケーションの種類によって決まります。  配置の観点から見ると、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、次の 3 種類の重要なアプリケーションがあります。  
  
-   スタンドアロン アプリケーション。  
  
-   マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] アプリケーション。  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].  
  
<a name="Deploying_Standalone_Applications"></a>   
### スタンドアロン アプリケーションの配置  
 スタンドアロン アプリケーションは [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] または [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]を使用して配置されます。  いずれの場合も、スタンドアロン アプリケーションを実行するにはアプリケーションが完全に信頼されている必要があります。  [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]を使用して配置されたスタンドアロン アプリケーションには、完全な信頼が自動的に与えられます。  [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] を使用して配置されたスタンドアロン アプリケーションには、完全な信頼が自動的に与えられません。  代わりに、スタンドアロン アプリケーションをインストールする前に、[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] に表示されるセキュリティ警告ダイアログを受け入れる必要があります。  受け入れた場合は、スタンドアロン アプリケーションがインストールされ、完全な信頼が与えられます。  受け入れない場合、スタンドアロン アプリケーションはインストールされません。  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### マークアップのみの XAML アプリケーションの配置  
 通常、マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] ページのように Web サーバーに公開され、[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] を使用して表示できます。  マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは、部分信頼セキュリティ サンドボックス内で実行され、インターネット ゾーン アクセス許可セットに定義された制約が適用されます。  これにより、[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] ベース Web アプリケーションと同等のセキュリティ サンドボックスが提供されます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションのセキュリティの詳細については、「[セキュリティ](../../../../docs/framework/wpf/security-wpf.md)」を参照してください。  
  
 マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは、XCopy または [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)]を使用してローカル ファイル システムにインストールできます。  ページは、[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] または [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] エクスプローラーを使用して表示できます。  
  
 XAML の詳細については、「[XAML の概要 \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照してください。  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### XAML ブラウザー アプリケーションの配置  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、次の 3 つのファイルを配置する必要がある、コンパイル済みのアプリケーションです。  
  
-   *ApplicationName*.exe: 実行可能アセンブリ アプリケーション ファイル。  
  
-   *ApplicationName*.xbap: 配置マニフェスト。  
  
-   *ApplicationName*.exe.manifest: アプリケーション マニフェスト。  
  
> [!NOTE]
>  配置マニフェストおよびアプリケーション マニフェストの詳細については、「[WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)」を参照してください。  
  
 これらのファイルは、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] がビルドされるときに生成されます。  詳細については、「[方法 : 新しい WPF ブラウザー アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/ja-jp/72ef4d90-e163-42a1-8df0-ea7ccfd1901f)」を参照してください。  マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページと同様に、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は通常 Web サーバーに公開され、[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] を使用して表示されます。  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、任意の配置技術を使用してクライアントに配置できます。  ただし、[!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] には次の機能が備わっているので、この方法をお勧めします。  
  
1.  新しいバージョンが公開されたときの自動更新。  
  
2.  完全な信頼で実行される [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] の特権の昇格。  
  
 既定では、ClickOnce によって、.deploy という拡張子のアプリケーション ファイルが公開されます。  これは問題になる可能性がありますが、無効にできます。  詳細については、「[ClickOnce 配置でのサーバーおよびクライアント構成の問題](../Topic/Server%20and%20Client%20Configuration%20Issues%20in%20ClickOnce%20Deployments.md)」を参照してください。  
  
 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] の配置の詳細については、「[WPF XAML ブラウザー アプリケーションの概要](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)」を参照してください。  
  
<a name="Installing__NET_Framework_3_0"></a>   
## .NET Framework のインストール  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションを実行するには、クライアントに [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] がインストールされている必要があります。  [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] では、ブラウザーでホストされる [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションを表示するときに、クライアントに [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がインストールされているかどうかが自動で検出されます。  [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がインストールされていない場合、[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] によって、インストールを要求するメッセージが表示されます。  
  
 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がインストールされているかどうかを検出するために、[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] には、.xaml、.xps、.xbap、および .application の拡張子を持つコンテンツ ファイルのフォールバック [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] ハンドラーとして登録されているブートストラップ アプリケーションが含まれています。  これらの種類のファイルに移動するときに、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がクライアントにインストールされていないと、ブートストラップ アプリケーションによってインストールに同意することが要求されます。  ユーザーがインストールに同意しない場合、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] もアプリケーションもインストールされません。  
  
 同意した場合は、[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] で [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)] を使用して [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がダウンロードされ、インストールされます。  [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] が正しくインストールされると、最初に要求されたファイルが新しいブラウザー ウィンドウで開きます。  
  
 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] の自動検出機能は、[!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] 以降がインストールされている [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)] クライアント、[!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)] クライアント、および [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] クライアントで利用できます。  
  
 詳細については、「[.NET Framework およびアプリケーションの配置](../../../../docs/framework/deployment/net-framework-and-applications.md)」を参照してください。  
  
## 参照  
 [WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [セキュリティ](../../../../docs/framework/wpf/security-wpf.md)