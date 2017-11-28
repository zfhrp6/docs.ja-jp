---
title: "データのパーティション分割 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32b95887e05767513dd818743dd1726149503b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-c"></a><span data-ttu-id="19a63-102">データのパーティション分割 (C#)</span><span class="sxs-lookup"><span data-stu-id="19a63-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="19a63-103">LINQ におけるパーティション分割とは、要素を並べ替えずに入力シーケンスを 2 つのセクションに分割し、それらのセクションの 1 つを返す操作を指します。</span><span class="sxs-lookup"><span data-stu-id="19a63-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="19a63-104">次の図は、文字のシーケンスに対して 3 つの異なるパーティション分割操作を実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="19a63-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="19a63-105">最初の操作では、シーケンスの最初の 3 つの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="19a63-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="19a63-106">2 番目の操作では、最初の 3 つの要素がスキップされ、残りの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="19a63-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="19a63-107">3 番目の操作では、シーケンスの最初の 2 つの要素がスキップされ、次の 3 つの要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="19a63-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="19a63-108">![LINQ パーティション分割操作](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="19a63-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="19a63-109">次のセクションに、シーケンスのパーティション分割を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="19a63-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="19a63-110">演算子</span><span class="sxs-lookup"><span data-stu-id="19a63-110">Operators</span></span>  
  
|<span data-ttu-id="19a63-111">演算子名</span><span class="sxs-lookup"><span data-stu-id="19a63-111">Operator Name</span></span>|<span data-ttu-id="19a63-112">説明</span><span class="sxs-lookup"><span data-stu-id="19a63-112">Description</span></span>|<span data-ttu-id="19a63-113">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="19a63-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="19a63-114">説明</span><span class="sxs-lookup"><span data-stu-id="19a63-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="19a63-115">Skip</span><span class="sxs-lookup"><span data-stu-id="19a63-115">Skip</span></span>|<span data-ttu-id="19a63-116">シーケンス内の指定した位置まで要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="19a63-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="19a63-117">該当なし。</span><span class="sxs-lookup"><span data-stu-id="19a63-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19a63-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="19a63-118">SkipWhile</span></span>|<span data-ttu-id="19a63-119">述語関数に基づき、条件を満たさない要素が出現する位置まで要素をスキップします。</span><span class="sxs-lookup"><span data-stu-id="19a63-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="19a63-120">該当なし。</span><span class="sxs-lookup"><span data-stu-id="19a63-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19a63-121">Take</span><span class="sxs-lookup"><span data-stu-id="19a63-121">Take</span></span>|<span data-ttu-id="19a63-122">シーケンス内の指定した位置までの要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="19a63-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="19a63-123">該当なし。</span><span class="sxs-lookup"><span data-stu-id="19a63-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="19a63-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="19a63-124">TakeWhile</span></span>|<span data-ttu-id="19a63-125">述語関数に基づき、条件を満たさない要素が出現する位置までの要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="19a63-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="19a63-126">該当なし。</span><span class="sxs-lookup"><span data-stu-id="19a63-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="19a63-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="19a63-127">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="19a63-128">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="19a63-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
