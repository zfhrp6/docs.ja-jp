---
title: "uint (C# リファレンス)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords: uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d32f7146d1f9e13d8cf0f275f4fd78b693b09d31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="uint-c-reference"></a><span data-ttu-id="fd4ce-102">uint (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="fd4ce-102">uint (C# Reference)</span></span>

<span data-ttu-id="fd4ce-103">`uint` キーワードは、次の表に示すサイズと範囲で値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="fd4ce-104">型</span><span class="sxs-lookup"><span data-stu-id="fd4ce-104">Type</span></span>|<span data-ttu-id="fd4ce-105">範囲</span><span class="sxs-lookup"><span data-stu-id="fd4ce-105">Range</span></span>|<span data-ttu-id="fd4ce-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="fd4ce-106">Size</span></span>|<span data-ttu-id="fd4ce-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="fd4ce-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`uint`|<span data-ttu-id="fd4ce-108">0 ～ 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="fd4ce-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="fd4ce-109">符号なし 32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="fd4ce-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=nameWithType>|  
  
 <span data-ttu-id="fd4ce-110">**メモ** `uint` 型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="fd4ce-111">可能な場合は、`int` を使用します。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-111">Use `int` whenever possible.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="fd4ce-112">リテラル</span><span class="sxs-lookup"><span data-stu-id="fd4ce-112">Literals</span></span>  

<span data-ttu-id="fd4ce-113">`uint` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="fd4ce-114">整数リテラルが `uint` の範囲外にある場合 (つまり、<xref:System.UInt32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="fd4ce-115">次の例では、整数 3,000,000,000 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`uint` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>  
  
[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> <span data-ttu-id="fd4ce-116">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="fd4ce-117">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="fd4ce-118">以降で c# 7、いくつかの機能が追加されて読みやすさを強化するためにします。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-118">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="fd4ce-119">C# 7.0 により、アンダー スコア文字の使用法`_`、桁区切り記号として。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="fd4ce-120">により、c# 7.2`_`プレフィックスの後に、バイナリまたは 16 進数リテラルの桁区切り記号として使用します。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="fd4ce-121">10 進数のリテラルはない、先頭にアンダー スコアを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="fd4ce-122">いくつかの例は、以下に示します。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-122">Some examples are shown below.</span></span>

[!code-csharp[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 <span data-ttu-id="fd4ce-123">整数リテラルには、型を表すサフィックスを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-123">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="fd4ce-124">サフィックス `U` または 'u' は、リテラルの数値に応じて `uint` または `ulong` を示します。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-124">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="fd4ce-125">次の例では、`u` サフィックスを使って、両方の型の符号なし整数を示しています。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-125">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="fd4ce-126">最初のリテラルは値が <xref:System.UInt32.MaxValue?displayProperty=nameWithType> より小さいため、`uint` であるのに対し、2 番目は値が <xref:System.UInt32.MaxValue?displayProperty=nameWithType> より大きいため、`ulong` であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-126">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span>

[!code-csharp[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
<span data-ttu-id="fd4ce-127">サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-127">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="fd4ce-128">int</span><span class="sxs-lookup"><span data-stu-id="fd4ce-128">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="fd4ce-129">long</span><span class="sxs-lookup"><span data-stu-id="fd4ce-129">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="fd4ce-130">ulong</span><span class="sxs-lookup"><span data-stu-id="fd4ce-130">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a><span data-ttu-id="fd4ce-131">変換</span><span class="sxs-lookup"><span data-stu-id="fd4ce-131">Conversions</span></span>  
 <span data-ttu-id="fd4ce-132">`uint` から [long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-132">There is a predefined implicit conversion from `uint` to [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="fd4ce-133">例:</span><span class="sxs-lookup"><span data-stu-id="fd4ce-133">For example:</span></span>  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 <span data-ttu-id="fd4ce-134">[byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `uint` への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-134">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `uint`.</span></span> <span data-ttu-id="fd4ce-135">それ以外の場合は、キャストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-135">Otherwise you must use a cast.</span></span> <span data-ttu-id="fd4ce-136">たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-136">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 <span data-ttu-id="fd4ce-137">浮動小数点型から `uint` への暗黙的な変換が行われないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-137">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="fd4ce-138">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-138">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 <span data-ttu-id="fd4ce-139">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」および「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-139">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="fd4ce-140">暗黙的な数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd4ce-140">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fd4ce-141">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="fd4ce-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fd4ce-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd4ce-142">See Also</span></span>  
 <xref:System.UInt32>  
 [<span data-ttu-id="fd4ce-143">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="fd4ce-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fd4ce-144">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fd4ce-144">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fd4ce-145">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="fd4ce-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fd4ce-146">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="fd4ce-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="fd4ce-147">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="fd4ce-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="fd4ce-148">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="fd4ce-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="fd4ce-149">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="fd4ce-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
