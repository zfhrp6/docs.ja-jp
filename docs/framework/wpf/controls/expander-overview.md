---
title: エキスパンダーの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
ms.openlocfilehash: abcc7c48c602aee742959b39bb5244563eaf4d5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557590"
---
# <a name="expander-overview"></a>エキスパンダーの概要
<xref:System.Windows.Controls.Expander>コントロールがコンテンツをウィンドウのようになり、ヘッダーを含む拡張可能な領域を提供する方法を提供します。  
  
  
<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>単純なエキスパンダーの作成  
 次の例は、単純なを作成する方法を示します<xref:System.Windows.Controls.Expander>コントロール。 この例で作成、<xref:System.Windows.Controls.Expander>前の図のようになります。  
  
 [!code-xaml[ExpanderExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A>と<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>の<xref:System.Windows.Controls.Expander>など、複雑なコンテンツは、ことができますも含まれて<xref:System.Windows.Controls.RadioButton>と<xref:System.Windows.Controls.Image>オブジェクト。  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>コンテンツ エリアの展開方向の設定  
 コンテンツ領域を設定することができます、<xref:System.Windows.Controls.Expander>を 4 つの方向のいずれかで展開コントロール (<xref:System.Windows.Controls.ExpandDirection.Down>、 <xref:System.Windows.Controls.ExpandDirection.Up>、 <xref:System.Windows.Controls.ExpandDirection.Left>、または<xref:System.Windows.Controls.ExpandDirection.Right>) を使用して、<xref:System.Windows.Controls.ExpandDirection>プロパティです。 ときに、コンテンツ領域が折りたたまれて、のみ、 <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>され、トグル ボタンが表示されます。 A<xref:System.Windows.Controls.Button>方向矢印を表示するコントロールは、展開または折りたたみのコンテンツ領域にトグル ボタンとして使用します。 展開すると、<xref:System.Windows.Controls.Expander>ウィンドウのような領域内のすべてのコンテンツの表示しようとしています。  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>パネル内のエキスパンダーのサイズの制御  
 場合、<xref:System.Windows.Controls.Expander>コントロールがから継承するレイアウト コントロールの内部<xref:System.Windows.Controls.Panel>など<xref:System.Windows.Controls.StackPanel>を指定しない、<xref:System.Windows.FrameworkElement.Height%2A>上、<xref:System.Windows.Controls.Expander>ときに、<xref:System.Windows.Controls.Expander.ExpandDirection%2A>プロパティに設定されている<xref:System.Windows.Controls.ExpandDirection.Down>または<xref:System.Windows.Controls.ExpandDirection.Up>です。 同様に、指定しない、<xref:System.Windows.FrameworkElement.Width%2A>上、<xref:System.Windows.Controls.Expander>ときに、<xref:System.Windows.Controls.Expander.ExpandDirection%2A>プロパティに設定されている<xref:System.Windows.Controls.ExpandDirection.Left>または<xref:System.Windows.Controls.ExpandDirection.Right>です。  
  
 サイズを設定すると、<xref:System.Windows.Controls.Expander>展開されたコンテンツが表示されている方向、<xref:System.Windows.Controls.Expander>周囲の境界線を表示し、コンテンツでは使用される領域のコントロールを取得します。 コンテンツが折りたたまれても、境界線は表示されます。 展開されたコンテンツ領域のサイズを設定するには、コンテンツのサイズを設定、 <xref:System.Windows.Controls.Expander>、または上で、機能のスクロールする場合、<xref:System.Windows.Controls.ScrollViewer>コンテンツを囲みます。  
  
 ときに、<xref:System.Windows.Controls.Expander>コントロールは、最後の要素、 <xref:System.Windows.Controls.DockPanel>、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]が自動的に設定、<xref:System.Windows.Controls.Expander>ディメンションの残りの部分と等しく、<xref:System.Windows.Controls.DockPanel>です。 この既定の動作を防ぐためには、設定、<xref:System.Windows.Controls.DockPanel.LastChildFill%2A>プロパティを<xref:System.Windows.Controls.DockPanel>オブジェクトを`false`、ことを確認または、<xref:System.Windows.Controls.Expander>の最後の要素ではありません、<xref:System.Windows.Controls.DockPanel>です。  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>スクロール可能なコンテンツの作成  
 内容がコンテンツ領域のサイズに対して大きすぎる場合は、内容をラップすることができます、<xref:System.Windows.Controls.Expander>で、<xref:System.Windows.Controls.ScrollViewer>スクロール可能なコンテンツを提供するためにします。 <xref:System.Windows.Controls.Expander>コントロールはスクロール機能を自動的に提供しません。 次の図は、<xref:System.Windows.Controls.Expander>が含まれるコントロール、<xref:System.Windows.Controls.ScrollViewer>コントロール。  
  
 **ScrollViewer 内のエキスパンダー**  
  
 ![ScrollBar を持つ Expander](../../../../docs/framework/wpf/controls/media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 配置するとき、<xref:System.Windows.Controls.Expander>で制御、 <xref:System.Windows.Controls.ScrollViewer>、設定、<xref:System.Windows.Controls.ScrollViewer>ディメンションの方向に対応するプロパティ、<xref:System.Windows.Controls.Expander>のサイズにコンテンツが表示されます、<xref:System.Windows.Controls.Expander>コンテンツ領域です。 例では、設定した場合の<xref:System.Windows.Controls.Expander.ExpandDirection%2A>プロパティを<xref:System.Windows.Controls.Expander>に<xref:System.Windows.Controls.ExpandDirection.Down>(コンテンツ領域はダウンが開きます)、設定、<xref:System.Windows.FrameworkElement.Height%2A>プロパティを<xref:System.Windows.Controls.ScrollViewer>コンテンツ領域の必要な高さを制御します。 代わりにコンテンツそのものの高さを設定した場合<xref:System.Windows.Controls.ScrollViewer>この設定は認識されず、したがって、スクロール可能なコンテンツは提供されません。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.Expander>を持つ複合コンテンツを含むコントロール、<xref:System.Windows.Controls.ScrollViewer>コントロール。 この例で作成、<xref:System.Windows.Controls.Expander>先頭の図は、このセクションのようなものです。  
  
 [!code-csharp[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>配置プロパティの使用  
 コンテンツの配置を設定することができます、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>と<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>プロパティを<xref:System.Windows.Controls.Expander>コントロール。 これらのプロパティを設定すると、配置がヘッダーに適用され、展開されたコンテンツにも適用されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Expander>  
 <xref:System.Windows.Controls.ExpandDirection>  
 [データ バインドに関する「方法」トピック](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
