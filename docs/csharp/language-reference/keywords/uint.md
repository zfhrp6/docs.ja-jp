---
title: "uint (C# リファレンス)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 18
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
ms.openlocfilehash: 4342c08ab536f45a2e3b5fa6fe94839436600a4a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="uint-c-reference"></a><span data-ttu-id="63893-102">uint (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="63893-102">uint (C# Reference)</span></span>

<span data-ttu-id="63893-103">`uint` キーワードは、次の表に示すサイズと範囲で値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="63893-103">The `uint` keyword signifies an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="63893-104">型</span><span class="sxs-lookup"><span data-stu-id="63893-104">Type</span></span>|<span data-ttu-id="63893-105">範囲</span><span class="sxs-lookup"><span data-stu-id="63893-105">Range</span></span>|<span data-ttu-id="63893-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="63893-106">Size</span></span>|<span data-ttu-id="63893-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="63893-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`uint`|<span data-ttu-id="63893-108">0 ～ 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="63893-108">0 to 4,294,967,295</span></span>|<span data-ttu-id="63893-109">符号なし 32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="63893-109">Unsigned 32-bit integer</span></span>|<xref:System.UInt32?displayProperty=fullName>|  
  
 <span data-ttu-id="63893-110">**メモ** `uint` 型は CLS に準拠していません。</span><span class="sxs-lookup"><span data-stu-id="63893-110">**Note** The `uint` type is not CLS-compliant.</span></span> <span data-ttu-id="63893-111">可能な場合は、`int` を使用します。</span><span class="sxs-lookup"><span data-stu-id="63893-111">Use `int` whenever possible.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="63893-112">リテラル</span><span class="sxs-lookup"><span data-stu-id="63893-112">Literals</span></span>  

<span data-ttu-id="63893-113">`uint` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="63893-113">You can declare and initialize a `uint` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="63893-114">整数リテラルが `uint` の範囲外にある場合 (つまり、<xref:System.UInt32.MinValue?displayProperty=fullName> より小さいか、<xref:System.UInt32.MaxValue?displayProperty=fullName> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="63893-114">If the integer literal is outside the range of `uint` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=fullName> or greater than <xref:System.UInt32.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span>

<span data-ttu-id="63893-115">次の例では、整数 3,000,000,000 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`uint` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="63893-115">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `uint` values.</span></span>  
  
<span data-ttu-id="63893-116">[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]</span><span class="sxs-lookup"><span data-stu-id="63893-116">[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="63893-117">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="63893-117">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="63893-118">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="63893-118">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="63893-119">C# 7 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="63893-119">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="63893-120">[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]</span><span class="sxs-lookup"><span data-stu-id="63893-120">[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]</span></span>  
 
 <span data-ttu-id="63893-121">整数リテラルには、型を表すサフィックスを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="63893-121">Integer literals can also include a suffix that denotes the type.</span></span> <span data-ttu-id="63893-122">サフィックス `U` または 'u' は、リテラルの数値に応じて `uint` または `ulong` を示します。</span><span class="sxs-lookup"><span data-stu-id="63893-122">The suffix `U` or 'u' denotes either a `uint` or a `ulong`, depending on the numeric value of the literal.</span></span> <span data-ttu-id="63893-123">次の例では、`u` サフィックスを使って、両方の型の符号なし整数を示しています。</span><span class="sxs-lookup"><span data-stu-id="63893-123">The following example uses the `u` suffix to denote an unsigned integer of both types.</span></span> <span data-ttu-id="63893-124">最初のリテラルは値が <xref:System.UInt32.MaxValue?displayProperty=fullName> より小さいため、`uint` であるのに対し、2 番目は値が <xref:System.UInt32.MaxValue?displayProperty=fullName> より大きいため、`ulong` であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="63893-124">Note that the first literal is a `uint` because its value is less than <xref:System.UInt32.MaxValue?displayProperty=fullName>, while the second is a `ulong` because its value is greater than <xref:System.UInt32.MaxValue?displayProperty=fullName>.</span></span>

<span data-ttu-id="63893-125">[!code-cs[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="63893-125">[!code-cs[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]</span></span>  
 
<span data-ttu-id="63893-126">サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="63893-126">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. [<span data-ttu-id="63893-127">int</span><span class="sxs-lookup"><span data-stu-id="63893-127">int</span></span>](int.md)
2. `uint`
3. [<span data-ttu-id="63893-128">long</span><span class="sxs-lookup"><span data-stu-id="63893-128">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="63893-129">ulong</span><span class="sxs-lookup"><span data-stu-id="63893-129">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a><span data-ttu-id="63893-130">変換</span><span class="sxs-lookup"><span data-stu-id="63893-130">Conversions</span></span>  
 <span data-ttu-id="63893-131">`uint` から [long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="63893-131">There is a predefined implicit conversion from `uint` to [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="63893-132">例:</span><span class="sxs-lookup"><span data-stu-id="63893-132">For example:</span></span>  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 <span data-ttu-id="63893-133">[byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、または [char](../../../csharp/language-reference/keywords/char.md) から `uint` への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="63893-133">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `uint`.</span></span> <span data-ttu-id="63893-134">それ以外の場合は、キャストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63893-134">Otherwise you must use a cast.</span></span> <span data-ttu-id="63893-135">たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="63893-135">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 <span data-ttu-id="63893-136">浮動小数点型から `uint` への暗黙的な変換が行われないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="63893-136">Notice also that there is no implicit conversion from floating-point types to `uint`.</span></span> <span data-ttu-id="63893-137">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="63893-137">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 <span data-ttu-id="63893-138">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」および「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63893-138">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="63893-139">暗黙的な数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63893-139">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="63893-140">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="63893-140">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="63893-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="63893-141">See Also</span></span>  
 <span data-ttu-id="63893-142"><xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="63893-142"><xref:System.UInt32></span></span>   
 <span data-ttu-id="63893-143">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="63893-143">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="63893-144">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="63893-144">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="63893-145">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="63893-145">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="63893-146">[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="63893-146">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="63893-147">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="63893-147">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="63893-148">[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="63893-148">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="63893-149">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="63893-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

