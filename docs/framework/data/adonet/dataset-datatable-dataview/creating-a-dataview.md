---
title: "DataView の作成"
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
ms.assetid: b1cc02d1-23b1-4439-a998-0da1899f3442
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 53cbfc5097c28c0677a164f817cfe14927814d75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-dataview"></a><span data-ttu-id="3725b-102">DataView の作成</span><span class="sxs-lookup"><span data-stu-id="3725b-102">Creating a DataView</span></span>
<span data-ttu-id="3725b-103"><xref:System.Data.DataView> は 2 とおりの方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="3725b-103">There are two ways to create a <xref:System.Data.DataView>.</span></span> <span data-ttu-id="3725b-104">使用することができます、 **DataView**コンス トラクターを作成できますへの参照、<xref:System.Data.DataTable.DefaultView%2A>のプロパティ、<xref:System.Data.DataTable>です。</span><span class="sxs-lookup"><span data-stu-id="3725b-104">You can use the **DataView** constructor, or you can create a reference to the <xref:System.Data.DataTable.DefaultView%2A> property of the <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="3725b-105">**DataView**コンス トラクターは空、またはいずれかがかかることができます、 **DataTable**引数を 1 つとして、または**DataTable**フィルター条件、並べ替え基準、および行と共に状態フィルター。</span><span class="sxs-lookup"><span data-stu-id="3725b-105">The **DataView** constructor can be empty, or it can take either a **DataTable** as a single argument, or a **DataTable** along with filter criteria, sort criteria, and a row state filter.</span></span> <span data-ttu-id="3725b-106">使用する追加の引数の詳細については、 **DataView**を参照してください[並べ替え/フィルター データ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)です。</span><span class="sxs-lookup"><span data-stu-id="3725b-106">For more information about the additional arguments available for use with the **DataView**, see [Sorting and Filtering Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
 <span data-ttu-id="3725b-107">のインデックス、 **DataView**ときにも組み込まれて、 **DataView**が作成されるときのいずれかと、**並べ替え**、 **RowFilter**、または**RowStateFilter**プロパティが変更されると、最適なパフォーマンスを実現するには、最初の並べ替え順序を指定するかを作成するときに、コンス トラクターの引数としてフィルター条件を**DataView**です。</span><span class="sxs-lookup"><span data-stu-id="3725b-107">Because the index for a **DataView** is built both when the **DataView** is created, and when any of the **Sort**, **RowFilter**, or **RowStateFilter** properties are modified, you achieve best performance by supplying any initial sort order or filtering criteria as constructor arguments when you create the **DataView**.</span></span> <span data-ttu-id="3725b-108">作成する、 **DataView**並べ替えまたはフィルターの条件を指定しを設定せず、**並べ替え**、 **RowFilter**、または**RowStateFilter**プロパティが、その後、インデックスの構築には、少なくとも 2 回: したらときに、 **DataView**作成されると、再度並べ替えまたはフィルターのプロパティのいずれかが変更されました。</span><span class="sxs-lookup"><span data-stu-id="3725b-108">Creating a **DataView** without specifying sort or filter criteria and then setting the **Sort**, **RowFilter**, or **RowStateFilter** properties later causes the index to be built at least twice: once when the **DataView** is created, and again when any of the sort or filter properties are modified.</span></span>  
  
 <span data-ttu-id="3725b-109">作成する場合、 **DataView**を任意の引数を受け取らないコンス トラクターを使用していないことができますを使用する、 **DataView**を設定するまで、**テーブル**プロパティ.</span><span class="sxs-lookup"><span data-stu-id="3725b-109">Note that if you create a **DataView** using the constructor that does not take any arguments, you will not be able to use the **DataView** until you have set the **Table** property.</span></span>  
  
 <span data-ttu-id="3725b-110">次のコード例を作成する方法を示しています、 **DataView**を使用して、 **DataView**コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="3725b-110">The following code example demonstrates how to create a **DataView** using the **DataView** constructor.</span></span> <span data-ttu-id="3725b-111">A **RowFilter**、**並べ替え**列、および**DataViewRowState**と共に提供される、 **DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="3725b-111">A **RowFilter**, **Sort** column, and **DataViewRowState** are supplied along with the **DataTable**.</span></span>  
  
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
  
 <span data-ttu-id="3725b-112">次のコード例は、既定値への参照を取得する方法を示します**DataView**の**DataTable**を使用して、 **DefaultView**テーブルのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="3725b-112">The following code example demonstrates how to obtain a reference to the default **DataView** of a **DataTable** using the **DefaultView** property of the table.</span></span>  
  
```vb  
Dim custDV As DataView = custDS.Tables("Customers").DefaultView  
```  
  
```csharp  
DataView custDV = custDS.Tables["Customers"].DefaultView;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3725b-113">参照</span><span class="sxs-lookup"><span data-stu-id="3725b-113">See Also</span></span>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataView>  
 [<span data-ttu-id="3725b-114">DataViews</span><span class="sxs-lookup"><span data-stu-id="3725b-114">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 [<span data-ttu-id="3725b-115">データの並べ替えとフィルター処理</span><span class="sxs-lookup"><span data-stu-id="3725b-115">Sorting and Filtering Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/sorting-and-filtering-data.md)  
 [<span data-ttu-id="3725b-116">DataTables</span><span class="sxs-lookup"><span data-stu-id="3725b-116">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="3725b-117">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="3725b-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
