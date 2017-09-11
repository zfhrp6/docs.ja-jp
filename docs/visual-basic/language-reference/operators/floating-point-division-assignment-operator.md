---
title: "/= 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./=
dev_langs:
- VB
helpviewer_keywords:
- assignment statements, compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
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
ms.openlocfilehash: e877e98104b5c9fd679485b50a88943fac80a696
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b429b-102">/= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b429b-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="b429b-103">変数またはプロパティの値を式の値で除算し、浮動小数点の結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="b429b-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b429b-104">構文</span><span class="sxs-lookup"><span data-stu-id="b429b-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b429b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="b429b-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="b429b-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="b429b-106">Required.</span></span> <span data-ttu-id="b429b-107">任意の数値変数またはプロパティを使用しています。</span><span class="sxs-lookup"><span data-stu-id="b429b-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="b429b-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="b429b-108">Required.</span></span> <span data-ttu-id="b429b-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="b429b-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b429b-110">コメント</span><span class="sxs-lookup"><span data-stu-id="b429b-110">Remarks</span></span>  
 <span data-ttu-id="b429b-111">左側にある要素、`/=`演算子は単純なスカラー変数、プロパティ、または配列の要素があります。</span><span class="sxs-lookup"><span data-stu-id="b429b-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="b429b-112">変数やプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。</span><span class="sxs-lookup"><span data-stu-id="b429b-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="b429b-113">`/=`演算子は最初、(演算子の右側にある) の式の値で変数または (演算子の左側にある) のプロパティの値を除算します。</span><span class="sxs-lookup"><span data-stu-id="b429b-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="b429b-114">演算子は、その操作の浮動小数点の結果を変数やプロパティを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b429b-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="b429b-115">このステートメントは、代入、`Double`変数または左のプロパティの値。</span><span class="sxs-lookup"><span data-stu-id="b429b-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="b429b-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span><span class="sxs-lookup"><span data-stu-id="b429b-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="b429b-117">場合`Option Strict`は`Off`、Visual Basic の暗黙的な変換を実行およびに結果として得られる値を代入`variableorproperty`、実行時に潜在的なエラーとします。</span><span class="sxs-lookup"><span data-stu-id="b429b-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="b429b-118">詳細については、次を参照してください。[拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。</span><span class="sxs-lookup"><span data-stu-id="b429b-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b429b-119">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="b429b-119">Overloading</span></span>  
 <span data-ttu-id="b429b-120">[/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)を指定できます*オーバー ロードされた*、つまり、クラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合です。</span><span class="sxs-lookup"><span data-stu-id="b429b-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b429b-121">オーバー ロード、`/`演算子の動作に影響、`/=`演算子。</span><span class="sxs-lookup"><span data-stu-id="b429b-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="b429b-122">コードで使用する場合`/=`クラスまたは構造体をオーバー ロードで`/`、その再定義された動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="b429b-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b429b-123">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="b429b-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b429b-124">例</span><span class="sxs-lookup"><span data-stu-id="b429b-124">Example</span></span>  
 <span data-ttu-id="b429b-125">次の例では、`/=`演算子を&1; つに分割`Integer`秒を割り当て、最初の変数に、商により変数です。</span><span class="sxs-lookup"><span data-stu-id="b429b-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 <span data-ttu-id="b429b-126">[!code-vb[VbVbalrOperators&17;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b429b-126">[!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b429b-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="b429b-127">See Also</span></span>  
 <span data-ttu-id="b429b-128">[/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) </span><span class="sxs-lookup"><span data-stu-id="b429b-128">[/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) </span></span>  
<span data-ttu-id="b429b-129"> [\\= 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span><span class="sxs-lookup"><span data-stu-id="b429b-129"> [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md) </span></span>  
<span data-ttu-id="b429b-130"> [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md) </span><span class="sxs-lookup"><span data-stu-id="b429b-130"> [Assignment Operators](../../../visual-basic/language-reference/operators/assignment-operators.md) </span></span>  
<span data-ttu-id="b429b-131"> [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="b429b-131"> [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="b429b-132"> [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="b429b-132"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="b429b-133"> [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="b429b-133"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="b429b-134"> [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)</span><span class="sxs-lookup"><span data-stu-id="b429b-134"> [Statements](../../../visual-basic/programming-guide/language-features/statements.md)</span></span>

