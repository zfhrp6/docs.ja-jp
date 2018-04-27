---
title: トランザクションと同時実行
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 80db92f94f8cb523c3b8f9d0d08bbcb6b33c2fbe
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="73a89-102">トランザクションと同時実行</span><span class="sxs-lookup"><span data-stu-id="73a89-102">Transactions and Concurrency</span></span>
<span data-ttu-id="73a89-103">トランザクションは、単一のコマンド、またはパッケージとして実行されるコマンドのグループで構成されます。</span><span class="sxs-lookup"><span data-stu-id="73a89-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="73a89-104">トランザクションを使用することで、複数の操作を 1 つの作業単位にまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="73a89-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="73a89-105">トランザクションのあるポイントで障害が発生した場合は、トランザクションが開始される前の状態にすべての更新をロールバックできます。</span><span class="sxs-lookup"><span data-stu-id="73a89-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="73a89-106">データの一貫性を保証するために、トランザクションは ACID プロパティ (原始性、一貫性、分離性、および持続性) に準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73a89-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="73a89-107">Microsoft SQL Server など、ほとんどのリレーショナル データベース システムでは、クライアント アプリケーションが更新、挿入、または削除の操作を行うたびに、ロック、ログ、およびトランザクション管理の機能を提供し、トランザクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="73a89-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73a89-108">複数のリソースがかかわるトランザクションで、ロックがあまりにも長く保持されると、同時実行数が少なくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="73a89-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="73a89-109">そのため、トランザクションはできるだけ短くします。</span><span class="sxs-lookup"><span data-stu-id="73a89-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="73a89-110">トランザクションに、同じデータベースまたはサーバーの複数のテーブルが含まれている場合、一般的にストアド プロシージャ内の明示的トランザクションの方がパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="73a89-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="73a89-111">SQL Server のストアド プロシージャにトランザクションを作成するには、Transact-SQL ステートメントの `BEGIN TRANSACTION`、`COMMIT TRANSACTION`、および `ROLLBACK TRANSACTION` を使用します。</span><span class="sxs-lookup"><span data-stu-id="73a89-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="73a89-112">詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="73a89-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="73a89-113">SQL Server と Oracle 間のトランザクションなどの別のリソース マネージャーがトランザクションでは、分散トランザクションが必要です。</span><span class="sxs-lookup"><span data-stu-id="73a89-113">Transactions involving different resource managers, such as a transaction between SQL Server and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="73a89-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="73a89-114">In This Section</span></span>  
 [<span data-ttu-id="73a89-115">ローカル トランザクション</span><span class="sxs-lookup"><span data-stu-id="73a89-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="73a89-116">データベースに対してトランザクションを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="73a89-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="73a89-117">分散トランザクション</span><span class="sxs-lookup"><span data-stu-id="73a89-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="73a89-118">ADO.NET で分散トランザクションを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73a89-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="73a89-119">SQL Server と System.Transactions の統合</span><span class="sxs-lookup"><span data-stu-id="73a89-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="73a89-120">説明<xref:System.Transactions>は分散トランザクションを使用するための SQL Server と統合します。</span><span class="sxs-lookup"><span data-stu-id="73a89-120">Describes <xref:System.Transactions> integration with SQL Server for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="73a89-121">オプティミスティック同時実行制御</span><span class="sxs-lookup"><span data-stu-id="73a89-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="73a89-122">オプティミスティック同時実行制御とペシミスティック同時実行制御について、および同時実行違反をテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="73a89-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73a89-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="73a89-123">See Also</span></span>  
 [<span data-ttu-id="73a89-124">トランザクションの基礎</span><span class="sxs-lookup"><span data-stu-id="73a89-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [<span data-ttu-id="73a89-125">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="73a89-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="73a89-126">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="73a89-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="73a89-127">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="73a89-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="73a89-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="73a89-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="73a89-129">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="73a89-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
