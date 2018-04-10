---
title: Where 句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2572f513d00bc72e869cf28d382be799f7a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-visual-basic"></a><span data-ttu-id="1bf93-102">Where 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bf93-102">Where Clause (Visual Basic)</span></span>
<span data-ttu-id="1bf93-103">クエリのフィルター処理条件を指定します。</span><span class="sxs-lookup"><span data-stu-id="1bf93-103">Specifies the filtering condition for a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf93-104">構文</span><span class="sxs-lookup"><span data-stu-id="1bf93-104">Syntax</span></span>  
  
```  
Where condition  
```  
  
## <a name="parts"></a><span data-ttu-id="1bf93-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="1bf93-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="1bf93-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="1bf93-106">Required.</span></span> <span data-ttu-id="1bf93-107">コレクションの現在のアイテムの値を出力コレクションに含めるかどうかを決定する式。</span><span class="sxs-lookup"><span data-stu-id="1bf93-107">An expression that determines whether the values for the current item in the collection are included in the output collection.</span></span> <span data-ttu-id="1bf93-108">式を評価する、`Boolean`値またはのそれと同等、`Boolean`値。</span><span class="sxs-lookup"><span data-stu-id="1bf93-108">The expression must evaluate to a `Boolean` value or the equivalent of a `Boolean` value.</span></span> <span data-ttu-id="1bf93-109">条件の評価が場合`True`要素は、それ以外のクエリの結果に含まれている、要素が、クエリ結果から除外します。</span><span class="sxs-lookup"><span data-stu-id="1bf93-109">If the condition evaluates to `True`, the element is included in the query result; otherwise, the element is excluded from the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bf93-110">コメント</span><span class="sxs-lookup"><span data-stu-id="1bf93-110">Remarks</span></span>  
 <span data-ttu-id="1bf93-111">`Where`句では、特定の条件を満たす要素のみを選択してクエリのデータをフィルター処理することができます。</span><span class="sxs-lookup"><span data-stu-id="1bf93-111">The `Where` clause enables you to filter query data by selecting only elements that meet certain criteria.</span></span> <span data-ttu-id="1bf93-112">要素の値を持つが発生する、`Where`句を評価する`True`クエリの結果に含まれるその他の要素が除外されます。</span><span class="sxs-lookup"><span data-stu-id="1bf93-112">Elements whose values cause the `Where` clause to evaluate to `True` are included in the query result; other elements are excluded.</span></span> <span data-ttu-id="1bf93-113">式で使用されている、`Where`に句を評価する必要があります、`Boolean`またはのそれと同等、`Boolean`に評価される整数など`False`その値が 0 の場合。</span><span class="sxs-lookup"><span data-stu-id="1bf93-113">The expression that is used in a `Where` clause must evaluate to a `Boolean` or the equivalent of a `Boolean`, such as an Integer that evaluates to `False` when its value is zero.</span></span> <span data-ttu-id="1bf93-114">複数の式を組み合わせることができます、`Where`句などの論理演算子を使用して、 `And`、 `Or`、 `AndAlso`、 `OrElse`、 `Is`、および`IsNot`です。</span><span class="sxs-lookup"><span data-stu-id="1bf93-114">You can combine multiple expressions in a `Where` clause by using logical operators such as `And`, `Or`, `AndAlso`, `OrElse`, `Is`, and `IsNot`.</span></span>  
  
 <span data-ttu-id="1bf93-115">既定では、クエリ式は評価されませんがアクセスしない — たとえば、ときにデータ バインドまたはで反復されたり、`For`ループします。</span><span class="sxs-lookup"><span data-stu-id="1bf93-115">By default, query expressions are not evaluated until they are accessed—for example, when they are data-bound or iterated through in a `For` loop.</span></span> <span data-ttu-id="1bf93-116">その結果、`Where`句は、クエリがアクセスされるまでは評価されません。</span><span class="sxs-lookup"><span data-stu-id="1bf93-116">As a result, the `Where` clause is not evaluated until the query is accessed.</span></span> <span data-ttu-id="1bf93-117">外部で使用されるクエリに値があるかどうか、`Where`句で、適切な値が使用されるように、`Where`句、クエリの実行時にします。</span><span class="sxs-lookup"><span data-stu-id="1bf93-117">If you have values external to the query that are used in the `Where` clause, ensure that the appropriate value is used in the `Where` clause at the time the query is executed.</span></span> <span data-ttu-id="1bf93-118">クエリの実行の詳細については、次を参照してください。[書き込み、最初の LINQ クエリの](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。</span><span class="sxs-lookup"><span data-stu-id="1bf93-118">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
 <span data-ttu-id="1bf93-119">内で関数を呼び出すことができます、`Where`句をコレクション内の現在の要素から計算または値に対して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="1bf93-119">You can call functions within a `Where` clause to perform a calculation or operation on a value from the current element in the collection.</span></span> <span data-ttu-id="1bf93-120">関数を呼び出して、`Where`句には、それが定義されている場合の代わりにアクセスしたときの直前に実行するクエリ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1bf93-120">Calling a function in a `Where` clause can cause the query to be executed immediately when it is defined instead of when it is accessed.</span></span> <span data-ttu-id="1bf93-121">クエリの実行の詳細については、次を参照してください。[書き込み、最初の LINQ クエリの](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。</span><span class="sxs-lookup"><span data-stu-id="1bf93-121">For more information about query execution, see [Writing Your First LINQ Query](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf93-122">例</span><span class="sxs-lookup"><span data-stu-id="1bf93-122">Example</span></span>  
 <span data-ttu-id="1bf93-123">次のクエリ式は、`From`範囲変数を宣言する句`cust`各`Customer`内のオブジェクト、`customers`コレクション。</span><span class="sxs-lookup"><span data-stu-id="1bf93-123">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="1bf93-124">`Where`句では、範囲変数を使用して、顧客に指定した領域から出力を制限します。</span><span class="sxs-lookup"><span data-stu-id="1bf93-124">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="1bf93-125">`For Each`ループでは、クエリ結果の各顧客の会社名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1bf93-125">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="1bf93-126">例</span><span class="sxs-lookup"><span data-stu-id="1bf93-126">Example</span></span>  
 <span data-ttu-id="1bf93-127">次の例で`And`と`Or`論理演算子で、`Where`句。</span><span class="sxs-lookup"><span data-stu-id="1bf93-127">The following example uses `And` and `Or` logical operators in the `Where` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1bf93-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bf93-128">See Also</span></span>  
 [<span data-ttu-id="1bf93-129">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="1bf93-129">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="1bf93-130">クエリ</span><span class="sxs-lookup"><span data-stu-id="1bf93-130">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="1bf93-131">From 句</span><span class="sxs-lookup"><span data-stu-id="1bf93-131">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="1bf93-132">Select 句</span><span class="sxs-lookup"><span data-stu-id="1bf93-132">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="1bf93-133">For Each...Next ステートメント</span><span class="sxs-lookup"><span data-stu-id="1bf93-133">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
