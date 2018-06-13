---
title: ラムダ式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: c45500dc7a1e59a7ac83d43b826ca4cbfca6efb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654795"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="1acce-102">ラムダ式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1acce-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="1acce-103">A*ラムダ式*は関数またはサブルーチン デリゲートが有効な場所で使用できる名前のないです。</span><span class="sxs-lookup"><span data-stu-id="1acce-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="1acce-104">ラムダ式は関数またはサブルーチンを指定でき、単一行または複数行を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1acce-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="1acce-105">ラムダ式に現在のスコープから値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="1acce-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1acce-106">`RemoveHandler`ステートメントは例外です。</span><span class="sxs-lookup"><span data-stu-id="1acce-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="1acce-107">デリゲート パラメーターのラムダ式を渡すことはできません`RemoveHandler`です。</span><span class="sxs-lookup"><span data-stu-id="1acce-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="1acce-108">ラムダ式を使用して作成する、`Function`または`Sub`キーワード、標準の関数またはサブルーチンを作成すると同様です。</span><span class="sxs-lookup"><span data-stu-id="1acce-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="1acce-109">ただし、ステートメントでは、ラムダ式が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1acce-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="1acce-110">次の例は、ラムダ式をその引数をインクリメントし、値を返します。</span><span class="sxs-lookup"><span data-stu-id="1acce-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="1acce-111">この例では、単一行および複数行ラムダ式の両方の構文、関数を示します。</span><span class="sxs-lookup"><span data-stu-id="1acce-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 <span data-ttu-id="1acce-112">次の例は、値をコンソールに出力するラムダ式です。</span><span class="sxs-lookup"><span data-stu-id="1acce-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="1acce-113">この例では、単一行および複数行ラムダ式の両方の構文のサブルーチンを示します。</span><span class="sxs-lookup"><span data-stu-id="1acce-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 <span data-ttu-id="1acce-114">前の例で、ラムダ式に割り当てられている変数の名前に注意してください。</span><span class="sxs-lookup"><span data-stu-id="1acce-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="1acce-115">変数を参照するには、ラムダ式を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1acce-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="1acce-116">宣言し、次の例で示すように、同時に、ラムダ式を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1acce-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 <span data-ttu-id="1acce-117">ラムダ式は関数呼び出しの結果値として返すことができます (例に示すように、[コンテキスト](#context)このトピックで後述する「)、に渡されるで引数としてデリゲート型を受け取るパラメーター次に示すように、または例です。</span><span class="sxs-lookup"><span data-stu-id="1acce-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="1acce-118">ラムダ式の構文</span><span class="sxs-lookup"><span data-stu-id="1acce-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="1acce-119">ラムダ式の構文では、標準の関数またはサブルーチンに似ています。</span><span class="sxs-lookup"><span data-stu-id="1acce-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="1acce-120">相違点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1acce-120">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="1acce-121">ラムダ式には、名前がありません。</span><span class="sxs-lookup"><span data-stu-id="1acce-121">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="1acce-122">ラムダ式ことも、修飾子など`Overloads`または`Overrides`です。</span><span class="sxs-lookup"><span data-stu-id="1acce-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="1acce-123">単一行のラムダ関数は使用しないで、`As`戻り値の型を指定する句。</span><span class="sxs-lookup"><span data-stu-id="1acce-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="1acce-124">代わりに、型は、ラムダ式の本体に評価される値から推論されます。</span><span class="sxs-lookup"><span data-stu-id="1acce-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="1acce-125">たとえば、ラムダ式の本体が`cust.City = "London"`、戻り値の型は`Boolean`します。</span><span class="sxs-lookup"><span data-stu-id="1acce-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="1acce-126">複数行ラムダ関数のいずれかを指定できます戻り値の型を使用して、`As`句、または省略、`As`句戻り値の型を推論できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1acce-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="1acce-127">ときに、`As`複数行ラムダ関数の句を省略すると、すべての主要な型である戻り値の型を推論、`Return`複数行ラムダ関数内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="1acce-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="1acce-128">*基準となる型*は一意の型に拡大変換できるその他のすべての型です。</span><span class="sxs-lookup"><span data-stu-id="1acce-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="1acce-129">この一意の型を特定できない場合に絞り込むことが、配列内の他のすべての型を一意の型は、主要な型です。</span><span class="sxs-lookup"><span data-stu-id="1acce-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="1acce-130">これらの一意の型をどちらも特定できない場合は、 `Object`が最も優先度の高い型になります。</span><span class="sxs-lookup"><span data-stu-id="1acce-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="1acce-131">この例では場合、`Option Strict`に設定されている`On`、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1acce-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="1acce-132">式が指定された場合など、`Return`ステートメントは、型の値を含む`Integer`、 `Long`、および`Double`、結果の配列の型は`Double`します。</span><span class="sxs-lookup"><span data-stu-id="1acce-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="1acce-133">両方`Integer`と`Long`に拡大変換`Double`とのみ`Double`です。</span><span class="sxs-lookup"><span data-stu-id="1acce-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="1acce-134">そのため、 `Double` が最も優先度の高い型になります。</span><span class="sxs-lookup"><span data-stu-id="1acce-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="1acce-135">詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1acce-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="1acce-136">単一行の関数の本体は、ステートメントではなく、値を返す式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1acce-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="1acce-137">ない`Return`関数の単一行ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1acce-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="1acce-138">単一行の関数によって返される値は、関数の本体での式の値です。</span><span class="sxs-lookup"><span data-stu-id="1acce-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="1acce-139">単一行のサブルーチンの本体では、単一行ステートメントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1acce-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="1acce-140">単一行関数やサブルーチンを含めていない、`End Function`または`End Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1acce-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="1acce-141">ラムダ式のパラメーターのデータ型を使用して指定することができます、`As`キーワード、またはパラメーターのデータ型を推論することができます。</span><span class="sxs-lookup"><span data-stu-id="1acce-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="1acce-142">データ型またはすべてを推論する必要がありますかすべてのパラメーターが指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1acce-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="1acce-143">`Optional` `Paramarray`パラメーターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="1acce-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="1acce-144">ジェネリック パラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="1acce-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="1acce-145">非同期ラムダ</span><span class="sxs-lookup"><span data-stu-id="1acce-145">Async Lambdas</span></span>  
 <span data-ttu-id="1acce-146">ラムダ式およびステートメントを使用して、非同期処理を組み込んだを簡単に作成することができます、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)と[Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="1acce-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="1acce-147">たとえば、次に示す Windows フォーム例には、非同期メソッド `ExampleMethodAsync`を呼び出して待機するイベント ハンドラーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1acce-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="1acce-148">非同期のラムダを使用して、同じイベント ハンドラーを追加することができます、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="1acce-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="1acce-149">次の例に示すように、このハンドラーを追加するには、ラムダ パラメーター リストの前に `Async` 修飾子を追加します。</span><span class="sxs-lookup"><span data-stu-id="1acce-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="1acce-150">作成して、非同期メソッドを使用する方法の詳細については、次を参照してください。 [Async および Await を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="1acce-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <a name="context"></a> <span data-ttu-id="1acce-151">コンテキスト</span><span class="sxs-lookup"><span data-stu-id="1acce-151">Context</span></span>  
 <span data-ttu-id="1acce-152">ラムダ式は、内部で定義されたスコープとコンテキストを共有します。</span><span class="sxs-lookup"><span data-stu-id="1acce-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="1acce-153">コンテナーのスコープで記述されたコードと同じアクセス権を持ちます。</span><span class="sxs-lookup"><span data-stu-id="1acce-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="1acce-154">メンバー変数、関数とサブへのアクセスが含まれます`Me`、コンテナーのスコープ内のローカル変数やパラメーター。</span><span class="sxs-lookup"><span data-stu-id="1acce-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="1acce-155">ローカル変数と、コンテナー スコープ内のパラメーターへのアクセスは、そのスコープの有効期間を超えて拡張できます。</span><span class="sxs-lookup"><span data-stu-id="1acce-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="1acce-156">ラムダ式を参照するデリゲートがガベージ コレクションを使用できない限り、元の環境変数へのアクセスは保持されます。</span><span class="sxs-lookup"><span data-stu-id="1acce-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="1acce-157">次の例で、変数`target`に対してローカルな`makeTheGame`をメソッド、ラムダ式`playTheGame`が定義されています。</span><span class="sxs-lookup"><span data-stu-id="1acce-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="1acce-158">返されたラムダ式が割り当てられている注`takeAGuess`で`Main`、引き続きローカル変数にアクセスしている`target`です。</span><span class="sxs-lookup"><span data-stu-id="1acce-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 <span data-ttu-id="1acce-159">次の例では、入れ子になったラムダ式のアクセス権の幅の広い範囲を示します。</span><span class="sxs-lookup"><span data-stu-id="1acce-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="1acce-160">返されたラムダ式を実行すると`Main`として`aDel`、これらの要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="1acce-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="1acce-161">定義されているクラスのフィールド: `aField`</span><span class="sxs-lookup"><span data-stu-id="1acce-161">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="1acce-162">定義されているクラスのプロパティ: `aProp`</span><span class="sxs-lookup"><span data-stu-id="1acce-162">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="1acce-163">メソッドのパラメーター `functionWithNestedLambda`、それが定義されています。 `level1`</span><span class="sxs-lookup"><span data-stu-id="1acce-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="1acce-164">ローカル変数`functionWithNestedLambda`: `localVar`</span><span class="sxs-lookup"><span data-stu-id="1acce-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="1acce-165">入れ子になったラムダ式のパラメーター: `level2`</span><span class="sxs-lookup"><span data-stu-id="1acce-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="1acce-166">デリゲート型に変換します。</span><span class="sxs-lookup"><span data-stu-id="1acce-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="1acce-167">ラムダ式は、互換性のあるデリゲート型に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="1acce-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="1acce-168">互換性のための一般的な要件については、次を参照してください。[厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)です。</span><span class="sxs-lookup"><span data-stu-id="1acce-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="1acce-169">たとえば、次のコード例に暗黙的に変換するラムダ式を示しています。`Func(Of Integer, Boolean)`またはデリゲートのシグネチャが一致します。</span><span class="sxs-lookup"><span data-stu-id="1acce-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 <span data-ttu-id="1acce-170">次のコード例は、暗黙的に変換する、ラムダ式を示しています。`Sub(Of Double, String, Double)`またはデリゲートのシグネチャが一致します。</span><span class="sxs-lookup"><span data-stu-id="1acce-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 <span data-ttu-id="1acce-171">ラムダ式をデリゲートに割り当てるまたはプロシージャに引数として渡したりするときに、パラメーター名を指定は、データ型、型がデリゲートから取得されるを省略できます。</span><span class="sxs-lookup"><span data-stu-id="1acce-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1acce-172">使用例</span><span class="sxs-lookup"><span data-stu-id="1acce-172">Examples</span></span>  
  
-   <span data-ttu-id="1acce-173">次の例を返すラムダ式を定義する`True`null 許容型の引数に値が割り当てられる場合と`False`場合はその値は`Nothing`します。</span><span class="sxs-lookup"><span data-stu-id="1acce-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   <span data-ttu-id="1acce-174">次の例では、配列内の最後の要素のインデックスを返すラムダ式を定義します。</span><span class="sxs-lookup"><span data-stu-id="1acce-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1acce-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="1acce-175">See Also</span></span>  
 [<span data-ttu-id="1acce-176">手順</span><span class="sxs-lookup"><span data-stu-id="1acce-176">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="1acce-177">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="1acce-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="1acce-178">デリゲート</span><span class="sxs-lookup"><span data-stu-id="1acce-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="1acce-179">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="1acce-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="1acce-180">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="1acce-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="1acce-181">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="1acce-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 <span data-ttu-id="1acce-182">方法 : [Visual Basic でプロシージャを別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)</span><span class="sxs-lookup"><span data-stu-id="1acce-182">[How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)</span></span>  
 [<span data-ttu-id="1acce-183">方法 : ラムダ式を作成する</span><span class="sxs-lookup"><span data-stu-id="1acce-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)  
 [<span data-ttu-id="1acce-184">厳密でないデリゲート変換</span><span class="sxs-lookup"><span data-stu-id="1acce-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
