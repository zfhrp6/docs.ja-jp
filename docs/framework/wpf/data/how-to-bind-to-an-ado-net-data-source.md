---
title: "方法 : ADO.NET データ ソースにバインドする | Microsoft Docs"
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
  - "ADO.NET データ ソース, バインド"
  - "バインド, ADO.NET データ ソース"
  - "データ バインディング, バインド (ADO.NET データ ソースに)"
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : ADO.NET データ ソースにバインドする
この例では、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> コントロールを [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet` にバインドする方法を示します。  
  
## 使用例  
 ここでは、データ ソース \(接続文字列で指定された `Access MDB` ファイル\) に接続するために、`OleDbConnection` オブジェクトを使用します。  接続が確立されると、その後、`OleDbDataAdpater` オブジェクトが作成されます。  `OleDbDataAdpater` オブジェクトは、select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] ステートメントを使用して、データベースからレコードセットを取得します。  [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] コマンドの結果は、 `OleDbDataAdapter` の `Fill` メソッドを呼び出して、`DataSet` の `DataTable` に格納されます。  この例の `DataTable` には、`BookTable` という名前が付いています。  また、この例では、<xref:System.Windows.Controls.ListBox> の <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティを `DataSet` オブジェクトに設定します。  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 これで、<xref:System.Windows.Controls.ListBox> の <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティを、`DataSet` の `BookTable` にバインドできます。  
  
 [!code-xml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 `BookItemTemplate` は、データがどのように表示されるかを定義する <xref:System.Windows.DataTemplate> です。  
  
 [!code-xml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 `IntColorConverter` は、`int` を 1 つの色に変換します。  このコンバーターを使用すると、3 つ目の <xref:System.Windows.Controls.TextBlock> の <xref:System.Windows.Controls.TextBlock.Background%2A> の色は、`NumPages` の値が 350 未満の場合は緑で、それ以外の場合は赤で表示されます。  コンバーターの実装は、ここでは示されていません。  
  
## 参照  
 <xref:System.Windows.Data.BindingListCollectionView>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)