---
title: "トランザクションと同時実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e6dfa946313bb9d43077bad68b761e8f03c175c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="transactions-and-concurrency"></a>トランザクションと同時実行
トランザクションは、単一のコマンド、またはパッケージとして実行されるコマンドのグループで構成されます。 トランザクションを使用することで、複数の操作を 1 つの作業単位にまとめることができます。 トランザクションのあるポイントで障害が発生した場合は、トランザクションが開始される前の状態にすべての更新をロールバックできます。  
  
 データの一貫性を保証するために、トランザクションは ACID プロパティ (原始性、一貫性、分離性、および持続性) に準拠する必要があります。 Microsoft SQL Server など、ほとんどのリレーショナル データベース システムでは、クライアント アプリケーションが更新、挿入、または削除の操作を行うたびに、ロック、ログ、およびトランザクション管理の機能を提供し、トランザクションをサポートします。  
  
> [!NOTE]
>  複数のリソースがかかわるトランザクションで、ロックがあまりにも長く保持されると、同時実行数が少なくなる場合があります。 そのため、トランザクションはできるだけ短くします。  
  
 トランザクションに、同じデータベースまたはサーバーの複数のテーブルが含まれている場合、一般的にストアド プロシージャ内の明示的トランザクションの方がパフォーマンスが向上します。 SQL Server のストアド プロシージャにトランザクションを作成するには、Transact-SQL ステートメントの `BEGIN TRANSACTION`、`COMMIT TRANSACTION`、および `ROLLBACK TRANSACTION` を使用します。 詳細については、SQL Server オンライン ブックを参照してください。  
  
 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] と Oracle 間のトランザクションなど、種類の異なるリソース マネージャーがトランザクションに含まれる場合、分散トランザクションが必要になります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ローカル トランザクション](../../../../docs/framework/data/adonet/local-transactions.md)  
 データベースに対してトランザクションを実行する方法を示します。  
  
 [分散トランザクション](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 ADO.NET で分散トランザクションを実行する方法について説明します。  
  
 [SQL Server と System.Transactions の統合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 分散トランザクションを使用するための、<xref:System.Transactions> の [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 統合について説明します。  
  
 [オプティミスティック同時実行制御](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 オプティミスティック同時実行制御とペシミスティック同時実行制御について、および同時実行違反をテストする方法について説明します。  
  
## <a name="see-also"></a>参照  
 [トランザクションの基礎](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [データ ソースへの接続](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
