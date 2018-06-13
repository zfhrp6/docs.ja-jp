---
title: ^= 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 571ef26eb188d9044ec8f6c8e6e4b490780f17a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603497"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="232d5-102">^= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="232d5-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="232d5-103">変数または式のプロパティの値を生成し、結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="232d5-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="232d5-104">構文</span><span class="sxs-lookup"><span data-stu-id="232d5-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="232d5-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="232d5-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="232d5-106">必須。</span><span class="sxs-lookup"><span data-stu-id="232d5-106">Required.</span></span> <span data-ttu-id="232d5-107">任意の数値型の変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="232d5-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="232d5-108">必須。</span><span class="sxs-lookup"><span data-stu-id="232d5-108">Required.</span></span> <span data-ttu-id="232d5-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="232d5-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="232d5-110">コメント</span><span class="sxs-lookup"><span data-stu-id="232d5-110">Remarks</span></span>  
 <span data-ttu-id="232d5-111">左側にある要素、`^=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="232d5-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="232d5-112">変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="232d5-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="232d5-113">`^=` (演算子の右側にある) の式の値の累乗演算子が変数または (演算子の左側にある) のプロパティの値にまずを発生させます。</span><span class="sxs-lookup"><span data-stu-id="232d5-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="232d5-114">演算子は、変数またはプロパティにし、その操作の結果を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="232d5-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="232d5-115">Visual Basic での累乗を常に実行する、 [Double データ型](../../../visual-basic/language-reference/data-types/double-data-type.md)です。</span><span class="sxs-lookup"><span data-stu-id="232d5-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="232d5-116">任意の異なる型のオペランドに変換`Double`、され、結果は常に`Double`です。</span><span class="sxs-lookup"><span data-stu-id="232d5-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="232d5-117">値`expression`、小数部は、負の値、またはその両方です。</span><span class="sxs-lookup"><span data-stu-id="232d5-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="232d5-118">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="232d5-118">Overloading</span></span>  
 <span data-ttu-id="232d5-119">[^ 演算子](../../../visual-basic/language-reference/operators/exponentiation-operator.md)できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="232d5-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="232d5-120">オーバー ロード、`^`演算子の動作に影響、`^=`演算子。</span><span class="sxs-lookup"><span data-stu-id="232d5-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="232d5-121">コードで使用する場合`^=`クラスまたはオーバー ロードする構造体で`^`、再定義された動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="232d5-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="232d5-122">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="232d5-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="232d5-123">例</span><span class="sxs-lookup"><span data-stu-id="232d5-123">Example</span></span>  
 <span data-ttu-id="232d5-124">次の例では、`^=`いずれかの値を上げる演算子`Integer`変数の 2 つ目の変数と割り当て、その結果、最初の変数を電源にします。</span><span class="sxs-lookup"><span data-stu-id="232d5-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="232d5-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="232d5-125">See Also</span></span>  
 [<span data-ttu-id="232d5-126">^ 演算子</span><span class="sxs-lookup"><span data-stu-id="232d5-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [<span data-ttu-id="232d5-127">代入演算子</span><span class="sxs-lookup"><span data-stu-id="232d5-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="232d5-128">算術演算子</span><span class="sxs-lookup"><span data-stu-id="232d5-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="232d5-129">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="232d5-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="232d5-130">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="232d5-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="232d5-131">ステートメント</span><span class="sxs-lookup"><span data-stu-id="232d5-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
