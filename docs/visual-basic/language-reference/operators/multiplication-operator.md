---
title: '* 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 4e2d1000afcf8951e8914335f7b5a278b49f6277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603627"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="13552-102">\* 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13552-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="13552-103">2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="13552-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13552-104">構文</span><span class="sxs-lookup"><span data-stu-id="13552-104">Syntax</span></span>  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="13552-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="13552-105">Parts</span></span>  
  
|<span data-ttu-id="13552-106">用語</span><span class="sxs-lookup"><span data-stu-id="13552-106">Term</span></span>|<span data-ttu-id="13552-107">定義</span><span class="sxs-lookup"><span data-stu-id="13552-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="13552-108">必須。</span><span class="sxs-lookup"><span data-stu-id="13552-108">Required.</span></span> <span data-ttu-id="13552-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="13552-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="13552-110">必須。</span><span class="sxs-lookup"><span data-stu-id="13552-110">Required.</span></span> <span data-ttu-id="13552-111">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="13552-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="13552-112">結果</span><span class="sxs-lookup"><span data-stu-id="13552-112">Result</span></span>  
 <span data-ttu-id="13552-113">結果は、製品の`number1`と`number2`です。</span><span class="sxs-lookup"><span data-stu-id="13552-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="13552-114">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="13552-114">Supported Types</span></span>  
 <span data-ttu-id="13552-115">符号なしと浮動小数点型を含むすべての数値型と`Decimal`です。</span><span class="sxs-lookup"><span data-stu-id="13552-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13552-116">コメント</span><span class="sxs-lookup"><span data-stu-id="13552-116">Remarks</span></span>  
 <span data-ttu-id="13552-117">結果のデータ型は、オペランドの型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="13552-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="13552-118">次の表では、結果のデータ型を決定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="13552-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="13552-119">オペランドのデータ型</span><span class="sxs-lookup"><span data-stu-id="13552-119">Operand data types</span></span>|<span data-ttu-id="13552-120">結果のデータ型</span><span class="sxs-lookup"><span data-stu-id="13552-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="13552-121">両方の式が整数データ型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[バイト](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[短い](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span><span class="sxs-lookup"><span data-stu-id="13552-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="13552-122">数値データ型のデータ型に適した`number1`と`number2`です。</span><span class="sxs-lookup"><span data-stu-id="13552-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="13552-123">「整数算術演算による」テーブルを参照して[データ型の演算子の結果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)です。</span><span class="sxs-lookup"><span data-stu-id="13552-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="13552-124">両方の式が[10 進数](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="13552-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="13552-125">両方の式が[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="13552-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="13552-126">いずれかの式は、浮動小数点データ型 (`Single`または[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)) 両方ではなく`Single`(注`Decimal`浮動小数点データ型ではない)</span><span class="sxs-lookup"><span data-stu-id="13552-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="13552-127">式が評価された場合[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。</span><span class="sxs-lookup"><span data-stu-id="13552-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="13552-128">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="13552-128">Overloading</span></span>  
 <span data-ttu-id="13552-129">`*`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。</span><span class="sxs-lookup"><span data-stu-id="13552-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="13552-130">コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。</span><span class="sxs-lookup"><span data-stu-id="13552-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="13552-131">詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。</span><span class="sxs-lookup"><span data-stu-id="13552-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13552-132">例</span><span class="sxs-lookup"><span data-stu-id="13552-132">Example</span></span>  
 <span data-ttu-id="13552-133">この例では、`*`演算子を 2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="13552-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="13552-134">2 つのオペランドの積になります。</span><span class="sxs-lookup"><span data-stu-id="13552-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="13552-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="13552-135">See Also</span></span>  
 [<span data-ttu-id="13552-136">\*= 演算子</span><span class="sxs-lookup"><span data-stu-id="13552-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [<span data-ttu-id="13552-137">算術演算子</span><span class="sxs-lookup"><span data-stu-id="13552-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="13552-138">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="13552-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="13552-139">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="13552-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="13552-140">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="13552-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
