---
title: "量指定子操作 (C#)"
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
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
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
ms.openlocfilehash: f82df05693dffec64bcbc66cc2c0b9db2a7deb20
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="quantifier-operations-c"></a><span data-ttu-id="a7424-102">量指定子操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="a7424-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="a7424-103">量指定子操作は、シーケンス内の要素の一部またはすべてが条件を満たしているかどうかを示す <xref:System.Boolean> 値を返します。</span><span class="sxs-lookup"><span data-stu-id="a7424-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="a7424-104">次の図は、2 つの異なるソース シーケンスに対する、2 つの異なる量指定子操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="a7424-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="a7424-105">最初の操作では、1 つ以上の要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。</span><span class="sxs-lookup"><span data-stu-id="a7424-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="a7424-106">2 番目の操作では、すべての要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。</span><span class="sxs-lookup"><span data-stu-id="a7424-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="a7424-107">![LINQ 量指定子操作](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="a7424-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="a7424-108">次のセクションでは、量指定子操作を実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a7424-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7424-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="a7424-109">Methods</span></span>  
  
|<span data-ttu-id="a7424-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="a7424-110">Method Name</span></span>|<span data-ttu-id="a7424-111">説明</span><span class="sxs-lookup"><span data-stu-id="a7424-111">Description</span></span>|<span data-ttu-id="a7424-112">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="a7424-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="a7424-113">説明</span><span class="sxs-lookup"><span data-stu-id="a7424-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="a7424-114">すべて</span><span class="sxs-lookup"><span data-stu-id="a7424-114">All</span></span>|<span data-ttu-id="a7424-115">シーケンス内のすべての要素が条件を満たしているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="a7424-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="a7424-116">該当なし。</span><span class="sxs-lookup"><span data-stu-id="a7424-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=fullName>|  
|<span data-ttu-id="a7424-117">どれでも可</span><span class="sxs-lookup"><span data-stu-id="a7424-117">Any</span></span>|<span data-ttu-id="a7424-118">シーケンス内のいずれかの要素が条件を満たしているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="a7424-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="a7424-119">該当なし。</span><span class="sxs-lookup"><span data-stu-id="a7424-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=fullName>|  
|<span data-ttu-id="a7424-120">内容</span><span class="sxs-lookup"><span data-stu-id="a7424-120">Contains</span></span>|<span data-ttu-id="a7424-121">指定した要素がシーケンスに格納されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="a7424-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="a7424-122">該当なし。</span><span class="sxs-lookup"><span data-stu-id="a7424-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName>|  
  
## <a name="see-also"></a><span data-ttu-id="a7424-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7424-123">See Also</span></span>  
 <span data-ttu-id="a7424-124"><xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="a7424-124"><xref:System.Linq></span></span>   
 <span data-ttu-id="a7424-125">[標準クエリ演算子の概要 (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="a7424-125">[Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
 <span data-ttu-id="a7424-126">[方法: 実行時に述語フィルターを動的に指定する](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span><span class="sxs-lookup"><span data-stu-id="a7424-126">[How to: Dynamically Specify Predicate Filters at Runtime](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md) </span></span>  
 [<span data-ttu-id="a7424-127">方法 : 指定された単語のセットを含む文章を照会する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a7424-127">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)

