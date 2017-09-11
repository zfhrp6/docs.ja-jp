---
title: "select 句 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- select_CSharpKeyword
- select
dev_langs:
- CSharp
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: 19
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
ms.openlocfilehash: a505399eb79cbecbefcc53953329279a4abd92f6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="select-clause-c-reference"></a><span data-ttu-id="7ceea-102">select 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="7ceea-102">select clause (C# Reference)</span></span>
<span data-ttu-id="7ceea-103">クエリ式で、`select` 句は、クエリが実行されたときに生成される値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="7ceea-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="7ceea-104">結果は、以前のすべての句の評価と `select` 句自体の式に基づいています。</span><span class="sxs-lookup"><span data-stu-id="7ceea-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="7ceea-105">クエリ式は、`select` 句または [group](../../../csharp/language-reference/keywords/group-clause.md) 句のいずれかで終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ceea-105">A query expression must terminate with either a `select` clause or a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>  
  
 <span data-ttu-id="7ceea-106">次の例は、クエリ式での単純な `select` 句を示したものです。</span><span class="sxs-lookup"><span data-stu-id="7ceea-106">The following example shows a simple `select` clause in a query expression.</span></span>  
  
 <span data-ttu-id="7ceea-107">[!code-cs[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7ceea-107">[!code-cs[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]</span></span>  
  
 <span data-ttu-id="7ceea-108">`select` 句によって生成されるシーケンスの型は、クエリ変数 `queryHighScores` の型を決定します。</span><span class="sxs-lookup"><span data-stu-id="7ceea-108">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="7ceea-109">最も簡単なケースでは、`select` 句は、範囲変数だけを指定します。</span><span class="sxs-lookup"><span data-stu-id="7ceea-109">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="7ceea-110">これにより、返されるシーケンスにデータ ソースと同じ型の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7ceea-110">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="7ceea-111">詳細については、「[LINQ クエリ操作での型の関係](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ceea-111">For more information, see [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="7ceea-112">ただし、`select` 句は、ソース データを新しい型に変換する (または*投影*する) ための強力なメカニズムも提供します。</span><span class="sxs-lookup"><span data-stu-id="7ceea-112">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="7ceea-113">詳細については、「[LINQ によるデータ変換 (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ceea-113">For more information, see [Data Transformations with LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ceea-114">例</span><span class="sxs-lookup"><span data-stu-id="7ceea-114">Example</span></span>  
 <span data-ttu-id="7ceea-115">次の例は、`select` 句のすべての異なる形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="7ceea-115">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="7ceea-116">各クエリで、`select` 句と *クエリ変数* (`studentQuery1`、`studentQuery2`など) の型の関係に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7ceea-116">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>  
  
 <span data-ttu-id="7ceea-117">[!code-cs[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="7ceea-117">[!code-cs[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]</span></span>  
  
 <span data-ttu-id="7ceea-118">前の例の `studentQuery8` に示すように、返されるシーケンスの要素にソース要素のプロパティのサブセットのみを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="7ceea-118">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="7ceea-119">返されるシーケンスをできるだけ小さく維持することで、メモリ要件を減らし、クエリの実行の速度を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="7ceea-119">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="7ceea-120">これを行うには、`select` 句で匿名型を作成し、オブジェクト初期化子を使用して、ソース要素からの適切なプロパティで初期化します。</span><span class="sxs-lookup"><span data-stu-id="7ceea-120">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="7ceea-121">これを行う方法の例については、「[オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ceea-121">For an example of how to do this, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ceea-122">コメント</span><span class="sxs-lookup"><span data-stu-id="7ceea-122">Remarks</span></span>  
 <span data-ttu-id="7ceea-123">コンパイル時に、`select` 句は、<xref:System.Linq.Enumerable.Select%2A> 標準クエリ演算子へのメソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="7ceea-123">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ceea-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ceea-124">See Also</span></span>  
 <span data-ttu-id="7ceea-125">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7ceea-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7ceea-126">[クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="7ceea-126">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="7ceea-127">[from 句](../../../csharp/language-reference/keywords/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="7ceea-127">[from clause](../../../csharp/language-reference/keywords/from-clause.md) </span></span>  
 <span data-ttu-id="7ceea-128">[partial (メソッド) (C# リファレンス)](../../../csharp/language-reference/keywords/partial-method.md) </span><span class="sxs-lookup"><span data-stu-id="7ceea-128">[partial (Method) (C# Reference)](../../../csharp/language-reference/keywords/partial-method.md) </span></span>  
 <span data-ttu-id="7ceea-129">[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="7ceea-129">[Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="7ceea-130">[LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="7ceea-130">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="7ceea-131">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="7ceea-131">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)

