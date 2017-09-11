---
title: "(Visual Basic) のデータの並べ替え |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1870d401ffdeeb2452ace1b74a8fb70e19c9b9ed
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="019fe-102">データの並べ替え (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="019fe-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="019fe-103">並べ替え操作では、1 つまたは複数の属性に基づいてシーケンスの要素を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="019fe-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="019fe-104">並べ替えの第&1; 条件で、要素に対して一回目の並べ替えが実行されます。</span><span class="sxs-lookup"><span data-stu-id="019fe-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="019fe-105">第&2; 条件を指定すると、第&1; 条件で並べ替えられた各グループ内の要素を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="019fe-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="019fe-106">次の図は、文字のシーケンスでアルファベット順の並べ替え操作の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="019fe-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="019fe-107">![LINQ 並べ替え操作](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="019fe-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="019fe-108">次のセクションでは、データを並べ替える標準クエリ演算子のメソッドが一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="019fe-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="019fe-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="019fe-109">Methods</span></span>  
  
|<span data-ttu-id="019fe-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="019fe-110">Method Name</span></span>|<span data-ttu-id="019fe-111">説明</span><span class="sxs-lookup"><span data-stu-id="019fe-111">Description</span></span>|<span data-ttu-id="019fe-112">Visual Basic のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="019fe-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="019fe-113">説明</span><span class="sxs-lookup"><span data-stu-id="019fe-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="019fe-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="019fe-114">OrderBy</span></span>|<span data-ttu-id="019fe-115">値を昇順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="019fe-115">Sorts values in ascending order.</span></span>|`Order By`|<span data-ttu-id="019fe-116"><xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-116"><xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="019fe-117"><xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-117"><xref:System.Linq.Queryable.OrderBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="019fe-118">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="019fe-118">OrderByDescending</span></span>|<span data-ttu-id="019fe-119">値を降順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="019fe-119">Sorts values in descending order.</span></span>|`Order By … Descending`|<span data-ttu-id="019fe-120"><xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-120"><xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="019fe-121"><xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-121"><xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="019fe-122">ThenBy</span><span class="sxs-lookup"><span data-stu-id="019fe-122">ThenBy</span></span>|<span data-ttu-id="019fe-123">昇順で&2; 番目の並べ替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="019fe-123">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<span data-ttu-id="019fe-124"><xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-124"><xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="019fe-125"><xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-125"><xref:System.Linq.Queryable.ThenBy%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="019fe-126">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="019fe-126">ThenByDescending</span></span>|<span data-ttu-id="019fe-127">降順で、2 番目の並べ替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="019fe-127">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<span data-ttu-id="019fe-128"><xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-128"><xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="019fe-129"><xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-129"><xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=fullName></span></span>|  
|<span data-ttu-id="019fe-130">Reverse</span><span class="sxs-lookup"><span data-stu-id="019fe-130">Reverse</span></span>|<span data-ttu-id="019fe-131">コレクション内の要素の順序を反転します。</span><span class="sxs-lookup"><span data-stu-id="019fe-131">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="019fe-132">該当なし。</span><span class="sxs-lookup"><span data-stu-id="019fe-132">Not applicable.</span></span>|<span data-ttu-id="019fe-133"><xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-133"><xref:System.Linq.Enumerable.Reverse%2A?displayProperty=fullName></span></span><br /><br /> <span data-ttu-id="019fe-134"><xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="019fe-134"><xref:System.Linq.Queryable.Reverse%2A?displayProperty=fullName></span></span>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="019fe-135">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="019fe-135">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="019fe-136">プライマリの並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="019fe-136">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="019fe-137">プライマリの昇順の並べ替え</span><span class="sxs-lookup"><span data-stu-id="019fe-137">Primary Ascending Sort</span></span>  
 <span data-ttu-id="019fe-138">次の例では、使用して、`Order By`配列の文字列を文字列の長さ、昇順に並べ替える LINQ クエリに句。</span><span class="sxs-lookup"><span data-stu-id="019fe-138">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="019fe-139">プライマリの降順の並べ替え</span><span class="sxs-lookup"><span data-stu-id="019fe-139">Primary Descending Sort</span></span>  
 <span data-ttu-id="019fe-140">次の例では、使用する方法、`Order By Descending`を降順で、先頭の文字で文字列を並べ替える LINQ クエリ句で使用します。</span><span class="sxs-lookup"><span data-stu-id="019fe-140">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="019fe-141">2 番目の並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="019fe-141">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="019fe-142">セカンダリの昇順の並べ替え</span><span class="sxs-lookup"><span data-stu-id="019fe-142">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="019fe-143">次の例では、使用して、`Order By`並べ替えを実行する、プライマリとセカンダリの文字列の配列での LINQ クエリ句で使用します。</span><span class="sxs-lookup"><span data-stu-id="019fe-143">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="019fe-144">文字列は、長さで、主に、最初にどちらも昇順文字列の先頭文字で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="019fe-144">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="019fe-145">セカンダリ降順の並べ替え</span><span class="sxs-lookup"><span data-stu-id="019fe-145">Secondary Descending Sort</span></span>  
 <span data-ttu-id="019fe-146">次の例では、使用する方法、`Order By Descending`昇順、降順での&2; 番目の並べ替えでプライマリの並べ替えを実行する LINQ クエリ句で使用します。</span><span class="sxs-lookup"><span data-stu-id="019fe-146">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="019fe-147">文字列は、長さで、主に、最初に、文字列の先頭文字で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="019fe-147">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="019fe-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="019fe-148">See Also</span></span>  
 <span data-ttu-id="019fe-149"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="019fe-149"><xref:System.Linq></span></span>   
<span data-ttu-id="019fe-150"> [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span><span class="sxs-lookup"><span data-stu-id="019fe-150"> [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md) </span></span>  
<span data-ttu-id="019fe-151"> [Order By 句](../../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="019fe-151"> [Order By Clause](../../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="019fe-152"> [方法: クエリ結果を並べ替える](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="019fe-152"> [How to: Sort Query Results](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md) </span></span>  
<span data-ttu-id="019fe-153"> [方法: 並べ替えまたはフィルター テキスト データでは、任意の単語またはフィールド (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span><span class="sxs-lookup"><span data-stu-id="019fe-153"> [How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)</span></span>
