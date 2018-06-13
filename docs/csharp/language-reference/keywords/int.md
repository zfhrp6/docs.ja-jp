---
title: int (C# リファレンス)
ms.date: 03/14/2017
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
ms.openlocfilehash: c7d9bb0ee3d59ef3e0cf56d26e73a925fcfb4206
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275292"
---
# <a name="int-c-reference"></a><span data-ttu-id="e3ba7-102">int (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e3ba7-102">int (C# Reference)</span></span>

<span data-ttu-id="e3ba7-103">`int` は、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="e3ba7-104">型</span><span class="sxs-lookup"><span data-stu-id="e3ba7-104">Type</span></span>|<span data-ttu-id="e3ba7-105">範囲</span><span class="sxs-lookup"><span data-stu-id="e3ba7-105">Range</span></span>|<span data-ttu-id="e3ba7-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="e3ba7-106">Size</span></span>|<span data-ttu-id="e3ba7-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="e3ba7-107">.NET Framework type</span></span>|<span data-ttu-id="e3ba7-108">既定値</span><span class="sxs-lookup"><span data-stu-id="e3ba7-108">Default Value</span></span>|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|<span data-ttu-id="e3ba7-109">-2,147,483,648 ～ 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="e3ba7-109">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="e3ba7-110">符号付き 32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="e3ba7-110">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="e3ba7-111">0</span><span class="sxs-lookup"><span data-stu-id="e3ba7-111">0</span></span>|  
  
## <a name="literals"></a><span data-ttu-id="e3ba7-112">リテラル</span><span class="sxs-lookup"><span data-stu-id="e3ba7-112">Literals</span></span>  
 
<span data-ttu-id="e3ba7-113">`int` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7.0 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-113">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span>  <span data-ttu-id="e3ba7-114">整数リテラルが `int` の範囲外にある場合 (つまり、<xref:System.Int32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-114">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int32.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="e3ba7-115">次の例では、整数 90,946 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`int` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-115">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> <span data-ttu-id="e3ba7-116">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-116">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="e3ba7-117">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-117">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="e3ba7-118">C# 7.0 以降では、読みやすさを強化するためにいくつかの機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-118">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="e3ba7-119">C# 7.0 では、桁区切り記号としてアンダースコア文字 (`_`) が使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-119">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="e3ba7-120">C# 7.2 では、プレフィックスの後に、`_` をバイナリまたは 16 進リテラルの桁区切り記号として使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-120">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="e3ba7-121">10 進リテラルは先頭にアンダー スコアを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-121">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="e3ba7-122">以下にいくつか例を示します。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-122">Some examples are shown below.</span></span>

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 <span data-ttu-id="e3ba7-123">整数リテラルでは型を示すサフィックスを含めることもできますが、`int` 型を示すサフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-123">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="e3ba7-124">サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-124">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="e3ba7-125">uint</span><span class="sxs-lookup"><span data-stu-id="e3ba7-125">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="e3ba7-126">long</span><span class="sxs-lookup"><span data-stu-id="e3ba7-126">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="e3ba7-127">ulong</span><span class="sxs-lookup"><span data-stu-id="e3ba7-127">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="e3ba7-128">ここで示した例では、リテラル 90946 は `int` 型になります。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-128">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="e3ba7-129">変換</span><span class="sxs-lookup"><span data-stu-id="e3ba7-129">Conversions</span></span>  
 <span data-ttu-id="e3ba7-130">`int` から [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-130">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="e3ba7-131">例:</span><span class="sxs-lookup"><span data-stu-id="e3ba7-131">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="e3ba7-132">[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[char](../../../csharp/language-reference/keywords/char.md) から `int` への、定義済みの暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-132">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="e3ba7-133">たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-133">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="e3ba7-134">浮動小数点型から `int` への暗黙的な変換が行われないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-134">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="e3ba7-135">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-135">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="e3ba7-136">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3ba7-136">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e3ba7-137">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="e3ba7-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3ba7-138">参照</span><span class="sxs-lookup"><span data-stu-id="e3ba7-138">See Also</span></span>  
 <xref:System.Int32>  
 [<span data-ttu-id="e3ba7-139">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="e3ba7-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e3ba7-140">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e3ba7-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e3ba7-141">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="e3ba7-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e3ba7-142">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="e3ba7-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="e3ba7-143">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="e3ba7-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="e3ba7-144">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="e3ba7-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="e3ba7-145">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="e3ba7-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
