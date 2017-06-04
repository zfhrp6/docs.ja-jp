---
title: "方法 : 深度がわからないデータに TreeView をバインドする | Microsoft Docs"
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
  - "TreeView コントロール [WPF], バインド (深さがわからないデータに)"
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 深度がわからないデータに TreeView をバインドする
深度がわからないデータ ソースに <xref:System.Windows.Controls.TreeView> をバインドすることが必要になる場合があります。  たとえば、フォルダー内にフォルダーが含まれる可能性のあるファイル システムなど、データが再帰的な性質を持つ場合や、従業員が他の従業員を直属の部下として持つ企業の組織構造などの場合があります。  
  
 データ ソースには階層的なオブジェクト モデルが必要です。  たとえば、`Employee` には、従業員の直属の部下である Employee オブジェクトのコレクションが含まれることが考えられます。  データが階層的ではない方法で表現されている場合は、そのデータの階層的な表現を作成する必要があります。  
  
 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=fullName> プロパティを設定するときに、<xref:System.Windows.Controls.ItemsControl> がそれぞれの子項目用に <xref:System.Windows.Controls.ItemsControl> を生成する場合、子の <xref:System.Windows.Controls.ItemsControl> は親と同じ <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> を使用します。  たとえば、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> プロパティをデータ バインド <xref:System.Windows.Controls.TreeView> に設定する場合、生成される各 <xref:System.Windows.Controls.TreeViewItem> は、<xref:System.Windows.Controls.TreeView> の <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> プロパティに割り当てられた <xref:System.Windows.DataTemplate> を使用します。  
  
 <xref:System.Windows.HierarchicalDataTemplate> は、データ テンプレートで、<xref:System.Windows.Controls.TreeViewItem> 用の <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>、または任意の <xref:System.Windows.Controls.HeaderedItemsControl> を指定できるようにします。  <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=fullName> プロパティを設定すると、<xref:System.Windows.HierarchicalDataTemplate> の適用時にその値が使用されます。  <xref:System.Windows.HierarchicalDataTemplate> を使用することによって、<xref:System.Windows.Controls.TreeView> 内の各 <xref:System.Windows.Controls.TreeViewItem> 用に <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> を再帰的に設定できます。  
  
## 使用例  
 次の例は、<xref:System.Windows.Controls.TreeView> を階層データにバインドし、<xref:System.Windows.HierarchicalDataTemplate> を使用して各 <xref:System.Windows.Controls.TreeViewItem> 用に <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> を指定する方法を示しています。  <xref:System.Windows.Controls.TreeView> は、社内の従業員を表す XML データにバインドします。  各 `Employee` 要素に他の `Employee` 要素を含めることによって、だれがだれの部下であるかを示すことができます。  データは再帰的であるため、<xref:System.Windows.HierarchicalDataTemplate> を各レベルに適用することができます。  
  
 [!code-xml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)