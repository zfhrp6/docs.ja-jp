---
title: "関数 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fb55fecc7c876fda5918418e353eaf327ce6c034
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="functions-entity-sql"></a><span data-ttu-id="e62fd-102">関数 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e62fd-102">Functions (Entity SQL)</span></span>
<span data-ttu-id="e62fd-103">Entity SQL では、ユーザー定義関数、正規の関数、およびプロバイダー固有の関数がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e62fd-103">Entity SQL supports user-defined functions, canonical functions, and provider-specific functions.</span></span> <span data-ttu-id="e62fd-104">ユーザー定義関数は、概念モデルまたはクエリでインラインで指定されます。</span><span class="sxs-lookup"><span data-stu-id="e62fd-104">User-defined functions are specified in the conceptual model or inline in the query.</span></span> <span data-ttu-id="e62fd-105">詳細については、次を参照してください。[ユーザー定義関数](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)です。</span><span class="sxs-lookup"><span data-stu-id="e62fd-105">For more information, see [User-Defined Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).</span></span>  
  
 <span data-ttu-id="e62fd-106">正規の関数は Entity Framework で定義済みであり、データ プロバイダーによってサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e62fd-106">Canonical functions are predefined in the Entity Framework and should be supported by data providers.</span></span> <span data-ttu-id="e62fd-107">プロバイダーによってサポートされていない関数を呼び出すと、Entity SQL コマンドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="e62fd-107">Entity SQL commands will fail if a user calls a function that is not supported by a provider.</span></span> <span data-ttu-id="e62fd-108">そのため、通常は、プロバイダー固有の名前空間にあるストア固有の関数よりも正規の関数が推奨されます。</span><span class="sxs-lookup"><span data-stu-id="e62fd-108">Therefore, canonical functions are generally recommended over store-specific functions, which are in a provider-specific namespace.</span></span> <span data-ttu-id="e62fd-109">詳細については、次を参照してください。[正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)です。</span><span class="sxs-lookup"><span data-stu-id="e62fd-109">For more information, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
 <span data-ttu-id="e62fd-110">Microsoft SQL クライアント マネージ プロバイダーは、プロバイダー固有の一連の関数を提供しています。</span><span class="sxs-lookup"><span data-stu-id="e62fd-110">The Microsoft SQL Client Managed Provider provides a set of provider-specific functions.</span></span> <span data-ttu-id="e62fd-111">詳細については、次を参照してください。 [Framework 用 SqlClient エンティティ関数](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)です。</span><span class="sxs-lookup"><span data-stu-id="e62fd-111">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e62fd-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e62fd-112">In This Section</span></span>  
 [<span data-ttu-id="e62fd-113">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="e62fd-113">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [<span data-ttu-id="e62fd-114">関数のオーバー ロードの解決</span><span class="sxs-lookup"><span data-stu-id="e62fd-114">Function Overload Resolution</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [<span data-ttu-id="e62fd-115">集計関数</span><span class="sxs-lookup"><span data-stu-id="e62fd-115">Aggregate Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a><span data-ttu-id="e62fd-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="e62fd-116">See Also</span></span>  
 [<span data-ttu-id="e62fd-117">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="e62fd-117">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
