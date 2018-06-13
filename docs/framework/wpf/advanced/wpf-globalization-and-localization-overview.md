---
title: WPF のグローバリゼーションおよびローカリゼーションの概要
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: 957ba16886669acdfa5501ffe02501cbe6e57198
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549618"
---
# <a name="wpf-globalization-and-localization-overview"></a>WPF のグローバリゼーションおよびローカリゼーションの概要
1 つの言語、製品の可用性を制限する場合は、潜在的な顧客の世界 6.5 と人口の割合をベースを制限します。 世界各国のユーザーに到達するようにアプリケーションを実行する場合に、製品のコスト効果の高いローカライズはより多くの顧客に最適かつ最も経済的な方法のいずれかです。  
  
 この概要では、グローバリゼーションとローカリゼーションが導入されています[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。 グローバリゼーションとは、設計と複数の場所で実行されるアプリケーションを開発します。 たとえば、グローバリゼーション ローカライズされたユーザー インターフェイスとサポート地域のデータの異なるカルチャ内のユーザーのです。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] グローバル化されたデザイン機能、自動レイアウト、サテライト アセンブリ、およびローカライズされた属性を含むとコメントを提供します。
  
 ローカリゼーションとは、アプリケーションがサポートする特定のカルチャのローカライズ バージョンへのアプリケーション リソースを変換します。 ローカライズするときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で Api を使用する、<xref:System.Windows.Markup.Localizer>名前空間。 これらの Api 電源、 [LocBaml ツール サンプル](http://go.microsoft.com/fwlink/?LinkID=160016)コマンド ライン ツールです。 構築し、LocBaml を使用する方法については、次を参照してください。[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)です。    
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>グローバリゼーションとローカリゼーション WPF のベスト プラクティス  
 組み込まれているグローバリゼーションおよびローカリゼーションの機能を最大限に活用することができます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に従って、UI のデザイン、ローカリゼーション関連のヒントについてこのセクションの内容を提供します。  
  
### <a name="best-practices-for-wpf-ui-design"></a>WPF の UI の設計に関するベスト プラクティス  
 デザインするとき、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– ベース[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、これらのベスト プラクティスを実装することを検討してください。  
  
-   書き込み、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; を作成しないように[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のコードにします。 作成するときに、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、組み込みのローカリゼーション Api を介して公開します。  
  
-   コンテンツをレイアウトする絶対位置および固定サイズを使用しないでください。代わりに、相対パスまたは自動サイズ設定を使用します。
  
    -   使用して<xref:System.Windows.Window.SizeToContent%2A>; 幅と高さの設定を保持および`Auto`です。  
  
    -   使用しないでください<xref:System.Windows.Controls.Canvas>をレイアウトする[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]s。  
  
    -   使用して<xref:System.Windows.Controls.Grid>とそのサイズの共有機能します。  
  
-   ローカライズされたテキストには多くの場合より多くの領域が必要とするための余白で余分なスペースを提供します。 余分なスペースにより、考えられる突出文字。  
  
-   有効にする<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>で<xref:System.Windows.Controls.TextBlock>クリッピングを避けることです。
  
-   設定、 **xml:lang**属性。 この属性には、特定の要素とその子要素のカルチャがについて説明します。 このプロパティの値でいくつかの機能の動作が変更[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 たとえば、ハイフネーション、スペル チェック、数値の置換、複雑なスクリプトの整形、およびフォント フォールバックの動作を変更します。 参照してください[WPF のグローバリゼーション](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)設定に関する詳細について、 [xml:lang XAML での処理](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)です。  
  
-   異なる言語に使用されるフォントの制御を強化するためのカスタマイズされた複合フォントを作成します。 既定では、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows\Fonts ディレクトリに GlobalUserInterface.composite フォントを使用します。  
  
-   右から左へ形式でテキストを表示する、カルチャにローカライズされる可能性がありますナビゲーション アプリケーションを作成すると、明示的に設定、<xref:System.Windows.FlowDirection>の各ページには、ページを継承しません<xref:System.Windows.FlowDirection>から、<xref:System.Windows.Navigation.NavigationWindow>です。  
  
-   ブラウザー外でホストされているスタンドアロン ナビゲーション アプリケーションを作成するときに設定、<xref:System.Windows.Application.StartupUri%2A>初期アプリケーションに、<xref:System.Windows.Navigation.NavigationWindow>の代わりに、ページに (たとえば、 `<Application StartupUri="NavigationWindow.xaml">`)。 この設計では、変更することができます、<xref:System.Windows.FlowDirection>はウィンドウとナビゲーション バー。 例および詳細については、次を参照してください。[グローバリゼーション ホームページのサンプル](http://go.microsoft.com/fwlink/?LinkID=159990)です。  
  
### <a name="best-practices-for-wpf-localization"></a>WPF のローカライズ用のベスト プラクティス  
 ローカライズする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– ベースのアプリケーションでは、これらのベスト プラクティスの実装を検討します。  
  
-   ローカリゼーション コメントを使用して、ローカライズの余分なコンテキストを指定します。  
  
-   ローカリゼーション属性を使用して、選択的に省略することではなく制御<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>要素のプロパティです。 参照してください[ローカリゼーション属性とコメント](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md)詳細についてはします。  
  
-   使用して**msbuild/t:updateuid**と **/t:checkuid**を追加および確認<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティで、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 使用して<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>開発およびローカリゼーションの間での変更を追跡するプロパティです。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを使用して、新しい開発上の変更をローカライズできます。 手動で追加する場合<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティを[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]タスクは通常面倒と正確さに欠けます。  
  
    -   編集または変更しない<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティのローカライズを開始した後です。  
  
    -   重複データを使用しないでください<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティ (コピーと貼り付け コマンドを使用する場合は、このヒントを忘れないでください)。  
  
    -   設定、`UltimateResourceFallback`フォールバックの適切な言語を指定する AssemblyInfo.* 内の場所 (たとえば、 `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`)。  
  
         省略すると、メイン アセンブリに、元の言語を含める場合、`<UICulture>`は、プロジェクト ファイルにタグ付けは、設定、`UltimateResourceFallback`サテライトの代わりにメイン アセンブリと場所 (たとえば、 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`)。  
  
<a name="workflow_to_localize"></a>   
## <a name="localize-a-wpf-application"></a>WPF アプリケーションをローカライズします。  
 ローカライズするときに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション、複数のオプションがあります。 アプリケーションのローカライズ可能なリソースをバインドするなど、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ファイル、resx テーブル内のローカライズ可能なテキストを格納または使用して、ローカライザー[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル。 このセクションでは、いくつかの利点を提供する XAML の BAML 形式を使用するローカライズ ワークフローについて説明します。  
  
-   ビルドした後はローカライズできます。  
  
-   開発するのと同時にローカライズできるように XAML の BAML 形式の古いバージョンから XAMLwith のローカライズ版の BAML 形式は、の新しいバージョンに更新することができます。  
  
-   検証する元のソース要素とセマンティクス コンパイル時に XAML の BAML 形式は、コンパイルした形式のため[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。  
  
### <a name="localization-build-process"></a>ローカリゼーションのビルド プロセス  
 開発する際に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでのローカライズ用のビルド プロセスは次のようにします。  
  
-   開発者が作成し、グローバライズ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。 ファイル、プロジェクトでは開発者セット`<UICulture>en-US</UICulture>`言語に依存しないメイン アセンブリが生成されたアプリケーションをコンパイルするときに、できるようにします。 このアセンブリのサテライト。 ローカライズ可能なすべてのリソースを含む.resources.dll ファイル。 必要に応じて、おくソース言語メイン アセンブリであるため、ローカリゼーション[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]メインのアセンブリからの抽出をサポートします。  
  
-   ファイルが、ビルドにコンパイルされるときに、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は XAML の BAML 形式に変換されます。 カルチャに依存しない`MyDialog.exe`とカルチャに依存 (英語)`MyDialog.resources.dll`英語圏の顧客にファイルを解放します。  
  
### <a name="localization-workflow"></a>ローカリゼーション ワークフロー  
 ローカリゼーション処理した後に開始、ローカライズされていない`MyDialog.resources.dll`ファイルをビルドします。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素と、元のプロパティ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、キーと値のペアには、XAML の BAML 形式から抽出された、 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.Markup.Localizer>です。 ローカライザーでは、キー/値ペアを使用して、アプリケーションをローカライズします。 新しいを生成することができます。 ローカリゼーションが完了した後に新しい値から resource.dll です。  
  
 キー/値ペアのキーは、`x:Uid`開発者が、元に配置されている値[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 これら`x:Uid`値を有効にする、[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]を追跡およびローカリゼーションの中に、開発者やローカライザー間に行われる変更をマージします。 たとえば、開発者が変更された場合、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ローカライザーをローカライズする開始した後は、最小限の翻訳作業が失われたようにローカリゼーションが既に完了した作業と開発の変更をマージすることです。  
  
 次の図は、XAML の BAML 形式に基づいている一般的なローカリゼーション ワークフローを示します。 この図では、開発者が英語でアプリケーションを記述前提としています。 開発者は、作成し、WPF アプリケーションのグローバライズします。 ファイル、プロジェクトでは開発者を設定`<UICulture>en-US</UICulture>`ビルド時に、言語に中立的なメイン アセンブリはサテライトの生成を取得できるようにします。 すべてのローカライズ可能なリソースを含む resources.dll です。 代わりに、WPF ローカリゼーション Api メインのアセンブリからの抽出をサポートするためメイン アセンブリにソース言語を残す 1 つでした。 ビルド プロセスの後に、XAML は BAML にコンパイルを取得します。 カルチャ ニュートラル MyDialog.exe.resources.dll は、英語圏顧客に出荷を取得します。  
  
 ![ローカリゼーション ワークフロー](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![作業の流れローカライズされていない](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## <a name="examples-of-wpf-localization"></a>WPF のローカリゼーションの例  
 このセクションには、ローカライズされたアプリケーションをビルドおよびローカライズする方法を理解するための例が含まれています。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。  
  
#### <a name="run-dialog-box-example"></a>ダイアログ ボックスの例を実行します。  
 次の図の出力を表示する、**実行**ダイアログ ボックスのサンプルです。  
  
 **英語：**  
  
 ![実行 ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/rundialogenglish.PNG "RunDialogEnglish")  
  
 **ドイツ語：**  
  
 ![ドイツ語の実行 ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/rundialoggerman.PNG "RunDialogGerman")  
  
 **グローバルの実行 ダイアログ ボックスを設計**  
  
 この例で作成、**実行** ダイアログ ボックスを使用して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 このダイアログ ボックスは、**実行** ダイアログ ボックスが表示されます、 [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [スタート] メニュー。  
  
 グローバルなダイアログ ボックスを行うためのいくつかの特徴は次のとおりです。  
  
 **自動レイアウト**  
  
 *Window1.xaml: で*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 前のウィンドウのプロパティには、コンテンツのサイズに従ってウィンドウが自動的にサイズ変更します。 このプロパティにより、ローカリゼーション後にサイズが大きくなるコンテンツ ウィンドウローカライズ後のサイズでコンテンツが減少したとき、不要なスペースが削除されます。  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティがために必要な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカリゼーション[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]正常に動作します。  
  
 使用されている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカリゼーション[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]開発およびローカリゼーションの間の変更を追跡するために、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを使用すると、新しいバージョンのマージ、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の以前のローカリゼーション、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 追加する、<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>を実行して、プロパティ**msbuild/t:updateuid RunDialog.csproj**コマンド シェルでします。 これは、追加の推奨される方法<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティに手動で追加することが通常時間がかかる場合、正確さに欠けます。 確認することができます<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>を実行して、プロパティが正しく設定**msbuild/t:checkuid RunDialog.csproj**です。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を使用して構造化、<xref:System.Windows.Controls.Grid>を自動レイアウトの活用するために役立ちますコントロールにあるコントロールで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。 ダイアログ ボックスを次の 3 つの行と 5 つの列に分割することに注意してください。 固定サイズが使用されていないいずれかの行と列の定義そのため、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]は各セルに配置する要素が増加に適応できますとローカリゼーションの中にサイズは小さくなります。  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 最初の 2 つの列で、**開く:** ラベルと<xref:System.Windows.Controls.ComboBox>を配置しているの 10% を使用して、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]幅の合計します。  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 例では、の共有のサイズ変更機能を使用する注<xref:System.Windows.Controls.Grid>です。 最後の 3 つの列を活用これと同じでそれ自体を配置することによって<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>です。 プロパティの名前のいずれかと同様に、これにより、同じサイズを共有する列。 その場合に、「参照...」 ローカライズされますより長い文字列"Durchsuchen…"では、すべてのボタンを小さな [OK] ボタンと過度に大規模な"Durchsuchen…"ではなく幅で拡張。 を追加します。  
  
 **Xml:lang**  
  
 `Xml:lang="en-US"`  
  
 通知、 [xml:lang XAML での処理](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)のルート要素に配置され、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 このプロパティには、指定された要素とその子のカルチャがについて説明します。 この値はでいくつかの機能で使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]とローカリゼーションの中に適切に変更する必要があります。 この値は、どのような言語の辞書を使用して単語を区切るし、スペル チェックを変更します。 また、数字、およびフォント フォールバック システムが使用するフォントを選択する方法の表示も影響します。 最後に、いろいろな数字が表示されるプロパティへの影響と複雑な文字表記で記述された、方法テキストが形です。 既定値は、"EN-US"です。  
  
 **サテライト リソース アセンブリの構築**  
  
 *.Csproj: で*  
  
 `<UICulture>en-US</UICulture>`  
  
 追加に注意してください、`UICulture`値。 この設定されている場合に有効な<xref:System.Globalization.CultureInfo>プロジェクトをビルド、EN-US などの値はその中とすべてのローカライズ可能なリソースのサテライト アセンブリを生成します。  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG`すべてのカルチャと同じ表示するためにローカライズする必要はありません。 `Localizable` 設定されている`false`言語ニュートラル メイン アセンブリにサテライト アセンブリではなくが変わらないようにします。 Noncompilable のすべてのリソースの既定値は`Localizable`'éý'`true`です。  
  
 **実行用のダイアログのローカライズ**  
  
 **解析**  
  
 これをローカライズする最初の手順のアプリケーションをビルドした後はサテライト アセンブリ外ローカライズ可能なリソースが解析しています。 このトピックの目的で、ツールを使用して、サンプル LocBaml である[LocBaml ツール サンプル](http://go.microsoft.com/fwlink/?LinkID=160016)です。 LocBaml は、ローカリゼーション処理に適したローカリゼーション ツールの構築を開始するためのサンプル ツールだけであることに注意してください。 LocBaml を使用して、解析するには、次を実行: **LocBaml/解析 RunDialog.resources.dll/out:** "RunDialog.resources.dll.CSV"ファイルを生成します。  
  
 **ローカライズします。**  
  
 このファイルを編集する Unicode をサポートする使い慣れた CSV エディターを使用します。 "None"のローカライズのカテゴリのすべてのエントリをフィルター処理します。 次のエントリが表示されます。  
  
|リソース キー|ローカライズのカテゴリ|[値]|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|ボタン|OK|  
|Button_2:System.Windows.Controls.Button.$Content|ボタン|キャンセル|  
|Button_3:System.Windows.Controls.Button.$Content|ボタン|参照...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|テキスト|プログラム、フォルダー、ドキュメント、またはインターネット リソースの名前を入力し、Windows はファイルを開いて、します。|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|テキスト|開いています。|  
|Window_1:System.Windows.Window.Title|Title|実行|  
  
 アプリケーションをドイツ語のローカライズにを実行すると次の変換が必要です。  
  
|リソース キー|ローカライズのカテゴリ|[値]|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|ボタン|OK|  
|Button_2:System.Windows.Controls.Button.$Content|ボタン|Abbrechen|  
|Button_3:System.Windows.Controls.Button.$Content|ボタン|Durchsuchen しています.|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|テキスト|Geben Sie 書斎 Namen eines Programms、Ordners、Dokuments 並べ替えた einer Internetresource、します。|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|テキスト|Öffnen:|  
|Window_1:System.Windows.Window.Title|Title|実行|  
  
 **生成します。**  
  
 ローカリゼーションの最後の手順には、新しくローカライズされたサテライト アセンブリの作成が含まれます。 これには、次の LocBaml コマンドを使用します。  
  
 **LocBaml.exe/生成 RunDialog.resources.dll/trans:RunDialog.resources.dll.CSV/out: です。/cul:de-DE**  
  
 ドイツ語で[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]、このリソースは自動的に読み込ま EN-US フォルダーではなくこの resources.dll がメイン アセンブリの横にある DE-DE フォルダーに配置されている場合。 ドイツ語版のない[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]これをテストするには、任意のカルチャにカルチャを設定[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)](例: EN-US) を使用しているし、元の resources.dll を置き換えます。  
  
 **サテライト リソースの読み込み**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|コード|元の英語 BAML|ローカライズされた BAML|  
|カルチャ ニュートラル リソース|英語では、その他のリソース|ドイツ語にローカライズされた他のリソース|  
  
 .NET framework をどのサテライト リソース アセンブリを読み込むアプリケーションのに基づいて自動的に選択`Thread.CurrentThread.CurrentUICulture`です。 既定値はのカルチャ、 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] OS。 ドイツ語を使用している場合は[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]、英語を使用している場合、de-DE\MyDialog.resources.dll が読み込まれる[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]、en-US\MyDialog.resources.dll を読み込みます。 プロジェクトの AssemblyInfo.*、NeutralResourcesLanguage を指定することによって、アプリケーションの最終フォールバック リソースを設定できます。 たとえばを指定する場合。  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 de-DE\MyDialog.resources.dll または de\MyDialog.resources.dll の両方が使用できなくなった場合に、en-US\MyDialog.resources.dll ドイツ語の Windows で使用されます。  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft サウジアラビア ホーム ページ  
 次の図は、英語とアラビア語のホーム ページを表示します。 このようなグラフィックスを生成する完全なサンプルを参照してください。[グローバリゼーション ホームページのサンプル](http://go.microsoft.com/fwlink/?LinkID=159990)です。  
  
 **英語：**  
  
 ![英語版のページ](../../../../docs/framework/wpf/advanced/media/englishhomepage.jpg "EnglishHomepage")  
  
 **アラビア語：**  
  
 ![アラビア語ページ](../../../../docs/framework/wpf/advanced/media/arabichomepage.jpg "ArabicHomepage")  
  
### <a name="designing-a-global-microsoft-homepage"></a>グローバル Microsoft ホーム ページのデザイン  
 これは、模擬表示する、Microsoft サウジアラビア web サイトの RightToLeft 言語のグローバリゼーション機能を示しています。 ヘブライ語やアラビア語などの言語が、右から左への読み取り順序をあるため、レイアウトの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]多くの場合、配置する必要がある英語など、左から右への言語でより大きく異なります。 左から右への言語から、右から左へ記述する言語にまたはその逆をローカライズすると、非常に困難なことができます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] このようなローカライズかなり容易にするために設計されています。  
  
 **FlowDirection**  
  
 *Homepage.xaml:*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 通知、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティ<xref:System.Windows.Controls.Page>です。 このプロパティを変更する<xref:System.Windows.FlowDirection.RightToLeft>が変更されます、<xref:System.Windows.FrameworkElement.FlowDirection%2A>の<xref:System.Windows.Controls.Page>とその子要素ようにこれのレイアウト[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]は右から左へ記述するにつれて、アラビア語のユーザーが想定されるように反転します。 明示的なを指定して継承の動作をオーバーライドできる 1 つ<xref:System.Windows.FrameworkElement.FlowDirection%2A>任意の要素でします。 <xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティがいずれかで利用<xref:System.Windows.FrameworkElement>または関連する要素をドキュメントし、の暗黙の値を持つ<xref:System.Windows.FlowDirection.LeftToRight>します。  
  
 背景のグラデーション ブラシでもに反転するときに正しくことを確認ルート<xref:System.Windows.FrameworkElement.FlowDirection%2A>を変更します。  
  
 **FlowDirection"LeftToRight"を =**  
  
 ![左から右へのフロー](../../../../docs/framework/wpf/advanced/media/lefttoright.PNG "LeftToRight")  
  
 **FlowDirection="RightToLeft"**  
  
 ![右から左にフロー](../../../../docs/framework/wpf/advanced/media/righttoleft.PNG "RightToLeft")  
  
 **パネルとコントロールの固定サイズを使用しないでください。**  
  
 Homepage.xaml を見て、固定幅と高さが全体の指定した場合を除いてことに注意して[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]上<xref:System.Windows.Controls.DockPanel>、他の固定のディメンションはありません。 ソース テキストを超える可能性のあるローカライズされたテキストのクリッピングを防ぐために固定サイズを使用しないでください。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] パネルとコントロールが自動的に含まれているコンテンツに基づくサイズ変更します。 ほとんどのコントロールの詳細に制御を設定できる最小値と最大の次元を持つも (MinWidth =「20」) です。 <xref:System.Windows.Controls.Grid>を使用して、相対的な幅と高さを設定することも ' *' (つまり幅 ="0.25\*") または共有機能のセルのサイズを使用します。  
  
 **ローカリゼーション コメント**  
  
 ここでコンテンツしてあります。 あいまいな変換が困難な多くの場合があります。 開発者またはデザイナーは、ローカリゼーション コメントを通じてローカライザーに追加のコンテキストやコメントを提供する権限を持ちます。 下の Localization.Comments が文字の使用法を明確たとえば '&#124;' です。  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 このコメントが LocBaml ツール場合 TextBlock_1 のコンテンツに関連付けられます (を参照してください[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)) には、出力ファイルに、.csv TextBlock_1 行の 6 番目の列に表示されることができます。  
  
|リソース キー|カテゴリ|読み取り可能です|変更可能|コメント|[値]|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|テキスト|true|true|この文字は、装飾的な規則として使用されます。|&#124;|  
  
 コメントは、コンテンツまたは任意の要素の次の構文を使用してプロパティに配置できます。  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **ローカリゼーション属性**  
  
 開発者は多くの場合、またはローカリゼーション マネージャーの新機能のローカライザー読み取りおよび変更できるコントロールを必要とします。 たとえば、会社または法的な言い回しの名前を変換するローカライザーしない可能性があります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 読みやすくするため、変更、および要素のコンテンツや、ローカリゼーション ツールは、ロック、非表示、または要素の並べ替えに使用できるプロパティのカテゴリを設定できるようにする属性を提供します。 詳細については、「<xref:System.Windows.Localization.Attributes%2A>」を参照してください。 このサンプルの目的で、LocBaml ツールはこれらの属性の値だけを出力します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] すべてのコントロールは、これらの属性の既定値を持つがオーバーライドするできます。 たとえば、次の例がの既定のローカリゼーション属性よりも優先`TextBlock_1`およびローカライザーのコンテンツの読み取り可能なが不可能な状態を設定します。  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 読みやすさとを変更できる属性に加えて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の一般的な UI カテゴリの列挙体を提供 (<xref:System.Windows.LocalizationCategory>) ローカライザー詳細なコンテキストを使用できます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でプラットフォーム コントロールの既定のカテゴリをオーバーライドできる[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]も。  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 属性の既定のローカリゼーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供ため正しくカスタム コントロールの右側の既定値を設定することができますも、コード内にオーバーライドできます。 例えば:  
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 インスタンスの属性で設定ごと[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]カスタム コントロールのコードで設定された値より優先されます。 属性とコメントの詳細については、次を参照してください。[ローカリゼーション属性とコメント](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md)です。  
  
 **フォント フォールバックおよびコンポジット フォント**  
  
 指定されたコード ポイント範囲をサポートしないフォントを指定する場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は自動的には、Windows\Fonts ディレクトリに配置されているグローバル ユーザー Interface.compositefont を使用している 1 つにフォールバックします。 コンポジット フォントだけその他のフォントを使用し、要素の FontFamily を設定して明示的に使用されることができます (つまり FontFamily =「グローバル ユーザー インターフェイス」) です。 コンポジット フォントを作成し、特定のコード ポイント範囲や言語を使用するフォントを指定して、独自のフォント フォールバック設定を指定できます。  
  
 コンポジット フォントの詳細については「<xref:System.Windows.Media.FontFamily>です。  
  
 **Microsoft ホーム ページのローカライズ**  
  
 このアプリケーションをローカライズする実行 ダイアログ ボックスの例と同じ手順を行うことができます。 アラビア語のローカライズされた .csv ファイルが使用可能で、[グローバリゼーション ホームページのサンプル](http://go.microsoft.com/fwlink/?LinkID=159990)です。
