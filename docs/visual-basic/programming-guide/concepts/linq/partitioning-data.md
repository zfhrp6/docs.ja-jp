---
title: データのパーティション分割 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e4e6d6db07a520b97911de5388b8e42b7e1acc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="partitioning-data-visual-basic"></a><span data-ttu-id="c6d8b-102">データのパーティション分割 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6d8b-102">Partitioning Data (Visual Basic)</span></span>
<span data-ttu-id="c6d8b-103">LINQ におけるパーティション分割とは、要素を並べ替えずに入力シーケンスを 2 つのセクションに分割し、それらのセクションの 1 つを返す操作を指します。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="c6d8b-104">次の図は、文字のシーケンスに対して 3 つの異なるパーティション分割操作を実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="c6d8b-105">最初の操作では、シーケンスの最初の 3 つの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="c6d8b-106">2 番目の操作では、最初の 3 つの要素がスキップされ、残りの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="c6d8b-107">3 番目の操作では、シーケンスの最初の 2 つの要素がスキップされ、次の 3 つの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="c6d8b-108">![LINQ パーティション分割操作](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="c6d8b-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="c6d8b-109">次のセクションに、シーケンスのパーティション分割を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="c6d8b-110">演算子</span><span class="sxs-lookup"><span data-stu-id="c6d8b-110">Operators</span></span>  
  
|<span data-ttu-id="c6d8b-111">演算子名</span><span class="sxs-lookup"><span data-stu-id="c6d8b-111">Operator Name</span></span>|<span data-ttu-id="c6d8b-112">説明</span><span class="sxs-lookup"><span data-stu-id="c6d8b-112">Description</span></span>|<span data-ttu-id="c6d8b-113">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="c6d8b-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="c6d8b-114">説明</span><span class="sxs-lookup"><span data-stu-id="c6d8b-114">More Information</span></span>|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="c6d8b-115">Skip</span><span class="sxs-lookup"><span data-stu-id="c6d8b-115">Skip</span></span>|<span data-ttu-id="c6d8b-116">シーケンス内の指定した位置まで要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-116">Skips elements up to a specified position in a sequence.</span></span>|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6d8b-117">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="c6d8b-117">SkipWhile</span></span>|<span data-ttu-id="c6d8b-118">述語関数に基づき、条件を満たさない要素が出現する位置まで要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-118">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6d8b-119">Take</span><span class="sxs-lookup"><span data-stu-id="c6d8b-119">Take</span></span>|<span data-ttu-id="c6d8b-120">シーケンス内の指定した位置までの要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-120">Takes elements up to a specified position in a sequence.</span></span>|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c6d8b-121">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="c6d8b-121">TakeWhile</span></span>|<span data-ttu-id="c6d8b-122">述語関数に基づき、条件を満たさない要素が出現する位置までの要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-122">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="c6d8b-123">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="c6d8b-123">Query Expression Syntax Examples</span></span>  
  
### <a name="skip"></a><span data-ttu-id="c6d8b-124">Skip</span><span class="sxs-lookup"><span data-stu-id="c6d8b-124">Skip</span></span>  
 <span data-ttu-id="c6d8b-125">次のコード例では、`Skip`句、残りを返す前に文字列の配列内の最初の 4 つの文字列をスキップする Visual Basic で文字列配列。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-125">The following code example uses the `Skip` clause in Visual Basic to skip over the first four strings in an array of strings before returning the remaining strings in the array.</span></span>  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a><span data-ttu-id="c6d8b-126">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="c6d8b-126">SkipWhile</span></span>  
 <span data-ttu-id="c6d8b-127">次のコード例では、`Skip While`句、文字列の最初の文字は、配列内の文字列をスキップする Visual Basic では"a"です。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-127">The following code example uses the `Skip While` clause in Visual Basic to skip over the strings in an array while the first letter of the string is "a".</span></span> <span data-ttu-id="c6d8b-128">配列内の残りの文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-128">The remaining strings in the array are returned.</span></span>  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a><span data-ttu-id="c6d8b-129">Take</span><span class="sxs-lookup"><span data-stu-id="c6d8b-129">Take</span></span>  
 <span data-ttu-id="c6d8b-130">次のコード例では、`Take`を文字列の配列の最初の 2 つの文字列を返す Visual Basic での句。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-130">The following code example uses the `Take` clause in Visual Basic to return the first two strings in an array of strings.</span></span>  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a><span data-ttu-id="c6d8b-131">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="c6d8b-131">TakeWhile</span></span>  
 <span data-ttu-id="c6d8b-132">次のコード例では、`Take While`文字列を返す配列から文字列の長さが 5 個以下の Visual Basic での句。</span><span class="sxs-lookup"><span data-stu-id="c6d8b-132">The following code example uses the `Take While` clause in Visual Basic to return strings from an array while the length of the string is five or less.</span></span>  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c6d8b-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6d8b-133">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="c6d8b-134">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6d8b-134">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="c6d8b-135">Skip 句</span><span class="sxs-lookup"><span data-stu-id="c6d8b-135">Skip Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="c6d8b-136">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="c6d8b-136">Skip While Clause</span></span>](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="c6d8b-137">Take 句</span><span class="sxs-lookup"><span data-stu-id="c6d8b-137">Take Clause</span></span>](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="c6d8b-138">Take While 句</span><span class="sxs-lookup"><span data-stu-id="c6d8b-138">Take While Clause</span></span>](../../../../visual-basic/language-reference/queries/take-while-clause.md)
