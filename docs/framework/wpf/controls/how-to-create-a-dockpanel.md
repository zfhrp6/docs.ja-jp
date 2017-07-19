---
title: "方法 : DockPanel を作成する | Microsoft Docs"
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
  - "コントロール, DockPanel"
  - "DockPanel コントロール, 作成"
ms.assetid: 9194f663-e279-4f1a-86d7-125a57d05c6f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : DockPanel を作成する
## 使用例  
 次の例では、コードを使用して、<xref:System.Windows.Controls.DockPanel> のインスタンスを作成および使用します。  5 つの <xref:System.Windows.Shapes.Rectangle> 要素を作成し、それらを親 <xref:System.Windows.Controls.DockPanel> の内部に配置 \(ドッキング\) することで領域を分割する方法を次の例に示します。  既定の設定を維持した場合、最後の四角形は割り当てられていない残りの領域全体を満たします。  
  
 [!code-csharp[DockPanelCode#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DockPanelCode/CSharp/DockPanel_Code.cs#1)]
 [!code-vb[DockPanelCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelCode/VisualBasic/dockpanel_vb.vb#1)]  
  
## 参照  
 <xref:System.Windows.Controls.DockPanel>   
 <xref:System.Windows.Controls.Dock>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)