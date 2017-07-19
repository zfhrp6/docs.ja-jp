---
title: "方法 : ListView の列の水平方向の配置を変更する | Microsoft Docs"
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
  - "ListView コントロール, 水平方向の配置"
ms.assetid: b9573e44-9dad-4d14-939c-7859ca372758
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : ListView の列の水平方向の配置を変更する
既定では、<xref:System.Windows.Controls.ListViewItem> の各列の内容は左揃えで表示されます。  <xref:System.Windows.DataTemplate> を使用し、<xref:System.Windows.DataTemplate> 内の要素の <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティを設定すると、各列の配置を変更できます。  このトピックでは、<xref:System.Windows.Controls.ListView> の内容の既定の配置について、および <xref:System.Windows.Controls.ListView> の特定の列の配置を変更する方法について説明します。  
  
## 使用例  
 次の例では、`Title` 列および `ISBN` 列のデータは左揃えです。  
  
 [!code-xml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 `ISBN` 列の配置を変更するには、各 <xref:System.Windows.Controls.ListViewItem> の <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> プロパティを <xref:System.Windows.HorizontalAlignment> に設定する必要があります。こうすると、各 <xref:System.Windows.Controls.ListViewItem> の要素を各列の幅全体に広げて配置できます。  <xref:System.Windows.Controls.ListView> はデータ ソースにバインドされているため、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> を設定するスタイルを作成する必要があります。  次に、<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> プロパティではなく <xref:System.Windows.DataTemplate> を使用して内容を表示する必要があります。  各テンプレートの `ISBN` を表示するために <xref:System.Windows.DataTemplate> に必要なのは、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティを <xref:System.Windows.HorizontalAlignment> に設定した <xref:System.Windows.Controls.TextBlock> のみです。  
  
 次の例では、`ISBN` 列を右揃えにするために必要なスタイルと <xref:System.Windows.DataTemplate> を定義し、<xref:System.Windows.Controls.GridViewColumn> を変更して <xref:System.Windows.DataTemplate> を参照しています。  
  
 [!code-xml[ListViewHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#3)]  
[!code-xml[ListViewHowTos#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#4)]  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [XMLDataProvider と XPath クエリを使用して XML データにバインドする](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)