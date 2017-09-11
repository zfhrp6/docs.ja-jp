---
title: "グループ化操作でのサブクエリの実行"
description: "グループ化操作でサブクエリを実行する方法。"
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 68acc07e0c33d042123d3cd403a73d58a7c3d245
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="perform-a-subquery-on-a-grouping-operation"></a><span data-ttu-id="13a93-104">グループ化操作でのサブクエリの実行</span><span class="sxs-lookup"><span data-stu-id="13a93-104">Perform a subquery on a grouping operation</span></span>

<span data-ttu-id="13a93-105">このトピックでは、ソース データを複数のグループに整理し、各グループに対して個別にサブクエリを実行するクエリを作成する方法を 2 つ紹介します。</span><span class="sxs-lookup"><span data-stu-id="13a93-105">This topic shows two different ways to create a query that orders the source data into groups, and then performs a subquery over each group individually.</span></span> <span data-ttu-id="13a93-106">各例の基本的な手法として、ソース要素のグループ化には、`newGroup` という名前の "*継続*" を使用し、`newGroup` に対する新しいサブクエリを生成します。</span><span class="sxs-lookup"><span data-stu-id="13a93-106">The basic technique in each example is to group the source elements by using a *continuation* named `newGroup`, and then generating a new subquery against `newGroup`.</span></span> <span data-ttu-id="13a93-107">このサブクエリは、外部クエリによって作成された新しい各グループに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="13a93-107">This subquery is run against each new group that is created by the outer query.</span></span> <span data-ttu-id="13a93-108">この例では、最終出力がグループではなく、匿名型のフラットなシーケンスであることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="13a93-108">Note that in this particular example the final output is not a group, but a flat sequence of anonymous types.</span></span>  
  
 <span data-ttu-id="13a93-109">グループ化する方法の詳細については、「[group 句](../language-reference/keywords/group-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13a93-109">For more information about how to group, see [group clause](../language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="13a93-110">継続の詳細については、「[into](../language-reference/keywords/into.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13a93-110">For more information about continuations, see [into](../language-reference/keywords/into.md).</span></span> <span data-ttu-id="13a93-111">次の例では、インメモリ データ構造をデータ ソースとして使用していますが、どの種類の LINQ データ ソースにも同じ原則が当てはまります。</span><span class="sxs-lookup"><span data-stu-id="13a93-111">The following example uses an in-memory data structure as the data source, but the same principles apply for any kind of LINQ data source.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13a93-112">例</span><span class="sxs-lookup"><span data-stu-id="13a93-112">Example</span></span> 

 > [!NOTE]
 > <span data-ttu-id="13a93-113">この例には、「[オブジェクトのコレクションの照会](query-a-collection-of-objects.md)」のサンプル コードで定義されているオブジェクトへの参照が含まれています。</span><span class="sxs-lookup"><span data-stu-id="13a93-113">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span>

 <span data-ttu-id="13a93-114">[!code-cs[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="13a93-114">[!code-cs[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]</span></span>  
   
## <a name="see-also"></a><span data-ttu-id="13a93-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="13a93-115">See also</span></span>  
 [<span data-ttu-id="13a93-116">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="13a93-116">LINQ Query Expressions</span></span>](index.md)

