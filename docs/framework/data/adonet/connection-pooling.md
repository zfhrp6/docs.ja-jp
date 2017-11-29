---
title: "接続プール"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c7398fbea3b59cafed6f9a7f2f4f0440ef29b80a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="connection-pooling"></a><span data-ttu-id="4c5e6-102">接続プール</span><span class="sxs-lookup"><span data-stu-id="4c5e6-102">Connection Pooling</span></span>
<span data-ttu-id="4c5e6-103">データ ソースへの接続は時間のかかる処理です。</span><span class="sxs-lookup"><span data-stu-id="4c5e6-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="4c5e6-104">ADO.NET 接続を開くコストを最小限に抑えると呼ばれる最適化の手法を使用して*接続プーリング*、繰り返しタグと終了の接続のコストを最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="4c5e6-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="4c5e6-105">接続プールは、.NET Framework データ プロバイダーに応じて異なる処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="4c5e6-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c5e6-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4c5e6-106">In This Section</span></span>  
 [<span data-ttu-id="4c5e6-107">SQL Server の接続プール (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4c5e6-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="4c5e6-108">接続プールの概要および [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] における接続プールの動作を説明します。</span><span class="sxs-lookup"><span data-stu-id="4c5e6-108">Provides an overview of connection pooling and describes how connection pooling works in [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="4c5e6-109">OLE DB、ODBC、および Oracle 接続プール</span><span class="sxs-lookup"><span data-stu-id="4c5e6-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="4c5e6-110">.NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC、および .NET Framework Data Provider for Oracle の接続プールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4c5e6-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5e6-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c5e6-111">See Also</span></span>  
 [<span data-ttu-id="4c5e6-112">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="4c5e6-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="4c5e6-113">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="4c5e6-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
