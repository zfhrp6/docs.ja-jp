---
title: "プロシージャのトラブルシューティング (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b838644baa5ad10f1deb917cff5751a0f625fca6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-procedures-visual-basic"></a><span data-ttu-id="cd77a-102">プロシージャのトラブルシューティング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd77a-102">Troubleshooting Procedures (Visual Basic)</span></span>
<span data-ttu-id="cd77a-103">このページには、プロシージャを使用する場合に発生する可能性がある一般的な問題が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-103">This page lists some common problems that can occur when working with procedures.</span></span>  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a><span data-ttu-id="cd77a-104">Function プロシージャから配列型を返す</span><span class="sxs-lookup"><span data-stu-id="cd77a-104">Returning an Array Type from a Function Procedure</span></span>  
 <span data-ttu-id="cd77a-105">場合、`Function`プロシージャは、配列のデータ型を返しますでは使用できません、`Function`値を格納する配列の要素の名前。</span><span class="sxs-lookup"><span data-stu-id="cd77a-105">If a `Function` procedure returns an array data type, you cannot use the `Function` name to store values in the elements of the array.</span></span> <span data-ttu-id="cd77a-106">これを行うしようとすると、コンパイラによって呼び出しとして、`Function`です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-106">If you attempt to do this, the compiler interprets it as a call to the `Function`.</span></span> <span data-ttu-id="cd77a-107">次の例では、コンパイラ エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-107">The following example generates compiler errors.</span></span>  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 <span data-ttu-id="cd77a-108">`' The following statement generates a`   `COMPILER ERROR`  `.`</span><span class="sxs-lookup"><span data-stu-id="cd77a-108">`' The following statement generates a`   `COMPILER ERROR`  `.`</span></span>  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 <span data-ttu-id="cd77a-109">`' The following statement generates a`   `COMPILER ERROR`  `.`</span><span class="sxs-lookup"><span data-stu-id="cd77a-109">`' The following statement generates a`   `COMPILER ERROR`  `.`</span></span>  
  
 `Return allOnes()`  
  
 `End Function`  
  
 <span data-ttu-id="cd77a-110">ステートメント`allOnes(i) = 1`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`不適切なデータ型の引数を持つ (シングルトン`Integer`の代わりに、`Integer`配列)。</span><span class="sxs-lookup"><span data-stu-id="cd77a-110">The statement `allOnes(i) = 1` generates a compiler error because it appears to call `allOnes` with an argument of the wrong data type (a singleton `Integer` instead of an `Integer` array).</span></span> <span data-ttu-id="cd77a-111">ステートメント`Return allOnes()`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`引数なしでします。</span><span class="sxs-lookup"><span data-stu-id="cd77a-111">The statement `Return allOnes()` generates a compiler error because it appears to call `allOnes` with no argument.</span></span>  
  
 <span data-ttu-id="cd77a-112">**適切なアプローチ:**が返される配列の要素を変更できるようにするには、ローカル変数として内部の配列を定義します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-112">**Correct Approach:** To be able to modify the elements of an array that is to be returned, define an internal array as a local variable.</span></span> <span data-ttu-id="cd77a-113">次の例がエラーなしでコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="cd77a-113">The following example compiles without error.</span></span>  
  
 [!code-vb[VbVbcnProcedures#66](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a><span data-ttu-id="cd77a-114">変更されていない引数によってプロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="cd77a-114">Argument Not Being Modified by Procedure Call</span></span>  
 <span data-ttu-id="cd77a-115">プロシージャは呼び出し元のコードで引数の基になるプログラミング要素の変更を許可する場合は、参照渡しで渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd77a-115">If you intend to allow a procedure to change a programming element underlying an argument in the calling code, you must pass it by reference.</span></span> <span data-ttu-id="cd77a-116">値渡しで渡す場合でも、プロシージャが参照型の引数の要素をアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-116">But a procedure can access the elements of a reference type argument even if you pass it by value.</span></span>  
  
-   <span data-ttu-id="cd77a-117">**変数を基になる**です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-117">**Underlying Variable**.</span></span> <span data-ttu-id="cd77a-118">基になる変数要素自体の値を変更する手順は、プロシージャには、パラメーターを宣言する必要があります[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-118">To allow the procedure to replace the value of the underlying variable element itself, the procedure must declare the parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="cd77a-119">また、呼び出し元のコードいない引数かっこで囲んでくださいをオーバーライドするため、`ByRef`引き渡し方法です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-119">Also, the calling code must not enclose the argument in parentheses, because that would override the `ByRef` passing mechanism.</span></span>  
  
-   <span data-ttu-id="cd77a-120">**型の要素を参照**です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-120">**Reference Type Elements**.</span></span> <span data-ttu-id="cd77a-121">パラメーターを宣言する場合[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャは、基になる変数要素自体を変更できません。</span><span class="sxs-lookup"><span data-stu-id="cd77a-121">If you declare a parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), the procedure cannot modify the underlying variable element itself.</span></span> <span data-ttu-id="cd77a-122">ただし、引数が参照型の場合、変数の値を置き換えることができない場合でも、プロシージャは、ポイントをするには、オブジェクトのメンバー変更できます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-122">However, if the argument is a reference type, the procedure can modify the members of the object to which it points, even though it cannot replace the variable's value.</span></span> <span data-ttu-id="cd77a-123">たとえば、引数が、配列変数の場合は、プロシージャは、新しい配列を割り当てることはできませんが、1 つまたは複数の要素を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-123">For example, if the argument is an array variable, the procedure cannot assign a new array to it, but it can change one or more of its elements.</span></span> <span data-ttu-id="cd77a-124">変更された要素は、基になる配列内の変数呼び出し元のコードに反映されます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-124">The changed elements are reflected in the underlying array variable in the calling code.</span></span>  
  
 <span data-ttu-id="cd77a-125">次の例では、その要素の値によって、配列変数を行い、操作を 2 つの手順を定義します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-125">The following example defines two procedures that take an array variable by value and operate on its elements.</span></span> <span data-ttu-id="cd77a-126">プロシージャ`increase`単に各要素に 1 を追加します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-126">Procedure `increase` simply adds one to each element.</span></span> <span data-ttu-id="cd77a-127">プロシージャ`replace`パラメーターに新しい配列を割り当てます`a()`し、各要素に 1 を追加します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-127">Procedure `replace` assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="cd77a-128">ただし、再割り当てには影響しません、基になる配列内の変数呼び出し元のコードのため`a()`が宣言されている`ByVal`です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-128">However, the reassignment does not affect the underlying array variable in the calling code because `a()` is declared `ByVal`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]  
  
 <span data-ttu-id="cd77a-129">次の例は、呼び出しを`increase`と`replace`です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-129">The following example makes calls to `increase` and `replace`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]  
  
 <span data-ttu-id="cd77a-130">最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="cd77a-131">`n` 、参照型では、`increase`渡される場合でも、そのメンバーを変更できます`ByVal`です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-131">Because `n` is a reference type, `increase` can change its members, even though it is passed `ByVal`.</span></span>  
  
 <span data-ttu-id="cd77a-132">2 番目`MsgBox`表示を呼び出して"目後: 41、11、21、31"です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-132">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="cd77a-133">`n`渡される`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることによってです。</span><span class="sxs-lookup"><span data-stu-id="cd77a-133">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` by assigning a new array to it.</span></span> <span data-ttu-id="cd77a-134">ときに`replace`配列の新しいインスタンスを作成`k`し、ローカル変数に代入`a`への参照が失われた`n`呼び出し元のコードで渡される入力します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-134">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="cd77a-135">メンバーをインクリメントするときに`a`、ローカルの配列のみ`k`が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-135">When it increments the members of `a`, only the local array `k` is affected.</span></span>  
  
 <span data-ttu-id="cd77a-136">**適切なアプローチ:**を基になる変数要素自体を変更するには、参照渡しで渡します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-136">**Correct Approach:** To be able to modify an underlying variable element itself, pass it by reference.</span></span> <span data-ttu-id="cd77a-137">次の例では、変更を示しますの宣言で`replace`呼び出し元のコードの別の 1 つの配列を置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-137">The following example shows the change in the declaration of `replace` that allows it to replace one array with another in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#64](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]  
  
## <a name="unable-to-define-an-overload"></a><span data-ttu-id="cd77a-138">オーバー ロードを定義できません。</span><span class="sxs-lookup"><span data-stu-id="cd77a-138">Unable to Define an Overload</span></span>  
 <span data-ttu-id="cd77a-139">プロシージャのオーバー ロードされたバージョンを定義する場合は、異なるシグネチャが同じ名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd77a-139">If you want to define an overloaded version of a procedure, you must use the same name but a different signature.</span></span> <span data-ttu-id="cd77a-140">コンパイラは、同じシグネチャを持つオーバー ロードの宣言を区別することはできません、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-140">If the compiler cannot differentiate your declaration from an overload with the same signature, it generates an error.</span></span>  
  
 <span data-ttu-id="cd77a-141">*署名*プロシージャのプロシージャ名とパラメーター リストによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-141">The *signature* of a procedure is determined by the procedure name and the parameter list.</span></span> <span data-ttu-id="cd77a-142">各オーバー ロードは、他のすべてのオーバー ロードと同じ名前を持つ必要がありますが、シグネチャの他のコンポーネントの少なくとも 1 つにそれらのすべてを異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd77a-142">Each overload must have the same name as all the other overloads but must differ from all of them in at least one of the other components of the signature.</span></span> <span data-ttu-id="cd77a-143">詳細については、次を参照してください。[プロシージャのオーバー ロード](./procedure-overloading.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-143">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="cd77a-144">次の項目を場合でも、パラメーター リストには関係ないコンポーネントを示します、プロシージャの署名。</span><span class="sxs-lookup"><span data-stu-id="cd77a-144">The following items, even though they pertain to the parameter list, are not components of a procedure's signature:</span></span>  
  
-   <span data-ttu-id="cd77a-145">プロシージャ修飾子キーワードなど`Public`、 `Shared`、および`Static`</span><span class="sxs-lookup"><span data-stu-id="cd77a-145">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
-   <span data-ttu-id="cd77a-146">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="cd77a-146">Parameter names</span></span>  
  
-   <span data-ttu-id="cd77a-147">パラメーター修飾子キーワードなど`ByRef`と`Optional`</span><span class="sxs-lookup"><span data-stu-id="cd77a-147">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
-   <span data-ttu-id="cd77a-148">(変換演算子) を除く、戻り値のデータ型</span><span class="sxs-lookup"><span data-stu-id="cd77a-148">The data type of the return value (except for a conversion operator)</span></span>  
  
 <span data-ttu-id="cd77a-149">1 つ以上の前の項目のみプロシージャをオーバー ロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="cd77a-149">You cannot overload a procedure by varying only one or more of the preceding items.</span></span>  
  
 <span data-ttu-id="cd77a-150">**適切なアプローチ:**プロシージャのオーバー ロードを定義できるようにするには、署名を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd77a-150">**Correct Approach:** To be able to define a procedure overload, you must vary the signature.</span></span> <span data-ttu-id="cd77a-151">同じ名前を使用する必要があるために、数、順序、またはパラメーターのデータ型を変更しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="cd77a-151">Because you must use the same name, you must vary the number, order, or data types of the parameters.</span></span> <span data-ttu-id="cd77a-152">ジェネリック プロシージャでは、型パラメーターの数を変更できます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-152">In a generic procedure, you can vary the number of type parameters.</span></span> <span data-ttu-id="cd77a-153">変換演算子で ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md))、戻り値の型を変更できます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-153">In a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)), you can vary the return type.</span></span>  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="cd77a-154">省略可能な解像度と ParamArray 引数にオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="cd77a-154">Overload Resolution with Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="cd77a-155">場合は 1 つまたは複数のプロシージャをオーバー ロードは[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)パラメーターまたは[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、複製のいずれかの回避する必要があります、*暗黙のオーバー ロード*です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-155">If you are overloading a procedure with one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters or a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you must avoid duplicating any of the *implicit overloads*.</span></span> <span data-ttu-id="cd77a-156">詳細については、次を参照してください。[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-156">For information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a><span data-ttu-id="cd77a-157">オーバー ロードされたプロシージャの間違ったバージョンの呼び出し</span><span class="sxs-lookup"><span data-stu-id="cd77a-157">Calling a Wrong Version of an Overloaded Procedure</span></span>  
 <span data-ttu-id="cd77a-158">プロシージャにいくつかのオーバー ロードされたバージョンがある場合に、すべてのパラメーター リストに習熟して理解してください方法[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]オーバー ロード間の呼び出しを解決します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-158">If a procedure has several overloaded versions, you should be familiar with all their parameter lists and understand how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] resolves calls among the overloads.</span></span> <span data-ttu-id="cd77a-159">それ以外の場合、意図したもの以外オーバー ロードを呼び出す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cd77a-159">Otherwise you could call an overload other than the intended one.</span></span>  
  
 <span data-ttu-id="cd77a-160">どのオーバー ロードを呼び出したいを特定する場合は、次の規則に注意してください。</span><span class="sxs-lookup"><span data-stu-id="cd77a-160">When you have determined which overload you want to call, be careful to observe the following rules:</span></span>  
  
-   <span data-ttu-id="cd77a-161">引数、および正しい順序では、正しい番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-161">Supply the correct number of arguments, and in the correct order.</span></span>  
  
-   <span data-ttu-id="cd77a-162">理想的には、引数には、対応するパラメーターとまったく同じデータ型が必要です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-162">Ideally, your arguments should have the exact same data types as the corresponding parameters.</span></span> <span data-ttu-id="cd77a-163">いずれの場合は、各引数のデータ型が、対応するパラメーターに拡大変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd77a-163">In any case, the data type of each argument must widen to that of its corresponding parameter.</span></span> <span data-ttu-id="cd77a-164">これは、true を使用しても、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)'éý'`Off`です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-164">This is true even with the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) set to `Off`.</span></span> <span data-ttu-id="cd77a-165">オーバー ロードをオーバー ロードする、引数リストから縮小変換を必要とする場合は、呼び出される対象となるではありません。</span><span class="sxs-lookup"><span data-stu-id="cd77a-165">If an overload requires any narrowing conversion from your argument list, that overload is not eligible to be called.</span></span>  
  
-   <span data-ttu-id="cd77a-166">拡大変換を必要とする引数を指定する場合は、対応するパラメーターのデータ型にできるだけ近いデータ型を確認します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-166">If you supply arguments that require widening, make their data types as close as possible to the corresponding parameter data types.</span></span> <span data-ttu-id="cd77a-167">2 つまたは複数のオーバー ロードは、引数のデータ型を受け取る、コンパイラは拡大量の最小のオーバー ロードへの呼び出しを解決します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-167">If two or more overloads accept your argument data types, the compiler resolves your call to the overload that calls for the least amount of widening.</span></span>  
  
 <span data-ttu-id="cd77a-168">使用してデータ型の不一致の可能性を低くことができます、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)引数を指定するとき、変換キーワード。</span><span class="sxs-lookup"><span data-stu-id="cd77a-168">You can reduce the chance of data type mismatches by using the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) conversion keyword when preparing your arguments.</span></span>  
  
### <a name="overload-resolution-failure"></a><span data-ttu-id="cd77a-169">オーバー ロードの解決に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="cd77a-169">Overload Resolution Failure</span></span>  
 <span data-ttu-id="cd77a-170">オーバー ロードされたプロシージャを呼び出すときに、コンパイラは、オーバー ロードの 1 つだけを削除しようとします。</span><span class="sxs-lookup"><span data-stu-id="cd77a-170">When you call an overloaded procedure, the compiler attempts to eliminate all but one of the overloads.</span></span> <span data-ttu-id="cd77a-171">成功した場合は、そのオーバー ロードへの呼び出しを解決します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-171">If it succeeds, it resolves the call to that overload.</span></span> <span data-ttu-id="cd77a-172">すべてのオーバー ロードがなく、オーバー ロード候補を 1 つを減らすことはできない場合や、エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-172">If it eliminates all the overloads, or if it cannot reduce the eligible overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="cd77a-173">次の例では、オーバー ロードの解決プロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-173">The following example illustrates the overload resolution process.</span></span>  
  
 [!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]  
  
 <span data-ttu-id="cd77a-174">コンパイラがあるため最初のオーバー ロードを排除最初の呼び出しで最初の引数の型 (`Short`)、対応するパラメーターの型へ縮小変換 (`Byte`)。</span><span class="sxs-lookup"><span data-stu-id="cd77a-174">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="cd77a-175">次に除去 3 番目のオーバー ロードは、2 番目のオーバー ロードで各引数の型 (`Short`と`Single`) 3 番目のオーバー ロードでは、対応する型に拡大変換 (`Integer`と`Single`)。</span><span class="sxs-lookup"><span data-stu-id="cd77a-175">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="cd77a-176">2 番目のオーバー ロードが必要な小さい拡大ので、コンパイラは、呼び出しに使用します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-176">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="cd77a-177">2 番目の呼び出しでは、コンパイラは縮小に基づいてオーバー ロードのいずれかで除去ことはできません。</span><span class="sxs-lookup"><span data-stu-id="cd77a-177">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="cd77a-178">引数の型の少ない拡大変換と 2 番目のオーバー ロードを呼び出すことがあるため最初の呼び出しと同様に、同じ理由から、3 番目のオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-178">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="cd77a-179">ただし、コンパイラは、最初と 2 番目のオーバー ロードの解決できません。</span><span class="sxs-lookup"><span data-stu-id="cd77a-179">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="cd77a-180">それぞれが、他の対応する型に拡大する 1 つの定義済みパラメーターの型 (`Byte`に`Short`が`Single`に`Double`)。</span><span class="sxs-lookup"><span data-stu-id="cd77a-180">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="cd77a-181">そのため、コンパイラには、オーバー ロードの解決エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="cd77a-181">The compiler therefore generates an overload resolution error.</span></span>  
  
 <span data-ttu-id="cd77a-182">**適切なアプローチ:**にあいまいさを排除オーバー ロードされたプロシージャを呼び出すには、次のように使用します。 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)パラメーターの型引数のデータ型を一致するようにします。</span><span class="sxs-lookup"><span data-stu-id="cd77a-182">**Correct Approach:** To be able to call an overloaded procedure without ambiguity, use [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to match the argument data types to the parameter types.</span></span> <span data-ttu-id="cd77a-183">次の例への呼び出しを示しています。`z`を強制的に 2 番目のオーバー ロードに解決します。</span><span class="sxs-lookup"><span data-stu-id="cd77a-183">The following example shows a call to `z` that forces resolution to the second overload.</span></span>  
  
 [!code-vb[VbVbcnProcedures#65](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="cd77a-184">省略可能な解像度と ParamArray 引数にオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="cd77a-184">Overload Resolution with Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="cd77a-185">最後のパラメーターを宣言する点を除いて、プロシージャの 2 つのオーバー ロードが同じシグネチャを持つ場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)いずれかでと[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)他のコンパイラがそのプロシージャの呼び出しを解決最も近いに従っています。</span><span class="sxs-lookup"><span data-stu-id="cd77a-185">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure according to the closest match.</span></span> <span data-ttu-id="cd77a-186">詳細については、次を参照してください。[オーバー ロードの解決](./overload-resolution.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd77a-186">For more information, see [Overload Resolution](./overload-resolution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd77a-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd77a-187">See Also</span></span>  
 [<span data-ttu-id="cd77a-188">手順</span><span class="sxs-lookup"><span data-stu-id="cd77a-188">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="cd77a-189">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="cd77a-189">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="cd77a-190">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="cd77a-190">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="cd77a-191">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="cd77a-191">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="cd77a-192">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="cd77a-192">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="cd77a-193">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="cd77a-193">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="cd77a-194">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="cd77a-194">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="cd77a-195">プロシージャのオーバーロードに関する注意事項</span><span class="sxs-lookup"><span data-stu-id="cd77a-195">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="cd77a-196">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="cd77a-196">Overload Resolution</span></span>](./overload-resolution.md)
