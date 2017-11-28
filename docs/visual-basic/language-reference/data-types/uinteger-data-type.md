---
title: "UInteger 型"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f3852bd56d11c19e327e6c2f3e23cfb082a54e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="uinteger-data-type"></a><span data-ttu-id="59f72-102">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="59f72-102">UInteger data type</span></span>

<span data-ttu-id="59f72-103">保持符号なし 32 ビット (4 バイト) 0 ~ 整数 4,294,967,295 です。</span><span class="sxs-lookup"><span data-stu-id="59f72-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59f72-104">コメント</span><span class="sxs-lookup"><span data-stu-id="59f72-104">Remarks</span></span>

 <span data-ttu-id="59f72-105">`UInteger`データ型は、最も効率的なデータの幅の最大の符号なしの値を提供します。</span><span class="sxs-lookup"><span data-stu-id="59f72-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="59f72-106">`UInteger` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="59f72-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="59f72-107">リテラルの割り当て</span><span class="sxs-lookup"><span data-stu-id="59f72-107">Literal assignments</span></span>

<span data-ttu-id="59f72-108">宣言して初期化することができます、`UInteger`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。</span><span class="sxs-lookup"><span data-stu-id="59f72-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="59f72-109">整数リテラルが `UInteger` の範囲外にある場合 (つまり、<xref:System.UInt32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="59f72-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="59f72-110">次の例では、整数 3,000,000,000 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`UInteger` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="59f72-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="59f72-111">プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="59f72-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="59f72-112">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="59f72-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="59f72-113">Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。</span><span class="sxs-lookup"><span data-stu-id="59f72-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="59f72-114">数値リテラルを含めることも、`UI`または`ui`[文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`UInteger`データ型は、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="59f72-114">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H0FAC14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="59f72-115">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="59f72-115">Programming tips</span></span>

 <span data-ttu-id="59f72-116">`UInteger`と`Integer`できないために、データ型が、32 ビットのプロセッサで最適なパフォーマンスを提供小さい整数型 (`UShort`、 `Short`、 `Byte`、および`SByte`) 少量のビットを使用する場合でも、時間がかかります読み込み、格納、およびフェッチします。</span><span class="sxs-lookup"><span data-stu-id="59f72-116">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
-   <span data-ttu-id="59f72-117">**負の数。**</span><span class="sxs-lookup"><span data-stu-id="59f72-117">**Negative Numbers.**</span></span> <span data-ttu-id="59f72-118">`UInteger`符号なしの型は、負の数を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="59f72-118">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="59f72-119">単項マイナスを使用する場合 (`-`) 型に評価される式で演算子`UInteger`、Visual Basic の式を変換する`Long`最初。</span><span class="sxs-lookup"><span data-stu-id="59f72-119">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
-   <span data-ttu-id="59f72-120">**CLS 準拠しています。**</span><span class="sxs-lookup"><span data-stu-id="59f72-120">**CLS Compliance.**</span></span> <span data-ttu-id="59f72-121">`UInteger`データ型がの一部、[共通言語仕様](http://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)、CLS 準拠コードがそれを使用するコンポーネントを使用できないようにします。</span><span class="sxs-lookup"><span data-stu-id="59f72-121">The `UInteger` data type is not part of the [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
-   <span data-ttu-id="59f72-122">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="59f72-122">**Interop Considerations.**</span></span> <span data-ttu-id="59f72-123">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合などの型を注意して`uint`他の環境で別のデータ幅 (16 ビット) を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="59f72-123">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="59f72-124">このようなコンポーネントに 16 ビットの引数を渡す場合として宣言`UShort`の代わりに`UInteger`マネージ コードを Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="59f72-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
-   <span data-ttu-id="59f72-125">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="59f72-125">**Widening.**</span></span> <span data-ttu-id="59f72-126">`UInteger`拡大変換後のデータ型`Long`、 `ULong`、 `Decimal`、 `Single`、および`Double`です。</span><span class="sxs-lookup"><span data-stu-id="59f72-126">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="59f72-127">つまり、変換することができます`UInteger`影響を受けずにこれらの型のいずれかに、<xref:System.OverflowException?displayProperty=nameWithType>エラーです。</span><span class="sxs-lookup"><span data-stu-id="59f72-127">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="59f72-128">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="59f72-128">**Type Characters.**</span></span> <span data-ttu-id="59f72-129">リテラルの型文字を付加`UI`リテラルにリテラルを`UInteger`データ型。</span><span class="sxs-lookup"><span data-stu-id="59f72-129">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="59f72-130">`UInteger`識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="59f72-130">`UInteger` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="59f72-131">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="59f72-131">**Framework Type.**</span></span> <span data-ttu-id="59f72-132">.NET Framework において対応する型は、<xref:System.UInt32?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="59f72-132">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f72-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="59f72-133">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="59f72-134">データの種類</span><span class="sxs-lookup"><span data-stu-id="59f72-134">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="59f72-135">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="59f72-135">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="59f72-136">変換の概要</span><span class="sxs-lookup"><span data-stu-id="59f72-136">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="59f72-137">方法 : 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="59f72-137">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="59f72-138">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="59f72-138">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
