---
title: "接続の確立 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 接続の確立
Microsoft SQL Server に接続する場合は、.NET Framework Data Provider for SQL Server の <xref:System.Data.SqlClient.SqlConnection> オブジェクトを使用します。  OLE DB データ ソースに接続する場合は、.NET Framework Data Provider for OLE DB の <xref:System.Data.OleDb.OleDbConnection> オブジェクトを使用します。  ODBC データ ソースに接続する場合は、.NET Framework Data Provider for ODBC の <xref:System.Data.Odbc.OdbcConnection> オブジェクトを使用します。  Oracle データ ソースに接続する場合は、.NET Framework Data Provider for Oracle の <xref:System.Data.OracleClient.OracleConnection> オブジェクトを使用します。  安全な接続文字列の格納および取得については、「[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)」を参照してください。  
  
## 接続の終了  
 接続がプールに返されるようにするために、接続を使い終えたら必ず接続を終了することをお勧めします。  Visual Basic または C\# の `Using` ブロックは、コードがこのブロックを終了したときに接続を破棄します。これは、未処理の例外の場合でも実行されます。  詳細については、「[using ステートメント](../Topic/using%20Statement%20\(C%23%20Reference\).md)」および「[Using Statement](../Topic/Using%20Statement%20\(Visual%20Basic\).md)」を参照してください。  
  
 また、使用しているプロバイダーの接続オブジェクトの `Close` または `Dispose` メソッドを使用することもできます。  明示的に終了されていない接続は、プールに追加したり返したりすることができないことがあります。  たとえば、スコープ外に出ても、明示的に終了されていない接続は、最大プール サイズに達した時点でその接続がまだ有効である場合にだけ接続プールに返されます。  詳細については、「[OLE DB、ODBC、および Oracle 接続プール](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)」を参照してください。  
  
> [!NOTE]
>  クラスの `Finalize` メソッド内で **Connection**、**DataReader**、またはその他のマネージ オブジェクトの `Close` または `Dispose` を呼び出さないでください。  終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。  クラスがアンマネージ リソースを所有していない場合は、クラス定義に `Finalize` メソッドを含めないでください。  詳細については、「[Garbage Collection](../../../../docs/standard/garbage-collection/index.md)」を参照してください。  
  
> [!NOTE]
>  接続が接続プールからフェッチされたり接続プールに返されたりしたとき、ログイン イベントとログアウト イベントはサーバーで発生しません。これは、接続プールに返されても接続は実際には終了していないためです。  詳細については、「[SQL Server の接続プール \(ADO.NET\)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)」を参照してください。  
  
## SQL Server への接続  
 .NET Framework Data Provider for SQL Server は、OLE DB \(ADO\) 接続文字列フォーマットに似た接続文字列フォーマットをサポートします。  有効な文字列フォーマットの名前および値については、<xref:System.Data.SqlClient.SqlConnection> オブジェクトの <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> プロパティを参照してください。  また、<xref:System.Data.SqlClient.SqlConnectionStringBuilder> クラスを使用すると、構文的に正しい接続文字列を実行時に作成できます。  詳細については、「[接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)」を参照してください。  
  
 SQL Server のデータベースへの接続を開いて確立する方法を次のサンプル コードに示します。  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New SqlConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (SqlConnection connection = new SqlConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
### 統合セキュリティと ASP.NET  
 SQL Server 統合セキュリティ \(信頼関係接続とも呼ばれます\) は、SQL Server への接続を保護します。接続文字列でユーザー ID とパスワードを公開することがなく、接続の認証用に推奨されている方法でもあるためです。  統合セキュリティでは、実行中のプロセスの現在のセキュリティ ID またはトークンを使用します。  これは、デスクトップ アプリケーションでは通常、現在ログオンしているユーザーの ID です。  
  
 ASP.NET アプリケーションのセキュリティ ID は、他のオプションのうちのいずれかに設定することもできます。  SQL Server に接続するときに ASP.NET アプリケーションが使用するセキュリティ ID の詳細については、「[ASP.NET Impersonation](../Topic/ASP.NET%20Impersonation.md)」、「[ASP.NET Authentication](../Topic/ASP.NET%20Authentication.md)」、および「[How to: Access SQL Server Using Windows Integrated Security](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Windows%20Integrated%20Security.md)」を参照してください。  
  
## OLE DB データ ソースへの接続  
 .NET Framework Data Provider for OLE DB は、**OleDbConnection** オブジェクトを使用して、OLE DB によって公開されているデータ ソースへの接続を \(SQLOLEDB: OLE DB Provider for SQL Server を通じて\) 提供します。  
  
 .NET Framework Data Provider for OLE DB で使用される接続文字列フォーマットは ADO で使用される接続文字列フォーマットと同じですが、次の例外があります。  
  
-   **Provider** キーワードは必須です。  
  
-   **URL**、**Remote Provider**、および **Remote Server** キーワードはサポートされていません。  
  
 OLE DB 接続文字列の詳細については、「<xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>」を参照してください。  また、<xref:System.Data.OleDb.OleDbConnectionStringBuilder> を使用すると、接続文字列を実行時に作成できます。  
  
> [!NOTE]
>  **OleDbConnection** オブジェクトは、OLE DB プロバイダー固有の動的プロパティの設定または取得をサポートしていません。  OLE DB プロバイダーに接続文字列で渡すことができるプロパティだけがサポートされています。  
  
 OLE DB データ ソースへの接続を作成し確立する方法を次のサンプル コードに示します。  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OleDbConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OleDbConnection connection =   
  new OleDbConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## Universal Data Link ファイルは使用しない  
 **OleDbConnection** の接続情報は、UDL \(Universal Data Link\) ファイルを使用して提供できますが、このファイルは使用しないでください。  UDL ファイルは暗号化されないため、接続文字列をテキスト形式で表現してしまいます。  UDL ファイルは、アプリケーションにとって外部ファイルをベースにしたリソースであるため、.NET Framework でセキュリティ保護できません。  
  
## ODBC データ ソースへの接続  
 .NET Framework Data Provider for ODBC は、**OdbcConnection** オブジェクトを通じて、ODBC によって公開されているデータ ソースへの接続を提供します。  
  
 .NET Framework Data Provider for ODBC で使用される接続文字列フォーマットは、できるだけ ODBC の接続文字列フォーマットと一致するようにデザインされています。  ODBC データ ソース名 \(DSN\) を指定することもできます。  **OdbcConnection** の詳細については、「[OdbcConnection クラス](frlrfSystemDataOdbcOdbcConnectionClassTopic)」を参照してください。  
  
 ODBC データ ソースへの接続を作成し確立する方法を次のサンプル コードに示します。  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OdbcConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OdbcConnection connection =   
  new OdbcConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
```  
  
## Oracle データ ソースへの接続  
 .NET Framework Data Provider for Oracle は、**OracleConnection** オブジェクトを通じて、Oracle データ ソースへの接続を提供します。  
  
 .NET Framework Data Provider for Oracle で使用される接続文字列フォーマットは、できるだけ MSDAORA \(OLE DB Provider for Oracle\) の接続文字列フォーマットと一致するようにデザインされています。  **OracleConnection** の詳細については、「[OracleConnection クラス](frlrfSystemDataOracleClientOracleConnectionClassTopic)」を参照してください。  
  
 Oracle データ ソースへの接続を作成し確立する方法を次のサンプル コードに示します。  
  
```vb  
' Assumes connectionString is a valid connection string.  
Using connection As New OracleConnection(connectionString)  
    connection.Open()  
    ' Do work here.  
End Using  
  
```  
  
```csharp  
// Assumes connectionString is a valid connection string.  
using (OracleConnection connection =   
  new OracleConnection(connectionString))  
{  
    connection.Open();  
    // Do work here.  
}  
OracleConnection nwindConn = new OracleConnection("Data Source=MyOracleServer;Integrated Security=yes;");  
nwindConn.Open();  
```  
  
## 参照  
 [データ ソースへの接続](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)   
 [接続文字列](../../../../docs/framework/data/adonet/connection-strings.md)   
 [OLE DB、ODBC、および Oracle 接続プール](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)