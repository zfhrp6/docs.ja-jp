---
title: "方法 : DockPanel 要素を使用して領域を分割する | Microsoft Docs"
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
  - "コントロール [WPF], DockPanel"
  - "DockPanel コントロール, 分割 (領域を)"
  - "分割 (領域を)"
ms.assetid: a219b9e5-b205-4438-89b5-0a137ac463ab
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : DockPanel 要素を使用して領域を分割する
<xref:System.Windows.Controls.DockPanel> 要素を使用して、単純な[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] フレームワークを作成する例を次に示します。  <xref:System.Windows.Controls.DockPanel> パーティションは使用可能な領域をその子要素に分割します。  
  
## 使用例  
 この例では、<xref:System.Windows.Controls.DockPanel.Dock%2A> プロパティを使用します。このプロパティは、分割された領域の <xref:System.Windows.Controls.Dock> にある 2 つの同じ <xref:System.Windows.Controls.Border> 要素をドッキングするための[添付プロパティ](GTMT)です。  3 つ目の <xref:System.Windows.Controls.Border> 要素は、幅が 200 ピクセルに設定されて <xref:System.Windows.Controls.Dock> にドッキングされます。  4 つ目の <xref:System.Windows.Controls.Border> は、画面の <xref:System.Windows.Controls.Dock> にドッキングされます。  最後の <xref:System.Windows.Controls.Border> 要素は、残りの領域を自動的に満たします。  
  
 [!code-cpp[DockPanelOvwSample#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xml[DockPanelOvwSample#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
> [!NOTE]
>  既定では、<xref:System.Windows.Controls.DockPanel> 要素の最後の子は、割り当てられていない残りの領域を満たします。  この動作が不要な場合は、`LastChildFill="False"` を設定します。  
  
 コンパイルされたアプリケーションは、下に示すような新しい UI を生成します。  
  
 ![一般的な DockPanel シナリオ。](../../../../docs/framework/wpf/controls/media/panel-intro-dockpanel.png "panel\_intro\_dockpanel")  
  
## 参照  
 <xref:System.Windows.Controls.DockPanel>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)