---
title: "配置、余白、パディングの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d53ec57bdd6126aa1b82e3fa34d01b8907ca169
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="alignment-margins-and-padding-overview"></a>配置、余白、パディングの概要
<xref:System.Windows.FrameworkElement>クラスは子要素を正確に配置に使用されるいくつかのプロパティを公開します。 このトピックでは、4 つの最も重要なプロパティについて説明します。 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、 <xref:System.Windows.Controls.Border.Padding%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>です。 これらのプロパティの効果を理解することが重要です。[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの要素の位置を制御するための基本となるためです。  
  
  
<a name="wcpsdk_layout_amp_introduction"></a>   
## <a name="introduction-to-element-positioning"></a>要素配置の概要  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を利用し、さまざまな方法で要素を配置できます。 ただし、最適なレイアウトを実現するを越えてだけで、右側の選択<xref:System.Windows.Controls.Panel>要素。 配置の詳細に制御するうえで、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、 <xref:System.Windows.Controls.Border.Padding%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティです。  
  
 次の図は、いくつかの配置プロパティを利用したレイアウト シナリオのものです。  
  
 ![WPF 位置決めプロパティのサンプル](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 一見、<xref:System.Windows.Controls.Button>をランダムに配置する次の図に要素があります。 しかしながら、位置は実際のところ、余白、配置、パディングを組み合わせることで正確に制御されます。  
  
 次の例は、前の図のレイアウトの作成方法を示しています。 A<xref:System.Windows.Controls.Border>要素が親をカプセル化<xref:System.Windows.Controls.StackPanel>で、 <xref:System.Windows.Controls.Border.Padding%2A> 15 デバイス非依存のピクセルの値。 これは、アカウントの範囲を絞り<xref:System.Windows.Media.Brushes.LightBlue%2A>バンドを子を囲む<xref:System.Windows.Controls.StackPanel>です。 子要素、<xref:System.Windows.Controls.StackPanel>使用の詳細については、このトピックで、さまざまな配置のプロパティについて説明します。 次の 3 つ<xref:System.Windows.Controls.Button>要素が両方を示すために使用される、<xref:System.Windows.FrameworkElement.Margin%2A>と<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティです。  
  
 [!code-csharp[MPALayoutSampleIntro#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 次の図は、前のサンプルで使用されたさまざまな配置プロパティを大写しにしたものです。 このトピックの後続のセクションでは、各配置プロパティの使用方法をさらに詳しく説明します。  
  
 ![配置プロパティ (解説付き)](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>   
## <a name="understanding-alignment-properties"></a>配置プロパティを理解する  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>と<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティは、親要素に割り当てられているレイアウト領域内で子要素を配置する方法について説明します。 これらのプロパティを一緒に使用することで、子要素を正確に配置できます。 たとえば、子要素の<xref:System.Windows.Controls.DockPanel>4 つの異なる水平方向のアラインメントを指定できます: <xref:System.Windows.HorizontalAlignment.Left>、 <xref:System.Windows.HorizontalAlignment.Right>、または<xref:System.Windows.HorizontalAlignment.Center>、または<xref:System.Windows.HorizontalAlignment.Stretch>使用可能なスペースを埋めます。 垂直配置にも同様の値を利用できます。  
  
> [!NOTE]
>  明示的にセット<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>要素のプロパティよりも優先、<xref:System.Windows.HorizontalAlignment.Stretch>プロパティの値。 設定しようとしています。 <xref:System.Windows.FrameworkElement.Height%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、および<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>の値`Stretch`結果、`Stretch`要求は無視されます。  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>   
### <a name="horizontalalignment-property"></a>HorizontalAlignment プロパティ  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティは、子要素に適用する水平方向の配置特性を宣言します。 それぞれの有効な値の次の表は、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティです。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|子要素は、親要素に割り当てられたレイアウト領域の左に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Center>|子要素は、親要素に割り当てられたレイアウト領域の中央に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Right>|子要素は、親要素に割り当てられたレイアウト領域の右に揃えて配置されます。|  
|<xref:System.Windows.HorizontalAlignment.Stretch>(既定値)|子要素は引き伸ばされ、親要素に割り当てられたレイアウト領域を埋めます。 明示的な<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>値が優先されます。|  
  
 次の例に適用する方法を示しています、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>プロパティを<xref:System.Windows.Controls.Button>要素。 各属性値が示され、さまざまなレンダリング動作をより良く表しています。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 前のコードは次の画像のようなレイアウトを作ります。 それぞれの位置の影響<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>値は、図に表示されます。  
  
 ![HorizontalAlignment のサンプル](../../../../docs/framework/wpf/advanced/media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>   
### <a name="verticalalignment-property"></a>VerticalAlignment プロパティ  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティは、子要素に適用する垂直方向の配置特性を記述します。 それぞれの有効な値の次の表は、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティです。  
  
|メンバー|説明|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|子要素は、親要素に割り当てられたレイアウト領域の上に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Center>|子要素は、親要素に割り当てられたレイアウト領域の中央に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Bottom>|子要素は、親要素に割り当てられたレイアウト領域の下に揃えて配置されます。|  
|<xref:System.Windows.VerticalAlignment.Stretch>(既定値)|子要素は引き伸ばされ、親要素に割り当てられたレイアウト領域を埋めます。 明示的な<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>値が優先されます。|  
  
 次の例に適用する方法を示しています、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>プロパティを<xref:System.Windows.Controls.Button>要素。 各属性値が示され、さまざまなレンダリング動作をより良く表しています。 このサンプルの目的で、<xref:System.Windows.Controls.Grid>表示のグリッド線を持つ要素は各プロパティ値のレイアウトの動作を理解する、親として使用します。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 前のコードは次の画像のようなレイアウトを作ります。 それぞれの位置の影響<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>値は、図に表示されます。  
  
 ![VerticalAlignment プロパティのサンプル](../../../../docs/framework/wpf/advanced/media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>   
## <a name="understanding-margin-properties"></a>余白プロパティを理解する  
 <xref:System.Windows.FrameworkElement.Margin%2A>プロパティには、要素とその子またはピア間の距離がについて説明します。 <xref:System.Windows.FrameworkElement.Margin%2A>ような構文を使用して値を統一されたできます`Margin="20"`です。 この構文では、一様に<xref:System.Windows.FrameworkElement.Margin%2A>要素に適用される非依存のピクセルの 20 デバイス。 <xref:System.Windows.FrameworkElement.Margin%2A>値をとることも次の 4 つの個別の値の形式左、上、右、およびその順序で、一番下に適用する個別の余白を記述するそれぞれの値と同様に`Margin="0,10,5,25"`です。 適切な使用、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティ要素の描画位置とその近隣ノード要素と子の描画位置の非常に詳細に制御を有効にします。  
  
> [!NOTE]
>  0 以外の余白は、要素の<xref:System.Windows.FrameworkElement.ActualWidth%2A>と<xref:System.Windows.FrameworkElement.ActualHeight%2A>です。  
  
 次の例は、グループの周囲の統一された余白を適用する方法を示しています。<xref:System.Windows.Controls.Button>要素。 <xref:System.Windows.Controls.Button>要素を各方向に 10 ピクセルの余白のバッファーで等間隔に配置します。  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 多くの場合、均一余白は適切ではありません。 適切でなければ、均一ではない間隔を適用できます。 次の例は、均一ではない余白間隔を子要素に適用する方法を示しています。 余白は左、上、右、下の順序で記述されます。  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>   
## <a name="understanding-the-padding-property"></a>Padding プロパティを理解する  
 パディングは<xref:System.Windows.FrameworkElement.Margin%2A>ほとんどの点でします。 便宜を図って、主に、いくつかのクラスでのみ、Padding プロパティに公開される: <xref:System.Windows.Documents.Block>、 <xref:System.Windows.Controls.Border>、 <xref:System.Windows.Controls.Control>、および<xref:System.Windows.Controls.TextBlock>パディング プロパティを公開するクラスのサンプルです。 <xref:System.Windows.Controls.Border.Padding%2A>プロパティは、指定した子要素の有効なサイズを拡大<xref:System.Windows.Thickness>値。  
  
 次の例は、適用する方法を示しています。<xref:System.Windows.Controls.Border.Padding%2A>親<xref:System.Windows.Controls.Border>要素。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>   
## <a name="using-alignment-margins-and-padding-in-an-application"></a>アプリケーションで配置、余白、パディングを利用する  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A>、 <xref:System.Windows.Controls.Border.Padding%2A>、および<xref:System.Windows.FrameworkElement.VerticalAlignment%2A>、複雑なを作成するために必要なコントロールが配置[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。 各プロパティの効果を利用し、子要素の配置を変更できます。動的なアプリケーション/ユーザー体験を生み出す柔軟性が与えられます。  
  
 次の例は、このトピックで説明した各概念を示しています。 このトピックの最初のサンプルについては、インフラストラクチャの構築、この例では追加、<xref:System.Windows.Controls.Grid>の子要素として、<xref:System.Windows.Controls.Border>最初のサンプルです。 <xref:System.Windows.Controls.Border.Padding%2A>親に適用される<xref:System.Windows.Controls.Border>要素。 <xref:System.Windows.Controls.Grid> 3 つの子の間にスペースをパーティション分割に使用される<xref:System.Windows.Controls.StackPanel>要素。 <xref:System.Windows.Controls.Button>さまざまな影響を表示する要素を使用再度<xref:System.Windows.FrameworkElement.Margin%2A>と<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>です。 <xref:System.Windows.Controls.TextBlock>要素がそれぞれに追加され<xref:System.Windows.Controls.ColumnDefinition>をより適切に適用されるさまざまなプロパティを定義する、<xref:System.Windows.Controls.Button>各列内の要素。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 コンパイルすると、先のアプリケーションは次の図のような [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] になります。 要素間の間隔では、さまざまなプロパティ値の効果は、内に表示される各列内の要素の重要なプロパティ値<xref:System.Windows.Controls.TextBlock>要素。  
  
 ![1 つのアプリケーション内の複数の配置プロパティ](../../../../docs/framework/wpf/advanced/media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>   
## <a name="whats-next"></a>次の内容  
 配置のプロパティによって定義された、<xref:System.Windows.FrameworkElement>クラス内の要素の配置の詳細に制御を有効にする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションです。 これで [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] を利用して効果的に要素を配置するための手法を理解できたことでしょう。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] レイアウトの詳細はその他の資料で確認できます。 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)トピックには、さまざまなについての詳細が含まれています。<xref:System.Windows.Controls.Panel>要素。 トピック[チュートリアル: 最初の WPF デスクトップ アプリケーション](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)コンポーネントを配置して、そのアクションをデータ ソースにバインドするレイアウト要素を使用して高度な技術が導入されています。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.Margin%2A>  
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [レイアウト](../../../../docs/framework/wpf/advanced/layout.md)  
 [WPF レイアウト ギャラリー サンプル](http://go.microsoft.com/fwlink/?LinkID=160054)
