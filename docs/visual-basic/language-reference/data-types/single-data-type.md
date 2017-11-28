---
title: "単精度浮動小数点型 (Single) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c91dbdf73ed1e26393518001ec8651557e5b780f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="56e65-102">単精度浮動小数点型 (Single) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56e65-102">Single Data Type (Visual Basic)</span></span>
<span data-ttu-id="56e65-103">IEEE 32 ビット (4 バイト) の単精度浮動小数点数が 3.4028235 e + 38 までの値の範囲の符号付き - 1.401298E を通じて-1.401298E と負の値の 45-から 3.4028235 e + 38 正の値の 45。</span><span class="sxs-lookup"><span data-stu-id="56e65-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="56e65-104">単精度の数値は、実数の概算値を格納します。</span><span class="sxs-lookup"><span data-stu-id="56e65-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56e65-105">コメント</span><span class="sxs-lookup"><span data-stu-id="56e65-105">Remarks</span></span>  
 <span data-ttu-id="56e65-106">使用して、`Single`データ型の完全なデータの幅を必要としない浮動小数点値を含む`Double`です。</span><span class="sxs-lookup"><span data-stu-id="56e65-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="56e65-107">場合によっては、共通言語ランタイムがパックすることがあります、`Single`変数密接に関連しておよびメモリの消費量を保存します。</span><span class="sxs-lookup"><span data-stu-id="56e65-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="56e65-108">`Single` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="56e65-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="56e65-109">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="56e65-109">Programming Tips</span></span>  
  
-   <span data-ttu-id="56e65-110">**有効桁数です。**</span><span class="sxs-lookup"><span data-stu-id="56e65-110">**Precision.**</span></span> <span data-ttu-id="56e65-111">浮動小数点数を使用する場合は、ことが常に正確に表現でないメモリに留意してください。</span><span class="sxs-lookup"><span data-stu-id="56e65-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="56e65-112">これにより予期しない結果を比較値などの特定の操作から、`Mod`演算子。</span><span class="sxs-lookup"><span data-stu-id="56e65-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="56e65-113">詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="56e65-113">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
-   <span data-ttu-id="56e65-114">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="56e65-114">**Widening.**</span></span> <span data-ttu-id="56e65-115">`Single`拡大変換後のデータ型`Double`です。</span><span class="sxs-lookup"><span data-stu-id="56e65-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="56e65-116">つまり、変換することができます`Single`に`Double`遭遇することがなく、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。</span><span class="sxs-lookup"><span data-stu-id="56e65-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="56e65-117">**後続のゼロです。**</span><span class="sxs-lookup"><span data-stu-id="56e65-117">**Trailing Zeros.**</span></span> <span data-ttu-id="56e65-118">浮動小数点データ型には、末尾の 0 文字の任意の内部表現はありません。</span><span class="sxs-lookup"><span data-stu-id="56e65-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="56e65-119">たとえば、それらによって区別されません 4.2000 および 4.2 です。</span><span class="sxs-lookup"><span data-stu-id="56e65-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="56e65-120">その結果、後続の 0 文字では、表示または浮動小数点値を印刷するときに表示されません。</span><span class="sxs-lookup"><span data-stu-id="56e65-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
-   <span data-ttu-id="56e65-121">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="56e65-121">**Type Characters.**</span></span> <span data-ttu-id="56e65-122">あるリテラルにリテラルの型文字 `F` を付けると、そのリテラルは `Single` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="56e65-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="56e65-123">ある識別子に識別子の型文字 `!` を付けると、その識別子は整数型 (`Single`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="56e65-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
-   <span data-ttu-id="56e65-124">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="56e65-124">**Framework Type.**</span></span> <span data-ttu-id="56e65-125">.NET Framework において対応する型は、<xref:System.Single?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="56e65-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e65-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="56e65-126">See Also</span></span>  
 <xref:System.Single?displayProperty=nameWithType>  
 [<span data-ttu-id="56e65-127">データの種類</span><span class="sxs-lookup"><span data-stu-id="56e65-127">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="56e65-128">Decimal データ型</span><span class="sxs-lookup"><span data-stu-id="56e65-128">Decimal Data Type</span></span>](../../../visual-basic/language-reference/data-types/decimal-data-type.md)  
 [<span data-ttu-id="56e65-129">Double 型</span><span class="sxs-lookup"><span data-stu-id="56e65-129">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="56e65-130">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="56e65-130">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="56e65-131">変換の概要</span><span class="sxs-lookup"><span data-stu-id="56e65-131">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="56e65-132">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="56e65-132">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="56e65-133">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="56e65-133">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
