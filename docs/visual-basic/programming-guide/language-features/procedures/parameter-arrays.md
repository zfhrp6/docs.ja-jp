---
title: "パラメーター配列 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8ca2b5f02ac4fb3eb613488c8a9852eb2aa4ce5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="parameter-arrays-visual-basic"></a><span data-ttu-id="527ad-102">パラメーター配列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="527ad-102">Parameter Arrays (Visual Basic)</span></span>
<span data-ttu-id="527ad-103">通常、プロシージャ宣言で指定より引数を持つプロシージャを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="527ad-103">Usually, you cannot call a procedure with more arguments than the procedure declaration specifies.</span></span> <span data-ttu-id="527ad-104">不特定多数の引数が必要なときを宣言できます、*パラメーター配列*、これにより、プロシージャ パラメーターの値の配列を受け入れるようにします。</span><span class="sxs-lookup"><span data-stu-id="527ad-104">When you need an indefinite number of arguments, you can declare a *parameter array*, which allows a procedure to accept an array of values for a parameter.</span></span> <span data-ttu-id="527ad-105">プロシージャを定義するときに、パラメーター配列内の要素の数を把握する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="527ad-105">You do not have to know the number of elements in the parameter array when you define the procedure.</span></span> <span data-ttu-id="527ad-106">配列のサイズは、プロシージャ呼び出しごとに個別に決定されます。</span><span class="sxs-lookup"><span data-stu-id="527ad-106">The array size is determined individually by each call to the procedure.</span></span>  
  
## <a name="declaring-a-paramarray"></a><span data-ttu-id="527ad-107">ParamArray を宣言します。</span><span class="sxs-lookup"><span data-stu-id="527ad-107">Declaring a ParamArray</span></span>  
 <span data-ttu-id="527ad-108">使用する、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター リストでは、パラメーター配列を示すキーワードです。</span><span class="sxs-lookup"><span data-stu-id="527ad-108">You use the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) keyword to denote a parameter array in the parameter list.</span></span> <span data-ttu-id="527ad-109">次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="527ad-109">The following rules apply:</span></span>  
  
-   <span data-ttu-id="527ad-110">プロシージャが 1 つだけのパラメーター配列を定義およびプロシージャの定義の最後のパラメーターをする必要があります。</span><span class="sxs-lookup"><span data-stu-id="527ad-110">A procedure can define only one parameter array, and it must be the last parameter in the procedure definition.</span></span>  
  
-   <span data-ttu-id="527ad-111">パラメーター配列は、値で渡される必要があります。</span><span class="sxs-lookup"><span data-stu-id="527ad-111">The parameter array must be passed by value.</span></span> <span data-ttu-id="527ad-112">明示的に指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャの定義のキーワードです。</span><span class="sxs-lookup"><span data-stu-id="527ad-112">It is good programming practice to explicitly include the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword in the procedure definition.</span></span>  
  
-   <span data-ttu-id="527ad-113">パラメーター配列は、自動的に省略可能です。</span><span class="sxs-lookup"><span data-stu-id="527ad-113">The parameter array is automatically optional.</span></span> <span data-ttu-id="527ad-114">既定値は、パラメーター配列の要素の型の空の 1 次元配列です。</span><span class="sxs-lookup"><span data-stu-id="527ad-114">Its default value is an empty one-dimensional array of the parameter array's element type.</span></span>  
  
-   <span data-ttu-id="527ad-115">パラメーター配列の前のすべてのパラメーターを必須にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="527ad-115">All parameters preceding the parameter array must be required.</span></span> <span data-ttu-id="527ad-116">パラメーター配列は、のみ省略可能なパラメーターである必要があります。</span><span class="sxs-lookup"><span data-stu-id="527ad-116">The parameter array must be the only optional parameter.</span></span>  
  
## <a name="calling-a-paramarray"></a><span data-ttu-id="527ad-117">ParamArray を呼び出す</span><span class="sxs-lookup"><span data-stu-id="527ad-117">Calling a ParamArray</span></span>  
 <span data-ttu-id="527ad-118">パラメーター配列を定義するプロシージャを呼び出すときに、次の方法のいずれかで、引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="527ad-118">When you call a procedure that defines a parameter array, you can supply the argument in any one of the following ways:</span></span>  
  
-   <span data-ttu-id="527ad-119">何も — は、省略できます、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)引数。</span><span class="sxs-lookup"><span data-stu-id="527ad-119">Nothing — that is, you can omit the [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) argument.</span></span> <span data-ttu-id="527ad-120">この場合、空の配列は、プロシージャに渡されます。</span><span class="sxs-lookup"><span data-stu-id="527ad-120">In this case, an empty array is passed to the procedure.</span></span> <span data-ttu-id="527ad-121">渡すことも、 [Nothing](../../../../visual-basic/language-reference/nothing.md)キーワードは、同じ効果を持つ。</span><span class="sxs-lookup"><span data-stu-id="527ad-121">You can also pass the [Nothing](../../../../visual-basic/language-reference/nothing.md) keyword, with the same effect.</span></span>  
  
-   <span data-ttu-id="527ad-122">任意の数の引数、コンマ区切りの一覧。</span><span class="sxs-lookup"><span data-stu-id="527ad-122">A list of an arbitrary number of arguments, separated by commas.</span></span> <span data-ttu-id="527ad-123">各引数のデータ型は暗黙的に変換する必要があります、`ParamArray`要素の型。</span><span class="sxs-lookup"><span data-stu-id="527ad-123">The data type of each argument must be implicitly convertible to the `ParamArray` element type.</span></span>  
  
-   <span data-ttu-id="527ad-124">同じ要素を持つ配列は、パラメーター配列の要素型として入力します。</span><span class="sxs-lookup"><span data-stu-id="527ad-124">An array with the same element type as the parameter array's element type.</span></span>  
  
 <span data-ttu-id="527ad-125">すべての場合、プロシージャ内のコード、パラメーターは配列として扱いますと同じデータ型の要素を持つ 1 次元配列、`ParamArray`データ型。</span><span class="sxs-lookup"><span data-stu-id="527ad-125">In all cases, the code within the procedure treats the parameter array as a one-dimensional array with elements of the same data type as the `ParamArray` data type.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="527ad-126">無制限に大きくなることが、配列を処理するたびに、アプリケーションの内部の容量を超過してしまうリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="527ad-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="527ad-127">パラメーター配列を受け取る場合は、呼び出し元のコードによって渡される配列のサイズをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="527ad-127">If you accept a parameter array, you should test for the size of the array that the calling code passed to it.</span></span> <span data-ttu-id="527ad-128">アプリケーションには大きすぎる場合は、適切な手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="527ad-128">Take appropriate steps if it is too large for your application.</span></span> <span data-ttu-id="527ad-129">詳細については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="527ad-129">For more information, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="527ad-130">例</span><span class="sxs-lookup"><span data-stu-id="527ad-130">Example</span></span>  
 <span data-ttu-id="527ad-131">次の例を定義し、関数を呼び出す`calcSum`です。</span><span class="sxs-lookup"><span data-stu-id="527ad-131">The following example defines and calls the function `calcSum`.</span></span> <span data-ttu-id="527ad-132">`ParamArray`パラメーター修飾子`args`可変個の引数を受け入れるように関数を有効にします。</span><span class="sxs-lookup"><span data-stu-id="527ad-132">The `ParamArray` modifier for the parameter `args` enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 <span data-ttu-id="527ad-133">次の例では、パラメーター配列を持つプロシージャを定義し、パラメーター配列に渡されるすべての配列要素の値を出力します。</span><span class="sxs-lookup"><span data-stu-id="527ad-133">The following example defines a procedure with a parameter array, and outputs the values of all the array elements passed to the parameter array.</span></span>  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="527ad-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="527ad-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="527ad-135">手順</span><span class="sxs-lookup"><span data-stu-id="527ad-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="527ad-136">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="527ad-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="527ad-137">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="527ad-137">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="527ad-138">位置と名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="527ad-138">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="527ad-139">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="527ad-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="527ad-140">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="527ad-140">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="527ad-141">配列</span><span class="sxs-lookup"><span data-stu-id="527ad-141">Arrays</span></span>](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="527ad-142">Optional</span><span class="sxs-lookup"><span data-stu-id="527ad-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
