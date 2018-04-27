---
title: ADO.NET でのデータの取得および変更
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 05760e7295606f700f72e5a3af14e395bcc5d820
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="28b33-102">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="28b33-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="28b33-103">データベース アプリケーションの主な機能は、データ ソースとの接続およびデータベースに格納されているデータの取得です。</span><span class="sxs-lookup"><span data-stu-id="28b33-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="28b33-104">使用してデータの取得も同様のコマンドを実行することができます、アプリケーションとデータ ソース間のブリッジとしての ADO.NET の .NET Framework データ プロバイダーの機能、 **DataReader**または**DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="28b33-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="28b33-105">データベースに格納されているデータを更新する機能は、データベース アプリケーションの重要な機能の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="28b33-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="28b33-106">ADO.NET でデータの更新を使用して、 **DataAdapter**と<xref:System.Data.DataSet>、および**コマンド**オブジェクトも含まれますトランザクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="28b33-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28b33-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="28b33-107">In This Section</span></span>  
 [<span data-ttu-id="28b33-108">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="28b33-108">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 <span data-ttu-id="28b33-109">データ ソースへの接続を確立する方法、および接続イベントを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="28b33-110">接続文字列</span><span class="sxs-lookup"><span data-stu-id="28b33-110">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 <span data-ttu-id="28b33-111">接続文字列のキーワード、セキュリティ情報、セキュリティ情報の格納や取得など、接続文字列を使用するうえでのさまざまな側面について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="28b33-112">接続プール</span><span class="sxs-lookup"><span data-stu-id="28b33-112">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 <span data-ttu-id="28b33-113">.NET Framework Data Provider の接続プールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="28b33-114">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="28b33-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="28b33-115">コマンドおよびコマンド ビルダーを作成する方法、パラメーターを構成する方法、およびコマンドを実行してデータを取得および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="28b33-116">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="28b33-116">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 <span data-ttu-id="28b33-117">DataReaders、DataAdapters、パラメーター、DataAdapter イベントの処理、およびバッチ操作の実行について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="28b33-118">トランザクションと同時実行</span><span class="sxs-lookup"><span data-stu-id="28b33-118">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="28b33-119">ローカル トランザクションや分散トランザクションの実行方法、およびオプティミスティック同時実行の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="28b33-120">ID 値および Autonumber 値の取得</span><span class="sxs-lookup"><span data-stu-id="28b33-120">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="28b33-121">生成された値のマッピングの例を示します、 **identity**またはの SQL Server テーブル内の列、 **Autonumber**フィールドをテーブルに挿入された行の列の Access テーブルにします。</span><span class="sxs-lookup"><span data-stu-id="28b33-121">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="28b33-122">`DataTable` での ID 値の結合について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="28b33-123">バイナリ データの取得</span><span class="sxs-lookup"><span data-stu-id="28b33-123">Retrieving Binary Data</span></span>](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 <span data-ttu-id="28b33-124">バイナリ データまたは使用して大規模なデータ構造体を取得する方法について説明`CommandBehavior`です。`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="28b33-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="28b33-125">既定の動作を変更する、`DataReader`です。</span><span class="sxs-lookup"><span data-stu-id="28b33-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="28b33-126">ストアド プロシージャでのデータの変更</span><span class="sxs-lookup"><span data-stu-id="28b33-126">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="28b33-127">ストアド プロシージャの入力パラメーターおよび出力パラメーターを使用してデータベースに行を挿入し、新しい ID 値を返す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="28b33-128">データベース スキーマ情報の取得</span><span class="sxs-lookup"><span data-stu-id="28b33-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 <span data-ttu-id="28b33-129">データベースまたはカタログ、データベース内のテーブルおよびビュー、テーブルに対して存在する制約、およびその他のスキーマ情報をデータ ソースから取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="28b33-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="28b33-130">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="28b33-131">プロバイダー ファクトリ モデルについて説明し、`System.Data.Common` 名前空間の基本クラスの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="28b33-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="28b33-132">ADO.NET のデータ追跡</span><span class="sxs-lookup"><span data-stu-id="28b33-132">Data Tracing in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-tracing.md)  
 <span data-ttu-id="28b33-133">ADO.NET が備える組み込みデータ トレース機能のしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="28b33-134">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="28b33-134">Performance Counters</span></span>](../../../../docs/framework/data/adonet/performance-counters.md)  
 <span data-ttu-id="28b33-135">`SqlClient` および `OracleClient` で使用できるパフォーマンス カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="28b33-136">非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="28b33-136">Asynchronous Programming</span></span>](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 <span data-ttu-id="28b33-137">非同期プログラミングに対する [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] サポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-137">Describes [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="28b33-138">SqlClient ストリーミング サポート</span><span class="sxs-lookup"><span data-stu-id="28b33-138">SqlClient Streaming Support</span></span>](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 <span data-ttu-id="28b33-139">完全にメモリに読み込まれていることをしなくても SQL Server からアプリケーション ストリーム データを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="28b33-139">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b33-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="28b33-140">See Also</span></span>  
 [<span data-ttu-id="28b33-141">ADO.NET でのデータ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="28b33-141">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="28b33-142">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="28b33-142">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="28b33-143">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="28b33-143">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="28b33-144">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="28b33-144">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="28b33-145">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="28b33-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
