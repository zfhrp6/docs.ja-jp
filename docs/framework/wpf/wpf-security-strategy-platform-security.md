---
title: "WPF のセキュリティ方針 - プラットフォーム セキュリティ | Microsoft Docs"
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
  - "CLR のセキュリティ機能"
  - "共通言語ランタイム (CLR) のセキュリティ機能"
  - "Internet Explorer のセキュリティ機能"
  - "オペレーティング システムのセキュリティ モデル"
  - "プラットフォームのセキュリティ モデル"
  - "セキュリティ モデル"
  - "セキュリティ モデル, オペレーティング システム"
  - "セキュリティ モデル, platform"
  - "セキュリティ クリティカルな方法"
  - "Windows Presentation Foundation, セキュリティ モデルの概要"
  - "WPF, セキュリティ モデルの概要"
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# WPF のセキュリティ方針 - プラットフォーム セキュリティ
[!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] は、さまざまなセキュリティ サービスを提供する一方で、基になるプラットフォーム \(オペレーティング システム、[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)]、[!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] など\) のセキュリティ機能も活用します。  これらの層を組み合わせることで、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] に強力な多重防御のセキュリティ モデルが提供されます。このセキュリティ モデルでは、次の図に示すように、単一障害点の回避を試みます。  
  
 ![WPF セキュリティの図](../../../docs/framework/wpf/media/windowplatformsecurity.PNG "windowplatformsecurity")  
  
 このトピックの残りの部分では、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] に関連するこれらの各層の機能について具体的に説明します。  
  
   
  
<a name="Operating_System_Security"></a>   
## オペレーティング システムのセキュリティ  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] が必要とするオペレーティング システムの最小レベルは [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] です。  [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] の中核には、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] で構築されたセキュリティ機能など、すべての [!INCLUDE[TLA2#tla_win](../../../includes/tla2sharptla-win-md.md)] アプリケーションのセキュリティ基盤を形成する複数のセキュリティ機能があります。  [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] には、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] のセキュリティ機能が搭載され、それをさらに拡張しています。  このトピックでは、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] にとって重要なセキュリティ機能の一式、および [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] がそれらを統合してさらに多重防御を行う方法について説明します。  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### Microsoft Windows XP Service Pack 2 \(SP2\)  
 [!INCLUDE[TLA2#tla_win](../../../includes/tla2sharptla-win-md.md)] の総括と強化に加えて、このトピックでは、[!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] にある次の 3 つの主要機能についても説明します。  
  
-   \/GS のコンパイル  
  
-   [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### \/GS のコンパイル  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] は、バッファー オーバーランを軽減するために、[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] など、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] の依存関係のすべてを含む多数のコア システム ライブラリを再コンパイルして、保護を行います。  これは、C や C\+\+ のコマンド ライン コンパイラの \/GS パラメーターを使用して実現されます。  バッファー オーバーランを明示的に避ける必要はありますが、\/GS コンパイルは、故意であるかないかにかかわらずバッファー オーバーランによって生み出される潜在的な脆弱性に対する多重防御の一例となります。  
  
 従来、バッファー オーバーランは、影響が大きいセキュリティ攻撃の多くの原因となっていました。  バッファー オーバーランは、バッファーの境界を超えて書き込む、悪意のあるコードの挿入を許すコードの脆弱性を攻撃者が利用するときに発生します。  これにより、攻撃者はプロセスを乗っ取ることができます。この場合、コードは、攻撃者のコードを実行するように関数のリターン アドレスを上書きすることで実行されます。  結果として、乗っ取ったプロセスと同じ特権を持つ任意のコードを実行する悪意のあるコードが生成されます。  
  
 概略でとらえると、\/GS コンパイラ フラグは、ローカル文字列のバッファーを持つ関数のリターン アドレスを保護する特殊なセキュリティ クッキーを挿入して、潜在的なバッファー オーバーランから保護します。  関数が返されると、セキュリティ クッキーはその前の値と比較されます。  値が変更されている場合、バッファー オーバーランが発生した可能性があるとして、プロセスはエラー状態によって停止されます。  プロセスの停止により、悪意のある可能性があるコードの実行を防止できます。  詳細については、「[\/GS \(バッファーのセキュリティ チェック\)](http://msdn.microsoft.com/library/8dbf701c.aspx)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、\/GS フラグでコンパイルされて、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションに別の防御層を追加します。  
  
#### Microsoft Windows 更新プログラムの拡張機能  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] では、[!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] も改善され、更新プログラムのダウンロードとインストールのプロセスが簡略化されました。  これらの変更により、特にセキュリティ更新プログラムに関して、システムを確実に最新の状態にすることで、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] のお客様のセキュリティ保護が大きく拡大しました。  
  
<a name="Windows_Vista"></a>   
### Windows Vista  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] の [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ユーザーは、「最小限の特権によるユーザー アクセス」、コードの整合性チェック、および特権の分離など、オペレーティング システムのさらなるセキュリティ機能強化の恩恵を受けられます。  
  
#### ユーザー アカウント制御 \[UAC\]  
 現在のところ、[!INCLUDE[TLA2#tla_win](../../../includes/tla2sharptla-win-md.md)] ユーザーは、管理者特権で実行する傾向があります。多くのアプリケーションで、インストールや実行、またはその両方に管理者特権が必要となるためです。  既定のアプリケーションの設定をレジストリに書き込めることが、その一例です。  
  
 管理者特権で実行することの本当の意味は、管理者特権を付与されているプロセスからアプリケーションを実行することです。  これによるセキュリティへの影響は、管理者特権で実行するプロセスを乗っ取る悪意のあるコードが、重要なシステム リソースへのアクセスなど、これらの権限を自動的に継承することです。  
  
 このセキュリティの脅威から保護するための 1 つの方法は、必要最小限の特権でアプリケーションを実行することです。  これは、最小特権の原則として知られ、[!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] オペレーティング システムの主要機能となっています。  この機能をユーザー アカウント制御 \(UAC\) といい、[!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] UAC によって主に次の 2 つの方法で使用されます。  
  
-   ユーザーが管理者であっても、既定で UAC 特権を持つほとんどのアプリケーションを実行するために、管理者特権を必要とするアプリケーションのみが管理者特権で実行されます。  管理者特権で実行するためには、アプリケーションは、アプリケーション マニフェストで、またはセキュリティ ポリシーのエントリとして明示的にマークされる必要があります。  
  
-   仮想化のような互換性に関する解決策を提供します。  たとえば、多くのアプリケーションが C:\\Program Files のような制限された場所への書き込みを試みるなどです。  UAC の下で実行するアプリケーションでは、書き込みに管理者特権が必要でない、ユーザーごとの代替の場所が存在します。  UAC の下で実行するアプリケーションでは、UAC は C:\\Program Files を仮想化して、書き込もうとしているアプリケーションが、実際はユーザーごとの代替の場所に書き込むようにします。  このような互換性の作業により、オペレーティング システムは、以前は UAC で実行できなかった多くのアプリケーションを実行できるようになります。  
  
#### コードの整合性チェック  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] には、読み込み時または実行時に、悪意のあるコードがシステム ファイルやカーネルに挿入されないようにするための、より詳細なコード整合性チェックが組み込まれています。  これは、システム ファイルの保護を超えて動作します。  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### ブラウザーでホストされるアプリケーションの制限付き権限のプロセス  
 ブラウザーでホストされる [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションは、インターネット ゾーンのサンド ボックス内で実行します。  [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] と [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] を統合すると、この保護が追加のサポートで拡張されます。  
  
#### Internet Explorer 6 Service Pack 2 および XP 用の Internet Explorer 7  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、オペレーティング システムのセキュリティを利用して、[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] のプロセスの特権を制限してさらに保護します。  ブラウザーでホストされる [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションを起動する前に、オペレーティング システムは、プロセス トークンから不要な特権を取り除くホスト プロセスを作成します。  取り除かれる特権のいくつかの例として、ユーザーのコンピューターのシャット ダウン機能、ドライバーの読み込み、およびコンピューター上の全ファイルに対する読み取りアクセスがあります。  
  
#### Vista 用 Internet Explorer 7  
 [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)] では、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションは保護モードで実行します。  具体的には、[!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] は中レベルの整合性で実行します。  
  
#### 多重防御層  
 [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] は一般に、インターネット ゾーン アクセス許可セットによってセキュリティで保護されるため、互換性の観点から、これらの特権を取り除いても、[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] には害を及ぼしません。  代わりに、追加の多重防御層が作成されます。セキュリティで保護されたアプリケーションが他のレイヤーを利用してプロセスを乗っ取ることができる場合、プロセスの特権は制限されたままとなります。  
  
 「[最小特権のユーザー アカウントを使用する](http://technet.microsoft.com/library/cc700846.aspx)」を参照してください。  
  
<a name="Common_Language_Runtime_Security"></a>   
## 共通言語ランタイムのセキュリティ  
 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] は、確認と検証、[!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]、およびセキュリティ クリティカルな方法などの、多数のセキュリティ上の重要なメリットをもたらします。  
  
<a name="Validation_and_Verification"></a>   
### 確認と検証  
 アセンブリの分離と整合性を提供するため、[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] は検証のプロセスを使用します。  [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] の検証では、アセンブリの外部にポイントするアドレスのポータブル実行可能ファイル \(PE\) ファイル形式を検証して、アセンブリが分離されていることを確認します。  また、[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] 検証では、アセンブリ内に埋め込まれているメタデータの整合性を検証します。  
  
 タイプ セーフを保証するため、一般的なセキュリティ上の問題 \(例:   バッファー オーバーラン\) を予防します。さらに、サブプロセスの分離を通じてサンドボックスを可能にします。[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] のセキュリティでは、確認の概念を使用します。  
  
 マネージ アプリケーションは、Microsoft Intermediate Language \(MSIL\) にコンパイルされます。  マネージ アプリケーション内のメソッドを実行する際、その MSIL は Just\-In\-Time \(JIT\) コンパイルを通じてネイティブ コードにコンパイルされます。  JIT コンパイルには、コードが以下を行わないようにする多数の安全性と堅牢性ルールを適用する検証プロセスがあります。  
  
-   型のコントラクトの違反  
  
-   バッファー オーバーランの導入  
  
-   乱暴なメモリへのアクセス  
  
 マネージ コードが信頼されたコードと見なされない限り、検証ルールに適合しないマネージ コードの実行は許可されません。  
  
 検証可能なコードの利点は、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] が [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] 上に構築される主な理由になります。  検証可能なコードを使用する範囲で、起こりうる脆弱性の悪用の可能性が大幅に減少します。  
  
<a name="Code_Access_Security"></a>   
### コード アクセス セキュリティ  
 クライアント コンピューターは、ファイル システム、レジストリ、印刷サービス、ユーザー インターフェイス、リフレクション、および環境変数など、マネージ アプリケーションがアクセスできる多種多様なリソースを公開します。  マネージ アプリケーションは、クライアント コンピューター上のリソースのいずれかにアクセスするまでに、それを実行するための [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] のアクセス許可を得る必要があります。  [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] のアクセス許可は、<xref:System.Security.CodeAccessPermission> のサブクラスです。[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] は、マネージ アプリケーションがアクセスできるリソースごとに 1 つのサブクラスを実装します。  
  
 マネージ アプリケーションが実行を開始する際に [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] によって付与される一連のアクセス許可は、アクセス許可セットとして知られ、アプリケーションが提供する証拠によって決定されます。  [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションでは、提供される証拠は、アプリケーションが起動される場所またはゾーンです。  [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] は次のゾーンを識別します。  
  
-   **マイ コンピューター**。  クライアント コンピューターから起動するアプリケーション \(完全信頼\)。  
  
-   **ローカル イントラネット**。  イントラネットから起動するアプリケーション。  \(部分信頼\)。  
  
-   **インターネット** インターネットから起動するアプリケーション。  \(最小信頼\)。  
  
-   **信頼済みサイト**。  ユーザーから信頼すると特定されたアプリケーション。  \(最小信頼\)。  
  
-   **信頼されていないサイト** ユーザーから信頼しないと特定されたアプリケーション。  \(非信頼\)。  
  
 これらのゾーンごとに、[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] は、それぞれが関連付けられている信頼レベルと一致するアクセス許可を含む定義済みの権限セットを提供します。  以下に例を示します。  
  
-   **FullTrust**。  **マイ コンピューター** ゾーンから起動するアプリケーション向け。  可能性のあるすべてのアクセス許可が付与されます。  
  
-   **LocalIntranet**。  **ローカル イントラネット** ゾーンから起動するアプリケーション向け。  分離ストレージ、UI の無制限のアクセス、制約のないファイル ダイアログ、制限付きのリフレクション、環境変数へのアクセス制限など、クライアント コンピューターのリソースへの中程度のアクセスを提供するアクセス許可のサブセットが付与されます。  レジストリのような重要なリソースに対するアクセス許可は提供されません。  
  
-   **インターネット** **インターネット**または**信頼済みサイト** ゾーンから起動するアプリケーション向け。  分離ストレージ、ファイルを開くのみ、および制限付きの UI など、クライアント コンピューターに制限付きのアクセス権を付与するため、アクセス許可のサブセットを付与します。  基本的に、このアクセス許可セットでは、アプリケーションはクライアント コンピューターから分離されます。  
  
 **信頼されていないサイト** ゾーンのアプリケーションと識別されたアプリケーションは、[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] からアクセス許可を付与されません。  その結果、定義済みのアクセス許可セットは存在しません。  
  
 次の図は、ゾーン、アクセス許可セット、アクセス許可、およびリソース間の関係を示しています。  
  
 ![CAS アクセス許可セット](../../../docs/framework/wpf/media/caspermissionsets.png "CASPermissionSets")  
  
 インターネット ゾーンのセキュリティ サンドボックスの制約は、[!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] が [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] を含むシステム ライブラリからインポートする任意のコードに等しく適用されます。  これにより、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] であっても、コードはビットごとにロック ダウンされます。  残念ながら、実行できるようにするためには、[!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] は、インターネット ゾーンのセキュリティ サンドボックスで有効化されたアクセス許可より多くのアクセス許可を必要とする機能を実行する必要があります。  
  
 次のページを含む [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] アプリケーションを検討してください。  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 この [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] を実行するために、基になる [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] コードは、呼び出し元の [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] で使用できるより多くの機能を実行する必要があります。それらは次のとおりです。  
  
-   表示するためのウィンドウ ハンドル \(hWnd\) の作成  
  
-   メッセージのディスパッチ  
  
-   Tahoma フォントの読み込み  
  
 セキュリティの観点から、セキュリティで保護されたアプリケーションからこれらの操作のいずれかに直接アクセスを許可すると、致命的な状態になります。  
  
 幸い、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、セキュリティで保護されたアプリケーションの代わりに、これらの操作が昇格した特権で実行できるようにすることで、この状況に対応します。  すべての [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] の操作に対して [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] のアプリケーション ドメインにおける制限付きのインターネット ゾーンのセキュリティのアクセス許可がチェックされます。[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] には、\(その他のシステム ライブラリと同様に、\) 可能性があるすべてのアクセス許可を含むアクセス許可が付与されます。  
  
 そのためには、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] が昇格した特権を受け取る一方、それらの特権がホスト アプリケーション ドメインのインターネット ゾーンのアクセス許可セットによって制御されないようにする必要があります。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、アクセス許可の **Assert** メソッドを使用してこれを実行します。  次のコードは、その方法を示しています。  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 基本的に、**Assert** は、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] が必要とする無制限のアクセス許可が、[!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] のインターネット ゾーンのアクセス許可によって制限されないようにします。  
  
 プラットフォームの観点から、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は **Assert** を適切に使用する役割を担います。**Assert** を正しく使用しないと、悪意のあるコードが特権を昇格してしまう恐れがあります。  したがって、**Assert** は必要なときにのみ呼び出し、サンドボックスによる制約は変更しないようにすることが重要です。  たとえば、セキュリティで保護されたコードでは、ランダムなファイルを開くことはできませんが、フォントは使用できます。  [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] は、セキュリティで保護されたアプリケーションが **Assert** を呼び出してフォントの機能を使えるようにするとともに、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] がセキュリティで保護されたアプリケーションの代わりにそれらのフォントが含まれていることが分かっているファイルを読み取れるようにします。  
  
<a name="ClickOnce_Deployment"></a>   
### ClickOnce の配置  
 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] は、[!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] に付属する包括的な配置テクノロジで、[!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] と統合されています \(詳細については、「[ClickOnce の配置の概要](http://msdn.microsoft.com/library/142dbbz4.aspx)」を参照してください\)。  スタンドアロンの [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションは、[!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] を使用して配置できます。一方、ブラウザーでホストされるアプリケーションは [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] で配置する必要があります。  
  
 [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] を使用して配置されたアプリケーションには、[!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] の上に追加のセキュリティ層が設けられます。基本的に、[!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] の配置済みのアプリケーションは、必要なアクセス許可を要求します。  これらのアプリケーションが、アプリケーションの配置元ゾーンのアクセス許可セット数を超えていない場合、これらのアプリケーションには必要なアクセス許可のみが付与されます。  アクセス許可セット数を必要な数のみに減らすことで、起動ゾーンのアクセス許可セットが提供するアクセス許可数を下回る場合でも、アプリケーションがアクセスできるリソースの数が最小限まで削減されます。  その結果、アプリケーションが乗っ取られた場合、クライアント コンピューターの損傷の可能性が低減します。  
  
<a name="Security_Critical_Methodology"></a>   
### セキュリティ クリティカルな方法  
 [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] アプリケーションでインターネット ゾーンのサンド ボックスを有効にするアクセス許可を使用する [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] コードは、セキュリティ監査および制御の程度を可能な限り高く保持する必要があります。  この要件に対応するため、[!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] は、特権を昇格するコードを管理するための新しいサポートを提供します。  具体的には、[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] は、特権を昇格させるコードを識別して <xref:System.Security.SecurityCriticalAttribute> でマークできるようにします。<xref:System.Security.SecurityCriticalAttribute> でマークされていないコードは、この方法を使用して*透過的*になります。  逆に、<xref:System.Security.SecurityCriticalAttribute> でマークされていないマネージ コードは特権の昇格ができなくなります。  
  
 セキュリティ クリティカルな方法では、*セキュリティ クリティカルなカーネル*に特権が昇格する [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] コードの組織が、残りの部分を透過的にすることを許可します。  セキュリティ クリティカルなコードを分離することにより、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] のエンジニアリング チームは、標準的なセキュリティ プラクティスを超えた追加のセキュリティ分析とソース コントロールに重点を置くことができます \([WPF のセキュリティ方針 \- セキュリティ エンジニアリング](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)を参照してください\)。  
  
 なお [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] は、開発者が <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) でマークされ、ユーザーのグローバル アセンブリ キャッシュ \(GAC\) に配置されたマネージ アセンブリに書き込めるようにすることで、信頼されたコードが [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] のインターネット ゾーンのサンドボックスに拡張することを許可します。  アセンブリを APTCA でマークすることは、機密性の高いセキュリティ操作です。インターネットからの悪意のあるコードなど、いずれのコードもそのアセンブリを呼び出すことができるためです。  これを実施する際は十分注意し、ベスト プラクティスを使用する必要があります。ソフトウェアをインストールするためには、ユーザーがそのソフトウェアを信頼することを選択する必要があります。  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## Microsoft Internet Explorer のセキュリティ  
 セキュリティ上の問題を減らし、セキュリティの構成を簡素化するだけでなく、[!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] には、[!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] のユーザーのセキュリティを強化するようセキュリティが向上した複数の機能が含まれています。  これらの機能の推進により、ユーザーが閲覧の制御を拡大できるようにしています。  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] の前のバージョンでは、ユーザーは次のいずれかの影響を受ける可能性がありました。  
  
-   ランダムなポップアップ ウィンドウ。  
  
-   スクリプトのリダイレクトの混乱。  
  
-   一部の Web サイトでの多数のセキュリティ ダイアログ。  
  
 場合によっては、信頼できない Web サイトで [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] のインストールのなりすましをしたり、ユーザーがキャンセルしていても [!INCLUDE[TLA#tla_actx](../../../includes/tlasharptla-actx-md.md)] のインストールのダイアログ ボックスを繰り返し表示したりしてユーザーを騙そうとします。  これらの方法によって、大多数のユーザーが騙されて不適切な判断を行い、スパイウェア アプリケーションのインストールにつながる可能性があります。  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] には、ユーザーによる開始の概念にまつわるこのような問題を軽減するいくつかの機能があります。  [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] は、アクションの前にユーザーがリンクやページ要素をクリックしたとき \(*ユーザーによる開始*として知られる\) に検出し、同様のアクションがページのスクリプトによってトリガーされる場合とは異なる処理をします。  たとえば、[!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] には、ページのポップアップを作成する前にユーザーがボタンをクリックすると検出する**ポップアップ ブロック**が組み込まれています。  これにより、[!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] は何の問題もないポップアップを許可する一方、ユーザーが要求も希望もしていないポップアップを防ぎます。  ブロックされたポップアップは、新しい**情報バー**にトラップされます。情報バーを使用すると、ユーザーは手動でブロックをオーバーライドし、ポップアップ ウィンドウを表示できます。  
  
 同じユーザーによる開始のロジックが、**\[開く\]**\/**\[保存\]** のセキュリティに関するメッセージにも適用されています。  [!INCLUDE[TLA2#tla_actx](../../../includes/tla2sharptla-actx-md.md)] のインストールのダイアログ ボックスは、以前インストールされたコントロールからのアップグレードを表す場合を除いて、情報バーにトラップされます。  これらの対策を組み合わせると、より安全かつ制御されたユーザー エクスペリエンスがユーザーに提供されます。ユーザーを攻撃して不要または悪意のあるソフトウェアをインストールさせるサイトからユーザーが保護されるためです。  
  
 これらの機能は、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションのダウンロードとインストールを行えるようにする Web サイトを閲覧するために [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] を使用するお客様も保護します。  特に [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] では、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] を含め、構築にどのテクノロジを使用したかに関係なく、悪意のあるまたは不正なアプリケーションをユーザーがインストールする機会を減らす上でユーザーエクスペリエンスの向上を提供しているからです。  [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] では、[!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] を使用してこのような保護を追加することで、インターネット経由でアプリケーションをダウンロードしやすくします。  [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] はインターネット ゾーンのセキュリティ サンドボックス内で実行するので、シームレスに起動することができます。  一方、スタンドアロンの [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] アプリケーションでは、実行するには完全な信頼が必要になります。  これらのアプリケーションでは、起動プロセス中に [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] はセキュリティに関するダイアログ ボックスを表示して、アプリケーションの追加のセキュリティ要件を使用するよう通知します。  ただし、これはユーザーが開始する必要があり、ユーザーが開始したロジックによって制御されるとともに、キャンセルが可能です。  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)] は、継続的なセキュリティへの取り組みの一環として、[!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] のセキュリティ機能を強化しています。  
  
## 参照  
 [Windows XP SP2 での Microsoft Internet explorer 6 のセキュリティについて](http://www.microsoft.com/downloads/details.aspx?FamilyId=E550F940-37A0-4541-B5E2-704AB386C3ED&displaylang=jp)   
 [保護モードの Internet Explorer の理解と機能](http://msdn.microsoft.com/library/bb250462.aspx)   
 [Windows XP Service Pack 3](http://www.microsoft.com/windows/products/windowsxp/sp3/default.mspx)   
 [Windows Vista セキュリティ ガイド](http://www.microsoft.com/downloads/details.aspx?familyid=a3d1bbed-7f35-4e72-bfb5-b84a526c1565&displaylang=jp)   
 [コード アクセス セキュリティ](../../../docs/framework/misc/code-access-security.md)   
 [セキュリティ](../../../docs/framework/wpf/security-wpf.md)   
 [WPF 部分信頼セキュリティ](../../../docs/framework/wpf/wpf-partial-trust-security.md)   
 [WPF のセキュリティ方針 \- セキュリティ エンジニアリング](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)