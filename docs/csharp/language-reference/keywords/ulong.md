---
title: "ulong (C# リファレンス)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords: ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2058d9f6a228b13938fe08d7e2fb11e3b9f4600a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ulong-c-reference"></a><span data-ttu-id="117f4-102">ulong (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="117f4-102">ulong (C# Reference)</span></span>

<span data-ttu-id="117f4-103">`ulong` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="117f4-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="117f4-104">型</span><span class="sxs-lookup"><span data-stu-id="117f4-104">Type</span></span>|<span data-ttu-id="117f4-105">範囲</span><span class="sxs-lookup"><span data-stu-id="117f4-105">Range</span></span>|<span data-ttu-id="117f4-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="117f4-106">Size</span></span>|<span data-ttu-id="117f4-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="117f4-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ulong`|<span data-ttu-id="117f4-108">0 ～ 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="117f4-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="117f4-109">符号なし 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="117f4-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="117f4-110">リテラル</span><span class="sxs-lookup"><span data-stu-id="117f4-110">Literals</span></span>  

<span data-ttu-id="117f4-111">`ulong` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="117f4-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="117f4-112">整数リテラルが `ulong` の範囲外にある場合 (つまり、<xref:System.UInt64.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt64.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="117f4-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span> 

<span data-ttu-id="117f4-113">次の例では、整数 7,934,076,125 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`ulong` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="117f4-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>  
  
[!code-csharp[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]  

> [!NOTE] 
> <span data-ttu-id="117f4-114">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="117f4-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="117f4-115">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="117f4-115">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="117f4-116">以降で c# 7、いくつかの機能が追加されて読みやすさを強化するためにします。</span><span class="sxs-lookup"><span data-stu-id="117f4-116">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="117f4-117">C# 7.0 により、アンダー スコア文字の使用法`_`、桁区切り記号として。</span><span class="sxs-lookup"><span data-stu-id="117f4-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="117f4-118">により、c# 7.2`_`プレフィックスの後に、バイナリまたは 16 進数リテラルの桁区切り記号として使用します。</span><span class="sxs-lookup"><span data-stu-id="117f4-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="117f4-119">10 進数のリテラルはない、先頭にアンダー スコアを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="117f4-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="117f4-120">いくつかの例は、以下に示します。</span><span class="sxs-lookup"><span data-stu-id="117f4-120">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="117f4-121">整数リテラルには、型を表すサフィックスを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="117f4-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="117f4-122">サフィックス `UL` または `ul` は、数値リテラルを `ulong` 値として明確に示します。</span><span class="sxs-lookup"><span data-stu-id="117f4-122">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="117f4-123">リテラル値が <xref:System.Int64.MaxValue?displayProperty=nameWithType> を超える場合、`L` サフィックスは `ulong` を表します。</span><span class="sxs-lookup"><span data-stu-id="117f4-123">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="117f4-124">また、リテラル値が <xref:System.UInt32.MaxValue?displayProperty=nameWithType> を超える場合、`U` または `u` サフィックスは `ulong` を表します。</span><span class="sxs-lookup"><span data-stu-id="117f4-124">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.</span></span> <span data-ttu-id="117f4-125">次の例では、`ul` サフィックスを使って long 整数を示しています。</span><span class="sxs-lookup"><span data-stu-id="117f4-125">The following example uses the `ul` suffix to denote a long integer:</span></span>
 
[!code-csharp[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

<span data-ttu-id="117f4-126">サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="117f4-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="117f4-127">int</span><span class="sxs-lookup"><span data-stu-id="117f4-127">int</span></span>](int.md)
2. [<span data-ttu-id="117f4-128">uint</span><span class="sxs-lookup"><span data-stu-id="117f4-128">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="117f4-129">long</span><span class="sxs-lookup"><span data-stu-id="117f4-129">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="117f4-130">コンパイラのオーバーロード解決</span><span class="sxs-lookup"><span data-stu-id="117f4-130">Compiler overload resolution</span></span>
  
 <span data-ttu-id="117f4-131">サフィックスは、オーバーロードされたメソッドの呼び出しでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="117f4-131">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="117f4-132">たとえば、`ulong` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用するオーバーロードされたメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="117f4-132">Consider, for example, the following overloaded methods that use `ulong` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 <span data-ttu-id="117f4-133">サフィックスを `ulong` パラメーターと共に使用すると、正しい型が呼び出されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="117f4-133">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="117f4-134">変換</span><span class="sxs-lookup"><span data-stu-id="117f4-134">Conversions</span></span>  
 <span data-ttu-id="117f4-135">`ulong` から [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="117f4-135">There is a predefined implicit conversion from `ulong` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="117f4-136">`ulong` から整数型への暗黙的な変換は行われません。</span><span class="sxs-lookup"><span data-stu-id="117f4-136">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="117f4-137">たとえば、次の代入ステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="117f4-137">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 <span data-ttu-id="117f4-138">[byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `ulong` への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="117f4-138">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `ulong`.</span></span>  
  
 <span data-ttu-id="117f4-139">浮動小数点型から `ulong` への暗黙の型変換はありません。</span><span class="sxs-lookup"><span data-stu-id="117f4-139">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="117f4-140">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="117f4-140">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 <span data-ttu-id="117f4-141">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="117f4-141">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="117f4-142">暗黙的な数値変換規則について詳しくは、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="117f4-142">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="117f4-143">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="117f4-143">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="117f4-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="117f4-144">See Also</span></span>  
 <xref:System.UInt64>  
 [<span data-ttu-id="117f4-145">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="117f4-145">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="117f4-146">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="117f4-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="117f4-147">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="117f4-147">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="117f4-148">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="117f4-148">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="117f4-149">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="117f4-149">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="117f4-150">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="117f4-150">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="117f4-151">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="117f4-151">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
