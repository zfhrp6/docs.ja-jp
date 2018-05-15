---
title: DataRelation の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: 451ee0eee466efca86345ea7112e9b178a2c66e2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="adding-datarelations"></a><span data-ttu-id="f5c1b-102">DataRelation の追加</span><span class="sxs-lookup"><span data-stu-id="f5c1b-102">Adding DataRelations</span></span>
<span data-ttu-id="f5c1b-103">複数の <xref:System.Data.DataSet> オブジェクトを含む <xref:System.Data.DataTable> では、<xref:System.Data.DataRelation> オブジェクトを使用して 1 つのテーブルを別のテーブルに関連付けたり、テーブル間を移動したり、関連付けたテーブルから子または親の行を戻したりできます。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="f5c1b-104">作成に必要な引数、 **DataRelation**の名前は、 **DataRelation**作成されており、1 つ以上の配列<xref:System.Data.DataColumn>親と子として機能する列への参照リレーションシップの列です。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="f5c1b-105">作成した後、 **DataRelation**テーブル間を移動して値の取得に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="f5c1b-106">追加する、 **DataRelation**を<xref:System.Data.DataSet>追加すると、既定では、<xref:System.Data.UniqueConstraint>親テーブルに、<xref:System.Data.ForeignKeyConstraint>する子テーブルにします。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="f5c1b-107">これらの既定の制約の詳細については、次を参照してください。 [DataTable の制約](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-107">For more information about these default constraints, see [DataTable Constraints](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="f5c1b-108">次のコード例を作成、 **DataRelation** 2 つを使用して<xref:System.Data.DataTable>内のオブジェクト、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f5c1b-109">各<xref:System.Data.DataTable>という名前の列を含む**CustID**、2 つの間のリンクとして機能する<xref:System.Data.DataTable>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="f5c1b-110">この例は、1 つを追加**DataRelation**に、**リレーション**のコレクション、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="f5c1b-111">この例の最初の引数の名前を指定する、 **DataRelation**作成中です。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="f5c1b-112">2 番目の引数は、親を設定します。 **DataColumn** 3 番目の引数、子の設定と**DataColumn**です。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="f5c1b-113">A **DataRelation**も、**入れ子になった**プロパティに設定すると**true**、親テーブルから関連する行の入れ子にする子テーブルの行が使用して XML 要素として書き込まれるときに<xref:System.Data.DataSet.WriteXml%2A>です。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="f5c1b-114">詳しくは、「[DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5c1b-114">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5c1b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5c1b-115">See Also</span></span>  
 [<span data-ttu-id="f5c1b-116">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="f5c1b-116">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="f5c1b-117">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="f5c1b-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
