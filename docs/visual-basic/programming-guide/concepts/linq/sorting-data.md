---
title: データの並べ替え (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: f52000d37df45c97754463de1e81cd523806e9c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646865"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="5f6c9-102">データの並べ替え (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f6c9-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="5f6c9-103">並べ替え操作では、1 つ以上の属性に基づいてシーケンスの要素を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="5f6c9-104">並べ替えの第 1 条件で、要素に対して一回目の並べ替えが実行されます。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="5f6c9-105">第 2 条件を指定すると、第 1 条件で並べ替えられた各グループ内の要素を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="5f6c9-106">次の図は、文字のシーケンスに対してアルファベット順の並べ替え操作を実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="5f6c9-107">![LINQ 並べ替え操作](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="5f6c9-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="5f6c9-108">次のセクションでは、データの並べ替えを実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f6c9-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="5f6c9-109">Methods</span></span>  
  
|<span data-ttu-id="5f6c9-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="5f6c9-110">Method Name</span></span>|<span data-ttu-id="5f6c9-111">説明</span><span class="sxs-lookup"><span data-stu-id="5f6c9-111">Description</span></span>|<span data-ttu-id="5f6c9-112">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="5f6c9-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="5f6c9-113">説明</span><span class="sxs-lookup"><span data-stu-id="5f6c9-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="5f6c9-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="5f6c9-114">OrderBy</span></span>|<span data-ttu-id="5f6c9-115">値を昇順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5f6c9-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="5f6c9-116">OrderByDescending</span></span>|<span data-ttu-id="5f6c9-117">値を降順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5f6c9-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="5f6c9-118">ThenBy</span></span>|<span data-ttu-id="5f6c9-119">2 番目の並べ替えを昇順で実行します。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5f6c9-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="5f6c9-120">ThenByDescending</span></span>|<span data-ttu-id="5f6c9-121">2 番目の並べ替えを降順で実行します。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5f6c9-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="5f6c9-122">Reverse</span></span>|<span data-ttu-id="5f6c9-123">コレクションの要素の順序を反転させます。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="5f6c9-124">該当なし。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="5f6c9-125">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="5f6c9-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="5f6c9-126">1 番目の並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="5f6c9-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="5f6c9-127">1 番目の並べ替え (昇順)</span><span class="sxs-lookup"><span data-stu-id="5f6c9-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="5f6c9-128">次の例は、LINQ クエリで `Order By` 句を使用して、配列内の文字列を文字列長に従って昇順に並べ替える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
' quick  
' brown  
' jumps  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="5f6c9-129">1 番目の並べ替え (降順)</span><span class="sxs-lookup"><span data-stu-id="5f6c9-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="5f6c9-130">次の例は、LINQ クエリで `Order By Descending` 句を使用して、文字列を最初の文字に従って降順に並べ替える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' quick  
' jumps  
' fox  
' brown  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="5f6c9-131">2 番目の並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="5f6c9-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="5f6c9-132">2 番目の並べ替え (昇順)</span><span class="sxs-lookup"><span data-stu-id="5f6c9-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="5f6c9-133">次の例は、LINQ クエリで `Order By` 句を使用して、配列内の文字列に対して 1 番目および 2 番目の並べ替えを実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="5f6c9-134">文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として、どちらも昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1)   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' brown  
' jumps  
' quick  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="5f6c9-135">2 番目の並べ替え (降順)</span><span class="sxs-lookup"><span data-stu-id="5f6c9-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="5f6c9-136">次の例は、LINQ クエリで `Order By Descending` 句を使用して、1 番目の並べ替えを昇順で実行し、2 番目の並べ替えを降順で実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="5f6c9-137">各文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="5f6c9-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```vb  
Dim words = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim sortQuery = From word In words   
                Order By word.Length, word.Substring(0, 1) Descending   
                Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In sortQuery  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' fox  
' the  
' quick  
' jumps  
' brown  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f6c9-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f6c9-138">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="5f6c9-139">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f6c9-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="5f6c9-140">Order By 句</span><span class="sxs-lookup"><span data-stu-id="5f6c9-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="5f6c9-141">方法: クエリ結果を並べ替える</span><span class="sxs-lookup"><span data-stu-id="5f6c9-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
 [<span data-ttu-id="5f6c9-142">方法: 並べ替えまたはフィルター テキスト データで任意の単語またはフィールド (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f6c9-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
