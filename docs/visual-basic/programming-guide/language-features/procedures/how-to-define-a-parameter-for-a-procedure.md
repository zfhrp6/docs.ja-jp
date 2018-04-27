---
title: '方法: プロシージャに対してパラメーターを定義する (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eb4bac9208c03fd18e1904f58b247824d2c215da
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="f8ee6-102">方法: プロシージャに対してパラメーターを定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8ee6-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>
<span data-ttu-id="f8ee6-103">A*パラメーター*に呼び出したときに、プロシージャに値を渡すには、呼び出し元のコードを許可します。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="f8ee6-104">プロシージャの各パラメーターを宣言すると、変数を宣言すると、その名前とデータ型を指定するのと同様にします。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="f8ee6-105">また、渡す方法を指定するパラメーターは省略可能かどうか。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="f8ee6-106">詳細については、次を参照してください。[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="f8ee6-107">プロシージャ パラメーターを定義するには</span><span class="sxs-lookup"><span data-stu-id="f8ee6-107">To define a procedure parameter</span></span>  
  
1.  <span data-ttu-id="f8ee6-108">プロシージャ宣言では、プロシージャのパラメーター リスト、コンマでその他のパラメーターから分離することをパラメーター名を追加します。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2.  <span data-ttu-id="f8ee6-109">パラメーターのデータ型を決定します。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-109">Decide the data type of the parameter.</span></span>  
  
3.  <span data-ttu-id="f8ee6-110">パラメーター名に続けて、`As`句をデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4.  <span data-ttu-id="f8ee6-111">パラメーターの引き渡し方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="f8ee6-112">通常、値は呼び出し元のコードを変更できるようにする手順をしない場合に、値でパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5.  <span data-ttu-id="f8ee6-113">パラメーター名の前に記述しなければ[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引渡し方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-113">Precede the parameter name with [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="f8ee6-114">詳細については、次を参照してください。[の相違点の間で値と参照渡しによって引数の渡し](./differences-between-passing-an-argument-by-value-and-by-reference.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6.  <span data-ttu-id="f8ee6-115">パラメーターが省略可能な場合は、前に渡し[省略可能](../../../../visual-basic/language-reference/modifiers/optional.md)等号 (=) でパラメーターのデータ型に従います (`=`)、既定値は。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="f8ee6-116">次の例の輪郭の定義、 `Sub` 3 つのパラメーターを持つプロシージャ。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="f8ee6-117">最初の 2 つが必要と 3 つ目は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="f8ee6-118">パラメーターの宣言は、パラメーター リストではコンマで区切られます。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     <span data-ttu-id="f8ee6-119">最初のパラメーターを受け入れる、`customer`オブジェクト、および`updateCustomer`に渡された変数を直接更新できます`c`引数が渡されるため[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-119">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="f8ee6-120">渡されるために、プロシージャが最後の 2 つの引数の値を変更できません[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)です。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-120">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="f8ee6-121">呼び出し元のコードがの値を指定しないかどうか、`level`パラメーター、Visual Basic 設定が既定値は 0 にします。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-121">If the calling code does not supply a value for the `level` parameter, Visual Basic sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="f8ee6-122">型チェック スイッチの場合 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`Off`、`As`パラメーターを定義するときに、句は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="f8ee6-123">ただし、すべて 1 つのパラメーターで使用する場合、`As`句、それらのすべて使用する必要の。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-123">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="f8ee6-124">場合は、型チェック スイッチ`On`、`As`句がパラメーター定義のそれぞれに必要です。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-124">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="f8ee6-125">すべてのプログラミング要素のデータ型の指定と呼びます*厳密な型指定*です。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-125">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="f8ee6-126">設定すると`Option Strict On`、Visual Basic では、厳密な型指定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-126">When you set `Option Strict On`, Visual Basic enforces strong typing.</span></span> <span data-ttu-id="f8ee6-127">これを強くお勧め、次の理由。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-127">This is strongly recommended, for the following reasons:</span></span>  
  
    -   <span data-ttu-id="f8ee6-128">変数およびパラメーターについての IntelliSense サポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-128">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="f8ee6-129">これにより、コードに入力すると、そのプロパティおよびその他のメンバーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-129">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    -   <span data-ttu-id="f8ee6-130">これにより、コンパイラが型チェックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-130">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="f8ee6-131">これは、オーバーフローなどのエラーにより実行時に失敗するステートメントを検出するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-131">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="f8ee6-132">それらをサポートしないオブジェクトに対するメソッドの呼び出しをキャッチします。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-132">It also catches calls to methods on objects that do not support them.</span></span>  
  
    -   <span data-ttu-id="f8ee6-133">コードの実行を高速になります。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-133">It results in faster execution of your code.</span></span> <span data-ttu-id="f8ee6-134">理由は、1 つがある場合、プログラミング要素のデータ型を指定しないと、Visual Basic コンパイラが割り当てる、`Object`型です。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-134">One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type.</span></span> <span data-ttu-id="f8ee6-135">コンパイル済みのコードは間を変換する必要があります`Object`およびその他のデータ型は、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="f8ee6-135">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ee6-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8ee6-136">See also</span></span>

 [<span data-ttu-id="f8ee6-137">手順</span><span class="sxs-lookup"><span data-stu-id="f8ee6-137">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="f8ee6-138">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f8ee6-138">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="f8ee6-139">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f8ee6-139">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="f8ee6-140">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="f8ee6-140">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="f8ee6-141">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="f8ee6-141">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="f8ee6-142">再帰プロシージャ</span><span class="sxs-lookup"><span data-stu-id="f8ee6-142">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="f8ee6-143">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="f8ee6-143">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="f8ee6-144">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="f8ee6-144">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="f8ee6-145">オブジェクト指向プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8ee6-145">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)  
