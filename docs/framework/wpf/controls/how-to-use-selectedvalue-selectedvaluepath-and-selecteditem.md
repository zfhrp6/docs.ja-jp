---
title: "方法 : SelectedValue、SelectedValuePath、および SelectedItem を使用する | Microsoft Docs"
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
  - "Control クラス, SelectedItem プロパティ"
  - "Control クラス, SelectedValue プロパティ"
  - "Control クラス, SelectedValuePath プロパティ"
  - "Control クラス, TreeView プロパティ"
  - "SelectedValue, SelectedItem プロパティ"
  - "SelectedValue, SelectedValuePath プロパティ"
  - "TreeView コントロール, SelectedItem プロパティ"
  - "TreeView コントロール, SelectedValue プロパティ"
  - "TreeView コントロール, SelectedValuePath プロパティ"
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : SelectedValue、SelectedValuePath、および SelectedItem を使用する
この例では、<xref:System.Windows.Controls.TreeView.SelectedValue%2A> および <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> プロパティを使用して、<xref:System.Windows.Controls.TreeView> の <xref:System.Windows.Controls.TreeView.SelectedItem%2A> の値を指定する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> プロパティは、<xref:System.Windows.Controls.TreeView> の <xref:System.Windows.Controls.TreeView.SelectedItem%2A> に対して <xref:System.Windows.Controls.TreeView.SelectedValue%2A> を指定する方法を提供します。  <xref:System.Windows.Controls.TreeView.SelectedItem%2A> は <xref:System.Windows.Controls.ItemsControl.Items%2A> コレクション内のオブジェクトを表し、<xref:System.Windows.Controls.TreeView> は選択された項目の 1 つのプロパティの値を表示します。  <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> プロパティは、<xref:System.Windows.Controls.TreeView.SelectedValue%2A> プロパティの値の決定に使用されたプロパティへのパスを指定します。  このトピックの例で、この概念を示します。  
  
 次の例では、従業員情報を含む <xref:System.Windows.Data.XmlDataProvider> を示します。  
  
 [!code-xml[TreeViewSelectedValue#XMLDataProvider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 次の例は、`Employee` の `EmployeeName` と `EmployeeWorkDay` を表示する <xref:System.Windows.HierarchicalDataTemplate> を定義しています。  <xref:System.Windows.HierarchicalDataTemplate> では、`EmployeeNumber` をテンプレートの一部として指定していないことに注意してください。  
  
 [!code-xml[TreeViewSelectedValue#HierarchicalDataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 次の例は、前に定義された <xref:System.Windows.HierarchicalDataTemplate> を使用し、<xref:System.Windows.Controls.TreeView.SelectedValue%2A> プロパティを `EmployeeNumber` に設定する、<xref:System.Windows.Controls.TreeView> を示しています。  <xref:System.Windows.Controls.TreeView> で `EmployeeName` を選択すると、<xref:System.Windows.Controls.TreeView.SelectedItem%2A> プロパティは、選択された `EmployeeName` に対応する `EmployeeInfo` データ項目を返します。  ただし、この <xref:System.Windows.Controls.TreeView> の <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> は `EmployeeNumber` に設定されているため、<xref:System.Windows.Controls.TreeView.SelectedValue%2A> は `EmployeeNumber` に設定されます。  
  
 [!code-xml[TreeViewSelectedValue#SelectedValuePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## 参照  
 <xref:System.Windows.Controls.TreeView>   
 <xref:System.Windows.Controls.TreeViewItem>   
 [TreeView の概要](../../../../docs/framework/wpf/controls/treeview-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)