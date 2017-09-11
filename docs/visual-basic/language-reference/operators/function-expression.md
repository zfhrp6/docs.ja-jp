---
title: "関数式 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: c379ed1694f72243ccb8367d5b820803b4fcf190
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="c2388-102">Function 式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2388-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="c2388-103">パラメーターと関数のラムダ式を定義するコードを宣言します。</span><span class="sxs-lookup"><span data-stu-id="c2388-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2388-104">構文</span><span class="sxs-lookup"><span data-stu-id="c2388-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="c2388-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c2388-105">Parts</span></span>  
  
|<span data-ttu-id="c2388-106">用語</span><span class="sxs-lookup"><span data-stu-id="c2388-106">Term</span></span>|<span data-ttu-id="c2388-107">定義</span><span class="sxs-lookup"><span data-stu-id="c2388-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="c2388-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c2388-108">Optional.</span></span> <span data-ttu-id="c2388-109">このプロシージャのパラメーターを表すローカル変数名の一覧。</span><span class="sxs-lookup"><span data-stu-id="c2388-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="c2388-110">かっこは、リストが空の場合にも存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2388-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="c2388-111">参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)します。</span><span class="sxs-lookup"><span data-stu-id="c2388-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="c2388-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="c2388-112">Required.</span></span> <span data-ttu-id="c2388-113">1 つの式。</span><span class="sxs-lookup"><span data-stu-id="c2388-113">A single expression.</span></span> <span data-ttu-id="c2388-114">式の型は、関数の戻り値の型です。</span><span class="sxs-lookup"><span data-stu-id="c2388-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="c2388-115">必須です。</span><span class="sxs-lookup"><span data-stu-id="c2388-115">Required.</span></span> <span data-ttu-id="c2388-116">使用して値を返すステートメントの一覧、`Return`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="c2388-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="c2388-117">(参照[Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md))。返される値の型は、関数の戻り値の型です。</span><span class="sxs-lookup"><span data-stu-id="c2388-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2388-118">コメント</span><span class="sxs-lookup"><span data-stu-id="c2388-118">Remarks</span></span>  
 <span data-ttu-id="c2388-119">A*ラムダ式*を計算し、値を返し、名前を持たない関数です。</span><span class="sxs-lookup"><span data-stu-id="c2388-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="c2388-120">ラムダ式を使用する引数として使用する以外にデリゲート型を使用する任意の場所`RemoveHandler`します。</span><span class="sxs-lookup"><span data-stu-id="c2388-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="c2388-121">詳細については、デリゲート、およびデリゲートでのラムダ式を使用する、次を参照してください。 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)と[厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)します。</span><span class="sxs-lookup"><span data-stu-id="c2388-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="c2388-122">ラムダ式の構文</span><span class="sxs-lookup"><span data-stu-id="c2388-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="c2388-123">標準的な関数のラムダ式の構文に似ています。</span><span class="sxs-lookup"><span data-stu-id="c2388-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="c2388-124">相違点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c2388-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="c2388-125">ラムダ式には、名前がありません。</span><span class="sxs-lookup"><span data-stu-id="c2388-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="c2388-126">ラムダ式がなど、修飾子を持つことはできません`Overloads`または`Overrides`です。</span><span class="sxs-lookup"><span data-stu-id="c2388-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="c2388-127">ラムダ式は使用しないでください、`As`関数の戻り値の型を指定する句。</span><span class="sxs-lookup"><span data-stu-id="c2388-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="c2388-128">代わりに、型は、単一行のラムダ式の本体に評価される値または複数行のラムダ式の戻り値から推論されます。</span><span class="sxs-lookup"><span data-stu-id="c2388-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="c2388-129">たとえば、単一行のラムダ式の本体が`Where cust.City = "London"`、戻り値の型`Boolean`します。</span><span class="sxs-lookup"><span data-stu-id="c2388-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="c2388-130">単一行のラムダ式の本体は、ステートメントではなく、式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2388-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="c2388-131">本文は、関数プロシージャへの呼び出しがない sub プロシージャの呼び出しで構成できます。</span><span class="sxs-lookup"><span data-stu-id="c2388-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="c2388-132">データ型、またはすべてを推論する必要がありますかすべてパラメーターが指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2388-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="c2388-133">省略可能と Paramarray パラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="c2388-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="c2388-134">ジェネリック パラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="c2388-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2388-135">例</span><span class="sxs-lookup"><span data-stu-id="c2388-135">Example</span></span>  
 <span data-ttu-id="c2388-136">次の例では、単純なラムダ式を作成する&2; つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c2388-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="c2388-137">最初の使用、`Dim`関数の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2388-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="c2388-138">関数を呼び出すには、パラメーターの値で送信します。</span><span class="sxs-lookup"><span data-stu-id="c2388-138">To call the function, you send in a value for the parameter.</span></span>  
  
 <span data-ttu-id="c2388-139">[!code-vb[VbVbalrLambdas&#1;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2388-139">[!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]</span></span>  
  
 <span data-ttu-id="c2388-140">[!code-vb[VbVbalrLambdas&#2;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2388-140">[!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2388-141">例</span><span class="sxs-lookup"><span data-stu-id="c2388-141">Example</span></span>  
 <span data-ttu-id="c2388-142">またはを宣言し、同時に、関数を実行します。</span><span class="sxs-lookup"><span data-stu-id="c2388-142">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 <span data-ttu-id="c2388-143">[!code-vb[VbVbalrLambdas&#3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2388-143">[!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2388-144">例</span><span class="sxs-lookup"><span data-stu-id="c2388-144">Example</span></span>  
 <span data-ttu-id="c2388-145">引数をインクリメントし、値を返すラムダ式の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c2388-145">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="c2388-146">この例では、単一行および複数行のラムダ式の両方の構文、関数を示します。</span><span class="sxs-lookup"><span data-stu-id="c2388-146">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="c2388-147">例については、次を参照してください。[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。</span><span class="sxs-lookup"><span data-stu-id="c2388-147">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="c2388-148">[!code-vb[VbVbalrLambdas&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2388-148">[!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2388-149">例</span><span class="sxs-lookup"><span data-stu-id="c2388-149">Example</span></span>  
 <span data-ttu-id="c2388-150">ラムダ式では、多くのクエリ演算子の基本となる[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]、メソッド ベースのクエリで明示的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2388-150">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="c2388-151">次の例は、標準的な[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)]メソッド形式に、クエリの変換後にクエリします。</span><span class="sxs-lookup"><span data-stu-id="c2388-151">The following example shows a typical [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="c2388-152">クエリ メソッドの詳細については、次を参照してください。[クエリ](../../../visual-basic/language-reference/queries/queries.md)します。</span><span class="sxs-lookup"><span data-stu-id="c2388-152">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="c2388-153">標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)します。</span><span class="sxs-lookup"><span data-stu-id="c2388-153">For more information about standard query operators, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2388-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2388-154">See Also</span></span>  
 <span data-ttu-id="c2388-155">[Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="c2388-155">[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="c2388-156"> [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="c2388-156"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="c2388-157"> [演算子よぶ式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="c2388-157"> [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md) </span></span>  
<span data-ttu-id="c2388-158"> [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="c2388-158"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="c2388-159"> [値の比較](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="c2388-159"> [Value Comparisons](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="c2388-160"> [ブール式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="c2388-160"> [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span></span>  
<span data-ttu-id="c2388-161"> [場合演算子](../../../visual-basic/language-reference/operators/if-operator.md) </span><span class="sxs-lookup"><span data-stu-id="c2388-161"> [If Operator](../../../visual-basic/language-reference/operators/if-operator.md) </span></span>  
<span data-ttu-id="c2388-162"> [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="c2388-162"> [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span></span>

