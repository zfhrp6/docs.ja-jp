---
title: "ToolTip の概要"
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
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bd56323e90368f850ae54854e6f50b63d5f7fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-overview"></a>ToolTip の概要
ツールヒントは、ユーザーなどを超えると、要素の上にマウス ポインターを置いたときに表示される小さいポップアップ ウィンドウ、<xref:System.Windows.Controls.Button>です。 このトピックでは、ツールヒントを紹介し、ツールヒントの内容を作成およびカスタマイズする方法について説明します。  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a>ツールヒントとは  
 ツールヒントを持つ要素の上にマウス ポインターを置くと、一定の時間、ツールヒントの内容 (たとえば、コントロールの機能を説明するテキスト コンテンツ) を含むウィンドウが表示されます。 コントロールからマウス ポインターを移動すると、ツールヒントの内容がフォーカスを受け取ることができなくなるため、ウィンドウが消えます  
  
 ツールヒントの内容は、1 行または複数行のテキスト、イメージ、図形などのビジュアル コンテンツを含めることができます。 次のプロパティの 1 つをツールヒントの内容に設定することによって、コントロールのツールヒントを定義します。  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 使用するどのプロパティから、ツールヒントを定義するコントロールを継承するかどうかに依存、<xref:System.Windows.FrameworkContentElement>または<xref:System.Windows.FrameworkElement>クラスです。  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a>ツールヒントの作成  
 次の例を設定して、単純なツールヒントを作成する方法を示しています、<xref:System.Windows.FrameworkElement.ToolTip%2A>プロパティを<xref:System.Windows.Controls.Button>コントロールにテキスト文字列。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 としてのツールヒントを定義することも、<xref:System.Windows.Controls.ToolTip>オブジェクト。 次の例で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を指定する、<xref:System.Windows.Controls.ToolTip>オブジェクトのツールヒントとして、<xref:System.Windows.Controls.TextBox>要素。 例では、指定、<xref:System.Windows.Controls.ToolTip>を設定して、<xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>プロパティです。  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 次の例では、コードを使用して、生成する、<xref:System.Windows.Controls.ToolTip>オブジェクト。 例は、作成、 <xref:System.Windows.Controls.ToolTip> (`tt`) に関連付けますと、<xref:System.Windows.Controls.Button>です。  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 として定義されていないツールヒントのコンテンツを作成することも、<xref:System.Windows.Controls.ToolTip>などをレイアウト要素のツールヒントのコンテンツを囲むことによってオブジェクト、<xref:System.Windows.Controls.DockPanel>です。 次の例は、設定する方法を示します、<xref:System.Windows.FrameworkElement.ToolTip%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>で囲まれたコンテンツを<xref:System.Windows.Controls.DockPanel>コントロール。  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>ToolTip クラスおよび ToolTipService クラスのプロパティの使用  
 ビジュアル プロパティを設定し、スタイルを適用して、ツールヒントの内容をカスタマイズできます。 ツールヒントとしてコンテンツを定義する場合、<xref:System.Windows.Controls.ToolTip>オブジェクトのビジュアル プロパティを設定することができます、<xref:System.Windows.Controls.ToolTip>オブジェクト。 それ以外の場合でと同等の添付プロパティを設定する必要があります、<xref:System.Windows.Controls.ToolTipService>クラスです。  
  
 使用して、ツールヒントのコンテンツの位置を指定するためにプロパティを設定する方法の例については、<xref:System.Windows.Controls.ToolTip>と<xref:System.Windows.Controls.ToolTipService>プロパティを参照してください[ツールヒントを配置](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md)です。  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a>ツールヒントのスタイル設定  
 スタイルを設定することができます、<xref:System.Windows.Controls.ToolTip>カスタムを定義することによって<xref:System.Windows.Style>です。 次の例では定義、<xref:System.Windows.Style>と呼ばれる`Simple`の配置をオフセットする方法を示す、<xref:System.Windows.Controls.ToolTip>を設定して、外観を変更し、 <xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>、 <xref:System.Windows.Controls.Control.FontSize%2A>、および<xref:System.Windows.Controls.Control.FontWeight%2A>です。  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>ToolTipService の時間間隔プロパティの使用  
 <xref:System.Windows.Controls.ToolTipService> 、次のプロパティにツールヒントを設定する時刻を表示するクラスが用意されています: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>、 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>、および<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>です。  
  
 使用して、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>と<xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>プロパティで、遅延を指定する通常の簡単な前に、<xref:System.Windows.Controls.ToolTip>が表示されますおよび期間を指定にも、<xref:System.Windows.Controls.ToolTip>表示されたままです。 詳細については、「[ How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/en-us/618e05ef-f2bf-4a53-a0f4-aacb49918bd7)」を参照してください。  
  
 <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>プロパティ間にマウス ポインターをすばやく移動するときに初期遅延なしのさまざまなコントロールのツールヒントが表示されるかどうかがします。 詳細については、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>プロパティを参照してください[BetweenShowDelay プロパティを使用して](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md)です。  
  
 次の例では、ツールヒントのこれらのプロパティを設定する方法を示します。  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [データ バインドに関する「方法」トピック](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
