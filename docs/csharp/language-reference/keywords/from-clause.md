---
title: "from 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- from_CSharpKeyword
- from
dev_langs:
- CSharp
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
caps.latest.revision: 27
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
ms.openlocfilehash: f0165144acfa8d0928015e8222179f7e69f19644
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="from-clause-c-reference"></a><span data-ttu-id="6ba9c-102">from 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6ba9c-102">from clause (C# Reference)</span></span>
<span data-ttu-id="6ba9c-103">クエリ式は、`from` 句で始める必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-103">A query expression must begin with a `from` clause.</span></span> <span data-ttu-id="6ba9c-104">また、クエリ式にはサブクエリを含めることができます。サブクエリも `from` 句で始めます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-104">Additionally, a query expression can contain sub-queries, which also begin with a `from` clause.</span></span> <span data-ttu-id="6ba9c-105">`from` 句は次を指定します。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-105">The `from` clause specifies the following:</span></span>  
  
-   <span data-ttu-id="6ba9c-106">クエリまたはサブクエリを実行するデータ ソース。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-106">The data source on which the query or sub-query will be run.</span></span>  
  
-   <span data-ttu-id="6ba9c-107">ソース シーケンスの各要素を表す、ローカルの*範囲変数*。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-107">A local *range variable* that represents each element in the source sequence.</span></span>  
  
 <span data-ttu-id="6ba9c-108">範囲変数とデータ ソースの両方は厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-108">Both the range variable and the data source are strongly typed.</span></span> <span data-ttu-id="6ba9c-109">`from` 句で参照されるデータ ソースには、<xref:System.Collections.IEnumerable> 型、<xref:System.Collections.Generic.IEnumerable%601> 型、あるいは <xref:System.Linq.IQueryable%601> のような派生型が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-109">The data source referenced in the `from` clause must have a type of <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, or a derived type such as <xref:System.Linq.IQueryable%601>.</span></span>  
  
 <span data-ttu-id="6ba9c-110">次の例では、`numbers` はデータ ソースであり、`num` は範囲変数です。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-110">In the following example, `numbers` is the data source and `num` is the range variable.</span></span> <span data-ttu-id="6ba9c-111">[var](../../../csharp/language-reference/keywords/var.md) キーワードが使用されていても、両方の変数が厳密に型指定されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-111">Note that both variables are strongly typed even through the [var](../../../csharp/language-reference/keywords/var.md) keyword is used.</span></span>  
  
 <span data-ttu-id="6ba9c-112">[!code-cs[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6ba9c-112">[!code-cs[cscsrefQueryKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_1.cs)]</span></span>  
  
## <a name="the-range-variable"></a><span data-ttu-id="6ba9c-113">範囲変数</span><span class="sxs-lookup"><span data-stu-id="6ba9c-113">The Range Variable</span></span>  
 <span data-ttu-id="6ba9c-114">データ ソースが <xref:System.Collections.Generic.IEnumerable%601> を実装するとき、コンパイラは範囲変数の型を推測します。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-114">The compiler infers the type of the range variable when the data source implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="6ba9c-115">たとえば、ソースの型が `IEnumerable<Customer>` の場合、範囲変数は `Customer` ではないかと推測されます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-115">For example, if the source has a type of `IEnumerable<Customer>`, then the range variable is inferred to be `Customer`.</span></span> <span data-ttu-id="6ba9c-116">ソースが <xref:System.Collections.ArrayList> のような非ジェネリック `IEnumerable` 型のときにのみ、型を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-116">The only time that you must specify the type explicitly is when the source is a non-generic `IEnumerable` type such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="6ba9c-117">詳細については、「[How to: Query an ArrayList with LINQ](http://msdn.microsoft.com/library/c318b79a-fa4d-4de3-b62d-c1162beb267e)」(方法: LINQ を使用して ArrayList を照会する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-117">For more information, see [How to: Query an ArrayList with LINQ](http://msdn.microsoft.com/library/c318b79a-fa4d-4de3-b62d-c1162beb267e).</span></span>  
  
 <span data-ttu-id="6ba9c-118">前述の例では、`num` は型 `int` として推測されます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-118">In the previous example `num` is inferred to be of type `int`.</span></span> <span data-ttu-id="6ba9c-119">範囲変数は厳密に型指定されるため、範囲変数の上でメソッドを呼び出したり、他の操作で範囲変数を使用したりできます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-119">Because the range variable is strongly typed, you can call methods on it or use it in other operations.</span></span> <span data-ttu-id="6ba9c-120">たとえば、`select num` を記述する代わりに、`select num.ToString()` を記述し、クエリ式が整数ではなく文字列のシーケンスを返すようにできます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-120">For example, instead of writing `select num`, you could write `select num.ToString()` to cause the query expression to return a sequence of strings instead of integers.</span></span> <span data-ttu-id="6ba9c-121">あるいは、式でシーケンス 14、11、13、12、10 を返すように `select n + 10` を記述できます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-121">Or you could write `select n + 10` to cause the expression to return the sequence 14, 11, 13, 12, 10.</span></span> <span data-ttu-id="6ba9c-122">詳細については、「[select 句](../../../csharp/language-reference/keywords/select-clause.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-122">For more information, see [select clause](../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
 <span data-ttu-id="6ba9c-123">範囲変数は [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントの繰り返し変数に似ていますが、1 つだけ非常に重要な違いがあります。範囲変数がソースのデータを格納することは決してありません。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-123">The range variable is like an iteration variable in a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement except for one very important difference: a range variable never actually stores data from the source.</span></span> <span data-ttu-id="6ba9c-124">これは構文上の利便性のためです。クエリの実行時に何が起こるのかクエリで表現できます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-124">It just a syntactic convenience that enables the query to describe what will occur when the query is executed.</span></span> <span data-ttu-id="6ba9c-125">詳細については、「[LINQ クエリの概要 (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-125">For more information, see [Introduction to LINQ Queries (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="compound-from-clauses"></a><span data-ttu-id="6ba9c-126">複合 from 句</span><span class="sxs-lookup"><span data-stu-id="6ba9c-126">Compound from Clauses</span></span>  
 <span data-ttu-id="6ba9c-127">ソース シーケンスの各要素がそれ自体シーケンスになったり、それ自体にシーケンスが含まれたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-127">In some cases, each element in the source sequence may itself be either a sequence or contain a sequence.</span></span> <span data-ttu-id="6ba9c-128">たとえば、データ ソースが `IEnumerable<Student>` になることがあります。この場合、シーケンスの各学生オブジェクト参照にテストの点数の一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-128">For example, your data source may be an `IEnumerable<Student>` where each student object in the sequence contains a list of test scores.</span></span> <span data-ttu-id="6ba9c-129">各 `Student` 要素内の内部一覧にアクセスするには、複合 `from` 句を利用できます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-129">To access the inner list within each `Student` element, you can use compound `from` clauses.</span></span> <span data-ttu-id="6ba9c-130">この手法は、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントを入れ子にして使う場合に似ています。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-130">The technique is like using nested [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statements.</span></span> <span data-ttu-id="6ba9c-131">[where](../../../csharp/language-reference/keywords/partial-method.md) 句または [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) 句をいずれかの `from` 句に追加し、結果を絞り込むことができます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-131">You can add [where](../../../csharp/language-reference/keywords/partial-method.md) or [orderby](../../../csharp/language-reference/keywords/orderby-clause.md) clauses to either `from` clause to filter the results.</span></span> <span data-ttu-id="6ba9c-132">次は、`Student` オブジェクトのシーケンスの例です。テストの点数を表す整数の内部 `List` がそれぞれに含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-132">The following example shows a sequence of `Student` objects, each of which contains an inner `List` of integers representing test scores.</span></span> <span data-ttu-id="6ba9c-133">内部一覧にアクセスするには、複合 `from` 句を利用できます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-133">To access the inner list, use a compound `from` clause.</span></span> <span data-ttu-id="6ba9c-134">必要に応じて、2 つの `from` 句の間に句を挿入できます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-134">You can insert clauses between the two `from` clauses if necessary.</span></span>  
  
 <span data-ttu-id="6ba9c-135">[!code-cs[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6ba9c-135">[!code-cs[cscsrefQueryKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_2.cs)]</span></span>  
  
## <a name="using-multiple-from-clauses-to-perform-joins"></a><span data-ttu-id="6ba9c-136">複数の from 句を使用して結合を実行する</span><span class="sxs-lookup"><span data-stu-id="6ba9c-136">Using Multiple from Clauses to Perform Joins</span></span>  
 <span data-ttu-id="6ba9c-137">複合 `from` 句を使用し、単一データ ソースの内部コレクションにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-137">A compound `from` clause is used to access inner collections in a single data source.</span></span> <span data-ttu-id="6ba9c-138">ただし、個別データ ソースから補足クエリを生成する複数の `from` 句をクエリに含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-138">However, a query can also contain multiple `from` clauses that generate supplemental queries from independent data sources.</span></span> <span data-ttu-id="6ba9c-139">この手法では、[join 句](../../../csharp/language-reference/keywords/join-clause.md)で不可能な特定の結合操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-139">This technique enables you to perform certain types of join operations that are not possible by using the [join clause](../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
 <span data-ttu-id="6ba9c-140">2 つの `from` 句を使用し、2 つのデータ ソースの完全なクロス結合を作る様子を示したのが次の例です。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-140">The following example shows how two `from` clauses can be used to form a complete cross join of two data sources.</span></span>  
  
 <span data-ttu-id="6ba9c-141">[!code-cs[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="6ba9c-141">[!code-cs[cscsrefQueryKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/from-clause_3.cs)]</span></span>  
  
 <span data-ttu-id="6ba9c-142">複数の `from` 句を使用する結合操作の詳細については、「[方法 : カスタム結合操作を実行する](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ba9c-142">For more information about join operations that use multiple `from` clauses, see [How to: Perform Custom Join Operations](../../../csharp/programming-guide/linq-query-expressions/how-to-perform-custom-join-operations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ba9c-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ba9c-143">See Also</span></span>  
 <span data-ttu-id="6ba9c-144">[クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="6ba9c-144">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 [<span data-ttu-id="6ba9c-145">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="6ba9c-145">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)

