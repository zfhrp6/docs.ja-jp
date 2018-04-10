---
title: '&amp;= 演算子 (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 929a9e8c3384451679fc52ad478eb03219d67192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="466e0-102">&amp;= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="466e0-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="466e0-103">連結、`String`式を`String`変数またはプロパティと、結果を変数またはプロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="466e0-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="466e0-104">構文</span><span class="sxs-lookup"><span data-stu-id="466e0-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="466e0-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="466e0-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="466e0-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="466e0-106">Required.</span></span> <span data-ttu-id="466e0-107">どの`String`変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="466e0-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="466e0-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="466e0-108">Required.</span></span> <span data-ttu-id="466e0-109">任意のブール型 (`String`) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="466e0-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="466e0-110">コメント</span><span class="sxs-lookup"><span data-stu-id="466e0-110">Remarks</span></span>  
 <span data-ttu-id="466e0-111">左側にある要素、`&=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="466e0-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="466e0-112">変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="466e0-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="466e0-113">`&=`演算子は、連結、 `String` 、右辺の式、`String`変数またはプロパティの左側にし、変数またはプロパティの左側に結果を代入します。</span><span class="sxs-lookup"><span data-stu-id="466e0-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="466e0-114">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="466e0-114">Overloading</span></span>  
 <span data-ttu-id="466e0-115">[& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)できます*オーバー ロードされた*、いるクラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合は。</span><span class="sxs-lookup"><span data-stu-id="466e0-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="466e0-116">オーバー ロード、`&`演算子の動作に影響、`&=`演算子。</span><span class="sxs-lookup"><span data-stu-id="466e0-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="466e0-117">コードで使用する場合`&=`クラスまたはオーバー ロードする構造体で`&`、再定義された動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="466e0-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="466e0-118">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="466e0-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="466e0-119">例</span><span class="sxs-lookup"><span data-stu-id="466e0-119">Example</span></span>  
 <span data-ttu-id="466e0-120">次の例で、`&=`を 2 つ連結演算子`String`変数と、その結果、最初の変数を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="466e0-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="466e0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="466e0-121">See Also</span></span>  
 [<span data-ttu-id="466e0-122">& 演算子</span><span class="sxs-lookup"><span data-stu-id="466e0-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [<span data-ttu-id="466e0-123">+= 演算子</span><span class="sxs-lookup"><span data-stu-id="466e0-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [<span data-ttu-id="466e0-124">代入演算子</span><span class="sxs-lookup"><span data-stu-id="466e0-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="466e0-125">連結演算子</span><span class="sxs-lookup"><span data-stu-id="466e0-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="466e0-126">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="466e0-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="466e0-127">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="466e0-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="466e0-128">ステートメント</span><span class="sxs-lookup"><span data-stu-id="466e0-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
