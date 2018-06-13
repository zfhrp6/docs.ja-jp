---
title: 部分式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 602212e664fa3362742fb1ba0dc033610272d3af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603536"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="2dadc-102">部分式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2dadc-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="2dadc-103">パラメーターとサブルーチン ラムダ式を定義するコードを宣言します。</span><span class="sxs-lookup"><span data-stu-id="2dadc-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dadc-104">構文</span><span class="sxs-lookup"><span data-stu-id="2dadc-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="2dadc-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="2dadc-105">Parts</span></span>  
  
|<span data-ttu-id="2dadc-106">用語</span><span class="sxs-lookup"><span data-stu-id="2dadc-106">Term</span></span>|<span data-ttu-id="2dadc-107">定義</span><span class="sxs-lookup"><span data-stu-id="2dadc-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="2dadc-108">任意。</span><span class="sxs-lookup"><span data-stu-id="2dadc-108">Optional.</span></span> <span data-ttu-id="2dadc-109">プロシージャのパラメーターを表すローカル変数名の一覧。</span><span class="sxs-lookup"><span data-stu-id="2dadc-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="2dadc-110">かっこは、リストが空の場合にも存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dadc-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="2dadc-111">詳細については、次を参照してください。[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)です。</span><span class="sxs-lookup"><span data-stu-id="2dadc-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="2dadc-112">必須。</span><span class="sxs-lookup"><span data-stu-id="2dadc-112">Required.</span></span> <span data-ttu-id="2dadc-113">1 つのステートメント。</span><span class="sxs-lookup"><span data-stu-id="2dadc-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="2dadc-114">必須。</span><span class="sxs-lookup"><span data-stu-id="2dadc-114">Required.</span></span> <span data-ttu-id="2dadc-115">ステートメントの一覧。</span><span class="sxs-lookup"><span data-stu-id="2dadc-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2dadc-116">コメント</span><span class="sxs-lookup"><span data-stu-id="2dadc-116">Remarks</span></span>  
 <span data-ttu-id="2dadc-117">A*ラムダ式*名前がないサブルーチンは、1 つまたは複数のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="2dadc-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="2dadc-118">任意の場所、ラムダ式を使用することができますを使える、デリゲート型以外に引数として`RemoveHandler`です。</span><span class="sxs-lookup"><span data-stu-id="2dadc-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="2dadc-119">デリゲート、およびデリゲートでのラムダ式の使用に関する詳細については、次を参照してください。 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)と[厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)です。</span><span class="sxs-lookup"><span data-stu-id="2dadc-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="2dadc-120">ラムダ式の構文</span><span class="sxs-lookup"><span data-stu-id="2dadc-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="2dadc-121">標準のサブルーチンのラムダ式の構文に似ています。</span><span class="sxs-lookup"><span data-stu-id="2dadc-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="2dadc-122">相違点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2dadc-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="2dadc-123">ラムダ式には、名前がありません。</span><span class="sxs-lookup"><span data-stu-id="2dadc-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="2dadc-124">ラムダ式はなどの修飾子を持つことはできません`Overloads`または`Overrides`です。</span><span class="sxs-lookup"><span data-stu-id="2dadc-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="2dadc-125">単一行のラムダ式の本体は、ステートメント、式ではないをする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dadc-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="2dadc-126">本文は、sub プロシージャへの呼び出しがない、プロシージャの呼び出しを関数で構成できます。</span><span class="sxs-lookup"><span data-stu-id="2dadc-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="2dadc-127">ラムダ式では、すべてのパラメーターまたはデータ型を推論する必要がありますすべてパラメーターのどちらかを指定した必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dadc-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="2dadc-128">省略可能なと`ParamArray`パラメーターはラムダ式で許可されていません。</span><span class="sxs-lookup"><span data-stu-id="2dadc-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="2dadc-129">ジェネリック パラメーターは、ラムダ式では使用できません。</span><span class="sxs-lookup"><span data-stu-id="2dadc-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dadc-130">例</span><span class="sxs-lookup"><span data-stu-id="2dadc-130">Example</span></span>  
 <span data-ttu-id="2dadc-131">値をコンソールに出力するラムダ式の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2dadc-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="2dadc-132">この例では、単一行および複数行ラムダ式の両方の構文のサブルーチンを示します。</span><span class="sxs-lookup"><span data-stu-id="2dadc-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="2dadc-133">例については、次を参照してください。[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="2dadc-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2dadc-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="2dadc-134">See Also</span></span>  
 [<span data-ttu-id="2dadc-135">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="2dadc-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="2dadc-136">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="2dadc-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="2dadc-137">演算子および式</span><span class="sxs-lookup"><span data-stu-id="2dadc-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="2dadc-138">ステートメント</span><span class="sxs-lookup"><span data-stu-id="2dadc-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="2dadc-139">厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="2dadc-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
