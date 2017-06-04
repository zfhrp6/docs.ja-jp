---
title: "方法 : ToolTip を配置する | Microsoft Docs"
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
  - "配置 (ToolTip コントロールを)"
  - "ToolTip コントロール, 配置"
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : ToolTip を配置する
画面上でのツールヒントの位置を指定する方法を次の例に示します。  
  
## 使用例  
 ツールヒントを配置するには、<xref:System.Windows.Controls.ToolTip> クラスと <xref:System.Windows.Controls.ToolTipService> クラスの両方で定義されている 5 つのプロパティのセットを使用します。  これら 5 つのプロパティの 2 つのセットと、そのクラス別の参考資料へのリンクを次の表に示します。  
  
### クラス別の対応するツールヒント プロパティ  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=fullName> クラスのプロパティ|<xref:System.Windows.Controls.ToolTipService?displayProperty=fullName> クラスのプロパティ|  
|-------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=fullName>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=fullName>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=fullName>|  
  
 ツールヒントのコンテンツを <xref:System.Windows.Controls.ToolTip> オブジェクトを使用して定義する場合は、どちらのクラスのプロパティも使用できます。ただし、<xref:System.Windows.Controls.ToolTipService> のプロパティが優先されます。  <xref:System.Windows.Controls.ToolTip> オブジェクトとして定義されていないツールヒントには、<xref:System.Windows.Controls.ToolTipService> のプロパティを使用してください。  
  
 これらのプロパティを使用してツールヒントを配置する方法を以下の図に示します。  これらの図の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] の例では、<xref:System.Windows.Controls.ToolTip> クラスで定義されるプロパティの設定方法を示していますが、<xref:System.Windows.Controls.ToolTipService> クラスの対応する各プロパティも、同じレイアウト ルールに従います。  Placement プロパティに使用できる値の詳細については、「[ポップアップの配置動作](../../../../docs/framework/wpf/controls/popup-placement-behavior.md)」を参照してください。  
  
 ![ツールヒント配置](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")  
Placement プロパティを使用して ToolTip を配置する  
  
 ![配置四角形を使用したツールヒントの配置](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")  
Placement および PlacementRectangle プロパティを使用して ToolTip を配置する  
  
 ![ツールヒント配置のダイアグラム](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")  
Placement、PlacementRectangle、および Offset プロパティを使用して ToolTip を配置する  
  
 <xref:System.Windows.Controls.ToolTip> のプロパティを使用して <xref:System.Windows.Controls.ToolTip> オブジェクトをコンテンツとするツールヒントの位置を指定する方法を次の例に示します。  
  
 [!code-xml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <xref:System.Windows.Controls.ToolTipService> のプロパティを使用して、コンテンツが <xref:System.Windows.Controls.ToolTip> オブジェクトでないツールヒントの位置を指定する方法を次の例に示します。  
  
 [!code-xml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## 参照  
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipService>   
 [方法のトピック](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)   
 [ToolTip の概要](../../../../docs/framework/wpf/controls/tooltip-overview.md)   
 [Use the ContextMenuService and ToolTipService](http://msdn.microsoft.com/ja-jp/809b0e9c-d612-4cda-b8af-1a698c68f4d1)