---
title: "Entity Framework 用 SqlClient 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71a3613c-b94e-494c-8ad8-90cf86ae0b87
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6fb244d25a61f0c842455d6f1d2e5eb2fd9ff6f9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-for-entity-framework-functions"></a><span data-ttu-id="5b700-102">Entity Framework 用 SqlClient 関数</span><span class="sxs-lookup"><span data-stu-id="5b700-102">SqlClient for Entity Framework Functions</span></span>
<span data-ttu-id="5b700-103">Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) には、`System.DateTime` や `string` の操作を実行する関数の他に、数学計算および集計計算を実行する関数のセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5b700-103">The .NET Framework Data Provider for SQL Server (SqlClient) for the Entity Framework provides a set of functions to perform mathematical and aggregation calculations, as well as functions to perform `System.DateTime` and `string` operations.</span></span> <span data-ttu-id="5b700-104">これらの関数は `SQLServer` 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="5b700-104">These functions are in the `SQLServer` namespace.</span></span>  
  
 <span data-ttu-id="5b700-105">任意のプロバイダーで動作するはずの機能の一覧は、次を参照してください。[正規関数](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)です。</span><span class="sxs-lookup"><span data-stu-id="5b700-105">For a list of functions that should work with any provider, see [Canonical Functions](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="5b700-106">SQL Server 関数にどの正規関数のマップ方法については、次を参照してください。[概念モデル正規 SQL Server に関数マッピング](../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)です。</span><span class="sxs-lookup"><span data-stu-id="5b700-106">For information about how canonical functions map to SQL Server functions, see [Conceptual Model Canonical to SQL Server Functions Mapping](../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5b700-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5b700-107">In This Section</span></span>  
 [<span data-ttu-id="5b700-108">概念モデル正規関数と SQL Server 関数とのマッピング</span><span class="sxs-lookup"><span data-stu-id="5b700-108">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
  
 [<span data-ttu-id="5b700-109">集計関数</span><span class="sxs-lookup"><span data-stu-id="5b700-109">Aggregate Functions</span></span>](../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
 [<span data-ttu-id="5b700-110">日付と時刻関数</span><span class="sxs-lookup"><span data-stu-id="5b700-110">Date and Time Functions</span></span>](../../../../../docs/framework/data/adonet/ef/date-and-time-functions.md)  
  
 [<span data-ttu-id="5b700-111">数学関数</span><span class="sxs-lookup"><span data-stu-id="5b700-111">Mathematical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/mathematical-functions.md)  
  
 [<span data-ttu-id="5b700-112">文字列関数</span><span class="sxs-lookup"><span data-stu-id="5b700-112">String Functions</span></span>](../../../../../docs/framework/data/adonet/ef/string-functions.md)  
  
 [<span data-ttu-id="5b700-113">システム関数</span><span class="sxs-lookup"><span data-stu-id="5b700-113">System Functions</span></span>](../../../../../docs/framework/data/adonet/ef/system-functions.md)  
  
## <a name="see-also"></a><span data-ttu-id="5b700-114">参照</span><span class="sxs-lookup"><span data-stu-id="5b700-114">See Also</span></span>  
 [<span data-ttu-id="5b700-115">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="5b700-115">Entity SQL Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="5b700-116">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="5b700-116">Entity SQL Overview</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
