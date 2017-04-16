---
title: "方法 : テンプレートを使用して、GridView を使用する ListView のスタイルを設定する | Microsoft Docs"
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
  - "ListView コントロール, スタイル設定"
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : テンプレートを使用して、GridView を使用する ListView のスタイルを設定する
<xref:System.Windows.DataTemplate> オブジェクトと <xref:System.Windows.Style> オブジェクトを使用して、<xref:System.Windows.Controls.GridView> 表示モードを使用する <xref:System.Windows.Controls.ListView> コントロールの外観を指定する方法を次の例に示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Controls.GridViewColumn> の列ヘッダーの外観をカスタマイズする <xref:System.Windows.Style> オブジェクトと <xref:System.Windows.DataTemplate> オブジェクトを示します。  
  
 [!code-xml[ListViewTemplate#GridViewHeaderStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xml[ListViewTemplate#GridViewHeaderTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 これらの <xref:System.Windows.Style> オブジェクトと <xref:System.Windows.DataTemplate> オブジェクトを使用して <xref:System.Windows.Controls.GridViewColumn> の <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> プロパティと <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> プロパティを設定する方法を次の例に示します。  <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> プロパティでは、列のセルのコンテンツが定義されています。  
  
 [!code-xml[ListViewTemplate#GridViewColumnTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A> と <xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> の他にも、<xref:System.Windows.Controls.GridView> コントロールには、列ヘッダーの外観をカスタマイズするために使用できるプロパティがいくつかあります。  詳細については、「[GridView の列ヘッダー スタイルおｙびテンプレートの概要](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)」を参照してください。  
  
 次の例では、<xref:System.Windows.Controls.GridViewColumn> のセルの外観をカスタマイズする <xref:System.Windows.DataTemplate> を定義する方法を示します。  
  
 [!code-xml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 次の例では、この <xref:System.Windows.DataTemplate> を使用して <xref:System.Windows.Controls.GridViewColumn> セルのコンテンツを定義する方法を示します。  このテンプレートは、前の <xref:System.Windows.Controls.GridViewColumn> の例で示した <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> プロパティの代わりに使用されています。  
  
 [!code-xml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## 参照  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)