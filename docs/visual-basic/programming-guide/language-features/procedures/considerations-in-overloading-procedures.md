---
title: プロシージャのオーバーロードに関する注意事項 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: e1768d0ac03cb6730c4337d7476ae163e75adfd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="92b78-102">プロシージャのオーバーロードに関する注意事項 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92b78-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="92b78-103">プロシージャをオーバー ロードするときに使用する必要あります別*署名*オーバー ロードされたバージョンごとにします。</span><span class="sxs-lookup"><span data-stu-id="92b78-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="92b78-104">通常、このエラーは、各バージョンは、異なるパラメーター リストを指定する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="92b78-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="92b78-105">詳細についてを参照してください「異なる署名」[プロシージャのオーバー ロード](./procedure-overloading.md)です。</span><span class="sxs-lookup"><span data-stu-id="92b78-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="92b78-106">オーバー ロードすることができます、`Function`プロシージャを`Sub`プロシージャをその逆の場合は、異なる署名があるを提供します。</span><span class="sxs-lookup"><span data-stu-id="92b78-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="92b78-107">2 つのオーバー ロードできませんとは異なり、のみ戻り値を持つ 1 つともう一方にないです。</span><span class="sxs-lookup"><span data-stu-id="92b78-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="92b78-108">プロシージャのオーバー ロードするのと同様にプロパティをオーバー ロードできますと同じ制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="92b78-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="92b78-109">ただし、プロシージャをオーバー ロードすることはできません、プロパティ、またはその逆です。</span><span class="sxs-lookup"><span data-stu-id="92b78-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="92b78-110">オーバー ロードされたバージョンに代わる方法</span><span class="sxs-lookup"><span data-stu-id="92b78-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="92b78-111">引数の有無は省略可能またはその数が可変である場合に特にオーバー ロードされたバージョンは、選択肢場合もありますがあります。</span><span class="sxs-lookup"><span data-stu-id="92b78-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="92b78-112">省略可能な引数が必ずしもすべての言語でサポートされていません、パラメーター配列は、Visual Basic に制限に注意してください。</span><span class="sxs-lookup"><span data-stu-id="92b78-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="92b78-113">任意のいくつかの異なる言語で記述されたコードから呼び出される可能性のあるプロシージャを作成している場合に、バージョンによって柔軟性がオーバー ロードされます。</span><span class="sxs-lookup"><span data-stu-id="92b78-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="92b78-114">省略可能な引数とオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="92b78-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="92b78-115">呼び出し元のコードの指定または 1 つまたは複数の引数を省略できます必要に応じて、ときに、複数のオーバー ロードされたバージョンを定義または省略可能なパラメーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="92b78-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="92b78-116">オーバー ロードされたバージョンを使用する場合</span><span class="sxs-lookup"><span data-stu-id="92b78-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="92b78-117">次の場合に、一連のオーバー ロードされたバージョンを定義するを考慮することができます。</span><span class="sxs-lookup"><span data-stu-id="92b78-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="92b78-118">プロシージャ コード内のロジックは、呼び出し元のコードに省略可能な引数が指定されていない、またはかどうかによって大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="92b78-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="92b78-119">プロシージャのコードは、呼び出し元のコードには、省略可能な引数が指定されているかどうかを確実にテストできません。</span><span class="sxs-lookup"><span data-stu-id="92b78-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="92b78-120">これは、ようななどの既定値の値を可能性のある候補がない場合は呼び出し元のコードいないと考えられるを指定します。</span><span class="sxs-lookup"><span data-stu-id="92b78-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="92b78-121">省略可能なパラメーターを使用する場合</span><span class="sxs-lookup"><span data-stu-id="92b78-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="92b78-122">次の場合、1 つまたは複数の省略可能なパラメーターを好む場合があります。</span><span class="sxs-lookup"><span data-stu-id="92b78-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="92b78-123">呼び出し元のコードは省略可能な引数を指定しない場合にのみ必要な操作では、既定値にパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="92b78-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="92b78-124">このような場合は、プロシージャのコードを単純化できますと 1 つ以上の 1 つのバージョンを定義する場合`Optional`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="92b78-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="92b78-125">詳細については、次を参照してください。[省略可能なパラメーター](./optional-parameters.md)です。</span><span class="sxs-lookup"><span data-stu-id="92b78-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="92b78-126">Paramarray とオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="92b78-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="92b78-127">呼び出し元のコードは、可変個の引数を渡すことができます、ときに複数のオーバー ロードされたバージョンを定義したり、パラメーター配列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="92b78-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="92b78-128">オーバー ロードされたバージョンを使用する場合</span><span class="sxs-lookup"><span data-stu-id="92b78-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="92b78-129">次の場合に、一連のオーバー ロードされたバージョンを定義するを考慮することができます。</span><span class="sxs-lookup"><span data-stu-id="92b78-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="92b78-130">呼び出し元のコードことはありませんが合格する少数の値を超えるパラメーター配列にわかります。</span><span class="sxs-lookup"><span data-stu-id="92b78-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="92b78-131">プロシージャ コード内のロジックは、呼び出し元のコードに渡す値の数によって大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="92b78-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="92b78-132">呼び出し元のコードは、異なるデータ型の値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="92b78-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="92b78-133">パラメーター配列を使用する場合</span><span class="sxs-lookup"><span data-stu-id="92b78-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="92b78-134">方が、`ParamArray`パラメーターは、次の場合。</span><span class="sxs-lookup"><span data-stu-id="92b78-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="92b78-135">呼び出し元のコードは、パラメーター配列を渡すことができます数の値を予測できないし、数が多い可能性があります。</span><span class="sxs-lookup"><span data-stu-id="92b78-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="92b78-136">プロシージャのロジックは、呼び出し元のコードを渡します、すべての値に同じ操作を実行するすべての値を反復処理に適しています。</span><span class="sxs-lookup"><span data-stu-id="92b78-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="92b78-137">詳細については、次を参照してください。[パラメーター配列](./parameter-arrays.md)です。</span><span class="sxs-lookup"><span data-stu-id="92b78-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="92b78-138">省略可能なパラメーターの暗黙のオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="92b78-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="92b78-139">使用するプロシージャを[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)パラメータは、省略可能なパラメーターを使用して 1 つと 2 つのオーバー ロードされたプロシージャに相当します。</span><span class="sxs-lookup"><span data-stu-id="92b78-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="92b78-140">これらのいずれかに対応するパラメーター リストで、このようなプロシージャをオーバー ロードできません。</span><span class="sxs-lookup"><span data-stu-id="92b78-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="92b78-141">次の宣言では、この問題を説明します。</span><span class="sxs-lookup"><span data-stu-id="92b78-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 <span data-ttu-id="92b78-142">省略可能なパラメーターを 1 つ以上の手順は、前の例と同様のロジックによって到着暗黙のオーバー ロードの集合であります。</span><span class="sxs-lookup"><span data-stu-id="92b78-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="92b78-143">ParamArray パラメーターの暗黙のオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="92b78-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="92b78-144">コンパイラは、使用するプロシージャを[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)無数のオーバー ロードが互いにどのような呼び出し元のコードを渡しますはパラメーター配列に次のように異なるパラメーター。</span><span class="sxs-lookup"><span data-stu-id="92b78-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="92b78-145">1 つのオーバー ロードの呼び出し元のコードでは引数に指定されていない場合、 `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="92b78-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="92b78-146">1 つのオーバー ロードの 1 次元配列を呼び出し元のコードが提供する場合の`ParamArray`要素の型</span><span class="sxs-lookup"><span data-stu-id="92b78-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="92b78-147">すべての正の整数のいずれかのオーバー ロードの呼び出し元のコードは、それぞれの引数の数を指定した場合、`ParamArray`要素の型</span><span class="sxs-lookup"><span data-stu-id="92b78-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="92b78-148">次の宣言では、これらの暗黙的なオーバー ロードを示しています。</span><span class="sxs-lookup"><span data-stu-id="92b78-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 <span data-ttu-id="92b78-149">パラメーター配列の 1 次元配列を受け取るパラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="92b78-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="92b78-150">ただし、他の暗黙的なオーバー ロードの署名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="92b78-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="92b78-151">次の宣言では、この問題を説明します。</span><span class="sxs-lookup"><span data-stu-id="92b78-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="92b78-152">オーバー ロードの代わりとしてを省略したプログラミング</span><span class="sxs-lookup"><span data-stu-id="92b78-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="92b78-153">パラメーターに異なるデータ型を渡すには、呼び出し元のコードを許可する場合は、別の方法を省略したプログラミングします。</span><span class="sxs-lookup"><span data-stu-id="92b78-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="92b78-154">型チェックにスイッチを設定することができます`Off`いずれかで、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)または[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="92b78-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="92b78-155">パラメーターのデータ型を宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="92b78-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="92b78-156">ただし、このアプローチでは、オーバー ロードと比較して次の欠点があります。</span><span class="sxs-lookup"><span data-stu-id="92b78-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="92b78-157">省略したプログラミングでは、小さく効率的な実行コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="92b78-157">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="92b78-158">プロシージャに渡される可能性がすべてのデータ型をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="92b78-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="92b78-159">呼び出し元のコードが、プロシージャがサポートしていないデータ型を渡すかどうか、コンパイラでエラーが生成されません。</span><span class="sxs-lookup"><span data-stu-id="92b78-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b78-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="92b78-160">See Also</span></span>  
 [<span data-ttu-id="92b78-161">手順</span><span class="sxs-lookup"><span data-stu-id="92b78-161">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="92b78-162">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="92b78-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="92b78-163">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="92b78-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="92b78-164">方法 : プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="92b78-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="92b78-165">方法 : オーバーロードされたプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="92b78-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="92b78-166">方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="92b78-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="92b78-167">方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="92b78-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="92b78-168">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="92b78-168">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="92b78-169">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="92b78-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
