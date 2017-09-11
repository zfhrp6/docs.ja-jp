---
title: "-= 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
dev_langs:
- VB
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements, compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
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
ms.openlocfilehash: 694033ec89e32b5fdba4092bd60292af536f58dd
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="--operator-visual-basic"></a><span data-ttu-id="e3553-102">-= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3553-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="e3553-103">変数またはプロパティの値から式の値を減算し、その結果を変数やプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="e3553-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3553-104">構文</span><span class="sxs-lookup"><span data-stu-id="e3553-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="e3553-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="e3553-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="e3553-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="e3553-106">Required.</span></span> <span data-ttu-id="e3553-107">任意の数値変数またはプロパティを使用しています。</span><span class="sxs-lookup"><span data-stu-id="e3553-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="e3553-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="e3553-108">Required.</span></span> <span data-ttu-id="e3553-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="e3553-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3553-110">コメント</span><span class="sxs-lookup"><span data-stu-id="e3553-110">Remarks</span></span>  
 <span data-ttu-id="e3553-111">左側にある要素、`-=`演算子は単純なスカラー変数、プロパティ、または配列の要素があります。</span><span class="sxs-lookup"><span data-stu-id="e3553-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="e3553-112">変数やプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。</span><span class="sxs-lookup"><span data-stu-id="e3553-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="e3553-113">`-=`演算子は最初に、変数または (演算子の左側にある) のプロパティの値から (演算子の右側にある) の式の値を減算します。</span><span class="sxs-lookup"><span data-stu-id="e3553-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="e3553-114">演算子は、その操作の結果を変数やプロパティを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e3553-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e3553-115">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="e3553-115">Overloading</span></span>  
 <span data-ttu-id="e3553-116">[-演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)を指定できます*過負荷になって*、つまり、クラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合です。</span><span class="sxs-lookup"><span data-stu-id="e3553-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e3553-117">オーバー ロード、`-`演算子の動作に影響、`-=`演算子。</span><span class="sxs-lookup"><span data-stu-id="e3553-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="e3553-118">コードで使用する場合`-=`クラスまたは構造体をオーバー ロードで`-`、その再定義された動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="e3553-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e3553-119">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="e3553-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3553-120">例</span><span class="sxs-lookup"><span data-stu-id="e3553-120">Example</span></span>  
 <span data-ttu-id="e3553-121">次の例では、 `-=`&1; を減算する演算子を`Integer`から別の変数と割り当て、その結果、後者の変数をします。</span><span class="sxs-lookup"><span data-stu-id="e3553-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 <span data-ttu-id="e3553-122">[!code-vb[VbVbalrOperators&#11;](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e3553-122">[!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3553-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3553-123">See Also</span></span>  
 <span data-ttu-id="e3553-124">[-演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) </span><span class="sxs-lookup"><span data-stu-id="e3553-124">[- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) </span></span>  
<span data-ttu-id="e3553-125"> [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="e3553-125"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="e3553-126"> [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="e3553-126"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="e3553-127"> [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="e3553-127"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="e3553-128"> [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="e3553-128"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="e3553-129"> [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="e3553-129"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

