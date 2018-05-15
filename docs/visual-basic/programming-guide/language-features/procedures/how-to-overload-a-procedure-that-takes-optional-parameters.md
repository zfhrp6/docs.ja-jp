---
title: '方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 1da1d67726a9669477721aabc0aace0119aa7e56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="7bfbf-102">方法: 省略可能なパラメーターを受け取るプロシージャをオーバーロードする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bfbf-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="7bfbf-103">プロシージャが 1 つまたは複数場合[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)パラメーター、暗黙的なオーバー ロードのいずれかに一致するオーバー ロード バージョンを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="7bfbf-104">詳細についてを参照してください"暗黙的なオーバー ロードの省略可能なパラメーター"[プロシージャのオーバー ロードでの考慮事項](./considerations-in-overloading-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="7bfbf-105">1 つの省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="7bfbf-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="7bfbf-106">1 つの省略可能なパラメーターを受け取るプロシージャをオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="7bfbf-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="7bfbf-107">書き込み、`Sub`または`Function`パラメーター リストで省略可能なパラメーターを含む宣言ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="7bfbf-108">使用しないで、`Optional`このオーバー ロードされたバージョンではキーワードです。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="7bfbf-109">前に、`Sub`または`Function`キーワード、 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="7bfbf-110">呼び出し元のコードには、省略可能な引数が指定されている場合に実行するプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="7bfbf-111">使用してプロシージャを終了、`End Sub`または`End Function`に応じてステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="7bfbf-112">パラメーター リストで省略可能なパラメーターを含まないする点を除いて、最初の宣言と同じである 2 つ目の宣言ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="7bfbf-113">呼び出し元のコードは、省略可能な引数を指定していない場合に実行するプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="7bfbf-114">使用してプロシージャを終了、`End Sub`または`End Function`に応じてステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="7bfbf-115">次の例では、2 つのオーバー ロードされたプロシージャでは、そして最後に無効なと無効の両方のオーバー ロードされたバージョンの省略可能なパラメーターを指定して定義された手順を示します。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="7bfbf-116">複数の省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="7bfbf-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="7bfbf-117">省略可能なパラメーターを 1 つ以上の手順は、通常 2 つ以上のオーバー ロードされたバージョンを必要です。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="7bfbf-118">たとえば、2 つの省略可能なパラメーターがあると、呼び出し元のコードを指定したり省略とは無関係に、他の 1 つずつ、4 つのオーバー ロードされたバージョンを組み合わせて指定された引数のいずれか必要があります。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="7bfbf-119">省略可能なパラメーターの数が多いほど、オーバー ロードの複雑さが増加します。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="7bfbf-120">指定された引数のいくつかの組み合わせが許されない限り、N の省略可能なパラメーターにする必要があります 2 ^ N のオーバー ロードされたバージョンです。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="7bfbf-121">プロシージャの性質、によって、わかりやすくするためのロジックが妥当な労力をすべてのオーバー ロードされたバージョンを定義することがあります。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="7bfbf-122">1 つ以上の省略可能なパラメーターを受け取るプロシージャをオーバー ロード</span><span class="sxs-lookup"><span data-stu-id="7bfbf-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="7bfbf-123">プロシージャのロジックを受け入れ可能な省略可能な引数の組み合わせが判断します。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="7bfbf-124">無効な組み合わせは、別の 1 つの省略可能なパラメーターが依存している場合に発生する可能性です。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="7bfbf-125">たとえば、1 つのパラメーターは、配偶者の名前を受け入れ、配偶者の年齢を受け取る場合は、経過期間を指定することが、名前を省略する引数の組み合わせは使用できません。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="7bfbf-126">省略可能な引数の許容可能な組み合わせごとに、書き込み、`Sub`または`Function`対応するパラメーター リストを定義する宣言ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="7bfbf-127">使用しないで、`Optional`キーワード。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-127">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="7bfbf-128">各宣言の前に、`Sub`または`Function`キーワード、 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワード。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="7bfbf-129">次の各宣言には、呼び出し元のコードは、その宣言のパラメーター リストに対応する引数リストを指定した場合に実行するプロシージャ コードを記述します。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="7bfbf-130">各プロシージャの終了、`End Sub`または`End Function`に応じてステートメントです。</span><span class="sxs-lookup"><span data-stu-id="7bfbf-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfbf-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="7bfbf-131">See Also</span></span>  
 [<span data-ttu-id="7bfbf-132">手順</span><span class="sxs-lookup"><span data-stu-id="7bfbf-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="7bfbf-133">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="7bfbf-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="7bfbf-134">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="7bfbf-134">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="7bfbf-135">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="7bfbf-135">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="7bfbf-136">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="7bfbf-136">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="7bfbf-137">プロシージャのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7bfbf-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="7bfbf-138">方法 : プロシージャの複数のバージョンを定義する</span><span class="sxs-lookup"><span data-stu-id="7bfbf-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="7bfbf-139">方法 : オーバーロードされたプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="7bfbf-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="7bfbf-140">方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする</span><span class="sxs-lookup"><span data-stu-id="7bfbf-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="7bfbf-141">オーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="7bfbf-141">Overload Resolution</span></span>](./overload-resolution.md)
