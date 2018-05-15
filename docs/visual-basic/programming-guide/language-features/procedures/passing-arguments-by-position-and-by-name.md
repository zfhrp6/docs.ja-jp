---
title: 位置と名前による引数渡し (Visual Basic)
ms.date: 02/01/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49e313b2d5aa8302ea4b99e643e09f7b43659785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="5b933-102">位置と名前による引数渡し (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b933-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="5b933-103">呼び出すと、`Sub`または`Function`プロシージャの引数を渡すことができます*位置によって*— プロシージャの定義に表示される順序で — 渡したりすることができます*名前によって*、なし配置を考慮します。</span><span class="sxs-lookup"><span data-stu-id="5b933-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="5b933-104">宣言されている引数の名前、コロンと等号 (=) を指定する名前で引数を渡す場合 (`:=`)、その後に、引数の値。</span><span class="sxs-lookup"><span data-stu-id="5b933-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="5b933-105">任意の順序で名前付き引数を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="5b933-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="5b933-106">たとえば、次`Sub`プロシージャでは、3 つの引数。</span><span class="sxs-lookup"><span data-stu-id="5b933-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 <span data-ttu-id="5b933-107">このプロシージャを呼び出すときは、位置、名、または両方の組み合わせを使用して引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5b933-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="5b933-108">位置による引数渡し</span><span class="sxs-lookup"><span data-stu-id="5b933-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="5b933-109">呼び出すことができます、`Display`その引数を持つメソッドが位置によって渡され、次の例に示すように、コンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="5b933-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 <span data-ttu-id="5b933-110">位置指定引数リストで省略可能な引数を省略した場合、コンマでは、その場所を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b933-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="5b933-111">次の例では、`Display`メソッドなし、`age`引数。</span><span class="sxs-lookup"><span data-stu-id="5b933-111">The following example calls the `Display` method without the `age` argument:</span></span>  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="5b933-112">名前による引数渡し</span><span class="sxs-lookup"><span data-stu-id="5b933-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="5b933-113">代わりに、呼び出すことができます`Display`、名前によって渡される引数でもコンマで区切られた、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="5b933-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 <span data-ttu-id="5b933-114">この方法で名前による引数渡しは、1 つ以上の省略可能な引数を持つプロシージャを呼び出す場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="5b933-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="5b933-115">名前で引数を指定する場合、引数の位置を示すためにコンマを使用するはありません。</span><span class="sxs-lookup"><span data-stu-id="5b933-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="5b933-116">名前による引数渡しもやすく引数を渡し、どれを省略しているを追跡するためです。</span><span class="sxs-lookup"><span data-stu-id="5b933-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="5b933-117">位置と名前による引数の混在</span><span class="sxs-lookup"><span data-stu-id="5b933-117">Mixing Arguments by Position and by Name</span></span>  

<span data-ttu-id="5b933-118">次の例で示すように、両方の位置と、1 つのプロシージャ呼び出しで名前による引数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5b933-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 <span data-ttu-id="5b933-119">上記の例では、余分なコンマは省略された場所を保持するために必要な`age`引数、ので`birth`は名前によって渡されます。</span><span class="sxs-lookup"><span data-stu-id="5b933-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
<span data-ttu-id="5b933-120">15.5 前に、のバージョンの Visual Basic での位置と名前、位置指定引数の組み合わせで引数を指定するときにする必要がありますすべて先に指定します。</span><span class="sxs-lookup"><span data-stu-id="5b933-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="5b933-121">名前で引数を指定すると、残りの引数必要がありますすべてで渡される名前。</span><span class="sxs-lookup"><span data-stu-id="5b933-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="5b933-122">たとえば、次の呼び出し、`Display`メソッドには、コンパイラ エラーが表示されます。 [BC30241: 名前付き引数が期待どおり](../../../misc/bc30241.md)です。</span><span class="sxs-lookup"><span data-stu-id="5b933-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

<span data-ttu-id="5b933-123">Visual Basic 15.5 から始めて、位置指定引数は、名前付き引数終了の位置指定引数が正しい位置にある場合。</span><span class="sxs-lookup"><span data-stu-id="5b933-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="5b933-124">Visual Basic 15.5、前の呼び出しでコンパイルされた場合、`Display`メソッドが正常にコンパイルし、コンパイラ エラーが発生しなく[BC30241](../../../misc/bc30241.md)です。</span><span class="sxs-lookup"><span data-stu-id="5b933-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>  

<span data-ttu-id="5b933-125">混在させるし、任意の順序で名前付きおよび位置指定引数を照合するには、この機能は、コードを読みやすくする名前付き引数を使用するときに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="5b933-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="5b933-126">たとえば、次`Person`クラスのコンス トラクターには、型の 2 つの引数が必要です。 `Person`、どちらも指定できます`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="5b933-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span> 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

<span data-ttu-id="5b933-127">ときに、コードの意図を作成するために役立ちますオフ、混合の名前付きおよび位置指定引数を使用しての値、`father`と`mother`引数は`Nothing`:</span><span class="sxs-lookup"><span data-stu-id="5b933-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

<span data-ttu-id="5b933-128">名前付き引数による位置指定引数を次に、Visual Basic プロジェクトに次の要素を追加する必要があります (\*.vbproj) ファイル。</span><span class="sxs-lookup"><span data-stu-id="5b933-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="5b933-129">名前による引数渡しに関する制限事項</span><span class="sxs-lookup"><span data-stu-id="5b933-129">Restrictions on Supplying Arguments by Name</span></span>  

<span data-ttu-id="5b933-130">必須の引数を入力せずに名前で引数を渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="5b933-130">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="5b933-131">省略可能な引数だけを省略できます。</span><span class="sxs-lookup"><span data-stu-id="5b933-131">You can omit only the optional arguments.</span></span>  
  
<span data-ttu-id="5b933-132">名前で、パラメーター配列を渡すことはできません。</span><span class="sxs-lookup"><span data-stu-id="5b933-132">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="5b933-133">これは、プロシージャを呼び出すときのパラメーター配列に対してコンマで区切った不特定数を指定して、コンパイラは、単一の名前を 1 つ以上の引数を関連付けることはできませんです。</span><span class="sxs-lookup"><span data-stu-id="5b933-133">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b933-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b933-134">See Also</span></span>  
 [<span data-ttu-id="5b933-135">手順</span><span class="sxs-lookup"><span data-stu-id="5b933-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="5b933-136">プロシージャのパラメーターと引数</span><span class="sxs-lookup"><span data-stu-id="5b933-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5b933-137">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="5b933-137">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="5b933-138">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="5b933-138">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="5b933-139">省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="5b933-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="5b933-140">パラメーター配列</span><span class="sxs-lookup"><span data-stu-id="5b933-140">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="5b933-141">Optional</span><span class="sxs-lookup"><span data-stu-id="5b933-141">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="5b933-142">ParamArray</span><span class="sxs-lookup"><span data-stu-id="5b933-142">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
