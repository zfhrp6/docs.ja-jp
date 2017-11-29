---
title: "- 演算子 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ffb7c96fe95e73dc857a15608df94ed8468f9df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="035fe-102">- 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="035fe-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="035fe-103">2 つの数値式または数値式の負の値の差を返します。</span><span class="sxs-lookup"><span data-stu-id="035fe-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="035fe-104">構文</span><span class="sxs-lookup"><span data-stu-id="035fe-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="035fe-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="035fe-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="035fe-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="035fe-106">Required.</span></span> <span data-ttu-id="035fe-107">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="035fe-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="035fe-108">いない限り、必須、`–`演算子が負の値を計算します。</span><span class="sxs-lookup"><span data-stu-id="035fe-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="035fe-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="035fe-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="035fe-110">結果</span><span class="sxs-lookup"><span data-stu-id="035fe-110">Result</span></span>  
 <span data-ttu-id="035fe-111">結果の違いは、`expression1`と`expression2`、またはの負数化された値`expression1`です。</span><span class="sxs-lookup"><span data-stu-id="035fe-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="035fe-112">結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`です。</span><span class="sxs-lookup"><span data-stu-id="035fe-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="035fe-113">「整数算術演算による」テーブルを参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="035fe-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="035fe-114">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="035fe-114">Supported Types</span></span>  
 <span data-ttu-id="035fe-115">すべての数値型。</span><span class="sxs-lookup"><span data-stu-id="035fe-115">All numeric types.</span></span> <span data-ttu-id="035fe-116">これには、符号なし型と浮動小数点型が含まれますと`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="035fe-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="035fe-117">コメント</span><span class="sxs-lookup"><span data-stu-id="035fe-117">Remarks</span></span>  
 <span data-ttu-id="035fe-118">最初の使用率が、前に示した構文に示すように、`–`演算子は、*バイナリ*2 つの数値式の違いを減算演算子。</span><span class="sxs-lookup"><span data-stu-id="035fe-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="035fe-119">2 番目の使用率が、前に示した構文に示すように、`–`演算子は、*単項*式の負の値の否定演算子。</span><span class="sxs-lookup"><span data-stu-id="035fe-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="035fe-120">符号を反転することの否定は、この意味で`expression1`結果が正の値になるよう場合`expression1`が負の値。</span><span class="sxs-lookup"><span data-stu-id="035fe-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="035fe-121">いずれかの式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)、`–`演算子は 0 として処理します。</span><span class="sxs-lookup"><span data-stu-id="035fe-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="035fe-122">`–`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="035fe-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="035fe-123">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、その再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="035fe-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="035fe-124">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="035fe-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="035fe-125">例</span><span class="sxs-lookup"><span data-stu-id="035fe-125">Example</span></span>  
 <span data-ttu-id="035fe-126">次の例では、`–`演算子を計算し、2 つの数値の差を返すし、数値を否定します。</span><span class="sxs-lookup"><span data-stu-id="035fe-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 <span data-ttu-id="035fe-127">次のこれらのステートメントの実行`binaryResult`124.45 が含まれていますと`unaryResult`–334.90 が含まれています。</span><span class="sxs-lookup"><span data-stu-id="035fe-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035fe-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="035fe-128">See Also</span></span>  
 <span data-ttu-id="035fe-129">[-= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="035fe-129">[-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span></span>  
 [<span data-ttu-id="035fe-130">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="035fe-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="035fe-131">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="035fe-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="035fe-132">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="035fe-132">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
