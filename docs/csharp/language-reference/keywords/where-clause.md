---
title: "where 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereclause_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 97d7c16d6bf8048e621141fff52a47907881fd2f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="where-clause-c-reference"></a><span data-ttu-id="dc602-102">where 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="dc602-102">where clause (C# Reference)</span></span>
<span data-ttu-id="dc602-103">`where` 句をクエリ式で使用して、クエリ式で返されるデータ ソースの要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc602-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="dc602-104">ブール条件 (*述語*) を (範囲変数で参照される) 各ソース要素に適用し、指定した条件に該当するものを返します。</span><span class="sxs-lookup"><span data-stu-id="dc602-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="dc602-105">単一のクエリ式に複数の `where` 句を含めることができ、単一の句に複数の述語部分式を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="dc602-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc602-106">例</span><span class="sxs-lookup"><span data-stu-id="dc602-106">Example</span></span>  
 <span data-ttu-id="dc602-107">次の例では、`where` 句で、5 未満の数値を除くすべての数値を除外します。</span><span class="sxs-lookup"><span data-stu-id="dc602-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="dc602-108">`where` 句を削除すると、データ ソースのすべての数値が返されます。</span><span class="sxs-lookup"><span data-stu-id="dc602-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="dc602-109">式 `num < 5` は、各要素に適用される述語です。</span><span class="sxs-lookup"><span data-stu-id="dc602-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 <span data-ttu-id="dc602-110">[!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc602-110">[!code-cs[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc602-111">例</span><span class="sxs-lookup"><span data-stu-id="dc602-111">Example</span></span>  
 <span data-ttu-id="dc602-112">単一の `where` 句内には、[&&](../../../csharp/language-reference/operators/conditional-and-operator.md) および [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 演算子を使用して、必要な数の述語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="dc602-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="dc602-113">次の例のクエリでは、5 未満の偶数のみを選択するために 2 つの述語を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc602-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 <span data-ttu-id="dc602-114">[!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc602-114">[!code-cs[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc602-115">例</span><span class="sxs-lookup"><span data-stu-id="dc602-115">Example</span></span>  
 <span data-ttu-id="dc602-116">`where` 句には、ブール値を返す 1 つ以上のメソッドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="dc602-116">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="dc602-117">次の例の `where` 句では、範囲変数の現在の値が偶数であるか、奇数であるかを判断するためのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc602-117">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 <span data-ttu-id="dc602-118">[!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc602-118">[!code-cs[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc602-119">コメント</span><span class="sxs-lookup"><span data-stu-id="dc602-119">Remarks</span></span>  
 <span data-ttu-id="dc602-120">`where` 句はフィルター メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="dc602-120">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="dc602-121">クエリ式のほぼどこにでも指定できますが、最初の句や最後の句にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="dc602-121">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="dc602-122">`where` 句は、ソース要素のフィルター処理をグループ化の前に行うか後に行うかによって、[group](../../../csharp/language-reference/keywords/group-clause.md) 句の前または後に指定できます。</span><span class="sxs-lookup"><span data-stu-id="dc602-122">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="dc602-123">指定した述語がデータ ソース内の要素に対して有効でない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dc602-123">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="dc602-124">これは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] で提供される厳密な型チェックの 1 つの利点です。</span><span class="sxs-lookup"><span data-stu-id="dc602-124">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="dc602-125">コンパイル時に、`where` キーワードは <xref:System.Linq.Enumerable.Where%2A> 標準クエリ演算子メソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="dc602-125">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc602-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc602-126">See Also</span></span>  
 <span data-ttu-id="dc602-127">[クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="dc602-127">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="dc602-128">[from 句](../../../csharp/language-reference/keywords/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="dc602-128">[from clause](../../../csharp/language-reference/keywords/from-clause.md) </span></span>  
 <span data-ttu-id="dc602-129">[select 句](../../../csharp/language-reference/keywords/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="dc602-129">[select clause](../../../csharp/language-reference/keywords/select-clause.md) </span></span>  
 <span data-ttu-id="dc602-130">[データのフィルター処理](http://msdn.microsoft.com/library/cee88d0f-31aa-4c60-9452-cc122ed0057d) </span><span class="sxs-lookup"><span data-stu-id="dc602-130">[Filtering Data](http://msdn.microsoft.com/library/cee88d0f-31aa-4c60-9452-cc122ed0057d) </span></span>  
 <span data-ttu-id="dc602-131">[LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc602-131">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="dc602-132">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="dc602-132">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

