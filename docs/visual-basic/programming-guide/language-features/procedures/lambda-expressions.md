---
title: "ラムダ式 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.LambdaFunction
dev_langs:
- VB
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: 52
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
ms.openlocfilehash: e4624e5f20beeebf85656c893043030566200557
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="175c5-102">ラムダ式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="175c5-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="175c5-103">A*ラムダ式*関数またはサブルーチン デリゲートが有効な場所で使用できる名前のないです。</span><span class="sxs-lookup"><span data-stu-id="175c5-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="175c5-104">ラムダ式は、関数またはサブルーチンを指定でき、単一行または複数行を指定できます。</span><span class="sxs-lookup"><span data-stu-id="175c5-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="175c5-105">ラムダ式に現在のスコープから値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="175c5-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="175c5-106">`RemoveHandler`ステートメントは例外です。</span><span class="sxs-lookup"><span data-stu-id="175c5-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="175c5-107">デリゲート パラメーターのラムダ式を渡すことはできません`RemoveHandler`します。</span><span class="sxs-lookup"><span data-stu-id="175c5-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="175c5-108">ラムダ式を使用して作成する、`Function`または`Sub`キーワード、標準的な関数またはサブルーチンを作成すると同じです。</span><span class="sxs-lookup"><span data-stu-id="175c5-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="175c5-109">ただし、ステートメントでラムダ式が含まれています。</span><span class="sxs-lookup"><span data-stu-id="175c5-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="175c5-110">次の例は、ラムダ式を引数をインクリメントし、値を返します。</span><span class="sxs-lookup"><span data-stu-id="175c5-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="175c5-111">この例では、単一行と複数行のラムダ式の両方の構文、関数を示します。</span><span class="sxs-lookup"><span data-stu-id="175c5-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 <span data-ttu-id="175c5-112">[!code-vb[VbVbalrLambdas&#14;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-112">[!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]</span></span>  
  
 <span data-ttu-id="175c5-113">次の例は、値をコンソールに出力するラムダ式です。</span><span class="sxs-lookup"><span data-stu-id="175c5-113">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="175c5-114">この例では、単一行と複数行のラムダ式の両方の構文、サブルーチンを示します。</span><span class="sxs-lookup"><span data-stu-id="175c5-114">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 <span data-ttu-id="175c5-115">[!code-vb[VbVbalrLambdas&#15;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-115">[!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]</span></span>  
  
 <span data-ttu-id="175c5-116">前の例では変数名にラムダ式が割り当てられたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="175c5-116">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="175c5-117">変数を参照するには、ラムダ式を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="175c5-117">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="175c5-118">宣言し、次の例で示すように、同時に、ラムダ式を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="175c5-118">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 <span data-ttu-id="175c5-119">[!code-vb[VbVbalrLambdas&#3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-119">[!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]</span></span>  
  
 <span data-ttu-id="175c5-120">ラムダ式は関数呼び出しの結果値として返されることができます (例で示すように、[コンテキスト](#context)このトピックで後述する「)、するやに渡す引数としてデリゲート型を受け取るパラメーターが次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="175c5-120">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 <span data-ttu-id="175c5-121">[!code-vb[VbVbalrLambdas&#8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-121">[!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="175c5-122">ラムダ式の構文</span><span class="sxs-lookup"><span data-stu-id="175c5-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="175c5-123">ラムダ式の構文では、標準の関数またはサブルーチンに似ています。</span><span class="sxs-lookup"><span data-stu-id="175c5-123">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="175c5-124">相違点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="175c5-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="175c5-125">ラムダ式には、名前がありません。</span><span class="sxs-lookup"><span data-stu-id="175c5-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="175c5-126">ラムダ式がなど、修飾子を持つことはできません`Overloads`または`Overrides`です。</span><span class="sxs-lookup"><span data-stu-id="175c5-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="175c5-127">単一行のラムダ関数は使用しないでください、`As`戻り値の型を指定する句。</span><span class="sxs-lookup"><span data-stu-id="175c5-127">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="175c5-128">代わりに、型は、ラムダ式の本体に評価される値から推論されます。</span><span class="sxs-lookup"><span data-stu-id="175c5-128">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="175c5-129">たとえば、ラムダ式の本体は`cust.City = "London"`、戻り値の型`Boolean`します。</span><span class="sxs-lookup"><span data-stu-id="175c5-129">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="175c5-130">複数行ラムダの関数のいずれかを指定できます戻り値の型を使用して、`As`句、または省略、`As`句戻り値の型を推論できるようにします。</span><span class="sxs-lookup"><span data-stu-id="175c5-130">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="175c5-131">ときに、`As`複数行のラムダ関数の句を省略すると、すべての主要な型である戻り値の型を推論、`Return`複数行のラムダ関数内のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="175c5-131">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="175c5-132">*基準となる型*は一意の型に拡大変換できるその他のすべての種類です。</span><span class="sxs-lookup"><span data-stu-id="175c5-132">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="175c5-133">この一意の型を特定できない場合に絞り込むことが、配列内の他のすべての型の一意の型は、基準となる型。</span><span class="sxs-lookup"><span data-stu-id="175c5-133">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="175c5-134">これらの一意の型をどちらも特定できない場合は、`Object` が最も優先度の高い型になります。</span><span class="sxs-lookup"><span data-stu-id="175c5-134">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="175c5-135">この場合は場合、`Option Strict`に設定されている`On`、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="175c5-135">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="175c5-136">式が指定された場合など、`Return`ステートメントは、型の値を含む`Integer`、 `Long`、および`Double`、結果の配列の型は`Double`です。</span><span class="sxs-lookup"><span data-stu-id="175c5-136">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="175c5-137">両方とも`Integer`と`Long`に拡大変換`Double`およびのみ`Double`します。</span><span class="sxs-lookup"><span data-stu-id="175c5-137">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="175c5-138">そのため、 `Double` が最も優先度の高い型になります。</span><span class="sxs-lookup"><span data-stu-id="175c5-138">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="175c5-139">詳細については、次を参照してください。[拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)します。</span><span class="sxs-lookup"><span data-stu-id="175c5-139">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="175c5-140">単一行の関数の本文には、ステートメントではなく、値を返す式を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="175c5-140">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="175c5-141">ない`Return`関数の単一行のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="175c5-141">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="175c5-142">単一行の関数によって返される値は、関数の本体での式の値です。</span><span class="sxs-lookup"><span data-stu-id="175c5-142">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="175c5-143">単一行のサブルーチンの本文は、単一行のステートメントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="175c5-143">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="175c5-144">単一行の関数やサブルーチンを含めていない、`End Function`または`End Sub`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="175c5-144">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="175c5-145">ラムダ式のパラメーターのデータ型を指定するにを使用して、`As`キーワード、またはパラメーターのデータ型を推論することができます。</span><span class="sxs-lookup"><span data-stu-id="175c5-145">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="175c5-146">データ型、またはすべてを推論する必要がありますかすべてパラメーターが指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="175c5-146">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="175c5-147">`Optional``Paramarray`パラメーターは使用できません。</span><span class="sxs-lookup"><span data-stu-id="175c5-147">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="175c5-148">ジェネリック パラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="175c5-148">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="175c5-149">非同期ラムダ</span><span class="sxs-lookup"><span data-stu-id="175c5-149">Async Lambdas</span></span>  
 <span data-ttu-id="175c5-150">ラムダ式およびステートメントを使用して非同期処理を組み込んでいるを簡単に作成することができます、 [Async](../../../../visual-basic/language-reference/modifiers/async.md)と[Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md)キーワードです。</span><span class="sxs-lookup"><span data-stu-id="175c5-150">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="175c5-151">たとえば、次に示す Windows フォーム例には、非同期メソッド `ExampleMethodAsync`を呼び出して待機するイベント ハンドラーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="175c5-151">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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
  
 <span data-ttu-id="175c5-152">非同期ラムダを使用して、同じイベント ハンドラーを追加することができます、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="175c5-152">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="175c5-153">次の例に示すように、このハンドラーを追加するには、ラムダ パラメーター リストの前に `Async` 修飾子を追加します。</span><span class="sxs-lookup"><span data-stu-id="175c5-153">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="175c5-154">作成して、非同期のメソッドを使用する方法の詳細については、次を参照してください。 [Async および Await を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)します。</span><span class="sxs-lookup"><span data-stu-id="175c5-154">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <span data-ttu-id="175c5-155"><a name="context"></a>コンテキスト</span><span class="sxs-lookup"><span data-stu-id="175c5-155"><a name="context"></a> Context</span></span>  
 <span data-ttu-id="175c5-156">ラムダ式が定義されているスコープとコンテキストを共有します。</span><span class="sxs-lookup"><span data-stu-id="175c5-156">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="175c5-157">コンテナーのスコープ内に記述されたコードと同じアクセス権を持ちます。</span><span class="sxs-lookup"><span data-stu-id="175c5-157">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="175c5-158">これにより、メンバー変数、関数とサブへのアクセスが含まれます。 `Me`、コンテナーのスコープ内のローカル変数やパラメーター。</span><span class="sxs-lookup"><span data-stu-id="175c5-158">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="175c5-159">ローカル変数と、コンテナー スコープ内のパラメーターへのアクセスは、そのスコープの有効期間を超えて拡張できます。</span><span class="sxs-lookup"><span data-stu-id="175c5-159">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="175c5-160">ラムダ式を参照するデリゲートがガベージ コレクションを使用できない限り、元の環境変数へのアクセスは保持されます。</span><span class="sxs-lookup"><span data-stu-id="175c5-160">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="175c5-161">次の例で、変数`target`に対してローカルな`makeTheGame`、するメソッドは、ラムダ式`playTheGame`が定義されています。</span><span class="sxs-lookup"><span data-stu-id="175c5-161">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="175c5-162">返されたラムダ式が割り当てられている注`takeAGuess`で`Main`、ローカル変数にアクセスするにはまだ`target`です。</span><span class="sxs-lookup"><span data-stu-id="175c5-162">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 <span data-ttu-id="175c5-163">[!code-vb[VbVbalrLambdas&#12;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-163">[!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]</span></span>  
  
 <span data-ttu-id="175c5-164">次の例では、入れ子になったラムダ式のアクセス権は幅広いを示します。</span><span class="sxs-lookup"><span data-stu-id="175c5-164">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="175c5-165">返されたラムダ式の実行時に`Main`として`aDel`、これらの要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="175c5-165">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="175c5-166">定義されているクラスのフィールド:`aField`</span><span class="sxs-lookup"><span data-stu-id="175c5-166">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="175c5-167">定義されているクラスのプロパティ:`aProp`</span><span class="sxs-lookup"><span data-stu-id="175c5-167">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="175c5-168">メソッドのパラメーターの`functionWithNestedLambda`、それが定義されています。`level1`</span><span class="sxs-lookup"><span data-stu-id="175c5-168">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="175c5-169">ローカル変数`functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="175c5-169">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="175c5-170">入れ子になったラムダ式のパラメーター:`level2`</span><span class="sxs-lookup"><span data-stu-id="175c5-170">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 <span data-ttu-id="175c5-171">[!code-vb[VbVbalrLambdas&#9;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-171">[!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]</span></span>  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="175c5-172">デリゲート型に変換します。</span><span class="sxs-lookup"><span data-stu-id="175c5-172">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="175c5-173">ラムダ式は、互換性のあるデリゲート型に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="175c5-173">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="175c5-174">互換性のための一般的な要件については、次を参照してください。[厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)します。</span><span class="sxs-lookup"><span data-stu-id="175c5-174">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="175c5-175">たとえば、次のコード例に暗黙的に変換するラムダ式を示しています。`Func(Of Integer, Boolean)`またはデリゲート シグネチャの一致します。</span><span class="sxs-lookup"><span data-stu-id="175c5-175">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 <span data-ttu-id="175c5-176">[!code-vb[VbVbalrLambdas&#16;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-176">[!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]</span></span>  
  
 <span data-ttu-id="175c5-177">次のコード例は、暗黙的に変換するラムダ式を示しています。`Sub(Of Double, String, Double)`またはデリゲート シグネチャの一致します。</span><span class="sxs-lookup"><span data-stu-id="175c5-177">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 <span data-ttu-id="175c5-178">[!code-vb[VbVbalrLambdas 第&23;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-178">[!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]</span></span>  
  
 <span data-ttu-id="175c5-179">ラムダ式をデリゲートに割り当てるかをプロシージャに引数として渡すときに、パラメーター名を指定ができる型がデリゲートから取得されるようにすること、データ型を省略できます。</span><span class="sxs-lookup"><span data-stu-id="175c5-179">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="175c5-180">例</span><span class="sxs-lookup"><span data-stu-id="175c5-180">Examples</span></span>  
  
-   <span data-ttu-id="175c5-181">次の例を返すラムダ式を定義する`True`場合 null 許容型の引数は、割り当てられた値と`False`場合はその値は`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="175c5-181">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     <span data-ttu-id="175c5-182">[!code-vb[VbVbalrLambdas&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-182">[!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]</span></span>  
  
-   <span data-ttu-id="175c5-183">次の例では、配列内の最後の要素のインデックスを返すラムダ式を定義します。</span><span class="sxs-lookup"><span data-stu-id="175c5-183">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     <span data-ttu-id="175c5-184">[!code-vb[VbVbalrLambdas&#5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="175c5-184">[!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="175c5-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="175c5-185">See Also</span></span>  
 <span data-ttu-id="175c5-186">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="175c5-186">[Procedures](./index.md) </span></span>  
<span data-ttu-id="175c5-187"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="175c5-187"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="175c5-188"> [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="175c5-188"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="175c5-189"> [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="175c5-189"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="175c5-190"> [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="175c5-190"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="175c5-191"> [Null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="175c5-191"> [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="175c5-192"> [方法: Visual Basic での別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="175c5-192"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="175c5-193"> [方法: ラムダ式を作成します。](./how-to-create-a-lambda-expression.md) </span><span class="sxs-lookup"><span data-stu-id="175c5-193"> [How to: Create a Lambda Expression](./how-to-create-a-lambda-expression.md) </span></span>  
<span data-ttu-id="175c5-194"> [厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="175c5-194"> [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span></span>

