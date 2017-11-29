---
title: "+= 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ac8f5679aa90c50c15c33a957cfc75d9ccecde6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="d58c3-102">+= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d58c3-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="d58c3-103">数値型の変数またはプロパティの値に数値式の値を追加し、結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="d58c3-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="d58c3-104">連結するためにも使用する、`String`式、`String`変数やプロパティと、割り当て、その結果を変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="d58c3-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d58c3-105">構文</span><span class="sxs-lookup"><span data-stu-id="d58c3-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d58c3-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="d58c3-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d58c3-107">必須です。</span><span class="sxs-lookup"><span data-stu-id="d58c3-107">Required.</span></span> <span data-ttu-id="d58c3-108">任意の数値または`String`変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="d58c3-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="d58c3-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="d58c3-109">Required.</span></span> <span data-ttu-id="d58c3-110">任意の数値または`String`式。</span><span class="sxs-lookup"><span data-stu-id="d58c3-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d58c3-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d58c3-111">Remarks</span></span>  
 <span data-ttu-id="d58c3-112">左側にある要素、`+=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d58c3-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d58c3-113">変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="d58c3-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="d58c3-114">`+=`演算子が変数またはプロパティの左側にするには、その右側の値を追加し、結果を変数またはプロパティの左側に代入します。</span><span class="sxs-lookup"><span data-stu-id="d58c3-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="d58c3-115">`+=`連結する演算子を使用することも、 `String` 、右辺の式、`String`変数またはプロパティに割り当て、その結果、変数を左、またはプロパティの左側にします。</span><span class="sxs-lookup"><span data-stu-id="d58c3-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d58c3-116">使用すると、`+=`演算子ができないことがありますを追加または文字列の連結が発生するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d58c3-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="d58c3-117">使用して、`&=`演算子の連結のあいまいさを排除し、自己文書化コードを提供します。</span><span class="sxs-lookup"><span data-stu-id="d58c3-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="d58c3-118">この代入演算子は、拡大縮小ではなく変換のコンパイル環境で厳密なセマンティクスを適用する場合、暗黙的に実行します。</span><span class="sxs-lookup"><span data-stu-id="d58c3-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="d58c3-119">これらの変換の詳細については、次を参照してください。[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)です。</span><span class="sxs-lookup"><span data-stu-id="d58c3-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="d58c3-120">厳密なと制限の緩やかなセマンティクスの詳細については、次を参照してください。 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)です。</span><span class="sxs-lookup"><span data-stu-id="d58c3-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="d58c3-121">寛容が許可されている場合、`+=`演算子によって実行されるものと同じ文字列と数値の変換のさまざまなを暗黙的に実行する、`+`演算子。</span><span class="sxs-lookup"><span data-stu-id="d58c3-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="d58c3-122">これらの変換の詳細については、「 [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)です。</span><span class="sxs-lookup"><span data-stu-id="d58c3-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d58c3-123">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="d58c3-123">Overloading</span></span>  
 <span data-ttu-id="d58c3-124">`+`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="d58c3-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="d58c3-125">オーバー ロード、`+`演算子の動作に影響、`+=`演算子。</span><span class="sxs-lookup"><span data-stu-id="d58c3-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="d58c3-126">コードで使用する場合`+=`クラスまたはオーバー ロードする構造体で`+`、再定義された動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="d58c3-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="d58c3-127">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="d58c3-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d58c3-128">例</span><span class="sxs-lookup"><span data-stu-id="d58c3-128">Example</span></span>  
 <span data-ttu-id="d58c3-129">次の例では、`+=`と他の 1 つの変数の値を結合する演算子です。</span><span class="sxs-lookup"><span data-stu-id="d58c3-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="d58c3-130">最初の部分を使用して`+=`に 1 つの値を加算する数値変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="d58c3-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="d58c3-131">2 番目の部分を使用して`+=`で`String`変数を別の 1 つの値を連結します。</span><span class="sxs-lookup"><span data-stu-id="d58c3-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="d58c3-132">どちらの場合は、結果は、最初の変数に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="d58c3-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 <span data-ttu-id="d58c3-133">値`num1`13、およびの値が、 `str1` 「103」になります。</span><span class="sxs-lookup"><span data-stu-id="d58c3-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d58c3-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="d58c3-134">See Also</span></span>  
 [<span data-ttu-id="d58c3-135">+ 演算子</span><span class="sxs-lookup"><span data-stu-id="d58c3-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [<span data-ttu-id="d58c3-136">代入演算子</span><span class="sxs-lookup"><span data-stu-id="d58c3-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="d58c3-137">算術演算子</span><span class="sxs-lookup"><span data-stu-id="d58c3-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="d58c3-138">連結演算子</span><span class="sxs-lookup"><span data-stu-id="d58c3-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="d58c3-139">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="d58c3-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d58c3-140">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="d58c3-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d58c3-141">ステートメント</span><span class="sxs-lookup"><span data-stu-id="d58c3-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
