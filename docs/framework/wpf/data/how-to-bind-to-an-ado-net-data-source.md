---
title: '方法 : ADO.NET データ ソースにバインドする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: c9e16b9fd100eb9aec7bee2f94307aa80371d5ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556862"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>方法 : ADO.NET データ ソースにバインドする
この例では、バインド、 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox>コントロールを[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)]`DataSet`です。  
  
## <a name="example"></a>例  
 この例では、データ ソース (接続文字列で指定された `OleDbConnection` ファイル) に接続するために、`Access MDB` オブジェクトを使用します。 接続が確立されると、`OleDbDataAdpater` オブジェクトが作成されます。 `OleDbDataAdpater` オブジェクトは、select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] ステートメントを実行して、データベースからレコードセットを取得します。 [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] コマンドの結果は、`OleDbDataAdapter` の `Fill` メソッドを呼び出して、`DataSet` の `DataTable` に格納されます。 この例の `DataTable` には、`BookTable` という名前が付いています。 設定して、<xref:System.Windows.FrameworkElement.DataContext%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>を`DataSet`オブジェクト。  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 バインドできます、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>に`BookTable`の`DataSet`:  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 `BookItemTemplate` <xref:System.Windows.DataTemplate>データの表示方法を定義します。  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 `IntColorConverter` は、`int` を 1 つの色に変換します。 このコンバーターの使用で、 <xref:System.Windows.Controls.TextBlock.Background%2A> 、3 番目の色<xref:System.Windows.Controls.TextBlock>が緑で表示場合の値`NumPages`350 より小さいと、赤をそれ以外の場合は。 コンバーターの実装は、ここでは示されていません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Data.BindingListCollectionView>  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
