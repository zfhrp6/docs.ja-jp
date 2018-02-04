---
title: "整数型 (Integer) (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba700cac58c96b3d6d2f5ed3c74fdd7e95761352
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="integer-data-type-visual-basic"></a><span data-ttu-id="02c87-102">整数データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02c87-102">Integer data type (Visual Basic)</span></span>
<span data-ttu-id="02c87-103">-2,147,483,648 から 2,147,483,647 までの符号付き 32 ビット (4 バイト) の整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="02c87-103">Holds signed 32-bit (4-byte) integers that range in value from -2,147,483,648 through 2,147,483,647.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02c87-104">コメント</span><span class="sxs-lookup"><span data-stu-id="02c87-104">Remarks</span></span>
 <span data-ttu-id="02c87-105">`Integer` データ型は、32 ビットのプロセッサでパフォーマンスが最大になります。</span><span class="sxs-lookup"><span data-stu-id="02c87-105">The `Integer` data type provides optimal performance on a 32-bit processor.</span></span> <span data-ttu-id="02c87-106">他の整数型では、メモリとの間の読み込みと格納により長い時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="02c87-106">The other integral types are slower to load and store from and to memory.</span></span>  
  
 <span data-ttu-id="02c87-107">`Integer` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="02c87-107">The default value of `Integer` is 0.</span></span>  

## <a name="literal-assignments"></a><span data-ttu-id="02c87-108">リテラルの割り当て</span><span class="sxs-lookup"><span data-stu-id="02c87-108">Literal assignments</span></span>

<span data-ttu-id="02c87-109">宣言して初期化することができます、`Integer`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。</span><span class="sxs-lookup"><span data-stu-id="02c87-109">You can declare and initialize an `Integer` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="02c87-110">整数リテラルが `Integer` の範囲外にある場合 (つまり、<xref:System.Int32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="02c87-110">If the integer literal is outside the range of `Integer` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="02c87-111">次の例では、整数 16,342 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Integer` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="02c87-111">In the following example, integers equal to 16,342 that are represented as decimal, hexadecimal, and binary literals are assigned to `Integer` values.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> <span data-ttu-id="02c87-112">プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="02c87-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="02c87-113">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="02c87-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="02c87-114">Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。</span><span class="sxs-lookup"><span data-stu-id="02c87-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

<span data-ttu-id="02c87-115">Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。</span><span class="sxs-lookup"><span data-stu-id="02c87-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="02c87-116">例:</span><span class="sxs-lookup"><span data-stu-id="02c87-116">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="02c87-117">数値リテラルを含めることも、 `I` [文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`Integer`データ型は、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="02c87-117">Numeric literals can also include the `I` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Integer` data type, as the following example shows.</span></span>

```vb
Dim number = &H_035826I
```

## <a name="programming-tips"></a><span data-ttu-id="02c87-118">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="02c87-118">Programming tips</span></span>

-   <span data-ttu-id="02c87-119">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="02c87-119">**Interop Considerations.**</span></span> <span data-ttu-id="02c87-120">オートメーションまたは COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合の点に注意`Integer`が他の環境で別のデータ幅 (16 ビット) を持ちます。</span><span class="sxs-lookup"><span data-stu-id="02c87-120">If you are interfacing with components not written for the .NET Framework, such as Automation or COM objects, remember that `Integer` has a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="02c87-121">そのようなコンポーネントに 16 ビットの引数を渡す場合は、新しい Visual Basic のコードで、整数型 (`Short`) ではなく短整数型 (`Integer`) として宣言します。</span><span class="sxs-lookup"><span data-stu-id="02c87-121">If you are passing a 16-bit argument to such a component, declare it as `Short` instead of `Integer` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="02c87-122">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="02c87-122">**Widening.**</span></span> <span data-ttu-id="02c87-123">`Integer` データ型は、`Long`、`Decimal`、`Single`、または `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="02c87-123">The `Integer` data type widens to `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="02c87-124">これは、`Integer` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="02c87-124">This means you can convert `Integer` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="02c87-125">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="02c87-125">**Type Characters.**</span></span> <span data-ttu-id="02c87-126">あるリテラルにリテラルの型文字 `I` を付けると、そのリテラルは `Integer` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="02c87-126">Appending the literal type character `I` to a literal forces it to the `Integer` data type.</span></span> <span data-ttu-id="02c87-127">ある識別子に識別子の型文字 `%` を付けると、その識別子は整数型 (`Integer`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="02c87-127">Appending the identifier type character `%` to any identifier forces it to `Integer`.</span></span>  
  
-   <span data-ttu-id="02c87-128">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="02c87-128">**Framework Type.**</span></span> <span data-ttu-id="02c87-129">.NET Framework において対応する型は、<xref:System.Int32?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="02c87-129">The corresponding type in the .NET Framework is the <xref:System.Int32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="02c87-130">範囲</span><span class="sxs-lookup"><span data-stu-id="02c87-130">Range</span></span>

<span data-ttu-id="02c87-131">整数型の変数をその型の範囲外の数値に設定しようとすると、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="02c87-131">If you try to set a variable of an integral type to a number outside the range for that type, an error occurs.</span></span> <span data-ttu-id="02c87-132">小数に設定しようとすると、最も近い整数値に丸められます。</span><span class="sxs-lookup"><span data-stu-id="02c87-132">If you try to set it to a fraction, the number is rounded up or down to the nearest integer value.</span></span> <span data-ttu-id="02c87-133">2 つの整数値に等しく近い場合は、最も近い偶数の整数に丸められます。</span><span class="sxs-lookup"><span data-stu-id="02c87-133">If the number is equally close to two integer values, the value is rounded to the nearest even integer.</span></span> <span data-ttu-id="02c87-134">この処理により、常に中間値を単一方向に丸めるために発生する丸め誤差が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="02c87-134">This behavior minimizes rounding errors that result from consistently rounding a midpoint value in a single direction.</span></span> <span data-ttu-id="02c87-135">丸めの例を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="02c87-135">The following code shows examples of rounding.</span></span>  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a><span data-ttu-id="02c87-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="02c87-136">See also</span></span>

<span data-ttu-id="02c87-137"><xref:System.Int32?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="02c87-137"><xref:System.Int32?displayProperty=nameWithType></span></span>   
 [<span data-ttu-id="02c87-138">データの種類</span><span class="sxs-lookup"><span data-stu-id="02c87-138">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="02c87-139">Long データ型</span><span class="sxs-lookup"><span data-stu-id="02c87-139">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="02c87-140">Short データ型</span><span class="sxs-lookup"><span data-stu-id="02c87-140">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="02c87-141">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="02c87-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="02c87-142">変換の概要</span><span class="sxs-lookup"><span data-stu-id="02c87-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="02c87-143">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="02c87-143">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
