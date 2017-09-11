---
title: "ushort (C# リファレンス)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ushort
- ushort_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
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
ms.openlocfilehash: 2b067a2ffd0fbffe06dc5c9f2a9910c9563eec4b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ushort-c-reference"></a><span data-ttu-id="054bb-102">ushort (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="054bb-102">ushort (C# Reference)</span></span>

<span data-ttu-id="054bb-103">`ushort` キーワードは、次の表に示すサイズと範囲で値を格納する整数データ型を示します。</span><span class="sxs-lookup"><span data-stu-id="054bb-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="054bb-104">型</span><span class="sxs-lookup"><span data-stu-id="054bb-104">Type</span></span>|<span data-ttu-id="054bb-105">範囲</span><span class="sxs-lookup"><span data-stu-id="054bb-105">Range</span></span>|<span data-ttu-id="054bb-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="054bb-106">Size</span></span>|<span data-ttu-id="054bb-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="054bb-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ushort`|<span data-ttu-id="054bb-108">0 ～ 65,535</span><span class="sxs-lookup"><span data-stu-id="054bb-108">0 to 65,535</span></span>|<span data-ttu-id="054bb-109">符号なし 16 ビット整数</span><span class="sxs-lookup"><span data-stu-id="054bb-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="054bb-110">リテラル</span><span class="sxs-lookup"><span data-stu-id="054bb-110">Literals</span></span>  

<span data-ttu-id="054bb-111">`ushort` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="054bb-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="054bb-112">整数リテラルが `ushort` の範囲外にある場合 (つまり、<xref:System.UInt16.MinValue?displayProperty=fullName> より小さいか、<xref:System.UInt16.MaxValue?displayProperty=fullName> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="054bb-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=fullName> or greater than <xref:System.UInt16.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span>

<span data-ttu-id="054bb-113">次の例では、整数 65,034 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[int](../../../csharp/language-reference/keywords/int.md) から `ushort` 値に暗黙的に変換されています。</span><span class="sxs-lookup"><span data-stu-id="054bb-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `ushort` values.</span></span>    
  
<span data-ttu-id="054bb-114">[!code-cs[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]</span><span class="sxs-lookup"><span data-stu-id="054bb-114">[!code-cs[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="054bb-115">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="054bb-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="054bb-116">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="054bb-116">Decimal literals have no prefix.</span></span>

<span data-ttu-id="054bb-117">C# 7 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="054bb-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="054bb-118">[!code-cs[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]</span><span class="sxs-lookup"><span data-stu-id="054bb-118">[!code-cs[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]</span></span>  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="054bb-119">コンパイラのオーバーロード解決</span><span class="sxs-lookup"><span data-stu-id="054bb-119">Compiler overload resolution</span></span>
  
 <span data-ttu-id="054bb-120">オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="054bb-120">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="054bb-121">たとえば、`ushort` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用するオーバーロードされたメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="054bb-121">Consider, for example, the following overloaded methods that use `ushort` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 <span data-ttu-id="054bb-122">`ushort` キャストを使用すると、正しい型が呼び出されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="054bb-122">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a><span data-ttu-id="054bb-123">変換</span><span class="sxs-lookup"><span data-stu-id="054bb-123">Conversions</span></span>  
 <span data-ttu-id="054bb-124">`ushort` から [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="054bb-124">There is a predefined implicit conversion from `ushort` to [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="054bb-125">[byte](../../../csharp/language-reference/keywords/byte.md) または [char](../../../csharp/language-reference/keywords/char.md) から `ushort` への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="054bb-125">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md) or [char](../../../csharp/language-reference/keywords/char.md) to `ushort`.</span></span> <span data-ttu-id="054bb-126">それ以外の場合は、キャストを使用して明示的な変換を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="054bb-126">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="054bb-127">たとえば、2 つの `ushort` 変数 `x` と `y` があるとします。</span><span class="sxs-lookup"><span data-stu-id="054bb-127">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 <span data-ttu-id="054bb-128">次の代入ステートメントは、代入演算子の右側にある算術式が既定で `int` に評価されるため、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="054bb-128">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 <span data-ttu-id="054bb-129">この問題を解決するには、キャストを使用します。</span><span class="sxs-lookup"><span data-stu-id="054bb-129">To fix this problem, use a cast:</span></span>  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 <span data-ttu-id="054bb-130">ただし、次のステートメントは使用できます。このステートメントでは、変換先の変数の記憶領域サイズは元のサイズ以上になります。</span><span class="sxs-lookup"><span data-stu-id="054bb-130">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="054bb-131">浮動小数点型から `ushort` への暗黙的な変換が行われないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="054bb-131">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="054bb-132">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="054bb-132">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 <span data-ttu-id="054bb-133">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」および「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="054bb-133">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="054bb-134">暗黙的な数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="054bb-134">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="054bb-135">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="054bb-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="054bb-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="054bb-136">See Also</span></span>  
 <span data-ttu-id="054bb-137"><xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="054bb-137"><xref:System.UInt16></span></span>   
 <span data-ttu-id="054bb-138">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="054bb-138">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="054bb-139">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="054bb-139">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="054bb-140">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="054bb-140">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="054bb-141">[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="054bb-141">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="054bb-142">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="054bb-142">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="054bb-143">[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="054bb-143">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="054bb-144">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="054bb-144">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

