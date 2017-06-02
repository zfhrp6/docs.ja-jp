---
title: "方法 : GridSplitter を使用して列のサイズを変更する | Microsoft Docs"
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
  - "グリッド列, サイズ変更"
  - "GridSplitter コントロール, サイズ変更 (グリッド列の)"
  - "サイズ変更 (グリッド列の)"
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : GridSplitter を使用して列のサイズを変更する
この例では、<xref:System.Windows.Controls.Grid> の寸法を変更せずに <xref:System.Windows.Controls.Grid> 内の列の間で領域を再配分するために垂直 <xref:System.Windows.Controls.GridSplitter> を作成する方法を示します。  
  
## 使用例  
 **列の端に重なって表示される GridSplitter を作成する方法**  
  
 <xref:System.Windows.Controls.Grid> 内の隣接する列のサイズを変更する <xref:System.Windows.Controls.GridSplitter> を指定するには、サイズを変更する列の 1 つに <xref:System.Windows.Controls.Grid.Column%2A> [添付プロパティ](GTMT)を設定します。  <xref:System.Windows.Controls.Grid> に複数の行がある場合は、<xref:System.Windows.Controls.Grid.RowSpan%2A> 添付プロパティに行の数を設定します。  次に、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティを <xref:System.Windows.HorizontalAlignment> または <xref:System.Windows.HorizontalAlignment> に設定します \(どちらの配置に設定するかはサイズを変更する 2 列によって異なります\)。  最後に、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> プロパティを <xref:System.Windows.VerticalAlignment> に設定します。  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 独自の列を持たない <xref:System.Windows.Controls.GridSplitter> は、<xref:System.Windows.Controls.Grid> 内の他のコントロールによって隠される場合があります。  この問題を回避する方法の詳細については、「[GridSplitter を表示されるようにする](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)」を参照してください。  
  
 **列を占有する GridSplitter を作成する方法**  
  
 <xref:System.Windows.Controls.Grid> 内の列を占有する <xref:System.Windows.Controls.GridSplitter> を指定するには、サイズを変更する列の 1 つに <xref:System.Windows.Controls.Grid.Column%2A> [添付プロパティ](GTMT)を設定します。  Grid に複数の行がある場合は、<xref:System.Windows.Controls.Grid.RowSpan%2A> 添付プロパティに行の数を設定します。  次に、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> を <xref:System.Windows.HorizontalAlignment> に設定し、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> プロパティを <xref:System.Windows.VerticalAlignment> に設定して、<xref:System.Windows.Controls.GridSplitter> を含む列の <xref:System.Windows.Controls.ColumnDefinition.Width%2A> を <xref:System.Windows.GridLength.Auto%2A> に設定します。  
  
 列を占有し、その列の両側の列のサイズを変更する垂直 <xref:System.Windows.Controls.GridSplitter> を定義する方法を次の例に示します。  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## 参照  
 <xref:System.Windows.Controls.GridSplitter>   
 [方法のトピック](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)