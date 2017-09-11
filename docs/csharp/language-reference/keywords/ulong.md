---
title: "ulong (C# リファレンス)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
dev_langs:
- CSharp
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
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
ms.openlocfilehash: c2da253e4da7a5d6cfa71116e4fcba7816441e92
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ulong-c-reference"></a><span data-ttu-id="7e554-102">ulong (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="7e554-102">ulong (C# Reference)</span></span>

<span data-ttu-id="7e554-103">`ulong` キーワードは、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="7e554-103">The `ulong` keyword denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="7e554-104">型</span><span class="sxs-lookup"><span data-stu-id="7e554-104">Type</span></span>|<span data-ttu-id="7e554-105">範囲</span><span class="sxs-lookup"><span data-stu-id="7e554-105">Range</span></span>|<span data-ttu-id="7e554-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="7e554-106">Size</span></span>|<span data-ttu-id="7e554-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="7e554-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ulong`|<span data-ttu-id="7e554-108">0 ～ 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="7e554-108">0 to 18,446,744,073,709,551,615</span></span>|<span data-ttu-id="7e554-109">符号なし 64 ビット整数</span><span class="sxs-lookup"><span data-stu-id="7e554-109">Unsigned 64-bit integer</span></span>|<xref:System.UInt64?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="7e554-110">リテラル</span><span class="sxs-lookup"><span data-stu-id="7e554-110">Literals</span></span>  

<span data-ttu-id="7e554-111">`ulong` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="7e554-111">You can declare and initialize a `ulong` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="7e554-112">整数リテラルが `ulong` の範囲外にある場合 (つまり、<xref:System.UInt64.MinValue?displayProperty=fullName> より小さいか、<xref:System.UInt64.MaxValue?displayProperty=fullName> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7e554-112">If the integer literal is outside the range of `ulong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=fullName> or greater than <xref:System.UInt64.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span> 

<span data-ttu-id="7e554-113">次の例では、整数 7,934,076,125 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`ulong` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="7e554-113">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ulong` values.</span></span>  
  
<span data-ttu-id="7e554-114">[!code-cs[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]</span><span class="sxs-lookup"><span data-stu-id="7e554-114">[!code-cs[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="7e554-115">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="7e554-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="7e554-116">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="7e554-116">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="7e554-117">C# 7 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7e554-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="7e554-118">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span><span class="sxs-lookup"><span data-stu-id="7e554-118">[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]</span></span>  
 
 <span data-ttu-id="7e554-119">整数リテラルには、型を表すサフィックスを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="7e554-119">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="7e554-120">サフィックス `UL` または `ul` は、数値リテラルを `ulong` 値として明確に示します。</span><span class="sxs-lookup"><span data-stu-id="7e554-120">The suffix `UL` or `ul` unambiguously identifies a numeric literal as a `ulong` value.</span></span> <span data-ttu-id="7e554-121">リテラル値が <xref:System.Int64.MaxValue?displayProperty=fullName> を超える場合、`L` サフィックスは `ulong` を表します。</span><span class="sxs-lookup"><span data-stu-id="7e554-121">The `L` suffix denotes a `ulong` if the literal value exceeds <xref:System.Int64.MaxValue?displayProperty=fullName>.</span></span> <span data-ttu-id="7e554-122">また、リテラル値が <xref:System.UInt32.MaxValue?displayProperty=fullName> を超える場合、`U` または `u` サフィックスは `ulong` を表します。</span><span class="sxs-lookup"><span data-stu-id="7e554-122">And the `U` or `u` suffix denotes a `ulong` if the literal value exceeds <xref:System.UInt32.MaxValue?displayProperty=fullName>.</span></span> <span data-ttu-id="7e554-123">次の例では、`ul` サフィックスを使って long 整数を示しています。</span><span class="sxs-lookup"><span data-stu-id="7e554-123">The following example uses the `ul` suffix to denote a long integer:</span></span>
 
<span data-ttu-id="7e554-124">[!code-cs[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="7e554-124">[!code-cs[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]</span></span>

<span data-ttu-id="7e554-125">サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="7e554-125">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="7e554-126">int</span><span class="sxs-lookup"><span data-stu-id="7e554-126">int</span></span>](int.md)
2. [<span data-ttu-id="7e554-127">uint</span><span class="sxs-lookup"><span data-stu-id="7e554-127">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="7e554-128">long</span><span class="sxs-lookup"><span data-stu-id="7e554-128">long</span></span>](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a><span data-ttu-id="7e554-129">コンパイラのオーバーロード解決</span><span class="sxs-lookup"><span data-stu-id="7e554-129">Compiler overload resolution</span></span>
  
 <span data-ttu-id="7e554-130">サフィックスは、オーバーロードされたメソッドの呼び出しでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e554-130">A common use of the suffix is with calling overloaded methods.</span></span> <span data-ttu-id="7e554-131">たとえば、`ulong` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用するオーバーロードされたメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="7e554-131">Consider, for example, the following overloaded methods that use `ulong` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 <span data-ttu-id="7e554-132">サフィックスを `ulong` パラメーターと共に使用すると、正しい型が呼び出されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7e554-132">Using a suffix with the `ulong` parameter guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="7e554-133">変換</span><span class="sxs-lookup"><span data-stu-id="7e554-133">Conversions</span></span>  
 <span data-ttu-id="7e554-134">`ulong` から [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="7e554-134">There is a predefined implicit conversion from `ulong` to [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="7e554-135">`ulong` から整数型への暗黙的な変換は行われません。</span><span class="sxs-lookup"><span data-stu-id="7e554-135">There is no implicit conversion from `ulong` to any integral type.</span></span> <span data-ttu-id="7e554-136">たとえば、次の代入ステートメントは、明示的なキャストを使用しない場合、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="7e554-136">For example, the following statement will produce a compilation error without an explicit cast:</span></span>  
  
```csharp  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 <span data-ttu-id="7e554-137">[byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `ulong` への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="7e554-137">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md), or [char](../../../csharp/language-reference/keywords/char.md) to `ulong`.</span></span>  
  
 <span data-ttu-id="7e554-138">浮動小数点型から `ulong` への暗黙の型変換はありません。</span><span class="sxs-lookup"><span data-stu-id="7e554-138">Also, there is no implicit conversion from floating-point types to `ulong`.</span></span> <span data-ttu-id="7e554-139">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="7e554-139">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 <span data-ttu-id="7e554-140">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e554-140">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="7e554-141">暗黙的な数値変換規則について詳しくは、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7e554-141">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7e554-142">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="7e554-142">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e554-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e554-143">See Also</span></span>  
 <span data-ttu-id="7e554-144"><xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="7e554-144"><xref:System.UInt64></span></span>   
 <span data-ttu-id="7e554-145">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e554-145">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="7e554-146">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e554-146">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7e554-147">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e554-147">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="7e554-148">[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="7e554-148">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="7e554-149">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="7e554-149">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="7e554-150">[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="7e554-150">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="7e554-151">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="7e554-151">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

