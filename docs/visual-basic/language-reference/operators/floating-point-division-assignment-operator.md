---
title: /= 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 642307bc531e7d9ce21a932b112795b35e7b3182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604095"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="18875-102">/= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18875-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="18875-103">変数またはプロパティの値式の値で除算し、浮動小数点の結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="18875-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18875-104">構文</span><span class="sxs-lookup"><span data-stu-id="18875-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="18875-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="18875-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="18875-106">必須。</span><span class="sxs-lookup"><span data-stu-id="18875-106">Required.</span></span> <span data-ttu-id="18875-107">任意の数値型の変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="18875-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="18875-108">必須。</span><span class="sxs-lookup"><span data-stu-id="18875-108">Required.</span></span> <span data-ttu-id="18875-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="18875-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18875-110">コメント</span><span class="sxs-lookup"><span data-stu-id="18875-110">Remarks</span></span>  
 <span data-ttu-id="18875-111">左側にある要素、`/=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="18875-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="18875-112">変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="18875-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="18875-113">`/=`最初は、変数または (演算子の左側にある) のプロパティの値が演算子によって (演算子の右側にある) の式の値で除算します。</span><span class="sxs-lookup"><span data-stu-id="18875-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="18875-114">演算子は、変数やプロパティにし、その操作の浮動小数点の結果を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="18875-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="18875-115">このステートメントは、代入、`Double`を変数または左側のプロパティの値。</span><span class="sxs-lookup"><span data-stu-id="18875-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="18875-116">場合`Option Strict`は`On`、`variableorproperty`する必要があります、`Double`です。</span><span class="sxs-lookup"><span data-stu-id="18875-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="18875-117">場合`Option Strict`は`Off`、Visual Basic の暗黙的な変換を実行およびを結果として得られる値を割り当てます`variableorproperty`、実行時に可能性のあるエラーとします。</span><span class="sxs-lookup"><span data-stu-id="18875-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="18875-118">詳細については、次を参照してください。[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="18875-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="18875-119">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="18875-119">Overloading</span></span>  
 <span data-ttu-id="18875-120">[/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="18875-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="18875-121">オーバー ロード、`/`演算子の動作に影響、`/=`演算子。</span><span class="sxs-lookup"><span data-stu-id="18875-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="18875-122">コードで使用する場合`/=`クラスまたはオーバー ロードする構造体で`/`、再定義された動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="18875-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="18875-123">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="18875-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18875-124">例</span><span class="sxs-lookup"><span data-stu-id="18875-124">Example</span></span>  
 <span data-ttu-id="18875-125">次の例では、`/=`演算子を 1 つに分割`Integer`変数の 2 番目と割り当て、最初の変数への商。</span><span class="sxs-lookup"><span data-stu-id="18875-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="18875-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="18875-126">See Also</span></span>  
 [<span data-ttu-id="18875-127">/演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18875-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [<span data-ttu-id="18875-128">\\= 演算子</span><span class="sxs-lookup"><span data-stu-id="18875-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="18875-129">代入演算子</span><span class="sxs-lookup"><span data-stu-id="18875-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="18875-130">算術演算子</span><span class="sxs-lookup"><span data-stu-id="18875-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="18875-131">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="18875-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="18875-132">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="18875-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="18875-133">ステートメント</span><span class="sxs-lookup"><span data-stu-id="18875-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
