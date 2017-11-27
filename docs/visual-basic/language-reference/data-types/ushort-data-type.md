---
title: "UShort 型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ushort
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 513e8ce4694788d33c5aa14e34b95e88b6d37ff1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-data-type-visual-basic"></a><span data-ttu-id="cbe66-102">UShort データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbe66-102">UShort data type (Visual Basic)</span></span>

<span data-ttu-id="cbe66-103">保持符号なし 16 ビット (2 バイト) 整数値 0 から 65,535 までの範囲です。</span><span class="sxs-lookup"><span data-stu-id="cbe66-103">Holds unsigned 16-bit (2-byte) integers ranging in value from 0 through 65,535.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbe66-104">コメント</span><span class="sxs-lookup"><span data-stu-id="cbe66-104">Remarks</span></span>

 <span data-ttu-id="cbe66-105">使用して、`UShort`に対して大きすぎますバイナリ データを格納するデータ型`Byte`です。</span><span class="sxs-lookup"><span data-stu-id="cbe66-105">Use the `UShort` data type to contain binary data too large for `Byte`.</span></span>  
  
 <span data-ttu-id="cbe66-106">`UShort` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="cbe66-106">The default value of `UShort` is 0.</span></span>  

# <a name="literal-assignments"></a><span data-ttu-id="cbe66-107">リテラルの割り当て</span><span class="sxs-lookup"><span data-stu-id="cbe66-107">Literal assignments</span></span>

<span data-ttu-id="cbe66-108">宣言して初期化することができます、`UShort`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。</span><span class="sxs-lookup"><span data-stu-id="cbe66-108">You can declare and initialize a `UShort` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="cbe66-109">整数リテラルが `UShort` の範囲外にある場合 (つまり、<xref:System.UInt16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="cbe66-109">If the integer literal is outside the range of `UShort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="cbe66-110">次の例では、整数と等しい 16 進数、10 進数として表される 65,034 およびに割り当てられているバイナリ リテラル`UShort`値。</span><span class="sxs-lookup"><span data-stu-id="cbe66-110">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are assigned to `UShort` values.</span></span>
  
[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShort)]

> [!NOTE]
> <span data-ttu-id="cbe66-111">プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="cbe66-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="cbe66-112">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="cbe66-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="cbe66-113">Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。</span><span class="sxs-lookup"><span data-stu-id="cbe66-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UShort](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UShortS)]

<span data-ttu-id="cbe66-114">数値リテラルを含めることも、`US`または`us`[文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`UShort`データ型は、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="cbe66-114">Numeric literals can also include the `US` or `us` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UShort` data type, as the following example shows.</span></span>

```vb
Dim number = &H035826us
```

## <a name="programming-tips"></a><span data-ttu-id="cbe66-115">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="cbe66-115">Programming tips</span></span>
  
-   <span data-ttu-id="cbe66-116">**負の数。**</span><span class="sxs-lookup"><span data-stu-id="cbe66-116">**Negative Numbers.**</span></span> <span data-ttu-id="cbe66-117">`UShort`符号なしの型は、負の数を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="cbe66-117">Because `UShort` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="cbe66-118">単項マイナスを使用する場合 (`-`) 型に評価される式で演算子`UShort`、Visual Basic の式を変換する`Integer`最初。</span><span class="sxs-lookup"><span data-stu-id="cbe66-118">If you use the unary minus (`-`) operator on an expression that evaluates to type `UShort`, Visual Basic converts the expression to `Integer` first.</span></span>  
  
-   <span data-ttu-id="cbe66-119">**CLS 準拠しています。**</span><span class="sxs-lookup"><span data-stu-id="cbe66-119">**CLS Compliance.**</span></span> <span data-ttu-id="cbe66-120">`UShort`データ型がの一部、[共通言語仕様](http://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)、CLS 準拠コードがそれを使用するコンポーネントを使用できないようにします。</span><span class="sxs-lookup"><span data-stu-id="cbe66-120">The `UShort` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="cbe66-121">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="cbe66-121">**Widening.**</span></span> <span data-ttu-id="cbe66-122">`UShort`拡大変換後のデータ型`Integer`、 `UInteger`、 `Long`、 `ULong`、 `Decimal`、 `Single`、および`Double`です。</span><span class="sxs-lookup"><span data-stu-id="cbe66-122">The `UShort` data type widens to `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="cbe66-123">つまり、変換することができます`UShort`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。</span><span class="sxs-lookup"><span data-stu-id="cbe66-123">This means you can convert `UShort` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="cbe66-124">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="cbe66-124">**Type Characters.**</span></span> <span data-ttu-id="cbe66-125">リテラルの型文字を付加`US`リテラルにリテラルを`UShort`データ型。</span><span class="sxs-lookup"><span data-stu-id="cbe66-125">Appending the literal type characters `US` to a literal forces it to the `UShort` data type.</span></span> <span data-ttu-id="cbe66-126">`UShort`識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="cbe66-126">`UShort` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="cbe66-127">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="cbe66-127">**Framework Type.**</span></span> <span data-ttu-id="cbe66-128">.NET Framework において対応する型は、<xref:System.UInt16?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="cbe66-128">The corresponding type in the .NET Framework is the <xref:System.UInt16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbe66-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="cbe66-129">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="cbe66-130">データの種類</span><span class="sxs-lookup"><span data-stu-id="cbe66-130">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="cbe66-131">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="cbe66-131">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="cbe66-132">変換の概要</span><span class="sxs-lookup"><span data-stu-id="cbe66-132">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="cbe66-133">方法 : 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="cbe66-133">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="cbe66-134">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="cbe66-134">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
