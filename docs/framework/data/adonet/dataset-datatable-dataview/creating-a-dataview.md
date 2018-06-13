---
title: DataView の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
ms.openlocfilehash: d118f97e425782dbdf89c7e5d1eccd4d371b419c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759115"
---
# <a name="creating-a-dataview"></a><span data-ttu-id="a4bce-102">DataView の作成</span><span class="sxs-lookup"><span data-stu-id="a4bce-102">Creating a DataView</span></span>
<span data-ttu-id="a4bce-103"><xref:System.Data.DataView> は 2 とおりの方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="a4bce-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="a4bce-104">使用することができます、 **DataView**コンス トラクターを作成できますへの参照、<xref:System.Data.DataTable.DefaultView%2A>のプロパティ、<xref:System.Data.DataTable>です。</span><span class="sxs-lookup"><span data-stu-id="a4bce-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a4bce-105">**DataView**コンス トラクターは空、またはいずれかがかかることができます、 **DataTable**引数を 1 つとして、または**DataTable**フィルター条件、並べ替え基準、および行と共に状態フィルター。</span><span class="sxs-lookup"><span data-stu-id="a4bce-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="a4bce-106">使用する追加の引数の詳細については、 **DataView**を参照してください[並べ替え/フィルター データ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)です。</span><span class="sxs-lookup"><span data-stu-id="a4bce-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="a4bce-107">のインデックス、 **DataView**ときにも組み込まれて、 **DataView**が作成されるときのいずれかと、**並べ替え**、 **RowFilter**、または**RowStateFilter**プロパティが変更されると、最適なパフォーマンスを実現するには、最初の並べ替え順序を指定するかを作成するときに、コンス トラクターの引数としてフィルター条件を**DataView**です。</span><span class="sxs-lookup"><span data-stu-id="a4bce-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="a4bce-108">作成する、 **DataView**並べ替えまたはフィルターの条件を指定しを設定せず、**並べ替え**、 **RowFilter**、または**RowStateFilter**プロパティが、その後、インデックスの構築には、少なくとも 2 回: したらときに、 **DataView**作成されると、再度並べ替えまたはフィルターのプロパティのいずれかが変更されました。</span><span class="sxs-lookup"><span data-stu-id="a4bce-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="a4bce-109">作成する場合、 **DataView**を任意の引数を受け取らないコンス トラクターを使用していないことができますを使用する、 **DataView**を設定するまで、**テーブル**プロパティ.</span><span class="sxs-lookup"><span data-stu-id="a4bce-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="a4bce-110">次のコード例を作成する方法を示しています、 **DataView**を使用して、 **DataView**コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="a4bce-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="a4bce-111">A **RowFilter**、**並べ替え**列、および**DataViewRowState**と共に提供される、 **DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="a4bce-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
```vb  
Dim custDV As DataView = New DataView(custDS.Tables("Customers"), _  
    "Country = 'USA'", _  
    "ContactName", _  
    DataViewRowState.CurrentRows)  
```  
  
```csharp  
DataView custDV = new DataView(custDS.Tables["Customers"],   
    "Country = 'USA'",   
    "ContactName",   
    DataViewRowState.CurrentRows);  
```  
  
 <span data-ttu-id="a4bce-112">次のコード例は、既定値への参照を取得する方法を示します**DataView**の**DataTable**を使用して、 **DefaultView**テーブルのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a4bce-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4bce-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4bce-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="a4bce-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="a4bce-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="a4bce-115">データの並べ替えとフィルター処理</span><span class="sxs-lookup"><span data-stu-id="a4bce-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="a4bce-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="a4bce-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="a4bce-117">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="a4bce-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
