---
title: "WPF の双方向機能の概要 | Microsoft Docs"
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
  - "双方向機能"
  - "FlowDirection プロパティ"
  - "FlowDocument プロパティ"
  - "Span 要素"
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# WPF の双方向機能の概要
他のどの開発プラットフォームとも異なり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には双方向コンテンツ \(たとえば、同じドキュメント内で左から右へ記述される情報と右から左へ記述される情報が混在している状態\) の迅速な開発をサポートする多数の機能があります。  また [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、アラビア語やヘブライ語を扱うユーザーなど双方向機能を必要とするユーザーにとって、操作性が優れています。  
  
 以降のセクションでは、多数の双方向機能と双方向コンテンツを最適に表示した例について説明します。  この概念は [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] コードまたは [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] コードに容易に適用できますが、ほとんどのサンプルでは [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] を使用します。  
  
   
  
<a name="FlowDirection"></a>   
## FlowDirection  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでのコンテンツのフロー方向を定義する基本プロパティが <xref:System.Windows.FrameworkElement.FlowDirection%2A> です。  このプロパティは 2 つの列挙値のいずれか、つまり <xref:System.Windows.FlowDirection> または <xref:System.Windows.FlowDirection> に設定できます。  このプロパティは、<xref:System.Windows.FrameworkElement> を継承するすべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 要素に対して使用できます。  
  
 以下の例は、<xref:System.Windows.Controls.TextBox> 要素のフロー方向を設定したものです。  
  
 **左から右へ記述するフロー方向**  
  
 [!code-xml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **右から左へ記述するフロー方向**  
  
 [!code-xml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 次の図は、前のコードがどのように表示されるのかを示します。  
  
 **FlowDirection を示す図**  
  
 ![TextBlock 配置](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.png "LefttoRightRighttoLeft")  
  
 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ツリー内の要素が <xref:System.Windows.FrameworkElement.FlowDirection%2A> をそのコンテナーから継承します。  次の例では、<xref:System.Windows.Controls.TextBlock> が、<xref:System.Windows.Window> に存在する <xref:System.Windows.Controls.Grid> 内にあります。  <xref:System.Windows.Window> に対して <xref:System.Windows.FrameworkElement.FlowDirection%2A> を設定することは、<xref:System.Windows.Controls.Grid> と <xref:System.Windows.Controls.TextBlock> に対しても設定することを意味します。  
  
 次の例では、<xref:System.Windows.FrameworkElement.FlowDirection%2A> の設定を示します。  
  
 [!code-xml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 また、最上位の <xref:System.Windows.Window> には <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection> があるため、これに格納されているすべての要素も同じ <xref:System.Windows.FrameworkElement.FlowDirection%2A> を継承します。  要素が指定された <xref:System.Windows.FrameworkElement.FlowDirection%2A> を上書きするためには、前の例で <xref:System.Windows.FlowDirection> に変更された 2 番目の <xref:System.Windows.Controls.TextBlock> などの明示的な方向変更を追加する必要があります。  <xref:System.Windows.FrameworkElement.FlowDirection%2A> が定義されていない場合、既定の <xref:System.Windows.FlowDirection> が適用されます。  
  
 前の例の出力を次の図に示します。  
  
 **明示的に割り当てられた FlowDirection を示す図**  
  
 ![フロー方向の図](../../../../docs/framework/wpf/advanced/media/flowdir.png "FlowDir")  
  
<a name="FlowDocument"></a>   
## FlowDocument  
 [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]、Java などの多数の開発プラットフォームは、双方向コンテンツ開発を特別にサポートしています。  [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] などのマークアップ言語では、コンテンツの作成者が任意の必要な方向にテキストを表示するために必要なマークアップを使用できます。たとえば "rtl" または "ltr" を値として解釈する [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 タグの "dir" などです。  このタグは <xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティに似ていますが、<xref:System.Windows.FrameworkElement.FlowDirection%2A> プロパティはテキスト コンテンツのレイアウトに対する機能がより拡張されていて、テキスト以外のコンテンツでも使用できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、<xref:System.Windows.Documents.FlowDocument> がテキスト、テーブル、イメージ、および他の要素の組み合わせをホストできる、柔軟性のある [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素となります。  以下のセクションのサンプルでは、この要素を使用します。  
  
 <xref:System.Windows.Documents.FlowDocument> へのテキストの追加には、複数の方法があります。  単純な方法は、テキストなどのコンテンツのグループ化に使用するブロック レベル要素の <xref:System.Windows.Documents.Paragraph> を用いることです。  サンプルでは、インライン レベルの要素にテキストを追加するために、<xref:System.Windows.Documents.Span> と <xref:System.Windows.Documents.Run> が使用されています。  <xref:System.Windows.Documents.Span> は他のインライン要素のグループ化に使用されるインライン レベルのフロー コンテンツ要素で、<xref:System.Windows.Documents.Run> は書式設定されていない一連のテキストを格納するためのインライン レベルのフロー コンテンツ要素です。  1 つの <xref:System.Windows.Documents.Span> に、複数の <xref:System.Windows.Documents.Run> 要素を含めることができます。  
  
 最初のドキュメント例には、いくつかのネットワーク共有名 \(たとえば `\\server1\folder\file.ext`\) がある文書が含まれます。  このネットワーク リンクがアラビア語または英語のいずれの文書にあっても、常に同じように表示する必要があります。  次の図は、アラビア語の <xref:System.Windows.FlowDirection> ドキュメントのリンクを示します。  
  
 **Span 要素の使用を示す図**  
  
 ![右から左に読むドキュメント](../../../../docs/framework/wpf/advanced/media/flowdocument.png "FlowDocument")  
  
 テキストは <xref:System.Windows.FlowDirection> であるため、"\\" などのすべての特殊文字でテキストを右から左の順序で区切ります。  この場合、リンクが正しい順序で表示されません。したがって、この問題を解決するためにテキストを埋め込んで、フロー方向が <xref:System.Windows.FlowDirection> の <xref:System.Windows.Documents.Run> を個別に残す必要があります。  言語ごとに <xref:System.Windows.Documents.Run> を作成するのではなく、頻繁には使用しない英語のテキストは大きなアラビア語の <xref:System.Windows.Documents.Span> に埋め込むのがより良い問題の解決法です。  
  
 次の図にこれを示します。  
  
 **Span 要素に埋め込んだ実行要素の使用を示す図**  
  
 ![XamlPad スクリーンショット](../../../../docs/framework/wpf/advanced/media/runspan.png "RunSpan")  
  
 次の例は、<xref:System.Windows.Documents.Run> と <xref:System.Windows.Documents.Span> 要素をドキュメントで使用する方法を示します。  
  
 [!code-xml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## Span 要素  
 <xref:System.Windows.Documents.Span> 要素は、フロー方向が異なるテキストの境界区切り記号の役割を果たします。  フロー方向が同じ <xref:System.Windows.Documents.Span> 要素でも、双方向スコープは異なると見なされます。これは、コンテナーの <xref:System.Windows.FlowDirection> 中で <xref:System.Windows.Documents.Span> 要素が順序付けられているということです。<xref:System.Windows.Documents.Span> 要素内のコンテンツのみが <xref:System.Windows.Documents.Span> の <xref:System.Windows.FlowDirection> に従います。  
  
 次の図は、複数の <xref:System.Windows.Controls.TextBlock> 要素のフロー方向を示します。  
  
 **複数の TextBlock 要素での FlowDirection を示す図**  
  
 ![フロー方向が異なるテキスト ブロック](../../../../docs/framework/wpf/advanced/media/span.png "Span")  
  
 次の例には、前の図で表示された結果を作成するために <xref:System.Windows.Documents.Span> 要素と <xref:System.Windows.Documents.Run> 要素を使用する方法を示します。  
  
 [!code-xml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 サンプルの <xref:System.Windows.Controls.TextBlock> 要素では、<xref:System.Windows.Documents.Span> 要素は親の <xref:System.Windows.FlowDirection> に従って配置されます。ただし、各 <xref:System.Windows.Documents.Span> 要素内のテキストはそれ自体の <xref:System.Windows.FlowDirection> に従って流れます。  これは、ラテン語やアラビア語だけでなく、他のどの言語にも当てはまります。  
  
### xml:lang の追加  
 次の図は、`"200.0+21.4=221.4"` などの番号と算術式を使用する別の例を示します。  <xref:System.Windows.FlowDirection> だけが設定されることに注意してください。  
  
 **FlowDirection のみを使用して数値を表示する図**  
  
 ![右から左に読む数字](../../../../docs/framework/wpf/advanced/media/langattribute.png "LangAttribute")  
  
 残念ながらこのアプリケーションの出力では、<xref:System.Windows.FlowDirection> が正しいにもかかわらず、数字がアラビア数字の形状になりません。  
  
 XAML 要素には、各要素の言語を定義する [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 属性 \(`xml:lang`\) を含めることができます。  また、XAML では、ツリーの親要素に `xml:lang` 値を適用すると、子要素にもその属性が適用されるという [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 言語の原則も遵守されます。  前の例では、<xref:System.Windows.Documents.Run> 要素に対しても、その最上位要素に対しても言語が定義されていないため、`xml:lang` の既定値 \(XAML では `en-US`\) が適用されています。  また、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] の内部数字形成アルゴリズムによって、対応する言語 \(この場合は英語\) の数字が選択されます。  アラビア数字を正しく表示するためには、`xml:lang` を設定する必要があります。  
  
 次の図は、`xml:lang` を追加した例を示しています。  
  
 **xml:lang 属性の使用を示す図**  
  
 ![右から左に読むアラビア数字](../../../../docs/framework/wpf/advanced/media/langattribute2.png "LangAttribute2")  
  
 次の例では、アプリケーションに `xml:lang` が追加されています。  
  
 [!code-xml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 多くの言語では、対象となる地域に応じて異なる `xml:lang` 値があります。たとえば、`"ar-SA"` と `"ar-EG"` はアラビア語の 2 つのバリエーションです。  前の例は、`xml:lang` と <xref:System.Windows.FlowDirection> の両方の値を定義する必要があることを示しています。  
  
<a name="FlowDirectionNontext"></a>   
## 非テキスト要素のある FlowDirection  
 <xref:System.Windows.FlowDirection> は、テキストのテキスト要素内でのフロー方向だけでなく、他のほぼすべての [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素の流れ方も定義します。  次の図は、背景を描画するために、水平 <xref:System.Windows.Media.LinearGradientBrush> で使用する <xref:System.Windows.Controls.ToolBar> を示します。  
  
 **左から右へのグラデーションを付けたツール バーを示す図**  
  
 ![グラデーションのスクリーンショット](../../../../docs/framework/wpf/advanced/media/gradient.png "Gradient")  
  
 <xref:System.Windows.FlowDirection> に <xref:System.Windows.FlowDirection> を設定すると、<xref:System.Windows.Controls.ToolBar> ボタンが右から左に整列されるだけでなく、<xref:System.Windows.Media.LinearGradientBrush> によりそのオフセットが右から左に移動するように調整されます。  
  
 次の図は、再構成された <xref:System.Windows.Media.LinearGradientBrush> を示します。  
  
 **右から左へのグラデーションを付けたツール バーを示す図**  
  
 ![右から左に読むグラデーション](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.png "Gradient2\_WPF")  
  
 <xref:System.Windows.FlowDirection> <xref:System.Windows.Controls.ToolBar> を作成する例を次に示します。  \(左から右に描画するには、<xref:System.Windows.Controls.ToolBar> に対する <xref:System.Windows.FlowDirection> 属性を削除します。  
  
 [!code-xml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### FlowDirection の例外  
 <xref:System.Windows.FlowDirection> が期待どおりに動作しない場合があります。  ここでは、そのような例外を 2 つ取り上げて説明します。  
  
 **Image**  
  
 <xref:System.Windows.Controls.Image> は、イメージを表示するコントロールを表します。  [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] では、表示する <xref:System.Windows.Controls.Image> の [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] を定義する <xref:System.Windows.Controls.Image.Source%2A> プロパティと合わせてこのコントロールを使用できます。  
  
 他の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素とは異なり、<xref:System.Windows.Controls.Image> はコンテナーから <xref:System.Windows.FlowDirection> を継承しません。  ただし、<xref:System.Windows.FlowDirection> が <xref:System.Windows.FlowDirection> に明示的に設定されると、<xref:System.Windows.Controls.Image> は左右反転して表示されます。  これは、双方向コンテンツの開発者にとって便利な機能として実装されています。場合によっては、イメージを左右反転して表示することで必要な効果が得られるためです。  
  
 次の図は、反転された <xref:System.Windows.Controls.Image> を示します。  
  
 **反転されたイメージを示す図**  
  
 ![XamlPad スクリーンショット](../../../../docs/framework/wpf/advanced/media/image.png "Image")  
  
 次の例は、<xref:System.Windows.Controls.Image> が、それが含まれる <xref:System.Windows.Controls.StackPanel> からの <xref:System.Windows.FlowDirection> の継承に失敗することを示します。  **メモ** この例を実行するには、C:\\ ドライブに  **ms logo.jpg** という名前のファイルが必要です。  
  
 [!code-xml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **メモ** ダウンロード ファイルには、**Ms logo.jpg** ファイルが含まれています。  コードは、この .jpg ファイルがプロジェクト内ではなく、C:\\ ドライブ上にあることを前提としています。  プロジェクト内のファイルを検索するためには、プロジェクト ファイルから C:\\ドライブに .jpg をコピーするかコードを変更する必要があります。  これを行うには、`Source="file://c:/ms_logo.jpg"` を `Source="ms_logo.jpg"` に変更します。  
  
 **パス**  
  
 <xref:System.Windows.Controls.Image> のほかに興味深い要素は <xref:System.Windows.Shapes.Path> です。  Pathは、接続された一連の線と曲線を描画できるオブジェクトです。  <xref:System.Windows.FlowDirection> に関しては <xref:System.Windows.Controls.Image> と同様に動作します。たとえば <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection> は <xref:System.Windows.FlowDirection> を水平方向に反転したものです。  ただし、<xref:System.Windows.Controls.Image> とは異なり、<xref:System.Windows.Shapes.Path> は <xref:System.Windows.FlowDirection> をコンテナーから継承し、明示的に指定する必要がありません。  
  
 次の例では、3 本の線を用いて単純な矢印を描画します。  最初の矢印は、始点と終点が右側を起点として計測されるように、<xref:System.Windows.Controls.StackPanel> から <xref:System.Windows.FlowDirection> フロー方向を継承します。  明示的な <xref:System.Windows.FlowDirection> <xref:System.Windows.FlowDirection> を持つ 2 番目の矢印も右側を起点とします。  ただし、3 番目の矢印の起点は左側です。  描画の詳細については、「<xref:System.Windows.Media.LineGeometry>」および「<xref:System.Windows.Media.GeometryGroup>」を参照してください。  
  
 [!code-xml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 前の例の出力を次の図に示します。  
  
 **Path 要素を使用して描画した矢印の図**  
  
 ![パス](../../../../docs/framework/wpf/advanced/media/paths.png "Paths")  
  
 <xref:System.Windows.Controls.Image> と <xref:System.Windows.Shapes.Path> は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] による <xref:System.Windows.FlowDirection> の使用方法を示す 2 つの例です。  <xref:System.Windows.FlowDirection> は、コンテナー内の特定の方向に [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素を配置する他に、サーフェイス上にインクをレンダリングする <xref:System.Windows.Controls.InkPresenter>、<xref:System.Windows.Media.RadialGradientBrush>、および <xref:System.Windows.Media.LinearGradientBrush> などの要素と合わせて使用できます。  左から右への動作を模したコンテンツに対して右から左への動作が必要な場合、またはその逆の場合には、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] を使用すれば可能です。  
  
<a name="NumberSubstitution"></a>   
## 数字代替  
 従来から、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] は、同じ数字をカルチャによって異なる形状で表現できるようにすると同時に、ロケールが異なってもこれらの数字の内部ストレージを統一する \(たとえば、数字をごく一般的な 16 進値である 0x40 や 0x41 で格納しながら、表示は選択された言語で行う\) ことによって、数字代替をサポートしてきました。  
  
 これによって、言語間での変換を行わなくてもアプリケーションが数値を処理することができます。たとえば、ローカライズされたアラビア語 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] の [!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)] スプレッドシートを開いて、アラビア語の形状の数字を表示することができますが、このスプレッドシートを [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] のヨーロッパ言語バージョンで開き同じ数字のヨーロッパ語表現を表示することもできます。  これは、コンマ区切りやパーセント記号などの他の記号でも必要です。これらの記号は、通常同じドキュメント内で数字を伴っているからです。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は引き続きこの機能を備え、代替を用いるタイミングと方法をユーザーがより広く制御できるようにこの機能を改善してゆきます。  この機能はどの言語に対しても有効ですが、アプリケーションが使用されるカルチャが多岐にわたるために特定の言語に合わせて数字の形状を設定することがアプリケーション開発者にとってに問題となる双方向コンテンツに対して特に有用です。  
  
 数字代替の [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] での機能を制御する中核のプロパティは、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A> 依存プロパティです。  <xref:System.Windows.Media.NumberSubstitution> クラスは、テキストでの数字の表示方法を指定します。  動作を定義する 3 つのパブリック プロパティがあります。  以下は、各プロパティの概要です。  
  
 **CultureSource:**  
  
 このプロパティは、数字のカルチャを確認する方法を指定します。  3 つの <xref:System.Windows.Media.NumberCultureSource> 列挙値のいずれかをとります。  
  
-   Override: 数字カルチャは、<xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> プロパティの数字カルチャです。  
  
-   Text: 数字カルチャは、テキスト ランのカルチャです。  マークアップでは、これは `xml:lang`、つまりエイリアスである `Language` プロパティ \(<xref:System.Windows.FrameworkElement.Language%2A> または <xref:System.Windows.FrameworkContentElement.Language%2A>\) です。  <xref:System.Windows.FrameworkContentElement> から派生しているクラスの既定でもあります。  こうしたクラスには、<xref:System.Windows.Documents.Paragraph?displayProperty=fullName>、<xref:System.Windows.Documents.Table?displayProperty=fullName>、<xref:System.Windows.Documents.TableCell?displayProperty=fullName> などが含まれます。  
  
-   User: 数字カルチャは、現在のスレッドのカルチャです。  このプロパティは、<xref:System.Windows.Controls.Page>、<xref:System.Windows.Window>、および <xref:System.Windows.Controls.TextBlock> などの <xref:System.Windows.FrameworkElement> のすべてのサブクラスの既定です。  
  
 **CultureOverride** :  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A> プロパティが使用されるのは <xref:System.Windows.Media.NumberCultureSource> が <xref:System.Windows.Media.NumberSubstitution.CultureSource%2A> プロパティに設定されている場合のみで、それ以外の場合は無視されます。  このプロパティは、数字カルチャを指定します。  既定値である `null` の値は、en\-US として解釈されます。  
  
 **代替** :  
  
 このプロパティは、実行する数字代替の種類を指定します。  次の <xref:System.Windows.Media.NumberSubstitutionMethod> 列挙値のいずれかをとります。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>: 数字カルチャの <xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=fullName> プロパティ値に基づいて代替方法が決定されます。  これは、既定の設定です。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>: 数字カルチャがアラビアまたはペルシアのカルチャである場合に、数字がコンテキストに応じて使用されるように指定します。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>: 数字は常にヨーロッパ数字として描画されます。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>: カルチャの <xref:System.Globalization.CultureInfo.NumberFormat%2A> プロパティで指定された、数字カルチャに対応する国の数字を使って、数字が描画されます。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod>: 数字カルチャの通常の数字を使用して数字を描画することを指定します。  ほとんどのカルチャで、これは <xref:System.Windows.Media.NumberSubstitutionMethod> と同じです。  ただし、<xref:System.Windows.Media.NumberSubstitutionMethod> では一部のアラビア カルチャでラテン数字が表示されますが、Traditional ではすべてのアラビア カルチャでアラビア数字が表示されます。  
  
 これらの値は双方向コンテンツ開発者にとってどういった意味があるのでしょうか。  ほとんどの場合、開発者は <xref:System.Windows.FlowDirection> と各テキスト [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 要素の言語 \(たとえば `Language="ar-SA"`\) を定義するだけでよく、数字の表示は、<xref:System.Windows.Media.NumberSubstitution> ロジックにより、各 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] に応じて行われます。  次の例は、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] のアラビア語版で実行されている [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションでアラビア数字と英語数字を使用する方法を示します。  
  
 [!code-xml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 次の図は、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] のアラビア語版を実行している場合の、前のサンプルの出力を示します。  
  
 **表示されたアラビア数字と英語数字を示す図**  
  
 ![数字を含む XamlPad のスクリーンショット](../../../../docs/framework/wpf/advanced/media/numbers.png "Numbers")  
  
 この場合、代わりに <xref:System.Windows.FlowDirection> に <xref:System.Windows.FlowDirection> を設定するとヨーロッパ数字が生成されていたため、<xref:System.Windows.FlowDirection> が重要でした。  以下のセクションでは、ドキュメント全体で数字の表示を統一する方法について説明します。  この例では、アラビア語版 Windows で実行されていなければ、すべての数字がヨーロッパ数字として表示されます。  
  
 **代替ルールの定義**  
  
 実際のアプリケーションでは、プログラムでの言語設定が必要となる場合があります。  たとえば、`xml:lang` 属性をシステムの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] により使用されている属性と同じものに設定する場合もありますし、アプリケーション状態に応じて言語を変更する場合もあります。  
  
 アプリケーションの状態に基づいて変更を行う場合には、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] が備えている他の機能を使用してください。  
  
 アプリケーション コンポーネントの `NumberSubstitution.CultureSource="Text"` を最初に設定します。  この設定を使用すると、<xref:System.Windows.Controls.TextBlock> などの既定値が "User" であるテキスト要素の [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] から設定が取得されることはありません。  
  
 次に例を示します。  
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 対応する [!INCLUDE[TLA2#tla_lhcshrp](../../../../includes/tla2sharptla-lhcshrp-md.md)] コードで、`Language` プロパティを `"ar-SA"` などに設定します。  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 現在のユーザーの [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 言語に `Language` プロパティを設定する必要がある場合、次のコードを使用します。  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> は、実行時に現在のスレッドによって使用される現在のカルチャを表します。  
  
 最終的な [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] 例は、次の例に似たものになります。  
  
 [!code-xml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 最終的な [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] 例は、次のようなものになります。  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 次の図は、いずれかのプログラミング言語に対するウィンドウの外観を示します。  
  
 **アラビア数字を表示した図**  
  
 ![アラビア数字](../../../../docs/framework/wpf/advanced/media/numbers2.png "Numbers2")  
  
 **Substitution プロパティの使用**  
  
 数字代替の [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] での機能は、テキスト要素の言語と <xref:System.Windows.FlowDirection> の両方によって異なります。  <xref:System.Windows.FlowDirection> が左から右の場合、ヨーロッパ数字が表示されます。  ただし、アラビア語のテキストが前にある場合、または言語が "ar" に設定されており、<xref:System.Windows.FlowDirection> が <xref:System.Windows.FlowDirection> の場合には、代わりにアラビア数字が描画されます。  
  
 ただし、たとえばすべてのユーザーに対してヨーロッパ数字を表示するなどの、統一されたアプリケーションを作成する必要のある場合もあります。  また、特定の <xref:System.Windows.Style> で <xref:System.Windows.Documents.Table> セルにアラビア数字を表示する必要のある場合もあります。  これを行う簡単な方法の 1 つは、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A> プロパティを使用することです。  
  
 次の例で、最初の <xref:System.Windows.Controls.TextBlock> には <xref:System.Windows.Media.NumberSubstitution.Substitution%2A> プロパティ セットがないため、予想されるようにアルゴリズムによってアラビア数字が表示されます。  ただし、2 番目の <xref:System.Windows.Controls.TextBlock> では、代替がヨーロッパ言語に設定されて、既定のアラビア数字への代替がオーバーライドされているため、ヨーロッパ数字が表示されます。  
  
 [!code-xml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]