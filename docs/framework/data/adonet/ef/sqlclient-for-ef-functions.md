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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 08526aeebd01196c064154a35df267b8040df796
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sqlclient-for-entity-framework-functions"></a><span data-ttu-id="5673d-102">Entity Framework 用 SqlClient 関数</span><span class="sxs-lookup"><span data-stu-id="5673d-102">SqlClient for Entity Framework Functions</span></span>
<span data-ttu-id="5673d-103">Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) には、`System.DateTime` や `string` の操作を実行する関数の他に、数学計算および集計計算を実行する関数のセットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5673d-103">The .NET Framework Data Provider for SQL Server (SqlClient) for the Entity Framework provides a set of functions to perform mathematical and aggregation calculations, as well as functions to perform `System.DateTime` and `string` operations.</span></span> <span data-ttu-id="5673d-104">これらの関数は `SQLServer` 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="5673d-104">These functions are in the `SQLServer` namespace.</span></span>  
  
 <span data-ttu-id="5673d-105">任意のプロバイダーで動作するはずの機能の一覧は、次を参照してください。[正規関数](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)です。</span><span class="sxs-lookup"><span data-stu-id="5673d-105">For a list of functions that should work with any provider, see [Canonical Functions](../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="5673d-106">SQL Server 関数にどの正規関数のマップ方法については、次を参照してください。[概念モデル正規 SQL Server に関数マッピング](../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)です。</span><span class="sxs-lookup"><span data-stu-id="5673d-106">For information about how canonical functions map to SQL Server functions, see [Conceptual Model Canonical to SQL Server Functions Mapping](../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5673d-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5673d-107">In This Section</span></span>  
 [<span data-ttu-id="5673d-108">概念モデル正規 SQL Server の関数のマッピング</span><span class="sxs-lookup"><span data-stu-id="5673d-108">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
  
 [<span data-ttu-id="5673d-109">集計関数</span><span class="sxs-lookup"><span data-stu-id="5673d-109">Aggregate Functions</span></span>](../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
 [<span data-ttu-id="5673d-110">日付と時刻関数</span><span class="sxs-lookup"><span data-stu-id="5673d-110">Date and Time Functions</span></span>](../../../../../docs/framework/data/adonet/ef/date-and-time-functions.md)  
  
 [<span data-ttu-id="5673d-111">数学関数</span><span class="sxs-lookup"><span data-stu-id="5673d-111">Mathematical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/mathematical-functions.md)  
  
 [<span data-ttu-id="5673d-112">文字列関数</span><span class="sxs-lookup"><span data-stu-id="5673d-112">String Functions</span></span>](../../../../../docs/framework/data/adonet/ef/string-functions.md)  
  
 [<span data-ttu-id="5673d-113">システム関数</span><span class="sxs-lookup"><span data-stu-id="5673d-113">System Functions</span></span>](../../../../../docs/framework/data/adonet/ef/system-functions.md)  
  
## <a name="see-also"></a><span data-ttu-id="5673d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5673d-114">See Also</span></span>  
 [<span data-ttu-id="5673d-115">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="5673d-115">Entity SQL Reference</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="5673d-116">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="5673d-116">Entity SQL Overview</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
