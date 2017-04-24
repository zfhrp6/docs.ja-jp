---
title: "フロー ドキュメントの概要 | Microsoft Docs"
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
  - "コンテンツ スキーマ"
  - "ドキュメント, フロー ドキュメント"
  - "フロー コンテンツ要素 [WPF], フロー ドキュメント"
  - "フロー ドキュメント"
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
caps.latest.revision: 39
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# フロー ドキュメントの概要
フロー ドキュメントは、表示と読みやすさを最適化するように設計されたドキュメントです。  フロー ドキュメントは、1 つの定義済みのレイアウトに設定するのではなく、ウィンドウのサイズ、デバイスの解像度、省略可能なユーザー設定など、ランタイム変数に基づいてコンテンツを動的に調整したり再配置したりします。  また、フロー ドキュメントは、改ページ位置の自動修正や列などの高度なドキュメント機能を提供します。  ここでは、フロー ドキュメントの概要およびフロー ドキュメントの作成方法について説明します。  
  
   
  
<a name="what_is_a_flow_document"></a>   
## フロー ドキュメントとは  
 フロー ドキュメントは、ウィンドウ サイズ、デバイスの解像度、およびその他の環境変数に応じて "コンテンツを再配置" するために設計されています。  また、フロー ドキュメントには、検索、読みやすさを最適化するモードの表示、およびフォントのサイズと外観を変更する機能を含むさまざまな組み込み済みの機能があります。  フロー ドキュメントは、主なドキュメントの使用シナリオが読みやすさである場合に最適です。  これに対し、固定ドキュメントは、静的なプレゼンテーションを行うように設計されています。  ソース コンテンツの忠実性が重要である場合は、固定ドキュメントが適しています。  各種ドキュメントの詳細については、「[WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)」を参照してください。  
  
 さまざまなサイズの複数のウィンドウで表示されるサンプルのフロー ドキュメントを次の図に示します。  表示領域が変わると、コンテンツはスペースを最大限に利用できるように再配置されます。  
  
 ![フロー ドキュメントの内容のフロー変更](../../../../docs/framework/wpf/advanced/media/edocs-flowdocument.png "eDocs\_FlowDocument")  
  
 上のイメージに示すように、フロー コンテンツには、段落、リスト、図などの複数のコンポーネントを含めることができます。  これらのコンポーネントは、マークアップでの要素と手順コードでのオブジェクトに対応します。  これらのクラスの詳細については、この概要の「[フロー関連のクラス](#flow_related_classes)」でもう一度説明します。  ここでは、太字テキストとリストが含まれている段落で構成されているフロー ドキュメントを作成する単純なコード例を示します。  
  
 [!code-xml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 次の図は、このコード スニペットの結果を示したものです。  
  
 ![スクリーンショット: 表示される FlowDocument の例](../../../../docs/framework/wpf/advanced/media/flow-ovw-first-example.png "Flow\_Ovw\_First\_Example")  
  
 この例では、<xref:System.Windows.Controls.FlowDocumentReader> コントロールはフロー コンテンツをホストするために使用されています。  コントロールをホストしているフロー コンテンツの詳細については、「[フロー ドキュメントの種類](#flow_document_types)」を参照してください。  <xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.List>、<xref:System.Windows.Documents.ListItem>、および <xref:System.Windows.Documents.Bold> 要素は、マークアップでの順序に基づいて、コンテンツの書式設定を制御するために使用されます。  たとえば、<xref:System.Windows.Documents.Bold> 要素は、段落内のテキストの部分のみにまたがっています。結果として、その部分のみが太字のテキストになります。  HTML を使用したことがある場合、これは慣れ親しまれているでしょう。  
  
 上の図が示すように、フロー ドキュメントには、いくつかの機能が組み込まれています。  
  
-   検索 : ユーザーがドキュメント全体のフルテキスト検索を実行できるようにします。  
  
-   表示モード : ユーザーは、単一ページ \(一度に 1 ページ\) 表示モード、2 ページ \(読書形式\) 表示モード、および連続したスクロール \(ボトムレス\) 表示モードなど、各自に適切な表示モードを選択できます。  これらの表示モードの詳細については、<xref:System.Windows.Controls.FlowDocumentReaderViewingMode> を参照してください。  
  
-   ページ ナビゲーション コントロール : ドキュメントの表示モードでページを使用する場合、ページ ナビゲーション コントロールには、次のページへのジャンプ用ボタン \(下向き矢印\)、前のページへのジャンプ用ボタン \(上向き矢印\)、および現在のページ番号と総ページ数のインジケーターが含まれます。  ページ間の移動は、キーボードの方向キーを使用して行うこともできます。  
  
-   ズーム : ユーザーはプラス \(\+\) ボタンまたはマイナス \(\-\) ボタンをクリックして、ズーム レベルを上げたり下げたりできます。  ズーム コントロールには、ズーム レベルの調整用スライダーも含まれます。  詳細については、「<xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>」を参照してください。  
  
 これらの機能は、フロー コンテンツをホストするために使用されるコントロールに基づいて変更できます。  次のセクションでは、さまざまなコントロールについて説明します。  
  
<a name="flow_document_types"></a>   
## フロー ドキュメントの種類  
 フロー ドキュメント コンテンツの表示、およびそれがどのように表示されるかは、どのようなオブジェクトがフロー コンテンツをホストするために使用されるかに依存します。  <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>、<xref:System.Windows.Controls.RichTextBox>、および <xref:System.Windows.Controls.FlowDocumentScrollViewer> の 4 つのコントロールがフロー コンテンツの表示をサポートします。  これらのコントロールについて、以下に簡単に説明します。  
  
 **メモ :**  <xref:System.Windows.Documents.FlowDocument> はフロー コントロールを直接ホストするために必要であるため、これらのすべての表示コントロールでは <xref:System.Windows.Documents.FlowDocument> を使用してフロー コンテンツのホストを可能にします。  
  
### FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> には、単一ページ \(一度に 1 ページ\) 表示モード、2 ページ \(読書形式\) 表示モード、連続スクロール \(ボトムレス\) 表示モードなど、さまざまな表示モードをユーザーが動的に選択できるようにするための機能が用意されています。  これらの表示モードの詳細については、<xref:System.Windows.Controls.FlowDocumentReaderViewingMode> を参照してください。  表示モードを動的に切り替える必要がない場合は、<xref:System.Windows.Controls.FlowDocumentPageViewer> および <xref:System.Windows.Controls.FlowDocumentScrollViewer> を使用すると便利です。これらは、特定の表示モードに固定された軽量のコンテンツ ビューアーです。  
  
### FlowDocumentPageViewer と FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> は、コンテンツを一度に 1 ページずつ表示し、<xref:System.Windows.Controls.FlowDocumentScrollViewer> はコンテンツを連続したスクロール モードで表示します。  <xref:System.Windows.Controls.FlowDocumentPageViewer> および <xref:System.Windows.Controls.FlowDocumentScrollViewer> は、いずれも特定の表示モードに固定されています。  <xref:System.Windows.Controls.FlowDocumentReader> と比較してください。このリーダーでは、<xref:System.Windows.Controls.FlowDocumentReaderViewingMode> 列挙体により各種表示モードを動的に切り替えることができますが、<xref:System.Windows.Controls.FlowDocumentPageViewer> や <xref:System.Windows.Controls.FlowDocumentScrollViewer> よりも多くのリソースを消費します。  
  
 既定では、垂直スクロール バーは常に表示され、水平スクロール バーは必要に応じて表示されます。  <xref:System.Windows.Controls.FlowDocumentScrollViewer> の既定の UI にはツール バーが含まれませんが、<xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> プロパティを使用して組み込みツール バーを有効にできます。  
  
### RichTextBox  
 ユーザーがフロー コンテンツを編集できるようにする場合は、<xref:System.Windows.Controls.RichTextBox> を使用します。  たとえば、表、斜体や太字の書式設定などをユーザーが操作できるようにするエディターを作成する必要がある場合は、<xref:System.Windows.Controls.RichTextBox> を使用します。  詳細については、「[RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)」を参照してください。  
  
 **メモ :** <xref:System.Windows.Controls.RichTextBox> 内のフロー コンテンツの動作は、他のコントロールに格納されたフロー コンテンツの動作とは異なる場合があります。  たとえば、<xref:System.Windows.Controls.RichTextBox> 内には列が存在しないため、自動サイズ変更動作もありません。  また、検索、表示モード、ページ ナビゲーション、およびズームなどのフロー コンテンツの通常の組み込み機能も、<xref:System.Windows.Controls.RichTextBox> 内では使用できません。  
  
<a name="creating_flow_content"></a>   
## フロー コンテンツの作成  
 フロー コンテンツは、テキスト、イメージ、テーブル、およびコントロールのような <xref:System.Windows.UIElement> 派生クラスを含むさまざまな要素で構成された複雑になものにすることができます。  複雑なフロー コンテンツを作成する方法を理解するには、次の点が重要です。  
  
-   **フロー関連のクラス** : フロー コンテンツ内で使用される各クラスには特定の目的があります。  また、フロー クラス間の階層型の関係により、それらがどのように使用されるかが理解しやすくなっています。  たとえば、<xref:System.Windows.Documents.Inline> から派生したクラスは表示されるオブジェクトを格納しますが、<xref:System.Windows.Documents.Block> クラスから派生したクラスは他のオブジェクトを格納するために使用されます。  
  
-   **コンテンツ スキーマ** : フロー ドキュメントには、多くの入れ子になった要素が必要になる場合があります。  コンテンツ スキーマは、使用可能な要素間の親子のリレーションシップを指定します。  
  
 以下のセクションでは、これらの点のそれぞれについて詳しく説明します。  
  
<a name="flow_related_classes"></a>   
## フロー関連のクラス  
 次の図は、フロー コンテンツで最も一般的に使用されるオブジェクトを示します。  
  
 ![ダイアグラム: フロー コンテンツ要素クラス階層](../../../../docs/framework/wpf/advanced/media/flow-class-hierarchy.png "Flow\_Class\_Hierarchy")  
  
 フロー コンテンツのために、2 つの重要なカテゴリがあります。  
  
1.  **Block の派生クラス** : "Block コンテンツ要素" または単に "Block 要素" とも呼ばれます。  <xref:System.Windows.Documents.Block> を継承する要素は、要素を共通の親の下にグループ化したり、共通の属性をグループに適用したりするために使用できます。  
  
2.  **Inline の派生クラス** : "Inline コンテンツ要素" または単に "Inline 要素" とも呼ばれます。  <xref:System.Windows.Documents.Inline> から継承する要素は、Block 要素または別の Inline 要素内に格納されます。  Inline 要素は、多くの場合、画面にレンダリングされるコンテンツの直接のコンテナーとして使用されます。  たとえば、<xref:System.Windows.Documents.Paragraph> \(Block 要素\) には <xref:System.Windows.Documents.Run> \(Inline 要素\) を格納することができますが、<xref:System.Windows.Documents.Run> には実際には画面にレンダリングされるテキストが格納されます。  
  
 これらの 2 つのカテゴリの各クラスについて、以下に簡単に説明します。  
  
### Block の派生クラス  
 **Paragraph**  
  
 <xref:System.Windows.Documents.Paragraph> は、通常、コンテンツを 1 つの段落にグループ化するために使用されます。  Paragraph の最も単純かつ一般的な用途は、テキストの段落の作成です。  
  
 [!code-xml[FlowOvwSnippets_snip#ParagraphExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 ただし、次に示すように、他の Inline の派生要素を格納することもできます。  
  
 **セクション**  
  
 <xref:System.Windows.Documents.Section> は、他の <xref:System.Windows.Documents.Block> の派生要素を格納するためにのみ使用されます。  格納している要素に対して、既定の書式設定を適用することはありません。  ただし、<xref:System.Windows.Documents.Section> で設定されたプロパティ値は、その子要素に適用されます。  セクションでは、プログラムで子コレクションを反復処理することもできます。  <xref:System.Windows.Documents.Section> は、HTML の \<DIV\> タグと同じように使用されます。  
  
 次の例では、3 つの段落は、1 つの <xref:System.Windows.Documents.Section> で定義されます。  このセクションには、<xref:System.Windows.Documents.TextElement.Background%2A> プロパティ値である Red があるため、段落の背景色も赤になります。  
  
 [!code-xml[FlowOvwSnippets_snip#SectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> は、<xref:System.Windows.UIElement> 要素 \(  <xref:System.Windows.Controls.Button> など\) を Block の派生フロー コンテンツに埋め込むことができるようにします。  <xref:System.Windows.Documents.InlineUIContainer> \(以下を参照\) は Inline の派生フロー コンテンツに <xref:System.Windows.UIElement> 要素を埋め込むために使用されます。  <xref:System.Windows.Documents.BlockUIContainer> および <xref:System.Windows.Documents.InlineUIContainer> は、これらの 2 つの要素のいずれかの中に格納されない限り、フロー コンテンツで <xref:System.Windows.UIElement> を使用する方法は他にないため重要です。  
  
 <xref:System.Windows.Documents.BlockUIContainer> 要素を使用してフロー コンテンツ内に <xref:System.Windows.UIElement> オブジェクトをホストする方法を次の例に示します。  
  
 [!code-xml[SpanSnippets#_BlockUIXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーンショット: フロー コンテンツに埋め込まれた UIElement](../../../../docs/framework/wpf/advanced/media/blockuicontainer.png "BlockUIContainer")  
  
 **リスト**  
  
 <xref:System.Windows.Documents.List> は、箇条書きリストまたは番号リストを作成するために使用されます。  <xref:System.Windows.Documents.List.MarkerStyle%2A> プロパティを <xref:System.Windows.TextMarkerStyle> 列挙値に設定して、リストのスタイルを決定します。  簡単なリストを作成する方法を次の例に示します。  
  
 [!code-xml[FlowOvwSnippets_snip#ListExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **メモ :** <xref:System.Windows.Documents.List> だけが <xref:System.Windows.Documents.ListItemCollection> を使用して子要素を管理するフロー要素です。  
  
 **テーブル**  
  
 <xref:System.Windows.Documents.Table> は、テーブルを作成するために使用されます。  <xref:System.Windows.Documents.Table> は、<xref:System.Windows.Controls.Grid> 要素と似ていますが、より多くの機能を備えています。そのため、さらに多くのリソースのオーバーヘッドを必要とします。  <xref:System.Windows.Controls.Grid> は <xref:System.Windows.UIElement> であるため、<xref:System.Windows.Documents.BlockUIContainer> または <xref:System.Windows.Documents.InlineUIContainer> に格納されない限り、フロー コンテンツで使用できません。  <xref:System.Windows.Documents.Table> の詳細については、「[テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)」を参照してください。  
  
### Inline の派生クラス  
 **\[実行\]**  
  
 <xref:System.Windows.Documents.Run> は、書式なしテキストを格納するために使用されます。  フロー コンテンツでは <xref:System.Windows.Documents.Run> オブジェクトを広範に使用することを想定している場合がありますが、  マークアップでは <xref:System.Windows.Documents.Run> 要素を明示的に使用する必要はありません。  <xref:System.Windows.Documents.Run> は、コードを使用してフロー ドキュメントを作成または操作するときに使用する必要があります。  たとえば、次のマークアップでは、最初の <xref:System.Windows.Documents.Paragraph> は <xref:System.Windows.Documents.Run> 要素を明示的に指定しますが、2 番目の Paragraph は Run 要素を明示的に指定しません。  両方の段落は、同じ出力を生成します。  
  
 [!code-xml[FlowOvwSnippets_snip#RunExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **メモ:** [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] 以降では、<xref:System.Windows.Documents.Run> オブジェクトの <xref:System.Windows.Documents.Run.Text%2A> プロパティは依存関係プロパティです。  <xref:System.Windows.Documents.Run.Text%2A> プロパティを <xref:System.Windows.Controls.TextBlock> などのデータ ソースにバインドできます。  <xref:System.Windows.Documents.Run.Text%2A> プロパティは、一方向のバインディングを完全にサポートしています。  また、<xref:System.Windows.Documents.Run.Text%2A> プロパティは、<xref:System.Windows.Controls.RichTextBox> を除く双方向のバインディングもサポートしています。  例については、<xref:System.Windows.Documents.Run.Text%2A?displayProperty=fullName> のトピックを参照してください。  
  
 **Span**  
  
 <xref:System.Windows.Documents.Span> は他のインライン コンテンツ要素をグループ化します。  継承されたレンダリングは、<xref:System.Windows.Documents.Span> 要素内のコンテンツには適用されません。  ただし、<xref:System.Windows.Documents.Hyperlink>、<xref:System.Windows.Documents.Bold>、<xref:System.Windows.Documents.Italic>、および <xref:System.Windows.Documents.Underline> を含む <xref:System.Windows.Documents.Span> から継承する要素は、テキストに書式設定を適用します。  
  
 テキスト、<xref:System.Windows.Documents.Bold> 要素、および <xref:System.Windows.Controls.Button> を含むインライン コンテンツを格納するために使用されている <xref:System.Windows.Documents.Span> の例を次に示します。  
  
 [!code-xml[FlowOvwSnippets_snip#SpanExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 次のスクリーンショットは、この例がどのようにレンダリングされるかを示しています。  
  
 ![スクリーンショット: 表示される Span の例](../../../../docs/framework/wpf/advanced/media/flow-spanexample.png "Flow\_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> は、<xref:System.Windows.UIElement> 要素 \(  <xref:System.Windows.Controls.Button> のようなコントロール\) を <xref:System.Windows.Documents.Inline> コンテンツ要素に埋め込むことができるようにします。  この要素は、前に説明した <xref:System.Windows.Documents.BlockUIContainer> と等価のインラインです。  <xref:System.Windows.Documents.Paragraph> に <xref:System.Windows.Controls.Button> インラインを挿入するために <xref:System.Windows.Documents.InlineUIContainer> を使用する例を次に示します。  
  
 [!code-xml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **メモ :** <xref:System.Windows.Documents.InlineUIContainer> は、マークアップでは明示的に使用する必要はありません。  これを省略した場合、コードがコンパイルされると <xref:System.Windows.Documents.InlineUIContainer> が作成されます。  
  
 ****Figure および Floater****  
  
 <xref:System.Windows.Documents.Figure> および <xref:System.Windows.Documents.Floater> は、主要コンテンツ フローとは別にカスタマイズできる配置プロパティを持つフロー ドキュメント内にコンテンツを埋め込むために使用されます。  多くの場合、<xref:System.Windows.Documents.Figure> 要素または <xref:System.Windows.Documents.Floater> 要素は、コンテンツの一部を強調表示したり目立たせたりするため、コンテンツのメイン フロー内のサポート イメージや他のコンテンツをホストするため、または広告などの関連の薄いコンテンツを挿入するために使用されます。  
  
 テキストの段落に <xref:System.Windows.Documents.Figure> を埋め込む方法を次の例に示します。  
  
 [!code-xml[FlowOvwSnippets_snip#FigureExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーンショット: 図形の例](../../../../docs/framework/wpf/advanced/media/flow-ovw-figure-example.png "Flow\_Ovw\_Figure\_Example")  
  
 <xref:System.Windows.Documents.Figure> と <xref:System.Windows.Documents.Floater> にはいくつか違いがあり、それぞれ異なる場面で使用されます。  
  
 ****Figure:****  
  
-   配置可能です。水平方向および垂直方向のアンカーを設定することによって、ページ、コンテンツ、列、または段落に対して相対的にドッキングできます。  <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> プロパティおよび <xref:System.Windows.Documents.Figure.VerticalOffset%2A> プロパティを使用して、任意のオフセットを指定することもできます。  
  
-   複数の列にまたがるサイズ指定が可能です。<xref:System.Windows.Documents.Figure> の高さと幅は、ページ、コンテンツ、または列の高さや幅の倍数に設定できます。  ページおよびコンテンツの場合は、1 より大きい倍数は指定できない点に注意してください。  たとえば、<xref:System.Windows.Documents.Figure> の幅を「0.5 ページ」、「0.25 コンテンツ」、「2 列」のように設定できます。  高さと幅は、絶対ピクセル値で指定することもできます。  
  
-   改ページ位置の自動修正は行いません。<xref:System.Windows.Documents.Figure> の内側のコンテンツが <xref:System.Windows.Documents.Figure> 内に収まらない場合は、収まる部分のみが表示され、残りの部分は失われます。  
  
 ****Floater:****  
  
-   位置の指定はできず、必要なスペースを確保できる場所に描画されます。  <xref:System.Windows.Documents.Floater> のオフセットやアンカーを設定することはできません。  
  
-   複数の列にまたがるサイズ指定はできません。<xref:System.Windows.Documents.Floater> の既定サイズは 1 列です。  絶対ピクセル値で指定できる <xref:System.Windows.Documents.Floater.Width%2A> プロパティがありますが、設定値が 1 列の幅より大きいと無視されるため、その場合の浮遊要素のサイズは 1 列になります。  正しいピクセル幅を設定することによってサイズを 1 列未満にすることはできますが、列を基準とした相対的なサイズ指定はできないため、<xref:System.Windows.Documents.Floater> の幅に関しては "0.5 列" という表現は有効ではありません。  <xref:System.Windows.Documents.Floater> には高さのプロパティはなく、高さを設定することはできません。高さはコンテンツに依存します。  
  
-   <xref:System.Windows.Documents.Floater> は改ページ位置の自動修正を行います。指定した幅のコンテンツが複数列の高さまで拡張されると、浮遊要素は分割されて、次の列、次のページなどに改ページ位置が自動修正されます。  
  
 <xref:System.Windows.Documents.Figure> は、サイズや位置の制御が求められ、指定サイズに収まることが確実な単体のコンテンツを配置する場合に適しています。  <xref:System.Windows.Documents.Floater> は、メイン ページのコンテンツと同様にフローする流動性の高いコンテンツを、メイン ページのコンテンツとは別に配置する場合に適しています。  
  
 ****LineBreak****  
  
 <xref:System.Windows.Documents.LineBreak> はフロー コンテンツの改行の原因となります。  次の例は <xref:System.Windows.Documents.LineBreak> の使い方を示しています。  
  
 [!code-xml[FlowOvwSnippets_snip#LineBreakExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 次のスクリーンショットは、この例がどのようにレンダリングされるかを示しています。  
  
 ![スクリーンショット: LineBreak の例](../../../../docs/framework/wpf/advanced/media/flow-ovw-linebreakexample.png "Flow\_Ovw\_LineBreakExample")  
  
### フロー コレクションの要素  
 上記の例の多くでは、プログラムでフロー コンテンツを構築するために <xref:System.Windows.Documents.BlockCollection> および <xref:System.Windows.Documents.InlineCollection> が使用されています。  たとえば、要素を <xref:System.Windows.Documents.Paragraph> に追加するには、次の構文を使用できます。  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 これは、<xref:System.Windows.Documents.Run> を <xref:System.Windows.Documents.Paragraph> の <xref:System.Windows.Documents.InlineCollection> に追加します。  これは、マークアップの <xref:System.Windows.Documents.Paragraph> の内部にある暗黙の <xref:System.Windows.Documents.Run> と同じです。  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 <xref:System.Windows.Documents.BlockCollection> の使用例として、次の例では、新しい <xref:System.Windows.Documents.Section> を作成してから、**Add** メソッドを使用して新しい <xref:System.Windows.Documents.Paragraph> を <xref:System.Windows.Documents.Section> コンテンツに追加します。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 フロー コレクションへの項目の追加に加えて、項目を削除できます。  次の例では、<xref:System.Windows.Documents.Span> 内の最後の <xref:System.Windows.Documents.Inline> 要素を削除します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 次の例では、<xref:System.Windows.Documents.Span> からすべての内容 \(<xref:System.Windows.Documents.Inline> 要素\) を消去します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 フロー コンテンツをプログラムによって操作する場合、これらのコレクションを広く活用する可能性があります。  
  
 フロー要素が子要素を格納するために <xref:System.Windows.Documents.InlineCollection> \(インライン\) または <xref:System.Windows.Documents.BlockCollection> \(ブロック\) を使用するかどうかは、親が格納できる子要素の種類 \(<xref:System.Windows.Documents.Block> または <xref:System.Windows.Documents.Inline>\) によって異なります。  フロー コンテンツ要素の格納規則については、次のセクションのコンテンツ スキーマで説明します。  
  
 **メモ :** フロー コンテンツと共に使用されるコレクションの 3 つ目の種類は <xref:System.Windows.Documents.ListItemCollection> ですが、このコレクションは <xref:System.Windows.Documents.List> と共にしか使用されません。  また、<xref:System.Windows.Documents.Table> と共に使用されるいくつかのコレクションがあります。  詳細については、「[テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)」を参照してください。  
  
<a name="content_schema"></a>   
## コンテンツ スキーマ  
 多数のさまざまなフロー コンテンツ要素が指定されると、要素が格納できる子要素の種類を追跡できなくなる可能性があります。  フロー要素の格納規則をまとめたものを次の図に示します。  矢印は、使用可能な親子のリレーションシップを表します。  
  
 ![ダイアグラム: フロー コンテンツ コンテインメント スキーマ](../../../../docs/framework/wpf/advanced/media/flow-content-schema.png "Flow\_Content\_Schema")  
  
 上の図からわかるように、要素で許容される子は、必ずしもそれが <xref:System.Windows.Documents.Block> 要素と <xref:System.Windows.Documents.Inline> 要素のどちらであるかによって決まるわけではありません。  たとえば、<xref:System.Windows.Documents.Span> \(<xref:System.Windows.Documents.Inline> 要素\) は <xref:System.Windows.Documents.Inline> 子要素だけを持つことができるのに対し、<xref:System.Windows.Documents.Figure> \(同じく <xref:System.Windows.Documents.Inline> 要素\) は <xref:System.Windows.Documents.Block> 子要素だけを持つことができます。  そのため、どの要素を別の要素に含めることができるかをすばやく判断するには、図が役立ちます。  例として、<xref:System.Windows.Controls.RichTextBox> のフロー コンテンツを構築する方法を、上の図を使用して判断してみましょう。  
  
 **1.** <xref:System.Windows.Controls.RichTextBox> は <xref:System.Windows.Documents.FlowDocument> を含んでいる必要があり、<xref:System.Windows.Documents.FlowDocument> は <xref:System.Windows.Documents.Block> の派生オブジェクトを含んでいる必要があります。  上の図でこれに対応する部分を次に示します。  
  
 ![ダイアグラム: RichTextBox コンテインメント規則](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough1.png "Flow\_Ovw\_SchemaWalkThrough1")  
  
 この段階では、マークアップは次のようになります。  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.**上の図によると、<xref:System.Windows.Documents.Block> 要素には、<xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.Table>、<xref:System.Windows.Documents.List>、および <xref:System.Windows.Documents.BlockUIContainer> を含む、いくつかの選択肢があります \(図の Block の派生クラスを参照\)。  ここで、<xref:System.Windows.Documents.Table> が必要だとします。  上の図によると、<xref:System.Windows.Documents.Table> は <xref:System.Windows.Documents.TableRowGroup> を含んでおり、これは <xref:System.Windows.Documents.TableRow> 要素を含んでいます。さらにこれは <xref:System.Windows.Documents.TableCell> 要素を含んでおり、これは <xref:System.Windows.Documents.Block> の派生オブジェクトを含んでいます。  上の図で、<xref:System.Windows.Documents.Table> に対応する部分を次に示します。  
  
 ![ダイアグラム: テーブルの親&#47;子スキーマ](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough2.png "Flow\_Ovw\_SchemaWalkThrough2")  
  
 以下は、これに対応するマークアップです。  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaWalkThrough2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.**さらに、<xref:System.Windows.Documents.TableCell> の下にも、1 つ以上の <xref:System.Windows.Documents.Block> 要素が必要です。  簡単にするために、セル内にいくつかのテキストを配置することにします。  これを行うには、<xref:System.Windows.Documents.Paragraph> を <xref:System.Windows.Documents.Run> 要素と組み合わせて使用します。  上の図でこれに対応する部分を次に示します。ここには、<xref:System.Windows.Documents.Paragraph> が <xref:System.Windows.Documents.Inline> 要素を取ることができ、<xref:System.Windows.Documents.Run> \(<xref:System.Windows.Documents.Inline> 要素の 1 つ\) がプレーン テキストのみを取ることができることが示されています。  
  
 ![ダイアグラム: 段落の親&#47;子スキーマ](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough3.png "Flow\_Ovw\_SchemaWalkThrough3")  
  
 ![ダイアグラム: 実行の親&#47;子スキーマ](../../../../docs/framework/wpf/advanced/media/flow-ovw-schemawalkthrough4.png "Flow\_Ovw\_SchemaWalkThrough4")  
  
 以下は、マークアップによる例の全体です。  
  
 [!code-xml[FlowOvwSnippets_snip#SchemaExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## テキストのカスタマイズ  
 通常、テキストは、フロー ドキュメントで最も一般的なコンテンツの種類です。  上で導入されたオブジェクトは、テキストをレンダリングする方法のほとんどの側面を制御するために使用できますが、このセクションで説明されるテキストのカスタマイズ用にその他のメソッドがいくつか存在します。  
  
### 文字装飾  
 文字装飾によって、下線、上線、ベースライン、および取り消し線の効果をテキストに適用できます \(下図を参照\)。  これらの装飾は、<xref:System.Windows.Documents.Inline>、<xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Controls.TextBlock>、および <xref:System.Windows.Controls.TextBox> を含む複数のオブジェクトによって公開される <xref:System.Windows.Documents.Inline.TextDecorations%2A> プロパティを使用して追加されます。  
  
 <xref:System.Windows.Documents.Paragraph> の <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> プロパティを設定する方法を次の例に示します。  
  
 [!code-xml[InlineSnippets#_Paragraph_TextDecXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーンショット: 既定の取り消し線が適用されたテキスト](../../../../docs/framework/wpf/advanced/media/inline-textdec-strike.png "Inline\_TextDec\_Strike")  
  
 次の図は、それぞれ**上線**、**標準**、**下線**の各装飾の表示結果を示しています。  
  
 ![スクリーンショット: TextDecorator の上に線を引く](../../../../docs/framework/wpf/advanced/media/inline-textdec-over.png "Inline\_TextDec\_Over")  
  
 ![スクリーンショット: テキストに対する既定のベースライン効果](../../../../docs/framework/wpf/advanced/media/inline-textdec-base.png "Inline\_TextDec\_Base")  
  
 ![スクリーンショット: 既定の下線が適用されたテキスト](../../../../docs/framework/wpf/advanced/media/inline-textdec-under.png "Inline\_TextDec\_Under")  
  
### タイポグラフィ  
 <xref:System.Windows.Documents.TextElement.Typography%2A> プロパティは、<xref:System.Windows.Documents.TextElement>、<xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Controls.TextBlock>、および <xref:System.Windows.Controls.TextBox> を含むほとんどのフロー関連のコンテンツによって公開されます。  このプロパティは、テキストの文字体裁の特性またはバリエーション \(  小さい大文字か大きい大文字か、上付き文字と下付き文字の作成など\) を制御するために使用されます。  
  
 要素として <xref:System.Windows.Documents.Paragraph> を使用して、<xref:System.Windows.Documents.TextElement.Typography%2A> 属性を設定する方法を次の例に示します。  
  
 [!code-xml[TextElementSnippets#_TextElement_TypogXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーンショット: 変更されたタイポグラフィを含むテキスト](../../../../docs/framework/wpf/advanced/media/textelement-typog.png "TextElement\_Typog")  
  
 既定の文字体裁プロパティを設定した同様の例の表示結果を次の図に示します。  
  
 ![スクリーンショット: 変更されたタイポグラフィを含むテキスト](../../../../docs/framework/wpf/advanced/media/textelement-typog-default.png "TextElement\_Typog\_Default")  
  
 <xref:System.Windows.Controls.TextBox.Typography%2A> プロパティをプログラムによって設定する方法を次の例に示します。  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 文字体裁の詳細については、「[WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)」を参照してください。  
  
## 参照  
 [テキスト](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/flow-content-elements-how-to-topics.md)   
 [TextElement コンテンツ モデルの概要](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)   
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [テーブルの概要](../../../../docs/framework/wpf/advanced/table-overview.md)   
 [注釈の概要](../../../../docs/framework/wpf/advanced/annotations-overview.md)