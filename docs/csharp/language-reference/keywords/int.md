---
title: "int (C# リファレンス)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
dev_langs:
- CSharp
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 19
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
ms.sourcegitcommit: 935428cc9442a3e1d15eeb8942176c237bff4e22
ms.openlocfilehash: 6e87893bcd9800b61297e71b782028fec5116479
ms.contentlocale: ja-jp
ms.lasthandoff: 08/22/2017

---
# <a name="int-c-reference"></a><span data-ttu-id="bbebd-102">int (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="bbebd-102">int (C# Reference)</span></span>

<span data-ttu-id="bbebd-103">`int` は、次の表に示されたサイズと範囲に従って値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="bbebd-103">`int` denotes an integral type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="bbebd-104">型</span><span class="sxs-lookup"><span data-stu-id="bbebd-104">Type</span></span>|<span data-ttu-id="bbebd-105">範囲</span><span class="sxs-lookup"><span data-stu-id="bbebd-105">Range</span></span>|<span data-ttu-id="bbebd-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="bbebd-106">Size</span></span>|<span data-ttu-id="bbebd-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="bbebd-107">.NET Framework type</span></span>|<span data-ttu-id="bbebd-108">既定値</span><span class="sxs-lookup"><span data-stu-id="bbebd-108">Default Value</span></span>|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|<span data-ttu-id="bbebd-109">-2,147,483,648 ～ 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="bbebd-109">-2,147,483,648 to 2,147,483,647</span></span>|<span data-ttu-id="bbebd-110">符号付き 32 ビット整数</span><span class="sxs-lookup"><span data-stu-id="bbebd-110">Signed 32-bit integer</span></span>|<xref:System.Int32?displayProperty=fullName>|<span data-ttu-id="bbebd-111">0</span><span class="sxs-lookup"><span data-stu-id="bbebd-111">0</span></span>|  
  
## <a name="literals"></a><span data-ttu-id="bbebd-112">リテラル</span><span class="sxs-lookup"><span data-stu-id="bbebd-112">Literals</span></span>  
 
<span data-ttu-id="bbebd-113">`int` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="bbebd-113">You can declare and initialize an `int` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="bbebd-114">整数リテラルが `int` の範囲外にある場合 (つまり、<xref:System.Int32.MinValue?displayProperty=fullName> より小さいか、<xref:System.Int32.MaxValue?displayProperty=fullName> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="bbebd-114">If the integer literal is outside the range of `int` (that is, if it is less than <xref:System.Int32.MinValue?displayProperty=fullName> or greater than <xref:System.Int32.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span> 

<span data-ttu-id="bbebd-115">次の例では、整数 90,946 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`int` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="bbebd-115">In the following example, integers equal to 90,946 that are represented as decimal, hexadecimal, and binary literals are assigned to `int` values.</span></span>  
  
<span data-ttu-id="bbebd-116">[!code-cs[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]</span><span class="sxs-lookup"><span data-stu-id="bbebd-116">[!code-cs[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="bbebd-117">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="bbebd-117">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="bbebd-118">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="bbebd-118">Decimal literals have no prefix.</span></span> 

<span data-ttu-id="bbebd-119">C# 7 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="bbebd-119">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="bbebd-120">[!code-cs[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]</span><span class="sxs-lookup"><span data-stu-id="bbebd-120">[!code-cs[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]</span></span>  
 
 <span data-ttu-id="bbebd-121">整数リテラルでは型を示すサフィックスを含めることもできますが、`int` 型を示すサフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="bbebd-121">Integer literals can also include a suffix that denotes the type, although there is no suffix that denotes the `int` type.</span></span> <span data-ttu-id="bbebd-122">サフィックスがない整数リテラルの型は、以下の型のうちその値を表すことができる最初のものになります。</span><span class="sxs-lookup"><span data-stu-id="bbebd-122">If an integer literal has no suffix, its type is the first of the following types in which its value can be represented:</span></span> 

1. `int`
2. [<span data-ttu-id="bbebd-123">uint</span><span class="sxs-lookup"><span data-stu-id="bbebd-123">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)
3. [<span data-ttu-id="bbebd-124">long</span><span class="sxs-lookup"><span data-stu-id="bbebd-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)
4. [<span data-ttu-id="bbebd-125">ulong</span><span class="sxs-lookup"><span data-stu-id="bbebd-125">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md) 
 
<span data-ttu-id="bbebd-126">ここで示した例では、リテラル 90946 は `int` 型になります。</span><span class="sxs-lookup"><span data-stu-id="bbebd-126">In these examples, the literal 90946 is of type `int`.</span></span>
  
## <a name="conversions"></a><span data-ttu-id="bbebd-127">変換</span><span class="sxs-lookup"><span data-stu-id="bbebd-127">Conversions</span></span>  
 <span data-ttu-id="bbebd-128">`int` から [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="bbebd-128">There is a predefined implicit conversion from `int` to [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="bbebd-129">例:</span><span class="sxs-lookup"><span data-stu-id="bbebd-129">For example:</span></span>  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 <span data-ttu-id="bbebd-130">[sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[char](../../../csharp/language-reference/keywords/char.md) から `int` への、定義済みの暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="bbebd-130">There is a predefined implicit conversion from [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), or [char](../../../csharp/language-reference/keywords/char.md) to `int`.</span></span> <span data-ttu-id="bbebd-131">たとえば、次の代入ステートメントは、キャストを使用しない場合、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="bbebd-131">For example, the following assignment statement will produce a compilation error without a cast:</span></span>  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 <span data-ttu-id="bbebd-132">浮動小数点型から `int` への暗黙的な変換が行われないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="bbebd-132">Notice also that there is no implicit conversion from floating-point types to `int`.</span></span> <span data-ttu-id="bbebd-133">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="bbebd-133">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 <span data-ttu-id="bbebd-134">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbebd-134">For more information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bbebd-135">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="bbebd-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbebd-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbebd-136">See Also</span></span>  
 <span data-ttu-id="bbebd-137"><xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="bbebd-137"><xref:System.Int32></span></span>   
 <span data-ttu-id="bbebd-138">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="bbebd-138">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="bbebd-139">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="bbebd-139">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="bbebd-140">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="bbebd-140">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="bbebd-141">[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="bbebd-141">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="bbebd-142">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="bbebd-142">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="bbebd-143">[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="bbebd-143">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="bbebd-144">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="bbebd-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

