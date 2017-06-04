---
title: "方法 : GridViewRowPresenter を使用してデータを表示する | Microsoft Docs"
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
  - "表示 (GridViewRowPresenter でデータを)"
  - "GridViewRowPresenter"
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : GridViewRowPresenter を使用してデータを表示する
この例では、<xref:System.Windows.Controls.GridViewRowPresenter> オブジェクトと <xref:System.Windows.Controls.GridViewHeaderRowPresenter> オブジェクトを使用して、列内にデータを表示する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.GridViewRowPresenter> オブジェクトと <xref:System.Windows.Controls.GridViewHeaderRowPresenter> オブジェクトを使用して、<xref:System.DateTime> オブジェクトの <xref:System.DateTime.DayOfWeek%2A> と <xref:System.DateTime.Year%2A> を表示する <xref:System.Windows.Controls.GridViewColumnCollection> を指定する方法を次の例に示します。  この例では、<xref:System.Windows.Controls.GridViewColumn> の <xref:System.Windows.Controls.GridViewColumn.Header%2A> の <xref:System.Windows.Style> も定義します。  
  
 [!code-xml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## 参照  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>   
 <xref:System.Windows.Controls.GridViewRowPresenter>   
 <xref:System.Windows.Controls.GridViewColumnCollection>   
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)