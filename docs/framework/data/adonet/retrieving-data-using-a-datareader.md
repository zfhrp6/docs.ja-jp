---
title: DataReader によるデータの取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 0c78db5ce7a6a988e40718daca1d828096a734d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353261"
---
# <a name="retrieving-data-using-a-datareader"></a><span data-ttu-id="adab3-102">DataReader によるデータの取得</span><span class="sxs-lookup"><span data-stu-id="adab3-102">Retrieving Data Using a DataReader</span></span>
<span data-ttu-id="adab3-103">使用してデータの取得、 **DataReader**のインスタンスを作成、**コマンド**オブジェクト作成し、作成、 **DataReader**を呼び出して**Command.ExecuteReader**データ ソースから行を取得します。</span><span class="sxs-lookup"><span data-stu-id="adab3-103">Retrieving data using a **DataReader** involves creating an instance of the **Command** object and then creating a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="adab3-104">使用して次の例を示しています、 **DataReader**場所`reader`は有効な datareader および`command`有効なコマンド オブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="adab3-104">The following example illustrates using a **DataReader** where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  
  
```  
reader = command.ExecuteReader();  
```  
  
 <span data-ttu-id="adab3-105">使用する、**読み取り**のメソッド、 **DataReader**クエリの結果から行を取得するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="adab3-105">You use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span> <span data-ttu-id="adab3-106">返される行の各列をアクセスするには、名前または列の序数参照を渡すことによって、 **DataReader**です。</span><span class="sxs-lookup"><span data-stu-id="adab3-106">You can access each column of the returned row by passing the name or ordinal reference of the column to the **DataReader**.</span></span> <span data-ttu-id="adab3-107">ただし、最適なパフォーマンスを**DataReader**一連の列の値に、ネイティブ データ型にアクセスできるようにするメソッドを提供 (**GetDateTime**、 **GetDouble**、 **GetGuid**、 **GetInt32**など)。</span><span class="sxs-lookup"><span data-stu-id="adab3-107">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="adab3-108">データ プロバイダーに固有の型指定されたアクセサー メソッドの一覧については**DataReaders**を参照してください<xref:System.Data.OleDb.OleDbDataReader>と<xref:System.Data.SqlClient.SqlDataReader>です。</span><span class="sxs-lookup"><span data-stu-id="adab3-108">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="adab3-109">基になるデータ型がわかっている場合、型指定されたアクセサー メソッドを使用すると、列の値を取得するときに必要な型変換の量が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="adab3-109">Using the typed accessor methods, assuming the underlying data type is known, reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adab3-110">.NET Framework の Windows Server 2003 リリースには、その他のプロパティが含まれています、 **DataReader**、 **HasRows**を使用するかどうかを**DataReader**がそこから読み取る前に結果を返した。</span><span class="sxs-lookup"><span data-stu-id="adab3-110">The Windows Server 2003 release of the .NET Framework includes an additional property for the **DataReader**, **HasRows**, which enables you to determine if the **DataReader** has returned any results before reading from it.</span></span>  
  
 <span data-ttu-id="adab3-111">次のコード例を反復処理する**DataReader**オブジェクト、およびそれぞれの行から 2 つの列を返します。</span><span class="sxs-lookup"><span data-stu-id="adab3-111">The following code example iterates through a **DataReader** object, and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 <span data-ttu-id="adab3-112">**DataReader**は効率的にデータ ソースからの結果を順番に処理する手続き型のロジックを可能にするデータのバッファリングされていないストリームを提供します。</span><span class="sxs-lookup"><span data-stu-id="adab3-112">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="adab3-113">**DataReader**データがメモリにキャッシュされていないために、大量のデータを取得するときにお勧めします。</span><span class="sxs-lookup"><span data-stu-id="adab3-113">The **DataReader** is a good choice when retrieving large amounts of data because the data is not cached in memory.</span></span>  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="adab3-114">DataReader の終了</span><span class="sxs-lookup"><span data-stu-id="adab3-114">Closing the DataReader</span></span>  
 <span data-ttu-id="adab3-115">常に呼び出す必要があります、**閉じる**メソッドを使用してが完了したら、 **DataReader**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="adab3-115">You should always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="adab3-116">場合、**コマンド**出力を含むパラメーターまたは戻り値の場合が使用できなくまで、 **DataReader**が閉じられます。</span><span class="sxs-lookup"><span data-stu-id="adab3-116">If your **Command** contains output parameters or return values, they will not be available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="adab3-117">注意してください、 **DataReader**が開いている場合、**接続**によって排他的に使用されて**DataReader**です。</span><span class="sxs-lookup"><span data-stu-id="adab3-117">Note that while a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="adab3-118">ためのコマンドを実行することはできません、**接続**、別の作成を含む**DataReader**、オリジナルまで**DataReader**が閉じられます。</span><span class="sxs-lookup"><span data-stu-id="adab3-118">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adab3-119">呼び出す必要はありません**閉じる**または**Dispose**上、**接続**、 **DataReader**、またはその他のマネージ オブジェクトで、 **Finalize**クラスのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="adab3-119">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="adab3-120">終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。</span><span class="sxs-lookup"><span data-stu-id="adab3-120">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="adab3-121">クラスがアンマネージ リソースを所有していない場合は含まれません、 **Finalize**メソッド、クラス定義にします。</span><span class="sxs-lookup"><span data-stu-id="adab3-121">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="adab3-122">詳細については、次を参照してください。[ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="adab3-122">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="adab3-123">NextResult による複数の結果セットの取得</span><span class="sxs-lookup"><span data-stu-id="adab3-123">Retrieving Multiple Result Sets using NextResult</span></span>  
 <span data-ttu-id="adab3-124">複数の結果セットが返される場合は、 **DataReader**提供、 **NextResult**の順序で結果を反復処理するメソッドを設定します。</span><span class="sxs-lookup"><span data-stu-id="adab3-124">If multiple result sets are returned, the **DataReader** provides the **NextResult** method to iterate through the result sets in order.</span></span> <span data-ttu-id="adab3-125"><xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、2 つの SELECT ステートメントの結果を処理する <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="adab3-125">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="adab3-126">DataReader からのスキーマ情報の取得</span><span class="sxs-lookup"><span data-stu-id="adab3-126">Getting Schema Information from the DataReader</span></span>  
 <span data-ttu-id="adab3-127">中に、 **DataReader**は開くことができますを取得する、現在使用して結果セットに関するスキーマ情報、 **GetSchemaTable**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="adab3-127">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="adab3-128">**GetSchemaTable**を返します、<xref:System.Data.DataTable>オブジェクトの現在の結果セットのスキーマ情報が含まれている行と列に設定されます。</span><span class="sxs-lookup"><span data-stu-id="adab3-128">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="adab3-129">**DataTable**結果セットの列ごとに 1 つの行が含まれています。</span><span class="sxs-lookup"><span data-stu-id="adab3-129">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="adab3-130">スキーマ テーブル行の各列に返される列のプロパティにマップ結果セットの場所、 **ColumnName**プロパティの名前は、列の値は、プロパティの値。</span><span class="sxs-lookup"><span data-stu-id="adab3-130">Each column of the schema table row maps to a property of the column returned in the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="adab3-131">次のコード例は、のスキーマ情報を書き込みます**DataReader**です。</span><span class="sxs-lookup"><span data-stu-id="adab3-131">The following code example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="adab3-132">OLE DB のチャプターの使用</span><span class="sxs-lookup"><span data-stu-id="adab3-132">Working with OLE DB Chapters</span></span>  
 <span data-ttu-id="adab3-133">階層的な行セット、つまりチャプター (OLE DB 型**DBTYPE_HCHAPTER**、ADO 型**adChapter**) を使用して取得できます、<xref:System.Data.OleDb.OleDbDataReader>です。</span><span class="sxs-lookup"><span data-stu-id="adab3-133">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**) can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="adab3-134">チャプターを含むクエリとして返される場合、 **DataReader**、チャプターを内の列として返されます**DataReader**として公開されると、 **DataReader**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="adab3-134">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="adab3-135">ADO.NET**データセット**テーブル間の親子リレーションシップを使用して階層的な行セットを表すも使用できます。</span><span class="sxs-lookup"><span data-stu-id="adab3-135">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets using parent-child relationships between tables.</span></span> <span data-ttu-id="adab3-136">詳細については、次を参照してください。[データセット、Datatable、および Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="adab3-136">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="adab3-137">MSDataShape プロバイダーを使用して、顧客リストの顧客別オーダーのチャプター列を生成するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="adab3-137">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="adab3-138">Oracle REF CURSOR による結果の取得</span><span class="sxs-lookup"><span data-stu-id="adab3-138">Returning Results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="adab3-139">.NET Framework Data Provider for Oracle は、クエリ結果を返すために、Oracle REF CURSOR の使用をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="adab3-139">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="adab3-140">Oracle REF CURSOR は <xref:System.Data.OracleClient.OracleDataReader> として返されます。</span><span class="sxs-lookup"><span data-stu-id="adab3-140">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="adab3-141">取得することができます、 **OracleDataReader**を使用して、Oracle REF CURSOR を表すオブジェクト、<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>メソッド、およびするを指定できますも、<xref:System.Data.OracleClient.OracleCommand>として 1 つまたは複数の Oracle REF Cursor を返す、 **SelectCommand**の<xref:System.Data.OracleClient.OracleDataAdapter>塗りつぶしに使用される、<xref:System.Data.DataSet>です。</span><span class="sxs-lookup"><span data-stu-id="adab3-141">You can retrieve an **OracleDataReader** object, that represents an Oracle REF CURSOR using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method, and you can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="adab3-142">Oracle データ ソースから返された REF CURSOR にアクセスするには、作成、 **OracleCommand**クエリ用に REF カーソルを参照する出力パラメーターを追加し、**パラメーター** のコレクション**OracleCommand**です。</span><span class="sxs-lookup"><span data-stu-id="adab3-142">To access a REF CURSOR returned from an Oracle data source, create an **OracleCommand** for your query and add an output parameter that references the REF CURSOR to the **Parameters** collection of your **OracleCommand**.</span></span> <span data-ttu-id="adab3-143">パラメーターの名前は、クエリの REF CURSOR パラメーターの名前と一致させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="adab3-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="adab3-144">パラメーターの型を設定**OracleType.Cursor**です。</span><span class="sxs-lookup"><span data-stu-id="adab3-144">Set the type of the parameter to **OracleType.Cursor**.</span></span> <span data-ttu-id="adab3-145">**ExecuteReader**のメソッド、 **OracleCommand**が返されます、 **OracleDataReader** REF CURSOR のです。</span><span class="sxs-lookup"><span data-stu-id="adab3-145">The **ExecuteReader** method of your **OracleCommand** will return an **OracleDataReader** for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="adab3-146">場合、 **OracleCommand**複数の REF CURSOR を返す複数の出力パラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="adab3-146">If your **OracleCommand** returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="adab3-147">それぞれの REF Cursor を呼び出すことによってアクセスできる、 **OracleCommand.ExecuteReader**メソッドです。</span><span class="sxs-lookup"><span data-stu-id="adab3-147">You can access the different REF CURSORs by calling the **OracleCommand.ExecuteReader** method.</span></span> <span data-ttu-id="adab3-148">呼び出し**ExecuteReader**を返します、 **OracleDataReader**最初 REF カーソルを参照します。</span><span class="sxs-lookup"><span data-stu-id="adab3-148">The call to **ExecuteReader** returns an **OracleDataReader** referencing the first REF CURSOR.</span></span> <span data-ttu-id="adab3-149">呼び出すことができますし、 **OracleDataReader.NextResult**後続の REF Cursor にアクセスするメソッド。</span><span class="sxs-lookup"><span data-stu-id="adab3-149">You can then call the **OracleDataReader.NextResult** method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="adab3-150">ただしでは、パラメーター、 **OracleCommand.Parameters**コレクション一致 REF CURSOR 出力パラメーターを名前で、 **OracleDataReader** に追加された順序でそれらにアクセスします。**パラメーター**コレクション。</span><span class="sxs-lookup"><span data-stu-id="adab3-150">Although the parameters in your **OracleCommand.Parameters** collection match the REF CURSOR output parameters by name, the **OracleDataReader** accesses them in the order that they were added to the **Parameters** collection.</span></span>  
  
 <span data-ttu-id="adab3-151">たとえば、次のような Oracle パッケージとパッケージ本体があるとします。</span><span class="sxs-lookup"><span data-stu-id="adab3-151">For example, consider the following Oracle package and package body.</span></span>  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 <span data-ttu-id="adab3-152">次のコードを作成、 **OracleCommand**型の 2 つのパラメーターを追加することで、上の Oracle パッケージから REF Cursor を返す**OracleType.Cursor**を**パラメーター**コレクション。</span><span class="sxs-lookup"><span data-stu-id="adab3-152">The following code creates an **OracleCommand** that returns the REF CURSORs from the previous Oracle package by adding two parameters of type **OracleType.Cursor** to the **Parameters** collection.</span></span>  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 <span data-ttu-id="adab3-153">次のコードは、前のコマンドを使用して、結果を返します、**読み取り**と**NextResult**のメソッド、 **OracleDataReader**です。</span><span class="sxs-lookup"><span data-stu-id="adab3-153">The following code returns the results of the previous command using the **Read** and **NextResult** methods of the **OracleDataReader**.</span></span> <span data-ttu-id="adab3-154">REF CURSOR パラメーターは順番に返されます。</span><span class="sxs-lookup"><span data-stu-id="adab3-154">The REF CURSOR parameters are returned in order.</span></span>  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 <span data-ttu-id="adab3-155">次の例では、前のコマンドを使用して、事前設定、**データセット**Oracle パッケージの結果。</span><span class="sxs-lookup"><span data-stu-id="adab3-155">The following example uses the previous command to populate a **DataSet** with the results of the Oracle package.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="adab3-156">避けるために、 **OverflowException**は有効な .NET Framework 型の値を格納する前に Oracle の NUMBER 型から変換を処理することをお勧め、 **DataRow**です。</span><span class="sxs-lookup"><span data-stu-id="adab3-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a **DataRow**.</span></span> <span data-ttu-id="adab3-157">使用することができます、 **FillError**イベントかどうかを**OverflowException**が発生しました。</span><span class="sxs-lookup"><span data-stu-id="adab3-157">You can use the **FillError** event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="adab3-158">詳細については、 **FillError**イベントを参照してください[DataAdapter イベントの処理](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)です。</span><span class="sxs-lookup"><span data-stu-id="adab3-158">For more information on the **FillError** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a><span data-ttu-id="adab3-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="adab3-159">See Also</span></span>  
 [<span data-ttu-id="adab3-160">Datareader の操作</span><span class="sxs-lookup"><span data-stu-id="adab3-160">Working with DataReaders</span></span>](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="adab3-161">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="adab3-161">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="adab3-162">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="adab3-162">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="adab3-163">データベース スキーマ情報の取得</span><span class="sxs-lookup"><span data-stu-id="adab3-163">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="adab3-164">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="adab3-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
