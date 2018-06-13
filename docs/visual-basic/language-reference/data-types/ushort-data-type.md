---
title: UShort 型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ushort
helpviewer_keywords:
- numbers [Visual Basic], whole
- literal type characters [Visual Basic], US
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- UShort data type
- US literal type characters [Visual Basic]
ms.assetid: 138db892-665d-4ba8-9cae-d8d91c4a8f39
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 520c21d4df5c340b41a8b1e9055b3fadddfdf6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590369"
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="dcc68-102">UShort データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcc68-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="dcc68-103">保持符号なし 16 ビット (2 バイト) 整数値 0 から 65,535 までの範囲です。</span><span class="sxs-lookup"><span data-stu-id="dcc68-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcc68-104">コメント</span><span class="sxs-lookup"><span data-stu-id="dcc68-104">Remarks</span></span>

 <span data-ttu-id="dcc68-105">使用して、`UShort`に対して大きすぎますバイナリ データを格納するデータ型`Byte`です。</span><span class="sxs-lookup"><span data-stu-id="dcc68-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="dcc68-106">`UShort` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="dcc68-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="dcc68-107">リテラルの割り当て</span><span class="sxs-lookup"><span data-stu-id="dcc68-107">Literal assignments</span></span>

<span data-ttu-id="dcc68-108">宣言して初期化することができます、`UShort`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。</span><span class="sxs-lookup"><span data-stu-id="dcc68-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="dcc68-109">整数リテラルが `UShort` の範囲外にある場合 (つまり、<xref:System.UInt16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="dcc68-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="dcc68-110">次の例では、整数と等しい 16 進数、10 進数として表される 65,034 およびに割り当てられているバイナリ リテラル`UShort`値。</span><span class="sxs-lookup"><span data-stu-id="dcc68-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="dcc68-111">プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="dcc68-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="dcc68-112">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="dcc68-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="dcc68-113">Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。</span><span class="sxs-lookup"><span data-stu-id="dcc68-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="dcc68-114">Visual Basic 15.5 から始めて、使用することできますも、アンダー スコア文字 (`_`) のプレフィックスと 16 進数、バイナリ、または 8 進数の数字間に先行する区切り記号として。</span><span class="sxs-lookup"><span data-stu-id="dcc68-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="dcc68-115">例えば:</span><span class="sxs-lookup"><span data-stu-id="dcc68-115">For example:</span></span>

```vb
Dim number As UShort = &H_FF8C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="dcc68-116">数値リテラルを含めることも、`US`または`us`[文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`UShort`データ型は、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="dcc68-116">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H_5826us
```

## <a name="programming-tips"></a><span data-ttu-id="dcc68-117">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="dcc68-117">Programming tips</span></span>
  
-   <span data-ttu-id="dcc68-118">**負の数。**</span><span class="sxs-lookup"><span data-stu-id="dcc68-118">**Negative Numbers.**</span></span> <span data-ttu-id="dcc68-119">`UShort`符号なしの型は、負の数を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="dcc68-119">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="dcc68-120">単項マイナスを使用する場合 (`-`) 型に評価される式で演算子`UShort`、Visual Basic の式を変換する`Integer`最初。</span><span class="sxs-lookup"><span data-stu-id="dcc68-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="dcc68-121">**CLS 準拠しています。**</span><span class="sxs-lookup"><span data-stu-id="dcc68-121">**CLS Compliance.**</span></span> <span data-ttu-id="dcc68-122">`UShort`データ型がの一部、[共通言語仕様](http://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)、CLS 準拠コードがそれを使用するコンポーネントを使用できないようにします。</span><span class="sxs-lookup"><span data-stu-id="dcc68-122">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="dcc68-123">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="dcc68-123">**Widening.**</span></span> <span data-ttu-id="dcc68-124">`UShort`拡大変換後のデータ型`Integer`、 `UInteger`、 `Long`、 `ULong`、 `Decimal`、 `Single`、および`Double`です。</span><span class="sxs-lookup"><span data-stu-id="dcc68-124">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="dcc68-125">つまり、変換することができます`UShort`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。</span><span class="sxs-lookup"><span data-stu-id="dcc68-125">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="dcc68-126">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="dcc68-126">**Type Characters.**</span></span> <span data-ttu-id="dcc68-127">リテラルの型文字を付加`US`リテラルにリテラルを`UShort`データ型。</span><span class="sxs-lookup"><span data-stu-id="dcc68-127">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="dcc68-128">`UShort` 識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="dcc68-128">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="dcc68-129">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="dcc68-129">**Framework Type.**</span></span> <span data-ttu-id="dcc68-130">.NET Framework において対応する型は、<xref:System.UInt16?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="dcc68-130">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc68-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="dcc68-131">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="dcc68-132">データの種類</span><span class="sxs-lookup"><span data-stu-id="dcc68-132">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="dcc68-133">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="dcc68-133">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="dcc68-134">変換の概要</span><span class="sxs-lookup"><span data-stu-id="dcc68-134">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="dcc68-135">方法 : 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="dcc68-135">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="dcc68-136">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="dcc68-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
