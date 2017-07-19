---
title: "方法 : StackPanel または DockPanel を選択する | Microsoft Docs"
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
  - "コントロール [WPF], StackPanel"
  - "DockPanel コントロール, StackPanel コントロールとの比較"
  - "StackPanel コントロール, DockPanel コントロールとの比較"
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : StackPanel または DockPanel を選択する
この例では、<xref:System.Windows.Controls.Panel> のコンテンツをスタックする場合に、<xref:System.Windows.Controls.StackPanel> または <xref:System.Windows.Controls.DockPanel> のどちらを使用するかを選択する方法を示します。  
  
## 使用例  
 子要素のスタックには <xref:System.Windows.Controls.DockPanel> または <xref:System.Windows.Controls.StackPanel> のどちらも使用できますが、2 つのコントロールが必ずしも同じ結果を生成するとは限りません。  たとえば、子要素を入力する順序は <xref:System.Windows.Controls.DockPanel> 内の子要素のサイズに影響を与える可能性がありますが、<xref:System.Windows.Controls.StackPanel> 内の子要素のサイズには影響を与えません。  このような動作の違いが発生するのは、<xref:System.Windows.Controls.StackPanel> が <xref:System.Double>.<xref:System.Double.PositiveInfinity> でのスタッキング方向で計測するためです。しかし、<xref:System.Windows.Controls.DockPanel> は使用可能なサイズだけを計測します。  
  
 次の例では、<xref:System.Windows.Controls.DockPanel> と <xref:System.Windows.Controls.StackPanel> の主な相違点を示します。  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## 参照  
 <xref:System.Windows.Controls.StackPanel>   
 <xref:System.Windows.Controls.DockPanel>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)