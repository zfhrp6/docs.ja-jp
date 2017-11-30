---
title: "DataAdapter と DataReader"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e7a0af0b5fabdfacfcc825258242868b0fbb513
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="5ff0d-102">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="5ff0d-102">DataAdapters and DataReaders</span></span>
<span data-ttu-id="5ff0d-103">ADO.NET を使用する**DataReader**をデータベースからデータの読み取り専用、前方参照専用のストリームを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-103">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="5ff0d-104">結果が返されるように、クエリが実行され、それらを要求するまで、クライアントのネットワーク バッファーに格納されますを使用して、**読み取り**のメソッド、 **DataReader**です。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-104">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="5ff0d-105">使用して、 **DataReader** 、使用可能になるとすぐにデータを取得して (既定) の両方に、アプリケーションのパフォーマンスを向上できるメモリ、システムのオーバーヘッドを減らすことで、一度に 1 行のみを格納します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-105">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="5ff0d-106"><xref:System.Data.Common.DataAdapter> は、データ ソースからデータを取得し、1 つの <xref:System.Data.DataSet> 内でテーブルを設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-106">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="5ff0d-107">また、`DataAdapter` は、`DataSet` に対して加えられた変更をデータ ソースに反映させます。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-107">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="5ff0d-108">`DataAdapter` は .NET Framework データ プロバイダーの `Connection` オブジェクトを使用してデータ ソースに接続し、`Command` オブジェクトを使用してデータ ソースからデータを取得し、変更をデータ ソースに反映させます。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-108">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="5ff0d-109">.NET Framework に含まれている各 .NET Framework データ プロバイダーには、<xref:System.Data.Common.DbDataReader> および <xref:System.Data.Common.DbDataAdapter> オブジェクトがあります。.NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbDataReader> および <xref:System.Data.OleDb.OleDbDataAdapter> オブジェクトがあります。.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlDataReader> および <xref:System.Data.SqlClient.SqlDataAdapter> オブジェクトがあります。.NET Framework Data Provider for ODBC には、<xref:System.Data.Odbc.OdbcDataReader> および <xref:System.Data.Odbc.OdbcDataAdapter> オブジェクトがあります。.NET Framework Data Provider for Oracle には、<xref:System.Data.OracleClient.OracleDataReader> および <xref:System.Data.OracleClient.OracleDataAdapter> オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-109">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ff0d-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5ff0d-110">In This Section</span></span>  
 [<span data-ttu-id="5ff0d-111">DataReader によるデータの取得</span><span class="sxs-lookup"><span data-stu-id="5ff0d-111">Retrieving Data Using a DataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="5ff0d-112">ADO.NET の説明**DataReader**オブジェクトと、ストリームを返す結果のデータ ソースから使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-112">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="5ff0d-113">DataAdapter からの DataSet の読み込み</span><span class="sxs-lookup"><span data-stu-id="5ff0d-113">Populating a DataSet from a DataAdapter</span></span>](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="5ff0d-114">`DataSet` を使用して `DataAdapter` にテーブル、列、および行を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-114">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="5ff0d-115">DataAdapter パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ff0d-115">DataAdapter Parameters</span></span>](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 <span data-ttu-id="5ff0d-116">`DataAdapter` のコマンド プロパティのパラメーターを使用する方法と、`DataSet` の列の内容をコマンド パラメーターに割り当てる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-116">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="5ff0d-117">DataSet への既存の制約の追加</span><span class="sxs-lookup"><span data-stu-id="5ff0d-117">Adding Existing Constraints to a DataSet</span></span>](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="5ff0d-118">既存の制約を `DataSet` に追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-118">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="5ff0d-119">DataAdapter DataTable と DataColumn のマップ</span><span class="sxs-lookup"><span data-stu-id="5ff0d-119">DataAdapter DataTable and DataColumn Mappings</span></span>](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="5ff0d-120">`DataTableMappings` の `ColumnMappings` および `DataAdapter` を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-120">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="5ff0d-121">クエリ結果のページング</span><span class="sxs-lookup"><span data-stu-id="5ff0d-121">Paging Through a Query Result</span></span>](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 <span data-ttu-id="5ff0d-122">クエリの結果をデータ ページとして表示する例を示します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-122">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="5ff0d-123">DataAdapter によるデータ ソースの更新</span><span class="sxs-lookup"><span data-stu-id="5ff0d-123">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="5ff0d-124">`DataAdapter` を使用して `DataSet` の変更内容を解決してデータベースに戻す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-124">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="5ff0d-125">DataAdapter のイベントを処理</span><span class="sxs-lookup"><span data-stu-id="5ff0d-125">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 <span data-ttu-id="5ff0d-126">`DataAdapter` のイベントおよびその使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-126">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="5ff0d-127">Dataadapter を使用したバッチ操作の実行</span><span class="sxs-lookup"><span data-stu-id="5ff0d-127">Performing Batch Operations Using DataAdapters</span></span>](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="5ff0d-128">`DataSet` から更新を適用する際に、SQL Server へのラウンド トリップ回数を減らすことにより、アプリケーションのパフォーマンスを向上させる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5ff0d-128">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ff0d-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ff0d-129">See Also</span></span>  
 [<span data-ttu-id="5ff0d-130">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="5ff0d-130">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="5ff0d-131">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="5ff0d-131">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="5ff0d-132">トランザクションと同時実行</span><span class="sxs-lookup"><span data-stu-id="5ff0d-132">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="5ff0d-133">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="5ff0d-133">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="5ff0d-134">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="5ff0d-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
