---
title: "配置、余白、パディングの概要 | Microsoft Docs"
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
  - "エイリアスの使用"
  - "クラス, FrameworkElement"
  - "FrameworkElement クラス"
  - "マージン"
  - "埋め込み"
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 配置、余白、パディングの概要
<xref:System.Windows.FrameworkElement> クラスは、子要素を正確に配置するために使用する複数のプロパティを公開します。  ここでは、最も重要な 4 つのプロパティ、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>、<xref:System.Windows.Controls.Border.Padding%2A>、および <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> について説明します。  これらのプロパティは、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーション内での要素の位置を制御するための基本機能を提供するため、その効果について理解しておくことが重要です。  
  
   
  
<a name="wcpsdk_layout_amp_introduction"></a>   
## 要素の配置の概要  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を使用して要素を配置する方法はいくつもあります。  ただし、適切な <xref:System.Windows.Controls.Panel> 要素を選択するだけでは、理想的なレイアウトを実現することはできません。  配置をきめ細かく制御するには、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>、<xref:System.Windows.Controls.Border.Padding%2A>、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> の各プロパティについて理解する必要があります。  
  
 複数の配置プロパティを利用するレイアウト シナリオを次の図に示します。  
  
 ![WPF 位置決めのプロパティのサンプル](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic1.png "layout\_margins\_padding\_alignment\_graphic1")  
  
 一見すると、この図の <xref:System.Windows.Controls.Button> 要素は無作為に配置されているように見えます。  しかし、実際には、これらの要素の位置は、余白、配置、およびパディングの組み合わせを使用して正確に制御されています。  
  
 前の図のレイアウトを作成する方法を次の例に示します。  <xref:System.Windows.Controls.Border> 要素は親の <xref:System.Windows.Controls.StackPanel> をカプセル化しており、<xref:System.Windows.Controls.Border.Padding%2A> の値は 15 [デバイス非依存ピクセル](GTMT)に設定されています。  これは、子 <xref:System.Windows.Controls.StackPanel> を囲む狭い <xref:System.Windows.Media.Brushes.LightBlue%2A> の帯の部分を説明しています。  <xref:System.Windows.Controls.StackPanel> の子要素は、このトピックで詳しく説明するさまざまな配置プロパティを示すために使用されます。  3 つの <xref:System.Windows.Controls.Button> 要素を使用して、<xref:System.Windows.FrameworkElement.Margin%2A> プロパティと <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティの効果を示します。  
  
 [!code-csharp[MPALayoutSampleIntro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 次の図では、上の例で使用されているさまざまな配置プロパティを拡大して示します。  以下では、各配置プロパティの使用方法を詳しく説明します。  
  
 ![画面コールアウトを含む位置決めプロパティ](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic2.png "layout\_margins\_padding\_alignment\_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## 配置プロパティの理解  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティと <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> プロパティは、親要素の割り当てられたレイアウト領域内で子要素を配置する方法を記述します。  これらのプロパティを一緒に使用することで、子要素を正確に配置できます。  たとえば、<xref:System.Windows.Controls.DockPanel> の子要素の水平方向の配置については、<xref:System.Windows.HorizontalAlignment>、<xref:System.Windows.HorizontalAlignment>、<xref:System.Windows.HorizontalAlignment>、または <xref:System.Windows.HorizontalAlignment> の 4 種類を指定できます。  垂直方向の配置についても同様の値を指定できます。  
  
> [!NOTE]
>  要素に対して明示的に設定された <xref:System.Windows.FrameworkElement.Height%2A> プロパティと <xref:System.Windows.FrameworkElement.Width%2A> プロパティは、<xref:System.Windows.HorizontalAlignment> プロパティの値より優先されます。  <xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.Width%2A>、および `Stretch` の <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> の値を設定しようとしても、`Stretch` 要求は無視されます。  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### HorizontalAlignment プロパティ  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティは、子要素に適用する水平方向の配置の特性を宣言します。  次の表は、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティに指定できる値を示します。  
  
|メンバー|Description|  
|----------|-----------------|  
|<xref:System.Windows.HorizontalAlignment>|子要素を、親要素に割り当てられているレイアウト空間の左端に配置します。|  
|<xref:System.Windows.HorizontalAlignment>|子要素を、親要素に割り当てられているレイアウト空間の中央に配置します。|  
|<xref:System.Windows.HorizontalAlignment>|子要素を、親要素に割り当てられているレイアウト空間の右端に配置します。|  
|<xref:System.Windows.HorizontalAlignment> \(既定値\)|子要素を、親要素に割り当てられているレイアウト空間全体に引き伸ばして配置します。  明示的に指定した <xref:System.Windows.FrameworkElement.Width%2A> および <xref:System.Windows.FrameworkElement.Height%2A> の値が優先されます。|  
  
 次の例は、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティを <xref:System.Windows.Controls.Button> 要素に適用する方法を示しています。  さまざまなレンダリング動作をわかりやすく図示するために、各属性の値を表示します。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 上記のコードの結果、レイアウトは次の図のようになります。  各 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> の値によって要素がどのように配置されるかを図示しています。  
  
 ![HorizontalAlignment のサンプル](../../../../docs/framework/wpf/advanced/media/layout-horizontal-alignment-graphic.png "layout\_horizontal\_alignment\_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### VerticalAlignment プロパティ  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> プロパティは、子要素に適用する垂直方向の配置の特性を記述します。  次の表は、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> プロパティに指定できる値を示します。  
  
|メンバー|Description|  
|----------|-----------------|  
|<xref:System.Windows.VerticalAlignment>|子要素を、親要素に割り当てられているレイアウト空間の上端に配置します。|  
|<xref:System.Windows.VerticalAlignment>|子要素を、親要素に割り当てられているレイアウト空間の中央に配置します。|  
|<xref:System.Windows.VerticalAlignment>|子要素を、親要素に割り当てられているレイアウト空間の下端に配置します。|  
|<xref:System.Windows.VerticalAlignment> \(既定値\)|子要素を、親要素に割り当てられているレイアウト空間全体に引き伸ばして配置します。  明示的に指定した <xref:System.Windows.FrameworkElement.Width%2A> および <xref:System.Windows.FrameworkElement.Height%2A> の値が優先されます。|  
  
 次の例は、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> プロパティを <xref:System.Windows.Controls.Button> 要素に適用する方法を示しています。  さまざまなレンダリング動作をわかりやすく図示するために、各属性の値を表示します。  このサンプルでは、ガイドラインを表示した <xref:System.Windows.Controls.Grid> 要素を親として使用し、各プロパティ値のレイアウト動作がよくわかるようにします。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xml[MPALayoutVerticalAlignment#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 上記のコードの結果、レイアウトは次の図のようになります。  各 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> の値によって要素がどのように配置されるかを図示しています。  
  
 ![VerticalAlignment プロパティのサンプル](../../../../docs/framework/wpf/advanced/media/layout-vertical-alignment-graphic.png "layout\_vertical\_alignment\_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## 余白プロパティの理解  
 <xref:System.Windows.FrameworkElement.Margin%2A> プロパティは、要素とその子 \(またはピア\) との間の距離を表します。  `Margin="20"` のような構文を使用することで、<xref:System.Windows.FrameworkElement.Margin%2A> の値を均一にできます。  この構文では、20 [デバイス非依存ピクセル](GTMT)という均一の <xref:System.Windows.FrameworkElement.Margin%2A> が、要素に適用されます。  また、<xref:System.Windows.FrameworkElement.Margin%2A> の値には、`Margin="0,10,5,25"` のような 4 つの値から成る形式を使用することもできます。各値は、左、上、右、下に \(この順序で\) 適用する余白を示します。  <xref:System.Windows.FrameworkElement.Margin%2A> プロパティを適切に使用することで、要素のレンダリング位置、および近隣の要素や子のレンダリング位置を、非常に細かく制御できます。  
  
> [!NOTE]
>  ゼロ以外の余白は、要素の <xref:System.Windows.FrameworkElement.ActualWidth%2A> および <xref:System.Windows.FrameworkElement.ActualHeight%2A> の外側の領域に適用されます。  
  
 <xref:System.Windows.Controls.Button> 要素のグループの周囲に均一の余白を適用する方法を次の例に示します。  <xref:System.Windows.Controls.Button> 要素は、各方向に 10 ピクセルの余白を設けて等間隔に配置されます。  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xml[MarginPaddingAlignmentSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 多くのインスタンスでは、均一の余白は適切ではありません。  このような場合は、不均一の間隔を適用できます。  次の例では、子要素に不均一の余白を適用する方法を示します。  余白は、左、上、右、下の順序で記述されています。  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xml[MarginPaddingAlignmentSample#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## パディング プロパティの理解  
 パディングは、多くの点で <xref:System.Windows.FrameworkElement.Margin%2A> に似ています。  パディング プロパティは少数のクラスでのみ、主に利便性向上のため、公開されています。パディング プロパティを公開しているクラスの例としては、<xref:System.Windows.Documents.Block>、<xref:System.Windows.Controls.Border>、<xref:System.Windows.Controls.Control>、<xref:System.Windows.Controls.TextBlock> などがあります。  <xref:System.Windows.Controls.Border.Padding%2A> プロパティは、指定した <xref:System.Windows.Thickness> の値だけ子要素の実質的なサイズを拡大します。  
  
 <xref:System.Windows.Controls.Border.Padding%2A> を親 <xref:System.Windows.Controls.Border> 要素に適用する方法を次の例に示します。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xml[MarginPaddingAlignmentSample#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## アプリケーションでの配置、余白、パディングの使用  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、<xref:System.Windows.FrameworkElement.Margin%2A>、<xref:System.Windows.Controls.Border.Padding%2A>、および <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> は、複雑な[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を作成するために必要なコントロールの配置機能を提供します。  各プロパティの効果を使用して子要素の配置を変更し、動的なアプリケーションやユーザー環境を柔軟に作成できます。  
  
 このトピックで詳しく説明した各概念の例を次に示します。  このトピックの最初のサンプルで示したインフラストラクチャを基にして、この例では、最初のサンプルの <xref:System.Windows.Controls.Border> の子として <xref:System.Windows.Controls.Grid> 要素を追加します。  <xref:System.Windows.Controls.Border.Padding%2A> を親の <xref:System.Windows.Controls.Border> 要素に適用します。  <xref:System.Windows.Controls.Grid> を使用して、3 つの子 <xref:System.Windows.Controls.StackPanel> 要素の間の領域を分割します。  再び <xref:System.Windows.Controls.Button> 要素を使用して、<xref:System.Windows.FrameworkElement.Margin%2A> と <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> のさまざまな効果を示します。  各 <xref:System.Windows.Controls.ColumnDefinition> に <xref:System.Windows.Controls.TextBlock> 要素を追加し、各列の <xref:System.Windows.Controls.Button> 要素に適用するさまざまなプロパティを定義しやすくします。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xml[MarginPaddingAlignmentSample#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 コンパイルすると、前のアプリケーションからは次の図に示すような [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が生成されます。  さまざまなプロパティ値の効果が要素間の間隔に示されており、各列の要素に対する重要なプロパティ値は <xref:System.Windows.Controls.TextBlock> 要素内に示されています。  
  
 ![1 つのアプリケーション内の複数の位置決めプロパティ](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-aligment-graphic3.png "layout\_margins\_padding\_aligment\_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## 次の内容  
 <xref:System.Windows.FrameworkElement> クラスで定義されている配置プロパティを使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション内の要素の配置をきめ細かく制御できます。  これまでに説明したいくつかの手法を使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を使用して、要素をより適切に配置できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のレイアウトについてさらに詳細に説明するソースが他にもあります。  「[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)」トピックでは、さまざまな <xref:System.Windows.Controls.Panel> 要素についてさらに詳しく説明されています。  「[チュートリアル: WPF の概要](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)」トピックでは、レイアウト要素を使用してコンポーネントを配置し、そのアクションをデータ ソースにバインドする、高度な手法が紹介されています。  
  
## 参照  
 <xref:System.Windows.FrameworkElement>   
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>   
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>   
 <xref:System.Windows.FrameworkElement.Margin%2A>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)   
 [WPF レイアウト ギャラリーのサンプル](http://go.microsoft.com/fwlink/?LinkID=160054)