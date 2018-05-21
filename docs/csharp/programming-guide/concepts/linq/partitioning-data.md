---
title: データのパーティション分割 (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: 003e292979b1dc75baa298ea4bda7ef432d0f27b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="partitioning-data-c"></a><span data-ttu-id="2d32f-102">データのパーティション分割 (C#)</span><span class="sxs-lookup"><span data-stu-id="2d32f-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="2d32f-103">LINQ におけるパーティション分割とは、要素を並べ替えずに入力シーケンスを 2 つのセクションに分割し、それらのセクションの 1 つを返す操作を指します。</span><span class="sxs-lookup"><span data-stu-id="2d32f-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="2d32f-104">次の図は、文字のシーケンスに対して 3 つの異なるパーティション分割操作を実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="2d32f-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="2d32f-105">最初の操作では、シーケンスの最初の 3 つの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="2d32f-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="2d32f-106">2 番目の操作では、最初の 3 つの要素がスキップされ、残りの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="2d32f-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="2d32f-107">3 番目の操作では、シーケンスの最初の 2 つの要素がスキップされ、次の 3 つの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="2d32f-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="2d32f-108">![LINQ パーティション分割操作](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="2d32f-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="2d32f-109">次のセクションに、シーケンスのパーティション分割を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="2d32f-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="2d32f-110">演算子</span><span class="sxs-lookup"><span data-stu-id="2d32f-110">Operators</span></span>  
  
|<span data-ttu-id="2d32f-111">演算子名</span><span class="sxs-lookup"><span data-stu-id="2d32f-111">Operator Name</span></span>|<span data-ttu-id="2d32f-112">説明</span><span class="sxs-lookup"><span data-stu-id="2d32f-112">Description</span></span>|<span data-ttu-id="2d32f-113">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="2d32f-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="2d32f-114">説明</span><span class="sxs-lookup"><span data-stu-id="2d32f-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="2d32f-115">Skip</span><span class="sxs-lookup"><span data-stu-id="2d32f-115">Skip</span></span>|<span data-ttu-id="2d32f-116">シーケンス内の指定した位置まで要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="2d32f-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="2d32f-117">該当なし。</span><span class="sxs-lookup"><span data-stu-id="2d32f-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2d32f-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="2d32f-118">SkipWhile</span></span>|<span data-ttu-id="2d32f-119">述語関数に基づき、条件を満たさない要素が出現する位置まで要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="2d32f-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="2d32f-120">該当なし。</span><span class="sxs-lookup"><span data-stu-id="2d32f-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2d32f-121">Take</span><span class="sxs-lookup"><span data-stu-id="2d32f-121">Take</span></span>|<span data-ttu-id="2d32f-122">シーケンス内の指定した位置までの要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="2d32f-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="2d32f-123">該当なし。</span><span class="sxs-lookup"><span data-stu-id="2d32f-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2d32f-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="2d32f-124">TakeWhile</span></span>|<span data-ttu-id="2d32f-125">述語関数に基づき、条件を満たさない要素が出現する位置までの要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="2d32f-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="2d32f-126">該当なし。</span><span class="sxs-lookup"><span data-stu-id="2d32f-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="2d32f-127">参照</span><span class="sxs-lookup"><span data-stu-id="2d32f-127">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="2d32f-128">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="2d32f-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
