---
title: "Function 式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e1d9d1223b340b2172c12bd8c2f364e314e764b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="d3850-102">Function 式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3850-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="d3850-103">パラメーターと関数のラムダ式を定義するコードを宣言します。</span><span class="sxs-lookup"><span data-stu-id="d3850-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3850-104">構文</span><span class="sxs-lookup"><span data-stu-id="d3850-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="d3850-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="d3850-105">Parts</span></span>  
  
|<span data-ttu-id="d3850-106">用語</span><span class="sxs-lookup"><span data-stu-id="d3850-106">Term</span></span>|<span data-ttu-id="d3850-107">定義</span><span class="sxs-lookup"><span data-stu-id="d3850-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="d3850-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="d3850-108">Optional.</span></span> <span data-ttu-id="d3850-109">このプロシージャのパラメーターを表すローカル変数名の一覧。</span><span class="sxs-lookup"><span data-stu-id="d3850-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="d3850-110">かっこは、リストが空の場合にも存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3850-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="d3850-111">参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3850-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="d3850-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="d3850-112">Required.</span></span> <span data-ttu-id="d3850-113">1 つの式。</span><span class="sxs-lookup"><span data-stu-id="d3850-113">A single expression.</span></span> <span data-ttu-id="d3850-114">式の型は、関数の戻り値の型です。</span><span class="sxs-lookup"><span data-stu-id="d3850-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="d3850-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="d3850-115">Required.</span></span> <span data-ttu-id="d3850-116">使用して値を返すステートメントの一覧、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="d3850-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="d3850-117">(を参照してください[Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md))。返される値の型は、関数の戻り値の型です。</span><span class="sxs-lookup"><span data-stu-id="d3850-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3850-118">コメント</span><span class="sxs-lookup"><span data-stu-id="d3850-118">Remarks</span></span>  
 <span data-ttu-id="d3850-119">A*ラムダ式*を計算し、値を返します、名前を持たない関数です。</span><span class="sxs-lookup"><span data-stu-id="d3850-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="d3850-120">ラムダ式を使用する任意の場所として使用できます、デリゲート型以外に渡す引数`RemoveHandler`です。</span><span class="sxs-lookup"><span data-stu-id="d3850-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="d3850-121">デリゲート、およびデリゲートでのラムダ式の使用に関する詳細については、次を参照してください。 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)と[厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3850-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="d3850-122">ラムダ式の構文</span><span class="sxs-lookup"><span data-stu-id="d3850-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="d3850-123">ラムダ式の構文では、標準的な関数に似ています。</span><span class="sxs-lookup"><span data-stu-id="d3850-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="d3850-124">相違点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d3850-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="d3850-125">ラムダ式には、名前がありません。</span><span class="sxs-lookup"><span data-stu-id="d3850-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="d3850-126">ラムダ式ことも、修飾子など`Overloads`または`Overrides`です。</span><span class="sxs-lookup"><span data-stu-id="d3850-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="d3850-127">ラムダ式は使用しないで、`As`句を関数の戻り値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="d3850-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="d3850-128">代わりに、単一行のラムダ式の本体に評価される値または複数行ラムダ式の戻り値の型が推論されます。</span><span class="sxs-lookup"><span data-stu-id="d3850-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="d3850-129">たとえば、単一行のラムダ式の本体が`Where cust.City = "London"`、戻り値の型は`Boolean`します。</span><span class="sxs-lookup"><span data-stu-id="d3850-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="d3850-130">単一行のラムダ式の本体は、ステートメントではなく、式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3850-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="d3850-131">本文は、function プロシージャへの呼び出しが sub プロシージャへの呼び出しではないので構成できます。</span><span class="sxs-lookup"><span data-stu-id="d3850-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="d3850-132">データ型またはすべてを推論する必要がありますかすべてのパラメーターが指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3850-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="d3850-133">省略可能と Paramarray パラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="d3850-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="d3850-134">ジェネリック パラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="d3850-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3850-135">例</span><span class="sxs-lookup"><span data-stu-id="d3850-135">Example</span></span>  
 <span data-ttu-id="d3850-136">次の例では、単純なラムダ式を作成する 2 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d3850-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="d3850-137">最初の例で、`Dim`関数の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d3850-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="d3850-138">関数を呼び出すには、パラメーターの値で送信します。</span><span class="sxs-lookup"><span data-stu-id="d3850-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="d3850-139">例</span><span class="sxs-lookup"><span data-stu-id="d3850-139">Example</span></span>  
 <span data-ttu-id="d3850-140">また、宣言し、同時に関数を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d3850-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="d3850-141">例</span><span class="sxs-lookup"><span data-stu-id="d3850-141">Example</span></span>  
 <span data-ttu-id="d3850-142">その引数をインクリメントし、値を返すラムダ式の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d3850-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="d3850-143">この例では、単一行および複数行ラムダ式の両方の構文、関数を示します。</span><span class="sxs-lookup"><span data-stu-id="d3850-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="d3850-144">例については、次を参照してください。[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3850-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="d3850-145">例</span><span class="sxs-lookup"><span data-stu-id="d3850-145">Example</span></span>  
 <span data-ttu-id="d3850-146">ラムダ式のクエリ演算子の多くの基になる[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]、メソッド ベースのクエリで明示的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="d3850-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="d3850-147">次の例は、一般的な[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ、クエリの変換メソッドの形式に続きます。</span><span class="sxs-lookup"><span data-stu-id="d3850-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="d3850-148">クエリ メソッドの詳細については、次を参照してください。[クエリ](../../../visual-basic/language-reference/queries/queries.md)です。</span><span class="sxs-lookup"><span data-stu-id="d3850-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="d3850-149">標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)です。</span><span class="sxs-lookup"><span data-stu-id="d3850-149">For more information about standard query operators, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3850-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3850-150">See Also</span></span>  
 [<span data-ttu-id="d3850-151">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="d3850-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="d3850-152">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="d3850-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="d3850-153">演算子および式</span><span class="sxs-lookup"><span data-stu-id="d3850-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="d3850-154">ステートメント</span><span class="sxs-lookup"><span data-stu-id="d3850-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="d3850-155">値の比較</span><span class="sxs-lookup"><span data-stu-id="d3850-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="d3850-156">ブール式</span><span class="sxs-lookup"><span data-stu-id="d3850-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="d3850-157">If 演算子</span><span class="sxs-lookup"><span data-stu-id="d3850-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="d3850-158">厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="d3850-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
