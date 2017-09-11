---
title: "sbyte (C# リファレンス)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
dev_langs:
- CSharp
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 69741a5b9556c769156687584041667312550c17
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="sbyte-c-reference"></a><span data-ttu-id="8b6f7-102">sbyte (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8b6f7-102">sbyte (C# Reference)</span></span>

<span data-ttu-id="8b6f7-103">`sbyte` は、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-103">`sbyte` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="8b6f7-104">型</span><span class="sxs-lookup"><span data-stu-id="8b6f7-104">Type</span></span>|<span data-ttu-id="8b6f7-105">範囲</span><span class="sxs-lookup"><span data-stu-id="8b6f7-105">Range</span></span>|<span data-ttu-id="8b6f7-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="8b6f7-106">Size</span></span>|<span data-ttu-id="8b6f7-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="8b6f7-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|<span data-ttu-id="8b6f7-108">-128 ～ 127</span><span class="sxs-lookup"><span data-stu-id="8b6f7-108">-128 to 127</span></span>|<span data-ttu-id="8b6f7-109">符号付き 8 ビット整数</span><span class="sxs-lookup"><span data-stu-id="8b6f7-109">Signed 8-bit integer</span></span>|<xref:System.SByte?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="8b6f7-110">リテラル</span><span class="sxs-lookup"><span data-stu-id="8b6f7-110">Literals</span></span>  

<span data-ttu-id="8b6f7-111">`sbyte` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-111">You can declare and initialize an `sbyte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> 

<span data-ttu-id="8b6f7-112">次の例では、整数 -102 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[int](../../../csharp/language-reference/keywords/int.md) から `sbyte` 値に変換されています。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-112">In the following example, integers equal to -102 that are represented as decimal, hexadecimal, and binary literals are converted from [int](../../../csharp/language-reference/keywords/int.md) to `sbyte` values.</span></span>    
  
<span data-ttu-id="8b6f7-113">[!code-cs[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]</span><span class="sxs-lookup"><span data-stu-id="8b6f7-113">[!code-cs[SByte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByte)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="8b6f7-114">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="8b6f7-115">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="8b6f7-116">C# 7 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-116">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="8b6f7-117">[!code-cs[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]</span><span class="sxs-lookup"><span data-stu-id="8b6f7-117">[!code-cs[SByteSeparator](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#SByteS)]</span></span>  

<span data-ttu-id="8b6f7-118">整数リテラルが `sbyte` の範囲外にある場合 (つまり、<xref:System.SByte.MinValue?displayProperty=fullName> より小さいか、<xref:System.SByte.MaxValue?displayProperty=fullName> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-118">If the integer literal is outside the range of `sbyte` (that is, if it is less than <xref:System.SByte.MinValue?displayProperty=fullName> or greater than <xref:System.SByte.MaxValue?displayProperty=fullName>, a compilation error occurs.</span></span> <span data-ttu-id="8b6f7-119">サフィックスがない整数リテラルの場合、整数リテラルの型は、[int](int.md)、[uint](uint.md)、[long](long.md)、[ulong](ulong.md) のうち、その値を表すことができる最初の型になります。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-119">When an integer literal has no suffix, its type is the first of these types in which its value can be represented: [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md).</span></span> <span data-ttu-id="8b6f7-120">つまり、この例では、数値リテラル `0x9A` と `0b10011010` は値が 156 の 32 ビット符号付き整数として解釈され、これは <xref:System.SByte.MaxValue?displayProperty=fullName> を超えています。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-120">This means that, in this example, the numeric literals `0x9A` and `0b10011010` are interpreted as 32-bit signed integers with a value of 156, which exceeds <xref:System.SByte.MaxValue?displayProperty=fullName>.</span></span> <span data-ttu-id="8b6f7-121">このため、キャスト演算子が必要であり、割り当ては [unchecked](unchecked.md) コンテキストで行われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-121">Because of this, the casting operator is needed, and the assignment must occur in an [unchecked](unchecked.md) context.</span></span> 

## <a name="compiler-overload-resolution"></a><span data-ttu-id="8b6f7-122">コンパイラのオーバーロード解決</span><span class="sxs-lookup"><span data-stu-id="8b6f7-122">Compiler overload resolution</span></span>

 <span data-ttu-id="8b6f7-123">オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-123">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="8b6f7-124">たとえば、`sbyte` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用するオーバーロードされたメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-124">Consider, for example, the following overloaded methods that use `sbyte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 <span data-ttu-id="8b6f7-125">`sbyte` キャストを使用すると、正しい型が呼び出されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-125">Using the `sbyte` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp 
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a><span data-ttu-id="8b6f7-126">変換</span><span class="sxs-lookup"><span data-stu-id="8b6f7-126">Conversions</span></span>  
 <span data-ttu-id="8b6f7-127">`sbyte` から [short](../../../csharp/language-reference/keywords/short.md)、[int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-127">There is a predefined implicit conversion from `sbyte` to [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="8b6f7-128">記憶領域が大きなリテラル以外の数値型を暗黙的に `sbyte` に変換することはできません (整数型の記憶領域については、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-128">You cannot implicitly convert nonliteral numeric types of larger storage size to `sbyte` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="8b6f7-129">たとえば、2 つの `sbyte` 変数 `x` と `y` があるとします。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-129">Consider, for example, the following two `sbyte` variables `x` and `y`:</span></span>  
  
```csharp  
sbyte x = 10, y = 20;  
```  
  
 <span data-ttu-id="8b6f7-130">次の代入ステートメントは、代入演算子の右側にある算術式が既定で [int](../../../csharp/language-reference/keywords/int.md) に評価されるため、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 <span data-ttu-id="8b6f7-131">この問題を解決するには、次の例のように式をキャストします。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-131">To fix this problem, cast the expression as in the following example:</span></span>  
  
```csharp  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 <span data-ttu-id="8b6f7-132">ただし、次のステートメントは使用できます。このステートメントでは、変換先の変数の記憶領域サイズは元のサイズ以上になります。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="8b6f7-133">浮動小数点型から `sbyte` への暗黙的な変換が行われないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-133">Notice also that there is no implicit conversion from floating-point types to `sbyte`.</span></span> <span data-ttu-id="8b6f7-134">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 <span data-ttu-id="8b6f7-135">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」および「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="8b6f7-136">暗黙的な数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b6f7-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8b6f7-137">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="8b6f7-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b6f7-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b6f7-138">See Also</span></span>  
 <span data-ttu-id="8b6f7-139"><xref:System.SByte></span><span class="sxs-lookup"><span data-stu-id="8b6f7-139"><xref:System.SByte></span></span>   
 <span data-ttu-id="8b6f7-140">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8b6f7-140">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8b6f7-141">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8b6f7-141">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8b6f7-142">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="8b6f7-142">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="8b6f7-143">[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="8b6f7-143">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="8b6f7-144">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="8b6f7-144">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="8b6f7-145">[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="8b6f7-145">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="8b6f7-146">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="8b6f7-146">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

