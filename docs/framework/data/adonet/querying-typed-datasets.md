---
title: 型指定された DataSet のクエリ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 30a6512202615590a4b399b8ce7173b213a8873c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353486"
---
# <a name="querying-typed-datasets"></a><span data-ttu-id="4c7d0-102">型指定された DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="4c7d0-102">Querying Typed DataSets</span></span>
<span data-ttu-id="4c7d0-103">アプリケーションのデザイン時に <xref:System.Data.DataSet> のスキーマがわかっている場合は、<xref:System.Data.DataSet> を使用するときに、型指定された [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を用いることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-103">If the schema of the <xref:System.Data.DataSet> is known at application design time, we recommend that you use a typed <xref:System.Data.DataSet> when using [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="4c7d0-104">型指定された<xref:System.Data.DataSet>から派生したクラスには、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-104">A typed <xref:System.Data.DataSet> is a class that derives from a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4c7d0-105">したがって、型指定されたデータセットは <xref:System.Data.DataSet> のすべてのメソッド、イベント、およびプロパティを継承します。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-105">As such, it inherits all the methods, events, and properties of a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4c7d0-106">さらに、型指定された<xref:System.Data.DataSet>厳密に型指定されたメソッド、イベント、およびプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-106">Additionally, a typed <xref:System.Data.DataSet> provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="4c7d0-107">つまり、コレクションベースのメソッドを使用せずに名前でテーブルおよび列にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-107">This means that you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="4c7d0-108">これによりクエリが簡素化され、読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-108">This makes queries simpler and more readable.</span></span> <span data-ttu-id="4c7d0-109">詳細については、次を参照してください。[型指定されたデータセット](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-109">For more information, see [Typed DataSets](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md).</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="4c7d0-110"> 型指定されたに対するクエリもサポート<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-110"> also supports querying over a typed <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="4c7d0-111">型指定された<xref:System.Data.DataSet>、ジェネリックを使用する必要はありません<xref:System.Data.DataRowExtensions.Field%2A>メソッドまたは<xref:System.Data.DataRowExtensions.SetField%2A>列データにアクセスするメソッド。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-111">With a typed <xref:System.Data.DataSet>, you do not have to use the generic <xref:System.Data.DataRowExtensions.Field%2A> method or <xref:System.Data.DataRowExtensions.SetField%2A> method to access column data.</span></span>  <span data-ttu-id="4c7d0-112">型情報が含まれているために、プロパティ名はコンパイル時に使用できる、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-112">Property names are available at compile time because the type information is included in the <xref:System.Data.DataSet>.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="4c7d0-113"> 実行時の代わりに、コードがコンパイルされるときに、型の不一致エラーがキャッチできるように、適切な型として列の値へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-113"> provides access to column values as the correct type, so that type mismatch errors are caught when the code is compiled instead of at run time.</span></span>  
  
 <span data-ttu-id="4c7d0-114">型指定された <xref:System.Data.DataSet> に対してクエリを実行するには、[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] のデータセット デザイナーを使用してあらかじめクラスを生成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-114">Before you can begin querying a typed <xref:System.Data.DataSet>, you must generate the class by using the DataSet Designer in [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)].</span></span>  <span data-ttu-id="4c7d0-115">詳細については、[データセットの作成と構成](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-115">For more information, see [Create and configure datasets](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c7d0-116">例</span><span class="sxs-lookup"><span data-stu-id="4c7d0-116">Example</span></span>  
 <span data-ttu-id="4c7d0-117">次の例では、型指定された <xref:System.Data.DataSet> に対してクエリを実行しています。</span><span class="sxs-lookup"><span data-stu-id="4c7d0-117">The following example shows a query over a typed <xref:System.Data.DataSet>:</span></span>  
  
```csharp  
var query = from o in orders  
            where o.OnlineOrderFlag == true  
            select new { o.SalesOrderID,  
                         o.OrderDate,  
                         o.SalesOrderNumber };  
  
foreach(var order in query)   
{  
    Console.WriteLine("{0}\t{1:d}\t{2}",   
order.SalesOrderID,   
order.OrderDate,   
order.SalesOrderNumber);  
}  
```  
  
```vb  
Dim orders = ds.Tables("SalesOrderHeader")  
  
Dim query = _  
       From o In orders _  
       Where o.OnlineOrderFlag = True _  
       Select New {SalesOrderID := o.SalesOrderID, _  
                   OrderDate := o.OrderDate, _  
                   SalesOrderNumber := o.SalesOrderNumber}  
  
For Each Dim onlineOrder In query  
 Console.WriteLine("{0}\t{1:d}\t{2}", _  
 onlineOrder.SalesOrderID, _  
 onlineOrder.OrderDate, _  
 onlineOrder.SalesOrderNumber)  
Next  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c7d0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c7d0-118">See Also</span></span>  
 [<span data-ttu-id="4c7d0-119">DataSet のクエリ</span><span class="sxs-lookup"><span data-stu-id="4c7d0-119">Querying DataSets</span></span>](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [<span data-ttu-id="4c7d0-120">複数テーブルにまたがるクエリ</span><span class="sxs-lookup"><span data-stu-id="4c7d0-120">Cross-Table Queries</span></span>](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [<span data-ttu-id="4c7d0-121">単一テーブルのクエリ</span><span class="sxs-lookup"><span data-stu-id="4c7d0-121">Single-Table Queries</span></span>](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
