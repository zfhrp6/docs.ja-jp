---
title: "方法 : Dock の値を取得または設定する | Microsoft Docs"
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
  - "Dock 値, 取得"
  - "Dock 値, 設定"
ms.assetid: fcf4ab8a-c7cd-4835-8d04-de1c999ab4a8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Dock の値を取得または設定する
次の例では、オブジェクトに <xref:System.Windows.Controls.Dock> 値を割り当てる方法を示します。  この例では、<xref:System.Windows.Controls.DockPanel> の <xref:System.Windows.Controls.DockPanel.GetDock%2A> メソッドと <xref:System.Windows.Controls.DockPanel.SetDock%2A> メソッドを使用します。  
  
## 使用例  
 この例では、<xref:System.Windows.Controls.TextBlock> 要素のインスタンスである `txt1` を作成し、<xref:System.Windows.Controls.DockPanel> の <xref:System.Windows.Controls.DockPanel.SetDock%2A> メソッドを使用して `Top` の <xref:System.Windows.Controls.Dock> 値を割り当てます。  次に、<xref:System.Windows.Controls.DockPanel.GetDock%2A> メソッドを使用して、<xref:System.Windows.Controls.TextBlock> 要素の <xref:System.Windows.Controls.TextBlock.Text%2A> に <xref:System.Windows.Controls.Dock> プロパティの値を追加します。  最後に、<xref:System.Windows.Controls.TextBlock> 要素を、親 <xref:System.Windows.Controls.DockPanel> である `dp1` に追加します。  
  
 [!code-csharp[DockPanelSetDock#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelSetDock/CSharp/DockPanel_SetDock.cs#1)]
 [!code-vb[DockPanelSetDock#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelSetDock/VisualBasic/DockPanel_SetDock.vb#1)]  
  
## 参照  
 <xref:System.Windows.Controls.DockPanel>   
 <xref:System.Windows.Controls.DockPanel.GetDock%2A>   
 <xref:System.Windows.Controls.DockPanel.SetDock%2A>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)