---
title: 10 進型 (Decimal) (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Decimal
helpviewer_keywords:
- literal type characters [Visual Basic], D
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- Decimal data type
- D literal type character [Visual Basic]
- decimals, Decimal data type
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- decimal keyword [Visual Basic]
- numbers [Visual Basic], real
- variable-precision numbers
- zeros, trailing
- '@ identifier type character'
- identifier type characters [Visual Basic], @
ms.assetid: 1d855b45-afe2-45b0-a623-96b6f63a43d5
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55a9293fa680a7a04cff4099654d4d66790e8d3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="decimal-data-type-visual-basic"></a><span data-ttu-id="11acb-102">10 進型 (Decimal) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11acb-102">Decimal Data Type (Visual Basic)</span></span>
<span data-ttu-id="11acb-103">可変 10 の累乗によってスケーリング 96 ビット (12 バイト) 整数値を表す 128 ビット (16 バイト) 値の符号付き保持します。</span><span class="sxs-lookup"><span data-stu-id="11acb-103">Holds signed 128-bit (16-byte) values representing 96-bit (12-byte) integer numbers scaled by a variable power of 10.</span></span> <span data-ttu-id="11acb-104">スケール ファクターです。 小数点の右側にある数字の数を指定します。範囲は 0 から 28 です。</span><span class="sxs-lookup"><span data-stu-id="11acb-104">The scaling factor specifies the number of digits to the right of the decimal point; it ranges from 0 through 28.</span></span> <span data-ttu-id="11acb-105">最大有効値は 0 (小数点は除く) の小数点以下桁数、79,228,162,514,264,337,593,543,950,335 +/-(7 +/-.9228162514264337593543950335E + 28)。</span><span class="sxs-lookup"><span data-stu-id="11acb-105">With a scale of 0 (no decimal places), the largest possible value is +/-79,228,162,514,264,337,593,543,950,335 (+/-7.9228162514264337593543950335E+28).</span></span> <span data-ttu-id="11acb-106">小数点以下桁数が 28 7.9228162514264337593543950335 については、最大値し、(1 e ~ 28) +/-+/-0.0000000000000000000000000001 は、0 以外の最小値。</span><span class="sxs-lookup"><span data-stu-id="11acb-106">With 28 decimal places, the largest value is +/-7.9228162514264337593543950335, and the smallest nonzero value is +/-0.0000000000000000000000000001 (+/-1E-28).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11acb-107">コメント</span><span class="sxs-lookup"><span data-stu-id="11acb-107">Remarks</span></span>  
 <span data-ttu-id="11acb-108">`Decimal`データ型有効桁数の最大数を提供しています。</span><span class="sxs-lookup"><span data-stu-id="11acb-108">The `Decimal` data type provides the greatest number of significant digits for a number.</span></span> <span data-ttu-id="11acb-109">最大 29 桁をサポートしており 7.9228 x 10 を超える値を表すことができる ^28 です。</span><span class="sxs-lookup"><span data-stu-id="11acb-109">It supports up to 29 significant digits and can represent values in excess of 7.9228 x 10^28.</span></span> <span data-ttu-id="11acb-110">など、計算に特に適しています財務、桁の数字の数が多い必要がありますが、丸め誤差が許容することはできません。</span><span class="sxs-lookup"><span data-stu-id="11acb-110">It is particularly suitable for calculations, such as financial, that require a large number of digits but cannot tolerate rounding errors.</span></span>  
  
 <span data-ttu-id="11acb-111">`Decimal` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="11acb-111">The default value of `Decimal` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="11acb-112">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="11acb-112">Programming Tips</span></span>  
  
-   <span data-ttu-id="11acb-113">**有効桁数です。**</span><span class="sxs-lookup"><span data-stu-id="11acb-113">**Precision.**</span></span> <span data-ttu-id="11acb-114">`Decimal`浮動小数点データ型がありません。</span><span class="sxs-lookup"><span data-stu-id="11acb-114">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="11acb-115">`Decimal`構造体は、符号ビット、およびスケール ファクター値のどの部分が、小数を指定する整数のバイナリ整数値を保持します。</span><span class="sxs-lookup"><span data-stu-id="11acb-115">The `Decimal` structure holds a binary integer value, together with a sign bit and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span> <span data-ttu-id="11acb-116">このため、`Decimal`番号より正確な表現を持つ浮動小数点型よりもメモリ内 (`Single`と`Double`)。</span><span class="sxs-lookup"><span data-stu-id="11acb-116">Because of this, `Decimal` numbers have a more precise representation in memory than floating-point types (`Single` and `Double`).</span></span>  
  
-   <span data-ttu-id="11acb-117">**パフォーマンス。**</span><span class="sxs-lookup"><span data-stu-id="11acb-117">**Performance.**</span></span> <span data-ttu-id="11acb-118">`Decimal`データ型はすべての数値型の最も遅い。</span><span class="sxs-lookup"><span data-stu-id="11acb-118">The `Decimal` data type is the slowest of all the numeric types.</span></span> <span data-ttu-id="11acb-119">データ型を選択する前にパフォーマンスと精度の重要性を比較検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11acb-119">You should weigh the importance of precision against performance before choosing a data type.</span></span>  
  
-   <span data-ttu-id="11acb-120">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="11acb-120">**Widening.**</span></span> <span data-ttu-id="11acb-121">`Decimal`拡大変換後のデータ型`Single`または`Double`です。</span><span class="sxs-lookup"><span data-stu-id="11acb-121">The `Decimal` data type widens to `Single` or `Double`.</span></span> <span data-ttu-id="11acb-122">つまり、変換することができます`Decimal`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。</span><span class="sxs-lookup"><span data-stu-id="11acb-122">This means you can convert `Decimal` to either of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="11acb-123">**後続のゼロです。**</span><span class="sxs-lookup"><span data-stu-id="11acb-123">**Trailing Zeros.**</span></span> <span data-ttu-id="11acb-124">Visual Basic では、後続の 0 は格納されません、`Decimal`リテラルです。</span><span class="sxs-lookup"><span data-stu-id="11acb-124">Visual Basic does not store trailing zeros in a `Decimal` literal.</span></span> <span data-ttu-id="11acb-125">ただし、`Decimal`変数には、計算に必要なすべての後続のゼロが保持されます。</span><span class="sxs-lookup"><span data-stu-id="11acb-125">However, a `Decimal` variable preserves any trailing zeros acquired computationally.</span></span> <span data-ttu-id="11acb-126">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="11acb-126">The following example illustrates this.</span></span>  
  
    ```  
    Dim d1, d2, d3, d4 As Decimal  
    d1 = 2.375D  
    d2 = 1.625D  
    d3 = d1 + d2  
    d4 = 4.000D  
    MsgBox("d1 = " & CStr(d1) & ", d2 = " & CStr(d2) &  
          ", d3 = " & CStr(d3) & ", d4 = " & CStr(d4))  
    ```  
  
     <span data-ttu-id="11acb-127">出力`MsgBox`前の例では、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="11acb-127">The output of `MsgBox` in the preceding example is as follows:</span></span>  
  
     <span data-ttu-id="11acb-128">d1 2.375、d2 を = = 1.625、d3 4.000、d4 = 4 を =</span><span class="sxs-lookup"><span data-stu-id="11acb-128">d1 = 2.375, d2 = 1.625, d3 = 4.000, d4 = 4</span></span>  
  
-   <span data-ttu-id="11acb-129">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="11acb-129">**Type Characters.**</span></span> <span data-ttu-id="11acb-130">あるリテラルにリテラルの型文字 `D` を付けると、そのリテラルは `Decimal` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="11acb-130">Appending the literal type character `D` to a literal forces it to the `Decimal` data type.</span></span> <span data-ttu-id="11acb-131">ある識別子に識別子の型文字 `@` を付けると、その識別子は整数型 (`Decimal`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="11acb-131">Appending the identifier type character `@` to any identifier forces it to `Decimal`.</span></span>  
  
-   <span data-ttu-id="11acb-132">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="11acb-132">**Framework Type.**</span></span> <span data-ttu-id="11acb-133">.NET Framework において対応する型は、<xref:System.Decimal?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="11acb-133">The corresponding type in the .NET Framework is the <xref:System.Decimal?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="range"></a><span data-ttu-id="11acb-134">範囲</span><span class="sxs-lookup"><span data-stu-id="11acb-134">Range</span></span>  
 <span data-ttu-id="11acb-135">使用する必要があります、`D`に大きな値を代入する文字を入力、`Decimal`変数または定数。</span><span class="sxs-lookup"><span data-stu-id="11acb-135">You might need to use the `D` type character to assign a large value to a `Decimal` variable or constant.</span></span> <span data-ttu-id="11acb-136">この要件は、コンパイラが、リテラルとして解釈されるので`Long`リテラルの型文字以下の例のように、リテラルに依存しない限り、します。</span><span class="sxs-lookup"><span data-stu-id="11acb-136">This requirement is because the compiler interprets a literal as `Long` unless a literal type character follows the literal, as the following example shows.</span></span>  
  
```  
Dim bigDec1 As Decimal = 9223372036854775807   ' No overflow.  
Dim bigDec2 As Decimal = 9223372036854775808   ' Overflow.  
Dim bigDec3 As Decimal = 9223372036854775808D  ' No overflow.  
```  
  
 <span data-ttu-id="11acb-137">宣言`bigDec1`に割り当てられている値の範囲に収まるので、オーバーフローを生成しない`Long`です。</span><span class="sxs-lookup"><span data-stu-id="11acb-137">The declaration for `bigDec1` doesn't produce an overflow because the value that's assigned to it falls within the range for `Long`.</span></span> <span data-ttu-id="11acb-138">`Long`に値を割り当てることができます、`Decimal`変数。</span><span class="sxs-lookup"><span data-stu-id="11acb-138">The `Long` value can be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="11acb-139">宣言`bigDec2`用に割り当てられている値が大きすぎるために、オーバーフロー エラーが発生`Long`です。</span><span class="sxs-lookup"><span data-stu-id="11acb-139">The declaration for `bigDec2` generates an overflow error because the value that's assigned to it is too large for `Long`.</span></span> <span data-ttu-id="11acb-140">数値リテラルとして最初に解釈できないため、`Long`に割り当てることができない、`Decimal`変数。</span><span class="sxs-lookup"><span data-stu-id="11acb-140">Because the numeric literal can't first be interpreted as a `Long`, it can't be assigned to the `Decimal` variable.</span></span>  
  
 <span data-ttu-id="11acb-141">`bigDec3`、リテラルの型文字`D`としてリテラルを解釈するコンパイラを強制することで問題が解決、`Decimal`の代わりとして、`Long`です。</span><span class="sxs-lookup"><span data-stu-id="11acb-141">For `bigDec3`, the literal type character `D` solves the problem by forcing the compiler to interpret the literal as a `Decimal` instead of as a `Long`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11acb-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="11acb-142">See Also</span></span>  
 <xref:System.Decimal?displayProperty=nameWithType>  
 <xref:System.Decimal.%23ctor%2A?displayProperty=nameWithType>  
 <xref:System.Math.Round%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="11acb-143">データの種類</span><span class="sxs-lookup"><span data-stu-id="11acb-143">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="11acb-144">Single データ型</span><span class="sxs-lookup"><span data-stu-id="11acb-144">Single Data Type</span></span>](../../../visual-basic/language-reference/data-types/single-data-type.md)  
 [<span data-ttu-id="11acb-145">Double 型</span><span class="sxs-lookup"><span data-stu-id="11acb-145">Double Data Type</span></span>](../../../visual-basic/language-reference/data-types/double-data-type.md)  
 [<span data-ttu-id="11acb-146">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="11acb-146">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="11acb-147">変換の概要</span><span class="sxs-lookup"><span data-stu-id="11acb-147">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="11acb-148">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="11acb-148">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
