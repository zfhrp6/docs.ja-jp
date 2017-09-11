---
title: "オブジェクトのコレクションの照会"
description: "コレクションをクエリする方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e08f2e5877ffe24f5a238ab19abb9760cb442f2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="58381-104">オブジェクトのコレクションの照会</span><span class="sxs-lookup"><span data-stu-id="58381-104">Query a collection of objects</span></span>
<span data-ttu-id="58381-105">この例では、`Student` オブジェクトのリストに対してシンプルなクエリを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="58381-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="58381-106">各 `Student` オブジェクトには、生徒に関する基本情報と、4 回の試験での生徒の点数を表すリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="58381-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="58381-107">このアプリケーションは、同じ `students` データ ソースを使用する、このセクション内のその他多くの例のフレームワークとして機能します。</span><span class="sxs-lookup"><span data-stu-id="58381-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58381-108">例</span><span class="sxs-lookup"><span data-stu-id="58381-108">Example</span></span>  
 <span data-ttu-id="58381-109">次のクエリは、最初の試験で 90 点以上を取った学生を返します。</span><span class="sxs-lookup"><span data-stu-id="58381-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 <span data-ttu-id="58381-110">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="58381-110">[!code-cs[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]</span></span>  
  
 <span data-ttu-id="58381-111">このクエリは、実験用として意図的にシンプルに記述されています。</span><span class="sxs-lookup"><span data-stu-id="58381-111">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="58381-112">たとえば、`where` 句でより多く条件を試したり、`orderby` 句を使用して結果を並べ替えたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="58381-112">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="58381-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="58381-113">See also</span></span>  
 [<span data-ttu-id="58381-114">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="58381-114">LINQ Query Expressions</span></span>](index.md)

