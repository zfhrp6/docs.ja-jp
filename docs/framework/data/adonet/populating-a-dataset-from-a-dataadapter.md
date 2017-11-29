---
title: "DataAdapter からの DataSet の読み込み"
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
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3648340050e5ee3a761efcbedd89f649ff8d9c91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="populating-a-dataset-from-a-dataadapter"></a><span data-ttu-id="83deb-102">DataAdapter からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="83deb-102">Populating a DataSet from a DataAdapter</span></span>
<span data-ttu-id="83deb-103">[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] の <xref:System.Data.DataSet> は、データ ソースに依存しない一貫したリレーショナル プログラミング モデルを提供するメモリ常駐型のデータ表現です。</span><span class="sxs-lookup"><span data-stu-id="83deb-103">The [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]<xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model independent of the data source.</span></span> <span data-ttu-id="83deb-104">`DataSet` はテーブル、制約、およびテーブル間のリレーションシップを含む完全なデータのセットを表します。</span><span class="sxs-lookup"><span data-stu-id="83deb-104">The `DataSet` represents a complete set of data that includes tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="83deb-105">`DataSet` はデータ ソースとは独立しているため、 `DataSet` にはそのアプリケーションに固有のデータと複数のデータ ソースからのデータを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="83deb-105">Because the `DataSet` is independent of the data source, a `DataSet` can include data local to the application, and data from multiple data sources.</span></span> <span data-ttu-id="83deb-106">既存のデータ ソースとの対話は `DataAdapter`によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-106">Interaction with existing data sources is controlled through the `DataAdapter`.</span></span>  
  
 <span data-ttu-id="83deb-107">`SelectCommand` の `DataAdapter` プロパティは、データ ソースからデータを取得する `Command` オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="83deb-107">The `SelectCommand` property of the `DataAdapter` is a `Command` object that retrieves data from the data source.</span></span> <span data-ttu-id="83deb-108">`InsertCommand`の `UpdateCommand`、 `DeleteCommand` 、 `DataAdapter` の各プロパティは、 `Command` のデータに対して行われた変更に基づいてデータ ソースのデータ更新を管理する `DataSet`オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="83deb-108">The `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of the `DataAdapter` are `Command` objects that manage updates to the data in the data source according to modifications made to the data in the `DataSet`.</span></span> <span data-ttu-id="83deb-109">これらのプロパティはで詳しく説明[Dataadapter によるデータ ソースを更新](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)です。</span><span class="sxs-lookup"><span data-stu-id="83deb-109">These properties are covered in more detail in [Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="83deb-110">`Fill` の `DataAdapter` メソッドは、 `DataSet` の `SelectCommand` の結果を `DataAdapter`に設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="83deb-110">The `Fill` method of the `DataAdapter` is used to populate a `DataSet` with the results of the `SelectCommand` of the `DataAdapter`.</span></span> <span data-ttu-id="83deb-111">`Fill` は、その引数として、設定対象である `DataSet` と、 `DataTable` オブジェクト (つまり、 `DataTable` から返された行を格納する `SelectCommand`の名前) を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="83deb-111">`Fill` takes as its arguments a `DataSet` to be populated, and a `DataTable` object, or the name of the `DataTable` to be filled with the rows returned from the `SelectCommand`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83deb-112">`DataAdapter` を使用してテーブル全体を取得すると、特にテーブルの行数が多い場合は処理に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="83deb-112">Using the `DataAdapter` to retrieve all of a table takes time, especially if there are many rows in the table.</span></span> <span data-ttu-id="83deb-113">データベースにアクセスし、データを検索して処理した後、そのデータをクライアントに転送するという時間のかかる処理が伴うためです。</span><span class="sxs-lookup"><span data-stu-id="83deb-113">This is because accessing the database, locating and processing the data, and then transferring the data to the client is time-consuming.</span></span> <span data-ttu-id="83deb-114">また、テーブル全体をクライアントに取得しようとすると、サーバー上ですべての行がロックされます。</span><span class="sxs-lookup"><span data-stu-id="83deb-114">Pulling all of the table to the client also locks all of the rows on the server.</span></span> <span data-ttu-id="83deb-115">`WHERE` 句を使用して、クライアントから返される行数をできるだけ減らすことでパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="83deb-115">To improve performance, you can use the `WHERE` clause to greatly reduce the number of rows returned to the client.</span></span> <span data-ttu-id="83deb-116">また、 `SELECT` ステートメントで必要な列を明示的に指定するだけでもクライアントに返されるデータ量を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="83deb-116">You can also reduce the amount of data returned to the client by only explicitly listing required columns in the `SELECT` statement.</span></span> <span data-ttu-id="83deb-117">それ以外の対策としては、一度に数百行など、行をバッチで取得し、クライアントが現在のバッチの処理を完了した時点で次のバッチを取得する方法も効果的です。</span><span class="sxs-lookup"><span data-stu-id="83deb-117">Another good workaround is to retrieve the rows in batches (such as several hundred rows at a time) and only retrieve the next batch when the client is finished with the current batch.</span></span>  
  
 <span data-ttu-id="83deb-118">`Fill` メソッドは、 `DataReader` オブジェクトを暗黙的に使用して `DataSet`内でテーブルを作成するための列の名前と型、および `DataSet`内のテーブルの行を設定するためのデータを返します。</span><span class="sxs-lookup"><span data-stu-id="83deb-118">The `Fill` method uses the `DataReader` object implicitly to return the column names and types that are used to create the tables in the `DataSet`, and the data to populate the rows of the tables in the `DataSet`.</span></span> <span data-ttu-id="83deb-119">テーブルおよび列は、存在しない場合にのみ作成されます。それ以外の場合、 `Fill` には、既存の `DataSet` スキーマが使用されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-119">Tables and columns are only created if they do not already exist; otherwise `Fill` uses the existing `DataSet` schema.</span></span> <span data-ttu-id="83deb-120">列の型として作成[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]に従って内のテーブルの種類[ADO.NET でのデータ型マッピング](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)です。</span><span class="sxs-lookup"><span data-stu-id="83deb-120">Column types are created as [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types according to the tables in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span> <span data-ttu-id="83deb-121">データ ソースに主キーが存在し、 `DataAdapter`**によって制御されます。**`MissingSchemaAction`</span><span class="sxs-lookup"><span data-stu-id="83deb-121">Primary keys are not created unless they exist in the data source and `DataAdapter`**.**`MissingSchemaAction`</span></span> <span data-ttu-id="83deb-122">が `MissingSchemaAction`**によって制御されます。**`AddWithKey`によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-122">is set to `MissingSchemaAction`**.**`AddWithKey`.</span></span> <span data-ttu-id="83deb-123">`Fill` はテーブルに主キーがあることがわかると、主キー列の値がデータ ソースから返された主キー列の値と一致する行について、データ ソースから返されたデータで `DataSet` 内のデータを上書きします。</span><span class="sxs-lookup"><span data-stu-id="83deb-123">If `Fill` finds that a primary key exists for a table, it will overwrite data in the `DataSet` with data from the data source for rows where the primary key column values match those of the row returned from the data source.</span></span> <span data-ttu-id="83deb-124">主キーが見つからない場合は、 `DataSet`のテーブルの末尾にデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="83deb-124">If no primary key is found, the data is appended to the tables in the `DataSet`.</span></span> <span data-ttu-id="83deb-125">`Fill`設定するときに存在するすべてのマッピングを使用して、 `DataSet` (を参照してください[DataAdapter DataTable と DataColumn のマップ](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md))。</span><span class="sxs-lookup"><span data-stu-id="83deb-125">`Fill` uses any mappings that may exist when you populate the `DataSet` (see [DataAdapter DataTable and DataColumn Mappings](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83deb-126">`SelectCommand` が OUTER JOIN の結果を返す場合、 `DataAdapter` は、生成される `PrimaryKey` に `DataTable`値を設定しません。</span><span class="sxs-lookup"><span data-stu-id="83deb-126">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` does not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="83deb-127">自分で `PrimaryKey` を定義して、重複行が正しく解決されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83deb-127">You must define the `PrimaryKey` yourself to make sure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="83deb-128">詳細については、次を参照してください。[主キーを定義する](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)です。</span><span class="sxs-lookup"><span data-stu-id="83deb-128">For more information, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="83deb-129">次のコード サンプルでは、Microsoft SQL Server の <xref:System.Data.SqlClient.SqlDataAdapter> データベースへの <xref:System.Data.SqlClient.SqlConnection> を使用する `Northwind` のインスタンスを作成し、 <xref:System.Data.DataTable> 内の `DataSet` に顧客リストを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="83deb-129">The following code example creates an instance of a <xref:System.Data.SqlClient.SqlDataAdapter> that uses a <xref:System.Data.SqlClient.SqlConnection> to the Microsoft SQL Server `Northwind` database and populates a <xref:System.Data.DataTable> in a `DataSet` with the list of customers.</span></span> <span data-ttu-id="83deb-130"><xref:System.Data.SqlClient.SqlConnection> コンストラクターに渡される SQL ステートメントおよび <xref:System.Data.SqlClient.SqlDataAdapter> 引数は、 <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> の <xref:System.Data.SqlClient.SqlDataAdapter>プロパティを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-130">The SQL statement and <xref:System.Data.SqlClient.SqlConnection> arguments passed to the <xref:System.Data.SqlClient.SqlDataAdapter> constructor are used to create the <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> property of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83deb-131">例</span><span class="sxs-lookup"><span data-stu-id="83deb-131">Example</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim queryString As String = _  
  "SELECT CustomerID, CompanyName FROM dbo.Customers"  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  queryString, connection)  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
string queryString =   
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  <span data-ttu-id="83deb-132">このサンプル コードでは、 `Connection`の開始と終了を明示的に行っていません。</span><span class="sxs-lookup"><span data-stu-id="83deb-132">The code shown in this example does not explicitly open and close the `Connection`.</span></span> <span data-ttu-id="83deb-133">`Fill` メソッドは、接続がまだ開いていないことを認識すると `Connection` が使用している `DataAdapter` を暗黙的に開きます。</span><span class="sxs-lookup"><span data-stu-id="83deb-133">The `Fill` method implicitly opens the `Connection` that the `DataAdapter` is using if it finds that the connection is not already open.</span></span> <span data-ttu-id="83deb-134">`Fill` が接続を開いた場合は、 `Fill` の終了時に Fill が接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="83deb-134">If `Fill` opened the connection, it also closes the connection when `Fill` is finished.</span></span> <span data-ttu-id="83deb-135">これにより、 `Fill` や `Update`などの単一の操作を扱う場合にコードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="83deb-135">This can simplify your code when you deal with a single operation such as a `Fill` or an `Update`.</span></span> <span data-ttu-id="83deb-136">これに対し、開いている接続を必要とする複数の操作を実行する場合は、 `Open` の `Connection`メソッドを明示的に呼び出し、データ ソースに対する操作の実行後に `Close` の `Connection`メソッドを呼び出すことでアプリケーションのパフォーマンスを改善できます。</span><span class="sxs-lookup"><span data-stu-id="83deb-136">However, if you are performing multiple operations that require an open connection, you can improve the performance of your application by explicitly calling the `Open` method of the `Connection`, performing the operations against the data source, and then calling the `Close` method of the `Connection`.</span></span> <span data-ttu-id="83deb-137">リソースを解放して他のクライアント アプリケーションが使用できるようにするために、データ ソースへの接続を開いたままにする時間は最小限にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="83deb-137">You should try to keep connections to the data source open as briefly as possible to free resources for use by other client applications.</span></span>  
  
## <a name="multiple-result-sets"></a><span data-ttu-id="83deb-138">複数結果セット</span><span class="sxs-lookup"><span data-stu-id="83deb-138">Multiple Result Sets</span></span>  
 <span data-ttu-id="83deb-139">`DataAdapter` は複数の結果セットを検出すると、 `DataSet`に複数のテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="83deb-139">If the `DataAdapter` encounters multiple result sets, it creates multiple tables in the `DataSet`.</span></span> <span data-ttu-id="83deb-140">これらのテーブルには、Table0 のように、"Table" で始まるインクリメンタル既定名 Table*N*が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="83deb-140">The tables are given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span> <span data-ttu-id="83deb-141">テーブル名を引数として `Fill` メソッドに渡すと、TableName0 を表す "TableName" で始まるインクリメンタル既定名 TableName*N*が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="83deb-141">If a table name is passed as an argument to the `Fill` method, the tables are given an incremental default name of TableName*N*, starting with "TableName" for TableName0.</span></span>  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a><span data-ttu-id="83deb-142">複数の DataAdapter からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="83deb-142">Populating a DataSet from Multiple DataAdapters</span></span>  
 <span data-ttu-id="83deb-143">任意の数の`DataAdapter`オブジェクトで使用できる、`DataSet`です。</span><span class="sxs-lookup"><span data-stu-id="83deb-143">Any number of `DataAdapter` objects can be used with a `DataSet`.</span></span> <span data-ttu-id="83deb-144">それぞれの `DataAdapter` で 1 つ以上の `DataTable` オブジェクトにデータを格納し、関連するデータ ソースに更新を反映させることができます。</span><span class="sxs-lookup"><span data-stu-id="83deb-144">Each `DataAdapter` can be used to fill one or more `DataTable` objects and resolve updates back to the relevant data source.</span></span> <span data-ttu-id="83deb-145">`DataRelation` に対して `Constraint` オブジェクトおよび `DataSet` オブジェクトを部分的に追加できるため、複数の異なるデータ ソースから取得したデータを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="83deb-145">`DataRelation` and `Constraint` objects can be added to the `DataSet` locally, which enables you to relate data from dissimilar data sources.</span></span> <span data-ttu-id="83deb-146">たとえば、Microsoft SQL Server データベース、OLE DB を通じて公開される IBM DB2 データベース、および XML をストリーム転送するデータ ソースからのデータを `DataSet` に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="83deb-146">For example, a `DataSet` can contain data from a Microsoft SQL Server database, an IBM DB2 database exposed through OLE DB, and a data source that streams XML.</span></span> <span data-ttu-id="83deb-147">1 つ以上の `DataAdapter` オブジェクトを使用して、各データ ソースとの通信を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="83deb-147">One or more `DataAdapter` objects can handle communication to each data source.</span></span>  
  
### <a name="example"></a><span data-ttu-id="83deb-148">例</span><span class="sxs-lookup"><span data-stu-id="83deb-148">Example</span></span>  
 <span data-ttu-id="83deb-149">次のコード サンプルでは、Microsoft SQL Server 2000 の `Northwind` データベースおよび Microsoft Access の `Northwind` データベースから、それぞれ顧客リストと注文リストを取得します。</span><span class="sxs-lookup"><span data-stu-id="83deb-149">The following code example populates a list of customers from the `Northwind` database on Microsoft SQL Server, and a list of orders from the `Northwind` database stored in Microsoft Access 2000.</span></span> <span data-ttu-id="83deb-150">取得したテーブルを `DataRelation`で関連付けて、顧客および対応する注文の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="83deb-150">The filled tables are related with a `DataRelation`, and the list of customers is then displayed with the orders for that customer.</span></span> <span data-ttu-id="83deb-151">詳細については`DataRelation`、オブジェクトを参照してください[追加 Datarelation](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)と[Datarelation の移動](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)です。</span><span class="sxs-lookup"><span data-stu-id="83deb-151">For more information about `DataRelation` objects, see [Adding DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) and [Navigating DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).</span></span>  
  
```vb  
' Assumes that customerConnection is a valid SqlConnection object.  
' Assumes that orderConnection is a valid OleDbConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", customerConnection)  
  
Dim ordAdapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SELECT * FROM Orders", orderConnection)  
  
Dim customerOrders As DataSet = New DataSet()  
custAdapter.Fill(customerOrders, "Customers")  
ordAdapter.Fill(customerOrders, "Orders")  
  
Dim relation As DataRelation = _  
  customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustomerID"), _   
  customerOrders.Tables("Orders").Columns("CustomerID"))  
  
Dim pRow, cRow As DataRow  
For Each pRow In customerOrders.Tables("Customers").Rows  
  Console.WriteLine(pRow("CustomerID").ToString())  
  
  For Each cRow In pRow.GetChildRows(relation)  
    Console.WriteLine(vbTab & cRow("OrderID").ToString())  
  Next  
Next  
```  
  
```csharp  
// Assumes that customerConnection is a valid SqlConnection object.  
// Assumes that orderConnection is a valid OleDbConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", customerConnection);  
OleDbDataAdapter ordAdapter = new OleDbDataAdapter(  
  "SELECT * FROM Orders", orderConnection);  
  
DataSet customerOrders = new DataSet();  
  
custAdapter.Fill(customerOrders, "Customers");  
ordAdapter.Fill(customerOrders, "Orders");  
  
DataRelation relation = customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustomerID"],  
  customerOrders.Tables["Orders"].Columns["CustomerID"]);  
  
foreach (DataRow pRow in customerOrders.Tables["Customers"].Rows)  
{  
  Console.WriteLine(pRow["CustomerID"]);  
   foreach (DataRow cRow in pRow.GetChildRows(relation))  
    Console.WriteLine("\t" + cRow["OrderID"]);  
}  
```  
  
## <a name="sql-server-decimal-type"></a><span data-ttu-id="83deb-152">SQL Server の 10 進数型</span><span class="sxs-lookup"><span data-stu-id="83deb-152">SQL Server Decimal Type</span></span>  
 <span data-ttu-id="83deb-153">既定では、 `DataSet` は、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] のデータ型を使用してデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="83deb-153">By default, the `DataSet` stores data by using [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data types.</span></span> <span data-ttu-id="83deb-154">ほとんどのアプリケーションで、これらのデータ型を使用してデータ ソース情報を簡単に表示できます。</span><span class="sxs-lookup"><span data-stu-id="83deb-154">For most applications, these provide a convenient representation of data source information.</span></span> <span data-ttu-id="83deb-155">しかし、データ ソースのデータ型が SQL Server の 10 進数データ型または数値データ型の場合は、この表現によって問題が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="83deb-155">However, this representation may cause a problem when the data type in the data source is a SQL Server decimal or numeric data type.</span></span> <span data-ttu-id="83deb-156">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` データ型の最大有効桁数は 28 桁であるのに対し、SQL Server の `decimal` データ型の有効桁数は 38 桁です。</span><span class="sxs-lookup"><span data-stu-id="83deb-156">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` data type allows a maximum of 28 significant digits, whereas the SQL Server `decimal` data type allows 38 significant digits.</span></span> <span data-ttu-id="83deb-157">`SqlDataAdapter` が動作している間に、 `Fill` が、SQL Server の `decimal` フィールドの有効桁数が 28 文字を超えていると判断した場合、現在の行は `DataTable`に追加されません。</span><span class="sxs-lookup"><span data-stu-id="83deb-157">If the `SqlDataAdapter` determines during a `Fill` operation that the precision of a SQL Server `decimal` field is larger than 28 characters, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="83deb-158">その場合は `FillError` イベントが発生するため、開発者は有効桁数の消失が発生していないかどうかを確認し、適切に対応できます。</span><span class="sxs-lookup"><span data-stu-id="83deb-158">Instead the `FillError` event occurs, which enables you to determine whether a loss of precision will occur, and respond appropriately.</span></span> <span data-ttu-id="83deb-159">詳細については、`FillError`イベントを参照してください[DataAdapter イベントの処理](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)です。</span><span class="sxs-lookup"><span data-stu-id="83deb-159">For more information about the `FillError` event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span> <span data-ttu-id="83deb-160">SQL Server の `decimal` 値を取得するために、 <xref:System.Data.SqlClient.SqlDataReader> オブジェクトを使用し、 <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> メソッドを呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="83deb-160">To get the SQL Server `decimal` value, you can also use a <xref:System.Data.SqlClient.SqlDataReader> object and call the <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> method.</span></span>  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]<span data-ttu-id="83deb-161"> 2.0 では、 <xref:System.Data.SqlTypes> の `DataSet`に対するサポート機能が強化されています。</span><span class="sxs-lookup"><span data-stu-id="83deb-161"> 2.0 introduced enhanced support for <xref:System.Data.SqlTypes> in the `DataSet`.</span></span> <span data-ttu-id="83deb-162">詳細については、「 [SqlTypes and the DataSet](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83deb-162">For more information, see [SqlTypes and the DataSet](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).</span></span>  
  
## <a name="ole-db-chapters"></a><span data-ttu-id="83deb-163">OLE DB のチャプター</span><span class="sxs-lookup"><span data-stu-id="83deb-163">OLE DB Chapters</span></span>  
 <span data-ttu-id="83deb-164">階層構造の行セット、つまりチャプター (OLE DB では `DBTYPE_HCHAPTER`型、ADO では `adChapter`型) を使用して `DataSet`の内容を格納できます。</span><span class="sxs-lookup"><span data-stu-id="83deb-164">Hierarchical rowsets, or chapters (OLE DB type `DBTYPE_HCHAPTER`, ADO type `adChapter`) can be used to fill the contents of a `DataSet`.</span></span> <span data-ttu-id="83deb-165"><xref:System.Data.OleDb.OleDbDataAdapter> が `Fill` が動作している間にチャプター列を検出すると、そのチャプター列のための `DataTable` を作成し、チャプターから取得した列と行をこのテーブルに格納します。</span><span class="sxs-lookup"><span data-stu-id="83deb-165">When the <xref:System.Data.OleDb.OleDbDataAdapter> encounters a chaptered column during a `Fill` operation, a `DataTable` is created for the chaptered column, and that table is filled with the columns and rows from the chapter.</span></span> <span data-ttu-id="83deb-166">チャプター列用に作成されたテーブルには、親テーブルの名前とチャプター列の名前の両方を使用した "*ParentTableNameChapteredColumnName*" 形式の名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="83deb-166">The table created for the chaptered column is named by using both the parent table name and the chaptered column name in the form "*ParentTableNameChapteredColumnName*".</span></span> <span data-ttu-id="83deb-167">`DataSet` にチャプター列の名前と一致するテーブルが既に存在する場合は、現在のテーブルにチャプター データが格納されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-167">If a table already exists in the `DataSet` that matches the name of the chaptered column, the current table is filled with the chapter data.</span></span> <span data-ttu-id="83deb-168">既存のテーブルにチャプター内の列と一致する列が存在しない場合は、新しい列が追加されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-168">If there is no column in an existing table that matches a column found in the chapter, a new column is added.</span></span>  
  
 <span data-ttu-id="83deb-169">`DataSet` 内のテーブルにチャプター列のデータを格納する前に、親テーブルと子テーブルの両方に 1 つの整数列を追加し、親列を自動インクリメントに設定し、両方のテーブルに追加された列を使用して `DataRelation` を作成すると、階層構造の行セットを形成している親テーブルと子テーブルの間にリレーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-169">Before the tables in the `DataSet` are filled with the data in the chaptered columns, a relation is created between the parent and child tables of the hierarchical rowset by adding an integer column to both the parent and child table, setting the parent column to auto-increment, and creating a `DataRelation` using the added columns from both tables.</span></span> <span data-ttu-id="83deb-170">追加されたリレーションには親テーブルの名前とチャプター列の名前を使用した "*ParentTableNameChapterColumnName*" 形式の名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="83deb-170">The added relation is named by using the parent table and chapter column names in the form "*ParentTableNameChapterColumnName*".</span></span>  
  
 <span data-ttu-id="83deb-171">関連付けられた列は、 `DataSet`だけに存在します。</span><span class="sxs-lookup"><span data-stu-id="83deb-171">Note that the related column only exists in the `DataSet`.</span></span> <span data-ttu-id="83deb-172">そのデータ ソースからの次の Fill 操作を実行すると、変更を既存の行にマージするのではなく、テーブルに新しい行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-172">Subsequent fills from the data source can cause new rows to be added to the tables instead of changes being merged into existing rows.</span></span>  
  
 <span data-ttu-id="83deb-173">`DataAdapter.Fill` を受け取る `DataTable`オーバーロードを使用した場合は、そのテーブルだけにデータが格納されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-173">Note also that, if you use the `DataAdapter.Fill` overload that takes a `DataTable`, only that table will be filled.</span></span> <span data-ttu-id="83deb-174">自動インクリメント整数列は、引き続きそのテーブルに追加されますが、子テーブルの作成、子テーブルへのデータの格納、およびリレーションの作成は行われません。</span><span class="sxs-lookup"><span data-stu-id="83deb-174">An auto-incrementing integer column will still be added to the table, but no child table will be created or filled, and no relation will be created.</span></span>  
  
 <span data-ttu-id="83deb-175">MSDataShape プロバイダーを使用して顧客リスト内の各顧客に対応するオーダー列を生成する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="83deb-175">The following example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span> <span data-ttu-id="83deb-176">チャプター列を生成した後で、1 つの `DataSet` 内にそのデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="83deb-176">A `DataSet` is then filled with the data.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=northwind")  
  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
  
Dim customers As DataSet = New DataSet()  
  
adapter.Fill(customers, "Customers")  
End Using  
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection("Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=(local);Integrated Security=SSPI;Initial Catalog=northwind"))  
{  
OleDbDataAdapter adapter = new OleDbDataAdapter("SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
}  
```  
  
 <span data-ttu-id="83deb-177">`Fill` 操作が完了すると、 `DataSet` に `Customers` と `CustomersOrders`の 2 つのテーブルが格納されます。 `CustomersOrders` はチャプター列を表します。</span><span class="sxs-lookup"><span data-stu-id="83deb-177">When the `Fill` operation is complete, the `DataSet` contains two tables: `Customers` and `CustomersOrders`, where `CustomersOrders` represents the chaptered column.</span></span> <span data-ttu-id="83deb-178">`Orders` という列が `Customers` テーブルに追加され、 `CustomersOrders` という列が `CustomersOrders` テーブルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-178">An additional column named `Orders` is added to the `Customers` table, and an additional column named `CustomersOrders` is added to the `CustomersOrders` table.</span></span> <span data-ttu-id="83deb-179">`Orders` テーブルの `Customers` 列は、自動インクリメントに設定されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-179">The `Orders` column in the `Customers` table is set to auto-increment.</span></span> <span data-ttu-id="83deb-180">親テーブルである `DataRelation`テーブルに追加された列を使用して、 `CustomersOrders`という `Customers` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="83deb-180">A `DataRelation`, `CustomersOrders`, is created by using the columns that were added to the tables with `Customers` as the parent table.</span></span> <span data-ttu-id="83deb-181">サンプル結果の一部を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="83deb-181">The following tables show some sample results.</span></span>  
  
### <a name="tablename-customers"></a><span data-ttu-id="83deb-182">TableName: Customers</span><span class="sxs-lookup"><span data-stu-id="83deb-182">TableName: Customers</span></span>  
  
|<span data-ttu-id="83deb-183">CustomerID</span><span class="sxs-lookup"><span data-stu-id="83deb-183">CustomerID</span></span>|<span data-ttu-id="83deb-184">CompanyName</span><span class="sxs-lookup"><span data-stu-id="83deb-184">CompanyName</span></span>|<span data-ttu-id="83deb-185">Orders</span><span class="sxs-lookup"><span data-stu-id="83deb-185">Orders</span></span>|  
|----------------|-----------------|------------|  
|<span data-ttu-id="83deb-186">ALFKI</span><span class="sxs-lookup"><span data-stu-id="83deb-186">ALFKI</span></span>|<span data-ttu-id="83deb-187">Alfreds Futterkiste</span><span class="sxs-lookup"><span data-stu-id="83deb-187">Alfreds Futterkiste</span></span>|<span data-ttu-id="83deb-188">0</span><span class="sxs-lookup"><span data-stu-id="83deb-188">0</span></span>|  
|<span data-ttu-id="83deb-189">ANATR</span><span class="sxs-lookup"><span data-stu-id="83deb-189">ANATR</span></span>|<span data-ttu-id="83deb-190">Ana Trujillo Emparedados y helados</span><span class="sxs-lookup"><span data-stu-id="83deb-190">Ana Trujillo Emparedados y helados</span></span>|<span data-ttu-id="83deb-191">1</span><span class="sxs-lookup"><span data-stu-id="83deb-191">1</span></span>|  
  
### <a name="tablename-customersorders"></a><span data-ttu-id="83deb-192">TableName: CustomersOrders</span><span class="sxs-lookup"><span data-stu-id="83deb-192">TableName: CustomersOrders</span></span>  
  
|<span data-ttu-id="83deb-193">CustomerID</span><span class="sxs-lookup"><span data-stu-id="83deb-193">CustomerID</span></span>|<span data-ttu-id="83deb-194">OrderID</span><span class="sxs-lookup"><span data-stu-id="83deb-194">OrderID</span></span>|<span data-ttu-id="83deb-195">CustomersOrders</span><span class="sxs-lookup"><span data-stu-id="83deb-195">CustomersOrders</span></span>|  
|----------------|-------------|---------------------|  
|<span data-ttu-id="83deb-196">ALFKI</span><span class="sxs-lookup"><span data-stu-id="83deb-196">ALFKI</span></span>|<span data-ttu-id="83deb-197">10643</span><span class="sxs-lookup"><span data-stu-id="83deb-197">10643</span></span>|<span data-ttu-id="83deb-198">0</span><span class="sxs-lookup"><span data-stu-id="83deb-198">0</span></span>|  
|<span data-ttu-id="83deb-199">ALFKI</span><span class="sxs-lookup"><span data-stu-id="83deb-199">ALFKI</span></span>|<span data-ttu-id="83deb-200">10692</span><span class="sxs-lookup"><span data-stu-id="83deb-200">10692</span></span>|<span data-ttu-id="83deb-201">0</span><span class="sxs-lookup"><span data-stu-id="83deb-201">0</span></span>|  
|<span data-ttu-id="83deb-202">ANATR</span><span class="sxs-lookup"><span data-stu-id="83deb-202">ANATR</span></span>|<span data-ttu-id="83deb-203">10308</span><span class="sxs-lookup"><span data-stu-id="83deb-203">10308</span></span>|<span data-ttu-id="83deb-204">1</span><span class="sxs-lookup"><span data-stu-id="83deb-204">1</span></span>|  
|<span data-ttu-id="83deb-205">ANATR</span><span class="sxs-lookup"><span data-stu-id="83deb-205">ANATR</span></span>|<span data-ttu-id="83deb-206">10625</span><span class="sxs-lookup"><span data-stu-id="83deb-206">10625</span></span>|<span data-ttu-id="83deb-207">1</span><span class="sxs-lookup"><span data-stu-id="83deb-207">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83deb-208">関連項目</span><span class="sxs-lookup"><span data-stu-id="83deb-208">See Also</span></span>  
 [<span data-ttu-id="83deb-209">Dataadapter と Datareader</span><span class="sxs-lookup"><span data-stu-id="83deb-209">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="83deb-210">ADO.NET でのデータ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="83deb-210">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="83deb-211">Dbdataadapter を使用したデータの変更</span><span class="sxs-lookup"><span data-stu-id="83deb-211">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [<span data-ttu-id="83deb-212">複数のアクティブな結果セット (MARS)</span><span class="sxs-lookup"><span data-stu-id="83deb-212">Multiple Active Result Sets (MARS)</span></span>](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [<span data-ttu-id="83deb-213">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="83deb-213">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
