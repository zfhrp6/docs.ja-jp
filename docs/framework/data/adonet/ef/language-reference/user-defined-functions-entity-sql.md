---
title: "ユーザー定義関数 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: bf0592a3e88f4e8142f1fb0aeb1e7364d818d4ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="user-defined-functions-entity-sql"></a><span data-ttu-id="47b15-102">ユーザー定義関数 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="47b15-102">User-Defined Functions (Entity SQL)</span></span>
<span data-ttu-id="47b15-103">Entity SQL では、クエリ内でのユーザー定義関数の呼び出しがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="47b15-103">Entity SQL supports calling user-defined functions in a query.</span></span> <span data-ttu-id="47b15-104">関数をインライン クエリでこれらを定義することができます (を参照してください[する方法: ユーザー定義関数を呼び出す](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) または概念モデルの一部として (を参照してください[する方法: カスタム関数を概念モデルで定義](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f))。</span><span class="sxs-lookup"><span data-stu-id="47b15-104">You can define these functions inline with the query (see [How to: Call a User-Defined Function](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) or as part of the conceptual model (see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)).</span></span> <span data-ttu-id="47b15-105">Entity SQL コマンドを概念モデル関数が定義されている、 [DefiningExpression](http://msdn.microsoft.com/en-us/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e)の要素、[関数](http://msdn.microsoft.com/en-us/dc3beca7-55cf-4977-8db0-5064cdbab134)概念モデル内の要素。</span><span class="sxs-lookup"><span data-stu-id="47b15-105">Conceptual model functions are defined as an Entity SQL command in the [DefiningExpression](http://msdn.microsoft.com/en-us/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) element of a [Function](http://msdn.microsoft.com/en-us/dc3beca7-55cf-4977-8db0-5064cdbab134) element in the conceptual model.</span></span>  
  
 <span data-ttu-id="47b15-106">Entity SQL を使用すると、関数をクエリ コマンド自体で定義することができます。</span><span class="sxs-lookup"><span data-stu-id="47b15-106">Entity SQL enables you to define functions in the query command itself.</span></span> <span data-ttu-id="47b15-107">[関数](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md)演算子は、インライン関数を定義します。</span><span class="sxs-lookup"><span data-stu-id="47b15-107">The [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operator defines inline functions.</span></span> <span data-ttu-id="47b15-108">複数の関数を 1 つのコマンドで定義することができます。関数の署名が一意であれば、これら複数の関数に同じ名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="47b15-108">You can define multiple functions in a single command, and these functions can have the same function name, as long as the function signatures are unique.</span></span> <span data-ttu-id="47b15-109">詳細については、「 [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47b15-109">For more information, see [Function Overload Resolution](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47b15-110">参照</span><span class="sxs-lookup"><span data-stu-id="47b15-110">See Also</span></span>  
 [<span data-ttu-id="47b15-111">関数</span><span class="sxs-lookup"><span data-stu-id="47b15-111">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
