---
title: "オブジェクトのコレクションの照会"
description: "コレクションをクエリする方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 11/30/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 74d6c1f080c3e70867f5d2f074315bd1d8486bf0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="query-a-collection-of-objects"></a><span data-ttu-id="81af0-104">オブジェクトのコレクションの照会</span><span class="sxs-lookup"><span data-stu-id="81af0-104">Query a collection of objects</span></span>
<span data-ttu-id="81af0-105">この例では、`Student` オブジェクトのリストに対してシンプルなクエリを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="81af0-105">This example shows how to perform a simple query over a list of `Student` objects.</span></span> <span data-ttu-id="81af0-106">各 `Student` オブジェクトには、生徒に関する基本情報と、4 回の試験での生徒の点数を表すリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="81af0-106">Each `Student` object contains some basic information about the student, and a list that represents the student's scores on four examinations.</span></span>  
  
 <span data-ttu-id="81af0-107">このアプリケーションは、同じ `students` データ ソースを使用する、このセクション内のその他多くの例のフレームワークとして機能します。</span><span class="sxs-lookup"><span data-stu-id="81af0-107">This application serves as the framework for many other examples in this section that use the same `students` data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81af0-108">例</span><span class="sxs-lookup"><span data-stu-id="81af0-108">Example</span></span>  
 <span data-ttu-id="81af0-109">次のクエリは、最初の試験で 90 点以上を取った学生を返します。</span><span class="sxs-lookup"><span data-stu-id="81af0-109">The following query returns the students who received a score of 90 or greater on their first exam.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#15](../../../samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
 <span data-ttu-id="81af0-110">このクエリは、実験用として意図的にシンプルに記述されています。</span><span class="sxs-lookup"><span data-stu-id="81af0-110">This query is intentionally simple to enable you to experiment.</span></span> <span data-ttu-id="81af0-111">たとえば、`where` 句でより多く条件を試したり、`orderby` 句を使用して結果を並べ替えたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="81af0-111">For example, you can try more conditions in the `where` clause, or use an `orderby` clause to sort the results.</span></span>  
  

## <a name="see-also"></a><span data-ttu-id="81af0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="81af0-112">See also</span></span>  
 [<span data-ttu-id="81af0-113">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="81af0-113">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="81af0-114">補間文字列</span><span class="sxs-lookup"><span data-stu-id="81af0-114">Interpolated Strings</span></span>](../language-reference/keywords/interpolated-strings.md)
