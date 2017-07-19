---
title: "DataReader によるデータの取得 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DataReader によるデータの取得
**DataReader** を使用してデータを取得するには、データ ソースから行を取得するために **Command.ExecuteReader** を呼び出して、**Command** オブジェクトのインスタンスを作成し、次に **DataReader** を作成する必要があります。  **DataReader** を使用する例を次に示します。ここで、`reader` は有効な DataReader を、`command` は有効な Command オブジェクトを表します。  
  
```  
reader = command.ExecuteReader();  
```  
  
 クエリの結果から行を取得するには、**DataReader** オブジェクトの **Read** メソッドを使用します。  返された行の各列にアクセスするには、その列の名前または序数参照を **DataReader** に渡します。  一方で **DataReader** は、最適のパフォーマンスが得られるように、ネイティブのデータ型を使用して列の値にアクセスするための一連のメソッド \(**GetDateTime**、**GetDouble**、**GetGuid**、**GetInt32** など\) も提供します。  データ プロバイダー固有の **DataReaders** の型指定されたアクセサー メソッドの一覧については、「<xref:System.Data.OleDb.OleDbDataReader>」および「<xref:System.Data.SqlClient.SqlDataReader>」を参照してください。  基になるデータ型がわかっている場合、型指定されたアクセサー メソッドを使用すると、列の値を取得するときに必要な型変換の量が少なくなります。  
  
> [!NOTE]
>  .NET Framework の Windows Server 2003 リリースには、**DataReader** の追加のプロパティである、**HasRows** が含まれているため、これを使用すると、読み取る前に **DataReader** が結果を返したかどうかを確認できます。  
  
 次に、**DataReader** オブジェクトを反復処理して各行から 2 つの列を返すコード サンプルを示します。  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 **DataReader** はバッファリングされないデータ ストリームを提供して、手続きロジックがデータ ソースからの結果を順番に効率的に処理できるようにします。  **DataReader** はデータをメモリにキャッシュしないため、大量のデータを取得する場合に適しています。  
  
## DataReader の終了  
 **DataReader** を使い終えたら、**Close** メソッドを呼び出す必要があります。  
  
 **Command** に出力パラメーターや戻り値が含まれていても、**DataReader** が終了するまでは使用できません。  
  
 **DataReader** が開いている間、**Connection** はその **DataReader** によって排他的に使用されています。  元の **DataReader** が終了するまでは、その **Connection** に対してはどのコマンドも実行できません。別の **DataReader** を作成することもできません。  
  
> [!NOTE]
>  クラスの **Finalize** メソッド内で **Connection**、**DataReader**、またはその他のマネージ オブジェクトの **Close** または **Dispose** を呼び出さないでください。  終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。  クラスがアンマネージ リソースを所有していない場合は、クラス定義に **Finalize** メソッドを含めないでください。  詳細については、「[Garbage Collection](../../../../docs/standard/garbage-collection/index.md)」を参照してください。  
  
## NextResult による複数の結果セットの取得  
 複数の結果セットが返された場合は、**DataReader** は **NextResult** メソッドを提供してその結果セットを順に反復処理します。  <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> メソッドを使用して、2 つの SELECT ステートメントの結果を処理する <xref:System.Data.SqlClient.SqlDataReader> の例を次に示します。  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## DataReader からのスキーマ情報の取得  
 **DataReader** が開いている間に **GetSchemaTable** メソッドを使用して、現在の結果セットについてのスキーマ情報を取得できます。  **GetSchemaTable** は、現在の結果セットのスキーマ情報を含む行と列が設定されている <xref:System.Data.DataTable> オブジェクトを返します。  **DataTable** には結果セットの列ごとに 1 行が設定されます。  スキーマ テーブル行の各列が、結果セットで返される列の 1 つのプロパティに割り当てられます。**ColumnName** はそのプロパティの名前であり、列の値はプロパティの値です。  **DataReader** のスキーマ情報を出力するコード サンプルを次に示します。  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## OLE DB のチャプターの使用  
 階層構造の行セット、つまりチャプター \(OLE DB では **DBTYPE\_HCHAPTER** 型、ADO では **adChapter** 型\) は <xref:System.Data.OleDb.OleDbDataReader> を使用して取得できます。  チャプターを含むクエリが **DataReader** として返されるとき、チャプターはその **DataReader** の列として返され、**DataReader** オブジェクトとして公開されます。  
  
 ADO.NET の **DataSet** を使用することで、テーブル間の親子のリレーションシップを使用して階層構造の行セットを表現することもできます。  詳細については、「[DataSets、DataTables、および DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)」を参照してください。  
  
 MSDataShape プロバイダーを使用して、顧客リストの顧客別オーダーのチャプター列を生成するコード サンプルを次に示します。  
  
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
  
## Oracle REF CURSOR による結果の取得  
 .NET Framework Data Provider for Oracle は、クエリ結果を返すために、Oracle REF CURSOR の使用をサポートしています。  Oracle REF CURSOR は <xref:System.Data.OracleClient.OracleDataReader> として返されます。  
  
 Oracle REF CURSOR を表す **OracleDataReader** オブジェクトは、<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> メソッドで取得できます。また、<xref:System.Data.DataSet> にデータを格納するために使用する <xref:System.Data.OracleClient.OracleDataAdapter> の **SelectCommand** として、1 つ以上の Oracle REF CURSOR を返す <xref:System.Data.OracleClient.OracleCommand> を指定することもできます。  
  
 Oracle データ ソースから返された REF CURSOR にアクセスするには、クエリ用の **OracleCommand** を作成し、その **Parameters** コレクションに、REF CURSOR を参照する出力パラメーターを追加します。  パラメーターの名前は、クエリの REF CURSOR パラメーターの名前と一致させる必要があります。  パラメーターの型を **OracleType.Cursor** に設定します。  **OracleCommand** の **ExecuteReader** メソッドは REF CURSOR に対する **OracleDataReader** を返します。  
  
 **OracleCommand** が複数の REF CURSOR を返す場合は、複数の出力パラメーターを追加してください。  **OracleCommand.ExecuteReader** メソッドを呼び出して、それぞれの REF CURSOR にアクセスできます。  **ExecuteReader** を呼び出すと、最初の REF CURSOR を参照する **OracleDataReader** が返されます。  次に **OracleDataReader.NextResult** メソッドを呼び出すと、後続の REF CURSOR にアクセスできます。  **OracleCommand.Parameters** コレクションのパラメーターが REF CURSOR 出力パラメーターと名前が一致していても、**OracleDataReader** は、**Parameters** コレクションに追加された順に出力パラメーターにアクセスします。  
  
 たとえば、次のような Oracle パッケージとパッケージ本体があるとします。  
  
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
  
 **OracleType.Cursor** 型の 2 つのパラメーターを **Parameters** コレクションに追加して、上の Oracle パッケージから REF CURSOR を返す **OracleCommand** を作成するコードを次に示します。  
  
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
  
 **OracleDataReader** の **Read** メソッドと **NextResult** メソッドを使用して、上のコマンドの結果を返すコードを次に示します。  REF CURSOR パラメーターは順番に返されます。  
  
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
  
 上のコマンドを使用して、Oracle パッケージの結果を **DataSet** に設定する例を次に示します。  
  
> [!NOTE]
>  **OverflowException** が発生しないようにするために、**DataRow** に値を格納する前に Oracle の NUMBER 型から有効な .NET Framework のデータ型への変換も行うことをお勧めします。  **FillError** イベントを使用して、**OverflowException** が発生したかどうかを確認できます。  **FillError** イベントの詳細については、「[DataAdapter のイベント処理](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)」を参照してください。  
  
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
  
## 参照  
 [Working with DataReaders](http://msdn.microsoft.com/ja-jp/126a966a-d08d-4d22-a19f-f432908b2b54)   
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [コマンドとパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)