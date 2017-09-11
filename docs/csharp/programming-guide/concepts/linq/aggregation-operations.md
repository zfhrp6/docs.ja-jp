---
title: "集計処理 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6fc035e5-7639-48b8-bc7f-b093dd31b039
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6c453bdccdb3af026fe4f4fb79c6e33e44e7a8f0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="aggregation-operations-c"></a><span data-ttu-id="1c54c-102">集計処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="1c54c-102">Aggregation Operations (C#)</span></span>
<span data-ttu-id="1c54c-103">集計の操作では、値の集合体から単一の値が計算されます。</span><span class="sxs-lookup"><span data-stu-id="1c54c-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="1c54c-104">たとえば、1 か月分の毎日の気温値から 1 日あたりの平均の気温値を計算することが集計操作です。</span><span class="sxs-lookup"><span data-stu-id="1c54c-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="1c54c-105">次の図は、数値のシーケンスに対する 2 つの集計処理の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="1c54c-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="1c54c-106">最初の処理で数値が合計されます。</span><span class="sxs-lookup"><span data-stu-id="1c54c-106">The first operation sums the numbers.</span></span> <span data-ttu-id="1c54c-107">2 つ目の処理でシーケンスの最大値が返されます。</span><span class="sxs-lookup"><span data-stu-id="1c54c-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 <span data-ttu-id="1c54c-108">![LINQ の集計処理](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span><span class="sxs-lookup"><span data-stu-id="1c54c-108">![LINQ Aggregation Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")</span></span>  
  
 <span data-ttu-id="1c54c-109">次のセクションでは、集計処理を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="1c54c-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1c54c-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="1c54c-110">Methods</span></span>  
  
|<span data-ttu-id="1c54c-111">メソッド名</span><span class="sxs-lookup"><span data-stu-id="1c54c-111">Method Name</span></span>|<span data-ttu-id="1c54c-112">説明</span><span class="sxs-lookup"><span data-stu-id="1c54c-112">Description</span></span>|<span data-ttu-id="1c54c-113">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="1c54c-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="1c54c-114">説明</span><span class="sxs-lookup"><span data-stu-id="1c54c-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="1c54c-115">Aggregate</span><span class="sxs-lookup"><span data-stu-id="1c54c-115">Aggregate</span></span>|<span data-ttu-id="1c54c-116">コレクションの値に対してカスタム集計処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="1c54c-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="1c54c-117">該当なし。</span><span class="sxs-lookup"><span data-stu-id="1c54c-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=fullName>|  
|<span data-ttu-id="1c54c-118">平均</span><span class="sxs-lookup"><span data-stu-id="1c54c-118">Average</span></span>|<span data-ttu-id="1c54c-119">値のコレクションの平均値を計算します。</span><span class="sxs-lookup"><span data-stu-id="1c54c-119">Calculates the average value of a collection of values.</span></span>|<span data-ttu-id="1c54c-120">該当なし。</span><span class="sxs-lookup"><span data-stu-id="1c54c-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Average%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=fullName>|  
|<span data-ttu-id="1c54c-121">カウント</span><span class="sxs-lookup"><span data-stu-id="1c54c-121">Count</span></span>|<span data-ttu-id="1c54c-122">コレクションの要素数をカウントします。述語関数を満たす要素のみをカウントすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1c54c-122">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="1c54c-123">該当なし。</span><span class="sxs-lookup"><span data-stu-id="1c54c-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=fullName>|  
|<span data-ttu-id="1c54c-124">LongCount</span><span class="sxs-lookup"><span data-stu-id="1c54c-124">LongCount</span></span>|<span data-ttu-id="1c54c-125">大規模なコレクションの要素数をカウントします。述語関数を満たす要素のみをカウントすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1c54c-125">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|<span data-ttu-id="1c54c-126">該当なし。</span><span class="sxs-lookup"><span data-stu-id="1c54c-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=fullName>|  
|<span data-ttu-id="1c54c-127">最大</span><span class="sxs-lookup"><span data-stu-id="1c54c-127">Max</span></span>|<span data-ttu-id="1c54c-128">コレクション内の最大値を決定します。</span><span class="sxs-lookup"><span data-stu-id="1c54c-128">Determines the maximum value in a collection.</span></span>|<span data-ttu-id="1c54c-129">該当なし。</span><span class="sxs-lookup"><span data-stu-id="1c54c-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Max%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>|  
|<span data-ttu-id="1c54c-130">最小</span><span class="sxs-lookup"><span data-stu-id="1c54c-130">Min</span></span>|<span data-ttu-id="1c54c-131">コレクション内の最小値を決定します。</span><span class="sxs-lookup"><span data-stu-id="1c54c-131">Determines the minimum value in a collection.</span></span>|<span data-ttu-id="1c54c-132">該当なし。</span><span class="sxs-lookup"><span data-stu-id="1c54c-132">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Min%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>|  
|<span data-ttu-id="1c54c-133">Sum</span><span class="sxs-lookup"><span data-stu-id="1c54c-133">Sum</span></span>|<span data-ttu-id="1c54c-134">コレクション内にある値の合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="1c54c-134">Calculates the sum of the values in a collection.</span></span>|<span data-ttu-id="1c54c-135">該当なし。</span><span class="sxs-lookup"><span data-stu-id="1c54c-135">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="1c54c-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c54c-136">See Also</span></span>  
 <span data-ttu-id="1c54c-137"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="1c54c-137"><xref:System.Linq></span></span>   
 <span data-ttu-id="1c54c-138">[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="1c54c-138">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="1c54c-139">[方法: CSV テキスト ファイルの列値を計算する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md) </span><span class="sxs-lookup"><span data-stu-id="1c54c-139">[How to: Compute Column Values in a CSV Text File (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md) </span></span>  
 <span data-ttu-id="1c54c-140">[方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md) </span><span class="sxs-lookup"><span data-stu-id="1c54c-140">[How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md) </span></span>  
 [<span data-ttu-id="1c54c-141">方法: 一連のフォルダーの合計バイト数を問い合わせる (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1c54c-141">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)

