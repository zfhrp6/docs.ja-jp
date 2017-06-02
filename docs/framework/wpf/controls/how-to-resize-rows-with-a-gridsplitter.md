---
title: "方法 : GridSplitter を使用して行のサイズを変更する | Microsoft Docs"
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
  - "グリッド行, サイズ変更"
  - "GridSplitter コントロール, サイズ変更 (グリッド行の)"
  - "サイズ変更 (グリッド行の)"
ms.assetid: 2413a9f2-1d81-46ed-95cb-95ec8233eea2
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : GridSplitter を使用して行のサイズを変更する
この例では、水平 <xref:System.Windows.Controls.GridSplitter> を使用して、<xref:System.Windows.Controls.Grid> の寸法を変更せずに <xref:System.Windows.Controls.Grid> 内の行間の領域を再配分する方法を示します。  
  
## 使用例  
 **行の端に重なって表示される GridSplitter を作成する方法**  
  
 <xref:System.Windows.Controls.Grid> 内の隣接する行のサイズを変更する <xref:System.Windows.Controls.GridSplitter> を指定するには、サイズを変更する行の 1 つに <xref:System.Windows.Controls.Grid.Row%2A> [添付プロパティ](GTMT)を設定します。  <xref:System.Windows.Controls.Grid> に複数の列がある場合は、<xref:System.Windows.Controls.Grid.ColumnSpan%2A> 添付プロパティを設定して列の数を指定します。  次に、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> を <xref:System.Windows.VerticalAlignment> または <xref:System.Windows.VerticalAlignment> に設定します \(どちらの配置に設定するかは、サイズを変更する 2 行がどちらであるかによって異なります\)。  最後に、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> のプロパティを <xref:System.Windows.HorizontalAlignment> に設定します。  
  
 隣接する行のサイズを変更する、水平 <xref:System.Windows.Controls.GridSplitter> を定義する方法を次の例に示します。  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterRowOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterrowoverlay)]  
  
 固有の行を占有しない <xref:System.Windows.Controls.GridSplitter> は、<xref:System.Windows.Controls.Grid> 内の他のコントロールによって隠される場合があります。  この問題を回避する方法の詳細については、「[GridSplitter を表示されるようにする](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md)」を参照してください。  
  
 **行を占有する GridSplitter を作成する方法**  
  
 <xref:System.Windows.Controls.Grid> 内の行を占有する <xref:System.Windows.Controls.GridSplitter> を指定するには、サイズを変更する行の 1 つに <xref:System.Windows.Controls.Grid.Row%2A> [添付プロパティ](GTMT)を設定します。  <xref:System.Windows.Controls.Grid> に複数の列がある場合は、<xref:System.Windows.Controls.Grid.ColumnSpan%2A> 添付プロパティに列の数を設定します。  次に、<xref:System.Windows.FrameworkElement.VerticalAlignment%2A> を <xref:System.Windows.VerticalAlignment> に設定し、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> プロパティを <xref:System.Windows.HorizontalAlignment> に設定して、<xref:System.Windows.Controls.GridSplitter> を含む行の <xref:System.Windows.Controls.RowDefinition.Height%2A> を <xref:System.Windows.GridLength.Auto%2A> に設定します。  
  
 行を占有し、その行の両側の行のサイズを変更する水平 <xref:System.Windows.Controls.GridSplitter> を定義する方法を次の例に示します。  
  
 [!code-xml[GridSplitterRowColumn#GridSplitterEntireRowPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart1)]  
[!code-xml[GridSplitterRowColumn#GridSplitterEntireRowPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirerowpart2)]  
  
## 参照  
 <xref:System.Windows.Controls.GridSplitter>   
 [方法のトピック](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)