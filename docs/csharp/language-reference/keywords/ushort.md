---
title: "ushort (C# リファレンス)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 83fa657303e8392997b04b7d80cdbcdbf39de887
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-c-reference"></a><span data-ttu-id="39a60-102">ushort (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="39a60-102">ushort (C# Reference)</span></span>

<span data-ttu-id="39a60-103">`ushort` キーワードは、次の表に示すサイズと範囲で値を格納する整数データ型を示します。</span><span class="sxs-lookup"><span data-stu-id="39a60-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="39a60-104">型</span><span class="sxs-lookup"><span data-stu-id="39a60-104">Type</span></span>|<span data-ttu-id="39a60-105">範囲</span><span class="sxs-lookup"><span data-stu-id="39a60-105">Range</span></span>|<span data-ttu-id="39a60-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="39a60-106">Size</span></span>|<span data-ttu-id="39a60-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="39a60-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`ushort`|<span data-ttu-id="39a60-108">0 ～ 65,535</span><span class="sxs-lookup"><span data-stu-id="39a60-108">0 to 65,535</span></span>|<span data-ttu-id="39a60-109">符号なし 16 ビット整数</span><span class="sxs-lookup"><span data-stu-id="39a60-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="39a60-110">リテラル</span><span class="sxs-lookup"><span data-stu-id="39a60-110">Literals</span></span>  

<span data-ttu-id="39a60-111">`ushort` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="39a60-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="39a60-112">整数リテラルが `ushort` の範囲外にある場合 (つまり、<xref:System.UInt16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="39a60-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="39a60-113">次の例では、整数 65,034 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[int](../../../csharp/language-reference/keywords/int.md) から `ushort` 値に暗黙的に変換されています。</span><span class="sxs-lookup"><span data-stu-id="39a60-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `ushort` values.</span></span>    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> <span data-ttu-id="39a60-114">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="39a60-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="39a60-115">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="39a60-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="39a60-116">以降で c# 7、いくつかの機能が追加されて読みやすさを強化するためにします。</span><span class="sxs-lookup"><span data-stu-id="39a60-116">Starting with C# 7, a couple of features have been added to enhance readability.</span></span> 
 - <span data-ttu-id="39a60-117">C# 7.0 により、アンダー スコア文字の使用法`_`、桁区切り記号として。</span><span class="sxs-lookup"><span data-stu-id="39a60-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
 - <span data-ttu-id="39a60-118">により、c# 7.2`_`プレフィックスの後に、バイナリまたは 16 進数リテラルの桁区切り記号として使用します。</span><span class="sxs-lookup"><span data-stu-id="39a60-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="39a60-119">10 進数のリテラルはない、先頭にアンダー スコアを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="39a60-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="39a60-120">いくつかの例は、以下に示します。</span><span class="sxs-lookup"><span data-stu-id="39a60-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="39a60-121">コンパイラのオーバーロード解決</span><span class="sxs-lookup"><span data-stu-id="39a60-121">Compiler overload resolution</span></span>
  
 <span data-ttu-id="39a60-122">オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39a60-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="39a60-123">たとえば、`ushort` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用するオーバーロードされたメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="39a60-123">Consider, for example, the following overloaded methods that use `ushort` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 <span data-ttu-id="39a60-124">`ushort` キャストを使用すると、正しい型が呼び出されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="39a60-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a><span data-ttu-id="39a60-125">変換</span><span class="sxs-lookup"><span data-stu-id="39a60-125">Conversions</span></span>  
 <span data-ttu-id="39a60-126">`ushort` から [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="39a60-126">There is a predefined implicit conversion from `ushort` to [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="39a60-127">[byte](../../../csharp/language-reference/keywords/byte.md) または [char](../../../csharp/language-reference/keywords/char.md) から `ushort` への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="39a60-127">There is a predefined implicit conversion from [byte](../../../csharp/language-reference/keywords/byte.md) or [char](../../../csharp/language-reference/keywords/char.md) to `ushort`.</span></span> <span data-ttu-id="39a60-128">それ以外の場合は、キャストを使用して明示的な変換を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39a60-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="39a60-129">たとえば、2 つの `ushort` 変数 `x` と `y` があるとします。</span><span class="sxs-lookup"><span data-stu-id="39a60-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 <span data-ttu-id="39a60-130">次の代入ステートメントは、代入演算子の右側にある算術式が既定で `int` に評価されるため、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="39a60-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 <span data-ttu-id="39a60-131">この問題を解決するには、キャストを使用します。</span><span class="sxs-lookup"><span data-stu-id="39a60-131">To fix this problem, use a cast:</span></span>  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 <span data-ttu-id="39a60-132">ただし、次のステートメントは使用できます。このステートメントでは、変換先の変数の記憶領域サイズは元のサイズ以上になります。</span><span class="sxs-lookup"><span data-stu-id="39a60-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="39a60-133">浮動小数点型から `ushort` への暗黙的な変換が行われないことにも注意してください。</span><span class="sxs-lookup"><span data-stu-id="39a60-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="39a60-134">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="39a60-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 <span data-ttu-id="39a60-135">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」および「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a60-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="39a60-136">暗黙的な数値変換規則の詳細については、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a60-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="39a60-137">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="39a60-137">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="39a60-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="39a60-138">See Also</span></span>  
 <xref:System.UInt16>  
 [<span data-ttu-id="39a60-139">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="39a60-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="39a60-140">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="39a60-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="39a60-141">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="39a60-141">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="39a60-142">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="39a60-142">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="39a60-143">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="39a60-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="39a60-144">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="39a60-144">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="39a60-145">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="39a60-145">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
