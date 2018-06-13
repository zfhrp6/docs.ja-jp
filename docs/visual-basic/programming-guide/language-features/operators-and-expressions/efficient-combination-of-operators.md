---
title: 演算子の効率のよい組み合わせ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8ced464cb0cc8e1bec3c3449dccb827575599905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648919"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="0295a-102">演算子の効率のよい組み合わせ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0295a-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="0295a-103">複雑な式には、さまざまな演算子を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0295a-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="0295a-104">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="0295a-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="0295a-105">前の例の 1 などの複雑な式を作成するには、演算子の優先順位の規則の確実な理解が必要です。</span><span class="sxs-lookup"><span data-stu-id="0295a-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="0295a-106">詳細については、次を参照してください。 [Visual Basic の演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)です。</span><span class="sxs-lookup"><span data-stu-id="0295a-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="0295a-107">かっこで囲んだ式</span><span class="sxs-lookup"><span data-stu-id="0295a-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="0295a-108">多くの場合、演算子の優先順位によって決定されるとは異なる順序で演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="0295a-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="0295a-109">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0295a-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="0295a-110">前の例の乗算`z`によって`y`、結果を追加`4`です。</span><span class="sxs-lookup"><span data-stu-id="0295a-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="0295a-111">追加する場合は`y`と`4`には、結果を乗算する前に`z`かっこを使用して通常の演算子の優先順位をオーバーライドすることができます。</span><span class="sxs-lookup"><span data-stu-id="0295a-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="0295a-112">式をかっこで囲んで、その評価される式を最初に、演算子の優先順位に関係なくを強制します。</span><span class="sxs-lookup"><span data-stu-id="0295a-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="0295a-113">最初に実行する追加の前の例を次の例のように書き直すことができます。</span><span class="sxs-lookup"><span data-stu-id="0295a-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="0295a-114">上記の例では追加`y`と`4`、によってその合計を乗算`z`です。</span><span class="sxs-lookup"><span data-stu-id="0295a-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="0295a-115">入れ子になったかっこで囲んだ式</span><span class="sxs-lookup"><span data-stu-id="0295a-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="0295a-116">さらに優先順位をオーバーライドするかっこの複数のレベルでの式を入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="0295a-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="0295a-117">かっこ内に最も深く入れ子になった式は、最も深く入れ子になったに最も深く入れ子にされた、および最後に式を次に最初に評価されます。</span><span class="sxs-lookup"><span data-stu-id="0295a-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="0295a-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="0295a-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="0295a-119">前の例で`z + 2`が評価された最初に、次に、その他のかっこで囲んだ式。</span><span class="sxs-lookup"><span data-stu-id="0295a-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="0295a-120">指数演算は、通常は、加算や乗算より高い優先順位をは他の式がかっこで囲まれているために、この例では最終評価されます。</span><span class="sxs-lookup"><span data-stu-id="0295a-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0295a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="0295a-121">See Also</span></span>  
 [<span data-ttu-id="0295a-122">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="0295a-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="0295a-123">Visual Basic における比較演算子</span><span class="sxs-lookup"><span data-stu-id="0295a-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="0295a-124">Visual Basic における論理/ビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="0295a-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="0295a-125">論理/ビット演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0295a-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="0295a-126">ブール式</span><span class="sxs-lookup"><span data-stu-id="0295a-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="0295a-127">値の比較</span><span class="sxs-lookup"><span data-stu-id="0295a-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="0295a-128">方法 : 数値を計算する</span><span class="sxs-lookup"><span data-stu-id="0295a-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="0295a-129">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="0295a-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
