---
title: "ToolTip の概要 | Microsoft Docs"
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
  - "コントロール, ヒント"
  - "ToolTip コントロール, ToolTip コントロールの概要"
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# ToolTip の概要
ツールヒントは、<xref:System.Windows.Controls.Button> などの要素の上にマウス ポインターを置いたときに表示される小さいポップアップ ウィンドウです。  ここでは、ツールヒントについて、およびツールヒントのコンテンツを作成およびカスタマイズする方法について説明します。  
  
   
  
<a name="what_is_a_tooltip"></a>   
## ツールヒントとは  
 ツールヒントを持つ要素の上にマウス ポインターを移動すると、ツールヒントのコンテンツ \(たとえば、コントロールの機能を説明するテキスト コンテンツなど\) を含むウィンドウが、指定した時間だけ表示されます。  マウス ポインターをコントロールの外に移動すると、ツールヒントのコンテンツはフォーカスを受け取ることができないので、ウィンドウは表示されなくなります。  
  
 ツールヒントのコンテンツには、1 行または複数行のテキスト、イメージ、図形、またはその他のビジュアル コンテンツを使用できます。  コントロールのツールヒントを定義するには、ツールヒントのコンテンツに次のいずれかのプロパティを設定します。  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=fullName>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=fullName>  
  
 どちらのプロパティを使用するかは、ツールヒントを定義するコントロールが <xref:System.Windows.FrameworkContentElement> クラスまたは <xref:System.Windows.FrameworkElement> クラスのどちらを継承するかによります。  
  
<a name="create_tooltip"></a>   
## ツールヒントの作成  
 <xref:System.Windows.Controls.Button> コントロールの <xref:System.Windows.FrameworkElement.ToolTip%2A> プロパティにテキスト文字列を設定して、簡単なツールヒントを作成する方法を次の例に示します。  
  
 [!code-xml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <xref:System.Windows.Controls.ToolTip> オブジェクトとしてツールヒントを定義することもできます。  次の例では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用し、<xref:System.Windows.Controls.TextBox> 要素のツールヒントとして <xref:System.Windows.Controls.ToolTip> オブジェクトを指定します。  <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=fullName> プロパティを設定することで <xref:System.Windows.Controls.ToolTip> を指定していることに注意してください。  
  
 [!code-xml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 コードを使用して <xref:System.Windows.Controls.ToolTip> オブジェクトを生成する例を次に示します。  この例では、<xref:System.Windows.Controls.ToolTip> \(`tt`\) を作成し、それを <xref:System.Windows.Controls.Button> に関連付けます。  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 ツールヒントのコンテンツを <xref:System.Windows.Controls.DockPanel> などのレイアウト要素で囲むことで、<xref:System.Windows.Controls.ToolTip> オブジェクトとして定義されていないツールヒントのコンテンツを作成することもできます。  次の例では、<xref:System.Windows.Controls.DockPanel> コントロールで囲まれているコンテンツを、<xref:System.Windows.Controls.TextBox> の <xref:System.Windows.FrameworkElement.ToolTip%2A> プロパティに設定する方法を示します。  
  
 [!code-xml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## ToolTip クラスと ToolTipService クラスのプロパティの使用  
 視覚プロパティを設定してスタイルを適用することで、ツールヒントのコンテンツをカスタマイズできます。  <xref:System.Windows.Controls.ToolTip> オブジェクトとしてツールヒントのコンテンツを定義する場合は、<xref:System.Windows.Controls.ToolTip> オブジェクトの視覚プロパティを設定できます。  それ以外の場合は、<xref:System.Windows.Controls.ToolTipService> クラスで等価の[添付プロパティ](GTMT)を設定する必要があります。  
  
 <xref:System.Windows.Controls.ToolTip> と <xref:System.Windows.Controls.ToolTipService> のプロパティを使用して、ツールヒントのコンテンツの位置を指定するプロパティを設定する方法の例については、「[ToolTip を配置する](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md)」を参照してください。  
  
<a name="StylingToolTip"></a>   
## ToolTip のスタイル設定  
 カスタム <xref:System.Windows.Style> を定義することで、<xref:System.Windows.Controls.ToolTip> のスタイルを設定できます。  次の例では、<xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A>、<xref:System.Windows.Controls.Control.FontSize%2A>、および <xref:System.Windows.Controls.Control.FontWeight%2A> を設定することで <xref:System.Windows.Controls.ToolTip> の配置をオフセットして外観を変更する、`Simple` という名前の <xref:System.Windows.Style> を定義しています。  
  
 [!code-xml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## ToolTipService の時間間隔プロパティの使用  
 <xref:System.Windows.Controls.ToolTipService> クラスで提供されている <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>、および <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> の各プロパティを使用すると、ツールヒントの表示時間を設定できます。  
  
 <xref:System.Windows.Controls.ToolTip> が表示されるまでの遅延時間 \(通常は短時間\)、および <xref:System.Windows.Controls.ToolTip> が表示されている時間を指定するには、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> プロパティと <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> プロパティを使用します。  詳細については、「[How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/ja-jp/618e05ef-f2bf-4a53-a0f4-aacb49918bd7)」を参照してください。  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> プロパティは、マウス ポインターをあるコントロールから別のコントロールに移動したときに、後のコントロールのツールヒントを初期遅延なしで表示するかどうかを指定します。  <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> プロパティの詳細については、「[BetweenShowDelay プロパティを使用する](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md)」を参照してください。  
  
 次の例では、ツールヒントにこれらのプロパティを設定する方法を示します。  
  
 [!code-xml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## 参照  
 <xref:System.Windows.Controls.ToolTipService>   
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipEventArgs>   
 <xref:System.Windows.Controls.ToolTipEventHandler>   
 [方法のトピック](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)