---
title: "方法 : ADO.NET データ ソースにバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 760b59bfa0d556974109ccc0211c021ee76df5dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="42742-102">方法 : ADO.NET データ ソースにバインドする</span><span class="sxs-lookup"><span data-stu-id="42742-102">How to: Bind to an ADO.NET Data Source</span></span>
<span data-ttu-id="42742-103">この例では、バインド、 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox>コントロールを[!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)]`DataSet`です。</span><span class="sxs-lookup"><span data-stu-id="42742-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42742-104">例</span><span class="sxs-lookup"><span data-stu-id="42742-104">Example</span></span>  
 <span data-ttu-id="42742-105">この例では、データ ソース (接続文字列で指定された `OleDbConnection` ファイル) に接続するために、`Access MDB` オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="42742-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="42742-106">接続が確立されると、`OleDbDataAdpater` オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="42742-106">After the connection is established, an `OleDbDataAdpater` object is created.</span></span> <span data-ttu-id="42742-107">`OleDbDataAdpater` オブジェクトは、select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] ステートメントを実行して、データベースからレコードセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="42742-107">The `OleDbDataAdpater` object executes a select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="42742-108">[!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] コマンドの結果は、`OleDbDataAdapter` の `Fill` メソッドを呼び出して、`DataSet` の `DataTable` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="42742-108">The results from the [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="42742-109">この例の `DataTable` には、`BookTable` という名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="42742-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="42742-110">設定して、<xref:System.Windows.FrameworkElement.DataContext%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>を`DataSet`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="42742-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="42742-111">バインドできます、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>のプロパティ、<xref:System.Windows.Controls.ListBox>に`BookTable`の`DataSet`:</span><span class="sxs-lookup"><span data-stu-id="42742-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="42742-112">`BookItemTemplate`<xref:System.Windows.DataTemplate>データの表示方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="42742-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 <span data-ttu-id="42742-113">`IntColorConverter` は、`int` を 1 つの色に変換します。</span><span class="sxs-lookup"><span data-stu-id="42742-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="42742-114">このコンバーターの使用で、 <xref:System.Windows.Controls.TextBlock.Background%2A> 、3 番目の色<xref:System.Windows.Controls.TextBlock>が緑で表示場合の値`NumPages`350 より小さいと、赤をそれ以外の場合は。</span><span class="sxs-lookup"><span data-stu-id="42742-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="42742-115">コンバーターの実装は、ここでは示されていません。</span><span class="sxs-lookup"><span data-stu-id="42742-115">The implementation of the converter is not shown here.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42742-116">参照</span><span class="sxs-lookup"><span data-stu-id="42742-116">See Also</span></span>  
 <xref:System.Windows.Data.BindingListCollectionView>  
 [<span data-ttu-id="42742-117">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="42742-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="42742-118">方法トピック</span><span class="sxs-lookup"><span data-stu-id="42742-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
