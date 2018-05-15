---
title: 主キーの定義
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2ea85959-e763-4669-8bd9-46a9dab894bd
ms.openlocfilehash: 21d63aa33e20019f8392b81fb69881296a52cb26
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="defining-primary-keys"></a><span data-ttu-id="bd467-102">主キーの定義</span><span class="sxs-lookup"><span data-stu-id="bd467-102">Defining Primary Keys</span></span>
<span data-ttu-id="bd467-103">通常、データベース テーブルには、テーブル内の各行を一意に識別する単一の列または複数の列があります。</span><span class="sxs-lookup"><span data-stu-id="bd467-103">A database table commonly has a column or group of columns that uniquely identifies each row in the table.</span></span> <span data-ttu-id="bd467-104">行を識別するこのような列を、主キーと呼びます。</span><span class="sxs-lookup"><span data-stu-id="bd467-104">This identifying column or group of columns is called the primary key.</span></span>  
  
 <span data-ttu-id="bd467-105">1 つを指定すると<xref:System.Data.DataColumn>として、<xref:System.Data.DataTable.PrimaryKey%2A>の<xref:System.Data.DataTable>、テーブルが自動的に設定、<xref:System.Data.DataColumn.AllowDBNull%2A>する列のプロパティ**false**と<xref:System.Data.DataColumn.Unique%2A>プロパティを**true**です。</span><span class="sxs-lookup"><span data-stu-id="bd467-105">When you identify a single <xref:System.Data.DataColumn> as the <xref:System.Data.DataTable.PrimaryKey%2A> for a <xref:System.Data.DataTable>, the table automatically sets the <xref:System.Data.DataColumn.AllowDBNull%2A> property of the column to **false** and the <xref:System.Data.DataColumn.Unique%2A> property to **true**.</span></span> <span data-ttu-id="bd467-106">複数列プライマリ キーの場合のみ、 **AllowDBNull**プロパティに設定されて自動的に**false**です。</span><span class="sxs-lookup"><span data-stu-id="bd467-106">For multiple-column primary keys, only the **AllowDBNull** property is automatically set to **false**.</span></span>  
  
 <span data-ttu-id="bd467-107">**PrimaryKey**のプロパティ、 <xref:System.Data.DataTable> 1 つ以上の配列をその値として受け取る**DataColumn**オブジェクトを次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="bd467-107">The **PrimaryKey** property of a <xref:System.Data.DataTable> receives as its value an array of one or more **DataColumn** objects, as shown in the following examples.</span></span> <span data-ttu-id="bd467-108">最初の例は、1 つの列を主キーとして定義しています。</span><span class="sxs-lookup"><span data-stu-id="bd467-108">The first example defines a single column as the primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustID")}  
  
' Or  
  
Dim columns(1) As DataColumn  
columns(0) = workTable.Columns("CustID")  
workTable.PrimaryKey = columns  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustID"]};  
  
// Or  
  
DataColumn[] columns = new DataColumn[1];  
columns[0] = workTable.Columns["CustID"];  
workTable.PrimaryKey = columns;  
```  
  
 <span data-ttu-id="bd467-109">2 つの列を主キーとして定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bd467-109">The following example defines two columns as a primary key.</span></span>  
  
```vb  
workTable.PrimaryKey = New DataColumn() {workTable.Columns("CustLName"), _  
                                         workTable.Columns("CustFName")}  
  
' Or  
  
Dim keyColumn(2) As DataColumn  
keyColumn(0) = workTable.Columns("CustLName")  
keyColumn(1) = workTable.Columns("CustFName")  
workTable.PrimaryKey = keyColumn  
```  
  
```csharp  
workTable.PrimaryKey = new DataColumn[] {workTable.Columns["CustLName"],   
                                         workTable.Columns["CustFName"]};  
  
// Or  
  
DataColumn[] keyColumn = new DataColumn[2];  
keyColumn[0] = workTable.Columns["CustLName"];  
keyColumn[1] = workTable.Columns["CustFName"];  
workTable.PrimaryKey = keyColumn;  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd467-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd467-110">See Also</span></span>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="bd467-111">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="bd467-111">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="bd467-112">DataTables</span><span class="sxs-lookup"><span data-stu-id="bd467-112">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="bd467-113">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="bd467-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
