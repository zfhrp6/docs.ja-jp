---
title: "Null 許容値型 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
dev_langs:
- VB
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 23
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 226ffb8a329e31576c9a8120940c683ad10a030b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="4e934-102">null 許容値型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e934-102">Nullable Value Types (Visual Basic)</span></span>
<span data-ttu-id="4e934-103">特定の状況で 定義済みの値がない値型を操作することがあります。</span><span class="sxs-lookup"><span data-stu-id="4e934-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="4e934-104">たとえば、データベース内のフィールドは、意味のある割り当てられた値を持つと、割り当てられた値がないとを区別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e934-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="4e934-105">値型は、通常の値または null 値のいずれかを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="4e934-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="4e934-106">このような拡張機能と呼ばれる、 *null 許容型*します。</span><span class="sxs-lookup"><span data-stu-id="4e934-106">Such an extension is called a *nullable type*.</span></span>  
  
 <span data-ttu-id="4e934-107">各 null 許容型がジェネリックから構築された<xref:System.Nullable%601>構造体</xref:System.Nullable%601>。</span><span class="sxs-lookup"><span data-stu-id="4e934-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="4e934-108">仕事に関連するアクティビティを追跡するデータベースを検討してください。</span><span class="sxs-lookup"><span data-stu-id="4e934-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="4e934-109">次の例は、null 許容型を構築`Boolean`を入力し、その型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="4e934-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="4e934-110">次の&3; つの方法では、宣言を記述できます。</span><span class="sxs-lookup"><span data-stu-id="4e934-110">You can write the declaration in three ways:</span></span>  
  
 <span data-ttu-id="4e934-111">[!code-vb[VbVbalrNullableValue&#1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4e934-111">[!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]</span></span>  
  
 <span data-ttu-id="4e934-112">変数`ridesBusToWork`の値を保持できる`True`の値`False`、またはすべてに値がありません。</span><span class="sxs-lookup"><span data-stu-id="4e934-112">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="4e934-113">初期の既定値値はありません、ここで可能性があることについては、いないまだに対して取得されたこの人。</span><span class="sxs-lookup"><span data-stu-id="4e934-113">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="4e934-114">これに対し、`False`情報を取得、ユーザーが仕事のバスをオーバーライドしていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="4e934-114">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>  
  
 <span data-ttu-id="4e934-115">変数とプロパティを宣言するには null 許容型と null 許容型の要素を持つ配列を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="4e934-115">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="4e934-116">プロシージャを宣言するには、パラメーターとして null 許容型およびから null 許容型を返すことができます、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="4e934-116">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>  
  
 <span data-ttu-id="4e934-117">配列などの参照型で null 許容型を構築することはできません、 `String`、またはクラスです。</span><span class="sxs-lookup"><span data-stu-id="4e934-117">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="4e934-118">基になる型は、値型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e934-118">The underlying type must be a value type.</span></span> <span data-ttu-id="4e934-119">詳細については、次を参照してください。[値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)します。</span><span class="sxs-lookup"><span data-stu-id="4e934-119">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="4e934-120">Null 許容型の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="4e934-120">Using a Nullable Type Variable</span></span>  
 <span data-ttu-id="4e934-121">Null 許容型の最も重要なメンバーは、その<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>プロパティ</xref:System.Nullable%601.Value%2A></xref:System.Nullable%601.HasValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e934-121">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="4e934-122">Null 許容型の変数の<xref:System.Nullable%601.HasValue%2A>変数が定義済みの値を含むかどうかがわかります</xref:System.Nullable%601.HasValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e934-122">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="4e934-123">場合<xref:System.Nullable%601.HasValue%2A>は`True`、 <xref:System.Nullable%601.Value%2A>.</xref:System.Nullable%601.Value%2A>から値を読み取ることができます</xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="4e934-123">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="4e934-124">両方<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>は`ReadOnly`プロパティ</xref:System.Nullable%601.Value%2A></xref:System.Nullable%601.HasValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e934-124">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>  
  
### <a name="default-values"></a><span data-ttu-id="4e934-125">既定値</span><span class="sxs-lookup"><span data-stu-id="4e934-125">Default Values</span></span>  
 <span data-ttu-id="4e934-126">Null 許容型を持つ変数を宣言するときにその<xref:System.Nullable%601.HasValue%2A>プロパティには、既定値は`False`</xref:System.Nullable%601.HasValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e934-126">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="4e934-127">つまり、既定では、変数がない、基になる値型の既定値ではなく、定義済みの値。</span><span class="sxs-lookup"><span data-stu-id="4e934-127">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="4e934-128">次の例では、変数`numberOfChildren`最初に値を持たない値が定義されても、既定の`Integer`型は 0 です。</span><span class="sxs-lookup"><span data-stu-id="4e934-128">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>  
  
 <span data-ttu-id="4e934-129">[!code-vb[VbVbalrNullableValue&#2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4e934-129">[!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]</span></span>  
  
 <span data-ttu-id="4e934-130">Null 値は、未定義または未知の値を指定すると便利です。</span><span class="sxs-lookup"><span data-stu-id="4e934-130">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="4e934-131">場合`numberOfChildren`として宣言されていた`Integer`がなくなることは、情報が現在使用できないことを示す値。</span><span class="sxs-lookup"><span data-stu-id="4e934-131">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>  
  
### <a name="storing-values"></a><span data-ttu-id="4e934-132">値を格納します。</span><span class="sxs-lookup"><span data-stu-id="4e934-132">Storing Values</span></span>  
 <span data-ttu-id="4e934-133">一般的な方法で変数または null 許容型のプロパティ値を格納します。</span><span class="sxs-lookup"><span data-stu-id="4e934-133">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="4e934-134">次の例では、その値を変数に代入`numberOfChildren`前の例で宣言します。</span><span class="sxs-lookup"><span data-stu-id="4e934-134">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>  
  
 <span data-ttu-id="4e934-135">[!code-vb[VbVbalrNullableValue&#3;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="4e934-135">[!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]</span></span>  
  
 <span data-ttu-id="4e934-136">変数または null 許容型のプロパティには定義済みの値がある場合、値を割り当てる必要があるの初期状態に戻すことが発生することができます。</span><span class="sxs-lookup"><span data-stu-id="4e934-136">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="4e934-137">変数またはプロパティを設定して、これを行う`Nothing`次の例を示します。</span><span class="sxs-lookup"><span data-stu-id="4e934-137">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>  
  
 <span data-ttu-id="4e934-138">[!code-vb[VbVbalrNullableValue&4;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="4e934-138">[!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e934-139">割り当てることはできます`Nothing`null 許容型の変数をテストできません`Nothing`等号 (=) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="4e934-139">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="4e934-140">比較に等号 (=) を使用して`someVar = Nothing`、常に評価`Nothing`します。</span><span class="sxs-lookup"><span data-stu-id="4e934-140">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="4e934-141">変数をテストして<xref:System.Nullable%601.HasValue%2A>プロパティを`False`、またはを使用してテスト、`Is`または`IsNot`演算子</xref:System.Nullable%601.HasValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e934-141">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>  
  
### <a name="retrieving-values"></a><span data-ttu-id="4e934-142">値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4e934-142">Retrieving Values</span></span>  
 <span data-ttu-id="4e934-143">Null 許容型の変数の値を取得するには、テストしてください、<xref:System.Nullable%601.HasValue%2A>プロパティに値を使用していることを確認します</xref:System.Nullable%601.HasValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e934-143">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="4e934-144">値を読み取るしようとする場合と<xref:System.Nullable%601.HasValue%2A>は`False`、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]スロー、<xref:System.InvalidOperationException>例外</xref:System.InvalidOperationException></xref:System.Nullable%601.HasValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="4e934-144">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="4e934-145">次の例では、変数を読み取ることをお勧め`numberOfChildren`上の例です。</span><span class="sxs-lookup"><span data-stu-id="4e934-145">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>  
  
 <span data-ttu-id="4e934-146">[!code-vb[VbVbalrNullableValue&#5;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="4e934-146">[!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]</span></span>  
  
## <a name="comparing-nullable-types"></a><span data-ttu-id="4e934-147">Null 許容型を比較します。</span><span class="sxs-lookup"><span data-stu-id="4e934-147">Comparing Nullable Types</span></span>  
 <span data-ttu-id="4e934-148">Null 許容型と`Boolean`ブール式で変数が使用を定義できます。 `True`、 `False`、または`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="4e934-148">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="4e934-149">次の真理値表は、`And`と`Or`です。</span><span class="sxs-lookup"><span data-stu-id="4e934-149">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="4e934-150">`b1`と`b2`これで&3; つの値がある&9; つの組み合わせを評価します。</span><span class="sxs-lookup"><span data-stu-id="4e934-150">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>  
  
|<span data-ttu-id="4e934-151">b1</span><span class="sxs-lookup"><span data-stu-id="4e934-151">b1</span></span>|<span data-ttu-id="4e934-152">b2</span><span class="sxs-lookup"><span data-stu-id="4e934-152">b2</span></span>|<span data-ttu-id="4e934-153">b1 および b2</span><span class="sxs-lookup"><span data-stu-id="4e934-153">b1 And b2</span></span>|<span data-ttu-id="4e934-154">b1 または b2</span><span class="sxs-lookup"><span data-stu-id="4e934-154">b1 Or b2</span></span>|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 <span data-ttu-id="4e934-155">ブール型の変数または式の値が`Nothing`はどちらも`true`も`false`です。</span><span class="sxs-lookup"><span data-stu-id="4e934-155">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="4e934-156">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4e934-156">Consider the following example.</span></span>  
  
 <span data-ttu-id="4e934-157">[!code-vb[VbVbalrNullableValue&6;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="4e934-157">[!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]</span></span>  
  
 <span data-ttu-id="4e934-158">この例では`b1 And b2`に評価`Nothing`します。</span><span class="sxs-lookup"><span data-stu-id="4e934-158">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="4e934-159">その結果、`Else`句が各実行`If`ステートメント、および、出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4e934-159">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
> <span data-ttu-id="4e934-160"> `AndAlso``OrElse`、1 つ目の評価が、2 番目のオペランドを評価する必要がありますなるショート サーキット評価、`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="4e934-160"> `AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>  
  
## <a name="propagation"></a><span data-ttu-id="4e934-161">伝達</span><span class="sxs-lookup"><span data-stu-id="4e934-161">Propagation</span></span>  
 <span data-ttu-id="4e934-162">算術演算子、比較、shift キー、または種類の操作のオペランドの一方または両方が null 許容型の場合は、操作の結果も null 値を許容できます。</span><span class="sxs-lookup"><span data-stu-id="4e934-162">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="4e934-163">両方のオペランドが値ではない`Nothing`がどちらも場合と同様に、オペランドの基になる値で、操作を実行、null 許容型です。</span><span class="sxs-lookup"><span data-stu-id="4e934-163">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="4e934-164">次の例では、変数`compare1`と`sum1`は暗黙的に型指定されています。</span><span class="sxs-lookup"><span data-stu-id="4e934-164">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="4e934-165">上にマウス ポインターを置く場合、コンパイラは、それらの両方に対して null 許容型を推測が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e934-165">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>  
  
 <span data-ttu-id="4e934-166">[!code-vb[VbVbalrNullableValue&#7;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="4e934-166">[!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]</span></span>  
  
 <span data-ttu-id="4e934-167">1 つまたは両方のオペランドの値であれば`Nothing`、結果になります`Nothing`します。</span><span class="sxs-lookup"><span data-stu-id="4e934-167">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>  
  
 <span data-ttu-id="4e934-168">[!code-vb[VbVbalrNullableValue&#8;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="4e934-168">[!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]</span></span>  
  
## <a name="using-nullable-types-with-data"></a><span data-ttu-id="4e934-169">Null 許容型のデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="4e934-169">Using Nullable Types with Data</span></span>  
 <span data-ttu-id="4e934-170">データベースは、null 許容型を使用する最も重要な場所の&1; つです。</span><span class="sxs-lookup"><span data-stu-id="4e934-170">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="4e934-171">すべてのデータベース オブジェクトが現在 null 許容型をサポートしますが、テーブルのデザイナーで生成されるアダプターします。</span><span class="sxs-lookup"><span data-stu-id="4e934-171">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="4e934-172">「TableAdapter で null 許容型のサポート」を参照してください[TableAdapter の概要](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview)します。</span><span class="sxs-lookup"><span data-stu-id="4e934-172">See "TableAdapter Support for Nullable Types" in [TableAdapter Overview](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e934-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e934-173">See Also</span></span>  
 <span data-ttu-id="4e934-174"><xref:System.InvalidOperationException></xref:System.InvalidOperationException></span><span class="sxs-lookup"><span data-stu-id="4e934-174"><xref:System.InvalidOperationException></span></span>   
 <span data-ttu-id="4e934-175"><xref:System.Nullable%601.HasValue%2A></xref:System.Nullable%601.HasValue%2A></span><span class="sxs-lookup"><span data-stu-id="4e934-175"><xref:System.Nullable%601.HasValue%2A></span></span>   
<span data-ttu-id="4e934-176"> [Null 許容型の使用](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md) </span><span class="sxs-lookup"><span data-stu-id="4e934-176"> [Using Nullable Types](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md) </span></span>  
<span data-ttu-id="4e934-177"> [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="4e934-177"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="4e934-178"> [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="4e934-178"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="4e934-179"> [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="4e934-179"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="4e934-180"> [TableAdapter の概要](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview) </span><span class="sxs-lookup"><span data-stu-id="4e934-180"> [TableAdapter Overview](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview) </span></span>  
<span data-ttu-id="4e934-181"> [場合演算子](../../../../visual-basic/language-reference/operators/if-operator.md) </span><span class="sxs-lookup"><span data-stu-id="4e934-181"> [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md) </span></span>  
<span data-ttu-id="4e934-182"> [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="4e934-182"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="4e934-183"> [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md) </span><span class="sxs-lookup"><span data-stu-id="4e934-183"> [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) </span></span>  
<span data-ttu-id="4e934-184"> [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)</span><span class="sxs-lookup"><span data-stu-id="4e934-184"> [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)</span></span>
