---
title: "DataSet の内容のコピー"
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
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d8f9eac80d7a6679e7b3717446e79caf54a5fed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="copying-dataset-contents"></a><span data-ttu-id="029c0-102">DataSet の内容のコピー</span><span class="sxs-lookup"><span data-stu-id="029c0-102">Copying DataSet Contents</span></span>
<span data-ttu-id="029c0-103">コピーを作成することができます、 <xref:System.Data.DataSet> 、元のデータに影響を与えずにデータを操作したり、作業できるようにからのデータのサブセットを**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="029c0-103">You can create a copy of a <xref:System.Data.DataSet> so that you can work with data without affecting the original data, or work with a subset of the data from a **DataSet**.</span></span> <span data-ttu-id="029c0-104">コピーするときに、**データセット**、することができます。</span><span class="sxs-lookup"><span data-stu-id="029c0-104">When copying a **DataSet**, you can:</span></span>  
  
-   <span data-ttu-id="029c0-105">正確なコピーを作成、**データセット**(スキーマ、データ、行状態情報、および行のバージョンなど)。</span><span class="sxs-lookup"><span data-stu-id="029c0-105">Create an exact copy of the **DataSet**, including the schema, data, row state information, and row versions.</span></span>  
  
-   <span data-ttu-id="029c0-106">作成、**データセット**、既存のスキーマを格納している**データセット**、変更された行だけです。</span><span class="sxs-lookup"><span data-stu-id="029c0-106">Create a **DataSet** that contains the schema of an existing **DataSet**, but only rows that have been modified.</span></span> <span data-ttu-id="029c0-107">変更されているすべての行を返すか、特定の指定**DataRowState**です。</span><span class="sxs-lookup"><span data-stu-id="029c0-107">You can return all rows that have been modified, or specify a specific **DataRowState**.</span></span> <span data-ttu-id="029c0-108">行の状態の詳細については、次を参照してください。[行の状態と行のバージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。</span><span class="sxs-lookup"><span data-stu-id="029c0-108">For more information about row states, see [Row States and Row Versions](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).</span></span>  
  
-   <span data-ttu-id="029c0-109">スキーマ、またはリレーショナル構造のコピー、**データセット**任意の行をコピーすることがなくのみです。</span><span class="sxs-lookup"><span data-stu-id="029c0-109">Copy the schema, or relational structure, of the **DataSet** only, without copying any rows.</span></span> <span data-ttu-id="029c0-110">行は、<xref:System.Data.DataTable> を使用して、既存の <xref:System.Data.DataTable.ImportRow%2A> にインポートできます。</span><span class="sxs-lookup"><span data-stu-id="029c0-110">Rows can be imported into an existing <xref:System.Data.DataTable> using <xref:System.Data.DataTable.ImportRow%2A>.</span></span>  
  
 <span data-ttu-id="029c0-111">正確なコピーを作成する、**データセット**スキーマとデータの両方が含まれている、使用して、<xref:System.Data.DataSet.Copy%2A>のメソッド、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="029c0-111">To create an exact copy of the **DataSet** that includes both schema and data, use the <xref:System.Data.DataSet.Copy%2A> method of the **DataSet**.</span></span> <span data-ttu-id="029c0-112">次のコード例の正確なコピーを作成する方法を示しています、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="029c0-112">The following code example shows how to create an exact copy of the **DataSet**.</span></span>  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 <span data-ttu-id="029c0-113">コピーを作成する、**データセット**スキーマとのみ、データを表すが含まれる**Added**、 **Modified**、または**Deleted**行を使用して、<xref:System.Data.DataSet.GetChanges%2A>のメソッド、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="029c0-113">To create a copy of a **DataSet** that includes schema and only the data representing **Added**, **Modified**, or **Deleted** rows, use the <xref:System.Data.DataSet.GetChanges%2A> method of the **DataSet**.</span></span> <span data-ttu-id="029c0-114">使用することも**GetChanges**を渡すことによって指定された行の状態を持つ行だけを返す、 **DataRowState**値の呼び出し時に**GetChanges**です。</span><span class="sxs-lookup"><span data-stu-id="029c0-114">You can also use **GetChanges** to return only rows with a specified row state by passing a **DataRowState** value when calling **GetChanges**.</span></span> <span data-ttu-id="029c0-115">次のコード例に渡す方法を示しています、 **DataRowState**を呼び出すときに**GetChanges**です。</span><span class="sxs-lookup"><span data-stu-id="029c0-115">The following code example shows how to pass a **DataRowState** when calling **GetChanges**.</span></span>  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 <span data-ttu-id="029c0-116">コピーを作成する、**データセット**スキーマのみを含む、使用して、<xref:System.Data.DataSet.Clone%2A>のメソッド、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="029c0-116">To create a copy of a **DataSet** that only includes schema, use the <xref:System.Data.DataSet.Clone%2A> method of the **DataSet**.</span></span> <span data-ttu-id="029c0-117">複製されたに既存の行を追加することもできます。**データセット**を使用して、 **ImportRow**のメソッド、 **DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="029c0-117">You can also add existing rows to the cloned **DataSet** using the **ImportRow** method of the **DataTable**.</span></span> <span data-ttu-id="029c0-118">**ImportRow**データ、行の状態、および行のバージョン情報を指定したテーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="029c0-118">**ImportRow** adds data, row state, and row version information to the specified table.</span></span> <span data-ttu-id="029c0-119">列名が一致し、データ型が互換性のある型の場合には、列の値だけが追加されます。</span><span class="sxs-lookup"><span data-stu-id="029c0-119">Column values are added only where the column name matches and the data type is compatible.</span></span>  
  
 <span data-ttu-id="029c0-120">次のコード例は、の複製を作成、**データセット**し、元の行を追加し、**データセット**を**顧客**テーブルに、**データセット**顧客の複製で、 **CountryRegion**列に値"Germany"です。</span><span class="sxs-lookup"><span data-stu-id="029c0-120">The following code example creates a clone of a **DataSet** and then adds the rows from the original **DataSet** to the **Customers** table in the **DataSet** clone for customers where the **CountryRegion** column has the value "Germany".</span></span>  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a><span data-ttu-id="029c0-121">参照</span><span class="sxs-lookup"><span data-stu-id="029c0-121">See Also</span></span>  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="029c0-122">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="029c0-122">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="029c0-123">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="029c0-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
