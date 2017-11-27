---
title: "Oracle 分散トランザクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c48232bb204b71c662a99bf210ad54fc3ee9eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="b14ff-102">Oracle 分散トランザクション</span><span class="sxs-lookup"><span data-stu-id="b14ff-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="b14ff-103"><xref:System.Data.OracleClient.OracleConnection> オブジェクトはトランザクションがアクティブであると判断した場合、既存の分散トランザクションに自動的に参加します。</span><span class="sxs-lookup"><span data-stu-id="b14ff-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="b14ff-104">自動トランザクション参加は、接続が開かれた場合または接続プールから取得された場合に行われます。</span><span class="sxs-lookup"><span data-stu-id="b14ff-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="b14ff-105">既存のトランザクションへの自動参加を無効にするには、</span><span class="sxs-lookup"><span data-stu-id="b14ff-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="b14ff-106">を <xref:System.Data.OracleClient.OracleConnection> の接続文字列パラメーターとして指定します。</span><span class="sxs-lookup"><span data-stu-id="b14ff-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b14ff-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="b14ff-107">See Also</span></span>  
 [<span data-ttu-id="b14ff-108">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b14ff-108">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="b14ff-109">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="b14ff-109">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
