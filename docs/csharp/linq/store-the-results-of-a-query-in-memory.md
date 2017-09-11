---
title: "クエリ結果をメモリに格納する"
description: "結果の格納方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 5b863961-1750-4cf9-9607-acea5054d15a
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 35d908bde06ef55ba2dc93a73211f7be33b9332c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="store-the-results-of-a-query-in-memory"></a><span data-ttu-id="29c96-104">クエリ結果をメモリに格納する</span><span class="sxs-lookup"><span data-stu-id="29c96-104">Store the results of a query in memory</span></span>

<span data-ttu-id="29c96-105">クエリは、基本的に、データの取得方法と編成方法を指示するための一連の命令です。</span><span class="sxs-lookup"><span data-stu-id="29c96-105">A query is basically a set of instructions for how to retrieve and organize data.</span></span> <span data-ttu-id="29c96-106">結果の各項目は順次要求されるため、クエリは遅延実行されます。</span><span class="sxs-lookup"><span data-stu-id="29c96-106">Queries are executed lazily, as each subsequent item in the result is requested.</span></span> <span data-ttu-id="29c96-107">`foreach` を使用して結果を反復すると、項目はアクセスのたびに返されます。</span><span class="sxs-lookup"><span data-stu-id="29c96-107">When you use `foreach` to iterate the results, items are returned as accessed.</span></span> <span data-ttu-id="29c96-108">クエリを評価し、`foreach` のループを実行せずに結果を格納するには、クエリ変数で次のメソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="29c96-108">To evaluate a query and store its results without executing a `foreach` loop, just call one of the following methods on the query variable:</span></span>  
  
-   <xref:System.Linq.Enumerable.ToList%2A>  
  
-   <xref:System.Linq.Enumerable.ToArray%2A>  
  
-   <xref:System.Linq.Enumerable.ToDictionary%2A>  
  
-   <xref:System.Linq.Enumerable.ToLookup%2A>  
  
 <span data-ttu-id="29c96-109">クエリ結果を格納するときは、次の例に示すように、返されたコレクション オブジェクトを新しい変数に割り当てることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="29c96-109">We recommend that when you store the query results, you assign the returned collection object to a new variable as shown in the following example:</span></span>  
  
## <a name="example"></a><span data-ttu-id="29c96-110">例</span><span class="sxs-lookup"><span data-stu-id="29c96-110">Example</span></span>  
 <span data-ttu-id="29c96-111">[!code-cs[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="29c96-111">[!code-cs[csProgGuideLINQ#25](../../../samples/snippets/csharp/concepts/linq/how-to-store-the-results-of-a-query-in-memory_1.cs)]</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="29c96-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="29c96-112">See Also</span></span>  
 [<span data-ttu-id="29c96-113">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="29c96-113">LINQ Query Expressions</span></span>](index.md)

