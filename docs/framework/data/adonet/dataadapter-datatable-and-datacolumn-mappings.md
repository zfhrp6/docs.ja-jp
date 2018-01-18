---
title: "DataAdapter DataTable と DataColumn のマップ"
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
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e104ba75026c2ff387eb7c74b11c505e34085f41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="90e65-102">DataAdapter DataTable と DataColumn のマップ</span><span class="sxs-lookup"><span data-stu-id="90e65-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="90e65-103">A **DataAdapter** 0 個以上のコレクションを含んでいます<xref:System.Data.Common.DataTableMapping>内のオブジェクトの**TableMappings**プロパティです。</span><span class="sxs-lookup"><span data-stu-id="90e65-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="90e65-104">A **DataTableMapping** 、データ ソースに対するクエリから返されるデータの間のマスター マッピングを提供し、<xref:System.Data.DataTable>です。</span><span class="sxs-lookup"><span data-stu-id="90e65-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="90e65-105">**DataTableMapping**の代わりに名前を渡すことができます、 **DataTable**名、**塗りつぶし**のメソッド、 **DataAdapter**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="90e65-106">次の例を作成、 **DataTableMapping**という**AuthorsMapping**の**作成者**テーブル。</span><span class="sxs-lookup"><span data-stu-id="90e65-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="90e65-107">A **DataTableMapping**内の列名を使用することができます、 **DataTable**は異なるデータベースにします。</span><span class="sxs-lookup"><span data-stu-id="90e65-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="90e65-108">**DataAdapter**マッピングを使用して、テーブルが更新されたときに、列を照合します。</span><span class="sxs-lookup"><span data-stu-id="90e65-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="90e65-109">指定しない場合、 **TableName**または**DataTableMapping**名前を呼び出すときに、**塗りつぶし**または**更新**のメソッド、 **DataAdapter**、 **DataAdapter**は検索、 **DataTableMapping** "Table"という名前です。</span><span class="sxs-lookup"><span data-stu-id="90e65-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="90e65-110">場合は、その**DataTableMapping**が存在しない、 **TableName**の**DataTable** 「テーブル」です。</span><span class="sxs-lookup"><span data-stu-id="90e65-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="90e65-111">既定値を指定することができます**DataTableMapping**作成することで、 **DataTableMapping** "Table"の名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="90e65-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="90e65-112">次のコード例を作成、 **DataTableMapping** (から、<xref:System.Data.Common>名前空間) を指定された既定のマッピングを返し**DataAdapter** "Table"名前を付けることによってです。</span><span class="sxs-lookup"><span data-stu-id="90e65-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="90e65-113">例では、クエリ結果内の最初のテーブルから列をマップし、(、**顧客**のテーブル、 **Northwind**データベース) にわかりやすい名前のセットを**Northwind の Customers**テーブルに、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="90e65-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="90e65-114">割り当てられない列には、データ ソースの列名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="90e65-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="90e65-115">高度な状況は、同じするを決めることがあります**DataAdapter**異なるマッピングに別のテーブルの読み込みをサポートするためにします。</span><span class="sxs-lookup"><span data-stu-id="90e65-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="90e65-116">これを行うには、単に追加**DataTableMapping**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="90e65-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="90e65-117">ときに、**塗りつぶし**メソッドのインスタンスに渡されます、**データセット**と**DataTableMapping** 、その名前のマッピングが存在する場合、名前が使用されますそれ以外の場合、、  **。DataTable**名を使用するとします。</span><span class="sxs-lookup"><span data-stu-id="90e65-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="90e65-118">次の例では、作成、 **DataTableMapping**の名前を持つ**顧客**と**DataTable**の名前**BizTalkSchema**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="90e65-119">例では、SELECT ステートメントによって返される行にマップされます、 **BizTalkSchema** **DataTable**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
>  <span data-ttu-id="90e65-120">列マップにソースの列名を指定しなかった場合、またはテーブル マップにソース テーブル名を指定しなかった場合は、自動的に既定の名前が生成されます。</span><span class="sxs-lookup"><span data-stu-id="90e65-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="90e65-121">列マッピングがの増分の既定の名前を指定した場合は、列マッピングの基になる列が指定されていません、 **SourceColumn** *N、*で始まる**SourceColumn1**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="90e65-122">テーブル マップにソース テーブル名を指定しない場合、テーブルのマッピングが指定されたのインクリメンタル既定名**SourceTable** *N*以降で、 **SourceTable1**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90e65-123">名前付け規則を回避することをお勧め**SourceColumn** *N*列マッピングの場合、または**SourceTable** *N*テーブル指定した名前の既存の既定の列マップ名の競合する場合もあるため、マッピング、 **ColumnMappingCollection**またはテーブル マップ名に、 **DataTableMappingCollection**.</span><span class="sxs-lookup"><span data-stu-id="90e65-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="90e65-124">指定した名前が既に存在する場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="90e65-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="90e65-125">複数の結果セットの処理</span><span class="sxs-lookup"><span data-stu-id="90e65-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="90e65-126">場合、 **SelectCommand**複数のテーブルを返します**塗りつぶし**内のテーブルの増分値を持つテーブル名を自動的に生成、**データセット**以降で、形式でテーブル名と続行を指定**TableName** *N*以降で、 **TableName1**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="90e65-127">内のテーブルに対して指定名前に、自動的に生成されたテーブル名をマップするテーブルのマッピングを使用することができます、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="90e65-128">たとえば、 **SelectCommand** 2 つのテーブルを返す**顧客**と**Orders**、次の呼び出しを発行**塗りつぶし**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="90e65-129">2 つのテーブルに作成されます、**データセット**:**顧客**と**Customers1**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="90e65-130">テーブルのマッピングを使用するには 2 番目のテーブルがという名前のことを確認する**Orders**の代わりに**Customers1**です。</span><span class="sxs-lookup"><span data-stu-id="90e65-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="90e65-131">これを行うには、マップのソース テーブル**Customers1**を**データセット**テーブル**注文**の次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="90e65-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="90e65-132">参照</span><span class="sxs-lookup"><span data-stu-id="90e65-132">See Also</span></span>  
 [<span data-ttu-id="90e65-133">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="90e65-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="90e65-134">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="90e65-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="90e65-135">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="90e65-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
