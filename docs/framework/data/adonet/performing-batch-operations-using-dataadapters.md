---
title: "DataAdapter を使用したバッチ操作の実行"
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
ms.assetid: e72ed5af-b24f-486c-8429-c8fd2208f844
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 66395e8011b5ea25bb3b52b25e0067dc5d8fc1ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="performing-batch-operations-using-dataadapters"></a><span data-ttu-id="86cd5-102">DataAdapter を使用したバッチ操作の実行</span><span class="sxs-lookup"><span data-stu-id="86cd5-102">Performing Batch Operations Using DataAdapters</span></span>
<span data-ttu-id="86cd5-103">ADO.NET のバッチ サポートを利用すると、<xref:System.Data.Common.DataAdapter> は、<xref:System.Data.DataSet> または <xref:System.Data.DataTable> から INSERT、UPDATE、および DELETE の各操作を 1 操作ずつサーバーに送信するのではなく、グループ化してサーバーに送信できます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-103">Batch support in ADO.NET allows a <xref:System.Data.Common.DataAdapter> to group INSERT, UPDATE, and DELETE operations from a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> to the server, instead of sending one operation at a time.</span></span> <span data-ttu-id="86cd5-104">こうすることで、サーバーへのラウンド トリップの回数が減少し、大幅なパフォーマンスの向上が期待できます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-104">The reduction in the number of round trips to the server typically results in significant performance gains.</span></span> <span data-ttu-id="86cd5-105">バッチ更新は、SQL Server (<xref:System.Data.SqlClient>) および Oracle (<xref:System.Data.OracleClient>) の .NET データ プロバイダーでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="86cd5-105">Batch updates are supported for the .NET data providers for SQL Server (<xref:System.Data.SqlClient>) and Oracle (<xref:System.Data.OracleClient>).</span></span>  
  
 <span data-ttu-id="86cd5-106">以前のバージョンの ADO.NET では、<xref:System.Data.DataSet> に格納されている変更内容をデータベースに反映する場合、`Update` の `DataAdapter` メソッドを実行して、1 行ずつデータベースを更新していました。</span><span class="sxs-lookup"><span data-stu-id="86cd5-106">When updating a database with changes from a <xref:System.Data.DataSet> in previous versions of ADO.NET, the `Update` method of a `DataAdapter` performed updates to the database one row at a time.</span></span> <span data-ttu-id="86cd5-107">このメソッドは、指定された <xref:System.Data.DataTable> 内の行を反復処理すると、各 <xref:System.Data.DataRow> を調べ、行が変更されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-107">As it iterated through the rows in the specified <xref:System.Data.DataTable>, it examined each <xref:System.Data.DataRow> to see if it had been modified.</span></span> <span data-ttu-id="86cd5-108">行が変更されている場合、その行の `UpdateCommand` プロパティの値に基づいて、適切な `InsertCommand`、`DeleteCommand`、または <xref:System.Data.DataRow.RowState%2A> のいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-108">If the row had been modified, it called the appropriate `UpdateCommand`, `InsertCommand`, or `DeleteCommand`, depending on the value of the <xref:System.Data.DataRow.RowState%2A> property for that row.</span></span> <span data-ttu-id="86cd5-109">各行の更新では、データベースへのネットワーク ラウンドトリップが発生します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-109">Every row update involved a network round-trip to the database.</span></span>  
  
 <span data-ttu-id="86cd5-110">ADO.NET 2.0 以降では、<xref:System.Data.Common.DbDataAdapter> は <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-110">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbDataAdapter> exposes an <xref:System.Data.Common.DbDataAdapter.UpdateBatchSize%2A> property.</span></span> <span data-ttu-id="86cd5-111">`UpdateBatchSize` を正の整数値に設定すると、データベースの更新が指定されたサイズのバッチとして送信されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-111">Setting the `UpdateBatchSize` to a positive integer value causes updates to the database to be sent as batches of the specified size.</span></span> <span data-ttu-id="86cd5-112">たとえば、`UpdateBatchSize` を 10 に設定すると、10 個の個別のステートメントがグループ化され、単一のバッチとして送信されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-112">For example, setting the `UpdateBatchSize` to 10 will group 10 separate statements and submit them as single batch.</span></span> <span data-ttu-id="86cd5-113">`UpdateBatchSize` を 0 に設定すると、<xref:System.Data.Common.DataAdapter> は、サーバーが処理できる最大のバッチ サイズを使用します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-113">Setting the `UpdateBatchSize` to 0 will cause the <xref:System.Data.Common.DataAdapter> to use the largest batch size that the server can handle.</span></span> <span data-ttu-id="86cd5-114">1 に設定すると、バッチ更新が無効になり、1 行ずつ送信されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-114">Setting it to 1 disables batch updates, as rows are sent one at a time.</span></span>  
  
 <span data-ttu-id="86cd5-115">サイズの大きいバッチを実行すると、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86cd5-115">Executing an extremely large batch could decrease performance.</span></span> <span data-ttu-id="86cd5-116">そのため、アプリケーションを実装する前に、バッチの最適なサイズ設定をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cd5-116">Therefore, you should test for the optimum batch size setting before implementing your application.</span></span>  
  
## <a name="using-the-updatebatchsize-property"></a><span data-ttu-id="86cd5-117">UpdateBatchSize プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="86cd5-117">Using the UpdateBatchSize Property</span></span>  
 <span data-ttu-id="86cd5-118">バッチ更新を有効にする場合、DataAdapter の <xref:System.Data.IDbCommand.UpdatedRowSource%2A>、`UpdateCommand` および `InsertCommand` の `DeleteCommand` プロパティ値を、<xref:System.Data.UpdateRowSource.None> または <xref:System.Data.UpdateRowSource.OutputParameters> に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86cd5-118">When batch updates are enabled, the <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of the DataAdapter's `UpdateCommand`, `InsertCommand`, and `DeleteCommand` should be set to <xref:System.Data.UpdateRowSource.None> or <xref:System.Data.UpdateRowSource.OutputParameters>.</span></span> <span data-ttu-id="86cd5-119">バッチ更新を実行する際、<xref:System.Data.IDbCommand.UpdatedRowSource%2A> または <xref:System.Data.UpdateRowSource.FirstReturnedRecord> のコマンドの <xref:System.Data.UpdateRowSource.Both> プロパティ値は、無効になります。</span><span class="sxs-lookup"><span data-stu-id="86cd5-119">When performing a batch update, the command's <xref:System.Data.IDbCommand.UpdatedRowSource%2A> property value of <xref:System.Data.UpdateRowSource.FirstReturnedRecord> or <xref:System.Data.UpdateRowSource.Both> is invalid.</span></span>  
  
 <span data-ttu-id="86cd5-120">`UpdateBatchSize` プロパティを使用するプロシージャを次に示します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-120">The following procedure demonstrates the use of the `UpdateBatchSize` property.</span></span> <span data-ttu-id="86cd5-121">このプロシージャは、2 つの引数、<xref:System.Data.DataSet>オブジェクトを表す列を持つ、 **ProductCategoryID**と**名前**フィールドで、 **Production.ProductCategory**テーブル、およびバッチ サイズ (バッチ内の行の数) を表す整数。</span><span class="sxs-lookup"><span data-stu-id="86cd5-121">The procedure takes two arguments, a <xref:System.Data.DataSet> object that has columns representing the **ProductCategoryID** and **Name** fields in the **Production.ProductCategory** table, and an integer representing the batch size (the number of rows in the batch).</span></span> <span data-ttu-id="86cd5-122">このコードにより、新しい <xref:System.Data.SqlClient.SqlDataAdapter> オブジェクトが作成され、その <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> プロパティ、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> プロパティ、および <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-122">The code creates a new <xref:System.Data.SqlClient.SqlDataAdapter> object, setting its <xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A>, <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A>, and <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> properties.</span></span> <span data-ttu-id="86cd5-123">このコードは、<xref:System.Data.DataSet> オブジェクトによって行が変更済みになっていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="86cd5-123">The code assumes that the <xref:System.Data.DataSet> object has modified rows.</span></span> <span data-ttu-id="86cd5-124">このオブジェクトは、`UpdateBatchSize` プロパティを設定し、更新を実行します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-124">It sets the `UpdateBatchSize` property and executes the update.</span></span>  
  
```vb  
Public Sub BatchUpdate( _  
  ByVal dataTable As DataTable, ByVal batchSize As Int32)  
    ' Assumes GetConnectionString() returns a valid connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    ' Connect to the AdventureWorks database.  
    Using connection As New SqlConnection(connectionString)  
        ' Create a SqlDataAdapter.  
        Dim adapter As New SqlDataAdapter()  
  
        'Set the UPDATE command and parameters.  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Production.ProductCategory SET " _  
          & "Name=@Name WHERE ProductCategoryID=@ProdCatID;", _  
          connection)  
        adapter.UpdateCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",  _  
          SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.UpdateCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the INSERT command and parameter.  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);", _  
  connection)  
        adapter.InsertCommand.Parameters.Add("@Name", _  
          SqlDbType.NVarChar, 50, "Name")  
        adapter.InsertCommand.UpdatedRowSource = _  
          UpdateRowSource.None  
  
        'Set the DELETE command and parameter.  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Production.ProductCategory " _  
          & "WHERE ProductCategoryID=@ProdCatID;", connection)  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID", _  
           SqlDbType.Int, 4, " ProductCategoryID ")  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None  
  
        ' Set the batch size.  
        adapter.UpdateBatchSize = batchSize  
  
        ' Execute the update.  
        adapter.Update(dataTable)  
    End Using  
End Sub  
```  
  
```csharp  
public static void BatchUpdate(DataTable dataTable,Int32 batchSize)  
{  
    // Assumes GetConnectionString() returns a valid connection string.  
    string connectionString = GetConnectionString();  
  
    // Connect to the AdventureWorks database.  
    using (SqlConnection connection = new   
      SqlConnection(connectionString))  
    {  
  
        // Create a SqlDataAdapter.  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        // Set the UPDATE command and parameters.  
        adapter.UpdateCommand = new SqlCommand(  
            "UPDATE Production.ProductCategory SET "  
            + "Name=@Name WHERE ProductCategoryID=@ProdCatID;",   
            connection);  
        adapter.UpdateCommand.Parameters.Add("@Name",   
           SqlDbType.NVarChar, 50, "Name");  
        adapter.UpdateCommand.Parameters.Add("@ProdCatID",   
           SqlDbType.Int, 4, "ProductCategoryID");  
         adapter.UpdateCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the INSERT command and parameter.  
        adapter.InsertCommand = new SqlCommand(  
            "INSERT INTO Production.ProductCategory (Name) VALUES (@Name);",   
            connection);  
        adapter.InsertCommand.Parameters.Add("@Name",   
          SqlDbType.NVarChar, 50, "Name");  
        adapter.InsertCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the DELETE command and parameter.  
        adapter.DeleteCommand = new SqlCommand(  
            "DELETE FROM Production.ProductCategory "  
            + "WHERE ProductCategoryID=@ProdCatID;", connection);  
        adapter.DeleteCommand.Parameters.Add("@ProdCatID",   
          SqlDbType.Int, 4, "ProductCategoryID");  
        adapter.DeleteCommand.UpdatedRowSource = UpdateRowSource.None;  
  
        // Set the batch size.  
        adapter.UpdateBatchSize = batchSize;  
  
        // Execute the update.  
        adapter.Update(dataTable);  
    }  
}  
```  
  
## <a name="handling-batch-update-related-events-and-errors"></a><span data-ttu-id="86cd5-125">バッチ更新に関連するイベントおよびエラーの処理</span><span class="sxs-lookup"><span data-stu-id="86cd5-125">Handling Batch Update-Related Events and Errors</span></span>  
 <span data-ttu-id="86cd5-126">**DataAdapter**が 2 つの更新に関連するイベント: **RowUpdating**と**RowUpdated**です。</span><span class="sxs-lookup"><span data-stu-id="86cd5-126">The **DataAdapter** has two update-related events: **RowUpdating** and **RowUpdated**.</span></span> <span data-ttu-id="86cd5-127">以前のバージョンの ADO.NET では、バッチ処理が無効になっていると、処理された行ごとにこれらのイベントがそれぞれ生成されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-127">In previous versions of ADO.NET, when batch processing is disabled, each of these events is generated once for each row processed.</span></span> <span data-ttu-id="86cd5-128">**RowUpdating**の更新が行われる前に生成および**RowUpdated**データベースの更新が完了した後に生成します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-128">**RowUpdating** is generated before the update occurs, and **RowUpdated** is generated after the database update has been completed.</span></span>  
  
### <a name="event-behavior-changes-with-batch-updates"></a><span data-ttu-id="86cd5-129">バッチ更新とイベント動作の違い</span><span class="sxs-lookup"><span data-stu-id="86cd5-129">Event Behavior Changes with Batch Updates</span></span>  
 <span data-ttu-id="86cd5-130">バッチ処理が有効になっている場合、1 度のデータベース操作で複数の行が更新されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-130">When batch processing is enabled, multiple rows are updated in a single database operation.</span></span> <span data-ttu-id="86cd5-131">このため、`RowUpdated` イベントは処理された各行ごとに発生しますが、`RowUpdating` イベントは各バッチ処理につき、1 つしか発生しません。</span><span class="sxs-lookup"><span data-stu-id="86cd5-131">Therefore, only one `RowUpdated` event occurs for each batch, whereas the `RowUpdating` event occurs for each row processed.</span></span> <span data-ttu-id="86cd5-132">バッチ処理が無効になっている場合、1 対 1 のインターリーブを伴う 2 つのイベントが発生します。つまり、1 つの行に対し、`RowUpdating` イベントが 1 つ、`RowUpdated` イベントが 1 つ発生します。すべての行が処理されるまで、次の行に対して `RowUpdating` イベントが 1 つ、`RowUpdated` イベントが 1 つ発生します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-132">When batch processing is disabled, the two events are fired with one-to-one interleaving, where one `RowUpdating` event and one `RowUpdated` event fire for a row, and then one `RowUpdating` and one `RowUpdated` event fire for the next row, until all of the rows are processed.</span></span>  
  
### <a name="accessing-updated-rows"></a><span data-ttu-id="86cd5-133">更新された行へのアクセス</span><span class="sxs-lookup"><span data-stu-id="86cd5-133">Accessing Updated Rows</span></span>  
 <span data-ttu-id="86cd5-134">バッチ処理が無効になっている場合、更新された行には、<xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> クラスの <xref:System.Data.Common.RowUpdatedEventArgs> プロパティを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-134">When batch processing is disabled, the row being updated can be accessed using the <xref:System.Data.Common.RowUpdatedEventArgs.Row%2A> property of the <xref:System.Data.Common.RowUpdatedEventArgs> class.</span></span>  
  
 <span data-ttu-id="86cd5-135">バッチ処理が有効になっている場合、複数の行に対して 1 つの `RowUpdated` イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-135">When batch processing is enabled, a single `RowUpdated` event is generated for multiple rows.</span></span> <span data-ttu-id="86cd5-136">つまり、各行の `Row` プロパティ値は null ですが、</span><span class="sxs-lookup"><span data-stu-id="86cd5-136">Therefore, the value of the `Row` property for each row is null.</span></span> <span data-ttu-id="86cd5-137">`RowUpdating` イベントは各行に対して生成されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-137">`RowUpdating` events are still generated for each row.</span></span> <span data-ttu-id="86cd5-138">処理された行にアクセスするには、<xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> クラスの <xref:System.Data.Common.RowUpdatedEventArgs> メソッドにより、配列に行への参照をコピーします。</span><span class="sxs-lookup"><span data-stu-id="86cd5-138">The <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method of the <xref:System.Data.Common.RowUpdatedEventArgs> class allows you to access the processed rows by copying references to the rows into an array.</span></span> <span data-ttu-id="86cd5-139">処理される行がない場合、`CopyToRows` が <xref:System.ArgumentNullException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="86cd5-139">If no rows are being processed, `CopyToRows` throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="86cd5-140"><xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> メソッドを呼び出す前に、<xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> プロパティを使用して、処理されている行数を取得できます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-140">Use the <xref:System.Data.Common.RowUpdatedEventArgs.RowCount%2A> property to return the number of rows processed before calling the <xref:System.Data.Common.RowUpdatedEventArgs.CopyToRows%2A> method.</span></span>  
  
### <a name="handling-data-errors"></a><span data-ttu-id="86cd5-141">データ エラーの処理</span><span class="sxs-lookup"><span data-stu-id="86cd5-141">Handling Data Errors</span></span>  
 <span data-ttu-id="86cd5-142">ステートメントを個別に実行した場合とバッチ処理を実行した場合では効果は同じです。</span><span class="sxs-lookup"><span data-stu-id="86cd5-142">Batch execution has the same effect as the execution of each individual statement.</span></span> <span data-ttu-id="86cd5-143">ステートメントはバッチに追加された順序と同じ順序で実行されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-143">Statements are executed in the order that the statements were added to the batch.</span></span> <span data-ttu-id="86cd5-144">エラーは、バッチ モードでも、バッチ モードが無効な場合と同様に処理されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-144">Errors are handled the same way in batch mode as they are when batch mode is disabled.</span></span> <span data-ttu-id="86cd5-145">つまり、各行が個別に処理されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-145">Each row is processed separately.</span></span> <span data-ttu-id="86cd5-146">データベース内で正常に処理された行だけが、<xref:System.Data.DataRow> 内の対応する <xref:System.Data.DataTable> で更新されます。</span><span class="sxs-lookup"><span data-stu-id="86cd5-146">Only rows that have been successfully processed in the database will be updated in the corresponding <xref:System.Data.DataRow> within the <xref:System.Data.DataTable>.</span></span>  
  
 <span data-ttu-id="86cd5-147">バッチ処理の実行に対してサポートされる SQL 構成は、データ プロバイダーとバックエンド データベースが決定します。</span><span class="sxs-lookup"><span data-stu-id="86cd5-147">The data provider and the back-end database server determine which SQL constructs are supported for batch execution.</span></span> <span data-ttu-id="86cd5-148">サポートされていないステートメントが実行時に送信されると、例外がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="86cd5-148">An exception may be thrown if a non-supported statement is submitted for execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86cd5-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="86cd5-149">See Also</span></span>  
 [<span data-ttu-id="86cd5-150">Dataadapter と Datareader</span><span class="sxs-lookup"><span data-stu-id="86cd5-150">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="86cd5-151">DataAdapter によるデータ ソースの更新</span><span class="sxs-lookup"><span data-stu-id="86cd5-151">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="86cd5-152">DataAdapter のイベントを処理</span><span class="sxs-lookup"><span data-stu-id="86cd5-152">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 [<span data-ttu-id="86cd5-153">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="86cd5-153">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
