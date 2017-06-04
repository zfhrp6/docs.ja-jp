---
title: "方法 : 単純または複雑な TreeView を作成する | Microsoft Docs"
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
  - "Control クラス, TreeView, 作成"
  - "TreeView コントロール, 作成"
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : 単純または複雑な TreeView を作成する
この例では、単純または複雑な <xref:System.Windows.Controls.TreeView> コントロールを作成する方法を示します。  
  
 <xref:System.Windows.Controls.TreeView> は <xref:System.Windows.Controls.TreeViewItem> コントロールの階層で構成されます。<xref:System.Windows.Controls.TreeViewItem> は、単純なテキスト文字列を含むことも、<xref:System.Windows.Controls.Button> コントロールや、コンテンツが埋め込まれた <xref:System.Windows.Controls.StackPanel> などのさらに複雑なコンテンツを含むこともできます。  <xref:System.Windows.Controls.TreeView> のコンテンツは、明示的に定義することも、データ ソースが提供することもできます。  このトピックでは、これらの概念の例を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.TreeViewItem> の <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> プロパティには、<xref:System.Windows.Controls.TreeView> がその項目に対して表示するコンテンツが含まれます。  <xref:System.Windows.Controls.TreeViewItem> は、子要素として <xref:System.Windows.Controls.TreeViewItem> を持つこともでき、これらの子要素は <xref:System.Windows.Controls.ItemsControl.Items%2A> プロパティを使用して定義できます。  
  
 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> プロパティにテキスト文字列を設定することで <xref:System.Windows.Controls.TreeViewItem> のコンテンツを明示的に定義する方法を次の例に示します。  
  
 [!code-xml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 <xref:System.Windows.Controls.Button> コントロールである <xref:System.Windows.Controls.ItemsControl.Items%2A> を定義することで <xref:System.Windows.Controls.TreeViewItem> の子要素を定義する方法を次の例に示します。  
  
 [!code-xml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 <xref:System.Windows.Data.XmlDataProvider> で <xref:System.Windows.Controls.TreeViewItem> のコンテンツを提供し、<xref:System.Windows.HierarchicalDataTemplate> でコンテンツの表示を定義して、<xref:System.Windows.Controls.TreeView> を作成する方法を次の例に示します。  
  
 [!code-xml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 <xref:System.Windows.Controls.TreeViewItem> のコンテンツとして、コンテンツが埋め込まれた <xref:System.Windows.Controls.DockPanel> コントロールを含む <xref:System.Windows.Controls.TreeView> を作成する方法を次の例に示します。  
  
 [!code-xml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## 参照  
 <xref:System.Windows.Controls.TreeView>   
 <xref:System.Windows.Controls.TreeViewItem>   
 [TreeView の概要](../../../../docs/framework/wpf/controls/treeview-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)