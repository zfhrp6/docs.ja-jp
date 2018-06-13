---
title: = 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 55b3a8201940a6fec351327aaa88e4ac1ee9246a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603601"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="4e35f-102">= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e35f-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="4e35f-103">変数またはプロパティに値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4e35f-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e35f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4e35f-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="4e35f-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="4e35f-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="4e35f-106">任意の書き込み可能な変数または任意のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="4e35f-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="4e35f-107">任意のリテラル、定数、または式。</span><span class="sxs-lookup"><span data-stu-id="4e35f-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e35f-108">コメント</span><span class="sxs-lookup"><span data-stu-id="4e35f-108">Remarks</span></span>  
 <span data-ttu-id="4e35f-109">等号の左側にある要素 (`=`) は、単純なスカラー変数、プロパティ、または配列の要素。</span><span class="sxs-lookup"><span data-stu-id="4e35f-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="4e35f-110">変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="4e35f-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="4e35f-111">`=`演算子は、変数にその右側にある値またはプロパティの左側に代入します。</span><span class="sxs-lookup"><span data-stu-id="4e35f-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e35f-112">`=`演算子、比較演算子としても使用します。</span><span class="sxs-lookup"><span data-stu-id="4e35f-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="4e35f-113">詳細については、「[比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)です。</span><span class="sxs-lookup"><span data-stu-id="4e35f-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4e35f-114">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="4e35f-114">Overloading</span></span>  
 <span data-ttu-id="4e35f-115">`=`比較演算子としてのみ、代入演算子としてではなく、演算子がオーバー ロードできます。</span><span class="sxs-lookup"><span data-stu-id="4e35f-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="4e35f-116">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="4e35f-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e35f-117">例</span><span class="sxs-lookup"><span data-stu-id="4e35f-117">Example</span></span>  
 <span data-ttu-id="4e35f-118">次の例では、代入演算子を示します。</span><span class="sxs-lookup"><span data-stu-id="4e35f-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="4e35f-119">右側の値が左側の変数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="4e35f-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4e35f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e35f-120">See Also</span></span>  
 [<span data-ttu-id="4e35f-121">& = 演算子</span><span class="sxs-lookup"><span data-stu-id="4e35f-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="4e35f-122">\*= 演算子</span><span class="sxs-lookup"><span data-stu-id="4e35f-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [<span data-ttu-id="4e35f-123">+= 演算子</span><span class="sxs-lookup"><span data-stu-id="4e35f-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [<span data-ttu-id="4e35f-124">-= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e35f-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [<span data-ttu-id="4e35f-125">/= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e35f-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="4e35f-126">\\= 演算子</span><span class="sxs-lookup"><span data-stu-id="4e35f-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="4e35f-127">^= 演算子</span><span class="sxs-lookup"><span data-stu-id="4e35f-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [<span data-ttu-id="4e35f-128">ステートメント</span><span class="sxs-lookup"><span data-stu-id="4e35f-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="4e35f-129">比較演算子</span><span class="sxs-lookup"><span data-stu-id="4e35f-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="4e35f-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="4e35f-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="4e35f-131">ローカル型の推論</span><span class="sxs-lookup"><span data-stu-id="4e35f-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
