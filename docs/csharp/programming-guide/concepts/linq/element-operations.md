---
title: "要素操作 (C#)"
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
ms.assetid: 283206c9-3246-4c48-b01a-d9de409a7231
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
ms.openlocfilehash: da747e884960c89fabc45d3761da92f913d66362
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="element-operations-c"></a><span data-ttu-id="581d0-102">要素操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="581d0-102">Element Operations (C#)</span></span>
<span data-ttu-id="581d0-103">要素操作では、シーケンスから単一の特定の要素が返されます。</span><span class="sxs-lookup"><span data-stu-id="581d0-103">Element operations return a single, specific element from a sequence.</span></span>  
  
 <span data-ttu-id="581d0-104">次のセクションでは、要素操作を実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="581d0-104">The standard query operator methods that perform element operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="581d0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="581d0-105">Methods</span></span>  
  
|<span data-ttu-id="581d0-106">メソッド名</span><span class="sxs-lookup"><span data-stu-id="581d0-106">Method Name</span></span>|<span data-ttu-id="581d0-107">説明</span><span class="sxs-lookup"><span data-stu-id="581d0-107">Description</span></span>|<span data-ttu-id="581d0-108">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="581d0-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="581d0-109">説明</span><span class="sxs-lookup"><span data-stu-id="581d0-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="581d0-110">ElementAt</span><span class="sxs-lookup"><span data-stu-id="581d0-110">ElementAt</span></span>|<span data-ttu-id="581d0-111">コレクション内の指定されたインデックス位置にある要素を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-111">Returns the element at a specified index in a collection.</span></span>|<span data-ttu-id="581d0-112">該当なし。</span><span class="sxs-lookup"><span data-stu-id="581d0-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ElementAt%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAt%2A?displayProperty=fullName>|  
|<span data-ttu-id="581d0-113">ElementAtOrDefault</span><span class="sxs-lookup"><span data-stu-id="581d0-113">ElementAtOrDefault</span></span>|<span data-ttu-id="581d0-114">コレクション内の指定したインデックス位置にある要素を返します。インデックスが範囲外の場合は既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-114">Returns the element at a specified index in a collection or a default value if the index is out of range.</span></span>|<span data-ttu-id="581d0-115">該当なし。</span><span class="sxs-lookup"><span data-stu-id="581d0-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.ElementAtOrDefault%2A?displayProperty=fullName>|  
|<span data-ttu-id="581d0-116">First</span><span class="sxs-lookup"><span data-stu-id="581d0-116">First</span></span>|<span data-ttu-id="581d0-117">コレクションの最初の要素、または条件を満たす最初の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-117">Returns the first element of a collection, or the first element that satisfies a condition.</span></span>|<span data-ttu-id="581d0-118">該当なし。</span><span class="sxs-lookup"><span data-stu-id="581d0-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.First%2A?displayProperty=fullName>|  
|<span data-ttu-id="581d0-119">FirstOrDefault</span><span class="sxs-lookup"><span data-stu-id="581d0-119">FirstOrDefault</span></span>|<span data-ttu-id="581d0-120">コレクションの最初の要素、または条件を満たす最初の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-120">Returns the first element of a collection, or the first element that satisfies a condition.</span></span> <span data-ttu-id="581d0-121">そのような要素が存在しない場合は、既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-121">Returns a default value if no such element exists.</span></span>|<span data-ttu-id="581d0-122">該当なし。</span><span class="sxs-lookup"><span data-stu-id="581d0-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.FirstOrDefault%60%601%28System.Linq.IQueryable%7B%60%600%7D%29?displayProperty=fullName>|  
|<span data-ttu-id="581d0-123">末尾</span><span class="sxs-lookup"><span data-stu-id="581d0-123">Last</span></span>|<span data-ttu-id="581d0-124">コレクションの最後の要素、または条件を満たす最後の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-124">Returns the last element of a collection, or the last element that satisfies a condition.</span></span>|<span data-ttu-id="581d0-125">該当なし。</span><span class="sxs-lookup"><span data-stu-id="581d0-125">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Last%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Last%2A?displayProperty=fullName>|  
|<span data-ttu-id="581d0-126">LastOrDefault</span><span class="sxs-lookup"><span data-stu-id="581d0-126">LastOrDefault</span></span>|<span data-ttu-id="581d0-127">コレクションの最後の要素、または条件を満たす最後の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-127">Returns the last element of a collection, or the last element that satisfies a condition.</span></span> <span data-ttu-id="581d0-128">そのような要素が存在しない場合は、既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-128">Returns a default value if no such element exists.</span></span>|<span data-ttu-id="581d0-129">該当なし。</span><span class="sxs-lookup"><span data-stu-id="581d0-129">Not applicable.</span></span>|<xref:System.Linq.Enumerable.LastOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LastOrDefault%2A?displayProperty=fullName>|  
|<span data-ttu-id="581d0-130">Single</span><span class="sxs-lookup"><span data-stu-id="581d0-130">Single</span></span>|<span data-ttu-id="581d0-131">コレクションの唯一の要素、または条件を満たす唯一の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-131">Returns the only element of a collection, or the only element that satisfies a condition.</span></span>|<span data-ttu-id="581d0-132">該当なし。</span><span class="sxs-lookup"><span data-stu-id="581d0-132">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Single%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Single%2A?displayProperty=fullName>|  
|<span data-ttu-id="581d0-133">SingleOrDefault</span><span class="sxs-lookup"><span data-stu-id="581d0-133">SingleOrDefault</span></span>|<span data-ttu-id="581d0-134">コレクションの唯一の要素、または条件を満たす唯一の要素を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-134">Returns the only element of a collection, or the only element that satisfies a condition.</span></span> <span data-ttu-id="581d0-135">そのような要素が存在しない場合、またはコレクションの要素が 1 つだけでない場合は、既定値を返します。</span><span class="sxs-lookup"><span data-stu-id="581d0-135">Returns a default value if no such element exists or the collection does not contain exactly one element.</span></span>|<span data-ttu-id="581d0-136">該当なし。</span><span class="sxs-lookup"><span data-stu-id="581d0-136">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SingleOrDefault%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SingleOrDefault%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="581d0-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="581d0-137">See Also</span></span>  
 <span data-ttu-id="581d0-138"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="581d0-138"><xref:System.Linq></span></span>   
 <span data-ttu-id="581d0-139">[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="581d0-139">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 [<span data-ttu-id="581d0-140">方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="581d0-140">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)

