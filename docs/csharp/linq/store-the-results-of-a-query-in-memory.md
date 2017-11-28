---
title: "クエリ結果をメモリに格納する"
description: "結果の格納方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.openlocfilehash: 86a9c2d464eac83cabb5faa68987ad580fc31248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="3d349-104">クエリ結果をメモリに格納する</span><span class="sxs-lookup"><span data-stu-id="3d349-104">Store the results of a query in memory</span></span>

<span data-ttu-id="3d349-105">クエリは、基本的に、データの取得方法と編成方法を指示するための一連の命令です。</span><span class="sxs-lookup"><span data-stu-id="3d349-105">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="3d349-106">結果の各項目は順次要求されるため、クエリは遅延実行されます。</span><span class="sxs-lookup"><span data-stu-id="3d349-106">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="3d349-107">`foreach` を使用して結果を反復すると、項目はアクセスのたびに返されます。</span><span class="sxs-lookup"><span data-stu-id="3d349-107">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="3d349-108">クエリを評価し、`foreach` のループを実行せずに結果を格納するには、クエリ変数で次のメソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3d349-108">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="3d349-109">クエリ結果を格納するときは、次の例に示すように、返されたコレクション オブジェクトを新しい変数に割り当てることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3d349-109">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d349-110">例</span><span class="sxs-lookup"><span data-stu-id="3d349-110">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]  
  

## <a name="see-also"></a><span data-ttu-id="3d349-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d349-111">See Also</span></span>  
 [<span data-ttu-id="3d349-112">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="3d349-112">LINQ Query Expressions</span></span>](index.md)
