---
title: "DataTable 内のデータの表示"
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
ms.assetid: 1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 147d6fb4509913de1f0331ce2ff6c580c6e41ef3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="viewing-data-in-a-datatable"></a><span data-ttu-id="88dcc-102">DataTable 内のデータの表示</span><span class="sxs-lookup"><span data-stu-id="88dcc-102">Viewing Data in a DataTable</span></span>
<span data-ttu-id="88dcc-103">内容にアクセスすることができます、<xref:System.Data.DataTable>を使用して、**行**と**列**のコレクション、 **DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="88dcc-103">You can access the contents of a <xref:System.Data.DataTable> by using the **Rows** and **Columns** collections of the **DataTable**.</span></span> <span data-ttu-id="88dcc-104">使用することも、<xref:System.Data.DataTable.Select%2A>内のデータのサブセットを返すメソッド、 **DataTable**のような検索条件の基準に従って並べ替え順序、および行の状態。</span><span class="sxs-lookup"><span data-stu-id="88dcc-104">You can also use the <xref:System.Data.DataTable.Select%2A> method to return subsets of the data in a **DataTable** according to criteria including search criteria, sort order, and row state.</span></span> <span data-ttu-id="88dcc-105">また、使用することができます、<xref:System.Data.DataRowCollection.Find%2A>のメソッド、 **DataRowCollection**主キーの値を使用して特定の行を検索するとき。</span><span class="sxs-lookup"><span data-stu-id="88dcc-105">Additionally, you can use the <xref:System.Data.DataRowCollection.Find%2A> method of the **DataRowCollection** when searching for a particular row using a primary key value.</span></span>  
  
 <span data-ttu-id="88dcc-106">**選択**のメソッド、 **DataTable**オブジェクトのセットを返します<xref:System.Data.DataRow>指定した条件に一致するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="88dcc-106">The **Select** method of the **DataTable** object returns a set of <xref:System.Data.DataRow> objects that match the specified criteria.</span></span> <span data-ttu-id="88dcc-107">**選択**は、フィルター式、並べ替え式の省略可能な引数を受け取り、 **DataViewRowState**です。</span><span class="sxs-lookup"><span data-stu-id="88dcc-107">**Select** takes optional arguments of a filter expression, sort expression, and **DataViewRowState**.</span></span> <span data-ttu-id="88dcc-108">フィルター式に基づいて返される行を識別する**DataColumn**などの値`LastName = 'Smith'`です。</span><span class="sxs-lookup"><span data-stu-id="88dcc-108">The filter expression identifies which rows to return based on **DataColumn** values, such as `LastName = 'Smith'`.</span></span> <span data-ttu-id="88dcc-109">並べ替え式は、列の並べ替えについての標準 SQL 規則に基づく `LastName ASC, FirstName ASC` などの式です。</span><span class="sxs-lookup"><span data-stu-id="88dcc-109">The sort expression follows standard SQL conventions for ordering columns, for example `LastName ASC, FirstName ASC`.</span></span> <span data-ttu-id="88dcc-110">式の作成に関する規則は、次を参照してください。、<xref:System.Data.DataColumn.Expression%2A>のプロパティ、 **DataColumn**クラスです。</span><span class="sxs-lookup"><span data-stu-id="88dcc-110">For rules about writing expressions, see the <xref:System.Data.DataColumn.Expression%2A> property of the **DataColumn** class.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="88dcc-111">呼び出しの数を実行している場合、**選択**のメソッド、 **DataTable**、最初に作成することでパフォーマンスを向上させることができますできます、<xref:System.Data.DataView>の**DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="88dcc-111">If you are performing a number of calls to the **Select** method of a **DataTable**, you can increase performance by first creating a <xref:System.Data.DataView> for the **DataTable**.</span></span> <span data-ttu-id="88dcc-112">作成する、 **DataView**テーブルの行のインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="88dcc-112">Creating the **DataView** indexes the rows of the table.</span></span> <span data-ttu-id="88dcc-113">**選択**メソッド、インデックス、除去クエリ結果を生成する時間を大幅に削減します。</span><span class="sxs-lookup"><span data-stu-id="88dcc-113">The **Select** method then usees that index, significantly reducing the time to generate the query result.</span></span> <span data-ttu-id="88dcc-114">作成する方法について、 **DataView**の**DataTable**を参照してください[Dataview](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)です。</span><span class="sxs-lookup"><span data-stu-id="88dcc-114">For information about creating a **DataView** for a **DataTable**, see [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).</span></span>  
  
 <span data-ttu-id="88dcc-115">**選択**メソッドに基づいて、表示または操作する行のバージョンを決定する<xref:System.Data.DataViewRowState>です。</span><span class="sxs-lookup"><span data-stu-id="88dcc-115">The **Select** method determines which version of the rows to view or manipulate based on a <xref:System.Data.DataViewRowState>.</span></span> <span data-ttu-id="88dcc-116">次の表に、考えられる**DataViewRowState**列挙値。</span><span class="sxs-lookup"><span data-stu-id="88dcc-116">The following table describes the possible **DataViewRowState** enumeration values.</span></span>  
  
|<span data-ttu-id="88dcc-117">DataViewRowState の値</span><span class="sxs-lookup"><span data-stu-id="88dcc-117">DataViewRowState value</span></span>|<span data-ttu-id="88dcc-118">説明</span><span class="sxs-lookup"><span data-stu-id="88dcc-118">Description</span></span>|  
|----------------------------|-----------------|  
|<span data-ttu-id="88dcc-119">**CurrentRows**</span><span class="sxs-lookup"><span data-stu-id="88dcc-119">**CurrentRows**</span></span>|<span data-ttu-id="88dcc-120">変更されていない行、追加された行、および変更された行を含む現在の行。</span><span class="sxs-lookup"><span data-stu-id="88dcc-120">Current rows including unchanged, added, and modified rows.</span></span>|  
|<span data-ttu-id="88dcc-121">**削除**</span><span class="sxs-lookup"><span data-stu-id="88dcc-121">**Deleted**</span></span>|<span data-ttu-id="88dcc-122">削除された行。</span><span class="sxs-lookup"><span data-stu-id="88dcc-122">A deleted row.</span></span>|  
|<span data-ttu-id="88dcc-123">**ModifiedCurrent**</span><span class="sxs-lookup"><span data-stu-id="88dcc-123">**ModifiedCurrent**</span></span>|<span data-ttu-id="88dcc-124">元のデータを変更した後のバージョンである、現在のバージョン。</span><span class="sxs-lookup"><span data-stu-id="88dcc-124">A current version, which is a modified version of original data.</span></span> <span data-ttu-id="88dcc-125">(を参照してください**ModifiedOriginal**)。</span><span class="sxs-lookup"><span data-stu-id="88dcc-125">(See **ModifiedOriginal**.)</span></span>|  
|<span data-ttu-id="88dcc-126">**ModifiedOriginal**</span><span class="sxs-lookup"><span data-stu-id="88dcc-126">**ModifiedOriginal**</span></span>|<span data-ttu-id="88dcc-127">変更されたすべての行の元のバージョン。</span><span class="sxs-lookup"><span data-stu-id="88dcc-127">The original version of all modified rows.</span></span> <span data-ttu-id="88dcc-128">現在のバージョンが利用可能なを使用して**ModifiedCurrent**です。</span><span class="sxs-lookup"><span data-stu-id="88dcc-128">The current version is available using **ModifiedCurrent**.</span></span>|  
|<span data-ttu-id="88dcc-129">**追加**</span><span class="sxs-lookup"><span data-stu-id="88dcc-129">**Added**</span></span>|<span data-ttu-id="88dcc-130">新しい行。</span><span class="sxs-lookup"><span data-stu-id="88dcc-130">A new row.</span></span>|  
|<span data-ttu-id="88dcc-131">**None**</span><span class="sxs-lookup"><span data-stu-id="88dcc-131">**None**</span></span>|<span data-ttu-id="88dcc-132">なし。</span><span class="sxs-lookup"><span data-stu-id="88dcc-132">None.</span></span>|  
|<span data-ttu-id="88dcc-133">**OriginalRows**</span><span class="sxs-lookup"><span data-stu-id="88dcc-133">**OriginalRows**</span></span>|<span data-ttu-id="88dcc-134">変更されていない行および削除された行を含む元の行。</span><span class="sxs-lookup"><span data-stu-id="88dcc-134">Original rows, including unchanged and deleted rows.</span></span>|  
|<span data-ttu-id="88dcc-135">**変更されません。**</span><span class="sxs-lookup"><span data-stu-id="88dcc-135">**Unchanged**</span></span>|<span data-ttu-id="88dcc-136">変更されていない行。</span><span class="sxs-lookup"><span data-stu-id="88dcc-136">An unchanged row.</span></span>|  
  
 <span data-ttu-id="88dcc-137">次の例で、**データセット**オブジェクトはフィルター処理のみを使用する行が**DataViewRowState**に設定されている**CurrentRows**です。</span><span class="sxs-lookup"><span data-stu-id="88dcc-137">In the following example, the **DataSet** object is filtered so that you are only working with rows whose **DataViewRowState** is set to **CurrentRows**.</span></span>  
  
```vb  
Dim column As DataColumn  
Dim row As DataRow  
  
Dim currentRows() As DataRow = _  
    workTable.Select(Nothing, Nothing, DataViewRowState.CurrentRows)  
  
If (currentRows.Length < 1 ) Then  
  Console.WriteLine("No Current Rows Found")  
Else  
  For Each column in workTable.Columns  
    Console.Write(vbTab & column.ColumnName)  
  Next  
  
  Console.WriteLine(vbTab & "RowState")  
  
  For Each row In currentRows  
    For Each column In workTable.Columns  
      Console.Write(vbTab & row(column).ToString())  
    Next  
  
    Dim rowState As String = _  
        System.Enum.GetName(row.RowState.GetType(), row.RowState)  
    Console.WriteLine(vbTab & rowState)  
  Next  
End If  
```  
  
```csharp  
DataRow[] currentRows = workTable.Select(  
    null, null, DataViewRowState.CurrentRows);  
  
if (currentRows.Length < 1 )  
  Console.WriteLine("No Current Rows Found");  
else  
{  
  foreach (DataColumn column in workTable.Columns)  
    Console.Write("\t{0}", column.ColumnName);  
  
  Console.WriteLine("\tRowState");  
  
  foreach (DataRow row in currentRows)  
  {  
    foreach (DataColumn column in workTable.Columns)  
      Console.Write("\t{0}", row[column]);  
  
    Console.WriteLine("\t" + row.RowState);  
  }  
}  
```  
  
 <span data-ttu-id="88dcc-138">**選択**が異なると行を返すメソッドを使用できます**RowState**値またはフィールド値。</span><span class="sxs-lookup"><span data-stu-id="88dcc-138">The **Select** method can be used to return rows with differing **RowState** values or field values.</span></span> <span data-ttu-id="88dcc-139">次の例を返します、 **DataRow**が削除されているし、他を返すすべての行を参照する配列**DataRow**順に、すべての行を参照している配列**CustLName**、場所、 **CustID**列が 5 より大きい。</span><span class="sxs-lookup"><span data-stu-id="88dcc-139">The following example returns a **DataRow** array that references all rows that have been deleted, and returns another **DataRow** array that references all rows, ordered by **CustLName**, where the **CustID** column is greater than 5.</span></span> <span data-ttu-id="88dcc-140">内の情報を表示する方法については、 **Deleted**行を参照してください[行の状態と行のバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。</span><span class="sxs-lookup"><span data-stu-id="88dcc-140">For information about how to view the information in the **Deleted** row, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
```vb  
' Retrieve all deleted rows.  
Dim deletedRows() As DataRow = workTable.Select(Nothing, Nothing, DataViewRowState.Deleted)  
  
' Retrieve rows where CustID > 5, and order by CustLName.  
Dim custRows() As DataRow = workTable.Select( _  
    "CustID > 5", "CustLName ASC")  
```  
  
```csharp  
// Retrieve all deleted rows.  
DataRow[] deletedRows = workTable.Select(  
    null, null, DataViewRowState.Deleted);  
  
// Retrieve rows where CustID > 5, and order by CustLName.  
DataRow[] custRows = workTable.Select("CustID > 5", "CustLName ASC");  
```  
  
## <a name="see-also"></a><span data-ttu-id="88dcc-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="88dcc-141">See Also</span></span>  
 <xref:System.Data.DataRow>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataViewRowState>  
 [<span data-ttu-id="88dcc-142">DataTable 内のデータを操作します。</span><span class="sxs-lookup"><span data-stu-id="88dcc-142">Manipulating Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)  
 [<span data-ttu-id="88dcc-143">行の状態と行のバージョン</span><span class="sxs-lookup"><span data-stu-id="88dcc-143">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 [<span data-ttu-id="88dcc-144">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="88dcc-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
