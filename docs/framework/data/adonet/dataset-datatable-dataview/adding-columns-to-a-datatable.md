---
title: "DataTable への列の追加"
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6340baa434467ec4ccde501b4bb11d55a72c069b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="adding-columns-to-a-datatable"></a><span data-ttu-id="2f3d0-102">DataTable への列の追加</span><span class="sxs-lookup"><span data-stu-id="2f3d0-102">Adding Columns to a DataTable</span></span>
<span data-ttu-id="2f3d0-103">A<xref:System.Data.DataTable>のコレクションを格納<xref:System.Data.DataColumn>によって参照されるオブジェクト、**列**テーブルのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-103">A <xref:System.Data.DataTable> contains a collection of <xref:System.Data.DataColumn> objects referenced by the **Columns** property of the table.</span></span> <span data-ttu-id="2f3d0-104">この列のコレクションと制約によって、テーブルのスキーマ (構造) が定義されます。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-104">This collection of columns, along with any constraints, defines the schema, or structure, of the table.</span></span>  
  
 <span data-ttu-id="2f3d0-105">作成する**DataColumn**を使用してテーブル内のオブジェクト、 **DataColumn**コンス トラクター、または呼び出すことによって、**追加**のメソッド、**列**これは、テーブルのプロパティ、<xref:System.Data.DataColumnCollection>です。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-105">You create **DataColumn** objects within a table by using the **DataColumn** constructor, or by calling the **Add** method of the **Columns** property of the table, which is a <xref:System.Data.DataColumnCollection>.</span></span> <span data-ttu-id="2f3d0-106">**追加**メソッドは省略可能なを受け取ります**ColumnName**、 **DataType**、および**式**引数新たに作成および**DataColumn**コレクションのメンバーとして。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-106">The **Add** method accepts optional **ColumnName**, **DataType**, and **Expression** arguments and creates a new **DataColumn** as a member of the collection.</span></span> <span data-ttu-id="2f3d0-107">指定することも、既存**DataColumn**オブジェクトし、コレクションに追加しを追加の参照を返します**DataColumn**要求されている場合。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-107">It also accepts an existing **DataColumn** object and adds it to the collection, and returns a reference to the added **DataColumn** if requested.</span></span> <span data-ttu-id="2f3d0-108">**DataTable**オブジェクトがすべてのデータ ソースに固有ではないのデータ型を指定するときに .NET Framework の型が使用される、 **DataColumn**です。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-108">Because **DataTable** objects are not specific to any data source, .NET Framework types are used when specifying the data type of a **DataColumn**.</span></span>  
  
 <span data-ttu-id="2f3d0-109">次の例では、次の 4 つの列を**DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-109">The following example adds four columns to a **DataTable**.</span></span>  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 <span data-ttu-id="2f3d0-110">例では、ことに注意してプロパティを**CustID**列は許可しないように設定**DBNull**値とを一意になる値を制限します。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-110">In the example, notice that the properties for the **CustID** column are set to not allow **DBNull** values and to constrain values to be unique.</span></span> <span data-ttu-id="2f3d0-111">ただし、定義した場合、 **CustID**列、テーブルの主キー列として、 **AllowDBNull**プロパティに自動的に設定する**false**と、 **Unique**プロパティに自動的に設定する**true**です。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-111">However, if you define the **CustID** column as the primary key column of the table, the **AllowDBNull** property will automatically be set to **false** and the **Unique** property will automatically be set to **true**.</span></span> <span data-ttu-id="2f3d0-112">詳細については、次を参照してください。[主キーを定義する](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)です。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-112">For more information, see [Defining Primary Keys](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2f3d0-113">列が列の増分の既定の名前を指定された列の列名が指定されない場合*N、* "Column1"から始めて、これが追加されたときに、 **DataColumnCollection**です。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-113">If a column name is not supplied for a column, the column is given an incremental default name of Column*N,* starting with "Column1", when it is added to the **DataColumnCollection**.</span></span> <span data-ttu-id="2f3d0-114">名前付け規則を回避することをお勧め"列*N*"の既存の既定の列名と競合があります、名前を指定するために、列名を指定するときに、 **DataColumnCollection**です。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-114">We recommend that you avoid the naming convention of "Column*N*" when you supply a column name, because the name you supply may conflict with an existing default column name in the **DataColumnCollection**.</span></span> <span data-ttu-id="2f3d0-115">指定した名前が既に存在する場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-115">If the supplied name already exists, an exception is thrown.</span></span>  
  
 <span data-ttu-id="2f3d0-116"><xref:System.Xml.Linq.XElement> を、<xref:System.Data.DataColumn.DataType%2A> 内の <xref:System.Data.DataColumn> の <xref:System.Data.DataTable> として使用すると、データを読み取るときに XML シリアル化が機能しません。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-116">If you are using <xref:System.Xml.Linq.XElement> as the <xref:System.Data.DataColumn.DataType%2A> of a <xref:System.Data.DataColumn> in the <xref:System.Data.DataTable>, XML serialization will not work when you read in data.</span></span> <span data-ttu-id="2f3d0-117">たとえば、<xref:System.Xml.XmlDocument> メソッドを使用して `DataTable.WriteXml` を書き込むと、XML へのシリアル化で <xref:System.Xml.Linq.XElement> に親ノードが追加されます。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-117">For example, if you write out a <xref:System.Xml.XmlDocument> by using the `DataTable.WriteXml` method, upon serialization to XML there is an additional parent node in the <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="2f3d0-118">この問題に対処するには、<xref:System.Data.SqlTypes.SqlXml> の代わりに <xref:System.Xml.Linq.XElement> 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-118">To work around this problem, use the <xref:System.Data.SqlTypes.SqlXml> type instead of <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="2f3d0-119">`ReadXml` および `WriteXml` は、<xref:System.Data.SqlTypes.SqlXml> で適切に機能します。</span><span class="sxs-lookup"><span data-stu-id="2f3d0-119">`ReadXml` and `WriteXml` work correctly with <xref:System.Data.SqlTypes.SqlXml>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f3d0-120">参照</span><span class="sxs-lookup"><span data-stu-id="2f3d0-120">See Also</span></span>  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [<span data-ttu-id="2f3d0-121">DataTable スキーマの定義</span><span class="sxs-lookup"><span data-stu-id="2f3d0-121">DataTable Schema Definition</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [<span data-ttu-id="2f3d0-122">DataTables</span><span class="sxs-lookup"><span data-stu-id="2f3d0-122">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="2f3d0-123">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="2f3d0-123">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
