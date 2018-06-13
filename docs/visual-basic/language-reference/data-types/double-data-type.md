---
title: 倍精度浮動小数点数型 (Double) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: c2d3d7d360ccb240bafbe0e19e9f396adfba7f7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590265"
---
# <a name="double-data-type-visual-basic"></a><span data-ttu-id="5f875-102">倍精度浮動小数点数型 (Double) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f875-102">Double Data Type (Visual Basic)</span></span>
<span data-ttu-id="5f875-103">-- をからの値の範囲は IEEE の 64 ビット (8 バイト) の倍精度浮動小数点数の符号付き 4.94065645841246544E-負の値と 4.94065645841246544E から 324-324 1.79769313486231570 e + 308 ~正の値。</span><span class="sxs-lookup"><span data-stu-id="5f875-103">Holds signed IEEE 64-bit (8-byte) double-precision floating-point numbers that range in value from -1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values and from 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span> <span data-ttu-id="5f875-104">倍精度数値には、実数の概算値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="5f875-104">Double-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f875-105">コメント</span><span class="sxs-lookup"><span data-stu-id="5f875-105">Remarks</span></span>  
 <span data-ttu-id="5f875-106">`Double`データ型、最大および最小規模が大きくを提供しています。</span><span class="sxs-lookup"><span data-stu-id="5f875-106">The `Double` data type provides the largest and smallest possible magnitudes for a number.</span></span>  
  
 <span data-ttu-id="5f875-107">`Double` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="5f875-107">The default value of `Double` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="5f875-108">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="5f875-108">Programming Tips</span></span>  
  
-   <span data-ttu-id="5f875-109">**有効桁数です。**</span><span class="sxs-lookup"><span data-stu-id="5f875-109">**Precision.**</span></span> <span data-ttu-id="5f875-110">浮動小数点数を使用する場合は、ことが常に正確に表現でないメモリに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5f875-110">When you work with floating-point numbers, remember that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="5f875-111">これにより予期しない結果を比較値などの特定の操作から、`Mod`演算子。</span><span class="sxs-lookup"><span data-stu-id="5f875-111">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="5f875-112">詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f875-112">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="5f875-113">**後続のゼロです。**</span><span class="sxs-lookup"><span data-stu-id="5f875-113">**Trailing Zeros.**</span></span> <span data-ttu-id="5f875-114">浮動小数点データ型には、後続のゼロ文字の任意の内部表現はありません。</span><span class="sxs-lookup"><span data-stu-id="5f875-114">The floating-point data types do not have any internal representation of trailing zero characters.</span></span> <span data-ttu-id="5f875-115">たとえば、それらによって区別されません 4.2000 および 4.2 です。</span><span class="sxs-lookup"><span data-stu-id="5f875-115">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="5f875-116">したがって、末尾のゼロは表示されませんを表示する場合、または印刷の浮動小数点値。</span><span class="sxs-lookup"><span data-stu-id="5f875-116">Consequently, trailing zero characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="5f875-117">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="5f875-117">**Type Characters.**</span></span> <span data-ttu-id="5f875-118">あるリテラルにリテラルの型文字 `R` を付けると、そのリテラルは `Double` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="5f875-118">Appending the literal type character `R` to a literal forces it to the `Double` data type.</span></span> <span data-ttu-id="5f875-119">たとえば、整数値が続く場合`R`に値が変更された、`Double`です。</span><span class="sxs-lookup"><span data-stu-id="5f875-119">For example, if an integer value is followed by `R`, the value is changed to a `Double`.</span></span>  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     <span data-ttu-id="5f875-120">ある識別子に識別子の型文字 `#` を付けると、その識別子は整数型 (`Double`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="5f875-120">Appending the identifier type character `#` to any identifier forces it to `Double`.</span></span> <span data-ttu-id="5f875-121">次の例では、変数`num`として型指定されて、 `Double`:</span><span class="sxs-lookup"><span data-stu-id="5f875-121">In the following example, the variable `num` is typed as a `Double`:</span></span>  
  
    ```  
    Dim num# = 3  
    ```  
  
-   <span data-ttu-id="5f875-122">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="5f875-122">**Framework Type.**</span></span> <span data-ttu-id="5f875-123">.NET Framework において対応する型は、<xref:System.Double?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="5f875-123">The corresponding type in the .NET Framework is the <xref:System.Double?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f875-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f875-124">See Also</span></span>  
 <xref:System.Double?displayProperty=nameWithType>  
 [<span data-ttu-id="5f875-125">データの種類</span><span class="sxs-lookup"><span data-stu-id="5f875-125">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="5f875-126">Decimal データ型</span><span class="sxs-lookup"><span data-stu-id="5f875-126">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="5f875-127">Single データ型</span><span class="sxs-lookup"><span data-stu-id="5f875-127">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [<span data-ttu-id="5f875-128">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="5f875-128">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="5f875-129">変換の概要</span><span class="sxs-lookup"><span data-stu-id="5f875-129">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="5f875-130">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="5f875-130">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="5f875-131">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="5f875-131">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="5f875-132">型文字</span><span class="sxs-lookup"><span data-stu-id="5f875-132">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
