---
title: "Long 型 (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Long
helpviewer_keywords:
- identifier type characters [Visual Basic], &
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- '& identifier type character'
- integer numbers
- literal type characters [Visual Basic], L
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- L literal type character [Visual Basic]
- integers [Visual Basic], types
- Long keyword [Visual Basic]
- data types [Visual Basic], integral
- data types [Visual Basic], assigning
- Long data type
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e21ed43ddc6efb018df0581faed1ebf270ab3ca
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="long-data-type-visual-basic"></a><span data-ttu-id="38de9-102">長い形式のデータ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38de9-102">Long data type (Visual Basic)</span></span>

<span data-ttu-id="38de9-103">符号付き 64 ビット (8 バイト) の整数 9,223,372,036,854,775,807 を通じて-9,223,372,036,854,775,808 から値の範囲 (9.2... E + 18) です。</span><span class="sxs-lookup"><span data-stu-id="38de9-103">Holds signed 64-bit (8-byte) integers ranging in value from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807 (9.2...E+18).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38de9-104">コメント</span><span class="sxs-lookup"><span data-stu-id="38de9-104">Remarks</span></span>

 <span data-ttu-id="38de9-105">使用して、`Long`が大きすぎてに収まるように整数値を格納するデータ型、`Integer`データ型。</span><span class="sxs-lookup"><span data-stu-id="38de9-105">Use the `Long` data type to contain integer numbers that are too large to fit in the `Integer` data type.</span></span>  
  
 <span data-ttu-id="38de9-106">`Long` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="38de9-106">The default value of `Long` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="38de9-107">リテラルの割り当て</span><span class="sxs-lookup"><span data-stu-id="38de9-107">Literal assignments</span></span> 

<span data-ttu-id="38de9-108">宣言して初期化することができます、`Long`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。</span><span class="sxs-lookup"><span data-stu-id="38de9-108">You can declare and initialize a `Long` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="38de9-109">整数リテラルが `Long` の範囲外にある場合 (つまり、<xref:System.Int64.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int64.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="38de9-109">If the integer literal is outside the range of `Long` (that is, if it is less than <xref:System.Int64.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="38de9-110">次の例では、整数 4,294,967,296 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Long` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="38de9-110">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `Long` values.</span></span>
  
[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Long)]  

> [!NOTE]
> <span data-ttu-id="38de9-111">プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。</span><span class="sxs-lookup"><span data-stu-id="38de9-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="38de9-112">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="38de9-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="38de9-113">Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。</span><span class="sxs-lookup"><span data-stu-id="38de9-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[long](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="38de9-114">数値リテラルを含めることも、 `L` [文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`Long`データ型は、次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="38de9-114">Numeric literals can also include the `L` [type character](../../programming-guide\language-features\data-types/type-characters.md) to denote the `Long` data type, as the following example shows.</span></span>

```vb
Dim number = &H0FAC0326L
```

## <a name="programming-tips"></a><span data-ttu-id="38de9-115">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="38de9-115">Programming tips</span></span>

-   <span data-ttu-id="38de9-116">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="38de9-116">**Interop Considerations.**</span></span> <span data-ttu-id="38de9-117">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合の点に注意`Long`が他の環境で別のデータ幅 (32 ビット) を持ちます。</span><span class="sxs-lookup"><span data-stu-id="38de9-117">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that `Long` has a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="38de9-118">このようなコンポーネントに 32 ビットの引数を渡す場合として宣言`Integer`の代わりに`Long`新しい Visual Basic コードでします。</span><span class="sxs-lookup"><span data-stu-id="38de9-118">If you are passing a 32-bit argument to such a component, declare it as `Integer` instead of `Long` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="38de9-119">**拡大します。**</span><span class="sxs-lookup"><span data-stu-id="38de9-119">**Widening.**</span></span> <span data-ttu-id="38de9-120">`Long`拡大変換後のデータ型`Decimal`、 `Single`、または`Double`です。</span><span class="sxs-lookup"><span data-stu-id="38de9-120">The `Long` data type widens to `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="38de9-121">これは、`Long` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="38de9-121">This means you can convert `Long` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="38de9-122">**型宣言文字。**</span><span class="sxs-lookup"><span data-stu-id="38de9-122">**Type Characters.**</span></span> <span data-ttu-id="38de9-123">あるリテラルにリテラルの型文字 `L` を付けると、そのリテラルは `Long` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="38de9-123">Appending the literal type character `L` to a literal forces it to the `Long` data type.</span></span> <span data-ttu-id="38de9-124">ある識別子に識別子の型文字 `&` を付けると、その識別子は整数型 (`Long`) に変換されます。</span><span class="sxs-lookup"><span data-stu-id="38de9-124">Appending the identifier type character `&` to any identifier forces it to `Long`.</span></span>  
  
-   <span data-ttu-id="38de9-125">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="38de9-125">**Framework Type.**</span></span> <span data-ttu-id="38de9-126">.NET Framework において対応する型は、<xref:System.Int64?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="38de9-126">The corresponding type in the .NET Framework is the <xref:System.Int64?displayProperty=nameWithType> structure.</span></span>  

## <a name="see-also"></a><span data-ttu-id="38de9-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="38de9-127">See also</span></span>

<span data-ttu-id="38de9-128"><xref:System.Int64>[データ型](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="38de9-128"><xref:System.Int64> [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="38de9-129">[整数データ型](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="38de9-129">[Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md) </span></span>  
<span data-ttu-id="38de9-130">[Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="38de9-130">[Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md) </span></span>  
<span data-ttu-id="38de9-131">[型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span><span class="sxs-lookup"><span data-stu-id="38de9-131">[Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md) </span></span>  
<span data-ttu-id="38de9-132">[変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span><span class="sxs-lookup"><span data-stu-id="38de9-132">[Conversion Summary](../../../visual-basic/language-reference/keywords/conversion-summary.md) </span></span>  
[<span data-ttu-id="38de9-133">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="38de9-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
