---
title: "DbProviderFactory の取得"
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
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d230a122cbc02521c8d300d96cdd074bd7faa979
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="obtaining-a-dbproviderfactory"></a><span data-ttu-id="4c48c-102">DbProviderFactory の取得</span><span class="sxs-lookup"><span data-stu-id="4c48c-102">Obtaining a DbProviderFactory</span></span>
<span data-ttu-id="4c48c-103"><xref:System.Data.Common.DbProviderFactory> を取得する過程では、データ プロバイダーに関する情報が <xref:System.Data.Common.DbProviderFactories> クラスに渡されます。</span><span class="sxs-lookup"><span data-stu-id="4c48c-103">The process of obtaining a <xref:System.Data.Common.DbProviderFactory> involves passing information about a data provider to the <xref:System.Data.Common.DbProviderFactories> class.</span></span> <span data-ttu-id="4c48c-104"><xref:System.Data.Common.DbProviderFactories.GetFactory%2A> メソッドはこの情報に基づいて、厳密に型指定されたプロバイダー ファクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4c48c-104">Based on this information, the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method creates a strongly typed provider factory.</span></span> <span data-ttu-id="4c48c-105">たとえば、<xref:System.Data.SqlClient.SqlClientFactory> を作成するには、`GetFactory` の引数にプロバイダー名 System.Data.SqlClient を文字列として指定します。</span><span class="sxs-lookup"><span data-stu-id="4c48c-105">For example, to create a <xref:System.Data.SqlClient.SqlClientFactory>, you can pass `GetFactory` a string with the provider name specified as "System.Data.SqlClient".</span></span> <span data-ttu-id="4c48c-106">`GetFactory` には、<xref:System.Data.DataRow> を引数として受け取るオーバーロードも存在します。</span><span class="sxs-lookup"><span data-stu-id="4c48c-106">The other overload of `GetFactory` takes a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="4c48c-107">プロバイダー ファクトリを作成すると、対応するメソッドを使って他のオブジェクトを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4c48c-107">Once you create the provider factory, you can then use its methods to create additional objects.</span></span> <span data-ttu-id="4c48c-108">`SqlClientFactory` のメソッドには、<xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>、<xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>、<xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A> などがあります。</span><span class="sxs-lookup"><span data-stu-id="4c48c-108">Some of the methods of a `SqlClientFactory` include <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, and <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c48c-109">同様の機能は、.NET Framework の <xref:System.Data.OracleClient.OracleClientFactory> クラス、<xref:System.Data.Odbc.OdbcFactory> クラス、および <xref:System.Data.OleDb.OleDbFactory> クラスにも用意されています。</span><span class="sxs-lookup"><span data-stu-id="4c48c-109">The .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, and <xref:System.Data.OleDb.OleDbFactory> classes also provide similar functionality.</span></span>  
  
## <a name="registering-dbproviderfactories"></a><span data-ttu-id="4c48c-110">DbProviderFactory の登録</span><span class="sxs-lookup"><span data-stu-id="4c48c-110">Registering DbProviderFactories</span></span>  
 <span data-ttu-id="4c48c-111">ファクトリ ベースのクラスをサポートする各 .NET Framework データ プロバイダーの登録の構成情報、 **DbProviderFactories**のセクションで、 **machine.config**ローカル コンピューター上のファイルです。</span><span class="sxs-lookup"><span data-stu-id="4c48c-111">Each .NET Framework data provider that supports a factory-based class registers configuration information in the **DbProviderFactories** section of the **machine.config** file on the local computer.</span></span> <span data-ttu-id="4c48c-112">次の構成ファイル フラグメントは、<xref:System.Data.SqlClient> の構文と形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="4c48c-112">The following configuration file fragment shows the syntax and format for <xref:System.Data.SqlClient>.</span></span>  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"   
     description=".Net Framework Data Provider for SqlServer"   
     type="System.Data.SqlClient.SqlClientFactory, System.Data,   
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 <span data-ttu-id="4c48c-113">**インバリアント**属性を基になるデータ プロバイダーを識別します。</span><span class="sxs-lookup"><span data-stu-id="4c48c-113">The **invariant** attribute identifies the underlying data provider.</span></span> <span data-ttu-id="4c48c-114">この 3 つの部分から成る命名構文は、新しいファクトリを作成するときのほか、プロバイダー名とそれに関連付けられた接続文字列を実行時に取得できるようにするために、アプリケーションの構成ファイルでプロバイダーを指定するときにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="4c48c-114">This three-part naming syntax is also used when creating a new factory and for identifying the provider in an application configuration file so that the provider name, along with its associated connection string, can be retrieved at run time.</span></span>  
  
## <a name="retrieving-provider-information"></a><span data-ttu-id="4c48c-115">プロバイダー情報の取得</span><span class="sxs-lookup"><span data-stu-id="4c48c-115">Retrieving Provider Information</span></span>  
 <span data-ttu-id="4c48c-116"><xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> メソッドを使用すると、ローカル コンピューターにインストールされているすべてのデータ プロバイダーに関する情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="4c48c-116">You can retrieve information about all of the data providers installed on the local computer by using the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method.</span></span> <span data-ttu-id="4c48c-117">返します、<xref:System.Data.DataTable>という**DbProviderFactories**次の表で説明されている列を含むです。</span><span class="sxs-lookup"><span data-stu-id="4c48c-117">It returns a <xref:System.Data.DataTable> named **DbProviderFactories** that contains the columns described in the following table.</span></span>  
  
|<span data-ttu-id="4c48c-118">列の序数</span><span class="sxs-lookup"><span data-stu-id="4c48c-118">Column ordinal</span></span>|<span data-ttu-id="4c48c-119">列名</span><span class="sxs-lookup"><span data-stu-id="4c48c-119">Column name</span></span>|<span data-ttu-id="4c48c-120">サンプルの出力</span><span class="sxs-lookup"><span data-stu-id="4c48c-120">Example output</span></span>|<span data-ttu-id="4c48c-121">説明</span><span class="sxs-lookup"><span data-stu-id="4c48c-121">Description</span></span>|  
|--------------------|-----------------|--------------------|-----------------|  
|<span data-ttu-id="4c48c-122">0</span><span class="sxs-lookup"><span data-stu-id="4c48c-122">0</span></span>|<span data-ttu-id="4c48c-123">**名前**</span><span class="sxs-lookup"><span data-stu-id="4c48c-123">**Name**</span></span>|<span data-ttu-id="4c48c-124">SqlClient Data Provider</span><span class="sxs-lookup"><span data-stu-id="4c48c-124">SqlClient Data Provider</span></span>|<span data-ttu-id="4c48c-125">データ プロバイダーの読み取り可能な名前</span><span class="sxs-lookup"><span data-stu-id="4c48c-125">Readable name for the data provider</span></span>|  
|<span data-ttu-id="4c48c-126">1</span><span class="sxs-lookup"><span data-stu-id="4c48c-126">1</span></span>|<span data-ttu-id="4c48c-127">**説明**</span><span class="sxs-lookup"><span data-stu-id="4c48c-127">**Description**</span></span>|<span data-ttu-id="4c48c-128">.Net Framework Data Provider for SqlServer</span><span class="sxs-lookup"><span data-stu-id="4c48c-128">.Net Framework Data Provider for SqlServer</span></span>|<span data-ttu-id="4c48c-129">データ プロバイダーの読み取り可能な説明</span><span class="sxs-lookup"><span data-stu-id="4c48c-129">Readable description of the data provider</span></span>|  
|<span data-ttu-id="4c48c-130">2</span><span class="sxs-lookup"><span data-stu-id="4c48c-130">2</span></span>|<span data-ttu-id="4c48c-131">**示す InvariantName**</span><span class="sxs-lookup"><span data-stu-id="4c48c-131">**InvariantName**</span></span>|<span data-ttu-id="4c48c-132">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="4c48c-132">System.Data.SqlClient</span></span>|<span data-ttu-id="4c48c-133">プログラムでデータ プロバイダーの参照に使用できる名前</span><span class="sxs-lookup"><span data-stu-id="4c48c-133">Name that can be used programmatically to refer to the data provider</span></span>|  
|<span data-ttu-id="4c48c-134">3</span><span class="sxs-lookup"><span data-stu-id="4c48c-134">3</span></span>|<span data-ttu-id="4c48c-135">**AssemblyQualifiedName**</span><span class="sxs-lookup"><span data-stu-id="4c48c-135">**AssemblyQualifiedName**</span></span>|<span data-ttu-id="4c48c-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="4c48c-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span></span>|<span data-ttu-id="4c48c-137">オブジェクトをインスタンス化するための十分な情報を保持している、ファクトリ クラスの完全修飾名</span><span class="sxs-lookup"><span data-stu-id="4c48c-137">Fully qualified name of the factory class, which contains enough information to instantiate the object</span></span>|  
  
 <span data-ttu-id="4c48c-138">この `DataTable` を使用して、ユーザーに実行時に <xref:System.Data.DataRow> を選択してもらうことができます。</span><span class="sxs-lookup"><span data-stu-id="4c48c-138">This `DataTable` can be used to enable a user to select a <xref:System.Data.DataRow> at run time.</span></span> <span data-ttu-id="4c48c-139">次に、選択された `DataRow` を <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> メソッドに渡すことで、厳密に型指定された <xref:System.Data.Common.DbProviderFactory> を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4c48c-139">The selected `DataRow` can then be passed to the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method to create a strongly typed <xref:System.Data.Common.DbProviderFactory>.</span></span> <span data-ttu-id="4c48c-140">選択された <xref:System.Data.DataRow> を `GetFactory` メソッドに渡すことによって、目的の `DbProviderFactory` オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4c48c-140">A selected <xref:System.Data.DataRow> can be passed to the `GetFactory` method to create the desired `DbProviderFactory` object.</span></span>  
  
## <a name="listing-the-installed-provider-factory-classes"></a><span data-ttu-id="4c48c-141">インストールされているプロバイダー ファクトリ クラスの一覧表示</span><span class="sxs-lookup"><span data-stu-id="4c48c-141">Listing the Installed Provider Factory Classes</span></span>  
 <span data-ttu-id="4c48c-142">次の例では、インストールされているプロバイダーの情報を含んだ <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> を、<xref:System.Data.DataTable> メソッドを使用して取得します。</span><span class="sxs-lookup"><span data-stu-id="4c48c-142">This example demonstrates how to use the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method to return a <xref:System.Data.DataTable> containing information about the installed providers.</span></span> <span data-ttu-id="4c48c-143">このコードは、`DataTable` 内の各行を反復処理しながら、インストールされている各プロバイダーの情報をコンソール ウィンドウに表示します。</span><span class="sxs-lookup"><span data-stu-id="4c48c-143">The code iterates through each row in the `DataTable`, displaying information for each installed provider in the console window.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a><span data-ttu-id="4c48c-144">アプリケーション構成ファイルを使用したファクトリ情報の保存</span><span class="sxs-lookup"><span data-stu-id="4c48c-144">Using Application Configuration Files to Store Factory Information</span></span>  
 <span data-ttu-id="4c48c-145">ファクトリを使用したデザイン パターンは、アプリケーション構成ファイルでプロバイダーと接続文字列情報を格納するなどを任せます**app.config** Windows アプリケーションの場合と**web.config** ASP.NET アプリケーション用。</span><span class="sxs-lookup"><span data-stu-id="4c48c-145">The design pattern used for working with factories entails storing provider and connection string information in an application configuration file, such as **app.config** for a Windows application, and **web.config** for an ASP.NET application.</span></span>  
  
 <span data-ttu-id="4c48c-146">次の構成ファイル フラグメントは、2 つの名前付き接続文字列 (SQL Server の Northwind データベースに接続するための "NorthwindSQL" と、Access/Jet の Northwind データベースに接続するための "NorthwindAccess") を保存する例を示したものです。</span><span class="sxs-lookup"><span data-stu-id="4c48c-146">The following configuration file fragment demonstrates how to save two named connection strings, "NorthwindSQL" for a connection to the Northwind database in SQL Server, and "NorthwindAccess" for a connection to the Northwind database in Access/Jet.</span></span> <span data-ttu-id="4c48c-147">**インバリアント**の名前が使用される、 **providerName**属性。</span><span class="sxs-lookup"><span data-stu-id="4c48c-147">The **invariant** name is used for the **providerName** attribute.</span></span>  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"   
     providerName="System.Data.SqlClient"   
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"   
     providerName="System.Data.OleDb"   
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a><span data-ttu-id="4c48c-148">プロバイダー名による接続文字列の取得</span><span class="sxs-lookup"><span data-stu-id="4c48c-148">Retrieving a Connection String by Provider Name</span></span>  
 <span data-ttu-id="4c48c-149">プロバイダー ファクトリを作成するには、プロバイダー名だけでなく接続文字列も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c48c-149">In order to create a provider factory, you must supply a connection string as well as the provider name.</span></span> <span data-ttu-id="4c48c-150">この例は、ロケールに依存しない形式でプロバイダー名を渡すことで、アプリケーション構成ファイルから接続文字列を取得する方法を示します"*System.Data.ProviderName*"です。</span><span class="sxs-lookup"><span data-stu-id="4c48c-150">This example demonstrates how to retrieve a connection string from an application configuration file by passing the provider name in the invariant format "*System.Data.ProviderName*".</span></span> <span data-ttu-id="4c48c-151">このコードでは、<xref:System.Configuration.ConnectionStringSettingsCollection> を反復処理しています。</span><span class="sxs-lookup"><span data-stu-id="4c48c-151">The code iterates through the <xref:System.Configuration.ConnectionStringSettingsCollection>.</span></span> <span data-ttu-id="4c48c-152">成功した場合には <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> が、それ以外の場合は `null` (Visual Basic の場合は `Nothing`) が返されます。</span><span class="sxs-lookup"><span data-stu-id="4c48c-152">It returns the <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> on success; otherwise `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="4c48c-153">プロバイダーに複数のエントリが存在した場合は、最初に見つかったエントリが返されます。</span><span class="sxs-lookup"><span data-stu-id="4c48c-153">If there are multiple entries for a provider, the first one found is returned.</span></span> <span data-ttu-id="4c48c-154">詳細と構成ファイルから接続文字列を取得する例については、次を参照してください。[接続文字列と構成ファイル](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c48c-154">For more information and examples of retrieving connection strings from configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c48c-155">このコードを実行するには、`System.Configuration.dll` を参照設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c48c-155">A reference to `System.Configuration.dll` is required in order for the code to run.</span></span>  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a><span data-ttu-id="4c48c-156">DbProviderFactory および DbConnection の作成</span><span class="sxs-lookup"><span data-stu-id="4c48c-156">Creating the DbProviderFactory and DbConnection</span></span>  
 <span data-ttu-id="4c48c-157">この例は、作成する方法を示します、<xref:System.Data.Common.DbProviderFactory>と<xref:System.Data.Common.DbConnection>形式でプロバイダー名を渡すことによってオブジェクト"*System.Data.ProviderName*"と接続文字列。</span><span class="sxs-lookup"><span data-stu-id="4c48c-157">This example demonstrates how to create a <xref:System.Data.Common.DbProviderFactory> and <xref:System.Data.Common.DbConnection> object by passing it the provider name in the format "*System.Data.ProviderName*" and a connection string.</span></span> <span data-ttu-id="4c48c-158">成功した場合には `DbConnection` オブジェクトが返されます。エラーが発生した場合は `null` (Visual Basic の場合は `Nothing`) が返されます。</span><span class="sxs-lookup"><span data-stu-id="4c48c-158">A `DbConnection` object is returned on success; `null` (`Nothing` in Visual Basic) on any error.</span></span>  
  
 <span data-ttu-id="4c48c-159">このコードでは、`DbProviderFactory` を呼び出すことによって <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> を取得しています。</span><span class="sxs-lookup"><span data-stu-id="4c48c-159">The code obtains the `DbProviderFactory` by calling <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span></span> <span data-ttu-id="4c48c-160">次に、<xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> メソッドで <xref:System.Data.Common.DbConnection> オブジェクトを作成し、<xref:System.Data.Common.DbConnection.ConnectionString%2A> プロパティに接続文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="4c48c-160">Then the <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> method creates the <xref:System.Data.Common.DbConnection> object and the <xref:System.Data.Common.DbConnection.ConnectionString%2A> property is set to the connection string.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4c48c-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c48c-161">See Also</span></span>  
 [<span data-ttu-id="4c48c-162">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="4c48c-162">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="4c48c-163">接続文字列</span><span class="sxs-lookup"><span data-stu-id="4c48c-163">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="4c48c-164">構成クラスの使用</span><span class="sxs-lookup"><span data-stu-id="4c48c-164">Using the Configuration Classes</span></span>](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [<span data-ttu-id="4c48c-165">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="4c48c-165">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
