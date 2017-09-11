---
title: "プロシージャのトラブルシューティング (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
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
- troubleshooting Visual Basic, procedures
- procedures, troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures, about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
caps.latest.revision: 17
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
ms.openlocfilehash: a16a03aa8c12e6696f80eeddb96f4f90c3bb7c68
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-procedures-visual-basic"></a><span data-ttu-id="1e204-102">プロシージャのトラブルシューティング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e204-102">Troubleshooting Procedures (Visual Basic)</span></span>
<span data-ttu-id="1e204-103">ここでは、プロシージャを使用する場合に発生することが一般的な問題についてを説明します。</span><span class="sxs-lookup"><span data-stu-id="1e204-103">This page lists some common problems that can occur when working with procedures.</span></span>  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a><span data-ttu-id="1e204-104">Function プロシージャから、配列型を返す</span><span class="sxs-lookup"><span data-stu-id="1e204-104">Returning an Array Type from a Function Procedure</span></span>  
 <span data-ttu-id="1e204-105">場合、`Function`配列のデータ型を返し、使用することはできません、`Function`配列の要素の値を格納する名前。</span><span class="sxs-lookup"><span data-stu-id="1e204-105">If a `Function` procedure returns an array data type, you cannot use the `Function` name to store values in the elements of the array.</span></span> <span data-ttu-id="1e204-106">これを行うしようとすると、コンパイラによって呼び出しとして、`Function`です。</span><span class="sxs-lookup"><span data-stu-id="1e204-106">If you attempt to do this, the compiler interprets it as a call to the `Function`.</span></span> <span data-ttu-id="1e204-107">次の例では、コンパイラ エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="1e204-107">The following example generates compiler errors.</span></span>  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 <span data-ttu-id="1e204-108">`' The following statement generates a`   `COMPILER ERROR`  `.`</span><span class="sxs-lookup"><span data-stu-id="1e204-108">`' The following statement generates a`   `COMPILER ERROR`  `.`</span></span>  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 <span data-ttu-id="1e204-109">`' The following statement generates a`   `COMPILER ERROR`  `.`</span><span class="sxs-lookup"><span data-stu-id="1e204-109">`' The following statement generates a`   `COMPILER ERROR`  `.`</span></span>  
  
 `Return allOnes()`  
  
 `End Function`  
  
 <span data-ttu-id="1e204-110">ステートメント`allOnes(i) = 1`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`無効なデータ型の引数を持つ (シングルトン`Integer`の代わりに、`Integer`配列)。</span><span class="sxs-lookup"><span data-stu-id="1e204-110">The statement `allOnes(i) = 1` generates a compiler error because it appears to call `allOnes` with an argument of the wrong data type (a singleton `Integer` instead of an `Integer` array).</span></span> <span data-ttu-id="1e204-111">ステートメント`Return allOnes()`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`引数なしでします。</span><span class="sxs-lookup"><span data-stu-id="1e204-111">The statement `Return allOnes()` generates a compiler error because it appears to call `allOnes` with no argument.</span></span>  
  
 <span data-ttu-id="1e204-112">**適切なアプローチ。**が返される配列の要素を変更できるようにするには、ローカル変数として内部の配列を定義します。</span><span class="sxs-lookup"><span data-stu-id="1e204-112">**Correct Approach:** To be able to modify the elements of an array that is to be returned, define an internal array as a local variable.</span></span> <span data-ttu-id="1e204-113">次の例では、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="1e204-113">The following example compiles without error.</span></span>  
  
 <span data-ttu-id="1e204-114">[!code-vb[VbVbcnProcedures #&66;](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1e204-114">[!code-vb[VbVbcnProcedures#66](./codesnippet/VisualBasic/troubleshooting-procedures_1.vb)]</span></span>  
  
## <a name="argument-not-being-modified-by-procedure-call"></a><span data-ttu-id="1e204-115">引数は変更されていないプロシージャ呼び出しで</span><span class="sxs-lookup"><span data-stu-id="1e204-115">Argument Not Being Modified by Procedure Call</span></span>  
 <span data-ttu-id="1e204-116">呼び出し元のコードで引数を基になるプログラミングの要素を変更する手順を許可する場合は、参照によって渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e204-116">If you intend to allow a procedure to change a programming element underlying an argument in the calling code, you must pass it by reference.</span></span> <span data-ttu-id="1e204-117">値渡しで渡す場合でも、プロシージャが参照型の引数の要素をアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1e204-117">But a procedure can access the elements of a reference type argument even if you pass it by value.</span></span>  
  
-   <span data-ttu-id="1e204-118">**変数を基になる**します。</span><span class="sxs-lookup"><span data-stu-id="1e204-118">**Underlying Variable**.</span></span> <span data-ttu-id="1e204-119">基になる変数要素自体の値を置き換えるための手順を許可するように、プロシージャには、パラメーターを宣言する必要があります[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)します。</span><span class="sxs-lookup"><span data-stu-id="1e204-119">To allow the procedure to replace the value of the underlying variable element itself, the procedure must declare the parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="1e204-120">また、呼び出し元のコードいない引数かっこで囲んでくださいをオーバーライドするため、`ByRef`渡す機能します。</span><span class="sxs-lookup"><span data-stu-id="1e204-120">Also, the calling code must not enclose the argument in parentheses, because that would override the `ByRef` passing mechanism.</span></span>  
  
-   <span data-ttu-id="1e204-121">**型の要素を参照する**です。</span><span class="sxs-lookup"><span data-stu-id="1e204-121">**Reference Type Elements**.</span></span> <span data-ttu-id="1e204-122">パラメーターを宣言する場合は、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャは、基になる変数要素自体を変更できません。</span><span class="sxs-lookup"><span data-stu-id="1e204-122">If you declare a parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md), the procedure cannot modify the underlying variable element itself.</span></span> <span data-ttu-id="1e204-123">ただし、引数が参照型の場合、変数の値を置き換えることができない場合でも、プロシージャは、ポイントをするには、オブジェクトのメンバー変更できます。</span><span class="sxs-lookup"><span data-stu-id="1e204-123">However, if the argument is a reference type, the procedure can modify the members of the object to which it points, even though it cannot replace the variable's value.</span></span> <span data-ttu-id="1e204-124">たとえば、引数が、配列変数の場合は、プロシージャは、新しい配列を割り当てることはできませんが、1 つまたは複数の要素を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="1e204-124">For example, if the argument is an array variable, the procedure cannot assign a new array to it, but it can change one or more of its elements.</span></span> <span data-ttu-id="1e204-125">変更された要素は、呼び出し元のコードで基になる配列変数に反映されます。</span><span class="sxs-lookup"><span data-stu-id="1e204-125">The changed elements are reflected in the underlying array variable in the calling code.</span></span>  
  
 <span data-ttu-id="1e204-126">次の例では、その要素の値によって、配列変数を実行して、操作を&2; つの手順を定義します。</span><span class="sxs-lookup"><span data-stu-id="1e204-126">The following example defines two procedures that take an array variable by value and operate on its elements.</span></span> <span data-ttu-id="1e204-127">プロシージャ`increase`単純に各要素に&1; を追加します。</span><span class="sxs-lookup"><span data-stu-id="1e204-127">Procedure `increase` simply adds one to each element.</span></span> <span data-ttu-id="1e204-128">プロシージャ`replace`パラメーターに新しい配列を割り当てます`a()`し、各要素に&1; を追加します。</span><span class="sxs-lookup"><span data-stu-id="1e204-128">Procedure `replace` assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="1e204-129">ただし、再割り当ては変わりません呼び出し元のコードで基になる配列変数のため`a()`が宣言されている`ByVal`します。</span><span class="sxs-lookup"><span data-stu-id="1e204-129">However, the reassignment does not affect the underlying array variable in the calling code because `a()` is declared `ByVal`.</span></span>  
  
 <span data-ttu-id="1e204-130">[!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1e204-130">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/troubleshooting-procedures_2.vb)]</span></span>  
  
 <span data-ttu-id="1e204-131">[!code-vb[VbVbcnProcedures #&38;](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1e204-131">[!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/troubleshooting-procedures_3.vb)]</span></span>  
  
 <span data-ttu-id="1e204-132">に対する呼び出しを次の例`increase`と`replace`です。</span><span class="sxs-lookup"><span data-stu-id="1e204-132">The following example makes calls to `increase` and `replace`.</span></span>  
  
 <span data-ttu-id="1e204-133">[!code-vb[VbVbcnProcedures #&37;](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="1e204-133">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/troubleshooting-procedures_4.vb)]</span></span>  
  
 <span data-ttu-id="1e204-134">最初の`MsgBox`表示を呼び出して"increase(n) 後: 11、21、31、41"です。</span><span class="sxs-lookup"><span data-stu-id="1e204-134">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="1e204-135">`n` 、参照型では、`increase`が渡される場合でも、そのメンバーを変更できます`ByVal`します。</span><span class="sxs-lookup"><span data-stu-id="1e204-135">Because `n` is a reference type, `increase` can change its members, even though it is passed `ByVal`.</span></span>  
  
 <span data-ttu-id="1e204-136">2 番目`MsgBox`表示を呼び出して"目後: 11、21、31、41"です。</span><span class="sxs-lookup"><span data-stu-id="1e204-136">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="1e204-137">`n`は`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることで。</span><span class="sxs-lookup"><span data-stu-id="1e204-137">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` by assigning a new array to it.</span></span> <span data-ttu-id="1e204-138">ときに`replace`配列の新しいインスタンスを作成`k`し、ローカル変数に代入`a`への参照が失われた`n`して呼び出し元のコードに渡されます。</span><span class="sxs-lookup"><span data-stu-id="1e204-138">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="1e204-139">メンバーをインクリメントして`a`、ローカル配列のみ`k`が影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="1e204-139">When it increments the members of `a`, only the local array `k` is affected.</span></span>  
  
 <span data-ttu-id="1e204-140">**適切なアプローチ。**を基になる変数要素自体を変更するには、参照渡しで渡します。</span><span class="sxs-lookup"><span data-stu-id="1e204-140">**Correct Approach:** To be able to modify an underlying variable element itself, pass it by reference.</span></span> <span data-ttu-id="1e204-141">次の例の宣言で、変更を表示する`replace`を呼び出し元のコードの別の&1; つの配列を置き換えるようになります。</span><span class="sxs-lookup"><span data-stu-id="1e204-141">The following example shows the change in the declaration of `replace` that allows it to replace one array with another in the calling code.</span></span>  
  
 <span data-ttu-id="1e204-142">[!code-vb[VbVbcnProcedures #&64;](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="1e204-142">[!code-vb[VbVbcnProcedures#64](./codesnippet/VisualBasic/troubleshooting-procedures_5.vb)]</span></span>  
  
## <a name="unable-to-define-an-overload"></a><span data-ttu-id="1e204-143">オーバー ロードを定義できません。</span><span class="sxs-lookup"><span data-stu-id="1e204-143">Unable to Define an Overload</span></span>  
 <span data-ttu-id="1e204-144">プロシージャのオーバー ロードされたバージョンを定義する場合は、同じ名前で別の署名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e204-144">If you want to define an overloaded version of a procedure, you must use the same name but a different signature.</span></span> <span data-ttu-id="1e204-145">コンパイラは、同じシグネチャを持つオーバー ロードの宣言を区別することはできません、エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="1e204-145">If the compiler cannot differentiate your declaration from an overload with the same signature, it generates an error.</span></span>  
  
 <span data-ttu-id="1e204-146">*署名*プロシージャのプロシージャ名とパラメーター リストによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="1e204-146">The *signature* of a procedure is determined by the procedure name and the parameter list.</span></span> <span data-ttu-id="1e204-147">各オーバー ロードは、他のすべてのオーバー ロードと同じ名前である必要がありますが、署名の他のコンポーネントの少なくとも&1; つにそれらすべてを異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e204-147">Each overload must have the same name as all the other overloads but must differ from all of them in at least one of the other components of the signature.</span></span> <span data-ttu-id="1e204-148">詳細については、次を参照してください。[プロシージャのオーバー ロード](./procedure-overloading.md)します。</span><span class="sxs-lookup"><span data-stu-id="1e204-148">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="1e204-149">次の項目場合でも、パラメーター リストには関係ないコンポーネントを示しますプロシージャの署名。</span><span class="sxs-lookup"><span data-stu-id="1e204-149">The following items, even though they pertain to the parameter list, are not components of a procedure's signature:</span></span>  
  
-   <span data-ttu-id="1e204-150">プロシージャ修飾子のキーワードなど`Public`、`Shared`と`Static`</span><span class="sxs-lookup"><span data-stu-id="1e204-150">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
-   <span data-ttu-id="1e204-151">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="1e204-151">Parameter names</span></span>  
  
-   <span data-ttu-id="1e204-152">パラメーター修飾子のキーワードなど`ByRef`と`Optional`</span><span class="sxs-lookup"><span data-stu-id="1e204-152">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
-   <span data-ttu-id="1e204-153">(変換演算子) を除く、戻り値のデータ型</span><span class="sxs-lookup"><span data-stu-id="1e204-153">The data type of the return value (except for a conversion operator)</span></span>  
  
 <span data-ttu-id="1e204-154">プロシージャをオーバー ロードするだけで&1; つ以上前の項目のことはできません。</span><span class="sxs-lookup"><span data-stu-id="1e204-154">You cannot overload a procedure by varying only one or more of the preceding items.</span></span>  
  
 <span data-ttu-id="1e204-155">**適切なアプローチ。**プロシージャのオーバー ロードを定義できるようにするには、署名を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e204-155">**Correct Approach:** To be able to define a procedure overload, you must vary the signature.</span></span> <span data-ttu-id="1e204-156">同じ名前を使用する必要がありますので、数、順序、またはパラメーターのデータ型を変更しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="1e204-156">Because you must use the same name, you must vary the number, order, or data types of the parameters.</span></span> <span data-ttu-id="1e204-157">ジェネリック プロシージャでは、型パラメーターの数を変更できます。</span><span class="sxs-lookup"><span data-stu-id="1e204-157">In a generic procedure, you can vary the number of type parameters.</span></span> <span data-ttu-id="1e204-158">変換演算子で ([CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md))、戻り値の型を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="1e204-158">In a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)), you can vary the return type.</span></span>  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="1e204-159">省略可能な解像度と ParamArray 引数をオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="1e204-159">Overload Resolution with Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="1e204-160">1 つまたは複数のプロシージャをオーバー ロードは場合[省略可能](../../../../visual-basic/language-reference/modifiers/optional.md)パラメーターまたは[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーターのいずれかの複製避ける必要があります、*暗黙のオーバー ロード*します。</span><span class="sxs-lookup"><span data-stu-id="1e204-160">If you are overloading a procedure with one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters or a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you must avoid duplicating any of the *implicit overloads*.</span></span> <span data-ttu-id="1e204-161">詳細については、次を参照してください。[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="1e204-161">For information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a><span data-ttu-id="1e204-162">オーバー ロードされたプロシージャの間違ったバージョンの呼び出し</span><span class="sxs-lookup"><span data-stu-id="1e204-162">Calling a Wrong Version of an Overloaded Procedure</span></span>  
 <span data-ttu-id="1e204-163">プロシージャにいくつかのオーバー ロードされたバージョンがある場合、すべてのパラメーター リストを理解しておく理解しておいてください方法[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]オーバー ロード間の呼び出しを解決します。</span><span class="sxs-lookup"><span data-stu-id="1e204-163">If a procedure has several overloaded versions, you should be familiar with all their parameter lists and understand how [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] resolves calls among the overloads.</span></span> <span data-ttu-id="1e204-164">それ以外の場合、意図したものではないオーバー ロードを呼び出す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1e204-164">Otherwise you could call an overload other than the intended one.</span></span>  
  
 <span data-ttu-id="1e204-165">どのオーバー ロードを呼び出そうとするを決定するには、次の規則に従うように注意します。</span><span class="sxs-lookup"><span data-stu-id="1e204-165">When you have determined which overload you want to call, be careful to observe the following rules:</span></span>  
  
-   <span data-ttu-id="1e204-166">引数、および正しい順序で、正確な数を指定します。</span><span class="sxs-lookup"><span data-stu-id="1e204-166">Supply the correct number of arguments, and in the correct order.</span></span>  
  
-   <span data-ttu-id="1e204-167">理想的には、引数には、対応するパラメーターとまったく同じデータ型が必要です。</span><span class="sxs-lookup"><span data-stu-id="1e204-167">Ideally, your arguments should have the exact same data types as the corresponding parameters.</span></span> <span data-ttu-id="1e204-168">いずれの場合は、各引数のデータ型は、対応するパラメーターに拡大変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e204-168">In any case, the data type of each argument must widen to that of its corresponding parameter.</span></span> <span data-ttu-id="1e204-169">これは、true の場合でも、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)に設定`Off`します。</span><span class="sxs-lookup"><span data-stu-id="1e204-169">This is true even with the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) set to `Off`.</span></span> <span data-ttu-id="1e204-170">オーバー ロードをオーバー ロードする引数リストから任意の縮小変換が必要な場合は、呼び出される対象ではありません。</span><span class="sxs-lookup"><span data-stu-id="1e204-170">If an overload requires any narrowing conversion from your argument list, that overload is not eligible to be called.</span></span>  
  
-   <span data-ttu-id="1e204-171">拡大変換で必要な引数を指定する場合は、対応するパラメーターのデータ型にできるだけ近くにそのデータ型を確認します。</span><span class="sxs-lookup"><span data-stu-id="1e204-171">If you supply arguments that require widening, make their data types as close as possible to the corresponding parameter data types.</span></span> <span data-ttu-id="1e204-172">2 つまたは複数のオーバー ロードは、引数のデータ型を受け取る、コンパイラは、拡大の最低限の呼び出しのオーバー ロードの呼び出しを解決します。</span><span class="sxs-lookup"><span data-stu-id="1e204-172">If two or more overloads accept your argument data types, the compiler resolves your call to the overload that calls for the least amount of widening.</span></span>  
  
 <span data-ttu-id="1e204-173">データ型の不一致の可能性を低くにを使用して、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)引数を指定するとき、変換キーワードです。</span><span class="sxs-lookup"><span data-stu-id="1e204-173">You can reduce the chance of data type mismatches by using the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) conversion keyword when preparing your arguments.</span></span>  
  
### <a name="overload-resolution-failure"></a><span data-ttu-id="1e204-174">オーバー ロードの解決に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="1e204-174">Overload Resolution Failure</span></span>  
 <span data-ttu-id="1e204-175">オーバー ロードされたプロシージャを呼び出すときに、コンパイラは、オーバー ロードの&1; つだけを削除しようとします。</span><span class="sxs-lookup"><span data-stu-id="1e204-175">When you call an overloaded procedure, the compiler attempts to eliminate all but one of the overloads.</span></span> <span data-ttu-id="1e204-176">成功した場合は、そのオーバー ロードの呼び出しを解決します。</span><span class="sxs-lookup"><span data-stu-id="1e204-176">If it succeeds, it resolves the call to that overload.</span></span> <span data-ttu-id="1e204-177">すべてのオーバー ロードを排除または、オーバー ロードの候補を&1; つを減らすことができない場合は、エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="1e204-177">If it eliminates all the overloads, or if it cannot reduce the eligible overloads to a single candidate, it generates an error.</span></span>  
  
 <span data-ttu-id="1e204-178">次の例では、オーバー ロードの解決プロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="1e204-178">The following example illustrates the overload resolution process.</span></span>  
  
 <span data-ttu-id="1e204-179">[!code-vb[VbVbcnProcedures #&62;](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="1e204-179">[!code-vb[VbVbcnProcedures#62](./codesnippet/VisualBasic/troubleshooting-procedures_6.vb)]</span></span>  
  
 <span data-ttu-id="1e204-180">[!code-vb[VbVbcnProcedures #&63;](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="1e204-180">[!code-vb[VbVbcnProcedures#63](./codesnippet/VisualBasic/troubleshooting-procedures_7.vb)]</span></span>  
  
 <span data-ttu-id="1e204-181">最初の呼び出しで、コンパイラが最初のオーバー ロードを排除の最初の引数の型 (`Short`) に対応するパラメーターの型を変更して (`Byte`)。</span><span class="sxs-lookup"><span data-stu-id="1e204-181">In the first call, the compiler eliminates the first overload because the type of the first argument (`Short`) narrows to the type of the corresponding parameter (`Byte`).</span></span> <span data-ttu-id="1e204-182">次に除去&3; 番目のオーバー ロードは、2 番目のオーバー ロードで各引数の型 (`Short`と`Single`)&3; 番目のオーバー ロードでは、対応する型に拡大変換 (`Integer`と`Single`)。</span><span class="sxs-lookup"><span data-stu-id="1e204-182">It then eliminates the third overload because each argument type in the second overload (`Short` and `Single`) widens to the corresponding type in the third overload (`Integer` and `Single`).</span></span> <span data-ttu-id="1e204-183">2 番目のオーバー ロードが必要な拡大が少ないので、コンパイラは、呼び出しの使用します。</span><span class="sxs-lookup"><span data-stu-id="1e204-183">The second overload requires less widening, so the compiler uses it for the call.</span></span>  
  
 <span data-ttu-id="1e204-184">2 番目の呼び出しで、コンパイラは縮小に基づいてオーバー ロードのいずれかを取り除くことはできません。</span><span class="sxs-lookup"><span data-stu-id="1e204-184">In the second call, the compiler cannot eliminate any of the overloads on the basis of narrowing.</span></span> <span data-ttu-id="1e204-185">除外した引数型の&2; 番目のオーバー ロードを呼び出すことがあるため、最初の呼び出しと同様に、同じ理由から&3; 番目のオーバー ロードを除外します。</span><span class="sxs-lookup"><span data-stu-id="1e204-185">It eliminates the third overload for the same reason as in the first call, because it can call the second overload with less widening of the argument types.</span></span> <span data-ttu-id="1e204-186">ただし、コンパイラは、最初と&2; 番目のオーバー ロードの間で解決できません。</span><span class="sxs-lookup"><span data-stu-id="1e204-186">However, the compiler cannot resolve between the first and second overloads.</span></span> <span data-ttu-id="1e204-187">もう一方で対応する型を拡張する&1; つの定義済みパラメーターの型を持つ各 (`Byte`に`Short`が`Single`に`Double`)。</span><span class="sxs-lookup"><span data-stu-id="1e204-187">Each has one defined parameter type that widens to the corresponding type in the other (`Byte` to `Short`, but `Single` to `Double`).</span></span> <span data-ttu-id="1e204-188">そのため、コンパイラは、オーバー ロードの解決エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="1e204-188">The compiler therefore generates an overload resolution error.</span></span>  
  
 <span data-ttu-id="1e204-189">**適切なアプローチ。**あいまいさなしのオーバー ロードされたプロシージャを呼び出すには、次のように使用します。 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)パラメーターの型への引数のデータ型を一致するようにします。</span><span class="sxs-lookup"><span data-stu-id="1e204-189">**Correct Approach:** To be able to call an overloaded procedure without ambiguity, use [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to match the argument data types to the parameter types.</span></span> <span data-ttu-id="1e204-190">次の例では、呼び出しを`z`を強制的に&2; 番目のオーバー ロードを解決します。</span><span class="sxs-lookup"><span data-stu-id="1e204-190">The following example shows a call to `z` that forces resolution to the second overload.</span></span>  
  
 <span data-ttu-id="1e204-191">[!code-vb[VbVbcnProcedures #&65;](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="1e204-191">[!code-vb[VbVbcnProcedures#65](./codesnippet/VisualBasic/troubleshooting-procedures_8.vb)]</span></span>  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a><span data-ttu-id="1e204-192">省略可能な解像度と ParamArray 引数をオーバー ロードします。</span><span class="sxs-lookup"><span data-stu-id="1e204-192">Overload Resolution with Optional and ParamArray Arguments</span></span>  
 <span data-ttu-id="1e204-193">最後のパラメーターを宣言する点を除いて、プロシージャの&2; つのオーバー ロードと同じシグネチャを持つ場合[省略可能](../../../../visual-basic/language-reference/modifiers/optional.md)いずれかでと[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) 、もう一方で、コンパイラは、最も近いに従ってそのプロシージャを呼び出すを解決します。</span><span class="sxs-lookup"><span data-stu-id="1e204-193">If two overloads of a procedure have identical signatures except that the last parameter is declared [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) in one and [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) in the other, the compiler resolves a call to that procedure according to the closest match.</span></span> <span data-ttu-id="1e204-194">詳細については、次を参照してください。[オーバー ロード解決](./overload-resolution.md)します。</span><span class="sxs-lookup"><span data-stu-id="1e204-194">For more information, see [Overload Resolution](./overload-resolution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e204-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e204-195">See Also</span></span>  
 <span data-ttu-id="1e204-196">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="1e204-196">[Procedures](./index.md) </span></span>  
<span data-ttu-id="1e204-197"> [Sub プロシージャ](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="1e204-197"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="1e204-198"> [Function プロシージャ](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="1e204-198"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="1e204-199"> [プロパティ プロシージャ](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="1e204-199"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="1e204-200"> [演算子プロシージャ](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="1e204-200"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="1e204-201"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="1e204-201"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="1e204-202"> [プロシージャのオーバー ロード](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="1e204-202"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="1e204-203"> [プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="1e204-203"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="1e204-204"> [オーバーロードの解決](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="1e204-204"> [Overload Resolution](./overload-resolution.md)</span></span>
