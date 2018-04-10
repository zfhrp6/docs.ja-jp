---
title: where 句 (C# リファレンス)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0324346ee5e214bf467fcb522ef781c91fa1b76f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="08931-102">where 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="08931-102">where clause (C# Reference)</span></span>
<span data-ttu-id="08931-103">`where` 句をクエリ式で使用して、クエリ式で返されるデータ ソースの要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="08931-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="08931-104">ブール条件 (*述語*) を (範囲変数で参照される) 各ソース要素に適用し、指定した条件に該当するものを返します。</span><span class="sxs-lookup"><span data-stu-id="08931-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="08931-105">単一のクエリ式に複数の `where` 句を含めることができ、単一の句に複数の述語部分式を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="08931-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08931-106">例</span><span class="sxs-lookup"><span data-stu-id="08931-106">Example</span></span>  
 <span data-ttu-id="08931-107">次の例では、`where` 句で、5 未満の数値を除くすべての数値を除外します。</span><span class="sxs-lookup"><span data-stu-id="08931-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="08931-108">`where` 句を削除すると、データ ソースのすべての数値が返されます。</span><span class="sxs-lookup"><span data-stu-id="08931-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="08931-109">式 `num < 5` は、各要素に適用される述語です。</span><span class="sxs-lookup"><span data-stu-id="08931-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="08931-110">例</span><span class="sxs-lookup"><span data-stu-id="08931-110">Example</span></span>  
 <span data-ttu-id="08931-111">単一の `where` 句内には、[&&](../../../csharp/language-reference/operators/conditional-and-operator.md) および [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 演算子を使用して、必要な数の述語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="08931-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="08931-112">次の例のクエリでは、5 未満の偶数のみを選択するために 2 つの述語を指定します。</span><span class="sxs-lookup"><span data-stu-id="08931-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="08931-113">例</span><span class="sxs-lookup"><span data-stu-id="08931-113">Example</span></span>  
 <span data-ttu-id="08931-114">`where` 句には、ブール値を返す 1 つ以上のメソッドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="08931-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="08931-115">次の例の `where` 句では、範囲変数の現在の値が偶数であるか、奇数であるかを判断するためのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="08931-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="08931-116">コメント</span><span class="sxs-lookup"><span data-stu-id="08931-116">Remarks</span></span>  
 <span data-ttu-id="08931-117">`where` 句はフィルター メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="08931-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="08931-118">クエリ式のほぼどこにでも指定できますが、最初の句や最後の句にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="08931-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="08931-119">`where` 句は、ソース要素のフィルター処理をグループ化の前に行うか後に行うかによって、[group](../../../csharp/language-reference/keywords/group-clause.md) 句の前または後に指定できます。</span><span class="sxs-lookup"><span data-stu-id="08931-119">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="08931-120">指定した述語がデータ ソース内の要素に対して有効でない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="08931-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="08931-121">これは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] で提供される厳密な型チェックの 1 つの利点です。</span><span class="sxs-lookup"><span data-stu-id="08931-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="08931-122">コンパイル時に、`where` キーワードは <xref:System.Linq.Enumerable.Where%2A> 標準クエリ演算子メソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="08931-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08931-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="08931-123">See Also</span></span>  
 [<span data-ttu-id="08931-124">クエリ キーワード (LINQ)</span><span class="sxs-lookup"><span data-stu-id="08931-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="08931-125">from 句</span><span class="sxs-lookup"><span data-stu-id="08931-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="08931-126">select 句</span><span class="sxs-lookup"><span data-stu-id="08931-126">select clause</span></span>](../../../csharp/language-reference/keywords/select-clause.md)  
 [<span data-ttu-id="08931-127">データのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="08931-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)  
 [<span data-ttu-id="08931-128">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="08931-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="08931-129">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="08931-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
