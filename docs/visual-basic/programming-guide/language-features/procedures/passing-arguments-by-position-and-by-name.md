---
title: "位置と名前による引数渡し (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="16b0a-102">位置と名前による引数渡し (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16b0a-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="16b0a-103">呼び出すと、`Sub`または`Function`プロシージャの引数を渡すことができます*位置によって*— プロシージャの定義に表示される順序で — 渡したりすることができます*名前によって*、なし配置を考慮します。</span><span class="sxs-lookup"><span data-stu-id="16b0a-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="16b0a-104">宣言されている引数の名前、コロンと等号 (=) を指定する名前で引数を渡す場合 (`:=`)、その後に、引数の値。</span><span class="sxs-lookup"><span data-stu-id="16b0a-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="16b0a-105">任意の順序で名前付き引数を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="16b0a-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="16b0a-106">たとえば、次`Sub`プロシージャでは、3 つの引数。</span><span class="sxs-lookup"><span data-stu-id="16b0a-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 <span data-ttu-id="16b0a-107">このプロシージャを呼び出すときは、位置、名、または両方の組み合わせを使用して引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="16b0a-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="16b0a-108">位置による引数渡し</span><span class="sxs-lookup"><span data-stu-id="16b0a-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="16b0a-109">プロシージャを呼び出すことができます`studentInfo`位置によって渡され、次の例で示すように、コンマで区切り、引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="16b0a-109">You can call the procedure `studentInfo` with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 <span data-ttu-id="16b0a-110">位置指定引数リストで省略可能な引数を省略した場合、コンマでは、その場所を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16b0a-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="16b0a-111">次の例では`studentInfo`せず、`age`引数。</span><span class="sxs-lookup"><span data-stu-id="16b0a-111">The following example calls `studentInfo` without the `age` argument:</span></span>  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="16b0a-112">名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="16b0a-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="16b0a-113">代わりに、呼び出すことができます`studentInfo`、名前によって渡される引数でもコンマで区切られた、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="16b0a-113">Alternatively, you can call `studentInfo` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="16b0a-114">位置と名前による引数の混在</span><span class="sxs-lookup"><span data-stu-id="16b0a-114">Mixing Arguments by Position and by Name</span></span>  
 <span data-ttu-id="16b0a-115">次の例で示すように、両方の位置と、1 つのプロシージャ呼び出しで名前による引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="16b0a-115">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 <span data-ttu-id="16b0a-116">上記の例では、余分なコンマは省略された場所を保持するために必要な`age`引数、ので`birth`は名前によって渡されます。</span><span class="sxs-lookup"><span data-stu-id="16b0a-116">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
 <span data-ttu-id="16b0a-117">位置と名前、位置指定引数の組み合わせで引数を指定するときのすべてを先にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="16b0a-117">When you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="16b0a-118">名前で引数を指定すると、残りの引数すべてがあります名前。</span><span class="sxs-lookup"><span data-stu-id="16b0a-118">Once you supply an argument by name, the remaining arguments must all be by name.</span></span>  
  
## <a name="supplying-optional-arguments-by-name"></a><span data-ttu-id="16b0a-119">省略可能な引数の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="16b0a-119">Supplying Optional Arguments by Name</span></span>  
 <span data-ttu-id="16b0a-120">名前による引数渡しは、1 つ以上の省略可能な引数を持つプロシージャを呼び出す場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="16b0a-120">Passing arguments by name is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="16b0a-121">名前で引数を指定する場合、引数の位置を示すためにコンマを使用するはありません。</span><span class="sxs-lookup"><span data-stu-id="16b0a-121">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="16b0a-122">名前による引数渡しもやすく引数を渡し、どれを省略しているを追跡するためです。</span><span class="sxs-lookup"><span data-stu-id="16b0a-122">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="16b0a-123">名前による引数渡しに関する制限事項</span><span class="sxs-lookup"><span data-stu-id="16b0a-123">Restrictions on Supplying Arguments by Name</span></span>  
 <span data-ttu-id="16b0a-124">必須の引数を入力せずに名前で引数を渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="16b0a-124">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="16b0a-125">省略可能な引数だけを省略できます。</span><span class="sxs-lookup"><span data-stu-id="16b0a-125">You can omit only the optional arguments.</span></span>  
  
 <span data-ttu-id="16b0a-126">名前で、パラメーター配列を渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="16b0a-126">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="16b0a-127">これは、プロシージャを呼び出すときのパラメーター配列に対してコンマで区切った不特定数を指定して、コンパイラは、単一の名前を 1 つ以上の引数を関連付けることはできませんです。</span><span class="sxs-lookup"><span data-stu-id="16b0a-127">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b0a-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="16b0a-128">See Also</span></span>  
 [<span data-ttu-id="16b0a-129">手順</span><span class="sxs-lookup"><span data-stu-id="16b0a-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="16b0a-130">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="16b0a-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="16b0a-131">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="16b0a-131">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="16b0a-132">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="16b0a-132">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="16b0a-133">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="16b0a-133">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="16b0a-134">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="16b0a-134">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="16b0a-135">Optional</span><span class="sxs-lookup"><span data-stu-id="16b0a-135">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="16b0a-136">ParamArray</span><span class="sxs-lookup"><span data-stu-id="16b0a-136">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
