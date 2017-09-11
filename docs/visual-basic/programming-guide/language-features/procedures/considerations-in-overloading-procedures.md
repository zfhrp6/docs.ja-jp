---
title: "プロシージャ (Visual Basic) のオーバー ロードに関する考慮事項 |Microsoft ドキュメント"
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
- signatures, ParamArray arguments
- ParamArray keyword, parameter arrays
- ParamArray keyword, arguments and signatures
- function overloading, implicit overloads for ParamArray
- ParamArray keyword, signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures, overloading
- parameters, lists
- function overloading, typeless programming
- typeless programming
- function overloading, restrictions
- arguments [Visual Basic], optional
- optional arguments, overloading
- signatures, procedure
- parameter lists
- parameter arrays, overloading arguments
- Visual Basic code, parameter lists
- procedure overloading, considerations
- Option Explicit statement
- restrictions, overloading procedures
- procedures, parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
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
ms.openlocfilehash: 486e6c08fe6284cc9b5856fb848f7307a5651120
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="daaec-102">プロシージャのオーバーロードに関する注意事項 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daaec-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="daaec-103">プロシージャをオーバー ロードする場合、さまざまなを使用*署名*オーバー ロードされたバージョンごとにします。</span><span class="sxs-lookup"><span data-stu-id="daaec-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="daaec-104">つまり、通常各バージョンは、異なるパラメーター リストを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="daaec-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="daaec-105">詳細については、「別の署名」を参照してください[プロシージャのオーバー ロード](./procedure-overloading.md)します。</span><span class="sxs-lookup"><span data-stu-id="daaec-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="daaec-106">オーバー ロードすることができます、`Function`プロシージャを`Sub`プロシージャ、その逆の場合は、異なるシグネチャを持つを提供します。</span><span class="sxs-lookup"><span data-stu-id="daaec-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="daaec-107">2 つのオーバー ロードできませんとは異なりのみ戻り値を持つ&1; つと持たないもう一方のです。</span><span class="sxs-lookup"><span data-stu-id="daaec-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="daaec-108">手順については、オーバー ロードするのと同様に、プロパティをオーバー ロードでき、同じ制限があります。</span><span class="sxs-lookup"><span data-stu-id="daaec-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="daaec-109">ただし、プロシージャをオーバー ロードできない、プロパティを使用して、またはその逆です。</span><span class="sxs-lookup"><span data-stu-id="daaec-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="daaec-110">オーバー ロードされたバージョンの代替手段</span><span class="sxs-lookup"><span data-stu-id="daaec-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="daaec-111">引数は省略可能なまたはその数が可変ときに特ににも、オーバー ロードされたバージョンの代替手段がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="daaec-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="daaec-112">省略可能な引数が必ずしもすべての言語でサポートされていませんし、パラメーター配列に限定されることに注意してください[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="daaec-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="daaec-113">複数の異なる言語のいずれかで記述されたコードから呼び出されると思われるプロシージャを作成する場合に、バージョンによって柔軟性がオーバー ロードされます。</span><span class="sxs-lookup"><span data-stu-id="daaec-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="daaec-114">省略可能な引数とオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="daaec-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="daaec-115">呼び出し元のコードの指定または&1; つまたは複数の引数を省略できます必要に応じて場合、は、複数のオーバー ロードされたバージョンを定義するか、省略可能なパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="daaec-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="daaec-116">オーバー ロードされたバージョンを使用する場合</span><span class="sxs-lookup"><span data-stu-id="daaec-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="daaec-117">次の場合に、一連のオーバー ロードされたバージョンを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="daaec-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="daaec-118">プロシージャ コード内のロジックは、呼び出し元のコードが省略可能な引数を提供するかどうかどうかによって大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="daaec-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="daaec-119">プロシージャのコードは、呼び出し元のコードには、省略可能な引数が指定されているかどうかを確実にテストできません。</span><span class="sxs-lookup"><span data-stu-id="daaec-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="daaec-120">これは、大文字と小文字などの既定値の値、候補になる可能性がない場合、呼び出し元コードいないと考えられるを指定します。</span><span class="sxs-lookup"><span data-stu-id="daaec-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="daaec-121">省略可能なパラメーターを使用する場合</span><span class="sxs-lookup"><span data-stu-id="daaec-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="daaec-122">次の場合に&1; つまたは複数の省略可能なパラメーターをすることができます。</span><span class="sxs-lookup"><span data-stu-id="daaec-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="daaec-123">呼び出し元のコードは省略可能な引数を指定しない場合にのみ必要なアクションでは、既定値にパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="daaec-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="daaec-124">このような場合は、プロシージャのコードを単純化できますと&1; つ以上の&1; つのバージョンを定義する場合`Optional`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="daaec-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="daaec-125">詳細については、次を参照してください。[省略可能なパラメーター](./optional-parameters.md)します。</span><span class="sxs-lookup"><span data-stu-id="daaec-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="daaec-126">Paramarray とオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="daaec-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="daaec-127">呼び出し元のコードでは、可変個の引数を渡すことができる場合、は、複数のオーバー ロードされたバージョンを定義するか、パラメーター配列を使用します。</span><span class="sxs-lookup"><span data-stu-id="daaec-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="daaec-128">オーバー ロードされたバージョンを使用する場合</span><span class="sxs-lookup"><span data-stu-id="daaec-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="daaec-129">次の場合に、一連のオーバー ロードされたバージョンを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="daaec-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="daaec-130">呼び出し元のコードことはありませんが合格する少数の値を超えるパラメーターの配列にわかります。</span><span class="sxs-lookup"><span data-stu-id="daaec-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="daaec-131">プロシージャ コード内のロジックは、呼び出し元のコードに渡す値の数によって大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="daaec-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="daaec-132">呼び出し元のコードでは、異なるデータ型の値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="daaec-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="daaec-133">パラメーター配列を使用する場合</span><span class="sxs-lookup"><span data-stu-id="daaec-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="daaec-134">方が適している、`ParamArray`パラメーターは、次の場合。</span><span class="sxs-lookup"><span data-stu-id="daaec-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="daaec-135">呼び出し元のコードは、パラメーターの配列を渡すことができます値の数を予測できないし、数が多い可能性があります。</span><span class="sxs-lookup"><span data-stu-id="daaec-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="daaec-136">プロシージャのロジックは、呼び出し元のコードを渡すと、すべての値に同じ操作を実行するすべての値を反復処理に適しています。</span><span class="sxs-lookup"><span data-stu-id="daaec-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="daaec-137">詳細については、次を参照してください。[パラメーター配列](./parameter-arrays.md)します。</span><span class="sxs-lookup"><span data-stu-id="daaec-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="daaec-138">省略可能なパラメーターの暗黙のオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="daaec-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="daaec-139">使用してプロシージャを[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)パラメータは、省略可能なパラメーターを持つと&2; つのオーバー ロードされたプロシージャに相当します。</span><span class="sxs-lookup"><span data-stu-id="daaec-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="daaec-140">これらのいずれかに対応する、パラメーター リストでこのようなプロシージャをオーバー ロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="daaec-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="daaec-141">次の宣言では、これを示しています。</span><span class="sxs-lookup"><span data-stu-id="daaec-141">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="daaec-142">[!code-vb[VbVbcnProcedures #&58;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="daaec-142">[!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="daaec-143">[!code-vb[VbVbcnProcedures&#60;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="daaec-143">[!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]</span></span>  
  
 <span data-ttu-id="daaec-144">[!code-vb[VbVbcnProcedures&#61;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="daaec-144">[!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]</span></span>  
  
 <span data-ttu-id="daaec-145">手順については、1 つ以上の省略可能なパラメーターでは、前の例と同様のロジックによってに到着した暗黙のオーバー ロードのセット。</span><span class="sxs-lookup"><span data-stu-id="daaec-145">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="daaec-146">暗黙のオーバー ロード (paramarray の) パラメーター</span><span class="sxs-lookup"><span data-stu-id="daaec-146">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="daaec-147">コンパイラは、使用してプロシージャを[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーターを無限数のオーバー ロード、互いにどのような呼び出し元のコードに渡すパラメーターの配列、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="daaec-147">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="daaec-148">1 つのオーバー ロードを呼び出し元のコードでは引数に指定されていない場合、`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="daaec-148">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="daaec-149">1 つのオーバー ロードを呼び出し元のコードでの&1; 次元配列を提供する場合、`ParamArray`要素の型</span><span class="sxs-lookup"><span data-stu-id="daaec-149">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="daaec-150">すべての正の整数のいずれかのオーバー ロードの呼び出し元のコードは、それぞれの引数をその数を指定すると、`ParamArray`要素の型</span><span class="sxs-lookup"><span data-stu-id="daaec-150">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="daaec-151">次の宣言では、これらの暗黙的なオーバー ロードを示しています。</span><span class="sxs-lookup"><span data-stu-id="daaec-151">The following declarations illustrate these implicit overloads.</span></span>  
  
 <span data-ttu-id="daaec-152">[!code-vb[VbVbcnProcedures #&68;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="daaec-152">[!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]</span></span>  
  
 <span data-ttu-id="daaec-153">[!code-vb[VbVbcnProcedures #&70;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="daaec-153">[!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]</span></span>  
  
 <span data-ttu-id="daaec-154">パラメーター配列の&1; 次元配列を受け取り、パラメーター リストで、このようなプロシージャをオーバー ロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="daaec-154">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="daaec-155">ただし、その他の暗黙のオーバー ロードの署名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="daaec-155">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="daaec-156">次の宣言では、これを示しています。</span><span class="sxs-lookup"><span data-stu-id="daaec-156">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="daaec-157">[!code-vb[VbVbcnProcedures #&71;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="daaec-157">[!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]</span></span>  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="daaec-158">オーバー ロードの代わりとしてを省略したプログラミング</span><span class="sxs-lookup"><span data-stu-id="daaec-158">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="daaec-159">パラメーターに異なるデータ型を渡すには、呼び出し元のコードを許可する場合、別の方法を省略したプログラミングします。</span><span class="sxs-lookup"><span data-stu-id="daaec-159">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="daaec-160">型チェックをスイッチを設定する`Off`いずれかで、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)または[/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラ オプション。</span><span class="sxs-lookup"><span data-stu-id="daaec-160">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="daaec-161">パラメーターのデータ型を宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="daaec-161">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="daaec-162">ただし、このアプローチでは、オーバー ロードと比較して、次の欠点があります。</span><span class="sxs-lookup"><span data-stu-id="daaec-162">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="daaec-163">省略したプログラミングでは、効率がよく実行コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="daaec-163">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="daaec-164">プロシージャは、渡されると予想されるすべてのデータ型をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="daaec-164">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="daaec-165">呼び出し元のコードが、プロシージャがサポートされていないデータ型を渡すかどうか、コンパイラでエラーが生成されません。</span><span class="sxs-lookup"><span data-stu-id="daaec-165">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daaec-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="daaec-166">See Also</span></span>  
 <span data-ttu-id="daaec-167">[手順](./index.md) </span><span class="sxs-lookup"><span data-stu-id="daaec-167">[Procedures](./index.md) </span></span>  
<span data-ttu-id="daaec-168"> [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="daaec-168"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="daaec-169"> [トラブルシューティングの手順](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="daaec-169"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="daaec-170"> [方法: プロシージャの複数のバージョンを定義します。](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="daaec-170"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="daaec-171"> [方法: オーバー ロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="daaec-171"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="daaec-172"> [方法: 省略可能なパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="daaec-172"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="daaec-173"> [方法: 不特定数のパラメーターを受け取るプロシージャをオーバー ロード](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="daaec-173"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="daaec-174"> [オーバー ロードの解決](./overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="daaec-174"> [Overload Resolution](./overload-resolution.md) </span></span>  
<span data-ttu-id="daaec-175"> [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="daaec-175"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>
