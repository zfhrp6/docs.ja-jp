---
title: "方法 : グリッド要素を作成する | Microsoft Docs"
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
  - "グリッド コントロール, 作成, グリッド インスタンス"
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : グリッド要素を作成する
## 使用例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] またはコードを使用して、<xref:System.Windows.Controls.Grid> のインスタンスを作成および使用する方法を次の例に示します。  次の例では、3 つの <xref:System.Windows.Controls.ColumnDefinition> オブジェクトおよび 3 つの <xref:System.Windows.Controls.RowDefinition> オブジェクトを使用して、ワークシートに見られるような、9 つのセルから成るグリッドを作成します。  各セルはデータを表す <xref:System.Windows.Controls.TextBlock> 要素を含み、一番上の行は <xref:System.Windows.Controls.Grid.ColumnSpan%2A> プロパティが適用される <xref:System.Windows.Controls.TextBlock> を含みます。  各セルの境界を表示するには、<xref:System.Windows.Controls.Grid.ShowGridLines%2A> プロパティを有効にします。  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## 参照  
 <xref:System.Windows.Controls.Grid>   
 [パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)