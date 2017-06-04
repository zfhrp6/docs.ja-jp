---
title: "DataAdapter パラメーター | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f21e6aba-b76d-46ad-a83e-2ad8e0af1e12
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# DataAdapter パラメーター
<xref:System.Data.Common.DbDataAdapter> には 4 つのプロパティがあり、データ ソースからデータを取得したりデータ ソースのデータを更新したりするために使用されます。<xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> プロパティは、データ ソースのデータを返します。<xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>、<xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>、および <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> の各プロパティは、データ ソースの変更を管理するために使用されます。  `SelectCommand` プロパティは、`DataAdapter` の `Fill` メソッドを呼び出す前に設定しておく必要があります。  `InsertCommand`、`UpdateCommand`、`DeleteCommand` の各プロパティは、<xref:System.Data.DataTable> 内のデータに加えられた変更に応じて、`DataAdapter` の `Update` メソッドを呼び出す前に設定する必要があります。  たとえば、行が追加された場合には、`Update` を呼び出す前に `InsertCommand` を設定する必要があります。  `Update` によって挿入行、更新行、または削除行が処理されるとき、`DataAdapter` でそれぞれの `Command` プロパティが使用され、アクションが処理されます。  変更された行に関する現在の情報が `Parameters` コレクションを経由して `Command` オブジェクトに渡されます。  
  
 データ ソースの行を更新するときは、一意識別子を使用してテーブル内の更新する列を識別する UPDATE ステートメントを呼び出します。  一意識別子は、一般には主キー フィールドの値です。  UPDATE ステートメントでは、次の Transact\-SQL ステートメントに示すように、一意識別子と更新する列および値の両方を含むパラメーターを使用します。  
  
```  
UPDATE Customers SET CompanyName = @CompanyName   
  WHERE CustomerID = @CustomerID  
```  
  
> [!NOTE]
>  パラメーターのプレースホルダーの構文はデータ ソースに依存します。  次に、SQL Server のデータ ソースのプレースホルダーの例を示します。  <xref:System.Data.OleDb> パラメーターおよび <xref:System.Data.Odbc> パラメーターのプレースホルダーとして、疑問符 \(?\) を使用します。  
  
 この [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] の例では、`CustomerID` が `@CustomerID``` パラメーターの値と等しい行の `@CompanyName` パラメーターの値で `CompanyName` フィールドが更新されます。  これらのパラメーターは <xref:System.Data.SqlClient.SqlParameter> オブジェクトの <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A> プロパティを使用して、変更された行から情報を取得します。  前のサンプル UPDATE ステートメントのパラメーターを次に示します。  このコードは、変数 `adapter` が有効な <xref:System.Data.SqlClient.SqlDataAdapter> オブジェクトを表すことを前提としています。  
  
```  
adapter.Parameters.Add( _  
  "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
Dim parameter As SqlParameter = _  
  adapter.UpdateCommand.Parameters.Add("@CustomerID", _  
  SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
```  
  
 `Parameters` コレクションの `Add` メソッドは、パラメーター名、データ型、サイズ \(その型に適用可能な場合\)、および <xref:System.Data.Common.DbParameter.SourceColumn%2A> の名前を `DataTable` から受け取ります。  `@CustomerID` パラメーターの <xref:System.Data.Common.DbParameter.SourceVersion%2A> が `Original` に設定されることに注意してください。  この設定により、変更された <xref:System.Data.DataRow> で 1 つまたは複数の識別列の値が変更されている場合に、データ ソース内の既存の行が確実に更新されます。  識別列の値が変更されている場合、`Original` 行の値がデータ ソースの現在の値と一致し、`Current` 行の値に更新済みの値が格納されます。  `@CompanyName` パラメーターの `SourceVersion` は設定されていないため、既定値である `Current` の行の値が使用されます。  
  
> [!NOTE]
>  `DataAdapter` の `Fill` 操作と `DataReader` の `Get` メソッドのどちらの場合も、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の型は [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] データ プロバイダーから返された型から推論されます。  Microsoft SQL Server、OLE DB、および ODBC のデータ型から推論される [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の型およびアクセサー メソッドについては、「[ADO.NET でのデータ型のマッピング](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)」を参照してください。  
  
## Parameter.SourceColumn、Parameter.SourceVersion  
 `SourceColumn` および `SourceVersion` が、引数として `Parameter` コンストラクターに渡されるか、既存の `Parameter` のプロパティとして設定されます。  `SourceColumn` は、`Parameter` の値の取得先である <xref:System.Data.DataRow> の <xref:System.Data.DataColumn> の名前です。  `SourceVersion` により、`DataAdapter` で値の取得に使用される `DataRow` のバージョンを指定します。  
  
 `SourceVersion` で使用できる <xref:System.Data.DataRowVersion> 列挙型の値を次の表に示します。  
  
|DataRowVersion 列挙定数|説明|  
|-------------------------|--------|  
|`Current`|このパラメーターは列の現在の値を使用します。  既定値です。|  
|`Default`|このパラメーターには列の `DefaultValue` を使用します。|  
|`Original`|このパラメーターは列の元の値を使用します。|  
|`Proposed`|このパラメーターは提示された値を使用します。|  
  
 次のセクションの `SqlClient` コード サンプルでは、`CustomerID` 列を 2 つのパラメーター `@CustomerID` \(`SET CustomerID = @CustomerID`\) および `@OldCustomerID` \(`WHERE CustomerID = @OldCustomerID`\) の `SourceColumn` として使用する <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> のパラメーターを定義します。  `@CustomerID` パラメーターを使用して、**CustomerID** 列を `DataRow` の現在の値に更新します。  そのため、`SourceVersion` が `Current` である `CustomerID` `SourceColumn` が使用されます。  *@OldCustomerID* パラメーターは、データ ソースの現在の行を識別するために使用されています。  一致する列の値がその行の `Original` バージョンで見つかったため、`SourceVersion` が `Original` である同じ `SourceColumn` \(`CustomerID`\) が使用されます。  
  
## SqlClient パラメーターの使用  
 次のコード サンプルでは、データベースから追加のスキーマ情報を取得するために <xref:System.Data.SqlClient.SqlDataAdapter> を作成し、<xref:System.Data.Common.DataAdapter.MissingSchemaAction%2A> を <xref:System.Data.MissingSchemaAction> に設定する方法を示します。  <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> プロパティ、<xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> プロパティ、<xref:System.Data.SqlClient.SqlDataAdapter.UpdateCommand%2A> プロパティ、および <xref:System.Data.SqlClient.SqlDataAdapter.DeleteCommand%2A> プロパティが設定され、各プロパティに対応する <xref:System.Data.SqlClient.SqlParameter> オブジェクトが <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> コレクションに追加されます。  このメソッドは `SqlDataAdapter` オブジェクトを返します。  
  
 [!code-csharp[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/CS/source.cs#1)]
 [!code-vb[Classic WebData SqlDataAdapter.SqlDataAdapter Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/Classic WebData SqlDataAdapter.SqlDataAdapter Example/VB/source.vb#1)]  
  
## OleDb パラメーターのプレースホルダー  
 <xref:System.Data.OleDb.OleDbDataAdapter> オブジェクトと <xref:System.Data.Odbc.OdbcDataAdapter> オブジェクトの場合は、疑問符 \(?\) のプレースホルダーを使用してパラメーターを特定する必要があります。  
  
```vb  
Dim selectSQL As String = _  
  "SELECT CustomerID, CompanyName FROM Customers " & _  
  "WHERE CountryRegion = ? AND City = ?"  
Dim insertSQL AS String = _  
  "INSERT INTO Customers (CustomerID, CompanyName) VALUES (?, ?)"  
Dim updateSQL AS String = _  
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " & _  
  WHERE CustomerID = ?"  
Dim deleteSQL As String = "DELETE FROM Customers WHERE CustomerID = ?"  
```  
  
```csharp  
string selectSQL =   
  "SELECT CustomerID, CompanyName FROM Customers " +  
  "WHERE CountryRegion = ? AND City = ?";  
string insertSQL =   
  "INSERT INTO Customers (CustomerID, CompanyName) " +  
  "VALUES (?, ?)";  
string updateSQL =   
  "UPDATE Customers SET CustomerID = ?, CompanyName = ? " +  
  "WHERE CustomerID = ? ";  
string deleteSQL = "DELETE FROM Customers WHERE CustomerID = ?";  
```  
  
 パラメーターとして使用されるクエリ ステートメントは、作成する必要のある入力パラメーターおよび出力パラメーターを定義します。  パラメーターを作成するには、`Parameters.Add` メソッドまたは `Parameter` コンストラクターを使用して、列名、データ型、およびサイズを指定します。  `Integer` などの組み込みのデータ型の場合は、サイズを指定する必要はありません。サイズを指定する場合、既定のサイズを指定することになります。  
  
 次のコード サンプルでは、SQL ステートメントのパラメーターを作成した後、`DataSet` にデータを格納します。  
  
## OleDb の例  
  
```vb  
' Assumes that connection is a valid OleDbConnection object.  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter   
  
Dim selectCMD AS OleDbCommand = New OleDbCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add parameters and set values.  
selectCMD.Parameters.Add( _  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add( _  
  "@City", OleDbType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
  
```  
  
```csharp  
// Assumes that connection is a valid OleDbConnection object.  
OleDbDataAdapter adapter = new OleDbDataAdapter();  
  
OleDbCommand selectCMD = new OleDbCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
// Add parameters and set values.  
selectCMD.Parameters.Add(  
  "@CountryRegion", OleDbType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add(  
  "@City", OleDbType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
## Odbc パラメーター  
  
```vb  
' Assumes that connection is a valid OdbcConnection object.  
Dim adapter As OdbcDataAdapter = New OdbcDataAdapter  
  
Dim selectCMD AS OdbcCommand = New OdbcCommand(selectSQL, connection)  
adapter.SelectCommand = selectCMD  
  
' Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK"  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London"  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
  
```  
  
```csharp  
// Assumes that connection is a valid OdbcConnection object.  
OdbcDataAdapter adapter = new OdbcDataAdapter();  
  
OdbcCommand selectCMD = new OdbcCommand(selectSQL, connection);  
adapter.SelectCommand = selectCMD;  
  
//Add Parameters and set values.  
selectCMD.Parameters.Add("@CountryRegion", OdbcType.VarChar, 15).Value = "UK";  
selectCMD.Parameters.Add("@City", OdbcType.VarChar, 15).Value = "London";  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
>  パラメーターにパラメーター名が指定されない場合、Parameter1 から始まり数字が増分される既定名 Parameter*N* が割り当てられます。  パラメーター名を指定するときには、Parameter*N* という名前付け規則を使用しないことをお勧めします。これは、指定した名前が `ParameterCollection` 内の既存の既定パラメーター名と競合しないようにするためです。  指定した名前が既に存在する場合は、例外がスローされます。  
  
## 参照  
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [コマンドとパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [DataAdapter によるデータ ソースの更新](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)   
 [ストアド プロシージャでのデータの変更](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)   
 [ADO.NET でのデータ型のマッピング](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)