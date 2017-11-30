---
title: "ADO.NET でのデータ ソースへの接続"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0d21c571b659e9d7aef65893db18b034d614e2af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="connecting-to-a-data-source-in-adonet"></a><span data-ttu-id="75a22-102">ADO.NET でのデータ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="75a22-102">Connecting to a Data Source in ADO.NET</span></span>
<span data-ttu-id="75a22-103">ADO.NET で使用して、**接続**接続文字列に必要な認証情報を入力して、特定のデータ ソースに接続するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="75a22-103">In ADO.NET you use a **Connection** object to connect to a specific data source by supplying necessary authentication information in a connection string.</span></span> <span data-ttu-id="75a22-104">**接続**オブジェクトを使用するデータ ソースの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="75a22-104">The **Connection** object you use depends on the type of data source.</span></span>  
  
 <span data-ttu-id="75a22-105">.NET Framework に含まれている各 .NET Framework データ プロバイダーは、<xref:System.Data.Common.DbConnection> オブジェクトを持っています。.NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbConnection> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlConnection> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcConnection> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleConnection> があります。</span><span class="sxs-lookup"><span data-stu-id="75a22-105">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbConnection> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbConnection> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlConnection> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcConnection> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleConnection> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75a22-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="75a22-106">In This Section</span></span>  
 [<span data-ttu-id="75a22-107">接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="75a22-107">Establishing the Connection</span></span>](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 <span data-ttu-id="75a22-108">使用する方法について説明します、**接続**オブジェクト データ ソースへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="75a22-108">Describes how to use a **Connection** object to establish a connection to a data source.</span></span>  
  
 [<span data-ttu-id="75a22-109">接続イベント</span><span class="sxs-lookup"><span data-stu-id="75a22-109">Connection Events</span></span>](../../../../docs/framework/data/adonet/connection-events.md)  
 <span data-ttu-id="75a22-110">使用する方法について説明します、 **InfoMessage**データ ソースから情報メッセージを取得するイベントです。</span><span class="sxs-lookup"><span data-stu-id="75a22-110">Describes how to use an **InfoMessage** event to retrieve informational messages from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75a22-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="75a22-111">See Also</span></span>  
 [<span data-ttu-id="75a22-112">接続文字列</span><span class="sxs-lookup"><span data-stu-id="75a22-112">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="75a22-113">接続プール</span><span class="sxs-lookup"><span data-stu-id="75a22-113">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [<span data-ttu-id="75a22-114">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="75a22-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="75a22-115">Dataadapter と Datareader</span><span class="sxs-lookup"><span data-stu-id="75a22-115">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="75a22-116">トランザクションと同時実行</span><span class="sxs-lookup"><span data-stu-id="75a22-116">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="75a22-117">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="75a22-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
