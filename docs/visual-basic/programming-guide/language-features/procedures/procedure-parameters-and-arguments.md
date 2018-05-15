---
title: プロシージャのパラメーターと引数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
ms.openlocfilehash: b0ab186945b456d7fb4dde3f52724b08a99e2827
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="ae2bd-102">プロシージャのパラメーターと引数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae2bd-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="ae2bd-103">ほとんどの場合、プロシージャが呼び出されたときの状況に関する情報を必要とします。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="ae2bd-104">繰り返しまたは共有のタスクを実行する手順は、呼び出しごとに異なる情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="ae2bd-105">この情報は、変数、定数、およびメソッドを呼び出すときに、プロシージャに渡す式で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="ae2bd-106">A*パラメーター*プロシージャには、このメソッドを呼び出すときに指定することが期待される値を表します。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="ae2bd-107">プロシージャの宣言では、そのパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="ae2bd-108">パラメーターを指定せず、1 つのパラメーター、または 1 つ以上を持つプロシージャを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="ae2bd-109">パラメーターを指定するプロシージャの定義の一部と呼ばれる、*パラメーター リスト*です。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="ae2bd-110">*引数*プロシージャを呼び出す場合、プロシージャのパラメーターに指定した値を表します。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="ae2bd-111">呼び出し元のコードは、プロシージャを呼び出すときに、引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="ae2bd-112">引数を指定するプロシージャ呼び出しの一部と呼ばれる、*引数リスト*です。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="ae2bd-113">次の図は、プロシージャを呼び出すコード`safeSquareRoot`2 つの異なる場所からします。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="ae2bd-114">最初の呼び出しは、変数の値を渡します`x`(4.0) パラメーターに`number`、され、戻り値で`root`(2.0)、変数に割り当てられた`y`です。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="ae2bd-115">2 番目の呼び出しにリテラル値 9.0 に渡します`number`、戻り値 (3.0) を変数に代入し、`z`です。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 <span data-ttu-id="ae2bd-116">![パラメーターに引数を渡すグラフィック ダイアグラム](./media/parametersargue.gif "ParametersArgue")</span><span class="sxs-lookup"><span data-stu-id="ae2bd-116">![Graphic diagram of passing argument to parameter](./media/parametersargue.gif "ParametersArgue")</span></span>  
<span data-ttu-id="ae2bd-117">パラメーターに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="ae2bd-117">Passing an argument to a parameter</span></span>  
  
 <span data-ttu-id="ae2bd-118">詳細については、次を参照してください。[の相違点の間でパラメーターと引数](./differences-between-parameters-and-arguments.md)です。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="ae2bd-119">パラメーターのデータ型</span><span class="sxs-lookup"><span data-stu-id="ae2bd-119">Parameter Data Type</span></span>  
 <span data-ttu-id="ae2bd-120">使用して、パラメーターのデータ型を定義する、`As`宣言内の句。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="ae2bd-121">たとえば、次の関数は、文字列と整数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 <span data-ttu-id="ae2bd-122">型チェック スイッチの場合 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`Off,`、`As`ことを除き、すべてのパラメーターがそれを使用する必要があります任意の 1 つのパラメーターが使用している場合は、句は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="ae2bd-123">型チェックが場合`On`、`As`句はすべてのプロシージャのパラメーターは必須です。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="ae2bd-124">呼び出し元のコードがなど、対応するパラメーターの異なるデータ型の引数を指定するかどうかは`Byte`を`String`パラメーターを次のいずれかの操作にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="ae2bd-125">パラメーターのデータ型に拡大変換するデータ型の引数だけを渡す</span><span class="sxs-lookup"><span data-stu-id="ae2bd-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="ae2bd-126">設定`Option Strict Off`暗黙的な縮小変換です使用できるように、または。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="ae2bd-127">変換キーワードを使用して、データ型を明示的に変換します。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="ae2bd-128">型パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae2bd-128">Type Parameters</span></span>  
 <span data-ttu-id="ae2bd-129">A*ジェネリック プロシージャ*も 1 つまたは複数定義されて*パラメーター入力*だけでなく、通常のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="ae2bd-130">ジェネリック プロシージャでは、個々 の呼び出しの要件をデータ型を調整できるように、プロシージャを呼び出すたびに異なるデータ型を渡すには、呼び出し元のコードを許可します。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="ae2bd-131">「 [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae2bd-131">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2bd-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae2bd-132">See Also</span></span>  
 [<span data-ttu-id="ae2bd-133">手順</span><span class="sxs-lookup"><span data-stu-id="ae2bd-133">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="ae2bd-134">Sub プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ae2bd-134">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="ae2bd-135">Function プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ae2bd-135">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="ae2bd-136">Property プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ae2bd-136">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="ae2bd-137">演算子プロシージャ</span><span class="sxs-lookup"><span data-stu-id="ae2bd-137">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="ae2bd-138">方法 : プロシージャにパラメーターを定義する</span><span class="sxs-lookup"><span data-stu-id="ae2bd-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="ae2bd-139">方法: プロシージャに引数を渡す</span><span class="sxs-lookup"><span data-stu-id="ae2bd-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="ae2bd-140">引数の値渡しと参照渡し</span><span class="sxs-lookup"><span data-stu-id="ae2bd-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="ae2bd-141">プロシージャのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="ae2bd-141">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="ae2bd-142">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="ae2bd-142">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
