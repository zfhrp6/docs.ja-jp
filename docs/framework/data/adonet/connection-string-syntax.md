---
title: 接続文字列の構文
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
caps.latest.revision: 11
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3939abaf376100e09d244afdb32662729a990ff7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="connection-string-syntax"></a><span data-ttu-id="24674-102">接続文字列の構文</span><span class="sxs-lookup"><span data-stu-id="24674-102">Connection String Syntax</span></span>
<span data-ttu-id="24674-103">すべての .NET Framework データ プロバイダーは、`Connection` を継承する <xref:System.Data.Common.DbConnection> オブジェクトに加え、プロバイダー固有の <xref:System.Data.Common.DbConnection.ConnectionString%2A> プロパティを持ちます。</span><span class="sxs-lookup"><span data-stu-id="24674-103">Each .NET Framework data provider has a `Connection` object that inherits from <xref:System.Data.Common.DbConnection> as well as a provider-specific <xref:System.Data.Common.DbConnection.ConnectionString%2A> property.</span></span> <span data-ttu-id="24674-104">それぞれのプロバイダーに固有の接続文字列の構文は、対応する `ConnectionString` プロパティのトピックで説明されています。</span><span class="sxs-lookup"><span data-stu-id="24674-104">The specific connection string syntax for each provider is documented in its `ConnectionString` property.</span></span> <span data-ttu-id="24674-105">次の表は、.NET Framework に含まれている 4 つのデータ プロバイダーを一覧にしたものです。</span><span class="sxs-lookup"><span data-stu-id="24674-105">The following table lists the four data providers that are included in the .NET Framework.</span></span>  
  
|<span data-ttu-id="24674-106">.NET Framework データ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="24674-106">.NET Framework data provider</span></span>|<span data-ttu-id="24674-107">説明</span><span class="sxs-lookup"><span data-stu-id="24674-107">Description</span></span>|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|<span data-ttu-id="24674-108">Microsoft SQL Server へのデータ アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="24674-108">Provides data access for Microsoft SQL Server.</span></span> <span data-ttu-id="24674-109">接続文字列の構文の詳細については、「<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24674-109">For more information on connection string syntax, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OleDb>|<span data-ttu-id="24674-110">OLE DB を使って公開されたデータ ソースへのデータ アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="24674-110">Provides data access for data sources exposed using OLE DB.</span></span> <span data-ttu-id="24674-111">接続文字列の構文の詳細については、「<xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24674-111">For more information on connection string syntax, see <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.Odbc>|<span data-ttu-id="24674-112">ODBC を使って公開されたデータ ソースへのデータ アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="24674-112">Provides data access for data sources exposed using ODBC.</span></span> <span data-ttu-id="24674-113">接続文字列の構文の詳細については、「<xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24674-113">For more information on connection string syntax, see <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>.</span></span>|  
|<xref:System.Data.OracleClient>|<span data-ttu-id="24674-114">Oracle バージョン 8.1.7 以降へのデータ アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="24674-114">Provides data access for Oracle version 8.1.7 or later.</span></span> <span data-ttu-id="24674-115">接続文字列の構文の詳細については、「<xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24674-115">For more information on connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>|  
  
## <a name="connection-string-builders"></a><span data-ttu-id="24674-116">接続文字列ビルダー</span><span class="sxs-lookup"><span data-stu-id="24674-116">Connection String Builders</span></span>  
 <span data-ttu-id="24674-117">ADO.NET 2.0 では、.NET Framework データ プロバイダー用の次の接続文字列ビルダーが導入されました。</span><span class="sxs-lookup"><span data-stu-id="24674-117">ADO.NET 2.0 introduced the following connection string builders for the .NET Framework data providers.</span></span>  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 <span data-ttu-id="24674-118">接続文字列ビルダーを使用すると、構文的に正しい接続文字列を実行時に構築できるため、コード内で接続文字列値を手動で連結する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="24674-118">The connection string builders allow you to construct syntactically valid connection strings at run time, so you do not have to manually concatenate connection string values in your code.</span></span> <span data-ttu-id="24674-119">詳細については、次を参照してください。[接続文字列ビルダー](../../../../docs/framework/data/adonet/connection-string-builders.md)です。</span><span class="sxs-lookup"><span data-stu-id="24674-119">For more information, see [Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md).</span></span>  

## <a name="windows-authentication"></a><span data-ttu-id="24674-120">Windows 認証</span><span class="sxs-lookup"><span data-stu-id="24674-120">Windows Authentication</span></span>  
 <span data-ttu-id="24674-121">Windows 認証を使用することをお勧め (とも呼ば*統合セキュリティ*) サポートされているデータ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="24674-121">We recommend using Windows Authentication (sometimes referred to as *integrated security*) to connect to data sources that support it.</span></span> <span data-ttu-id="24674-122">接続文字列の構文は、プロバイダーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="24674-122">The syntax employed in the connection string varies by provider.</span></span> <span data-ttu-id="24674-123">.NET Framework データ プロバイダーで使用されている Windows 認証の構文を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="24674-123">The following table shows the Windows Authentication syntax used with the .NET Framework data providers.</span></span>  
  
|<span data-ttu-id="24674-124">プロバイダー</span><span class="sxs-lookup"><span data-stu-id="24674-124">Provider</span></span>|<span data-ttu-id="24674-125">構文</span><span class="sxs-lookup"><span data-stu-id="24674-125">Syntax</span></span>|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  <span data-ttu-id="24674-126">`Integrated Security=true` プロバイダーで `OleDb` に設定すると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="24674-126">`Integrated Security=true` throws an exception when used with the `OleDb` provider.</span></span>  
  
## <a name="sqlclient-connection-strings"></a><span data-ttu-id="24674-127">SqlClient 接続文字列</span><span class="sxs-lookup"><span data-stu-id="24674-127">SqlClient Connection Strings</span></span>  
<span data-ttu-id="24674-128"><xref:System.Data.SqlClient.SqlConnection> 接続文字列の構文については、<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> プロパティで説明されています。</span><span class="sxs-lookup"><span data-stu-id="24674-128">The syntax for a <xref:System.Data.SqlClient.SqlConnection> connection string is documented in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="24674-129"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> プロパティを使用すると、SQL Server データベースの接続文字列を取得または設定することができます。</span><span class="sxs-lookup"><span data-stu-id="24674-129">You can use the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property to get or set a connection string for a SQL Server database.</span></span> <span data-ttu-id="24674-130">以前のバージョンの SQL Server に接続する必要がある場合は、.NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24674-130">If you need to connect to an earlier version of SQL Server, you must use the .NET Framework Data Provider for OleDb (<xref:System.Data.OleDb>).</span></span> <span data-ttu-id="24674-131">接続文字列のほとんどのキーワードは、<xref:System.Data.SqlClient.SqlConnectionStringBuilder> のプロパティにマップされています。</span><span class="sxs-lookup"><span data-stu-id="24674-131">Most connection string keywords also map to properties in the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="24674-132">既定の設定、`Persist Security Info`キーワードは`false`します。</span><span class="sxs-lookup"><span data-stu-id="24674-132">The default setting for the `Persist Security Info` keyword is `false`.</span></span> <span data-ttu-id="24674-133">このキーワードを `true` または `yes` に設定すると、ユーザー ID やパスワードなどのセキュリティ関連情報を、接続を開いた後にその接続から取得できます。</span><span class="sxs-lookup"><span data-stu-id="24674-133">Setting it to `true` or `yes` allows security-sensitive information, including the user ID and password, to be obtained from the connection after the connection has been opened.</span></span> <span data-ttu-id="24674-134">保持`Persist Security Info`'éý'`false`を信頼できないソースに機密を要する接続文字列情報へのアクセスがないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="24674-134">Keep `Persist Security Info` set to `false` to ensure that an untrusted source does not have access to sensitive connection string information.</span></span>  

### <a name="windows-authentication-with-sqlclient"></a><span data-ttu-id="24674-135">SqlClient で Windows 認証</span><span class="sxs-lookup"><span data-stu-id="24674-135">Windows authentication with SqlClient</span></span> 
 <span data-ttu-id="24674-136">接続に Windows 認証を使用して次の形式の構文の各、 **AdventureWorks**ローカル サーバー上のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="24674-136">Each of the following forms of syntax uses Windows Authentication to connect to the **AdventureWorks** database on a local server.</span></span>  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a><span data-ttu-id="24674-137">SqlClient で SQL Server 認証</span><span class="sxs-lookup"><span data-stu-id="24674-137">SQL Server authentication with SqlClient</span></span>   
 <span data-ttu-id="24674-138">SQL Server への接続には Windows 認証の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="24674-138">Windows Authentication is preferred for connecting to SQL Server.</span></span> <span data-ttu-id="24674-139">ただし、どうしても SQL Server 認証を使用する必要がある場合は、次の構文に従ってユーザー名とパスワードを指定してください。</span><span class="sxs-lookup"><span data-stu-id="24674-139">However, if SQL Server Authentication is required, use the following syntax to specify a user name and password.</span></span> <span data-ttu-id="24674-140">この例では、アスタリスクを使用して有効なユーザー名とパスワードを表しています。</span><span class="sxs-lookup"><span data-stu-id="24674-140">In this example, asterisks are used to represent a valid user name and password.</span></span>  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

<span data-ttu-id="24674-141">Azure SQL Database または Azure SQL Data Warehouse に接続し、形式のログインを提供するときに`user@servername`、ことを確認して、`servername`ログインの値に指定された値が一致する`Server=`です。</span><span class="sxs-lookup"><span data-stu-id="24674-141">When you connect to Azure SQL Database or to Azure SQL Data Warehouse and provide a login in the format `user@servername`, make sure that the `servername` value in the login matches the value provided for `Server=`.</span></span>

> [!NOTE]
>  <span data-ttu-id="24674-142">Windows 認証は SQL Server ログインよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="24674-142">Windows authentication takes precedence over SQL Server logins.</span></span> <span data-ttu-id="24674-143">Integrated Security を true に指定し、ユーザー名とパスワードも指定した場合、ユーザー名とパスワードは無視され、Windows 認証が使用されます。</span><span class="sxs-lookup"><span data-stu-id="24674-143">If you specify both Integrated Security=true as well as a user name and password, the user name and password will be ignored and Windows authentication will be used.</span></span>  

### <a name="connect-to-a-named-instance-of-sql-server"></a><span data-ttu-id="24674-144">SQL Server の名前付きインスタンスへの接続します。</span><span class="sxs-lookup"><span data-stu-id="24674-144">Connect to a named instance of SQL Server</span></span>
<span data-ttu-id="24674-145">SQL Server の名前付きインスタンスに接続するには、使用、*サーバー名 \ インスタンス名*構文です。</span><span class="sxs-lookup"><span data-stu-id="24674-145">To connect to a named instance of SQL Server, use the *server name\instance name* syntax.</span></span>  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
<span data-ttu-id="24674-146">接続文字列の作成時に、<xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> の `SqlConnectionStringBuilder` プロパティをインスタンス名に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="24674-146">You can also set the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> property of the `SqlConnectionStringBuilder` to the instance name when building a connection string.</span></span> <span data-ttu-id="24674-147"><xref:System.Data.SqlClient.SqlConnection.DataSource%2A> オブジェクトの <xref:System.Data.SqlClient.SqlConnection> プロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="24674-147">The <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object is read-only.</span></span>  
  
### <a name="type-system-version-changes"></a><span data-ttu-id="24674-148">Type System Version の変更</span><span class="sxs-lookup"><span data-stu-id="24674-148">Type System Version Changes</span></span>  
 <span data-ttu-id="24674-149">`Type System Version`キーワード、 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> SQL サーバーの種類のクライアント側表現を指定します。</span><span class="sxs-lookup"><span data-stu-id="24674-149">The `Type System Version` keyword in a <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> specifies the client-side representation of SQL Server types.</span></span> <span data-ttu-id="24674-150"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> キーワードの詳細については、`Type System Version` のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="24674-150">See <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> for more information about the `Type System Version` keyword.</span></span>  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a><span data-ttu-id="24674-151">SQL Server Express ユーザー インスタンスへの接続とアタッチ</span><span class="sxs-lookup"><span data-stu-id="24674-151">Connecting and Attaching to SQL Server Express User Instances</span></span>  
 <span data-ttu-id="24674-152">ユーザー インスタンスは、SQL Server Express の機能の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="24674-152">User instances are a feature in SQL Server Express.</span></span> <span data-ttu-id="24674-153">最小限の特権しか持たないローカル Windows アカウントで実行しているユーザーが、SQL Server データベースにアタッチできます。この場合、管理特権は不要です。</span><span class="sxs-lookup"><span data-stu-id="24674-153">They allow a user running on a least-privileged local Windows account to attach and run a SQL Server database without requiring administrative privileges.</span></span> <span data-ttu-id="24674-154">ユーザー インスタンスは、サービスとしてではなく、ユーザーの Windows 資格情報で実行されます。</span><span class="sxs-lookup"><span data-stu-id="24674-154">A user instance executes with the user's Windows credentials, not as a service.</span></span>  
  
 <span data-ttu-id="24674-155">ユーザー インスタンスの操作の詳細については、次を参照してください。 [SQL Server Express ユーザー インスタンス](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)です。</span><span class="sxs-lookup"><span data-stu-id="24674-155">For more information on working with user instances, see [SQL Server Express User Instances](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md).</span></span>  
  
## <a name="using-trustservercertificate"></a><span data-ttu-id="24674-156">TrustServerCertificate の使用</span><span class="sxs-lookup"><span data-stu-id="24674-156">Using TrustServerCertificate</span></span>  
 <span data-ttu-id="24674-157">`TrustServerCertificate`キーワードは、有効な証明書を持つ SQL Server インスタンスに接続するときにのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="24674-157">The `TrustServerCertificate` keyword is valid only when connecting to a SQL Server instance with a valid certificate.</span></span> <span data-ttu-id="24674-158">`TrustServerCertificate` を `true` に設定した場合、トランスポート層に SSL が使用されてチャネルが暗号化されます。また、証明書チェーンをたどることによる信頼性の検証は省略されます。</span><span class="sxs-lookup"><span data-stu-id="24674-158">When `TrustServerCertificate` is set to `true`, the transport layer will use SSL to encrypt the channel and bypass walking the certificate chain to validate trust.</span></span>  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  <span data-ttu-id="24674-159">`TrustServerCertificate` を `true` に設定して暗号化を有効にした場合、接続文字列で `Encrypt` を `false` に設定したとしても、サーバーで指定された暗号化レベルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="24674-159">If `TrustServerCertificate` is set to `true` and encryption is turned on, the encryption level specified on the server will be used even if `Encrypt` is set to `false` in the connection string.</span></span> <span data-ttu-id="24674-160">それ以外の場合、接続は失敗します。</span><span class="sxs-lookup"><span data-stu-id="24674-160">The connection will fail otherwise.</span></span>  
  
### <a name="enabling-encryption"></a><span data-ttu-id="24674-161">暗号化の有効化</span><span class="sxs-lookup"><span data-stu-id="24674-161">Enabling Encryption</span></span>  
 <span data-ttu-id="24674-162">サーバーで、証明書がプロビジョニングされていない場合は、暗号化を有効にする、 **Force Protocol Encryption**と**Trust Server Certificate**オプションは、SQL Server 構成マネージャーで設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24674-162">To enable encryption when a certificate has not been provisioned on the server, the **Force Protocol Encryption** and the **Trust Server Certificate** options must be set in SQL Server Configuration Manager.</span></span> <span data-ttu-id="24674-163">このように、検証可能なサーバー証明書がプロビジョニングされていない場合、暗号化には検証を伴わない自己署名入りのサーバー証明書が使用されます。</span><span class="sxs-lookup"><span data-stu-id="24674-163">In this case, encryption will use a self-signed server certificate without validation if no verifiable certificate has been provisioned on the server.</span></span>  
  
 <span data-ttu-id="24674-164">SQL Server で構成されたセキュリティのレベルを、アプリケーションの設定によって緩和することはできません。ただし、必要に応じて厳密にすることはできます。</span><span class="sxs-lookup"><span data-stu-id="24674-164">Application settings cannot reduce the level of security configured in SQL Server, but can optionally strengthen it.</span></span> <span data-ttu-id="24674-165">アプリケーションが要求する暗号化を設定して、`TrustServerCertificate`と`Encrypt`キーワード`true`、確実に暗号化行われるサーバーの証明書がプロビジョニングされていない場合でもと**プロトコルの暗号化**クライアントが構成されていません。</span><span class="sxs-lookup"><span data-stu-id="24674-165">An application can request encryption by setting the `TrustServerCertificate` and `Encrypt` keywords to `true`, guaranteeing that encryption takes place even when a server certificate has not been provisioned and **Force Protocol Encryption** has not been configured for the client.</span></span> <span data-ttu-id="24674-166">ただし、クライアントの構成で `TrustServerCertificate` を有効にしなかった場合は、プロビジョニングされたサーバー証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="24674-166">However, if `TrustServerCertificate` is not enabled in the client configuration, a provisioned server certificate is still required.</span></span>  
  
 <span data-ttu-id="24674-167">次の表ですべてのケースを説明します。</span><span class="sxs-lookup"><span data-stu-id="24674-167">The following table describes all cases.</span></span>  
  
|<span data-ttu-id="24674-168">[プロトコルの暗号化を設定する] クライアント設定</span><span class="sxs-lookup"><span data-stu-id="24674-168">Force Protocol Encryption client setting</span></span>|<span data-ttu-id="24674-169">[サーバー証明書を信頼する] クライアント設定</span><span class="sxs-lookup"><span data-stu-id="24674-169">Trust Server Certificate client setting</span></span>|<span data-ttu-id="24674-170">Encrypt/Use Encryption for Data 接続文字列/属性</span><span class="sxs-lookup"><span data-stu-id="24674-170">Encrypt/Use Encryption for Data connection string/attribute</span></span>|<span data-ttu-id="24674-171">Trust Server Certificate 接続文字列/属性</span><span class="sxs-lookup"><span data-stu-id="24674-171">Trust Server Certificate connection string/attribute</span></span>|<span data-ttu-id="24674-172">結果</span><span class="sxs-lookup"><span data-stu-id="24674-172">Result</span></span>|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|<span data-ttu-id="24674-173">Ｘ</span><span class="sxs-lookup"><span data-stu-id="24674-173">No</span></span>|<span data-ttu-id="24674-174">N/A</span><span class="sxs-lookup"><span data-stu-id="24674-174">N/A</span></span>|<span data-ttu-id="24674-175">無効 (既定値)</span><span class="sxs-lookup"><span data-stu-id="24674-175">No (default)</span></span>|<span data-ttu-id="24674-176">無視</span><span class="sxs-lookup"><span data-stu-id="24674-176">Ignored</span></span>|<span data-ttu-id="24674-177">暗号化は行われません。</span><span class="sxs-lookup"><span data-stu-id="24674-177">No encryption occurs.</span></span>|  
|<span data-ttu-id="24674-178">Ｘ</span><span class="sxs-lookup"><span data-stu-id="24674-178">No</span></span>|<span data-ttu-id="24674-179">N/A</span><span class="sxs-lookup"><span data-stu-id="24674-179">N/A</span></span>|<span data-ttu-id="24674-180">はい</span><span class="sxs-lookup"><span data-stu-id="24674-180">Yes</span></span>|<span data-ttu-id="24674-181">無効 (既定値)</span><span class="sxs-lookup"><span data-stu-id="24674-181">No (default)</span></span>|<span data-ttu-id="24674-182">暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。</span><span class="sxs-lookup"><span data-stu-id="24674-182">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="24674-183">Ｘ</span><span class="sxs-lookup"><span data-stu-id="24674-183">No</span></span>|<span data-ttu-id="24674-184">N/A</span><span class="sxs-lookup"><span data-stu-id="24674-184">N/A</span></span>|<span data-ttu-id="24674-185">はい</span><span class="sxs-lookup"><span data-stu-id="24674-185">Yes</span></span>|<span data-ttu-id="24674-186">はい</span><span class="sxs-lookup"><span data-stu-id="24674-186">Yes</span></span>|<span data-ttu-id="24674-187">暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。</span><span class="sxs-lookup"><span data-stu-id="24674-187">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="24674-188">はい</span><span class="sxs-lookup"><span data-stu-id="24674-188">Yes</span></span>|<span data-ttu-id="24674-189">Ｘ</span><span class="sxs-lookup"><span data-stu-id="24674-189">No</span></span>|<span data-ttu-id="24674-190">無視</span><span class="sxs-lookup"><span data-stu-id="24674-190">Ignored</span></span>|<span data-ttu-id="24674-191">無視</span><span class="sxs-lookup"><span data-stu-id="24674-191">Ignored</span></span>|<span data-ttu-id="24674-192">暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。</span><span class="sxs-lookup"><span data-stu-id="24674-192">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="24674-193">はい</span><span class="sxs-lookup"><span data-stu-id="24674-193">Yes</span></span>|<span data-ttu-id="24674-194">はい</span><span class="sxs-lookup"><span data-stu-id="24674-194">Yes</span></span>|<span data-ttu-id="24674-195">無効 (既定値)</span><span class="sxs-lookup"><span data-stu-id="24674-195">No (default)</span></span>|<span data-ttu-id="24674-196">無視</span><span class="sxs-lookup"><span data-stu-id="24674-196">Ignored</span></span>|<span data-ttu-id="24674-197">暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。</span><span class="sxs-lookup"><span data-stu-id="24674-197">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="24674-198">はい</span><span class="sxs-lookup"><span data-stu-id="24674-198">Yes</span></span>|<span data-ttu-id="24674-199">はい</span><span class="sxs-lookup"><span data-stu-id="24674-199">Yes</span></span>|<span data-ttu-id="24674-200">はい</span><span class="sxs-lookup"><span data-stu-id="24674-200">Yes</span></span>|<span data-ttu-id="24674-201">無効 (既定値)</span><span class="sxs-lookup"><span data-stu-id="24674-201">No (default)</span></span>|<span data-ttu-id="24674-202">暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。</span><span class="sxs-lookup"><span data-stu-id="24674-202">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
|<span data-ttu-id="24674-203">はい</span><span class="sxs-lookup"><span data-stu-id="24674-203">Yes</span></span>|<span data-ttu-id="24674-204">はい</span><span class="sxs-lookup"><span data-stu-id="24674-204">Yes</span></span>|<span data-ttu-id="24674-205">はい</span><span class="sxs-lookup"><span data-stu-id="24674-205">Yes</span></span>|<span data-ttu-id="24674-206">はい</span><span class="sxs-lookup"><span data-stu-id="24674-206">Yes</span></span>|<span data-ttu-id="24674-207">暗号化は、検証可能なサーバー証明書が提供されている場合にのみ行われます。それ以外の場合は、接続試行が失敗します。</span><span class="sxs-lookup"><span data-stu-id="24674-207">Encryption occurs only if there is a verifiable server certificate, otherwise the connection attempt fails.</span></span>|  
  
 <span data-ttu-id="24674-208">詳細については、次を参照してください。[を使用して検証を伴わない暗号化](http://go.microsoft.com/fwlink/?LinkId=120500)SQL Server オンライン ブック。</span><span class="sxs-lookup"><span data-stu-id="24674-208">For more information, see [Using Encryption Without Validation](http://go.microsoft.com/fwlink/?LinkId=120500) in SQL Server Books Online.</span></span>  
  
## <a name="oledb-connection-strings"></a><span data-ttu-id="24674-209">OleDb 接続文字列</span><span class="sxs-lookup"><span data-stu-id="24674-209">OleDb Connection Strings</span></span>  
 <span data-ttu-id="24674-210"><xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> の <xref:System.Data.OleDb.OleDbConnection> プロパティを使用すると、Microsoft Access などの OLE DB データ ソースの接続文字列を取得または設定することができます。</span><span class="sxs-lookup"><span data-stu-id="24674-210">The <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> property of a <xref:System.Data.OleDb.OleDbConnection> allows you to get or set a connection string for an OLE DB data source, such as Microsoft Access.</span></span> <span data-ttu-id="24674-211">`OleDb` クラスを使用して、実行時に <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 接続文字列を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="24674-211">You can also create an `OleDb` connection string at run time by using the <xref:System.Data.OleDb.OleDbConnectionStringBuilder> class.</span></span>  
  
### <a name="oledb-connection-string-syntax"></a><span data-ttu-id="24674-212">OleDb 接続文字列の構文</span><span class="sxs-lookup"><span data-stu-id="24674-212">OleDb Connection String Syntax</span></span>  
 <span data-ttu-id="24674-213"><xref:System.Data.OleDb.OleDbConnection> 接続文字列では、プロバイダー名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24674-213">You must specify a provider name for an <xref:System.Data.OleDb.OleDbConnection> connection string.</span></span> <span data-ttu-id="24674-214">次の接続文字列は、Jet プロバイダーを使用して Microsoft Access データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="24674-214">The following connection string connects to a Microsoft Access database using the Jet provider.</span></span> <span data-ttu-id="24674-215">`UserID` および `Password` キーワードは、データベースがセキュリティ保護されていない場合は省略できます (既定)。</span><span class="sxs-lookup"><span data-stu-id="24674-215">Note that the `UserID` and `Password` keywords are optional if the database is unsecured (the default).</span></span>  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 <span data-ttu-id="24674-216">ユーザー レベルのセキュリティを使用して Jet データベースがセキュリティ保護されている場合は、ワークグループ情報ファイル (.mdw) の場所を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24674-216">If the Jet database is secured using user-level security, you must provide the location of the workgroup information file (.mdw).</span></span> <span data-ttu-id="24674-217">ワークグループ情報ファイルを使用して接続文字列に表示された資格情報を検証します。</span><span class="sxs-lookup"><span data-stu-id="24674-217">The workgroup information file is used to validate the credentials presented in the connection string.</span></span>  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="24674-218">接続情報を指定することは、 **OleDbConnection** Universal Data Link (UDL) ファイルです。 ただししないでそうです。</span><span class="sxs-lookup"><span data-stu-id="24674-218">It is possible to supply connection information for an **OleDbConnection** in a Universal Data Link (UDL) file; however you should avoid doing so.</span></span> <span data-ttu-id="24674-219">UDL ファイルは暗号化されないため、接続文字列をテキスト形式で表現してしまいます。</span><span class="sxs-lookup"><span data-stu-id="24674-219">UDL files are not encrypted, and expose connection string information in clear text.</span></span> <span data-ttu-id="24674-220">UDL ファイルは、アプリケーションにとって外部ファイルをベースにしたリソースであるため、.NET Framework でセキュリティ保護できません。</span><span class="sxs-lookup"><span data-stu-id="24674-220">Because a UDL file is an external file-based resource to your application, it cannot be secured using the .NET Framework.</span></span> <span data-ttu-id="24674-221">UDL ファイルはサポートされていません**SqlClient**です。</span><span class="sxs-lookup"><span data-stu-id="24674-221">UDL files are not supported for **SqlClient**.</span></span>  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a><span data-ttu-id="24674-222">DataDirectory を使用した Access/Jet との接続</span><span class="sxs-lookup"><span data-stu-id="24674-222">Using DataDirectory to Connect to Access/Jet</span></span>  
 <span data-ttu-id="24674-223">`DataDirectory` の使用は `SqlClient` に限定されません。</span><span class="sxs-lookup"><span data-stu-id="24674-223">`DataDirectory` is not exclusive to `SqlClient`.</span></span> <span data-ttu-id="24674-224"><xref:System.Data.OleDb> および <xref:System.Data.Odbc> .NET データ プロバイダーでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="24674-224">It can also be used with the <xref:System.Data.OleDb> and <xref:System.Data.Odbc> .NET data providers.</span></span> <span data-ttu-id="24674-225">アプリケーションの app_data フォルダーに格納された Northwind.mdb に接続するための <xref:System.Data.OleDb.OleDbConnection> 文字列の構文を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="24674-225">The following sample <xref:System.Data.OleDb.OleDbConnection> string demonstrates the syntax required to connect to the Northwind.mdb located in the application's app_data folder.</span></span> <span data-ttu-id="24674-226">この場所には、システム データベース (System.mdw) も格納されています。</span><span class="sxs-lookup"><span data-stu-id="24674-226">The system database (System.mdw) is also stored in that location.</span></span>  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="24674-227">Access/Jet データベースをセキュリティで保護しない場合は、接続文字列にシステム データベースの場所を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="24674-227">Specifying the location of the system database in the connection string is not required if the Access/Jet database is unsecured.</span></span> <span data-ttu-id="24674-228">既定では、セキュリティが無効になります。すべてのユーザーが、空のパスワードで組み込みの Admin ユーザーとして接続することになります。</span><span class="sxs-lookup"><span data-stu-id="24674-228">Security is off by default, with all users connecting as the built-in Admin user with a blank password.</span></span> <span data-ttu-id="24674-229">ユーザー レベルのセキュリティを正しく実装したとしても、Jet データベースは攻撃に対して無防備です。</span><span class="sxs-lookup"><span data-stu-id="24674-229">Even when user-level security is correctly implemented, a Jet database remains vulnerable to attack.</span></span> <span data-ttu-id="24674-230">ファイル ベースのセキュリティでは克服できない限界があるため、Access/Jet データベースに機密情報を格納することはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="24674-230">Therefore, storing sensitive information in an Access/Jet database is not recommended because of the inherent weakness of its file-based security scheme.</span></span>  
  
### <a name="connecting-to-excel"></a><span data-ttu-id="24674-231">Excel への接続</span><span class="sxs-lookup"><span data-stu-id="24674-231">Connecting to Excel</span></span>  
 <span data-ttu-id="24674-232">Excel ワークブックへの接続には、Microsoft Jet プロバイダーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="24674-232">The Microsoft Jet provider is used to connect to an Excel workbook.</span></span> <span data-ttu-id="24674-233">次の接続文字列では、`Extended Properties` キーワードは Excel に固有のプロパティを設定しています。</span><span class="sxs-lookup"><span data-stu-id="24674-233">In the following connection string, the `Extended Properties` keyword sets properties that are specific to Excel.</span></span> <span data-ttu-id="24674-234">「HDR=Yes;」は最初の列にデータではなく行の名前が含まれていることを示し、「IMEX=1;」は "intermixed" データ行を常にテキストとして読み取ることをドライバーに指示しています。</span><span class="sxs-lookup"><span data-stu-id="24674-234">"HDR=Yes;" indicates that the first row contains column names, not data, and "IMEX=1;" tells the driver to always read "intermixed" data columns as text.</span></span>  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 <span data-ttu-id="24674-235">`Extended Properties` を二重引用符で囲む必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="24674-235">Note that the double quotation character required for the `Extended Properties` must also be enclosed in double quotation marks.</span></span>  
  
### <a name="data-shape-provider-connection-string-syntax"></a><span data-ttu-id="24674-236">Data Shape プロバイダーの接続文字列の構文</span><span class="sxs-lookup"><span data-stu-id="24674-236">Data Shape Provider Connection String Syntax</span></span>  
 <span data-ttu-id="24674-237">Microsoft Data Shape プロバイダーを使用するときは、`Provider` および `Data Provider` キーワードを両方使用してください。</span><span class="sxs-lookup"><span data-stu-id="24674-237">Use both the `Provider` and the `Data Provider` keywords when using the Microsoft Data Shape provider.</span></span> <span data-ttu-id="24674-238">Shape プロバイダーを使用して SQL Server のローカル インスタンスに接続する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="24674-238">The following example uses the Shape provider to connect to a local instance of SQL Server.</span></span>  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a><span data-ttu-id="24674-239">Odbc 接続文字列</span><span class="sxs-lookup"><span data-stu-id="24674-239">Odbc Connection Strings</span></span>  
 <span data-ttu-id="24674-240"><xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> の <xref:System.Data.Odbc.OdbcConnection> プロパティを使用すると、OLE DB データベースで接続文字列を取得または設定することができます。</span><span class="sxs-lookup"><span data-stu-id="24674-240">The <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> property of a <xref:System.Data.Odbc.OdbcConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="24674-241"><xref:System.Data.Odbc.OdbcConnectionStringBuilder> は、Odbc の接続文字列もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="24674-241">Odbc connection strings are also supported by the <xref:System.Data.Odbc.OdbcConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="24674-242">次の接続文字列では、Microsoft Text Driver を使用しています。</span><span class="sxs-lookup"><span data-stu-id="24674-242">The following connection string uses the Microsoft Text Driver.</span></span>  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a><span data-ttu-id="24674-243">DataDirectory を使用した Visual FoxPro との接続</span><span class="sxs-lookup"><span data-stu-id="24674-243">Using DataDirectory to Connect to Visual FoxPro</span></span>  
 <span data-ttu-id="24674-244">次の <xref:System.Data.Odbc.OdbcConnection> 接続文字列は、`DataDirectory` を使用して Microsoft Visual FoxPro ファイルに接続する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="24674-244">The following <xref:System.Data.Odbc.OdbcConnection> connection string sample demonstrates using `DataDirectory` to connect to a Microsoft Visual FoxPro file.</span></span>  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a><span data-ttu-id="24674-245">Oracle 接続文字列</span><span class="sxs-lookup"><span data-stu-id="24674-245">Oracle Connection Strings</span></span>  
 <span data-ttu-id="24674-246"><xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> の <xref:System.Data.OracleClient.OracleConnection> プロパティを使用すると、OLE DB データベースで接続文字列を取得または設定することができます。</span><span class="sxs-lookup"><span data-stu-id="24674-246">The <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> property of a <xref:System.Data.OracleClient.OracleConnection> allows you to get or set a connection string for an OLE DB data source.</span></span> <span data-ttu-id="24674-247"><xref:System.Data.OracleClient.OracleConnectionStringBuilder> は、Oracle の接続文字列もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="24674-247">Oracle connection strings are also supported by the <xref:System.Data.OracleClient.OracleConnectionStringBuilder> .</span></span>  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 <span data-ttu-id="24674-248">ODBC 接続文字列の構文の詳細については、「<xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24674-248">For more information on ODBC connection string syntax, see <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24674-249">関連項目</span><span class="sxs-lookup"><span data-stu-id="24674-249">See Also</span></span>  
 [<span data-ttu-id="24674-250">接続文字列</span><span class="sxs-lookup"><span data-stu-id="24674-250">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="24674-251">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="24674-251">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="24674-252">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="24674-252">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
