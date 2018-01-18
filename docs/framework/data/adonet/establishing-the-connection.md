---
title: "接続の確立"
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
ms.assetid: 3af512f3-87d9-4005-9e2f-abb1060ff43f
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5fa47254f97d48dccd13644e2547eaac4ca787bd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="establishing-the-connection"></a><span data-ttu-id="06ea6-102">接続の確立</span><span class="sxs-lookup"><span data-stu-id="06ea6-102">Establishing the Connection</span></span>
<span data-ttu-id="06ea6-103">Microsoft SQL Server に接続する場合は、.NET Framework Data Provider for SQL Server の <xref:System.Data.SqlClient.SqlConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="06ea6-103">To connect to Microsoft SQL Server, use the <xref:System.Data.SqlClient.SqlConnection> object of the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="06ea6-104">OLE DB データ ソースに接続する場合は、.NET Framework Data Provider for OLE DB の <xref:System.Data.OleDb.OleDbConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="06ea6-104">To connect to an OLE DB data source, use the <xref:System.Data.OleDb.OleDbConnection> object of the .NET Framework Data Provider for OLE DB.</span></span> <span data-ttu-id="06ea6-105">ODBC データ ソースに接続する場合は、.NET Framework Data Provider for ODBC の <xref:System.Data.Odbc.OdbcConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="06ea6-105">To connect to an ODBC data source, use the <xref:System.Data.Odbc.OdbcConnection> object of the .NET Framework Data Provider for ODBC.</span></span> <span data-ttu-id="06ea6-106">Oracle データ ソースに接続する場合は、.NET Framework Data Provider for Oracle の <xref:System.Data.OracleClient.OracleConnection> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="06ea6-106">To connect to an Oracle data source, use the <xref:System.Data.OracleClient.OracleConnection> object of the .NET Framework Data Provider for Oracle.</span></span> <span data-ttu-id="06ea6-107">安全に保管すると、接続文字列を取得する、次を参照してください。[接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-107">For securely storing and retrieving connection strings, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="closing-connections"></a><span data-ttu-id="06ea6-108">接続の終了</span><span class="sxs-lookup"><span data-stu-id="06ea6-108">Closing Connections</span></span>  
 <span data-ttu-id="06ea6-109">接続がプールに返されるようにするために、接続を使い終えたら必ず接続を終了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="06ea6-109">We recommend that you always close the connection when you are finished using it, so that the connection can be returned to the pool.</span></span> <span data-ttu-id="06ea6-110">Visual Basic または C# の `Using` ブロックは、コードがこのブロックを終了したときに接続を破棄します。これは、未処理の例外の場合でも実行されます。</span><span class="sxs-lookup"><span data-stu-id="06ea6-110">The `Using` block in Visual Basic or C# automatically disposes of the connection when the code exits the block, even in the case of an unhandled exception.</span></span> <span data-ttu-id="06ea6-111">参照してください[ステートメントを使用して](~/docs/csharp/language-reference/keywords/using-statement.md)と[Using ステートメント](~/docs/visual-basic/language-reference/statements/using-statement.md)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="06ea6-111">See [using Statement](~/docs/csharp/language-reference/keywords/using-statement.md) and [Using Statement](~/docs/visual-basic/language-reference/statements/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="06ea6-112">また、使用しているプロバイダーの接続オブジェクトの `Close` または `Dispose` メソッドを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="06ea6-112">You can also use the `Close` or `Dispose` methods of the connection object for the provider that you are using.</span></span> <span data-ttu-id="06ea6-113">明示的に終了されていない接続は、プールに追加したり返したりすることができないことがあります。</span><span class="sxs-lookup"><span data-stu-id="06ea6-113">Connections that are not explicitly closed might not be added or returned to the pool.</span></span> <span data-ttu-id="06ea6-114">たとえば、スコープ外に出ても、明示的に終了されていない接続は、最大プール サイズに達した時点でその接続がまだ有効である場合にだけ接続プールに返されます。</span><span class="sxs-lookup"><span data-stu-id="06ea6-114">For example, a connection that has gone out of scope but that has not been explicitly closed will only be returned to the connection pool if the maximum pool size has been reached and the connection is still valid.</span></span> <span data-ttu-id="06ea6-115">詳細については、次を参照してください。 [OLE DB、ODBC、および Oracle 接続プール](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-115">For more information, see [OLE DB, ODBC, and Oracle Connection Pooling](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06ea6-116">呼び出す必要はありません`Close`または`Dispose`上、**接続**、 **DataReader**、またはその他のマネージ オブジェクトで、`Finalize`クラスのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="06ea6-116">Do not call `Close` or `Dispose` on a **Connection**, a **DataReader**, or any other managed object in the `Finalize` method of your class.</span></span> <span data-ttu-id="06ea6-117">終了処理では、クラスに直接所有されているアンマネージ リソースだけを解放してください。</span><span class="sxs-lookup"><span data-stu-id="06ea6-117">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="06ea6-118">クラスがアンマネージ リソースを所有していない場合は、クラス定義に `Finalize` メソッドを含めないでください。</span><span class="sxs-lookup"><span data-stu-id="06ea6-118">If your class does not own any unmanaged resources, do not include a `Finalize` method in your class definition.</span></span> <span data-ttu-id="06ea6-119">詳細については、次を参照してください。[ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-119">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06ea6-120">接続が接続プールからフェッチされたり接続プールに返されたりしたとき、ログイン イベントとログアウト イベントはサーバーで発生しません。これは、接続プールに返されても接続は実際には終了していないためです。</span><span class="sxs-lookup"><span data-stu-id="06ea6-120">Login and logout events will not be raised on the server when a connection is fetched from or returned to the connection pool, because the connection is not actually closed when it is returned to the connection pool.</span></span> <span data-ttu-id="06ea6-121">詳細については、次を参照してください。 [SQL サーバー接続プール (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-121">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
## <a name="connecting-to-sql-server"></a><span data-ttu-id="06ea6-122">SQL Server への接続</span><span class="sxs-lookup"><span data-stu-id="06ea6-122">Connecting to SQL Server</span></span>  
 <span data-ttu-id="06ea6-123">.NET Framework Data Provider for SQL Server は、OLE DB (ADO) 接続文字列フォーマットに似た接続文字列フォーマットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="06ea6-123">The .NET Framework Data Provider for SQL Server supports a connection string format that is similar to the OLE DB (ADO) connection string format.</span></span> <span data-ttu-id="06ea6-124">有効な文字列フォーマットの名前および値については、<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> プロパティを参照してください。</span><span class="sxs-lookup"><span data-stu-id="06ea6-124">For valid string format names and values, see the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="06ea6-125">また、<xref:System.Data.SqlClient.SqlConnectionStringBuilder> クラスを使用すると、構文的に正しい接続文字列を実行時に作成できます。</span><span class="sxs-lookup"><span data-stu-id="06ea6-125">You can also use the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> class to create syntactically valid connection strings at run time.</span></span> <span data-ttu-id="06ea6-126">詳細については、次を参照してください。[接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-126">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  
  
 <span data-ttu-id="06ea6-127">SQL Server のデータベースへの接続を開いて確立する方法を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="06ea6-127">The following code example demonstrates how to create and open a connection to a SQL Server database.</span></span>  
  
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
  
### <a name="integrated-security-and-aspnet"></a><span data-ttu-id="06ea6-128">統合セキュリティと ASP.NET</span><span class="sxs-lookup"><span data-stu-id="06ea6-128">Integrated Security and ASP.NET</span></span>  
 <span data-ttu-id="06ea6-129">SQL Server 統合セキュリティ (信頼関係接続とも呼ばれます) は、SQL Server への接続を保護します。接続文字列でユーザー ID とパスワードを公開することがなく、接続の認証用に推奨されている方法でもあるためです。</span><span class="sxs-lookup"><span data-stu-id="06ea6-129">SQL Server integrated security (also known as trusted connections) helps to provide protection when connecting to SQL Server as it does not expose a user ID and password in the connection string and is the recommended method for authenticating a connection.</span></span> <span data-ttu-id="06ea6-130">統合セキュリティでは、実行中のプロセスの現在のセキュリティ ID またはトークンを使用します。</span><span class="sxs-lookup"><span data-stu-id="06ea6-130">Integrated security uses the current security identity, or token, of the executing process.</span></span> <span data-ttu-id="06ea6-131">これは、デスクトップ アプリケーションでは通常、現在ログオンしているユーザーの ID です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-131">For desktop applications, this is typically the identity of the currently logged-on user.</span></span>  
  
 <span data-ttu-id="06ea6-132">ASP.NET アプリケーションのセキュリティ ID は、他のオプションのうちのいずれかに設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="06ea6-132">The security identity for ASP.NET applications can be set to one of several different options.</span></span> <span data-ttu-id="06ea6-133">ASP.NET アプリケーションが SQL Server に接続するときに使用するセキュリティ id をより深く理解するを参照してください[ASP.NET の偽装](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d)、 [ASP.NET 認証](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)、および[する方法: アクセス SQL。Windows を使用してサーバーの統合セキュリティ](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5)です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-133">To better understand the security identity that an ASP.NET application uses when connecting to SQL Server, see [ASP.NET Impersonation](http://msdn.microsoft.com/library/a0cb3024-562f-4184-9d3c-095504787d3d), [ASP.NET Authentication](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1), and [How to: Access SQL Server Using Windows Integrated Security](http://msdn.microsoft.com/library/683f9c9f-4375-4de6-8111-943c4423fde5).</span></span>  
  
## <a name="connecting-to-an-ole-db-data-source"></a><span data-ttu-id="06ea6-134">OLE DB データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="06ea6-134">Connecting to an OLE DB Data Source</span></span>  
 <span data-ttu-id="06ea6-135">OLE DB (SQLOLEDB、OLE DB Provider for SQL Server) 経由で公開されているデータ ソースへの接続を提供する .NET Framework Data Provider for OLE DB を使用して、 **OleDbConnection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="06ea6-135">The .NET Framework Data Provider for OLE DB provides connectivity to data sources exposed using OLE DB (through SQLOLEDB, the OLE DB Provider for SQL Server), using the **OleDbConnection** object.</span></span>  
  
 <span data-ttu-id="06ea6-136">.NET Framework Data Provider for OLE DB で使用される接続文字列フォーマットは ADO で使用される接続文字列フォーマットと同じですが、次の例外があります。</span><span class="sxs-lookup"><span data-stu-id="06ea6-136">For the .NET Framework Data Provider for OLE DB, the connection string format is identical to the connection string format used in ADO, with the following exceptions:</span></span>  
  
-   <span data-ttu-id="06ea6-137">**プロバイダー**キーワードが必要です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-137">The **Provider** keyword is required.</span></span>  
  
-   <span data-ttu-id="06ea6-138">**URL**、**リモート プロバイダー**、および**リモート サーバー**キーワードがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="06ea6-138">The **URL**, **Remote Provider**, and **Remote Server** keywords are not supported.</span></span>  
  
 <span data-ttu-id="06ea6-139">OLE DB 接続文字列の詳細については、「<xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06ea6-139">For more information about OLE DB connection strings, see the <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> topic.</span></span> <span data-ttu-id="06ea6-140">また、<xref:System.Data.OleDb.OleDbConnectionStringBuilder> を使用すると、接続文字列を実行時に作成できます。</span><span class="sxs-lookup"><span data-stu-id="06ea6-140">You can also use the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> to create connection strings at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06ea6-141">**OleDbConnection**オブジェクトは設定または OLE DB プロバイダーに固有の動的プロパティの取得をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="06ea6-141">The **OleDbConnection** object does not support setting or retrieving dynamic properties specific to an OLE DB provider.</span></span> <span data-ttu-id="06ea6-142">OLE DB プロバイダーに接続文字列で渡すことができるプロパティだけがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="06ea6-142">Only properties that can be passed in the connection string for the OLE DB provider are supported.</span></span>  
  
 <span data-ttu-id="06ea6-143">OLE DB データ ソースへの接続を作成し確立する方法を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="06ea6-143">The following code example demonstrates how to create and open a connection to an OLE DB data source.</span></span>  
  
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
  
## <a name="do-not-use-universal-data-link-files"></a><span data-ttu-id="06ea6-144">Universal Data Link ファイルは使用しない</span><span class="sxs-lookup"><span data-stu-id="06ea6-144">Do Not Use Universal Data Link Files</span></span>  
 <span data-ttu-id="06ea6-145">接続情報を指定することは、 **OleDbConnection** Universal Data Link (UDL) ファイルです。 ただししないでそうです。</span><span class="sxs-lookup"><span data-stu-id="06ea6-145">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="06ea6-146">UDL ファイルは暗号化されないため、接続文字列をテキスト形式で表現してしまいます。</span><span class="sxs-lookup"><span data-stu-id="06ea6-146">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="06ea6-147">UDL ファイルは、アプリケーションにとって外部ファイルをベースにしたリソースであるため、.NET Framework でセキュリティ保護できません。</span><span class="sxs-lookup"><span data-stu-id="06ea6-147">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span>  
  
## <a name="connecting-to-an-odbc-data-source"></a><span data-ttu-id="06ea6-148">ODBC データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="06ea6-148">Connecting to an ODBC Data Source</span></span>  
 <span data-ttu-id="06ea6-149">.NET Framework Data Provider for ODBC は ODBC を使用して公開されるデータ ソースへの接続を提供、 **OdbcConnection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="06ea6-149">The .NET Framework Data Provider for ODBC provides connectivity to data sources exposed using ODBC using the **OdbcConnection** object.</span></span>  
  
 <span data-ttu-id="06ea6-150">.NET Framework Data Provider for ODBC で使用される接続文字列フォーマットは、できるだけ ODBC の接続文字列フォーマットと一致するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="06ea6-150">For the .NET Framework Data Provider for ODBC, the connection string format is designed to match the ODBC connection string format as closely as possible.</span></span> <span data-ttu-id="06ea6-151">ODBC データ ソース名 (DSN) を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="06ea6-151">You may also supply an ODBC data source name (DSN).</span></span> <span data-ttu-id="06ea6-152">詳細については、 **OdbcConnection**を参照してください、<xref:System.Data.Odbc.OdbcConnection>です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-152">For more detail on the **OdbcConnection** , see the <xref:System.Data.Odbc.OdbcConnection>.</span></span>  
  
 <span data-ttu-id="06ea6-153">ODBC データ ソースへの接続を作成し確立する方法を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="06ea6-153">The following code example demonstrates how to create and open a connection to an ODBC data source.</span></span>  
  
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
  
## <a name="connecting-to-an-oracle-data-source"></a><span data-ttu-id="06ea6-154">Oracle データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="06ea6-154">Connecting to an Oracle Data Source</span></span>  
 <span data-ttu-id="06ea6-155">.NET Framework Data Provider for Oracle を使用して Oracle データ ソースへの接続を提供する、 **OracleConnection**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="06ea6-155">The .NET Framework Data Provider for Oracle provides connectivity to Oracle data sources using the **OracleConnection** object.</span></span>  
  
 <span data-ttu-id="06ea6-156">.NET Framework Data Provider for Oracle で使用される接続文字列フォーマットは、できるだけ MSDAORA (OLE DB Provider for Oracle) の接続文字列フォーマットと一致するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="06ea6-156">For the .NET Framework Data Provider for Oracle, the connection string format is designed to match the OLE DB Provider for Oracle (MSDAORA) connection string format as closely as possible.</span></span> <span data-ttu-id="06ea6-157">詳細については、 **OracleConnection**を参照してください、<xref:System.Data.OracleClient.OracleConnection>です。</span><span class="sxs-lookup"><span data-stu-id="06ea6-157">For more detail on the **OracleConnection**, see the <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
 <span data-ttu-id="06ea6-158">Oracle データ ソースへの接続を作成し確立する方法を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="06ea6-158">The following code example demonstrates how to create and open a connection to an Oracle data source.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06ea6-159">参照</span><span class="sxs-lookup"><span data-stu-id="06ea6-159">See Also</span></span>  
 [<span data-ttu-id="06ea6-160">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="06ea6-160">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="06ea6-161">接続文字列</span><span class="sxs-lookup"><span data-stu-id="06ea6-161">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="06ea6-162">OLE DB、ODBC、および Oracle 接続プール</span><span class="sxs-lookup"><span data-stu-id="06ea6-162">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [<span data-ttu-id="06ea6-163">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="06ea6-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
