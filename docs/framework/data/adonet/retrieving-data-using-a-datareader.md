---
title: "DataReader によるデータの取得"
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
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0b66ca2fbcc760598b771b4c02a46acc3c9c1d4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-data-using-a-datareader"></a>DataReader によるデータの取得
使用してデータの取得、 **DataReader**のインスタンスを作成、**コマンド**オブジェクト作成し、作成、 **DataReader**を呼び出して**Command.ExecuteReader**データ ソースから行を取得します。 使用して次の例を示しています、 **DataReader**場所`reader`は有効な datareader および`command`有効なコマンド オブジェクトを表します。  
  
```  
reader = command.ExecuteReader();  
```  
  
 使用する、**読み取り**のメソッド、 **DataReader**クエリの結果から行を取得するオブジェクト。 返される行の各列をアクセスするには、名前または列の序数参照を渡すことによって、 **DataReader**です。 ただし、最適なパフォーマンスを**DataReader**一連の列の値に、ネイティブ データ型にアクセスできるようにするメソッドを提供 (**GetDateTime**、 **GetDouble**、 **GetGuid**、 **GetInt32**など)。 データ プロバイダーに固有の型指定されたアクセサー メソッドの一覧については**DataReaders**を参照してください<xref:System.Data.OleDb.OleDbDataReader>と<xref:System.Data.SqlClient.SqlDataReader>です。 基になるデータ型がわかっている場合、型指定されたアクセサー メソッドを使用すると、列の値を取得するときに必要な型変換の量が少なくなります。  
  
> [!NOTE]
>  .NET Framework の Windows Server 2003 リリースには、その他のプロパティが含まれています、 **DataReader**、 **HasRows**を使用するかどうかを**DataReader**がそこから読み取る前に結果を返した。  
  
 次のコード例を反復処理する**DataReader**オブジェクト、およびそれぞれの行から 2 つの列を返します。  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 **DataReader**は効率的にデータ ソースからの結果を順番に処理する手続き型のロジックを可能にするデータのバッファリングされていないストリームを提供します。 **DataReader**データがメモリにキャッシュされていないために、大量のデータを取得するときにお勧めします。  
  
## <a name="closing-the-datareader"></a>DataReader の終了  
 常に呼び出す必要があります、**閉じる**メソッドを使用してが完了したら、 **DataReader**オブジェクト。  
  
 場合、**コマンド**出力を含むパラメーターまたは戻り値の場合が使用できなくまで、 **DataReader**が閉じられます。  
  
 注意してください、 **DataReader**が開いている場合、**接続**によって排他的に使用されて**DataReader**です。 ためのコマンドを実行することはできません、**接続**、別の作成を含む**DataReader**、オリジナルまで**DataReader**が閉じられます。  
  
> [!NOTE]
>  呼び出す必要はありません**閉じる**または**Dispose**上、**接続**、 **DataReader**、またはその他のマネージ オブジェクトで、 **Finalize**クラスのメソッドです。 終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。 クラスがアンマネージ リソースを所有していない場合は含まれません、 **Finalize**メソッド、クラス定義にします。 詳細については、次を参照してください。[ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)です。  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>NextResult による複数の結果セットの取得  
 複数の結果セットが返される場合は、 **DataReader**提供、 **NextResult**の順序で結果を反復処理するメソッドを設定します。 <xref:System.Data.SqlClient.SqlDataReader> メソッドを使用して、2 つの SELECT ステートメントの結果を処理する <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> の例を次に示します。  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>DataReader からのスキーマ情報の取得  
 中に、 **DataReader**は開くことができますを取得する、現在使用して結果セットに関するスキーマ情報、 **GetSchemaTable**メソッドです。 **GetSchemaTable**を返します、<xref:System.Data.DataTable>オブジェクトの現在の結果セットのスキーマ情報が含まれている行と列に設定されます。 **DataTable**結果セットの列ごとに 1 つの行が含まれています。 スキーマ テーブル行の各列に返される列のプロパティにマップ結果セットの場所、 **ColumnName**プロパティの名前は、列の値は、プロパティの値。 次のコード例は、のスキーマ情報を書き込みます**DataReader**です。  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>OLE DB のチャプターの使用  
 階層的な行セット、つまりチャプター (OLE DB 型**DBTYPE_HCHAPTER**、ADO 型**adChapter**) を使用して取得できます、<xref:System.Data.OleDb.OleDbDataReader>です。 チャプターを含むクエリとして返される場合、 **DataReader**、チャプターを内の列として返されます**DataReader**として公開されると、 **DataReader**オブジェクト。  
  
 ADO.NET**データセット**テーブル間の親子リレーションシップを使用して階層的な行セットを表すも使用できます。 詳細については、次を参照してください。[データセット、Datatable、および Dataview](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)です。  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Oracle REF CURSOR による結果の取得  
 .NET Framework Data Provider for Oracle は、クエリ結果を返すために、Oracle REF CURSOR の使用をサポートしています。 Oracle REF CURSOR は <xref:System.Data.OracleClient.OracleDataReader> として返されます。  
  
 取得することができます、 **OracleDataReader**を使用して、Oracle REF CURSOR を表すオブジェクト、<xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>メソッド、およびするを指定できますも、<xref:System.Data.OracleClient.OracleCommand>として 1 つまたは複数の Oracle REF Cursor を返す、 **SelectCommand**の<xref:System.Data.OracleClient.OracleDataAdapter>塗りつぶしに使用される、<xref:System.Data.DataSet>です。  
  
 Oracle データ ソースから返された REF CURSOR にアクセスするには、作成、 **OracleCommand**クエリ用に REF カーソルを参照する出力パラメーターを追加し、**パラメーター** のコレクション**OracleCommand**です。 パラメーターの名前は、クエリの REF CURSOR パラメーターの名前と一致させる必要があります。 パラメーターの型を設定**OracleType.Cursor**です。 **ExecuteReader**のメソッド、 **OracleCommand**が返されます、 **OracleDataReader** REF CURSOR のです。  
  
 場合、 **OracleCommand**複数の REF CURSOR を返す複数の出力パラメーターを追加します。 それぞれの REF Cursor を呼び出すことによってアクセスできる、 **OracleCommand.ExecuteReader**メソッドです。 呼び出し**ExecuteReader**を返します、 **OracleDataReader**最初 REF カーソルを参照します。 呼び出すことができますし、 **OracleDataReader.NextResult**後続の REF Cursor にアクセスするメソッド。 ただしでは、パラメーター、 **OracleCommand.Parameters**コレクション一致 REF CURSOR 出力パラメーターを名前で、 **OracleDataReader** に追加された順序でそれらにアクセスします。**パラメーター**コレクション。  
  
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
  
 次のコードを作成、 **OracleCommand**型の 2 つのパラメーターを追加することで、上の Oracle パッケージから REF Cursor を返す**OracleType.Cursor**を**パラメーター**コレクション。  
  
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
  
 次のコードは、前のコマンドを使用して、結果を返します、**読み取り**と**NextResult**のメソッド、 **OracleDataReader**です。 REF CURSOR パラメーターは順番に返されます。  
  
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
  
 次の例では、前のコマンドを使用して、事前設定、**データセット**Oracle パッケージの結果。  
  
> [!NOTE]
>  避けるために、 **OverflowException**は有効な .NET Framework 型の値を格納する前に Oracle の NUMBER 型から変換を処理することをお勧め、 **DataRow**です。 使用することができます、 **FillError**イベントかどうかを**OverflowException**が発生しました。 詳細については、 **FillError**イベントを参照してください[DataAdapter イベントの処理](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)です。  
  
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
  
## <a name="see-also"></a>関連項目  
 [Datareader の操作](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Dataadapter と Datareader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [データベース スキーマ情報の取得](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
