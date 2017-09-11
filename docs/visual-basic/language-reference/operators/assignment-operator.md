---
title: "= 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
dev_langs:
- VB
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 46dc9e6018cf2ae71f1fc6dc2b8f19c2f0aadb62
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="00e8b-102">= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00e8b-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="00e8b-103">変数やプロパティに値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="00e8b-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e8b-104">構文</span><span class="sxs-lookup"><span data-stu-id="00e8b-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="00e8b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="00e8b-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="00e8b-106">書き込み可能な任意の変数または任意のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="00e8b-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="00e8b-107">任意のリテラル、定数、または式。</span><span class="sxs-lookup"><span data-stu-id="00e8b-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00e8b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="00e8b-108">Remarks</span></span>  
 <span data-ttu-id="00e8b-109">等号 (=) の左側にある要素 (`=`) 単純なスカラー変数、プロパティ、または配列の要素にすることができます。</span><span class="sxs-lookup"><span data-stu-id="00e8b-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="00e8b-110">変数やプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。</span><span class="sxs-lookup"><span data-stu-id="00e8b-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="00e8b-111">`=`演算子は、変数に、右側の値またはプロパティの左側に代入します。</span><span class="sxs-lookup"><span data-stu-id="00e8b-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="00e8b-112">`=`演算子、比較演算子としても使用します。</span><span class="sxs-lookup"><span data-stu-id="00e8b-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="00e8b-113">詳細については、「[比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)します。</span><span class="sxs-lookup"><span data-stu-id="00e8b-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="00e8b-114">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="00e8b-114">Overloading</span></span>  
 <span data-ttu-id="00e8b-115">`=`比較演算子としてのみ、代入演算子としてではなく、演算子がオーバー ロードできます。</span><span class="sxs-lookup"><span data-stu-id="00e8b-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="00e8b-116">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="00e8b-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="00e8b-117">例</span><span class="sxs-lookup"><span data-stu-id="00e8b-117">Example</span></span>  
 <span data-ttu-id="00e8b-118">次の例では、代入演算子を示します。</span><span class="sxs-lookup"><span data-stu-id="00e8b-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="00e8b-119">右側の値が左側の変数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="00e8b-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 <span data-ttu-id="00e8b-120">[!code-vb[VbVbalrOperators&#9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="00e8b-120">[!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e8b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="00e8b-121">See Also</span></span>  
 <span data-ttu-id="00e8b-122">[< = 演算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-122">[&= Operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md) </span></span>  
<span data-ttu-id="00e8b-123"> [* = 演算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-123"> [*= Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md) </span></span>  
<span data-ttu-id="00e8b-124"> [+ = 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-124"> [+= Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md) </span></span>  
<span data-ttu-id="00e8b-125"> [-= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-125"> [-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) </span></span>  
<span data-ttu-id="00e8b-126"> [/= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-126"> [/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md) </span></span>  
<span data-ttu-id="00e8b-127"> [\\= 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-127"> [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span></span>  
<span data-ttu-id="00e8b-128"> [^ = 演算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-128"> [^= Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md) </span></span>  
<span data-ttu-id="00e8b-129"> [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-129"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="00e8b-130"> [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-130"> [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="00e8b-131"> [読み取り専用](../../../visual-basic/language-reference/modifiers/readonly.md) </span><span class="sxs-lookup"><span data-stu-id="00e8b-131"> [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) </span></span>  
<span data-ttu-id="00e8b-132"> [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="00e8b-132"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>

