---
title: "方法 : GridView を使用して ListView コンテンツを表示する | Microsoft Docs"
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
  - "GridView, 表示 (ListView コンテンツを)"
  - "ListView コントロール, 表示 (GridView でコンテンツを)"
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : GridView を使用して ListView コンテンツを表示する
この例では、<xref:System.Windows.Controls.ListView> コントロールの <xref:System.Windows.Controls.GridView> 表示モードを定義する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.GridView> の表示モードは、<xref:System.Windows.Controls.GridViewColumn> オブジェクトを指定することで定義できます。  <xref:System.Windows.Controls.ListView> コントロールに対して指定されているデータ コンテンツにバインドする <xref:System.Windows.Controls.GridViewColumn> オブジェクトを定義する方法を次の例に示します。  この <xref:System.Windows.Controls.GridView> の例では、3 つの <xref:System.Windows.Controls.GridViewColumn> オブジェクトを指定します。これらのオブジェクトは、<xref:System.Windows.Controls.ListView> コントロールの <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> として設定されている `EmployeeInfoDataSource` の、`FirstName`、`LastName`、および `EmployeeNumber` フィールドにマップされています。  
  
 [!code-xml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 この例の表示結果を次の図に示します。  
  
 ![GridView 出力を含む ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.png "ListViewGridView")  
  
## 参照  
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.GridView>   
 [ListView の概要](../../../../docs/framework/wpf/controls/listview-overview.md)   
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)