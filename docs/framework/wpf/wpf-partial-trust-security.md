---
title: WPF 部分信頼セキュリティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- partial trust security [WPF]
- detecting permissions [WPF]
- security settings for Internet Explorer [WPF]
- partial trust applications [WPF], debugging
- permissions [WPF], managing
- debugging partial trust applications [WPF]
- permissions [WPF], detecting
- feature security requirements [WPF]
- managing permissions [WPF]
ms.assetid: ef2c0810-1dbf-4511-babd-1fab95b523b5
ms.openlocfilehash: 27934f782d6c1efde69794c73d653b57b287341f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566471"
---
# <a name="wpf-partial-trust-security"></a>WPF 部分信頼セキュリティ
<a name="introduction"></a> 一般に、悪意のある破損を防ぐための重要なシステム リソースに直接アクセスする必要がなくなりますインターネット アプリケーションを制限する必要があります。 既定では、[!INCLUDE[TLA#tla_html](../../../includes/tlasharptla-html-md.md)]クライアント側のスクリプト言語は、重要なシステム リソースにアクセスすることができません。 ブラウザーによってホストされるアプリケーションの Windows Presentation Foundation (WPF) は、ブラウザーから起動できる、ためには、同様の制限のセットに準拠している必要があります。 これらの制限が適用[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]両方に依存している[!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]と[!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)](を参照してください[WPF のセキュリティ方針 - プラットフォーム セキュリティ](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md))。 既定では、ブラウザ ホスト アプリケーションでは、インターネット ゾーンを要求[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]インターネット、ローカル イントラネット、またはローカル コンピューターから起動するかどうかに関係なく、権限のセット。 未満のアクセス許可の完全なセットを使用して実行するアプリケーションは、部分信頼で実行されていると見なされます。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] さまざまなサポートを実施し、できるだけ多くの機能を使用できることに安全に部分信頼でおよびと共に提供[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]、部分信頼のプログラミングの他のサポートを提供します。  
  
 このトピックは、次のセクションで構成されています。  
  
-   [部分信頼サポートされている WPF 機能](#WPF_Feature_Partial_Trust_Support)  
  
-   [部分信頼のプログラミング](#Partial_Trust_Programming)  
  
-   [アクセス許可の管理](#Managing_Permissions)  
  
<a name="WPF_Feature_Partial_Trust_Support"></a>   
## <a name="wpf-feature-partial-trust-support"></a>部分信頼サポートされている WPF 機能  
 次の表では、安全に、インターネット ゾーン アクセス許可セットの範囲内で使用される高度な機能 Windows Presentation Foundation (WPF) の一覧表示します。  
  
 部分信頼で安全な表 1: WPF 機能  
  
|機能分野|機能|  
|------------------|-------------|  
|全般|ブラウザーのウィンドウ<br /><br /> 配信元のアクセスのサイト<br /><br /> IsolatedStorage (512 KB 制限)<br /><br /> UIAutomation プロバイダー<br /><br /> コマンド実行<br /><br /> 入力方式エディター (IME)<br /><br /> タブレット スタイラスとインク<br /><br /> マウスのキャプチャと移動イベントを使用してシミュレートされたドラッグ アンド ドロップ<br /><br /> OpenFileDialog<br /><br /> (XamlReader.Load) 経由で XAML シリアル化解除|  
|Web の統合|ブラウザーのダウンロード ダイアログ ボックス<br /><br /> 最上位のユーザーによるナビゲーション<br /><br /> mailto:links<br /><br /> Uniform Resource Identifier パラメーター<br /><br /> HTTPWebRequest<br /><br /> IFRAME にホストされている WPF コンテンツ<br /><br /> フレームを使用して、同じサイトの HTML ページのホスト<br /><br /> Web ブラウザーを使用して、同じサイトの HTML ページのホスティング<br /><br /> Web サービス (ASMX)<br /><br /> (Windows Communication Foundation を使用して) web サービス<br /><br /> [スクリプティング]<br /><br /> ドキュメント オブジェクト モデル|  
|ビジュアル|2D および 3D<br /><br /> アニメーション<br /><br /> メディア (発信元とクロス ドメインのサイト)<br /><br /> イメージング/オーディオ/ビデオ|  
|読み取り|FlowDocument<br /><br /> XPS ドキュメント<br /><br /> 埋め込み (& a) のシステム フォント<br /><br /> CFF & TrueType フォント|  
|編集|スペル チェック<br /><br /> RichTextBox<br /><br /> プレーン テキストとインク クリップボードのサポート<br /><br /> ユーザーが開始した貼り付け<br /><br /> 選択したコンテンツのコピー|  
|コントロール|[全般] のコントロール|  
  
 この表は、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]高レベルで機能します。 詳細について、[!INCLUDE[TLA#tla_lhsdk](../../../includes/tlasharptla-lhsdk-md.md)]ドキュメント内の各メンバーによって必要なアクセス許可[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]です。 さらに、次の機能には、特別な考慮事項をなど、部分的な信頼の実行に関する情報がより詳細なです。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] (を参照してください[XAML の概要 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md))。  
  
-   ポップアップ (表示<xref:System.Windows.Controls.Primitives.Popup?displayProperty=nameWithType>)。  
  
-   ドラッグ アンド ドロップ (を参照してください[ドラッグ アンド ドロップの概要](../../../docs/framework/wpf/advanced/drag-and-drop-overview.md))。  
  
-   クリップボード (を参照してください<xref:System.Windows.Clipboard?displayProperty=nameWithType>)。  
  
-   イメージング (を参照してください<xref:System.Windows.Controls.Image?displayProperty=nameWithType>)。  
  
-   シリアル化 (を参照してください<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>、 <xref:System.Windows.Markup.XamlWriter.Save%2A?displayProperty=nameWithType>)。  
  
-   ファイル ダイアログ ボックスが開き (を参照してください<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>)。  
  
 次の表にアウトライン、[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]インターネットの制限内で実行しても安全ではない機能ゾーン アクセス許可セット。  
  
 部分信頼で安全でない表 2: WPF 機能  
  
|機能分野|機能|  
|------------------|-------------|  
|全般|ウィンドウ (定義済みのアプリケーション ウィンドウとダイアログ ボックス)<br /><br /> SaveFileDialog<br /><br /> ファイル システム<br /><br /> レジストリへのアクセス<br /><br /> ドラッグ アンド ドロップ<br /><br /> (XamlWriter.Save) 経由で XAML シリアル化<br /><br /> UIAutomation クライアント<br /><br /> ソース ウィンドウへのアクセス (HwndHost)<br /><br /> 完全な音声サポート<br /><br /> Windows フォームの相互運用性|  
|ビジュアル|ビットマップ効果<br /><br /> イメージのエンコード|  
|編集|リッチ テキスト形式のクリップボード<br /><br /> 完全な XAML サポート|  
  
<a name="Partial_Trust_Programming"></a>   
## <a name="partial-trust-programming"></a>部分信頼のプログラミング  
 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]アプリケーション、コードを既定の権限セットを超えることになります、セキュリティ ゾーンに応じて動作が異なります。 ユーザーがアプリケーションをインストールしようとすると警告が表示されることもあります。 ユーザーは、インストールを続行するか取り消すかを選択できます。 次の表は、各セキュリティ ゾーンのアプリケーション動作と、完全な信頼を受け取るアプリケーションで行う必要のある操作を示しています。  
  
|セキュリティ ゾーン|動作|完全信頼を受け取るための操作|  
|-------------------|--------------|------------------------|  
|ローカル コンピューター|完全な信頼を自動的に受け取る|アクションは必要ありません。|  
|イントラネットおよび信頼済みサイト|完全な信頼のプロンプトを表示する|プロンプトにソースが表示されるように、証明書を使用して XBAP に署名します。|  
|インターネット|"信頼されていません" というメッセージが表示され、失敗する|証明書を使用して XBAP に署名します。|  
  
> [!NOTE]
>  上記の表で説明されている動作は、完全な信頼、ClickOnce 信頼されている配置モデルに従っていない Xbap です。  
  
 一般に、許可されたアクセス許可を超える可能性のあるコードは、スタンドアロン アプリケーションとブラウザーによってホストされるアプリケーション間で共有される共通のコードを使用する可能性があります。 [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] および[!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]このシナリオを管理するためのいくつかの手法を提供します。  
  
<a name="Detecting_Permissions_using_CAS"></a>   
### <a name="detecting-permissions-using-cas"></a>CA を使用してアクセス許可の検出  
 一部の状況では、両方のスタンドアロン アプリケーションで使用するライブラリのアセンブリで共有コードと[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]です。 このような場合は、コードは、アプリケーションの付与されているアクセス許可セットよりも高い権限が必要になる機能を実行できます。 アプリケーションには、Microsoft .NET Framework のセキュリティを使用して特定のアクセス許可があるかどうかを検出できます。 具体的には、呼び出すことによって特定のアクセス許可があるかどうかをテストする、<xref:System.Security.CodeAccessPermission.Demand%2A>の必要なアクセス許可のインスタンス。 これがコードでローカル ディスクにファイルを保存する機能があるかどうかをクエリするは、次の例で表示されます。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandling.cs#detectpermscode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandling.vb#detectpermscode2)]  
  
 アプリケーションに、必要なアクセス許可への呼び出しがないかどうかは<xref:System.Security.CodeAccessPermission.Demand%2A>セキュリティ例外がスローされます。 それ以外の場合は、権限が与えられています。 `IsPermissionGranted` この動作をカプセル化し、返します`true`または`false`をクリックします。  
  
<a name="Graceful_Degradation_of_Functionality"></a>   
### <a name="graceful-degradation-of-functionality"></a>機能の正常な低下  
 コードが実行する必要がありますが、権限を持つかどうかを検出できることは、別のゾーンから実行できるコードにとって重要です。 ゾーンは、1 つの検出中にまで可能であれば、ユーザーの代替手段を提供することをお勧めします。 たとえば、完全信頼アプリケーションでは、通常、部分信頼アプリケーション分離ストレージでファイルを作成できるだけ中に、必要な任意の場所のファイルを作成するユーザーができます。 完全な信頼 (スタンドアロン) アプリケーションと部分的に信頼 (ブラウザーによってホストされる) のアプリケーションの両方で共有されているアセンブリに存在するファイルを作成するコード、両方のアプリケーション ユーザーのファイルを作成できるように場合、共有コードがかどうかを検出する必要があります。適切な場所にファイルを作成する前に、部分的または完全な信頼で実行されています。 次のコードでは、両方を示します。  
  
 [!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode1)]
 [!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE1](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode1)]  
[!code-csharp[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/csharp/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/CSharp/FileHandlingGraceful.cs#detectpermsgracefulcode2)]
[!code-vb[PartialTrustSecurityOverviewSnippets#DetectPermsGracefulCODE2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PartialTrustSecurityOverviewSnippets/VisualBasic/FileHandlingGraceful.vb#detectpermsgracefulcode2)]  
  
 多くの場合は、部分信頼の代替を検索することができます。  
  
 クライアントにベース、イントラネットなど、制御された環境でカスタム マネージ フレームワークをインストールすることができます、[!INCLUDE[TLA#tla_gac](../../../includes/tlasharptla-gac-md.md)]です。 これらのライブラリの完全な信頼を必要とするコードを実行できるを使用して部分信頼ではのみをアプリケーションから参照できる<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(詳細については、次を参照してください[セキュリティ](../../../docs/framework/wpf/security-wpf.md)と[WPF セキュリティ。方針 - プラットフォーム セキュリティ](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md))。  
  
<a name="Browser_Host_Detection"></a>   
### <a name="browser-host-detection"></a>ブラウザー ホストの検出  
 使用して[!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)]アクセス許可を確認するには適切な手法をごとのアクセス許可ごとに確認する必要がある場合は。 ただし、この手法に依存例外のキャッチ標準の一部として処理するは一般にお勧めせず、パフォーマンスの問題を持つことができます。 代わりに場合、[!INCLUDE[TLA#tla_xbap](../../../includes/tlasharptla-xbap-md.md)]インターネット ゾーンのサンド ボックス内でのみ実行して、<xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A?displayProperty=nameWithType>に対して true を返すプロパティ[!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]です。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.BrowserInteropHelper.IsBrowserHosted%2A> のみを実行しているアプリケーションのアクセス許可のどの設定されていないブラウザーで、アプリケーションが実行されているかどうかを区別します。  
  
<a name="Managing_Permissions"></a>   
## <a name="managing-permissions"></a>アクセス許可の管理  
 既定では、[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]部分的な信頼 (既定のインターネット ゾーン アクセス許可セット) を実行します。 ただし、アプリケーションの要件に応じて既定の権限のセットを変更することです。 たとえば場合、[!INCLUDE[TLA2#tla_xbap#plural](../../../includes/tla2sharptla-xbapsharpplural-md.md)]を起動、ローカル イントラネットからを利用する、増加したアクセス許可セットは、次の表に示されているのです。  
  
 テーブル 3: ローカル イントラネットとインターネットのアクセス許可  
  
|アクセス許可|属性|ローカル イントラネット|インターネット|  
|----------------|---------------|-------------------|--------------|  
|DNS|DNS サーバーのアクセス|[はい]|×|  
|環境変数|読み取り|[はい]|×|  
|ファイル ダイアログ ボックス|開く|[はい]|[はい]|  
|ファイル ダイアログ ボックス|無制限|[はい]|×|  
|分離ストレージ|ユーザーによるアセンブリの分離|[はい]|×|  
|分離ストレージ|不明な分離|[はい]|[はい]|  
|分離ストレージ|無制限のユーザーのクォータ|[はい]|×|  
|メディア|安全なオーディオ、ビデオ、およびイメージ|[はい]|[はい]|  
|印刷|既定の印刷|[はい]|×|  
|印刷|安全な印刷|[はい]|[はい]|  
|リフレクション|出力|[はい]|×|  
|セキュリティ|マネージ コードの実行|[はい]|[はい]|  
|セキュリティ|付与されたアクセス許可をアサートします。|[はい]|×|  
|ユーザー インターフェイス|無制限|[はい]|×|  
|ユーザー インターフェイス|安全なトップレベル ウィンドウ|[はい]|[はい]|  
|ユーザー インターフェイス|独自のクリップボード|[はい]|[はい]|  
|Web ブラウザー|HTML への安全なフレーム ナビゲーション|[はい]|[はい]|  
  
> [!NOTE]
>  切り取りと貼り付けは、のみ部分的な信頼でユーザーが開始したときにできます。  
  
 アクセス許可を増やす必要がある場合は、プロジェクトの設定と ClickOnce アプリケーション マニフェストを変更する必要があります。 詳細については、「[WPF XAML ブラウザー アプリケーションの概要](../../../docs/framework/wpf/app-development/wpf-xaml-browser-applications-overview.md)」をご覧ください。 次のドキュメントも役立つ場合があります。  
  
-   [Mage.exe (マニフェスト生成および編集ツール)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)です。  
  
-   [MageUI.exe (マニフェスト生成および編集ツールのグラフィカル クライアント)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)です。  
  
-   [ClickOnce アプリケーションのセキュリティ](/visualstudio/deployment/securing-clickonce-applications)です。  
  
 場合、 [!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)] 、完全な信頼を必要と同じツールを使用するを要求されたアクセス許可を増やします。 ただし、[!INCLUDE[TLA2#tla_xbap](../../../includes/tla2sharptla-xbap-md.md)]にインストールされ、ローカル コンピューターから、イントラネット、または記載されているブラウザーの信頼済みまたは許可されたサイト URL からを起動した場合のみ、完全な信頼が受信されます。 イントラネットまたは信頼済みサイトからアプリケーションをインストールすると、ユーザーは、管理者特権でのアクセス許可のことを通知する、標準の ClickOnce プロンプトを受け取ります。 ユーザーは、インストールを続行するか取り消すかを選択できます。  
  
 代わりに、任意のセキュリティ ゾーンから完全な信頼の展開用 ClickOnce 信頼されている配置モデルを使用することができます。 詳細については、次を参照してください。[信頼されたアプリケーションの展開の概要](/visualstudio/deployment/trusted-application-deployment-overview)と[セキュリティ](../../../docs/framework/wpf/security-wpf.md)です。  
  
## <a name="see-also"></a>関連項目  
 [セキュリティ](../../../docs/framework/wpf/security-wpf.md)  
 [WPF のセキュリティ方針 - プラットフォーム セキュリティ](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [WPF のセキュリティ方針 - セキュリティ エンジニアリング](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
