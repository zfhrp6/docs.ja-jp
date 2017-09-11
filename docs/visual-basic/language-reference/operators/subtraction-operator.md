---
title: "- 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Negate
- vb.-
dev_langs:
- VB
helpviewer_keywords:
- '- operator [Visual Basic]'
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator
- operators [Visual Basic], arithmetic
- subtraction operator, syntax
- arithmetic operators, subtraction
- difference operator
- math operators
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: 14
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
ms.openlocfilehash: eb9b8e94877cce9aacde69c5f555f4a7f4a9ad7c
ms.contentlocale: ja-jp
ms.lasthandoff: 05/23/2017

---
# <a name="--operator-visual-basic"></a><span data-ttu-id="c1d19-102">- 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1d19-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="c1d19-103">2 つの数値式または数値式の負の値の差を返します。</span><span class="sxs-lookup"><span data-stu-id="c1d19-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1d19-104">構文</span><span class="sxs-lookup"><span data-stu-id="c1d19-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="c1d19-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c1d19-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="c1d19-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="c1d19-106">Required.</span></span> <span data-ttu-id="c1d19-107">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="c1d19-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="c1d19-108">場合のみ必要、`–`演算子が負の値を計算します。</span><span class="sxs-lookup"><span data-stu-id="c1d19-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="c1d19-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="c1d19-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="c1d19-110">結果</span><span class="sxs-lookup"><span data-stu-id="c1d19-110">Result</span></span>  
 <span data-ttu-id="c1d19-111">結果の違いは、`expression1`と`expression2`、またはの符号反転値`expression1`です。</span><span class="sxs-lookup"><span data-stu-id="c1d19-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="c1d19-112">結果のデータ型が数値型のデータ型に適した`expression1`と`expression2`です。</span><span class="sxs-lookup"><span data-stu-id="c1d19-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="c1d19-113">「整数演算」テーブルが表示[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。</span><span class="sxs-lookup"><span data-stu-id="c1d19-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="c1d19-114">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="c1d19-114">Supported Types</span></span>  
 <span data-ttu-id="c1d19-115">すべての数値型。</span><span class="sxs-lookup"><span data-stu-id="c1d19-115">All numeric types.</span></span> <span data-ttu-id="c1d19-116">署名なしで、浮動小数点型を含む、`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="c1d19-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1d19-117">コメント</span><span class="sxs-lookup"><span data-stu-id="c1d19-117">Remarks</span></span>  
 <span data-ttu-id="c1d19-118">最初の使用率が、前に示した構文に示すように、`–`演算子は、*バイナリ*違いについては、2 つの数値式の間で減算演算子。</span><span class="sxs-lookup"><span data-stu-id="c1d19-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="c1d19-119">2 つ目の使用率が、前に示した構文に示すように、`–`演算子は、*単項*式の負の値を否定演算子。</span><span class="sxs-lookup"><span data-stu-id="c1d19-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="c1d19-120">符号を逆の符号を反転は、この意味で`expression1`、結果は正ように場合`expression1`が負の値。</span><span class="sxs-lookup"><span data-stu-id="c1d19-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="c1d19-121">いずれかの式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)、`–`演算子は&0; として処理します。</span><span class="sxs-lookup"><span data-stu-id="c1d19-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1d19-122">`–`演算子を指定できます*オーバー ロードされた*、つまり、クラスまたは構造体を再定義できます動作オペランドは、そのクラスまたは構造体の型を持つ場合です。</span><span class="sxs-lookup"><span data-stu-id="c1d19-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c1d19-123">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、その再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="c1d19-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="c1d19-124">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)します。</span><span class="sxs-lookup"><span data-stu-id="c1d19-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1d19-125">例</span><span class="sxs-lookup"><span data-stu-id="c1d19-125">Example</span></span>  
 <span data-ttu-id="c1d19-126">次の例では、`–`演算子を計算し、2 つの数値の差を返すし、数値を否定します。</span><span class="sxs-lookup"><span data-stu-id="c1d19-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 <span data-ttu-id="c1d19-127">[!code-vb[VbVbalrOperators&#10;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c1d19-127">[!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="c1d19-128">これらのステートメントの実行される`binaryResult`124.45 が含まれていて、 `unaryResult` –334.90 が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1d19-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d19-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1d19-129">See Also</span></span>  
 <span data-ttu-id="c1d19-130">[-= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="c1d19-130">[-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="c1d19-131"> [Visual Basic の演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="c1d19-131"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="c1d19-132"> [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="c1d19-132"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="c1d19-133"> [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="c1d19-133"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

