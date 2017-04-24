---
title: "WPF のグローバリゼーションおよびローカリゼーションの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "グローバリゼーション, グローバリゼーションの概要"
  - "ローカリゼーション, ローカリゼーションの概要"
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
caps.latest.revision: 39
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 34
---
# WPF のグローバリゼーションおよびローカリゼーションの概要
製品を 1 言語だけで作成することは、潜在的な顧客ベースを、65 億の世界人口のごく一部に制限することを意味します。  アプリケーション製品をグローバルな市場に届けようとする場合、最良かつ経済的な方法の 1 つは、費用対効果の高いローカリゼーションです。  
  
 ここでは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のグローバリゼーションとローカリゼーションについて説明します。  グローバリゼーションとは、さまざまな場所で実行されるアプリケーションを設計および開発することです。  たとえば、グローバリゼーションは、さまざまなカルチャのユーザーのために、ローカライズされたユーザー インターフェイスと地域データをサポートします。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、自動レイアウト、サテライト アセンブリ、ローカリゼーション属性とコメントなどの、グローバル化されたデザイン機能が用意されています。  
  
 ローカリゼーションとは、アプリケーションでサポートする特定のカルチャ用のローカライズ バージョンに、アプリケーション リソースを変換することです。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でローカライズする場合には、<xref:System.Windows.Markup.Localizer> 名前空間の API を使用します。これらの API により、[LocBaml ツールのサンプル](http://go.microsoft.com/fwlink/?LinkID=160016)のコマンド ライン ツールが機能します。  LocBaml を構築して使用する方法については、「[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)」を参照してください。  
  
   
  
## WPF のグローバリゼーションとローカリゼーションのベスト プラクティス  
 ここに示す UI 設計とローカリゼーションに関するヒントに従うと、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に組み込まれたグローバリゼーション機能とローカリゼーション機能を最大限に活用できます。  
  
### WPF の UI 設計のベスト プラクティス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を設計する場合、これらのベスト プラクティスの実装を考慮してください。  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で記述します。[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] はコードで作成しないようにします。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用して [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を作成する場合は、組み込みローカリゼーション API を通じてそれを公開します。  
  
-   コンテンツのレイアウト時に、絶対位置と固定サイズを使用しないようにします。代わりに、相対位置と自動サイズ設定を使用します。  
  
    -   <xref:System.Windows.Window.SizeToContent%2A> を使用し、幅と高さの設定を `Auto` に維持します。  
  
    -   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のレイアウト時に、<xref:System.Windows.Controls.Canvas> を使用しないようにします。  
  
    -   <xref:System.Windows.Controls.Grid> とそのサイズ共有機能を使用します。  
  
-   ローカライズされたテキストはより多くのスペースを必要とすることが多いため、余白にスペースを確保しておきます。  余分なスペースがあれば、文字の張り出しに対応できます。  
  
-   <xref:System.Windows.Controls.TextBlock> で <xref:System.Windows.Controls.TextBlock.TextWrapping%2A> を有効にして、クリッピングを回避します。  
  
-   **xml:lang** 属性を設定します。  この属性は、特定の要素のカルチャと、その子要素について記述します。  このプロパティの値は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のいくつかの機能の動作を変更します。たとえば、ハイフネーション、スペル チェック、数字の置換、複雑な文字の整形、フォントの代替などの動作を変更します。  [XAML における xml:lang の処理](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md) の設定の詳細については、「[WPF のグローバリゼーション](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)」を参照してください。  
  
-   さまざまな言語で使用されるフォントをより良く制御するには、カスタマイズした複合フォントを作成します。  既定では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって Windows\\Fonts ディレクトリの GlobalUserInterface.CompositeFont が使用されます。  
  
-   作成するナビゲーション アプリケーションが、右から左の方向にテキストを表示するカルチャにローカライズされる可能性がある場合は、各ページの <xref:System.Windows.FlowDirection> を明示的に設定して、ページが <xref:System.Windows.Navigation.NavigationWindow> の <xref:System.Windows.FlowDirection> を継承しないようにします。  
  
-   ブラウザーの外でホストされるスタンドアロンのナビゲーション アプリケーションを作成する場合、初期アプリケーションの <xref:System.Windows.Application.StartupUri%2A> に、ページ \(`<Application StartupUri="NavigationWindow.xaml">` など\) ではなく <xref:System.Windows.Navigation.NavigationWindow> を設定します。  この設計を使用すると、ウィンドウとナビゲーション バーの <xref:System.Windows.FlowDirection> を変更できます。  詳細および例については、[グローバリゼーション ホームページのサンプル](http://go.microsoft.com/fwlink/?LinkID=159990)を参照してください。  
  
### WPF のローカリゼーションのベスト プラクティス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのアプリケーションをローカライズする場合、次のベスト プラクティスの実装を考慮してください。  
  
-   ローカリゼーション コメントを使用して、ローカライザーに追加のコンテキストを提供します。  
  
-   ローカリゼーションを制御するには、要素の <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを選択的に省略するのではなく、ローカリゼーション属性を使用します。  詳細については、「[ローカリゼーション属性とコメント](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md)」を参照してください。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを追加して確認するには、**msbuild \/t:updateuid** および **\/t:checkuid** を使用します。  開発とローカリゼーション間の変更を追跡するには、<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを使用します。<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティは、開発の新しい変更をローカライズする際に役立ちます。  <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを手動で [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] に追加すると、一般に、作業が面倒なうえ正確さに欠けます。  
  
    -   ローカリゼーションの開始後は、<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを編集または変更しないようにします。  
  
    -   重複した <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを使用しないようにします \(コピーして貼り付けるコマンドを使用するときはこの点に留意してください\)。  
  
    -   AssemblyInfo.\* の `UltimateResourceFallback` 位置を設定して、フォールバックに適した言語を指定します \(たとえば `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`\)。  
  
         プロジェクト ファイルの `<UICulture>` タグを省略して、メイン アセンブリにソース言語を含める場合、`UltimateResourceFallback` 位置にサテライトではなくメイン アセンブリを設定します \(たとえば `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`\)。  
  
<a name="workflow_to_localize"></a>   
## WPF アプリケーションをローカライズする  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションをローカライズするときには、いくつかのオプションがあります。  たとえば、アプリケーション内のローカライズ可能リソースを [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ファイルにバインドしたり、ローカライズ可能テキストを resx テーブルに格納したり、ローカライザーが [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルを使用したりできます。  ここでは、XAML の BAML 形式を使用したローカリゼーション ワークフローについて説明します。これによって次のような利点が提供されます。  
  
-   ビルド後にローカライズできます。  
  
-   古いバージョンの XAML の BAML 形式を使用したローカリゼーションで、新しいバージョンの XAML の BAML 形式に更新できるので、開発と同時にローカライズできます。  
  
-   XAML の BAML 形式は [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] をコンパイルした形式であるので、元のソース要素とセマンティクスをコンパイル時に検証できます。  
  
### ローカリゼーションのビルド プロセス  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを開発する場合の、ローカリゼーションのビルド プロセスは次のとおりです。  
  
-   開発者が [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを作成し、グローバル化します。  アプリケーションのコンパイル時に、言語に依存しないメイン アセンブリが生成されるように、プロジェクト ファイルで開発者が `<UICulture>en-US</UICulture>` を設定します。このアセンブリには、すべてのローカライズ可能リソースが含まれた、サテライトの .resources.dll ファイルがあります。ローカリゼーション [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ではメイン アセンブリからの抽出がサポートされるので、必要に応じてソース言語をメイン アセンブリ内に残すこともできます。  
  
-   ファイルをビルドにコンパイルすると、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] が XAML の BAML 形式に変換されます。  カルチャに依存しない `MyDialog.exe` ファイルと、カルチャに依存する \(英語の\) `MyDialog.resources.dll` ファイルを、英語圏の顧客にリリースします。  
  
### ローカリゼーション ワークフロー  
 ローカライズされていない `MyDialog.resources.dll` ファイルがビルドされた後、ローカリゼーション プロセスが始まります。  <xref:System.Windows.Markup.Localizer> の下の [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] が使用され、元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 内の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素とプロパティが、XAML の BAML 形式からキーと値のペアとして抽出されます。  ローカライザーは、キーと値のペアを使用して、アプリケーションをローカライズします。  ローカリゼーションの完了後、新しい値から新しい .resource.dll を生成できます。  
  
 キーと値のペアにおけるキーは、開発者が元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] に配置した `x:Uid` 値です。  これらの `x:Uid` 値を使用すると、ローカリゼーション時に開発者とローカライザーの間で発生する変更を、[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] で追跡およびマージすることができます。  たとえば、ローカライザーがローカライズを開始した後に開発者が [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を変更した場合、完了したローカリゼーション作業に開発の変更をマージして、失われる変換作業を最小限に抑えることができます。  
  
 次の図に、XAML の BAML 形式に基づく一般的なローカリゼーション ワークフローを示します。  この図では、開発者が英語のアプリケーションを作成しているものとします。  開発者が WPF アプリケーションを作成し、グローバル化します。  開発者は、ビルド時に言語に依存しないメイン アセンブリが生成されるように、プロジェクト ファイルに `<UICulture>en-US</UICulture>` を設定します。このアセンブリには、すべてのローカライズ可能リソースが含まれた、サテライトの .resources.dll があります。  WPF のローカリゼーション API ではメイン アセンブリからの抽出がサポートされるため、必要に応じてソース言語をメイン アセンブリ内に残すこともできます。  ビルド処理が完了すると、XAML は BAML にコンパイルされます。  カルチャに依存しない MyDialog.exe.resources.dll を、英語圏の顧客に出荷します。  
  
 ![ローカリゼーション ワークフロー](../../../../docs/framework/wpf/advanced/media/localizationworkflow.png "LocalizationWorkflow")  
  
 ![非ローカライズ ワークフロー](../../../../docs/framework/wpf/advanced/media/localizationworkflow2.png "LocalizationWorkflow2")  
  
<a name="examples_of_localization"></a>   
## WPF のローカリゼーションの例  
 ここでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションをビルドおよびローカライズする方法の理解に役立つ、ローカライズされたアプリケーションの例を示します。  
  
#### \[Run\] ダイアログ ボックスの例  
 次の図は、\[Run\] ダイアログ ボックスのサンプルの出力を示します。  
  
 **次に示します。**  
  
 ![&#91;実行&#93; ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/rundialogenglish.png "RunDialogEnglish")  
  
 **ドイツ語 :**  
  
 ![ドイツ語の &#91;Run&#93; ダイアログ ボックス](../../../../docs/framework/wpf/advanced/media/rundialoggerman.png "RunDialogGerman")  
  
 **グローバルな \[Run\] ダイアログ ボックスの設計**  
  
 この例では、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] および [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用して、\[Run\] ダイアログ ボックスを作成します。  このダイアログ ボックスは、[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] の \[スタート\] メニューから使用可能な **\[ファイル名を指定して実行\]** ダイアログ ボックスと同じものです。  
  
 グローバルなダイアログ ボックスを作成するためのいくつかの要点を次に示します。  
  
 **Automatic Layout**  
  
 *次の Window1.xaml の行を見てください。*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 上記のウィンドウのプロパティでは、ウィンドウのサイズがコンテンツのサイズに合わせて自動的に変更されます。  このプロパティは、ローカリゼーション後にサイズが大きくなるコンテンツが切り捨てられないようにします。また、ローカリゼーション後にコンテンツのサイズが小さくなる場合は、不要なスペースを削除します。  
  
 `<Grid x:Uid="Grid_1">`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ローカリゼーションの [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] が正しく機能するためには、<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティが必要です。  
  
 これは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ローカリゼーションの [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] によって、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] の開発とローカリゼーション間の変更を追跡するために使用されます。  <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを使用すると、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の新しいバージョンを [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] の古いローカリゼーションにマージできます。  <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを追加するには、コマンド シェルで **msbuild \/t:updateuid RunDialog.csproj** を実行します。  <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティの追加には、この方法をお勧めします。一般に、手動で追加すると時間がかかり、正確さにも欠けます。  <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティが正しく設定されたことを確認するには、**msbuild \/t:checkuid RunDialog.csproj** を実行します。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は <xref:System.Windows.Controls.Grid> コントロールを使用して構造化されます。このコントロールは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の自動レイアウトを利用するために役立ちます。  ダイアログ ボックスは、3 行 5 列に分割されています。  どの行と列にも、固定サイズが定義されていません。このため、各セルに配置された [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素は、ローカライズ時のサイズの増加や減少に対応できます。  
  
 [!code-xml[GlobalizationRunDialog#GridColumnDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 **\[Open:\]** ラベルと <xref:System.Windows.Controls.ComboBox> が配置されている最初の 2 列は、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 全体の幅の 10%を使用します。  
  
 [!code-xml[GlobalizationRunDialog#GridColumnDef2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 この例では、<xref:System.Windows.Controls.Grid> のサイズ設定共有機能を使用しています。  最後の 3 列は同じ <xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A> に配置され、この機能を利用しています。  名前から推測できるとおり、このプロパティを使用すると、複数の列で同じサイズを共有できます。  このため、"Browse..." がこれより長い文字列 "Durchsuchen..." にローカライズされた場合、小さい \[OK\] ボタンと極端に大きい \[Durchsuchen...\] ボタンが作成される代わりに、すべてのボタンの幅が広くなります。  
  
 **Xml:lang**  
  
 `Xml:lang="en-US"`  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のルート要素に配置された [XAML における xml:lang の処理](../../../../docs/framework/xaml-services/xml-lang-handling-in-xaml.md)に注目してください。  このプロパティは、指定した要素のカルチャと、その子について記述します。  この値は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のいくつかの機能で使用され、ローカライズ時に適切に変更される必要があります。  この値は、単語のハイフネーションとスペル チェックに使用する言語辞書を変更します。  また、桁の表示と、フォントの代替システムが使用フォントを選択する方法にも影響します。  最後に、このプロパティは、数字の表示方法と、複雑な文字を使用したテキストの整形方法にも影響します。  既定値は "en\-US" です。  
  
 **Building a Satellite Resource Assembly**  
  
 *次の .csproj の行を見てください。*  
  
 `<UICulture>en-US</UICulture>`  
  
 `UICulture` 値が追加されています。  これが en\-US などの有効な <xref:System.Globalization.CultureInfo> 値に設定されている場合、プロジェクトのビルドによって、すべてのローカライズ可能リソースが含まれたサテライト アセンブリが生成されます。  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG` は、すべてのカルチャで同様に表示するため、ローカライズする必要がありません。  サテライト アセンブリに含めるのではなく、言語に依存しないメイン アセンブリ内にこれを残すよう、`Localizable` を `false` に設定します。  すべてのコンパイル不可能なリソースの `Localizable` は、既定で `true` に設定されます。  
  
 **\[Run\] ダイアログのローカライズ**  
  
 **Parse**  
  
 アプリケーションのビルド後、これをローカライズする最初の手順は、ローカライズ可能リソースをサテライト アセンブリから解析することです。  ここでは、[LocBaml ツールのサンプル](http://go.microsoft.com/fwlink/?LinkID=160016)にある、サンプルの LocBaml ツールを使用します。   ただし、LocBaml はサンプル ツールに過ぎず、独自のローカリゼーション プロセスに合ったローカリゼーション ツールの構築を始める支援するためのものです。  LocBaml で **LocBaml \/parse RunDialog.resources.dll \/out:** を実行して解析を行い、RunDialog.resources.dll.CSV ファイルを生成します。  
  
 **Localize**  
  
 Unicode をサポートする任意の CSV エディターを使用して、このファイルを編集します。  ローカリゼーションのカテゴリが "None" であるすべてのエントリを、フィルターで除外します。  次のエントリが表示されます。  
  
||||  
|-|-|-|  
|リソース キー|ローカライズのカテゴリ|値|  
|Button\_1:System.Windows.Controls.Button.$Content|ボタン|\[OK\]|  
|Button\_2:System.Windows.Controls.Button.$Content|ボタン|\[キャンセル\]|  
|Button\_3:System.Windows.Controls.Button.$Content|ボタン|Browse...|  
|ComboBox\_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock\_1:System.Windows.Controls.TextBlock.$Content|テキスト|Type the name of a program, folder, document, or Internet resource, and Windows will open it for you.|  
|TextBlock\_2:System.Windows.Controls.TextBlock.$Content|テキスト|Open:|  
|Window\_1:System.Windows.Window.Title|Title|\[実行\]|  
  
 アプリケーションをドイツ語にローカライズするには、次の変換が必要です。  
  
||||  
|-|-|-|  
|リソース キー|ローカライズのカテゴリ|値|  
|Button\_1:System.Windows.Controls.Button.$Content|ボタン|\[OK\]|  
|Button\_2:System.Windows.Controls.Button.$Content|ボタン|Abbrechen|  
|Button\_3:System.Windows.Controls.Button.$Content|ボタン|Durchsuchen…|  
|ComboBox\_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock\_1:System.Windows.Controls.TextBlock.$Content|テキスト|Geben Sie den Namen eines Programms, Ordners, Dokuments oder einer Internetresource an.|  
|TextBlock\_2:System.Windows.Controls.TextBlock.$Content|テキスト|Öffnen:|  
|Window\_1:System.Windows.Window.Title|Title|\[実行\]|  
  
 **Generate**  
  
 ローカリゼーションの最後の手順では、新しくローカライズされたサテライト アセンブリを作成します。  これを行うには、次の LocBaml コマンドを使用します。  
  
 **LocBaml.exe \/generate RunDialog.resources.dll \/trans:RunDialog.resources.dll.CSV \/out: .  \/cul:de\-DE**  
  
 ドイツ語版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] では、メイン アセンブリの隣の de\-DE フォルダーにこの resources.dll が配置されている場合、en\-US フォルダー内のリソースの代わりに、このリソースが自動的に読み込まれます。  これをテストするためのドイツ語版の [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] を所有していない場合は、カルチャに、現在使用している [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] のカルチャ \(  en\-US\) を設定し、元の resources.dll を置き換えます。  
  
 **Satellite Resource Loading**  
  
|MyDialog.exe|en\-US\\MyDialog.resources.dll|de\-DE\\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|コード|元の英語の BAML|ローカライズされた BAML|  
|カルチャに依存しないリソース|英語のその他のリソース|ドイツ語にローカライズされたその他のリソース|  
  
 .NET Framework は、読み込むサテライト リソース アセンブリを、アプリケーションの `Thread.CurrentThread.CurrentUICulture` に基づいて自動的に選択します。  既定では、使用している [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] OS のカルチャです。  つまり、ドイツ語版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] を使用している場合は de\-DE\\MyDialog.resources.dll が読み込まれ、英語版 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] を使用している場合は en\-US\\MyDialog.resources.dll が読み込まれます。  プロジェクトの AssemblyInfo.\* で NeutralResourcesLanguage を指定すると、アプリケーションの最終フォールバック リソースを設定できます。  たとえば、次のように指定するとします。  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 こうすると、ドイツ語版 Windows で de\-DE\\MyDialog.resources.dll と de\\MyDialog.resources.dll のどちらも使用できない場合に、en\-US\\MyDialog.resources.dll が使用されます。  
  
### Microsoft サウジアラビアのホームページ  
 次の図は、英語とアラビア語のホームページを示します。  これらのグラフィックスを生成するサンプル全体については、[グローバリゼーション ホームページのサンプル](http://go.microsoft.com/fwlink/?LinkID=159990)を参照してください。  
  
 **次に示します。**  
  
 ![英語ページ](../../../../docs/framework/wpf/advanced/media/englishhomepage.png "EnglishHomepage")  
  
 **アラビア語 :**  
  
 ![アラビア語ページ](../../../../docs/framework/wpf/advanced/media/arabichomepage.png "ArabicHomepage")  
  
### Microsoft のグローバルなホームページの設計  
 この Microsoft サウジアラビアの Web サイトのサンプルは、RightToLeft 言語に提供されるグローバリゼーション機能を表しています。  ヘブライ語やアラビア語などの言語は右から左に読むため、多くの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のレイアウトを、英語などの左から右に読む言語の場合とは大幅に変える必要があります。  左から右に読む言語と右から左に読む言語の間では、ローカリゼーションが困難な場合があります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、そのようなローカリゼーションをはるかに簡単に行うことができるよう設計されています。  
  
 **FlowDirection**  
  
 *Homepage.xaml を次に示します。*  
  
 [!code-xml[GlobalizationHomepage#Homepage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 <xref:System.Windows.Controls.Page> の <xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティに注目してください。  このプロパティを <xref:System.Windows.FlowDirection> に変更すると、<xref:System.Windows.Controls.Page> とその子要素の <xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティが変更されます。その結果、この [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] のレイアウトが反転し、アラビア語圏のユーザーに適した右から左の表示になります。  任意の要素で <xref:System.Windows.FrameworkElement.FlowDirection%2A> を明示的に指定すると、この継承動作をオーバーライドできます。  <xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティはすべての <xref:System.Windows.FrameworkElement> やドキュメント関連要素で使用でき、暗黙的な値は <xref:System.Windows.FlowDirection> です。  
  
 ルートの <xref:System.Windows.FrameworkElement.FlowDirection%2A> を変更すると、背景のグラデーション ブラシも正しく反転します。  
  
 **FlowDirection\="LeftToRight"**  
  
 ![左から右に読む](../../../../docs/framework/wpf/advanced/media/lefttoright.png "LeftToRight")  
  
 **FlowDirection\="RightToLeft"**  
  
 ![右から左に読む](../../../../docs/framework/wpf/advanced/media/righttoleft.png "RightToLeft")  
  
 **固定サイズのパネルとコントロールの使用を回避する**  
  
 Homepage.xaml を調べると、上部の <xref:System.Windows.Controls.DockPanel> の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 全体に対して固定の幅と高さが指定されていることを除けば、他に固定サイズがないことがわかります。  ローカライズ後にソース テキストより長くなったテキストがクリップされるのを回避するため、固定サイズは使用しないようにします。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のパネルとコントロールは、含まれているコンテンツに基づいて自動的にサイズ変更されます。  多くのコントロールは、最小サイズと最大サイズを設定して制御することもできます   \(MinWidth\= "20" など\)。  <xref:System.Windows.Controls.Grid> では、「\*」を使用して相対的な幅と高さを設定したり   \(Width\= "0.25\*" など\)、セル サイズの共有機能を使用したりすることもできます。  
  
 **ローカリゼーション コメント**  
  
 コンテンツが不明確で変換が困難な場合も少なくありません。  開発者またはデザイナーは、ローカリゼーション コメントを通じて、追加のコンテキストやコメントをローカライザーに提供できます。  たとえば、次の Localization.Comments は "&#124;" 文字の使用方法を説明しています。  
  
 [!code-xml[GlobalizationHomepage#LocalizationComment](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 このコメントは TextBlock\_1 のコンテンツと関連付けられ、LocBaml ツール \(「[アプリケーションをローカライズする](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md)」を参照\) の場合、出力 .csv ファイルの TextBlock\_1 行の 6 列目に表示されます。  
  
|||||||  
|-|-|-|-|-|-|  
|リソース キー|\[カテゴリ\]|読み取り可能|変更可能|コメント|値|  
|TextBlock\_1:System.Windows.Controls.TextBlock.$Content|テキスト|TRUE|TRUE|This character is used as a decorative rule.|&#124;|  
  
 任意の要素のコンテンツやプロパティにコメントを配置するには、次の構文を使用します。  
  
 [!code-xml[GlobalizationHomepage#LocalizationCommentsProp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **ローカリゼーション属性**  
  
 ローカライザーが読んだり変更したりできる箇所を、開発者やローカリゼーション マネージャーが制御する必要がある場合も少なくありません。  たとえば、会社名や法的文言をローカライザーに変換させたくない場合もあります。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、要素のコンテンツやプロパティの readability、modifiability、および category を設定するための属性が用意されています。これらの属性を独自のローカリゼーション ツールで使用して、要素をロックしたり、非表示にしたり、並べ替えたりできます。  詳細については、「<xref:System.Windows.Localization.Attributes%2A>」を参照してください。  このサンプルでは、LocBaml ツールがこれらの属性の値だけを出力します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のすべてのコントロールには、これらの属性の既定値がありますが、オーバーライドすることもできます。  たとえば、次の例では `TextBlock_1` の既定のローカリゼーション属性をオーバーライドして、ローカライザーがコンテンツを読み取ることはできても変更できないように設定します。  
  
 [!code-xml[LocalizationComAtt#LocalizationAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、readability および modifiability の属性に加えて、UI の一般的なカテゴリの列挙体 \(<xref:System.Windows.LocalizationCategory>\) が用意されており、より多くのコンテキストをローカライザーに提供するために使用できます。  プラットフォーム コントロールに対する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の既定のカテゴリも、次のように [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 内でオーバーライドできます。  
  
 [!code-xml[LocalizationComAtt#LocalizationAttributesOverridden](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で提供される既定のローカリゼーション属性は、コードを使用してもオーバーライドできるため、カスタム コントロールに対する適切な既定値を正しく設定できます。  次に例を示します。  
  
 `[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]`  
  
 `public class CorporateLogo: TextBlock`  
  
 `{`  
  
 `…`  
  
 `..`  
  
 `.`  
  
 `}`  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で設定されたインスタンスごとの属性は、カスタム コントロールに対してコードで設定された値より優先されます。  属性とコメントの詳細については、「[ローカリゼーション属性とコメント](../../../../docs/framework/wpf/advanced/localization-attributes-and-comments.md)」を参照してください。  
  
 **フォントの代替と複合フォント**  
  
 指定されているコード ポイント範囲をサポートしないフォントを指定した場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] によって Windows\\Fonts ディレクトリの GlobalUserInterface.CompositeFont が使用され、そのコード ポイント範囲をサポートするフォントに自動的に置き換えられます。  複合フォントは、その他のフォントと同様に機能し、要素の FontFamily \(たとえば、  FontFamily\= "Global User Interface"\) を設定することにより明示的に使用できます。  独自の複合フォントを作成し、特定のコード ポイント範囲や言語で使用するフォントを指定することにより、フォントの代替設定を独自に指定することもできます。  
  
 複合フォントの詳細については、<xref:System.Windows.Media.FontFamily> を参照してください。  
  
 **Microsoft ホームページのローカライズ**  
  
 \[Run\] ダイアログの例と同じ手順に従って、このアプリケーションをローカライズできます。  アラビア語にローカライズされた .csv ファイルについては、[グローバリゼーション ホームページのサンプル](http://go.microsoft.com/fwlink/?LinkID=159990)を参照してください。