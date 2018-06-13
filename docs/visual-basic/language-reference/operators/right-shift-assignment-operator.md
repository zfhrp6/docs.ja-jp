---
title: '&gt;&gt;= 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: d0c0ea819741f80e30e55a960b1187699898a3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604108"
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="1f2c7-102">&gt;&gt;= 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f2c7-102">&gt;&gt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="1f2c7-103">変数またはプロパティの値に対して算術右シフトを実行し、結果を変数またはプロパティに代入します。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f2c7-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f2c7-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="1f2c7-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="1f2c7-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="1f2c7-106">必須。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-106">Required.</span></span> <span data-ttu-id="1f2c7-107">整数型の変数またはプロパティ (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="1f2c7-108">必須。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-108">Required.</span></span> <span data-ttu-id="1f2c7-109">拡大変換をデータ型の数値式`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f2c7-110">コメント</span><span class="sxs-lookup"><span data-stu-id="1f2c7-110">Remarks</span></span>  
 <span data-ttu-id="1f2c7-111">左側にある要素、`>>=`演算子は、単純なスカラー変数、プロパティ、または配列の要素を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="1f2c7-112">変数またはプロパティにできません。 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="1f2c7-113">`>>=`演算子は最初、変数またはプロパティの値に算術右シフトを実行します。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="1f2c7-114">演算子は、変数またはプロパティにし、その操作の結果を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="1f2c7-115">算術シフトは循環、つまり、もう一方の端に結果の 1 つの端シフトは行われません。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="1f2c7-116">算術右シフトの右端のビット位置を超えてシフトは破棄され、最上位ビットは左側にある空いたビット位置に反映されます。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="1f2c7-117">つまり、`variableorproperty`負の値を持つ、空いた位置は 1 つに設定します。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="1f2c7-118">場合`variableorproperty`が正の値か、空いた位置を 0 に設定されて、データ型が符号なしの型の場合は、します。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1f2c7-119">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="1f2c7-119">Overloading</span></span>  
 <span data-ttu-id="1f2c7-120">[>> 演算子](../../../visual-basic/language-reference/operators/right-shift-operator.md)できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1f2c7-121">オーバー ロード、`>>`演算子の動作に影響、`>>=`演算子。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="1f2c7-122">コードで使用する場合`>>=`クラスまたはオーバー ロードする構造体で`>>`、再定義された動作を確認してください。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1f2c7-123">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f2c7-124">例</span><span class="sxs-lookup"><span data-stu-id="1f2c7-124">Example</span></span>  
 <span data-ttu-id="1f2c7-125">次の例では、`>>=`のビット パターンをシフトする演算子、`Integer`変数指定の量と割り当てを変数に結果を右。</span><span class="sxs-lookup"><span data-stu-id="1f2c7-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1f2c7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f2c7-126">See Also</span></span>  
 [<span data-ttu-id="1f2c7-127">>> 演算子</span><span class="sxs-lookup"><span data-stu-id="1f2c7-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [<span data-ttu-id="1f2c7-128">代入演算子</span><span class="sxs-lookup"><span data-stu-id="1f2c7-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="1f2c7-129">ビット シフト演算子</span><span class="sxs-lookup"><span data-stu-id="1f2c7-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="1f2c7-130">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="1f2c7-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="1f2c7-131">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="1f2c7-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="1f2c7-132">ステートメント</span><span class="sxs-lookup"><span data-stu-id="1f2c7-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
