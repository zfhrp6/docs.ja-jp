---
title: "エキスパンダーの概要 | Microsoft Docs"
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
  - "コントロール, Expander"
  - "Expander コントロール, エキスパンダー コントロールの概要"
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# エキスパンダーの概要
<xref:System.Windows.Controls.Expander> コントロールとは、ウィンドウに似た、ヘッダーを持つ展開可能な領域内にコンテンツを表示するための手段です。  
  
   
  
<a name="CreatinganExpanderinXAML"></a>   
## 単純なエキスパンダーの作成  
 簡単な <xref:System.Windows.Controls.Expander> コントロールを作成する方法を次の例に示します。  この例では、前の図のような外観の <xref:System.Windows.Controls.Expander> を作成します。  
  
 [!code-xml[ExpanderExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 <xref:System.Windows.Controls.Expander> の <xref:System.Windows.Controls.ContentControl.Content%2A> および <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> には、<xref:System.Windows.Controls.RadioButton> オブジェクトや <xref:System.Windows.Controls.Image> オブジェクトなどの複雑なコンテンツも格納できます。  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## コンテンツ エリアの展開方向の設定  
 <xref:System.Windows.Controls.ExpandDirection> プロパティを使用して、<xref:System.Windows.Controls.Expander> コントロールのコンテンツ領域を <xref:System.Windows.Controls.ExpandDirection>、<xref:System.Windows.Controls.ExpandDirection>、<xref:System.Windows.Controls.ExpandDirection>、<xref:System.Windows.Controls.ExpandDirection> の 4 つのうちどの方向に展開するかを設定します。  コンテンツ領域が折りたたまれているときは、<xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> およびそのトグル ボタンだけが表示されます。  方向を示す矢印を表示する <xref:System.Windows.Controls.Button> コントロールが、コンテンツ エリアを展開したり折りたたんだりするためのトグル ボタンとして使用されます。  展開されると、<xref:System.Windows.Controls.Expander> は、ウィンドウに似た領域にすべてのコンテンツを表示しようとします。  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## パネル内のエキスパンダーのサイズの制御  
 <xref:System.Windows.Controls.Expander> コントロールが <xref:System.Windows.Controls.StackPanel> などの <xref:System.Windows.Controls.Panel> から継承されるレイアウト コントロールの内側にあり、<xref:System.Windows.Controls.Expander.ExpandDirection%2A> プロパティが <xref:System.Windows.Controls.ExpandDirection> または <xref:System.Windows.Controls.ExpandDirection> に設定されている場合は、<xref:System.Windows.Controls.Expander> に対して <xref:System.Windows.FrameworkElement.Height%2A> を指定しないでください。  同様に、<xref:System.Windows.Controls.Expander.ExpandDirection%2A> プロパティが <xref:System.Windows.Controls.ExpandDirection> または <xref:System.Windows.Controls.ExpandDirection> に設定されている場合は、<xref:System.Windows.Controls.Expander> に対して <xref:System.Windows.FrameworkElement.Width%2A> を指定しないでください。  
  
 展開されたコンテンツを表示する方向のサイズを <xref:System.Windows.Controls.Expander> コントロールに対して設定すると、コンテンツが使用する領域は<xref:System.Windows.Controls.Expander> によって制御され、その周囲に境界線が表示されます。  コンテンツが折りたたまれても境界線は表示されます。  展開されたコンテンツ領域のサイズを設定するには、<xref:System.Windows.Controls.Expander> のコンテンツに対してサイズを設定します。スクロール可能にする場合は、コンテンツを囲む <xref:System.Windows.Controls.ScrollViewer> に対してサイズを設定します。  
  
 <xref:System.Windows.Controls.Expander> コントロールが <xref:System.Windows.Controls.DockPanel> の最後の要素である場合は、<xref:System.Windows.Controls.DockPanel> の残りの領域に等しくなるように、<xref:System.Windows.Controls.Expander> のサイズが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] によって自動的に設定されます。  この既定の動作を回避するには、<xref:System.Windows.Controls.DockPanel> オブジェクトの <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> プロパティを `false` に設定するか、<xref:System.Windows.Controls.Expander> が <xref:System.Windows.Controls.DockPanel> の最後の要素にならないようにします。  
  
<a name="CreatingScrollableContent"></a>   
## スクロール可能なコンテンツの作成  
 コンテンツが大きすぎてコンテンツ領域に表示できない場合は、<xref:System.Windows.Controls.Expander> のコンテンツを <xref:System.Windows.Controls.ScrollViewer> でラップすると、コンテンツがスクロール可能になります。  <xref:System.Windows.Controls.Expander> コントロールは、スクロール機能を自動的に持つわけではありません。  <xref:System.Windows.Controls.ScrollViewer> コントロールを持つ <xref:System.Windows.Controls.Expander> コントロールを次の図に示します。  
  
 **ScrollViewer 内のエキスパンダー**  
  
 ![ScrollBar を持つ Expander](../../../../docs/framework/wpf/controls/media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 <xref:System.Windows.Controls.Expander> コントロールを <xref:System.Windows.Controls.ScrollViewer> 内に配置する場合は、<xref:System.Windows.Controls.Expander> コンテンツが開く方向に対応する <xref:System.Windows.Controls.ScrollViewer> のサイズ プロパティを、<xref:System.Windows.Controls.Expander> コンテンツ領域のサイズに設定します。  たとえば、<xref:System.Windows.Controls.Expander> の <xref:System.Windows.Controls.Expander.ExpandDirection%2A> プロパティを <xref:System.Windows.Controls.ExpandDirection> に設定する \(コンテンツ領域が下に開く\) 場合は、<xref:System.Windows.Controls.ScrollViewer> コントロールの <xref:System.Windows.FrameworkElement.Height%2A> プロパティを、コンテンツ領域に必要な高さに設定します。  このような設定を行わずにコンテンツ自体の高さのサイズを設定しても、この設定は <xref:System.Windows.Controls.ScrollViewer> に認識されないので、コンテンツはスクロール可能にはなりません。  
  
 コンテンツが複雑で、<xref:System.Windows.Controls.ScrollViewer> コントロールを持つ <xref:System.Windows.Controls.Expander> コントロールを作成する方法を次の例に示します。  この例では、ここで最初に示した図のような <xref:System.Windows.Controls.Expander> を作成します。  
  
 [!code-csharp[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xml[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## 配置プロパティの使用  
 コンテンツの配置 \(左揃えや上揃えなど\) を指定するには、<xref:System.Windows.Controls.Expander> コントロールの <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> プロパティおよび <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> プロパティを設定します。  これらのプロパティを設定すると、配置がヘッダーに適用され、展開されたコンテンツにも適用されます。  
  
## 参照  
 <xref:System.Windows.Controls.Expander>   
 <xref:System.Windows.Controls.ExpandDirection>   
 [方法のトピック](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)