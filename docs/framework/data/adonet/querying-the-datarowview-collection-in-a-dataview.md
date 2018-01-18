---
title: "DataView の DataRowView コレクションの照会"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a1912526d98dc7872470953e1bf61b72db191de5
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a><span data-ttu-id="e2b1a-102">DataView の DataRowView コレクションの照会</span><span class="sxs-lookup"><span data-stu-id="e2b1a-102">Querying the DataRowView Collection in a DataView</span></span>
<span data-ttu-id="e2b1a-103"><xref:System.Data.DataView> は、<xref:System.Data.DataRowView> オブジェクトの列挙可能なコレクションを公開します。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-103">The <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="e2b1a-104"><xref:System.Data.DataRowView> は、<xref:System.Data.DataRow> のカスタマイズされたビューを表し、<xref:System.Data.DataRow> の特定のバージョンをコントロールに表示します。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-104"><xref:System.Data.DataRowView> represents a customized view of a <xref:System.Data.DataRow> and displays a specific version of that <xref:System.Data.DataRow> in a control.</span></span> <span data-ttu-id="e2b1a-105"><xref:System.Data.DataRow> などのコントロールを通じて、<xref:System.Windows.Forms.DataGridView> のバージョンを 1 つだけ表示できます。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-105">Only one version of a <xref:System.Data.DataRow> can be displayed through a control, such as a <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="e2b1a-106"><xref:System.Data.DataRow> が <xref:System.Data.DataRowView> の <xref:System.Data.DataRowView.Row%2A> プロパティを使用して公開している <xref:System.Data.DataRowView> にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-106">You can access the <xref:System.Data.DataRow> that is exposed by the <xref:System.Data.DataRowView> through the <xref:System.Data.DataRowView.Row%2A> property of the <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="e2b1a-107"><xref:System.Data.DataRowView> を使用して値を表示している場合は、<xref:System.Data.DataView.RowStateFilter%2A> プロパティによって、基になる <xref:System.Data.DataRow> から公開される行バージョンが決まります。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-107">When you view values by using a <xref:System.Data.DataRowView>, the <xref:System.Data.DataView.RowStateFilter%2A> property determines which row version of the underlying <xref:System.Data.DataRow> is exposed.</span></span> <span data-ttu-id="e2b1a-108">使用して別の行バージョンにアクセスする方法について、<xref:System.Data.DataRow>を参照してください[行の状態と行のバージョン](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-108">For information about accessing different row versions using a <xref:System.Data.DataRow>, see [Row States and Row Versions](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span> <span data-ttu-id="e2b1a-109">のコレクション<xref:System.Data.DataRowView>によって公開されているオブジェクト、<xref:System.Data.DataView>は列挙可能な行うこともできます[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]それに対してクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-109">Because the collection of <xref:System.Data.DataRowView> objects exposed by the <xref:System.Data.DataView> is enumerable, you can use [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] to query over it.</span></span>  
  
 <span data-ttu-id="e2b1a-110">次の例では、`Product` テーブルに対して赤色の製品を照会し、そのクエリに基づくテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-110">The following example queries the `Product` table for red-colored products and creates a table from that query.</span></span> <span data-ttu-id="e2b1a-111">このテーブルから <xref:System.Data.DataView> を作成し、<xref:System.Data.DataView.RowStateFilter%2A> プロパティに、削除行と変更行を条件とするフィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-111">A <xref:System.Data.DataView> is created from the table and the <xref:System.Data.DataView.RowStateFilter%2A> property is set to filter on deleted and modified rows.</span></span> <span data-ttu-id="e2b1a-112">次に <xref:System.Data.DataView> を LINQ クエリのソースとして使用し、変更済みおよび削除済みの <xref:System.Data.DataRowView> オブジェクトを <xref:System.Windows.Forms.DataGridView> コントロールにバインドします。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-112">The <xref:System.Data.DataView> is then used as a source in a LINQ query, and the <xref:System.Data.DataRowView> objects that have been modified and deleted are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 <span data-ttu-id="e2b1a-113">次の例では、<xref:System.Windows.Forms.DataGridView> コントロールにバインドされたビューから製品のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-113">The following example creates a table of products from a view that is bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e2b1a-114"><xref:System.Data.DataView> に対して赤色の製品を照会し、並べ替えた結果を <xref:System.Windows.Forms.DataGridView> コントロールにバインドしています。</span><span class="sxs-lookup"><span data-stu-id="e2b1a-114">The <xref:System.Data.DataView> is queried for red-colored products and the ordered results are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a><span data-ttu-id="e2b1a-115">参照</span><span class="sxs-lookup"><span data-stu-id="e2b1a-115">See Also</span></span>  
 [<span data-ttu-id="e2b1a-116">データ バインディングと LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e2b1a-116">Data Binding and LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
