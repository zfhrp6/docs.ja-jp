---
title: null 許容値型 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8734114b9d657066a0ef0b2d648f0290c03b1cbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="c8ddc-102">null 許容値型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8ddc-102">Nullable Value Types (Visual Basic)</span></span>
<span data-ttu-id="c8ddc-103">特定の状況で定義されている値を持たない値の型と連携することがあります。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="c8ddc-104">たとえば、データベース内のフィールドは、意味のある割り当てられた値を持つ、割り当てられた値がないとを区別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="c8ddc-105">値の型は、通常の値または null 値のいずれかを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="c8ddc-106">このような拡張機能が呼び出された、 *null 許容型*です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-106">Such an extension is called a *nullable type*.</span></span>  
  
 <span data-ttu-id="c8ddc-107">各 null 許容型がジェネリックから構築された<xref:System.Nullable%601>構造体。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="c8ddc-108">作業に関連するアクティビティを追跡するデータベースを検討してください。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="c8ddc-109">次の例は、null 許容型を構築`Boolean`を入力し、その型の変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="c8ddc-110">宣言は、次の 3 つの方法で記述できます。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-110">You can write the declaration in three ways:</span></span>  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 <span data-ttu-id="c8ddc-111">変数`ridesBusToWork`の値を保持できる`True`、値の`False`、またはすべての値はありません。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="c8ddc-112">初期の既定値はありません値すべての例ではこの可能性があること、情報がない取得されていないこのユーザーの。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="c8ddc-113">これに対し、`False`情報が取得され、ユーザーが仕事のバスをオーバーライドしていないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>  
  
 <span data-ttu-id="c8ddc-114">変数とプロパティを宣言するには、null 許容型で、null 許容型の要素を含む配列を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="c8ddc-115">Null 許容型をパラメーターとしてでプロシージャを宣言してから null 許容型を返すことができます、`Function`プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>  
  
 <span data-ttu-id="c8ddc-116">参照型、配列などに null 許容型を構築することはできません、 `String`、またはクラス。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="c8ddc-117">基になる型は、値型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-117">The underlying type must be a value type.</span></span> <span data-ttu-id="c8ddc-118">詳細については、次を参照してください。[値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-118">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="c8ddc-119">Null 許容型の変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-119">Using a Nullable Type Variable</span></span>  
 <span data-ttu-id="c8ddc-120">Null 許容型の最も重要なメンバーは、その<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="c8ddc-121">Null 許容型の変数に対して<xref:System.Nullable%601.HasValue%2A>変数が定義済みの値を含むかどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="c8ddc-122">場合<xref:System.Nullable%601.HasValue%2A>は`True`から値を読み取ることができます<xref:System.Nullable%601.Value%2A>です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="c8ddc-123">なお両方<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>は`ReadOnly`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>  
  
### <a name="default-values"></a><span data-ttu-id="c8ddc-124">既定値</span><span class="sxs-lookup"><span data-stu-id="c8ddc-124">Default Values</span></span>  
 <span data-ttu-id="c8ddc-125">Null 許容型を持つ変数を宣言するときにその<xref:System.Nullable%601.HasValue%2A>プロパティの既定値を持つ`False`します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="c8ddc-126">つまり、既定では、変数がない基になる値の型の既定値ではなく、定義済みの値。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="c8ddc-127">次の例では、変数`numberOfChildren`最初に値を持たない値が定義されていなくても、既定の`Integer`型は 0 です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 <span data-ttu-id="c8ddc-128">Null 値は、未定義または不明な値を示すために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="c8ddc-129">場合`numberOfChildren`として宣言された`Integer`情報が現在使用できないことを示す値になりますありません。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>  
  
### <a name="storing-values"></a><span data-ttu-id="c8ddc-130">値を格納します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-130">Storing Values</span></span>  
 <span data-ttu-id="c8ddc-131">一般的な方法で変数または null 許容型のプロパティ値を格納します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="c8ddc-132">次の例では、変数に値を割り当てます`numberOfChildren`前の例で宣言します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 <span data-ttu-id="c8ddc-133">変数または null 許容型のプロパティには定義済みの値がある場合は、割り当てられている値を持っていないの初期状態に戻すを生成できます。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="c8ddc-134">変数またはプロパティを設定して、これを行う`Nothing`次の例を示します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="c8ddc-135">割り当てることはできます`Nothing`、null 許容型の変数にすることはできないことをテスト用`Nothing`等号 (=) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="c8ddc-136">等号 (=) を使用する比較`someVar = Nothing`、常に評価`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="c8ddc-137">変数をテストする<xref:System.Nullable%601.HasValue%2A>プロパティ`False`、またはを使用してテスト、`Is`または`IsNot`演算子。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>  
  
### <a name="retrieving-values"></a><span data-ttu-id="c8ddc-138">値を取得します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-138">Retrieving Values</span></span>  
 <span data-ttu-id="c8ddc-139">Null 許容型の変数の値を取得する必要があります最初をテストするその<xref:System.Nullable%601.HasValue%2A>プロパティに値を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="c8ddc-140">値を読み取るしようとする場合と<xref:System.Nullable%601.HasValue%2A>は`False`、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]スロー、<xref:System.InvalidOperationException>例外。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="c8ddc-141">次の例では、変数を読み取ることをお勧め`numberOfChildren`前の例です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## <a name="comparing-nullable-types"></a><span data-ttu-id="c8ddc-142">Null 許容型を比較します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-142">Comparing Nullable Types</span></span>  
 <span data-ttu-id="c8ddc-143">Null 許容と`Boolean`変数がブール式で使用される、結果を指定できます`True`、 `False`、または`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="c8ddc-144">真理値表を次に示します`And`と`Or`です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="c8ddc-145">`b1`と`b2`3 つの値があるようになりました 9 つの組み合わせを評価します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>  
  
|<span data-ttu-id="c8ddc-146">B1</span><span class="sxs-lookup"><span data-stu-id="c8ddc-146">b1</span></span>|<span data-ttu-id="c8ddc-147">B2</span><span class="sxs-lookup"><span data-stu-id="c8ddc-147">b2</span></span>|<span data-ttu-id="c8ddc-148">b1 と b2</span><span class="sxs-lookup"><span data-stu-id="c8ddc-148">b1 And b2</span></span>|<span data-ttu-id="c8ddc-149">b1 または b2</span><span class="sxs-lookup"><span data-stu-id="c8ddc-149">b1 Or b2</span></span>|  
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
  
 <span data-ttu-id="c8ddc-150">ブール値変数または式の値が`Nothing`はどちらも`true`も`false`します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="c8ddc-151">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-151">Consider the following example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 <span data-ttu-id="c8ddc-152">この例では`b1 And b2`に評価される`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="c8ddc-153">その結果、`Else`各句が実行されて`If`ステートメントでは、呼び出し力には、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  <span data-ttu-id="c8ddc-154">`AndAlso`および`OrElse`、最初の評価が、2 番目のオペランドを評価する必要がありますを使用するショート サーキット評価、`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>  
  
## <a name="propagation"></a><span data-ttu-id="c8ddc-155">伝達</span><span class="sxs-lookup"><span data-stu-id="c8ddc-155">Propagation</span></span>  
 <span data-ttu-id="c8ddc-156">算術演算子、比較、shift キーを押し、または種類の操作のオペランドの一方または両方が null 許容の場合は、操作の結果も null 値を許容できます。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="c8ddc-157">両方のオペランドが値ではない`Nothing`、どちらもが場合と同様に、オペランドの基になる値に対して操作を実行 null 許容型。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="c8ddc-158">次の例では、変数`compare1`と`sum1`は暗黙的に型指定されています。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="c8ddc-159">上にマウス ポインターを置くと場合、コンパイラがそれらの両方に対して null 許容型を推測することが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 <span data-ttu-id="c8ddc-160">1 つまたは両方のオペランドの値を持つ場合`Nothing`、結果になります`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## <a name="using-nullable-types-with-data"></a><span data-ttu-id="c8ddc-161">Null 許容型のデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-161">Using Nullable Types with Data</span></span>  
 <span data-ttu-id="c8ddc-162">データベースは、null 許容型を使用する最も重要な場所の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="c8ddc-163">すべてのデータベース オブジェクトは null 許容の型を現在サポートしていますが、デザイナーで生成されたテーブルのアダプターです。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="c8ddc-164">「Null 許容型の TableAdapter サポート」を参照してください[TableAdapter の概要](/visualstudio/data-tools/tableadapter-overview)です。</span><span class="sxs-lookup"><span data-stu-id="c8ddc-164">See "TableAdapter Support for Nullable Types" in [TableAdapter Overview](/visualstudio/data-tools/tableadapter-overview).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ddc-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8ddc-165">See Also</span></span>  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [<span data-ttu-id="c8ddc-166">Null 許容型の使用</span><span class="sxs-lookup"><span data-stu-id="c8ddc-166">Using Nullable Types</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [<span data-ttu-id="c8ddc-167">データの種類</span><span class="sxs-lookup"><span data-stu-id="c8ddc-167">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="c8ddc-168">値型と参照型</span><span class="sxs-lookup"><span data-stu-id="c8ddc-168">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="c8ddc-169">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="c8ddc-169">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="c8ddc-170">TableAdapter の概要</span><span class="sxs-lookup"><span data-stu-id="c8ddc-170">TableAdapter Overview</span></span>](/visualstudio/data-tools/tableadapter-overview)  
 [<span data-ttu-id="c8ddc-171">If 演算子</span><span class="sxs-lookup"><span data-stu-id="c8ddc-171">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="c8ddc-172">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="c8ddc-172">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="c8ddc-173">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="c8ddc-173">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="c8ddc-174">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="c8ddc-174">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
