---
title: '- 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 4df8eb3844ed20fd24ca375f77cea46b9c6cee37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604316"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="9f20d-102">- 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f20d-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="9f20d-103">2 つの数値式または数値式の負の値の差を返します。</span><span class="sxs-lookup"><span data-stu-id="9f20d-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f20d-104">構文</span><span class="sxs-lookup"><span data-stu-id="9f20d-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="9f20d-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9f20d-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="9f20d-106">必須。</span><span class="sxs-lookup"><span data-stu-id="9f20d-106">Required.</span></span> <span data-ttu-id="9f20d-107">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="9f20d-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="9f20d-108">いない限り、必須、`–`演算子が負の値を計算します。</span><span class="sxs-lookup"><span data-stu-id="9f20d-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="9f20d-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="9f20d-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="9f20d-110">結果</span><span class="sxs-lookup"><span data-stu-id="9f20d-110">Result</span></span>  
 <span data-ttu-id="9f20d-111">結果の違いは、`expression1`と`expression2`、またはの負数化された値`expression1`です。</span><span class="sxs-lookup"><span data-stu-id="9f20d-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="9f20d-112">結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。</span><span class="sxs-lookup"><span data-stu-id="9f20d-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="9f20d-113">「整数算術演算による」テーブルを参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f20d-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="9f20d-114">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="9f20d-114">Supported Types</span></span>  
 <span data-ttu-id="9f20d-115">すべての数値型。</span><span class="sxs-lookup"><span data-stu-id="9f20d-115">All numeric types.</span></span> <span data-ttu-id="9f20d-116">これには、符号なし型と浮動小数点型が含まれますと`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="9f20d-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f20d-117">コメント</span><span class="sxs-lookup"><span data-stu-id="9f20d-117">Remarks</span></span>  
 <span data-ttu-id="9f20d-118">最初の使用率が、前に示した構文に示すように、`–`演算子は、*バイナリ*2 つの数値式の違いを減算演算子。</span><span class="sxs-lookup"><span data-stu-id="9f20d-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="9f20d-119">2 番目の使用率が、前に示した構文に示すように、`–`演算子は、*単項*式の負の値の否定演算子。</span><span class="sxs-lookup"><span data-stu-id="9f20d-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="9f20d-120">符号を反転することの否定は、この意味で`expression1`結果が正の値になるよう場合`expression1`が負の値。</span><span class="sxs-lookup"><span data-stu-id="9f20d-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="9f20d-121">いずれかの式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)、`–`演算子は 0 として処理します。</span><span class="sxs-lookup"><span data-stu-id="9f20d-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f20d-122">`–`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="9f20d-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9f20d-123">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、その再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="9f20d-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="9f20d-124">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="9f20d-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f20d-125">例</span><span class="sxs-lookup"><span data-stu-id="9f20d-125">Example</span></span>  
 <span data-ttu-id="9f20d-126">次の例では、`–`演算子を計算し、2 つの数値の差を返すし、数値を否定します。</span><span class="sxs-lookup"><span data-stu-id="9f20d-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 <span data-ttu-id="9f20d-127">次のこれらのステートメントの実行`binaryResult`124.45 が含まれていますと`unaryResult`–334.90 が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9f20d-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f20d-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f20d-128">See Also</span></span>  
 <span data-ttu-id="9f20d-129">[-= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="9f20d-129">[-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span></span>  
 [<span data-ttu-id="9f20d-130">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="9f20d-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="9f20d-131">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="9f20d-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="9f20d-132">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="9f20d-132">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
