---
title: "SByte 型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.sbyte
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- SByte data type
ms.assetid: 5c38374a-18a1-4cc2-b493-299e3dcaa60f
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2bcd00665ec5b8651089811a61212bfa302fe95d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sbyte-data-type-visual-basic"></a><span data-ttu-id="28c07-102">SByte データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28c07-102">SByte data type (Visual Basic)</span></span>

<span data-ttu-id="28c07-103">符号付き 8 ビット (1 バイト) 整数-128 から 127 までさまざまです。</span><span class="sxs-lookup"><span data-stu-id="28c07-103">Holds signed 8-bit (1-byte) integers that range in value from -128 through 127.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28c07-104">コメント</span><span class="sxs-lookup"><span data-stu-id="28c07-104">Remarks</span></span>

<span data-ttu-id="28c07-105">使用して、`SByte`データ型の完全なデータの幅を必要としない整数値を含む`Integer`のデータの半分の幅も`Short`します。</span><span class="sxs-lookup"><span data-stu-id="28c07-105">Use the `SByte` data type to contain integer values that do not require the full data width of `Integer` or even the half data width of `Short`.</span></span> <span data-ttu-id="28c07-106">場合によっては、共通言語ランタイムがパックすることがあります、`SByte`変数密接に関連しておよびメモリの消費量を保存します。</span><span class="sxs-lookup"><span data-stu-id="28c07-106">In some cases, the common language runtime might be able to pack your `SByte` variables closely together and save memory consumption.</span></span>

<span data-ttu-id="28c07-107">`SByte` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="28c07-107">The default value of `SByte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="28c07-108">リテラルの割り当て</span><span class="sxs-lookup"><span data-stu-id="28c07-108">Literal assignments</span></span>
  
<span data-ttu-id="28c07-109">宣言して初期化することができます、`SByte`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。</span><span class="sxs-lookup"><span data-stu-id="28c07-109">You can declare and initialize an `SByte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span>

<span data-ttu-id="28c07-110">次の例では、整数と等しい 16 進数、10 進数として表される-102 およびに割り当てられているバイナリ リテラル`SByte`値。</span><span class="sxs-lookup"><span data-stu-id="28c07-110">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are assigned to `SByte` values.</span></span> <span data-ttu-id="28c07-111">この例では、使用してコンパイルする必要があります、`/removeintchecks`コンパイラ スイッチ。</span><span class="sxs-lookup"><span data-stu-id="28c07-111">This example requires that you compile with the `/removeintchecks` compiler switch.</span></span>

[!code-vb[SByte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByte)]  

> [!NOTE] 
> <span data-ttu-id="28c07-112">プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="28c07-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="28c07-113">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="28c07-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="28c07-114">Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。</span><span class="sxs-lookup"><span data-stu-id="28c07-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[SByteSeparator](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#SByteS)]  

<span data-ttu-id="28c07-115">整数リテラルが `SByte` の範囲外にある場合 (つまり、<xref:System.SByte.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.SByte.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="28c07-115">If the integer literal is outside the range of `SByte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=nameWithType> or greater than <xref:System.SByte.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span> <span data-ttu-id="28c07-116">整数リテラルには、サフィックスがあるない場合に、[整数](integer-data-type.md)推論されます。</span><span class="sxs-lookup"><span data-stu-id="28c07-116">When an integer literal has no suffix, an [Integer](integer-data-type.md) is inferred.</span></span> <span data-ttu-id="28c07-117">整数リテラルは、範囲の場合、`Integer`型、[長い](long-data-type.md)推論されます。</span><span class="sxs-lookup"><span data-stu-id="28c07-117">If the integer literal is outside the range of the `Integer` type, a [Long](long-data-type.md) is inferred.</span></span> <span data-ttu-id="28c07-118">つまり、前の例では、数値リテラルで`0x9A`と`0b10011010`が 32 ビット符号付き整数を超える 156 の値として解釈される<xref:System.SByte.MaxValue?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="28c07-118">This means that, in the previous examples, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="28c07-119">正常にコンパイルする 10 進数以外の整数を代入するこのようなコードを`SByte`次のいずれかを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="28c07-119">To successfully compile code like this that assigns a non-decimal integer to an `SByte`, you can do either of the following:</span></span>

- <span data-ttu-id="28c07-120">コンパイルすると整数の範囲チェックを無効にする、`/removeintchecks`コンパイラ スイッチ。</span><span class="sxs-lookup"><span data-stu-id="28c07-120">Disable integer bounds checks by compiling with the `/removeintchecks` compiler switch.</span></span>

- <span data-ttu-id="28c07-121">使用して、[文字入力](../../programming-guide\language-features\data-types/type-characters.md)に割り当てるリテラルの値を明示的に定義する、`SByte`です。</span><span class="sxs-lookup"><span data-stu-id="28c07-121">Use a [type character](../../programming-guide\language-features\data-types/type-characters.md) to explicitly define the literal value that you want to assign to the `SByte`.</span></span> <span data-ttu-id="28c07-122">次の例では、負の値のリテラル`Short`値を`SByte`です。</span><span class="sxs-lookup"><span data-stu-id="28c07-122">The following example assigns a negative literal `Short` value to an `SByte`.</span></span> <span data-ttu-id="28c07-123">なお、負の値、数値リテラルの上位ワードの上位ビットを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="28c07-123">Note that, for negative numbers, the high-order bit of the high-order word of the numeric literal must be set.</span></span> <span data-ttu-id="28c07-124">このビットの場合はこの例では、リテラルの 15`Short`値。</span><span class="sxs-lookup"><span data-stu-id="28c07-124">In the case of our example, this is bit 15 of the literal `Short` value.</span></span>

   [!code-vb[SByteTypeChars](../../../../samples/snippets/visualbasic/language-reference/data-types/sbyte-assignment.vb#1)]

## <a name="programming-tips"></a><span data-ttu-id="28c07-125">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="28c07-125">Programming tips</span></span>
  
-   <span data-ttu-id="28c07-126">**CLS 準拠しています。**</span><span class="sxs-lookup"><span data-stu-id="28c07-126">**CLS Compliance.**</span></span> <span data-ttu-id="28c07-127">`SByte`データ型がの一部、[共通言語仕様](http://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)、CLS 準拠コードがそれを使用するコンポーネントを使用できないようにします。</span><span class="sxs-lookup"><span data-stu-id="28c07-127">The `SByte` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

-   <span data-ttu-id="28c07-128">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="28c07-128">**Widening.**</span></span> <span data-ttu-id="28c07-129">`SByte`拡大変換後のデータ型`Short`、 `Integer`、 `Long`、 `Decimal`、 `Single`、および`Double`です。</span><span class="sxs-lookup"><span data-stu-id="28c07-129">The `SByte` data type widens to `Short`, `Integer`, `Long`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="28c07-130">つまり、変換することができます`SByte`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。</span><span class="sxs-lookup"><span data-stu-id="28c07-130">This means you can convert `SByte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="28c07-131">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="28c07-131">**Type Characters.**</span></span> <span data-ttu-id="28c07-132">`SByte`リテラルの型文字または識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="28c07-132">`SByte` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="28c07-133">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="28c07-133">**Framework Type.**</span></span> <span data-ttu-id="28c07-134">.NET Framework において対応する型は、<xref:System.SByte?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="28c07-134">The corresponding type in the .NET Framework is the <xref:System.SByte?displayProperty=nameWithType> structure.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="28c07-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="28c07-135">See also</span></span>

 <xref:System.SByte?displayProperty=nameWithType>  
 [<span data-ttu-id="28c07-136">データの種類</span><span class="sxs-lookup"><span data-stu-id="28c07-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="28c07-137">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="28c07-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="28c07-138">変換の概要</span><span class="sxs-lookup"><span data-stu-id="28c07-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="28c07-139">Short データ型</span><span class="sxs-lookup"><span data-stu-id="28c07-139">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [<span data-ttu-id="28c07-140">整数データ型</span><span class="sxs-lookup"><span data-stu-id="28c07-140">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="28c07-141">Long データ型</span><span class="sxs-lookup"><span data-stu-id="28c07-141">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [<span data-ttu-id="28c07-142">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="28c07-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
