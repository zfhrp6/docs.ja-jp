---
title: "方法 : TreeView のパフォーマンスを改善する | Microsoft Docs"
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
  - "TreeView コントロール [WPF], 向上 (パフォーマンスを)"
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : TreeView のパフォーマンスを改善する
<xref:System.Windows.Controls.TreeView> に多くの項目が含まれていると、読み込みに時間を要するためにユーザー インターフェイスに大きな遅れが生じる可能性があります。  <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> 添付プロパティを `true` に設定することによって、読み込み時間を改善できます。  また、マウス ホイールの操作、またはスクロール バーのつまみのドラッグによる <xref:System.Windows.Controls.TreeView> のスクロール時に、UI の反応が遅れる場合があります。  <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> 添付プロパティを <xref:System.Windows.Controls.VirtualizationMode> に設定することで、ユーザーがスクロールを実行したときの <xref:System.Windows.Controls.TreeView> のパフォーマンスを向上させることができます。  
  
## 使用例  
  
## Description  
 <xref:System.Windows.Controls.TreeView> を作成する例を次に示します。この例では、<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=fullName> を true に設定し、<xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> を <xref:System.Windows.Controls.VirtualizationMode> に設定することにより、パフォーマンスを最適化します。  
  
## コード  
 [!code-xml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 次の例は、前の例で使用するデータを示しています。  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## 参照  
 [コントロール](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)