---
title: "方法 : GridView を実装する ListView の項目をグループ化する | Microsoft Docs"
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
  - "GridView コントロール, グループ化 (項目を)"
  - "グループ化 (GridView を実装する ListView で項目を)"
  - "ListView コントロール, グループ化 (GridView で項目を)"
ms.assetid: eebef25b-ddc6-424e-a66d-ea228d1bf33d
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : GridView を実装する ListView の項目をグループ化する
この例では、 <xref:System.Windows.Controls.ListView> コントロールの <xref:System.Windows.Controls.GridView> ビュー モードでグループの項目を表示する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.ListView> でグループの項目を表示するには、<xref:System.Windows.Data.CollectionViewSource> を定義します。  次の例では、 `Catalog` データ フィールドの値に従ってデータ項目をグループ化する <xref:System.Windows.Data.CollectionViewSource> を示します。  
  
 [!code-xml[GridViewWithGroups#GroupingCollectionViewSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#groupingcollectionviewsource)]  
  
 次の例では、前の例で定義される <xref:System.Windows.Data.CollectionViewSource> に、<xref:System.Windows.Controls.ListView> の <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> が設定されます。  また、この例では <xref:System.Windows.Controls.Expander> コントロールを実装する <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> も定義されます。  
  
 [!code-xml[GridViewWithGroups#ListViewGroups](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewgroups)]  
[!code-xml[GridViewWithGroups#ListViewEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewWithGroups/CS/Window1.xaml#listviewend)]  
  
## 参照  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [方法のトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)