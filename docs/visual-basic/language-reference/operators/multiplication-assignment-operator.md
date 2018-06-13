---
title: '*= 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 3863e6c7416057507e8ae569804ed4a1be6a5b50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604160"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="eb1d3-102">\*= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb1d3-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="eb1d3-103">式の値で変数またはプロパティの値を乗算し、結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb1d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="eb1d3-104">Syntax</span></span>  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="eb1d3-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="eb1d3-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="eb1d3-106">必須。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-106">Required.</span></span> <span data-ttu-id="eb1d3-107">任意の数値型の変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="eb1d3-108">必須。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-108">Required.</span></span> <span data-ttu-id="eb1d3-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb1d3-110">コメント</span><span class="sxs-lookup"><span data-stu-id="eb1d3-110">Remarks</span></span>  
 <span data-ttu-id="eb1d3-111">左側にある要素、`*=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="eb1d3-112">変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="eb1d3-113">`*=`演算子が変数または (演算子の左側にある) のプロパティの値によって最初 (演算子の右側にある) の式の値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="eb1d3-114">演算子は、変数やプロパティにし、その操作の結果を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="eb1d3-115">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="eb1d3-115">Overloading</span></span>  
 <span data-ttu-id="eb1d3-116">[\* 演算子](../../../visual-basic/language-reference/operators/multiplication-operator.md)できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="eb1d3-117">オーバー ロード、`*`演算子の動作に影響、`*=`演算子。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="eb1d3-118">コードで使用する場合`*=`クラスまたはオーバー ロードする構造体で`*`、再定義された動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="eb1d3-119">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb1d3-120">例</span><span class="sxs-lookup"><span data-stu-id="eb1d3-120">Example</span></span>  
 <span data-ttu-id="eb1d3-121">次の例で、`*=`を 1 つを乗算する演算子`Integer`変数の 2 番目と、その結果、最初の変数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="eb1d3-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="eb1d3-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="eb1d3-122">See Also</span></span>  
 [<span data-ttu-id="eb1d3-123">\* 演算子</span><span class="sxs-lookup"><span data-stu-id="eb1d3-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)  
 [<span data-ttu-id="eb1d3-124">代入演算子</span><span class="sxs-lookup"><span data-stu-id="eb1d3-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="eb1d3-125">算術演算子</span><span class="sxs-lookup"><span data-stu-id="eb1d3-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="eb1d3-126">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="eb1d3-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="eb1d3-127">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="eb1d3-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="eb1d3-128">ステートメント</span><span class="sxs-lookup"><span data-stu-id="eb1d3-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
