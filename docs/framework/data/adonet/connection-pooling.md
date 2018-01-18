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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7205bc307af6a4a9f307b84a7b3875b77dadb765
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="connection-pooling"></a><span data-ttu-id="bf941-102">接続プール</span><span class="sxs-lookup"><span data-stu-id="bf941-102">Connection Pooling</span></span>
<span data-ttu-id="bf941-103">データ ソースへの接続は時間のかかる処理です。</span><span class="sxs-lookup"><span data-stu-id="bf941-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="bf941-104">ADO.NET 接続を開くコストを最小限に抑えると呼ばれる最適化の手法を使用して*接続プーリング*、繰り返しタグと終了の接続のコストを最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="bf941-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="bf941-105">接続プールは、.NET Framework データ プロバイダーに応じて異なる処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="bf941-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf941-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bf941-106">In This Section</span></span>  
 [<span data-ttu-id="bf941-107">SQL Server の接続プール (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="bf941-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="bf941-108">接続プールの概要および [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] における接続プールの動作を説明します。</span><span class="sxs-lookup"><span data-stu-id="bf941-108">Provides an overview of connection pooling and describes how connection pooling works in [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="bf941-109">OLE DB、ODBC、および Oracle 接続プール</span><span class="sxs-lookup"><span data-stu-id="bf941-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="bf941-110">.NET Framework Data Provider for OLE DB、.NET Framework Data Provider for ODBC、および .NET Framework Data Provider for Oracle の接続プールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bf941-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf941-111">参照</span><span class="sxs-lookup"><span data-stu-id="bf941-111">See Also</span></span>  
 [<span data-ttu-id="bf941-112">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="bf941-112">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="bf941-113">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="bf941-113">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
