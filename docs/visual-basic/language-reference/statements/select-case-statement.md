---
title: Select...Case ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 9d24b455d92cbd00b268df26283aab082b7703a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604576"
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="50bf2-102">Select...Case ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50bf2-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="50bf2-103">式の値に応じて、ステートメントのいくつかのグループのいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="50bf2-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50bf2-104">構文</span><span class="sxs-lookup"><span data-stu-id="50bf2-104">Syntax</span></span>  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="50bf2-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="50bf2-105">Parts</span></span>  
  
|<span data-ttu-id="50bf2-106">用語</span><span class="sxs-lookup"><span data-stu-id="50bf2-106">Term</span></span>|<span data-ttu-id="50bf2-107">定義</span><span class="sxs-lookup"><span data-stu-id="50bf2-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="50bf2-108">必須。</span><span class="sxs-lookup"><span data-stu-id="50bf2-108">Required.</span></span> <span data-ttu-id="50bf2-109">式。</span><span class="sxs-lookup"><span data-stu-id="50bf2-109">Expression.</span></span> <span data-ttu-id="50bf2-110">基本データ型のいずれかに評価される必要があります (`Boolean`、 `Byte`、 `Char`、 `Date`、 `Double`、 `Decimal`、 `Integer`、 `Long`、 `Object`、 `SByte`、 `Short`、`Single`、 `String`、 `UInteger`、 `ULong`、および`UShort`)。</span><span class="sxs-lookup"><span data-stu-id="50bf2-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="50bf2-111">必要な`Case`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="50bf2-111">Required in a `Case` statement.</span></span> <span data-ttu-id="50bf2-112">一致した値を表す式の句の一覧`testexpression`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="50bf2-113">複数の式の句は、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="50bf2-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="50bf2-114">それぞれの句は、次の形式のいずれかを実行できます。</span><span class="sxs-lookup"><span data-stu-id="50bf2-114">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="50bf2-115">-   *expression1* `To` *expression2*</span><span class="sxs-lookup"><span data-stu-id="50bf2-115">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="50bf2-116">-[ `Is` ] *comparisonoperator* *式*</span><span class="sxs-lookup"><span data-stu-id="50bf2-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="50bf2-117">-   *式*</span><span class="sxs-lookup"><span data-stu-id="50bf2-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="50bf2-118">使用して、`To`一致の範囲の境界を指定するキーワードの値を`testexpression`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="50bf2-119">値`expression1`の値以下である必要があります`expression2`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="50bf2-120">使用して、`Is`比較演算子でキーワード (`=`、 `<>`、 `<`、 `<=`、 `>`、または`>=`)、一致した値に制限を指定する`testexpression`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="50bf2-121">場合、`Is`キーワードが指定されていないが自動的にする前に挿入*comparisonoperator*です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="50bf2-122">のみを指定するフォーム`expression`の特殊なケースとして扱われる、 `Is` where を形成*comparisonoperator*等号 (=) は、(`=`)。</span><span class="sxs-lookup"><span data-stu-id="50bf2-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="50bf2-123">このフォームの評価は`testexpression`  = `expression`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="50bf2-124">内の式`expressionlist`はの型に暗黙的に変換できる任意のデータ型を指定できます`testexpression`と適切な`comparisonoperator`に使用されている 2 つの型が有効です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="50bf2-125">任意。</span><span class="sxs-lookup"><span data-stu-id="50bf2-125">Optional.</span></span> <span data-ttu-id="50bf2-126">1 つまたは複数のステートメント次`Case`実行されている場合`testexpression`で任意の句に一致する`expressionlist`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="50bf2-127">任意。</span><span class="sxs-lookup"><span data-stu-id="50bf2-127">Optional.</span></span> <span data-ttu-id="50bf2-128">1 つまたは複数のステートメント次`Case Else`実行されている場合`testexpression`で句と一致しません、`expressionlist`のいずれかの`Case`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="50bf2-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="50bf2-129">定義を終了、`Select`しています.`Case`構築します。</span><span class="sxs-lookup"><span data-stu-id="50bf2-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50bf2-130">コメント</span><span class="sxs-lookup"><span data-stu-id="50bf2-130">Remarks</span></span>  
 <span data-ttu-id="50bf2-131">場合`testexpression`と一致する`Case``expressionlist`句、その次のステートメント`Case`ステートメントは、次実行`Case`、 `Case Else`、または`End Select`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="50bf2-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="50bf2-132">次のステートメントのパスを制御し、`End Select`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="50bf2-133">場合`testexpression`と一致する、`expressionlist`うち 1 つ以上の句`Case`句、最初の一致の次のステートメントのみを実行します。</span><span class="sxs-lookup"><span data-stu-id="50bf2-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="50bf2-134">`Case Else`ステートメントを使用して導入、`elsestatements`間で一致するものが見つからない場合に実行する、`testexpression`と`expressionlist`の他の句`Case`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="50bf2-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="50bf2-135">必須ではありませんが、これをお勧めして、`Case Else`内のステートメント、`Select Case`構築処理に予期しない`testexpression`値。</span><span class="sxs-lookup"><span data-stu-id="50bf2-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="50bf2-136">ない場合は`Case``expressionlist`句に一致する`testexpression`がありません`Case Else`ステートメントでは、次のステートメントのコントロール パス`End Select`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="50bf2-137">複数の式または範囲を使用するには各`Case`句。</span><span class="sxs-lookup"><span data-stu-id="50bf2-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="50bf2-138">たとえば、次の行は有効です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  <span data-ttu-id="50bf2-139">`Is`で使用されるキーワード、`Case`と`Case Else`ステートメントが同じではありません、 [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)、オブジェクト参照の比較に使用されます。</span><span class="sxs-lookup"><span data-stu-id="50bf2-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="50bf2-140">範囲や文字の文字列の複数の式を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="50bf2-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="50bf2-141">次の例では、 `Case` 「リンゴ」に等しい、アルファベット順に「ナット」と「スープ」の値であるかの現在の値とまったく同じ値を含む任意の文字列と一致する`testItem`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="50bf2-142">設定は、`Option Compare`文字列比較に影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="50bf2-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="50bf2-143">`Option Compare Text`、文字列「リンゴ」と「リンゴ」比較結果が等しいかどうかが`Option Compare Binary`、そうでないです。</span><span class="sxs-lookup"><span data-stu-id="50bf2-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50bf2-144">A`Case`句を指定して複数のステートメントが動作と呼ばれる*ショート サーキット*です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="50bf2-145">Visual Basic は左から右への句を評価し、1 つの場合との一致を生成します。 `testexpression`、残りの句は評価されません。</span><span class="sxs-lookup"><span data-stu-id="50bf2-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="50bf2-146">ショート サーキットのパフォーマンスが向上する、すべての式で必要とする場合、予期しない結果を生成できる`expressionlist`に評価されます。</span><span class="sxs-lookup"><span data-stu-id="50bf2-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="50bf2-147">ショート サーキットの詳細については、次を参照してください。[ブール式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-147">For more information on short-circuiting, see [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="50bf2-148">場合、コード内で、`Case`または`Case Else`ステートメント ブロックがブロック内のステートメントでそれ以上実行する必要はありませんを使用して、ブロックを終了できますが、`Exit Select`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="50bf2-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="50bf2-149">ステートメントに制御を直ちに移しますこの`End Select`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="50bf2-150">`Select Case` 構造を入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="50bf2-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="50bf2-151">入れ子になった`Select Case`構築の対応する必要がありますが`End Select`ステートメント内の 1 つに完全に含まする必要がありますと`Case`または`Case Else`、外側のステートメント ブロック`Select Case`構築の内部で入れ子にされています。</span><span class="sxs-lookup"><span data-stu-id="50bf2-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50bf2-152">例</span><span class="sxs-lookup"><span data-stu-id="50bf2-152">Example</span></span>  
 <span data-ttu-id="50bf2-153">次の例では、`Select Case`構造を使用して、変数の値に対応する行を書き込みます。`number`です。</span><span class="sxs-lookup"><span data-stu-id="50bf2-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="50bf2-154">2 番目`Case`ステートメントには、現在の値に一致する値が含まれています。 `number`"6、8、包括的"の間、ステートメントを書き込むため、実行します。</span><span class="sxs-lookup"><span data-stu-id="50bf2-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="50bf2-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="50bf2-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [<span data-ttu-id="50bf2-156">End ステートメント</span><span class="sxs-lookup"><span data-stu-id="50bf2-156">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="50bf2-157">If...Then...Else ステートメント</span><span class="sxs-lookup"><span data-stu-id="50bf2-157">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="50bf2-158">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="50bf2-158">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="50bf2-159">Exit ステートメント</span><span class="sxs-lookup"><span data-stu-id="50bf2-159">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
