---
title: DataRow の削除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 128c41e1906b17e7f42458e8a5f1b3d3ec9cc449
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757516"
---
# <a name="datarow-deletion"></a><span data-ttu-id="efbe5-102">DataRow の削除</span><span class="sxs-lookup"><span data-stu-id="efbe5-102">DataRow Deletion</span></span>
<span data-ttu-id="efbe5-103">削除に使用できる 2 つの方法がある、<xref:System.Data.DataRow>オブジェクトから、<xref:System.Data.DataTable>オブジェクト:**削除**のメソッド、<xref:System.Data.DataRowCollection>オブジェクト、および<xref:System.Data.DataRow.Delete%2A>のメソッド、 **DataRow**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="efbe5-103">There are two methods you can use to delete a <xref:System.Data.DataRow> object from a <xref:System.Data.DataTable> object: the **Remove** method of the <xref:System.Data.DataRowCollection> object, and the <xref:System.Data.DataRow.Delete%2A> method of the **DataRow** object.</span></span> <span data-ttu-id="efbe5-104">一方、<xref:System.Data.DataRowCollection.Remove%2A>メソッドの削除、 **DataRow**から、 **DataRowCollection**、<xref:System.Data.DataRow.Delete%2A>メソッドは削除対象の行をマークするだけです。</span><span class="sxs-lookup"><span data-stu-id="efbe5-104">Whereas the <xref:System.Data.DataRowCollection.Remove%2A> method deletes a **DataRow** from the **DataRowCollection**, the <xref:System.Data.DataRow.Delete%2A> method only marks the row for deletion.</span></span> <span data-ttu-id="efbe5-105">アプリケーションを呼び出すときに実際の削除が発生した、 **AcceptChanges**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="efbe5-105">The actual removal occurs when the application calls the **AcceptChanges** method.</span></span> <span data-ttu-id="efbe5-106"><xref:System.Data.DataRow.Delete%2A> を使用すると、行を実際に削除する前に、削除対象としてどの行がマークされているかをプログラムによってチェックできます。</span><span class="sxs-lookup"><span data-stu-id="efbe5-106">By using <xref:System.Data.DataRow.Delete%2A>, you can programmatically check which rows are marked for deletion before actually removing them.</span></span> <span data-ttu-id="efbe5-107">削除対象としてマークされている行の <xref:System.Data.DataRow.RowState%2A> プロパティは、<xref:System.Data.DataRow.Delete%2A> に設定されています。</span><span class="sxs-lookup"><span data-stu-id="efbe5-107">When a row is marked for deletion, its <xref:System.Data.DataRow.RowState%2A> property is set to <xref:System.Data.DataRow.Delete%2A>.</span></span>  
  
 <span data-ttu-id="efbe5-108"><xref:System.Data.DataRow.Delete%2A> オブジェクトを反復処理している間は、foreach ループで <xref:System.Data.DataRowCollection.Remove%2A> も <xref:System.Data.DataRowCollection> も呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="efbe5-108">Neither <xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> should be called in a foreach loop while iterating through a <xref:System.Data.DataRowCollection> object.</span></span> <span data-ttu-id="efbe5-109"><xref:System.Data.DataRow.Delete%2A> または <xref:System.Data.DataRowCollection.Remove%2A> はコレクションの状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="efbe5-109"><xref:System.Data.DataRow.Delete%2A> nor <xref:System.Data.DataRowCollection.Remove%2A> modify the state of the collection.</span></span>  
  
 <span data-ttu-id="efbe5-110">使用する場合、<xref:System.Data.DataSet>または**DataTable**と組み合わせて、 **DataAdapter**とを使用して、リレーショナル データ ソース、**削除**のメソッド、 **DataRow**行を削除します。</span><span class="sxs-lookup"><span data-stu-id="efbe5-110">When using a <xref:System.Data.DataSet> or **DataTable** in conjunction with a **DataAdapter** and a relational data source, use the **Delete** method of the **DataRow** to remove the row.</span></span> <span data-ttu-id="efbe5-111">**削除**メソッドとして行をマーク**Deleted**で、**データセット**または**DataTable**は削除されません。</span><span class="sxs-lookup"><span data-stu-id="efbe5-111">The **Delete** method marks the row as **Deleted** in the **DataSet** or **DataTable** but does not remove it.</span></span> <span data-ttu-id="efbe5-112">代わりに、 **DataAdapter**としてマークされている行を検出する**Deleted**を実行してその**DeleteCommand**データ ソースの行を削除するメソッドをします。</span><span class="sxs-lookup"><span data-stu-id="efbe5-112">Instead, when the **DataAdapter** encounters a row marked as **Deleted**, it executes its **DeleteCommand** method to delete the row at the data source.</span></span> <span data-ttu-id="efbe5-113">行、完全に削除できますを使用して、 **AcceptChanges**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="efbe5-113">The row can then be permanently removed using the **AcceptChanges** method.</span></span> <span data-ttu-id="efbe5-114">使用する場合**削除**行を削除する、行は、テーブルから完全に削除されるが、 **DataAdapter**データ ソースの行は削除されません。</span><span class="sxs-lookup"><span data-stu-id="efbe5-114">If you use **Remove** to delete the row, the row is removed entirely from the table, but the **DataAdapter** will not delete the row at the data source.</span></span>  
  
 <span data-ttu-id="efbe5-115">**削除**のメソッド、 **DataRowCollection**は、 **DataRow**を引数として、次の例に示すように、コレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="efbe5-115">The **Remove** method of the **DataRowCollection** takes a **DataRow** as an argument and removes it from the collection, as shown in the following example.</span></span>  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 <span data-ttu-id="efbe5-116">これに対し、次の例を呼び出す方法、**削除**メソッドを**DataRow**を変更するその**RowState**に**Deleted**.</span><span class="sxs-lookup"><span data-stu-id="efbe5-116">In contrast, the following example demonstrates how to call the **Delete** method on a **DataRow** to change its **RowState** to **Deleted**.</span></span>  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 <span data-ttu-id="efbe5-117">行が削除対象としてマークしを呼び出す場合、 **AcceptChanges**のメソッド、 **DataTable**から、行が削除されるオブジェクト、 **DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="efbe5-117">If a row is marked for deletion and you call the **AcceptChanges** method of the **DataTable** object, the row is removed from the **DataTable**.</span></span> <span data-ttu-id="efbe5-118">呼び出す場合とは異なり、 **RejectChanges**、 **RowState**としてマークされる前に元に戻します、行の**Deleted**です。</span><span class="sxs-lookup"><span data-stu-id="efbe5-118">In contrast, if you call **RejectChanges**, the **RowState** of the row reverts to what it was before being marked as **Deleted**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efbe5-119">場合、 **RowState**の**DataRow**は**Added**、つまり直前が追加されたテーブル、およびとしてマークされます**Deleted**はテーブルから削除します。</span><span class="sxs-lookup"><span data-stu-id="efbe5-119">If the **RowState** of a **DataRow** is **Added**, meaning it has just been added to the table, and it is then marked as **Deleted**, it is removed from the table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efbe5-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="efbe5-120">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataRowCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="efbe5-121">DataTable 内のデータの操作</span><span class="sxs-lookup"><span data-stu-id="efbe5-121">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="efbe5-122">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="efbe5-122">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
