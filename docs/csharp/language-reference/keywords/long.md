---
title: long (C# リファレンス)
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4f11c904aadc5cd27482072e9f6f97236c0cdce2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="long-c-reference"></a><span data-ttu-id="bd7ec-102">long (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="bd7ec-102">long (C# Reference)</span></span>

<span data-ttu-id="bd7ec-103">`long` は、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-103">`long` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="bd7ec-104">型</span><span class="sxs-lookup"><span data-stu-id="bd7ec-104">Type</span></span>|<span data-ttu-id="bd7ec-105">範囲</span><span class="sxs-lookup"><span data-stu-id="bd7ec-105">Range</span></span>|<span data-ttu-id="bd7ec-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="bd7ec-106">Size</span></span>|<span data-ttu-id="bd7ec-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="bd7ec-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`long`|<span data-ttu-id="bd7ec-108">-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="bd7ec-108">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|<span data-ttu-id="bd7ec-109">符号付き 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="bd7ec-109">Signed 64-bit integer</span></span>|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="bd7ec-110">リテラル</span><span class="sxs-lookup"><span data-stu-id="bd7ec-110">Literals</span></span> 

<span data-ttu-id="bd7ec-111">`long` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7.0 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-111">You can declare and initialize a `long` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> 

<span data-ttu-id="bd7ec-112">次の例では、整数 4,294,967,296 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`long` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-112">In the following example, integers equal to 4,294,967,296 that are represented as decimal, hexadecimal, and binary literals are assigned to `long` values.</span></span>  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> <span data-ttu-id="bd7ec-113">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-113">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="bd7ec-114">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-114">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="bd7ec-115">C# 7.0 以降では、読みやすさを強化するためにいくつかの機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-115">Starting with C# 7.0, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="bd7ec-116">C# 7.0 では、桁区切り記号としてアンダースコア文字 (`_`) が使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-116">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="bd7ec-117">C# 7.2 では、プレフィックスの後に、`_` をバイナリまたは 16 進リテラルの桁区切り記号として使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-117">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="bd7ec-118">10 進リテラルは先頭にアンダー スコアを持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-118">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="bd7ec-119">以下にいくつか例を示します。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-119">Some examples are shown below.</span></span>

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 <span data-ttu-id="bd7ec-120">整数リテラルには、型を表すサフィックスを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-120">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="bd7ec-121">サフィックス `L` は `long` を表します。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-121">The suffix `L` denotes a `long`.</span></span> <span data-ttu-id="bd7ec-122">次の例では、`L` サフィックスを使って long 整数を示しています。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-122">The following example uses the `L` suffix to denote a long integer:</span></span>
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  <span data-ttu-id="bd7ec-123">小文字の "l" もサフィックスとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-123">You can also use the lowercase letter "l" as a suffix.</span></span> <span data-ttu-id="bd7ec-124">ただし、文字の "l" は数字の "1" と混同しやすいため、コンパイラから警告が出されます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-124">However, this generates a compiler warning because the letter "l" is easily confused with the digit "1."</span></span> <span data-ttu-id="bd7ec-125">明確にするには、"L" を使用します。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-125">Use "L" for clarity.</span></span>  
  
 <span data-ttu-id="bd7ec-126">サフィックス `L` を使う場合、整数リテラルの型は、そのサイズに応じて `long` または [ulong](../../../csharp/language-reference/keywords/ulong.md) のいずれかに決まります。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-126">When you use the suffix `L`, the type of the literal integer is determined to be either `long` or [ulong](../../../csharp/language-reference/keywords/ulong.md), depending on its size.</span></span> <span data-ttu-id="bd7ec-127">この場合、整数リテラルが [ulong](../../../csharp/language-reference/keywords/ulong.md) の範囲より小さいため、`long` になります。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-127">In this case, it is `long` because it less than the range of [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="bd7ec-128">サフィックスは、オーバーロードされたメソッドの呼び出しによく使われます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-128">A common use of the suffix is to call overloaded methods.</span></span> <span data-ttu-id="bd7ec-129">たとえば、次のオーバーロードされたメソッドには、`long` 型と [int](../../../csharp/language-reference/keywords/int.md) 型のパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-129">For example, the following overloaded methods have parameters of type `long` and [int](../../../csharp/language-reference/keywords/int.md):</span></span>  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 <span data-ttu-id="bd7ec-130">`L` サフィックスにより、適切なオーバーロードが呼び出されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-130">The `L` suffix guarantees that the correct overload is called:</span></span>  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
<span data-ttu-id="bd7ec-131">サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-131">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="bd7ec-132">int</span><span class="sxs-lookup"><span data-stu-id="bd7ec-132">int</span></span>](int.md)
2. [<span data-ttu-id="bd7ec-133">uint</span><span class="sxs-lookup"><span data-stu-id="bd7ec-133">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [<span data-ttu-id="bd7ec-134">ulong</span><span class="sxs-lookup"><span data-stu-id="bd7ec-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 

<span data-ttu-id="bd7ec-135">前の例のリテラル 4294967296 は、[uint](../../../csharp/language-reference/keywords/uint.md) の範囲を超えているため、`long` 型になります (整数型の記憶サイズについては、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-135">The literal 4294967296 in the previous examples is of type `long`, because it exceeds the range of [uint](../../../csharp/language-reference/keywords/uint.md) (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span>  
  
 <span data-ttu-id="bd7ec-136">同じ式の他の整数型で `long` 型を使うと、式は `long` (関係式またはブール式の場合は [bool](../../../csharp/language-reference/keywords/bool.md)) として評価されます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-136">If you use the `long` type with other integral types in the same expression, the expression is evaluated as `long` (or [bool](../../../csharp/language-reference/keywords/bool.md) in the case of relational or Boolean expressions).</span></span> <span data-ttu-id="bd7ec-137">たとえば、次の式は `long` として評価されます。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-137">For example, the following expression evaluates as `long`:</span></span>  
  
```csharp  
898L + 88  
```  
  
 <span data-ttu-id="bd7ec-138">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-138">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="bd7ec-139">変換</span><span class="sxs-lookup"><span data-stu-id="bd7ec-139">Conversions</span></span>  
 <span data-ttu-id="bd7ec-140">`long` から [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-140">There is a predefined implicit conversion from `long` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="bd7ec-141">それ以外の型の場合は、キャストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-141">Otherwise a cast must be used.</span></span> <span data-ttu-id="bd7ec-142">たとえば、次の代入ステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-142">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 <span data-ttu-id="bd7ec-143">[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[char](../../../csharp/language-reference/keywords/char.md) から `long` への暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-143">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `long`.</span></span>  
  
 <span data-ttu-id="bd7ec-144">また、浮動小数点型から `long` への暗黙の型変換が行われないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-144">Notice also that there is no implicit conversion from floating-point types to `long`.</span></span> <span data-ttu-id="bd7ec-145">たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="bd7ec-145">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="bd7ec-146">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="bd7ec-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bd7ec-147">参照</span><span class="sxs-lookup"><span data-stu-id="bd7ec-147">See Also</span></span>  
 <xref:System.Int64>  
 [<span data-ttu-id="bd7ec-148">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="bd7ec-148">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bd7ec-149">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="bd7ec-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bd7ec-150">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="bd7ec-150">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="bd7ec-151">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="bd7ec-151">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="bd7ec-152">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="bd7ec-152">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="bd7ec-153">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="bd7ec-153">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="bd7ec-154">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="bd7ec-154">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
