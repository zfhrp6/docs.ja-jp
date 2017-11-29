---
title: USING (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c506484908d6b0ffe3a11e33b51d0bcc2d27c25c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-entity-sql"></a><span data-ttu-id="1f904-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1f904-102">USING (Entity SQL)</span></span>
<span data-ttu-id="1f904-103">クエリ式で使用する名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="1f904-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f904-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f904-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f904-105">引数</span><span class="sxs-lookup"><span data-stu-id="1f904-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="1f904-106">名前空間を修飾する短い別名。</span><span class="sxs-lookup"><span data-stu-id="1f904-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="1f904-107">任意の有効な名前空間。</span><span class="sxs-lookup"><span data-stu-id="1f904-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f904-108">例</span><span class="sxs-lookup"><span data-stu-id="1f904-108">Example</span></span>  
 <span data-ttu-id="1f904-109">次の Entity SQL クエリでは、USING 演算子を使用して、クエリ式に使用する名前空間が指定されています。</span><span class="sxs-lookup"><span data-stu-id="1f904-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="1f904-110">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1f904-110">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="1f904-111">」の手順に従って[する方法: PrimitiveType 結果が返されますそのクエリを実行する](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f904-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="1f904-112">次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="1f904-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="1f904-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f904-113">See Also</span></span>  
 [<span data-ttu-id="1f904-114">名前空間</span><span class="sxs-lookup"><span data-stu-id="1f904-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
 [<span data-ttu-id="1f904-115">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="1f904-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
