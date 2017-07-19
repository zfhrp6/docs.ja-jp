---
title: "方法: TreeView で TreeViewItem を検索する | Microsoft Docs"
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
  - "TreeView コントロール [WPF], 検索 (TreeViewItem を)"
  - "TreeViewItem [WPF], 検索"
ms.assetid: 72ecd40c-3939-4e01-b617-5e9daa6074d9
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法: TreeView で TreeViewItem を検索する
<xref:System.Windows.Controls.TreeView> コントロールは、階層データを表示するための便利な方法を提供します。  <xref:System.Windows.Controls.TreeView> をデータ ソースにバインドすると、<xref:System.Windows.Controls.TreeView.SelectedItem%2A> プロパティでは、選択したデータ オブジェクトをすばやく取得するための便利な方法を使用できるようになります。  通常、基になるデータ オブジェクトを使用することが最適な方法ですが、データが含まれている <xref:System.Windows.Controls.TreeViewItem> をプログラムで操作することが必要になる場合もあります。  たとえば、<xref:System.Windows.Controls.TreeViewItem> をプログラムで展開すること、または <xref:System.Windows.Controls.TreeView> 内の別の項目をプログラムで選択することが必要になる場合があります。  
  
 特定のデータ オブジェクトを含む <xref:System.Windows.Controls.TreeViewItem> を検索するには、<xref:System.Windows.Controls.TreeView> の各レベルを走査する必要があります。  また、パフォーマンスを向上させるために、<xref:System.Windows.Controls.TreeView> 内の項目を仮想化することもできます。  項目を仮想化する場合は、<xref:System.Windows.Controls.TreeViewItem> を取得して、そこにデータ オブジェクトが含まれているかどうかを確認することも必要です。  
  
## 使用例  
  
## Description  
 次の例では、<xref:System.Windows.Controls.TreeView> 内で特定のオブジェクトを検索し、オブジェクトが含まれている <xref:System.Windows.Controls.TreeViewItem> を返します。  この例では、子項目を検索できるように各 <xref:System.Windows.Controls.TreeViewItem> をインスタンス化する必要があります。  この例は、<xref:System.Windows.Controls.TreeView> に仮想化された項目がない場合も適用できます。  
  
> [!NOTE]
>  次の例は、基になるデータ モデルに関係なく、あらゆる <xref:System.Windows.Controls.TreeView> に適用できます。オブジェクトが見つかるまで、それぞれの <xref:System.Windows.Controls.TreeViewItem> を検索します。  より優れたパフォーマンスを実現するもう 1 つの方法は、データ モデル内で特定のオブジェクトを検索し、データ階層内のその場所を追跡して、<xref:System.Windows.Controls.TreeView> 内の対応する <xref:System.Windows.Controls.TreeViewItem> を見つけることです。  ただし、より優れたパフォーマンスを実現する方法は、データ モデルについての知識を必要とし、任意の <xref:System.Windows.Controls.TreeView> について一般化することはできません。  
  
## コード  
 [!code-csharp[TreeViewFindTVI#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[TreeViewFindTVI#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#1)]  
  
 前のコードは、`BringIntoView` という名前のメソッドを公開するカスタム <xref:System.Windows.Controls.VirtualizingStackPanel> に依存します。  次のコードは、カスタム <xref:System.Windows.Controls.VirtualizingStackPanel> を定義します。  
  
 [!code-csharp[TreeViewFindTVI#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml.cs#2)]
 [!code-vb[TreeViewFindTVI#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TreeViewFindTVI/VisualBasic/MainWindow.xaml.vb#2)]  
  
 次の XAML は、カスタム <xref:System.Windows.Controls.VirtualizingStackPanel> を使用する <xref:System.Windows.Controls.TreeView> を作成する方法を示します。  
  
 [!code-xml[TreeViewFindTVI#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewFindTVI/CSharp/MainWindow.xaml#3)]  
  
## 参照  
 [TreeView のパフォーマンスを改善する](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md)