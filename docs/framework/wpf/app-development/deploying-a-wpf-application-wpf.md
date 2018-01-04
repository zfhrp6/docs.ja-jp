---
title: "WPF アプリケーションの配置 (WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF applications [WPF], deployment
- deployment [WPF], applications
ms.assetid: 12cadca0-b32c-4064-9a56-e6a306dcc76d
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c7addef624ee8a41e2f421e0d912efbbaac6eb5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-a-wpf-application-wpf"></a>WPF アプリケーションの配置 (WPF)
ビルドされた [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] アプリケーションは、配置する必要があります。 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] および [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] には、いくつかの配置テクノロジがあります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの配置に使用される配置テクノロジは、アプリケーションの種類によって決まります。 このトピックでは、それぞれの配置テクノロジの概要と使用法を、それぞれの [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの種類の配置要件に関連して説明します。  
  
   
<a name="Deployment_Technologies"></a>   
## <a name="deployment-technologies"></a>配置テクノロジ  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] および [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] には、次のような、いくつかの配置テクノロジがあります。  
  
-   XCopy による配置。  
  
-   [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] による配置。  
  
-   [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] による配置。  
  
<a name="XCopy_Deployment"></a>   
### <a name="xcopy-deployment"></a>XCopy による配置  
 XCopy による配置とは、XCopy コマンド ライン プログラムを使用して、ある場所から別の場所へファイルをコピーすることです。 XCopy による配置は、次のような状況に適しています。  
  
-   アプリケーションは自己完結型である。 実行するためにクライアントを更新する必要がない。  
  
-   アプリケーション ファイルをある場所から別の場所へ、たとえば、ビルド場所 (ローカル ディスク、[!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] ファイル共有など) から公開場所 (Web サイト、[!INCLUDE[TLA2#tla_unc](../../../../includes/tla2sharptla-unc-md.md)] ファイル共有など) へ移動する必要がある。  
  
-   アプリケーションはシェル統合 ([スタート] メニューのショートカット、デスクトップ アイコンなど) を必要としない。  
  
 XCopy は、単純な配置シナリオには適していますが、複雑な配置機能が必要なシナリオには十分に対応できません。 特に、配置を堅牢な方法で管理する場合、XCopy を使用すると、スクリプトの作成、実行、および維持というオーバーヘッドが生じます。 さらに、XCopy は、バージョン管理、アンインストール、およびロールバックをサポートしません。  
  
<a name="Windows_Installer"></a>   
### <a name="windows-installer"></a>Windows インストーラー  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] を使用すると、アプリケーションを自己完結型の実行可能ファイルとしてパッケージ化でき、容易にクライアントに配布して、実行できます。 さらに、[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] は [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] と共にインストールされるため、デスクトップ、[スタート] メニュー、および [プログラム] コントロール パネルとの統合が可能です。  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] は、アプリケーションのインストールとアンインストールを単純化しますが、インストールされたアプリケーションをバージョン管理の観点から最新に保つ機能を提供しません。  
  
 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] の詳細については、「[Windows インストーラー配置](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)」を参照してください。  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce 配置  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] を使用すると、非 Web アプリケーションを Web スタイル アプリケーションと同じように配置できます。 アプリケーションは、Web サーバーまたはファイル サーバーに公開され、これらのサーバーから配置されます。 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] は、[!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] によってインストールされるアプリケーションがサポートするような広い範囲のクライアント機能をサポートするわけではありませんが、次のような機能をサポートします。  
  
-   [スタート] メニューおよび [プログラム] コントロール パネルとの統合。  
  
-   バージョン管理、ロールバック、およびアンインストール。  
  
-   アプリケーションを常に配置場所から起動するオンライン インストール モード。  
  
-   新しいバージョンがリリースされたときの自動更新。  
  
-   ファイル拡張子の登録。  
  
 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] の詳細については、「[ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください。  
  
<a name="Deploying_WPF_Applications"></a>   
## <a name="deploying-wpf-applications"></a>WPF アプリケーションの配置  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションの配置オプションは、アプリケーションの種類によって決まります。 配置の観点から見ると、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には次の 3 種類のアプリケーションがあります。  
  
-   スタンドアロン アプリケーション。  
  
-   マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] アプリケーション。  
  
-   [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]。  
  
<a name="Deploying_Standalone_Applications"></a>   
### <a name="deploying-standalone-applications"></a>スタンドアロン アプリケーションの配置  
 スタンドアロン アプリケーションは、[!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] または [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] を使用して配置されます。 いずれの場合も、スタンドアロン アプリケーションを実行するには、アプリケーションが完全に信頼されている必要があります。 [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] を使用して配置されたスタンドアロン アプリケーションには、完全な信頼が自動的に付与されます。 [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] を使用して配置されたスタンドアロン アプリケーションには、完全な信頼は自動的に付与されません。 代わりに、スタンドアロン アプリケーションをインストールする前に、[!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] は [セキュリティ警告] ダイアログを表示し、ユーザーがそれを受け入れる必要があります。 受け入れた場合、スタンドアロン アプリケーションがインストールされ、完全な信頼が付与されます。 受け入れなかった場合、スタンドアロン アプリケーションはインストールされません。  
  
<a name="Deploying_Markup_Only_XAML_Applications"></a>   
### <a name="deploying-markup-only-xaml-applications"></a>マークアップのみの XAML アプリケーションの配置  
 マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは、通常、[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] ページと同様に Web サーバーに公開され、[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] を使用して表示できます。 マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは、部分信頼セキュリティ サンドボックス内で実行され、インターネット ゾーン アクセス許可セットによって定義された制約が適用されます。 これにより、[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] ベースの Web アプリケーションと同等のセキュリティ サンドボックスが提供されます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションのセキュリティの詳細については、「[セキュリティ](../../../../docs/framework/wpf/security-wpf.md)」を参照してください。  
  
 マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページは、XCopy または [!INCLUDE[TLA2#tla_wininstall](../../../../includes/tla2sharptla-wininstall-md.md)] を使用してローカル ファイル システムにインストールできます。 これらのページは、[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] または [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] エクスプ ローラーを使用して表示できます。  
  
 XAML の詳細については、「[XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)」を参照してください。  
  
<a name="Deploying_XAML_Browser_Applications"></a>   
### <a name="deploying-xaml-browser-applications"></a>XAML ブラウザー アプリケーションの配置  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、次の 3 つのファイルを配置する必要があるコンパイル済みのアプリケーションです。  
  
-   *ApplicationName*.exe: 実行可能アセンブリのアプリケーション ファイル。  
  
-   *ApplicationName*.xbap: 配置マニフェスト。  
  
-   *ApplicationName*.exe.manifest: アプリケーション マニフェスト。  
  
> [!NOTE]
>  配置マニフェストおよびアプリケーション マニフェストの詳細については、「[WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)」を参照してください。  
  
 これらのファイルは、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] がビルドされるときに生成されます。 詳細については、「[方法: 新しい WPF ブラウザー アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/72ef4d90-e163-42a1-8df0-ea7ccfd1901f)」を参照してください。 マークアップのみの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページと同様に、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、通常、Web サーバーに更改され、[!INCLUDE[TLA2#tla_iegeneric](../../../../includes/tla2sharptla-iegeneric-md.md)] を使用して表示されます。  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、任意の配置技術を使用してクライアントに配置できます。 ただし、次の機能を備えている [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] をお勧めします。  
  
1.  新しいバージョンが公開されたときの自動更新。  
  
2.  完全な信頼で実行する [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] の特権の昇格。  
  
 既定では、ClickOnce は、.deploy 拡張子を持つアプリケーション ファイルを公開します。 これは問題になる可能性がありますが、無効にできます。 詳細については、「[ClickOnce 配置でのサーバーおよびクライアント構成の問題](/visualstudio/deployment/server-and-client-configuration-issues-in-clickonce-deployments)」を参照してください。  
  
 [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] の配置の詳細については、「[WPF XAML ブラウザー アプリケーションの概要](../../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)」を参照してください。  
  
<a name="Installing__NET_Framework_3_0"></a>   
## <a name="installing-the-net-framework"></a>.NET Framework のインストール  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションを実行するには、クライアントに [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] がインストールされている必要があります。 [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] は、ブラウザーでホストされる [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションが表示されるとき、クライアントに [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がインストールされているかどうかを自動的に検出します。 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がインストールされていない場合、[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] はユーザーにインストールを求めます。  
  
 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がインストールされているかどうかを検出するために、[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] には、.xaml、.xps、および .application の拡張子を持つコンテンツ ファイルのフォールバック [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] ハンドラーとして登録されているブートストラップ アプリケーションが含まれています。 これらのファイルの種類に移動するとき、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] がクライアントにインストールされていなかった場合、ブートス トラップ アプリケーションはインストールの許可を求めます。 許可が与えられなかった場合、[!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] もアプリケーションもインストールされません。  
  
 許可が与えられた場合、[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] は [!INCLUDE[TLA#tla_bits](../../../../includes/tlasharptla-bits-md.md)] を使用して [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] をダウンロードし、インストールします。 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] が正常にインストールされた後、最初に要求されたファイルが新しいブラウザー ウィンドウで開きます。  
  
 [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] の自動検出は、[!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)] 以降がインストールされている [!INCLUDE[TLA#tla_longhorn](../../../../includes/tlasharptla-longhorn-md.md)]、[!INCLUDE[TLA#tla_winxpsp2](../../../../includes/tlasharptla-winxpsp2-md.md)]、および [!INCLUDE[TLA#tla_winnetsvrfamsp1](../../../../includes/tlasharptla-winnetsvrfamsp1-md.md)] クライアントで利用できます。  
  
 詳細については、「[.NET Framework およびアプリケーションの配置](../../../../docs/framework/deployment/index.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [WPF アプリケーションのビルド](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [セキュリティ](../../../../docs/framework/wpf/security-wpf.md)
