---
title: 接続プール
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3cc97ec0681e58facd30e3dbbb74001676a6e451
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="connection-pooling"></a><span data-ttu-id="63150-102">接続プール</span><span class="sxs-lookup"><span data-stu-id="63150-102">Connection Pooling</span></span>
<span data-ttu-id="63150-103">データ ソースへの接続は時間のかかる処理です。</span><span class="sxs-lookup"><span data-stu-id="63150-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="63150-104">ADO.NET 接続を開くコストを最小限に抑えると呼ばれる最適化の手法を使用して*接続プーリング*、繰り返しタグと終了の接続のコストを最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="63150-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="63150-105">接続プールは、.NET Framework データ プロバイダーに応じて異なる処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="63150-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="63150-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="63150-106">In This Section</span></span>  
 [<span data-ttu-id="63150-107">SQL Server の接続プール (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="63150-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="63150-108">接続プールの概要を説明し、SQL Server で接続プールのしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="63150-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="63150-109">OLE DB、ODBC、および Oracle 接続プール</span><span class="sxs-lookup"><span data-stu-id="63150-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="63150-110">.NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC、および .NET Framework Data Provider for Oracle の接続プールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="63150-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63150-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="63150-111">See Also</span></span>  
 [<span data-ttu-id="63150-112">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="63150-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="63150-113">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="63150-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
