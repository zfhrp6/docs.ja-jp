---
title: int (C# リファレンス)
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: 41ee5ecdae815eaddf8652a4873c060fb8f92bc3
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028267"
---
# <a name="int-c-reference"></a><span data-ttu-id="f2490-102">int (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f2490-102">int (C# Reference)</span></span>

<span data-ttu-id="f2490-103">`int` は、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="f2490-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="f2490-104">型</span><span class="sxs-lookup"><span data-stu-id="f2490-104">Type</span></span>|<span data-ttu-id="f2490-105">範囲</span><span class="sxs-lookup"><span data-stu-id="f2490-105">Range</span></span>|<span data-ttu-id="f2490-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="f2490-106">Size</span></span>|<span data-ttu-id="f2490-107">.NET 型</span><span class="sxs-lookup"><span data-stu-id="f2490-107">.NET type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`int`|<span data-ttu-id="f2490-108">-2,147,483,648 ～ 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="f2490-108">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="f2490-109">符号付き 32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="f2490-109">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="f2490-110">リテラル</span><span class="sxs-lookup"><span data-stu-id="f2490-110">Literals</span></span>  
 
<span data-ttu-id="f2490-111">`int` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7.0 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="f2490-111">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="f2490-112">整数リテラルが `int` の範囲外にある場合 (つまり、<xref:System.Int32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f2490-112">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="f2490-113">次の例では、整数 90,946 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`int` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="f2490-113">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="f2490-114">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="f2490-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="f2490-115">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="f2490-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="f2490-116">C# 7.0 以降では、読みやすさを強化するためにいくつかの機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="f2490-116">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="f2490-117">C# 7.0 では、桁区切り記号としてアンダースコア文字 (`_`) が使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2490-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="f2490-118">C# 7.2 では、プレフィックスの後に、`_` をバイナリまたは 16 進リテラルの桁区切り記号として使用できます。</span><span class="sxs-lookup"><span data-stu-id="f2490-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="f2490-119">10 進リテラルは先頭にアンダー スコアを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="f2490-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="f2490-120">以下にいくつか例を示します。</span><span class="sxs-lookup"><span data-stu-id="f2490-120">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="f2490-121">整数リテラルでは型を示すサフィックスを含めることもできますが、`int` 型を示すサフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="f2490-121">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="f2490-122">サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="f2490-122">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="f2490-123">uint</span><span class="sxs-lookup"><span data-stu-id="f2490-123">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="f2490-124">long</span><span class="sxs-lookup"><span data-stu-id="f2490-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="f2490-125">ulong</span><span class="sxs-lookup"><span data-stu-id="f2490-125">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="f2490-126">ここで示した例では、リテラル 90946 は `int` 型になります。</span><span class="sxs-lookup"><span data-stu-id="f2490-126">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="f2490-127">変換</span><span class="sxs-lookup"><span data-stu-id="f2490-127">Conversions</span></span>  
 <span data-ttu-id="f2490-128">`int` から [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="f2490-128">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="f2490-129">例:</span><span class="sxs-lookup"><span data-stu-id="f2490-129">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="f2490-130">[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[char](../../../csharp/language-reference/keywords/char.md) から `int` への、定義済みの暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="f2490-130">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="f2490-131">たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="f2490-131">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="f2490-132">浮動小数点型から `int` への暗黙的な変換が行われないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="f2490-132">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="f2490-133">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="f2490-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="f2490-134">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f2490-134">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f2490-135">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f2490-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2490-136">参照</span><span class="sxs-lookup"><span data-stu-id="f2490-136">See Also</span></span>  
 <xref:System.Int32>  
 [<span data-ttu-id="f2490-137">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f2490-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f2490-138">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f2490-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f2490-139">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="f2490-139">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f2490-140">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="f2490-140">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="f2490-141">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="f2490-141">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="f2490-142">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="f2490-142">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="f2490-143">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="f2490-143">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
