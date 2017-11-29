---
title: "バイト型 (Byte) (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6475ff3ed905abb022a9ef60204c04b45130ae22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="byte-data-type-visual-basic"></a><span data-ttu-id="2cb37-102">Byte データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cb37-102">Byte data type (Visual Basic)</span></span>
<span data-ttu-id="2cb37-103">0 から 255 までの範囲の 8 ビット (1 バイト) の符号なし整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="2cb37-103">Holds unsigned 8-bit (1-byte) integers that range in value from 0 through 255.</span></span>

## <a name="remarks"></a><span data-ttu-id="2cb37-104">コメント</span><span class="sxs-lookup"><span data-stu-id="2cb37-104">Remarks</span></span>

<span data-ttu-id="2cb37-105">使用して、`Byte`バイナリ データを格納するデータ型。</span><span class="sxs-lookup"><span data-stu-id="2cb37-105">Use the `Byte` data type to contain binary data.</span></span>  
  
<span data-ttu-id="2cb37-106">`Byte` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="2cb37-106">The default value of `Byte` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="2cb37-107">リテラルの割り当て</span><span class="sxs-lookup"><span data-stu-id="2cb37-107">Literal assignments</span></span>

<span data-ttu-id="2cb37-108">宣言して初期化することができます、`Byte`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。</span><span class="sxs-lookup"><span data-stu-id="2cb37-108">You can declare and initialize a `Byte` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="2cb37-109">整数リテラルは、範囲の場合、 `Byte` (である場合より小さい<xref:System.Byte.MinValue?displayProperty=nameWithType>以上<xref:System.Byte.MaxValue?displayProperty=nameWithType>)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="2cb37-109">If the integral literal is outside the range of a `Byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=nameWithType> or greater than <xref:System.Byte.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="2cb37-110">次の例では、整数と等しい 16 進数、10 進数として表される 201 とからバイナリ リテラルを暗黙的に変換[整数](integer-data-type.md)に`byte`値。</span><span class="sxs-lookup"><span data-stu-id="2cb37-110">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `byte` values.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> <span data-ttu-id="2cb37-111">プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="2cb37-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="2cb37-112">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="2cb37-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="2cb37-113">Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。</span><span class="sxs-lookup"><span data-stu-id="2cb37-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

## <a name="programming-tips"></a><span data-ttu-id="2cb37-114">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="2cb37-114">Programming tips</span></span>

-   <span data-ttu-id="2cb37-115">**負の数。**</span><span class="sxs-lookup"><span data-stu-id="2cb37-115">**Negative Numbers.**</span></span> <span data-ttu-id="2cb37-116">`Byte`符号なしの型は、負の数を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="2cb37-116">Because `Byte` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="2cb37-117">単項マイナスを使用する場合 (`-`) 型に評価される式で演算子`Byte`、Visual Basic の式を変換する`Short`最初。</span><span class="sxs-lookup"><span data-stu-id="2cb37-117">If you use the unary minus (`-`) operator on an expression that evaluates to type `Byte`, Visual Basic converts the expression to `Short` first.</span></span>
  
-   <span data-ttu-id="2cb37-118">**形式を変換します。**</span><span class="sxs-lookup"><span data-stu-id="2cb37-118">**Format Conversions.**</span></span> <span data-ttu-id="2cb37-119">Visual Basic の読み取りまたは書き込みをファイルまたは Dll、メソッド、およびプロパティを呼び出すとき、データ形式間で自動的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="2cb37-119">When Visual Basic reads or writes files, or when it calls DLLs, methods, and properties, it can automatically convert between data formats.</span></span> <span data-ttu-id="2cb37-120">格納されているバイナリ データ`Byte`変数および配列はこのような形式の変換中に保持されます。</span><span class="sxs-lookup"><span data-stu-id="2cb37-120">Binary data stored in `Byte` variables and arrays is preserved during such format conversions.</span></span> <span data-ttu-id="2cb37-121">使用しないで、 `String` ANSI、Unicode 形式の間で変換中にその内容が破損する可能性があるため、バイナリ データの変数です。</span><span class="sxs-lookup"><span data-stu-id="2cb37-121">You should not use a `String` variable for binary data, because its contents can be corrupted during conversion between ANSI and Unicode formats.</span></span>

-   <span data-ttu-id="2cb37-122">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="2cb37-122">**Widening.**</span></span> <span data-ttu-id="2cb37-123">`Byte`拡大変換後のデータ型`Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、 `ULong`、 `Decimal`、 `Single`、または`Double`です。</span><span class="sxs-lookup"><span data-stu-id="2cb37-123">The `Byte` data type widens to `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="2cb37-124">つまり、変換することができます`Byte`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。</span><span class="sxs-lookup"><span data-stu-id="2cb37-124">This means you can convert `Byte` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>
  
-   <span data-ttu-id="2cb37-125">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="2cb37-125">**Type Characters.**</span></span> <span data-ttu-id="2cb37-126">`Byte`リテラルの型文字または識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="2cb37-126">`Byte` has no literal type character or identifier type character.</span></span>

-   <span data-ttu-id="2cb37-127">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="2cb37-127">**Framework Type.**</span></span> <span data-ttu-id="2cb37-128">.NET Framework において対応する型は、<xref:System.Byte?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="2cb37-128">The corresponding type in the .NET Framework is the <xref:System.Byte?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="2cb37-129">例</span><span class="sxs-lookup"><span data-stu-id="2cb37-129">Example</span></span>

 <span data-ttu-id="2cb37-130">次の例では、`b`は、`Byte`変数。</span><span class="sxs-lookup"><span data-stu-id="2cb37-130">In the following example, `b` is a `Byte` variable.</span></span> <span data-ttu-id="2cb37-131">ステートメントでは、変数の範囲およびにビット シフト演算子の適用を示しています。</span><span class="sxs-lookup"><span data-stu-id="2cb37-131">The statements demonstrate the range of the variable and the application of bit-shift operators to it.</span></span>

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a><span data-ttu-id="2cb37-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cb37-132">See Also</span></span>

 <xref:System.Byte?displayProperty=nameWithType>  
 [<span data-ttu-id="2cb37-133">データの種類</span><span class="sxs-lookup"><span data-stu-id="2cb37-133">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="2cb37-134">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="2cb37-134">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="2cb37-135">変換の概要</span><span class="sxs-lookup"><span data-stu-id="2cb37-135">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="2cb37-136">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="2cb37-136">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
