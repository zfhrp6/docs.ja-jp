---
title: WPF の双方向機能の概要
ms.date: 03/30/2017
helpviewer_keywords:
- Span elements [WPF]
- bidirectional features [WPF]
ms.assetid: fd850e25-7dba-408c-b521-8873e51dc968
ms.openlocfilehash: 7a2af8d7589ed1f0fceea1ba07d6802ffae1bdee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541925"
---
# <a name="bidirectional-features-in-wpf-overview"></a>WPF の双方向機能の概要
その他の開発プラットフォームとは異なり[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]双方向のコンテンツの迅速な開発をサポートする多くの機能にはたとえば、混合の左から右、および右には、同じドキュメント内データを除外します。 同時に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アラビア語やヘブライ語を話すユーザーなどの双方向機能を必要とするユーザーの最良のエクスペリエンスを作成します。  
  
 以降のセクションでは、多数の双方向機能と双方向コンテンツを最適に表示した例について説明します。 ほとんどのサンプルを使用して[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]概念は、c# または Visual Basic コードを簡単に適用できますが、します。  
  

  
<a name="FlowDirection"></a>   
## <a name="flowdirection"></a>FlowDirection  
 コンテンツ フローの方向を定義する基本的なプロパティ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは<xref:System.Windows.FrameworkElement.FlowDirection%2A>します。 このプロパティは、次の 2 つの列挙値のいずれかに設定できます<xref:System.Windows.FlowDirection.LeftToRight>または<xref:System.Windows.FlowDirection.RightToLeft>です。 プロパティがすべて使用できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素から継承する<xref:System.Windows.FrameworkElement>です。  
  
 次の例のフローの方向を設定する、<xref:System.Windows.Controls.TextBox>要素。  
  
 **左から右へ記述するフロー方向**  
  
 [!code-xaml[LTRRTL#LTR](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#ltr)]  
  
 **右から左へ記述するフロー方向**  
  
 [!code-xaml[LTRRTL#RTL](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LTRRTL/CS/Pane1.xaml#rtl)]  
  
 次の図は、前のコードがどのように表示されるのかを示します。  
  
 **FlowDirection を示す図**  
  
 ![TextBlock 配置](../../../../docs/framework/wpf/advanced/media/lefttorightrighttoleft.PNG "LefttoRightRighttoLeft")  
  
 内の要素、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]ツリーは、継承、<xref:System.Windows.FrameworkElement.FlowDirection%2A>コンテナーからです。 次の例で、<xref:System.Windows.Controls.TextBlock>内部にある、<xref:System.Windows.Controls.Grid>に常駐するが、<xref:System.Windows.Window>です。 設定、<xref:System.Windows.FrameworkElement.FlowDirection%2A>の<xref:System.Windows.Window>設定することの意味、<xref:System.Windows.Controls.Grid>と<xref:System.Windows.Controls.TextBlock>もします。  
  
 次の例では、設定<xref:System.Windows.FrameworkElement.FlowDirection%2A>です。  
  
 [!code-xaml[FlowDirection#FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirection/CS/Window1.xaml#flowdirection)]  
  
 最上位レベル<xref:System.Windows.Window>が、 <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>ので、そこに含まれるすべての要素と同じ継承も<xref:System.Windows.FrameworkElement.FlowDirection%2A>します。 指定した要素の<xref:System.Windows.FrameworkElement.FlowDirection%2A>、2 番目など、明示的な方向の変更を追加する必要があります<xref:System.Windows.Controls.TextBlock>を変更する前の例で<xref:System.Windows.FlowDirection.LeftToRight>です。 ない場合<xref:System.Windows.FrameworkElement.FlowDirection%2A>が定義されている既定の<xref:System.Windows.FlowDirection.LeftToRight>適用されます。  
  
 前の例の出力を次の図に示します。  
  
 **明示的に割り当てられた FlowDirection を示す図**  
  
 ![フロー方向の図](../../../../docs/framework/wpf/advanced/media/flowdir.PNG "FlowDir")  
  
<a name="FlowDocument"></a>   
## <a name="flowdocument"></a>FlowDocument  
 などの多くの開発プラットフォーム[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]、[!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]および Java は、双方向のコンテンツの開発の特別なサポートを提供します。 などのマークアップ言語[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]コンテンツ ライターなど、任意の必要な方向にテキストを表示するために必要なマークアップを与える、 [!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)] 4.0 のタグ、"dir"を値として"rtl"または"ltr"を受け取る。 このタグがに似ていますが、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティが、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティがレイアウトのテキスト コンテンツに高度な方法で動作し、テキスト以外のコンテンツに使用できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、<xref:System.Windows.Documents.FlowDocument>は、多様な[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素のテキスト、テーブル、イメージ、およびその他の要素の組み合わせをホストすることができます。 以下のセクションのサンプルでは、この要素を使用します。  
  
 テキストを追加、<xref:System.Windows.Documents.FlowDocument>複数の方法で行うことができます。 これを行う簡単な方法は、使用、<xref:System.Windows.Documents.Paragraph>テキストなどのコンテンツをグループに使用するブロック レベル要素であります。 サンプルを使用してインライン レベル要素にテキストを追加する<xref:System.Windows.Documents.Span>と<xref:System.Windows.Documents.Run>です。 <xref:System.Windows.Documents.Span> その他のインライン要素をグループ化するために使用するインライン レベル フロー コンテンツ要素は、中に、<xref:System.Windows.Documents.Run>インライン レベル フローはコンテンツでは要素の書式なしテキスト ランを格納するためのものです。 A<xref:System.Windows.Documents.Span>複数を含めることができる<xref:System.Windows.Documents.Run>要素。  
  
 ドキュメントの最初の例には、共有名です。 ネットワークの数を持つドキュメントが含まれています。たとえば`\\server1\folder\file.ext`します。 このネットワーク リンクがアラビア語または英語のいずれのドキュメントにあっても、常に同じように表示する必要があります。 次の図は、アラビア語の<xref:System.Windows.FlowDirection.RightToLeft>ドキュメント。  
  
 **Span 要素の使用を示す図**  
  
 ![右から左に読むドキュメント](../../../../docs/framework/wpf/advanced/media/flowdocument.PNG "FlowDocument")  
  
 テキストがあるため<xref:System.Windows.FlowDirection.RightToLeft>、すべての特殊ななどの文字、"\\"、右から左へテキストを区切ります。 そのため、問題を解決するテキスト埋め込む必要がある、個別に保持するためには、正しい順序で表示されていないリンクで、結果を<xref:System.Windows.Documents.Run>フロー<xref:System.Windows.FlowDirection.LeftToRight>です。 個別のではなく<xref:System.Windows.Documents.Run>言語ごとに、問題を解決する優れた方法としては、大規模なアラビア語に使用頻度の低い英語のテキストを埋め込む<xref:System.Windows.Documents.Span>です。  
  
 次の図にこれを示します。  
  
 **Span 要素に埋め込んだ実行要素の使用を示す図**  
  
 ![XamlPad スクリーン ショット](../../../../docs/framework/wpf/advanced/media/runspan.PNG "RunSpan")  
  
 次の例では、使用方法を示します<xref:System.Windows.Documents.Run>と<xref:System.Windows.Documents.Span>ドキュメント内の要素。  
  
 [!code-xaml[RunSpan#RunSpan](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RunSpan/CS/Window1.xaml#runspan)]  
  
<a name="SpanElements"></a>   
## <a name="span-elements"></a>Span 要素  
 <xref:System.Windows.Documents.Span>要素はテキスト フロー方向が異なる間の境界区切り記号として機能します。  でも<xref:System.Windows.Documents.Span>同じフローの方向を持つ要素をことを意味する双方向のさまざまなスコープを持つと見なされます、<xref:System.Windows.Documents.Span>でコンテナーの要素の順序が<xref:System.Windows.FlowDirection>、内のコンテンツのみ、<xref:System.Windows.Documents.Span>要素依存して、<xref:System.Windows.FlowDirection>の<xref:System.Windows.Documents.Span>です。  
  
 次の図は、いくつかのフローの方向を示しています。<xref:System.Windows.Controls.TextBlock>要素。  
  
 **複数の TextBlock 要素での FlowDirection を示す図**  
  
 ![フロー方向が異なるテキスト ブロック](../../../../docs/framework/wpf/advanced/media/span.PNG "Span")  
  
 次の例を使用する方法を示しています、<xref:System.Windows.Documents.Span>と<xref:System.Windows.Documents.Run>上の図に示すように結果を生成する要素。  
  
 [!code-xaml[Span#Span](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Span/CS/Window1.xaml#span)]  
  
 <xref:System.Windows.Controls.TextBlock>サンプルでは、要素、<xref:System.Windows.Documents.Span>要素のレイアウトに従って、<xref:System.Windows.FlowDirection>その親が各内のテキストの<xref:System.Windows.Documents.Span>要素のフローに従って独自<xref:System.Windows.FlowDirection>です。 これは、ラテン語やアラビア語だけでなく、他のどの言語にも当てはまります。  
  
### <a name="adding-xmllang"></a>xml:lang の追加  
 次の図は、番号と算術式などを使用する別の例を示しています。`"200.0+21.4=221.4"`です。 通知だけである、<xref:System.Windows.FlowDirection>が設定されています。  
  
 **FlowDirection のみを使用して数値を表示する図**  
  
 ![右から左に読む数字](../../../../docs/framework/wpf/advanced/media/langattribute.PNG "LangAttribute")  
  
 このアプリケーションのユーザーは、場合でも、出力で失望してありますが、<xref:System.Windows.FlowDirection>が正しいようにアラビア数字の形状になる必要があります、番号が制限されません。  
  
 XAML 要素を含めることができます、[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]属性 (`xml:lang`) の各要素の言語を定義します。 XAML もサポートしています、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]言語原則という`xml:lang`子要素によって、ツリー内の親要素に適用される値を使用します。 前の例での言語が定義されていないため、<xref:System.Windows.Documents.Run>要素またはその上のレベルの要素、既定値`xml:lang`を使用しているある`en-US`xaml です。 内部番号整形アルゴリズム[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]: 対応する言語の選択番号がここでは英語です。 アラビア語を作成するには、レンダリングを正しく番号`xml:lang`を設定する必要があります。  
  
 次の図で例を示しています`xml:lang`を追加します。  
  
 **xml:lang 属性の使用を示す図**  
  
 ![右から左に読むアラビア数字](../../../../docs/framework/wpf/advanced/media/langattribute2.PNG "LangAttribute2")  
  
 次の例では追加`xml:lang`アプリケーションにします。  
  
 [!code-xaml[LangAttribute#LangAttribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LangAttribute/CS/Window1.xaml#langattribute)]  
  
 多くの言語が異なることに注意してください`xml:lang`対象となる地域に応じて値`"ar-SA"`と`"ar-EG"`アラビア語の 2 つのバリエーションを表します。 前の例では、両方を定義する必要があることを示しています、`xml:lang`と<xref:System.Windows.FlowDirection>値。  
  
<a name="FlowDirectionNontext"></a>   
## <a name="flowdirection-with-non-text-elements"></a>非テキスト要素のある FlowDirection  
 <xref:System.Windows.FlowDirection> だけでなくテキストの流れを定義するテキスト要素もほとんどすべての他のフローの方向で[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素。 次の図が示す、<xref:System.Windows.Controls.ToolBar>水平方向を使用する<xref:System.Windows.Media.LinearGradientBrush>の背景を描画します。  
  
 **左から右へのグラデーションを付けたツール バーを示す図**  
  
 ![グラデーションのスクリーン ショット](../../../../docs/framework/wpf/advanced/media/gradient.PNG "Gradient")  
  
 設定した後、<xref:System.Windows.FlowDirection>に<xref:System.Windows.FlowDirection.RightToLeft>だけでなく、<xref:System.Windows.Controls.ToolBar>ボタンは右から左がさらに並べた<xref:System.Windows.Media.LinearGradientBrush>realigns が右から左に流れるには、そのオフセットします。  
  
 次の図の再編成、<xref:System.Windows.Media.LinearGradientBrush>です。  
  
 **右から左へのグラデーションを付けたツール バーを示す図**  
  
 ![右から左に読むグラデーション](../../../../docs/framework/wpf/advanced/media/gradient2-wpf.PNG "Gradient2_WPF")  
  
 次の例は、描画、 <xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.Controls.ToolBar>です。 (を描画すること左右から、削除、<xref:System.Windows.FlowDirection>属性を<xref:System.Windows.Controls.ToolBar>です。  
  
 [!code-xaml[Gradient#Gradient](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Gradient/CS/Window1.xaml#gradient)]  
  
<a name="FlowDirectionExceptions"></a>   
### <a name="flowdirection-exceptions"></a>FlowDirection の例外  
 いくつかのケースがある場所<xref:System.Windows.FlowDirection>予想どおりに動作しません。 ここでは、そのような例外を 2 つ取り上げて説明します。  
  
 **イメージ**  
  
 <xref:System.Windows.Controls.Image>イメージを表示するコントロールを表します。 [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]で使用できます、<xref:System.Windows.Controls.Image.Source%2A>を定義するプロパティ、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]の<xref:System.Windows.Controls.Image>を表示します。  
  
 他のとは異なり[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、要素、<xref:System.Windows.Controls.Image>を継承しない、<xref:System.Windows.FlowDirection>コンテナーからです。 ただし場合、<xref:System.Windows.FlowDirection>明示的に設定されて<xref:System.Windows.FlowDirection.RightToLeft>、<xref:System.Windows.Controls.Image>水平方向に反転表示されます。 これは、双方向コンテンツの開発者にとって便利な機能として実装されています。場合によっては、イメージを左右反転して表示することで必要な効果が得られるためです。  
  
 次の図は、反転<xref:System.Windows.Controls.Image>です。  
  
 **反転されたイメージを示す図**  
  
 ![XamlPad スクリーン ショット](../../../../docs/framework/wpf/advanced/media/image.PNG "Image")  
  
 次の例では、ことを示します、<xref:System.Windows.Controls.Image>継承に失敗した、<xref:System.Windows.FlowDirection>から、<xref:System.Windows.Controls.StackPanel>含まれています。 **注**という名前のファイルをする必要があります**ms_logo.jpg**の C:\ ドライブに、この例を実行します。  
  
 [!code-xaml[Image#Image](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Image/CS/Window1.xaml#image)]  
  
 **注**ダウンロード ファイルに含まれているは、 **ms_logo.jpg**ファイル。 コードは、この .jpg ファイルがプロジェクト内ではなく、C:\ ドライブ上にあることを前提としています。 プロジェクト内のファイルを検索するためには、プロジェクト ファイルから C:\ドライブに .jpg をコピーするかコードを変更する必要があります。 この変更を行う`Source="file://c:/ms_logo.jpg"`に`Source="ms_logo.jpg"`です。  
  
 **パス**  
  
 加え、 <xref:System.Windows.Controls.Image>、もう 1 つの興味深い要素は<xref:System.Windows.Shapes.Path>します。 パスは、接続された一連の線と曲線を描画できるオブジェクトです。 同様の方法で動作、<xref:System.Windows.Controls.Image>に関するその<xref:System.Windows.FlowDirection>。 たとえば、 <xref:System.Windows.FlowDirection.RightToLeft> <xref:System.Windows.FlowDirection>の水平方向ミラーの<xref:System.Windows.FlowDirection.LeftToRight>いずれか。 ただしとは異なり、 <xref:System.Windows.Controls.Image>、<xref:System.Windows.Shapes.Path>継承その<xref:System.Windows.FlowDirection>コンテナーと 1 つからしなくても、明示的に指定します。  
  
 次の例では、3 本の線を使用して単純な矢印を描画します。 最初の矢印は、<xref:System.Windows.FlowDirection.RightToLeft>フローの方向から、<xref:System.Windows.Controls.StackPanel>その始点と終点が右側にあるルートから測定されるようにします。 2 番目の矢印は、明示的な<xref:System.Windows.FlowDirection.RightToLeft><xref:System.Windows.FlowDirection>右側にあるも起動します。 ただし、3 番目の矢印の起点は左側です。 参照の描画の詳細については<xref:System.Windows.Media.LineGeometry>と<xref:System.Windows.Media.GeometryGroup>です。  
  
 [!code-xaml[Paths#Paths](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Paths/CS/Window1.xaml#paths)]  
  
 前の例の出力を次の図に示します。  
  
 **Path 要素を使用して描画した矢印の図**  
  
 ![パス](../../../../docs/framework/wpf/advanced/media/paths.PNG "Paths")  
  
 <xref:System.Windows.Controls.Image>と<xref:System.Windows.Shapes.Path>2 つの方法の例は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]使用<xref:System.Windows.FlowDirection>です。 レイアウトの横にある[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、コンテナー内の特定の方向に要素<xref:System.Windows.FlowDirection>などの要素と共に使用することができます<xref:System.Windows.Controls.InkPresenter>、サーフェイス上のインクをレンダリングする<xref:System.Windows.Media.LinearGradientBrush>、<xref:System.Windows.Media.RadialGradientBrush>です。 右左の動作からを左右の動作からを模倣したコンテンツの必要がある場合またはその逆[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]その機能を提供します。  
  
<a name="NumberSubstitution"></a>   
## <a name="number-substitution"></a>数字の置換  
 従来、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]は数字置換の例の数値が格納されているために、これらの数字を別のロケールでは、統一の内部記憶域を維持しながら、同じ数字の異なるカルチャ図形の形式を許可することでサポートされます。よく知られた 16 進数値、0x40、0x41、選択した言語に応じて表示されているがします。  
  
 これを 1 つの言語に変換する必要がない数値を処理するアプリケーションを許可するが、たとえば、ユーザーが開くことができます、[!INCLUDE[TLA#tla_xl](../../../../includes/tlasharptla-xl-md.md)]ローカライズ アラビア語のスプレッドシート[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]、アラビア語の形の番号を参照していてで開くヨーロッパ言語版の[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]し、同じ数字のヨーロッパ言語形式を参照してください。 これは、コンマ区切りやパーセント記号などの他の記号でも必要です。これらの記号は、通常同じドキュメント内で数字を伴っているからです。  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は引き続きこの機能を備え、置換を使用するタイミングと方法をユーザーがさらに制御できるようにこの機能のサポートが強化されています。 この機能はすべての言語向けに設計されていますが、アプリケーションが実行される可能性のあるカルチャが多岐にわたるために特定の言語に合わせて数字の形状を設定することがアプリケーション開発者にとって通常は問題となる双方向コンテンツに対して特に有用です。  
  
 どの数字置換を制御するコア プロパティは[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>依存関係プロパティです。 <xref:System.Windows.Media.NumberSubstitution>クラスは、テキスト内の数字の表示方法を指定します。 その動作を定義する 3 つのパブリック プロパティがあります。 以下は、各プロパティの概要です。  
  
 **CultureSource:**  
  
 このプロパティは、数字のカルチャを決定する方法を指定します。 3 つの時間を要する<xref:System.Windows.Media.NumberCultureSource>列挙値。  
  
-   優先: 数値のカルチャは、の<xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>プロパティです。  
  
-   Text: 数字カルチャは、テキスト ランのカルチャです。 マークアップでは、なります`xml:lang`、またはそのエイリアス`Language`プロパティ (<xref:System.Windows.FrameworkElement.Language%2A>または<xref:System.Windows.FrameworkContentElement.Language%2A>)。 派生するクラスの既定値はまた、<xref:System.Windows.FrameworkContentElement>です。 このようなクラスに含まれる<xref:System.Windows.Documents.Paragraph?displayProperty=nameWithType>、 <xref:System.Windows.Documents.Table?displayProperty=nameWithType>、<xref:System.Windows.Documents.TableCell?displayProperty=nameWithType>となります。  
  
-   User: 数字カルチャは、現在のスレッドのカルチャです。 このプロパティは、既定値のすべてのサブクラスを<xref:System.Windows.FrameworkElement>など<xref:System.Windows.Controls.Page>、<xref:System.Windows.Window>と<xref:System.Windows.Controls.TextBlock>です。  
  
 **CultureOverride**:  
  
 <xref:System.Windows.Media.NumberSubstitution.CultureOverride%2A>プロパティには、場合にのみ、使用、<xref:System.Windows.Media.NumberSubstitution.CultureSource%2A>プロパティに設定されている<xref:System.Windows.Media.NumberCultureSource.Override>それ以外の場合は無視されます。 このプロパティは数字カルチャを指定します。 値`null`既定値は EN-US として解釈されます。  
  
 **Substitution**:  
  
 このプロパティは、実行する数字の置換の種類を指定します。 次のいずれかになります<xref:System.Windows.Media.NumberSubstitutionMethod>列挙値。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.AsCulture>: 数値のカルチャに基づく置換方法を決定<xref:System.Globalization.NumberFormatInfo.DigitSubstitution%2A?displayProperty=nameWithType>プロパティです。 既定値です。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Context>: 数値のカルチャがアラビア語やペルシア語のカルチャの場合、数字がコンテキストに依存を指定します。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.European>: 番号は常に、ヨーロッパの数字としてレンダリングされます。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>: 数字を表示する、カルチャの指定に従って、数値のカルチャの国別の数字を使用して<xref:System.Globalization.CultureInfo.NumberFormat%2A>です。  
  
-   <xref:System.Windows.Media.NumberSubstitutionMethod.Traditional>: 数字を表示するには、数値のカルチャの従来の数字を使用します。 ほとんどのカルチャでは、これと同じ<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>です。 ただし、<xref:System.Windows.Media.NumberSubstitutionMethod.NativeNational>この値は、アラビア語のすべてのカルチャをアラビア語桁の数字で結果が一部アラビア語のカルチャのラテン桁の数字になります。  
  
 これらの値は双方向コンテンツ開発者にとってどういった意味があるのでしょうか。 ほとんどの場合、開発者が定義にのみ必要があります<xref:System.Windows.FlowDirection>と、各テキストの言語[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]例については、要素`Language="ar-SA"`と<xref:System.Windows.Media.NumberSubstitution>ロジックは、正しいに従って数値の表示の対処[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 次の例で、アラビア語および英語の番号を使用して、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アラビア語版で実行されるアプリケーション[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]です。  
  
 [!code-xaml[Numbers#Numbers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers/CS/Window1.xaml#numbers)]  
  
 アラビア語版で実行している場合、次の図は、前の例の出力[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]です。  
  
 **表示されたアラビア数字と英語数字を示す図**  
  
 ![数字を含む XamlPad のスクリーン ショット](../../../../docs/framework/wpf/advanced/media/numbers.PNG "Numbers")  
  
 <xref:System.Windows.FlowDirection>設定はここでは重要な<xref:System.Windows.FlowDirection>に<xref:System.Windows.FlowDirection.LeftToRight>が得られるヨーロッパ数字が代わりにします。 以下のセクションでは、ドキュメント全体で数字の表示を統一する方法について説明します。 この例では、アラビア語版 Windows で実行されていなければ、すべての数字がヨーロッパ数字として表示されます。  
  
 **置換ルールの定義**  
  
 実際のアプリケーションでは、プログラムでの言語設定が必要となる場合があります。 設定するなど、 `xml:lang` 、システムによって使用されているものと同じにする属性[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、またはアプリケーションの状態に応じて言語を変更する可能性があります。  
  
 する場合は、アプリケーションの状態に基づいて、変更、によって提供される他の機能を使用して[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]です。  
  
 まず、設定、アプリケーション コンポーネントの`NumberSubstitution.CultureSource="Text"`します。 この設定を使用するから、設定にならないことを確認、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]など、既定値として「ユーザー」をされているテキスト要素に<xref:System.Windows.Controls.TextBlock>です。  
  
 例えば:  
  
||  
|-|  
|`<TextBlock`<br /><br /> `Name="text1" NumberSubstitution.CultureSource="Text">`<br /><br /> `1234+5679=6913`<br /><br /> `</TextBlock>`|  
  
 対応する c# コードで設定、`Language`プロパティなど、`"ar-SA"`です。  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage("ar-SA");`|  
  
 設定する必要がある場合、`Language`プロパティを現在のユーザーの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]言語は、次のコードを使用します。  
  
||  
|-|  
|`text1.Language =`<br /><br /> `System.Windows.Markup.XmlLanguage.GetLanguage(`<br /><br /> `System.Globalization.CultureInfo.CurrentUICulture.IetfLanguageTag);`|  
  
 <xref:System.Globalization.CultureInfo.CurrentCulture%2A> 実行時に現在のスレッドで使用される現在のカルチャを表します。  
  
 最終的な[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]例を次の例のようにする必要があります。  
  
 [!code-xaml[Numbers2#Numbers2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers2/CS/Window1.xaml#numbers2)]  
  
 最終的な C# コード例は、次のようにする必要があります。  
  
 [!code-csharp[NumbersCSharp#NumbersCSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/NumbersCSharp/CSharp/Window1.xaml.cs#numberscsharp)]  
  
 次の図は、いずれかのプログラミング言語に対するウィンドウの外観を示します。  
  
 **アラビア数字を表示した図**  
  
 ![アラビア数字](../../../../docs/framework/wpf/advanced/media/numbers2.PNG "Numbers2")  
  
 **Substitution プロパティの使用**  
  
 動作するかまでの数字の置換[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]テキスト要素の両方の言語に依存し、その<xref:System.Windows.FlowDirection>です。 場合、<xref:System.Windows.FlowDirection>左から右、ヨーロッパの桁をレンダリングします。 ただし場合は、アラビア語を付けたものか、言語"ar"に設定され、<xref:System.Windows.FlowDirection>は<xref:System.Windows.FlowDirection.RightToLeft>、代わりにアラビア数字は表示されます。  
  
 ただし、たとえば、すべてのユーザーに対してヨーロッパ数字を表示するなどの、統一されたアプリケーションを作成する必要がある場合もあります。 アラビア語のや数字<xref:System.Windows.Documents.Table>特定セル<xref:System.Windows.Style>です。 使用しているために 1 つの簡単な方法、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>プロパティです。  
  
 次の例では、最初の<xref:System.Windows.Controls.TextBlock>はありません、<xref:System.Windows.Media.NumberSubstitution.Substitution%2A>アルゴリズムは、期待どおりにアラビア数字を表示できるように、プロパティを設定します。 ただし、2 番目の<xref:System.Windows.Controls.TextBlock>、代替文字列に設定されているヨーロッパ アラビア数字は、既定値の置換をオーバーライドするおよびヨーロッパ数字が表示されます。  
  
 [!code-xaml[Numbers3#Numbers3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Numbers3/CS/Window1.xaml#numbers3)]
