---
title: オブジェクトのコレクションの照会
description: コレクションをクエリする方法。
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: c690da2ae59d2a9b34a5bd403bc54797c4e95fa0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="4bbf1-103">オブジェクトのコレクションの照会</span><span class="sxs-lookup"><span data-stu-id="4bbf1-103">Query a collection of objects</span></span>
<span data-ttu-id="4bbf1-104">この例では、`Student` オブジェクトのリストに対してシンプルなクエリを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4bbf1-104">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="4bbf1-105">各 `Student` オブジェクトには、生徒に関する基本情報と、4 回の試験での生徒の点数を表すリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4bbf1-105">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="4bbf1-106">このアプリケーションは、同じ `students` データ ソースを使用する、このセクション内のその他多くの例のフレームワークとして機能します。</span><span class="sxs-lookup"><span data-stu-id="4bbf1-106">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bbf1-107">例</span><span class="sxs-lookup"><span data-stu-id="4bbf1-107">Example</span></span>  
 <span data-ttu-id="4bbf1-108">次のクエリは、最初の試験で 90 点以上を取った学生を返します。</span><span class="sxs-lookup"><span data-stu-id="4bbf1-108">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="4bbf1-109">このクエリは、実験用として意図的にシンプルに記述されています。</span><span class="sxs-lookup"><span data-stu-id="4bbf1-109">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="4bbf1-110">たとえば、`where` 句でより多く条件を試したり、`orderby` 句を使用して結果を並べ替えたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4bbf1-110">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="4bbf1-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bbf1-111">See also</span></span>  
 [<span data-ttu-id="4bbf1-112">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="4bbf1-112">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="4bbf1-113">文字列補間</span><span class="sxs-lookup"><span data-stu-id="4bbf1-113">String interpolation</span></span>](../language-reference/tokens/interpolated.md)
