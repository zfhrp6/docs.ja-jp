---
title: Short 型 (Visual Basic)
ms.date: 01/31/2018
author: rpetrusha
ms.author: ronpet
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: ef99743828d8d80844486b651178622ff45fd554
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590713"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="0bfa5-102">Short データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bfa5-102">Short data type (Visual Basic)</span></span>
<span data-ttu-id="0bfa5-103">符号付き 16 ビット (2 バイト) 整数-32,768 からの値の範囲は、32,767 までです。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bfa5-104">コメント</span><span class="sxs-lookup"><span data-stu-id="0bfa5-104">Remarks</span></span>  
 <span data-ttu-id="0bfa5-105">使用して、`Short`データ型の完全なデータの幅を必要としない整数値を含む`Integer`です。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="0bfa5-106">場合によっては、共通言語ランタイムがパックことができます、`Short`変数密接に関連しておよびメモリの消費量を保存します。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="0bfa5-107">`Short` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="0bfa5-108">リテラルの割り当て</span><span class="sxs-lookup"><span data-stu-id="0bfa5-108">Literal assignments</span></span>

<span data-ttu-id="0bfa5-109">宣言して初期化することができます、`Short`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="0bfa5-110">整数リテラルが `Short` の範囲外にある場合 (つまり、<xref:System.Int16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="0bfa5-111">次の例では、整数と等しい 16 進数、10 進数として表される 1,034 およびからバイナリ リテラルを暗黙的に変換[整数](integer-data-type.md)に`Short`値。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="0bfa5-112">プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="0bfa5-113">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="0bfa5-114">Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="0bfa5-115">Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="0bfa5-116">例えば:</span><span class="sxs-lookup"><span data-stu-id="0bfa5-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="0bfa5-117">数値リテラルを含めることも、 `S` [文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`Short`データ型は、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-117">Numeric literals can also include the `S` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="0bfa5-118">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="0bfa5-118">Programming tips</span></span>

-   <span data-ttu-id="0bfa5-119">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="0bfa5-119">**Widening.**</span></span> <span data-ttu-id="0bfa5-120">`Short`拡大変換後のデータ型`Integer`、 `Long`、 `Decimal`、 `Single`、または`Double`です。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="0bfa5-121">これは、`Short` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="0bfa5-122">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="0bfa5-122">**Type Characters.**</span></span> <span data-ttu-id="0bfa5-123">あるリテラルにリテラルの型文字 `S` を付けると、そのリテラルは `Short` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="0bfa5-124">`Short` 識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-124">`Short` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="0bfa5-125">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="0bfa5-125">**Framework Type.**</span></span> <span data-ttu-id="0bfa5-126">.NET Framework において対応する型は、<xref:System.Int16?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="0bfa5-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bfa5-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bfa5-127">See also</span></span>

 <xref:System.Int16?displayProperty=nameWithType>  
 [<span data-ttu-id="0bfa5-128">データの種類</span><span class="sxs-lookup"><span data-stu-id="0bfa5-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="0bfa5-129">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="0bfa5-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="0bfa5-130">変換の概要</span><span class="sxs-lookup"><span data-stu-id="0bfa5-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="0bfa5-131">整数データ型</span><span class="sxs-lookup"><span data-stu-id="0bfa5-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="0bfa5-132">Long データ型</span><span class="sxs-lookup"><span data-stu-id="0bfa5-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="0bfa5-133">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="0bfa5-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
