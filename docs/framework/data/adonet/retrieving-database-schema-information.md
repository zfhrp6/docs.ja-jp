---
title: "データベース スキーマ情報の取得"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 09a0ec444801d1fe2caccf9e25a68e3c6ae8f5c2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-database-schema-information"></a><span data-ttu-id="a0abe-102">データベース スキーマ情報の取得</span><span class="sxs-lookup"><span data-stu-id="a0abe-102">Retrieving Database Schema Information</span></span>
<span data-ttu-id="a0abe-103">データベースからのスキーマ情報の取得は、スキーマの検出プロセスによって行われます。</span><span class="sxs-lookup"><span data-stu-id="a0abe-103">Obtaining schema information from a database is accomplished with the process of schema discovery.</span></span> <span data-ttu-id="a0abe-104">スキーマの検出により、アプリケーションはマネージ プロバイダーを検索するとも呼ばれるデータベース スキーマに関する情報を返すことを要求する*メタデータ*、特定のデータベースです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-104">Schema discovery allows applications to request that managed providers find and return information about the database schema, also known as *metadata*, of a given database.</span></span> <span data-ttu-id="a0abe-105">テーブル、列、ストアド プロシージャなどの各種のデータベース スキーマ要素は、スキーマ コレクションを通じて公開されます。</span><span class="sxs-lookup"><span data-stu-id="a0abe-105">Different database schema elements such as tables, columns, and stored-procedures are exposed through schema collections.</span></span> <span data-ttu-id="a0abe-106">各スキーマ コレクションには、使用されているプロバイダーに固有の各種のスキーマ情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0abe-106">Each schema collection contains a variety of schema information specific to the provider being used.</span></span>  
  
 <span data-ttu-id="a0abe-107">.NET Framework マネージ プロバイダーの実装の各、 **GetSchema**メソッドで、**接続**クラス、およびから返されるスキーマ情報、 **GetSchema**メソッドは、の形式では、<xref:System.Data.DataTable>です。</span><span class="sxs-lookup"><span data-stu-id="a0abe-107">Each of the .NET Framework managed providers implement the **GetSchema** method in the **Connection** class, and the schema information that is returned from the **GetSchema** method comes in the form of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="a0abe-108">**GetSchema**メソッドが戻るには、スキーマ コレクションを指定し、返される情報の量を制限するための省略可能なパラメーターを提供するオーバー ロードされたメソッドです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-108">The **GetSchema** method is an overloaded method that provides optional parameters for specifying the schema collection to return, and restricting the amount of information returned.</span></span>  
  
 <span data-ttu-id="a0abe-109">OLE DB、ODBC、Oracle、および SqlClient 用の .NET Framework データ プロバイダーの提供、 **GetSchemaTable**の列のメタデータを表す DataTable を返すメソッド、 **DataReader**です。</span><span class="sxs-lookup"><span data-stu-id="a0abe-109">The .NET Framework Data Providers for OLE DB, ODBC, Oracle, and SqlClient provide a **GetSchemaTable** method that returns a DataTable describing the column metadata of the **DataReader**.</span></span>  
  
 <span data-ttu-id="a0abe-110">.NET Framework Data Provider for OLE DB では、<xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> オブジェクトの <xref:System.Data.OleDb.OleDbConnection> メソッドを使ってスキーマ情報を公開します。</span><span class="sxs-lookup"><span data-stu-id="a0abe-110">The .NET Framework Data Provider for OLE DB also exposes schema information by using the <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> method of the <xref:System.Data.OleDb.OleDbConnection> object.</span></span> <span data-ttu-id="a0abe-111">引数として、 **GetOleDbSchemaTable**受け取り、<xref:System.Data.OleDb.OleDbSchemaGuid>スキーマ情報を返すを識別して、これらの制限の配列には、列が返されます。</span><span class="sxs-lookup"><span data-stu-id="a0abe-111">As arguments, **GetOleDbSchemaTable** takes an <xref:System.Data.OleDb.OleDbSchemaGuid> that identifies the schema information to return, and an array of restrictions on those returned columns.</span></span> <span data-ttu-id="a0abe-112">**GetOleDbSchemaTable**を返します、<xref:System.Data.DataTable>要求されたスキーマ情報が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a0abe-112">**GetOleDbSchemaTable** returns a <xref:System.Data.DataTable> populated with the requested schema information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0abe-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a0abe-113">In This Section</span></span>  
 [<span data-ttu-id="a0abe-114">GetSchema およびスキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="a0abe-114">GetSchema and Schema Collections</span></span>](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 <span data-ttu-id="a0abe-115">について説明します、 **GetSchema**メソッドとそれを使用して、取得し、データベースからスキーマ情報を制限する方法です。</span><span class="sxs-lookup"><span data-stu-id="a0abe-115">Describes the **GetSchema** method and how it can be used to retrieve and restrict schema information from a database.</span></span>  
  
 <span data-ttu-id="a0abe-116">スキーマの制限</span><span class="sxs-lookup"><span data-stu-id="a0abe-116">Schema Restrictions</span></span>  
 <span data-ttu-id="a0abe-117">使用できるスキーマの制限について説明します**GetSchema**です。</span><span class="sxs-lookup"><span data-stu-id="a0abe-117">Describes schema restrictions that can be used with **GetSchema**.</span></span>  
  
 [<span data-ttu-id="a0abe-118">共通のスキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="a0abe-118">Common Schema Collections</span></span>](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 <span data-ttu-id="a0abe-119">すべての .NET Framework マネージ プロバイダーでサポートされる共通のスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0abe-119">Describes all of the common schema collections supported by all of the .NET Framework managed providers.</span></span>  
  
 [<span data-ttu-id="a0abe-120">SQL Server スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="a0abe-120">SQL Server Schema Collections</span></span>](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 <span data-ttu-id="a0abe-121">.NET Framework Provider for SQL Server でサポートされるスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0abe-121">Describes the schema collection supported by the .NET Framework provider for SQL Server.</span></span>  
  
 [<span data-ttu-id="a0abe-122">Oracle スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="a0abe-122">Oracle Schema Collections</span></span>](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 <span data-ttu-id="a0abe-123">.NET Framework Provider for Oracle でサポートされるスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0abe-123">Describes the schema collection supported by the .NET Framework provider for Oracle.</span></span>  
  
 [<span data-ttu-id="a0abe-124">ODBC スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="a0abe-124">ODBC Schema Collections</span></span>](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 <span data-ttu-id="a0abe-125">ODBC ドライバーのスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0abe-125">Describes the schema collections for ODBC drivers.</span></span>  
  
 [<span data-ttu-id="a0abe-126">OLE DB スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="a0abe-126">OLE DB Schema Collections</span></span>](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 <span data-ttu-id="a0abe-127">OLE DB プロバイダーのスキーマ コレクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a0abe-127">Describes the schema collections for OLE DB providers.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a0abe-128">参照</span><span class="sxs-lookup"><span data-stu-id="a0abe-128">Reference</span></span>  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <span data-ttu-id="a0abe-129">について説明します、 **GetSchema**のメソッド、<xref:System.Data.Common.DbConnection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-129">Describes the **GetSchema** method of the <xref:System.Data.Common.DbConnection> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <span data-ttu-id="a0abe-130">について説明します、 **GetSchema**のメソッド、<xref:System.Data.Odbc.OdbcConnection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-130">Describes the **GetSchema** method of the <xref:System.Data.Odbc.OdbcConnection> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <span data-ttu-id="a0abe-131">について説明します、 **GetSchema**のメソッド、<xref:System.Data.OleDb.OleDbConnection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-131">Describes the **GetSchema** method of the <xref:System.Data.OleDb.OleDbConnection> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <span data-ttu-id="a0abe-132">について説明します、 **GetSchema**のメソッド、<xref:System.Data.OracleClient.OracleConnection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-132">Describes the **GetSchema** method of the <xref:System.Data.OracleClient.OracleConnection> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <span data-ttu-id="a0abe-133">について説明します、 **GetSchema**のメソッド、<xref:System.Data.SqlClient.SqlConnection>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-133">Describes the **GetSchema** method of the <xref:System.Data.SqlClient.SqlConnection> class.</span></span>  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="a0abe-134">について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.Common.DbDataReader>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-134">Describes the **GetSchemaTable** method of the <xref:System.Data.Common.DbDataReader> class.</span></span>  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="a0abe-135">について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.Odbc.OdbcDataReader>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-135">Describes the **GetSchemaTable** method of the <xref:System.Data.Odbc.OdbcDataReader> class.</span></span>  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="a0abe-136">について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.OleDb.OleDbDataReader>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-136">Describes the **GetSchemaTable** method of the <xref:System.Data.OleDb.OleDbDataReader> class.</span></span>  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="a0abe-137">について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.OracleClient.OracleDataReader>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-137">Describes the **GetSchemaTable** method of the <xref:System.Data.OracleClient.OracleDataReader> class.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <span data-ttu-id="a0abe-138">について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.SqlClient.SqlDataReader>クラスです。</span><span class="sxs-lookup"><span data-stu-id="a0abe-138">Describes the **GetSchemaTable** method of the <xref:System.Data.SqlClient.SqlDataReader> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0abe-139">参照</span><span class="sxs-lookup"><span data-stu-id="a0abe-139">See Also</span></span>  
 [<span data-ttu-id="a0abe-140">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="a0abe-140">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="a0abe-141">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="a0abe-141">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
