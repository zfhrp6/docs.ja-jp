---
title: "パフォーマンスの最適化 : テキスト | Microsoft Docs"
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
  - "レンダリング (テキストの)"
  - "ハイパーリンク"
  - "書式設定テキスト [WPF]"
  - "テキスト、パフォーマンス"
  - "グリフ"
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# パフォーマンスの最適化 : テキスト
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]豊富な機能を使用してテキストの内容の表示のサポートが含まれています[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]コントロールです。 一般に&3; つの層でのテキスト表示に分けることができます。  
  
1.  使用して、<xref:System.Windows.Documents.Glyphs>と<xref:System.Windows.Media.GlyphRun>オブジェクトを直接します。  
  
2.  使用して、 <xref:System.Windows.Media.FormattedText>オブジェクトです。  
  
3.  などの高度なコントロールを使用して、 <xref:System.Windows.Controls.TextBlock>と<xref:System.Windows.Documents.FlowDocument>オブジェクトです。  
  
 このトピックは、テキストのレンダリングのパフォーマンスに関する推奨事項を提供します。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Glyph_Level"></a>   
## <a name="rendering-text-at-the-glyph-level"></a>グリフ レベルでのテキストのレンダリング  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]では、高度なテキストに直接アクセスできるグリフ レベルのマークアップを含む<xref:System.Windows.Documents.Glyphs>を途中受信してテキストの書式設定後は保持しお客様にします。 これらの機能要件を指定する重要なサポート別のテキストのレンダリングの各シナリオを次にします。  
  
-   固定形式のドキュメントの画面表示されます。  
  
-   シナリオを印刷します。  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]デバイスのプリンター言語です。  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]。  
  
    -   出力元の以前のプリンター ドライバー[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]固定形式のアプリケーションです。  
  
    -   印刷スプール形式です。  
  
-   固定形式のドキュメントの表示、以前のバージョンのクライアントを含む[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]やその他のコンピューティング デバイスです。  
  
> [!NOTE]
>  <xref:System.Windows.Documents.Glyphs>と<xref:System.Windows.Media.GlyphRun>固定形式のドキュメントの表示と印刷のシナリオ用に設計されています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]いくつかの要素は、一般的なレイアウトと[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]などのシナリオ<xref:System.Windows.Controls.Label>と<xref:System.Windows.Controls.TextBlock>します。 レイアウトについての詳細と[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]シナリオを参照して、 [WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)します。  
  
 次の例は、プロパティを定義する方法を示して、<xref:System.Windows.Documents.Glyphs>オブジェクト[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]します。 <xref:System.Windows.Documents.Glyphs>オブジェクトの出力を表す、 <xref:System.Windows.Media.GlyphRun>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 例に Arial、Courier New および Times New Roman フォントがインストールされているものと、 **C:\WINDOWS\Fonts**ローカル コンピューター上のフォルダーです。  
  
 [!code-xml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
### <a name="using-drawglyphrun"></a>DrawGlyphRun を使用します。  
 カスタム コントロールがあり、グリフをレンダリングを使用する場合、 <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>メソッドです。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]カスタム書式を使用するとの下位レベル サービスも提供、 <xref:System.Windows.Media.FormattedText>オブジェクトです。 最も効率的な方法でテキストのレンダリングの[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、グリフを使用してレベルでテキストの内容を生成することによって、<xref:System.Windows.Documents.Glyphs>と<xref:System.Windows.Media.GlyphRun>します。 ただし、この効率性の低下が簡単に使用されるリッチ テキスト書式、組み込まれている機能の損失はの[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]などのコントロール<xref:System.Windows.Controls.TextBlock>と<xref:System.Windows.Documents.FlowDocument>します。  
  
<a name="FormattedText_Object"></a>   
## <a name="formattedtext-object"></a>FormattedText オブジェクト  
 <xref:System.Windows.Media.FormattedText>オブジェクトをテキスト内の各文字形式指定できる個別に、複数行のテキストを描画することができます。 詳細については、次を参照してください。[形式のテキストを描画](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)します。  
  
 書式設定されたテキストを作成するには、 <xref:System.Windows.Media.FormattedText.%23ctor%2A>コンス トラクターを作成する、 <xref:System.Windows.Media.FormattedText>オブジェクトです。 最初の書式設定されたテキスト文字列を作成した後は、さまざまな書式設定スタイルを適用できます。 アプリケーションが独自のレイアウトを実装する場合、 <xref:System.Windows.Media.FormattedText>オブジェクトは、コントロールを使用してよりも適した選択肢<xref:System.Windows.Controls.TextBlock>します。 詳細については、 <xref:System.Windows.Media.FormattedText>オブジェクトは、「[形式テキストを描画](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)します。  
  
 <xref:System.Windows.Media.FormattedText>オブジェクトは低レベルな書式設定機能を提供します。 1 つまたは複数の文字には、複数の書式スタイルを適用できます。 たとえば、両方を呼び出すことが、 <xref:System.Windows.Media.FormattedText.SetFontSize%2A>と<xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A>テキストの最初の&5; つの文字の書式を変更する方法です。  
  
 次のコード例を作成、 <xref:System.Windows.Media.FormattedText>オブジェクトし、それをレンダリングします。  
  
 [!code-csharp[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[formattedtextsnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
<a name="FlowDocument_TextBlock_Label"></a>   
## <a name="flowdocument-textblock-and-label-controls"></a>FlowDocument、TextBlock、およびラベル コントロール  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]画面にテキストを描画するための複数のコントロールが含まれます。 各コントロールには別のシナリオを対象として、独自の機能と制限事項のリストを持ちます。  
  
### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument TextBlock またはラベルよりも多くのパフォーマンスに影響  
 一般に、 <xref:System.Windows.Controls.TextBlock>制限付きのテキストのサポートが必要な場合で、簡単な文など、要素を使用する必要があります、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。 <xref:System.Windows.Controls.Label>テキストが最小限のサポートが必要なときに使用できます。 <xref:System.Windows.Documents.FlowDocument>要素は、コンテンツのリッチ プレゼンテーションで使用できる再 flowable のドキュメントのコンテナーであり、そのため、使用するよりも大きい、パフォーマンスに影響を持つ、 <xref:System.Windows.Controls.TextBlock>または<xref:System.Windows.Controls.Label>コントロールです。  
  
 詳細については<xref:System.Windows.Documents.FlowDocument>を参照してください[フロー ドキュメントの概要](../../../../docs/framework/wpf/advanced/flow-document-overview.md)します。  
  
### <a name="avoid-using-textblock-in-flowdocument"></a>FlowDocument の TextBlock を使用しないでください。  
 <xref:System.Windows.Controls.TextBlock>から派生した要素が<xref:System.Windows.UIElement>します。 <xref:System.Windows.Documents.Run>から派生した要素が<xref:System.Windows.Documents.TextElement>を使用するより低コストである、 <xref:System.Windows.UIElement>-派生オブジェクト。 可能であれば、使用<xref:System.Windows.Documents.Run>なく<xref:System.Windows.Controls.TextBlock> 、テキスト コンテンツを表示するため、 <xref:System.Windows.Documents.FlowDocument>します。  
  
 次のマークアップのサンプル内のテキスト コンテンツの設定の&2; つの方法を示しています、 <xref:System.Windows.Documents.FlowDocument>:  
  
 [!code-xml[Performance#PerformanceSnippet13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]  
  
### <a name="avoid-using-run-to-set-text-properties"></a>テキストのプロパティを設定する実行を使用しないでください。  
 一般を使用して、<xref:System.Windows.Documents.Run>内で、 <xref:System.Windows.Controls.TextBlock>明示的なを使用していないよりもパフォーマンスにはありません<xref:System.Windows.Documents.Run>すべてのオブジェクトします。 使用している場合、<xref:System.Windows.Documents.Run>テキストのプロパティを設定するためにこれらのプロパティを設定に直接、 <xref:System.Windows.Controls.TextBlock>代わりにします。  
  
 この場合は、text プロパティを設定するこれら&2; つの方法を説明する次のマークアップ サンプル、 <xref:System.Windows.Controls.TextBlock.FontWeight%2A>プロパティ。  
  
 [!code-xml[Performance#PerformanceSnippet12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]  
  
 次の表に、1000 を表示するのにかかるコスト<xref:System.Windows.Controls.TextBlock>オブジェクトとそうでない明示的な<xref:System.Windows.Documents.Run>します。  
  
|**TextBlock 型**|**作成時間 (ミリ秒)**|**レンダリング時間 (ミリ秒)**|  
|------------------------|------------------------------|----------------------------|  
|テキストのプロパティの設定を実行します。|146|540|  
|TextBlock の text プロパティの設定|43|453|  
  
### <a name="avoid-databinding-to-the-labelcontent-property"></a>Label.Content プロパティへのデータ バインドを避ける  
 存在するシナリオを想像してみてください、<xref:System.Windows.Controls.Label>から頻繁に更新されるオブジェクト、<xref:System.String>ソース。 ときにデータ バインド、<xref:System.Windows.Controls.Label>要素の<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティを<xref:System.String>ソース オブジェクト、パフォーマンスの低下が発生する可能性があります。 たびに、ソース<xref:System.String>が更新されると、古い<xref:System.String>オブジェクトが破棄され、新しい<xref:System.String>が再作成されます: ため、<xref:System.String>オブジェクトは変更できない、変更することはできません。 これにより、 <xref:System.Windows.Controls.ContentPresenter>の<xref:System.Windows.Controls.Label>オブジェクトの古い内容を破棄し、新しい表示を新しいコンテンツを再生成<xref:System.String>します。  
  
 この問題の解決策は単純です。 場合、<xref:System.Windows.Controls.Label>カスタムに設定されていない<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>値で置き換えます、<xref:System.Windows.Controls.Label>で、 <xref:System.Windows.Controls.TextBlock>とデータ バインド、<xref:System.Windows.Controls.TextBlock.Text%2A>プロパティをソース文字列にします。  
  
|**データ バインドされたプロパティ**|**更新時間 (ミリ秒)**|  
|-----------------------------|----------------------------|  
|Label.Content|835|  
|TextBlock.Text|242|  
  
<a name="Hyperlink"></a>   
## <a name="hyperlink"></a>ハイパーリンク  
 <xref:System.Windows.Documents.Hyperlink>オブジェクトがインライン レベルのフロー コンテンツ要素フロー コンテンツ内のハイパーリンクをホストすることができます。  
  
### <a name="combine-hyperlinks-in-one-textblock-object"></a>1 つの TextBlock オブジェクト内のハイパーリンクを結合します。  
 複数の使用を最適化する<xref:System.Windows.Documents.Hyperlink>要素内で同じ化する<xref:System.Windows.Controls.TextBlock>します。 これで、アプリケーションを作成するオブジェクトの数を最小限に抑えるのに役立ちます。 たとえば、次のような複数のハイパーリンクを表示します。  
  
 MSN ホーム |MSN  
  
 次のマークアップの例に示します複数<xref:System.Windows.Controls.TextBlock>ハイパーリンクを表示するための要素。  
  
 [!code-xml[Performance#PerformanceSnippet9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]  
  
 次のマークアップの例を表示するハイパーリンク、今回は、1 つを使用してより効率的な方法について説明<xref:System.Windows.Controls.TextBlock>:  
  
 [!code-xml[Performance#PerformanceSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]  
  
### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>MouseEnter イベントにのみハイパーリンクに下線を表示  
 A <xref:System.Windows.TextDecoration>オブジェクトがビジュアルの装飾のテキストに追加することができます。 ただし、パフォーマンスをインスタンス化する処理を要するがあります。 広範な利用を加えた場合<xref:System.Windows.Documents.Hyperlink>など、イベントをトリガーする場合にのみ下線を表示、要素を検討、 <xref:System.Windows.ContentElement.MouseEnter>イベントです。 詳細については、次を参照してください。[を指定するかどうか、ハイパーリンクに下線が引かれた](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)です。  
  
 ![TextDecorations を表示します。](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")  
MouseEnter に表示されるハイパーリンク  
  
 次のマークアップのサンプルでは、<xref:System.Windows.Documents.Hyperlink>下線の有無を定義します。  
  
 [!code-xml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 次の表には、1000 を表示するパフォーマンス コストが示されます。<xref:System.Windows.Documents.Hyperlink>かつ下線のない要素です。  
  
|**ハイパーリンク**|**作成時間 (ミリ秒)**|**レンダリング時間 (ミリ秒)**|  
|-------------------|------------------------------|----------------------------|  
|下線付きで|289|1130|  
|下線なし|299|776|  
  
<a name="Text_Formatting_Features"></a>   
## <a name="text-formatting-features"></a>テキストの書式設定機能  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]リッチ テキスト形式の自動ハイフネーションが行わなどのサービスを提供します。 これらのサービスでは、アプリケーションのパフォーマンスに影響を与える可能性があり、必要な場合にのみ使用します。  
  
### <a name="avoid-unnecessary-use-of-hyphenation"></a>ハイフネーションの不要な使用を避ける  
 自動ハイフネーション、テキストの行のハイフンのブレークポイントを検索し、内の行の追加の改行位置ことができます<xref:System.Windows.Controls.TextBlock>と<xref:System.Windows.Documents.FlowDocument>オブジェクトです。 既定では、自動ハイフネーション機能は、これらのオブジェクトで無効になります。 オブジェクトの IsHyphenationEnabled プロパティを設定してこの機能を有効にすることができます`true`します。 しかし、この機能を有効にすると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を開始する[!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]相互運用性、アプリケーションのパフォーマンスに影響を与えることができます。 必要な場合は、ハイフネーションを使用しないことをお勧めします。  
  
### <a name="use-figures-carefully"></a>図表を慎重に使用します。  
 A<xref:System.Windows.Documents.Figure>要素がコンテンツのページ内で絶対位置は、フロー コンテンツの一部を示します。 場合によって、<xref:System.Windows.Documents.Figure>されていなかったり、既にコンテンツとの位置が衝突する場合に自動的に再フォーマットをページ全体が発生する可能性があります。 グループ化して、不要な再フォーマットの可能性を最小限に抑えることができます<xref:System.Windows.Documents.Figure>固定ページ サイズのシナリオでのコンテンツの最上部の宣言、または横にある要素。  
  
### <a name="optimal-paragraph"></a>段落の最適化  
 段落の最適化機能、 <xref:System.Windows.Documents.FlowDocument>空白をできる限り均等に分散されるように、オブジェクトが段落をレイアウトします。 既定では、段落の最適化機能は無効です。 この機能を有効にするには、オブジェクトのできます<xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A>プロパティを`true`します。 ただし、この機能を有効にすると、アプリケーションのパフォーマンスが影響します。 必要な場合は、段落の最適化機能を使用しないことをお勧めします。  
  
## <a name="see-also"></a>関連項目  
 [WPF アプリケーションのパフォーマンスを最適化します。](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [アプリケーションのパフォーマンスの計画](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [ハードウェアの活用](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [レイアウトとデザイン](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [2D グラフィックスとイメージング](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [オブジェクトの動作](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [アプリケーション リソース](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [データ バインディング](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [その他のパフォーマンスの推奨事項](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)