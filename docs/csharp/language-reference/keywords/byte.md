---
title: "byte (C# リファレンス)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- byte
- byte_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8ef7494e2a8a1463d37cff77d1dacebec8182b66
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="byte-c-reference"></a><span data-ttu-id="73989-102">byte (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="73989-102">byte (C# Reference)</span></span>

<span data-ttu-id="73989-103">`byte` は、次の表に示された値を格納する整数型を示します。</span><span class="sxs-lookup"><span data-stu-id="73989-103">`byte` denotes an integral type that stores values as indicated in the following table.</span></span>  
  
|<span data-ttu-id="73989-104">型</span><span class="sxs-lookup"><span data-stu-id="73989-104">Type</span></span>|<span data-ttu-id="73989-105">範囲</span><span class="sxs-lookup"><span data-stu-id="73989-105">Range</span></span>|<span data-ttu-id="73989-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="73989-106">Size</span></span>|<span data-ttu-id="73989-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="73989-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`byte`|<span data-ttu-id="73989-108">0 ～ 255</span><span class="sxs-lookup"><span data-stu-id="73989-108">0 to 255</span></span>|<span data-ttu-id="73989-109">符号なし 8 ビット整数</span><span class="sxs-lookup"><span data-stu-id="73989-109">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="73989-110">リテラル</span><span class="sxs-lookup"><span data-stu-id="73989-110">Literals</span></span>  

 <span data-ttu-id="73989-111">`byte` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="73989-111">You can declare and initialize a `byte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="73989-112">整数リテラルが `byte` の範囲外にある場合 (つまり、<xref:System.Byte.MinValue?displayProperty=fullName> より小さいか、<xref:System.Byte.MaxValue?displayProperty=fullName> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="73989-112">If the integer literal is outside the range of `byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=fullName> or greater than <xref:System.Byte.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span>

<span data-ttu-id="73989-113">次の例では、整数 201 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[int](../../../csharp/language-reference/keywords/int.md) から `byte` 値に暗黙的に変換されています。</span><span class="sxs-lookup"><span data-stu-id="73989-113">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `byte` values.</span></span>    
  
<span data-ttu-id="73989-114">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]</span><span class="sxs-lookup"><span data-stu-id="73989-114">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="73989-115">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="73989-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="73989-116">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="73989-116">Decimal literals have no prefix.</span></span>

<span data-ttu-id="73989-117">C# 7 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="73989-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="73989-118">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]</span><span class="sxs-lookup"><span data-stu-id="73989-118">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]</span></span>  
 
## <a name="conversions"></a><span data-ttu-id="73989-119">変換</span><span class="sxs-lookup"><span data-stu-id="73989-119">Conversions</span></span>  
 <span data-ttu-id="73989-120">`byte` から [short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への暗黙の型変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="73989-120">There is a predefined implicit conversion from `byte` to [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="73989-121">より大きな記憶領域のサイズを持つ、リテラル以外の数値型を暗黙的に `byte` に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="73989-121">You cannot implicitly convert non-literal numeric types of larger storage size to `byte`.</span></span> <span data-ttu-id="73989-122">整数型の記憶域サイズの詳細については、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73989-122">For more information on the storage sizes of integral types, see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md).</span></span> <span data-ttu-id="73989-123">たとえば、2 つの `byte` 変数 `x` と `y` があるとします。</span><span class="sxs-lookup"><span data-stu-id="73989-123">Consider, for example, the following two `byte` variables `x` and `y`:</span></span>  
  
```  
byte x = 10, y = 20;  
```  
  
 <span data-ttu-id="73989-124">次の代入ステートメントは、代入演算子の右側にある算術式が既定で `int` に評価されるため、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="73989-124">The following assignment statement will produce a compilation error, because the arithmetic expression on the right-hand side of the assignment operator evaluates to `int` by default.</span></span>  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 <span data-ttu-id="73989-125">この問題を解決するには、キャストを使用します。</span><span class="sxs-lookup"><span data-stu-id="73989-125">To fix this problem, use a cast:</span></span>  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 <span data-ttu-id="73989-126">ただし、次のステートメントは使用できます。このステートメントでは、変換先の変数の記憶領域サイズは元のサイズ以上になります。</span><span class="sxs-lookup"><span data-stu-id="73989-126">It is possible though, to use the following statements where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="73989-127">浮動小数点型から `byte` への暗黙の型変換はありません。</span><span class="sxs-lookup"><span data-stu-id="73989-127">Also, there is no implicit conversion from floating-point types to `byte`.</span></span> <span data-ttu-id="73989-128">たとえば、次のステートメントは、明示的なキャストを使用しない場合、コンパイラ エラーになります。</span><span class="sxs-lookup"><span data-stu-id="73989-128">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 <span data-ttu-id="73989-129">オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="73989-129">When calling overloaded methods, a cast must be used.</span></span> <span data-ttu-id="73989-130">たとえば、`byte` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用したオーバーロードされたメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="73989-130">Consider, for example, the following overloaded methods that use `byte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 <span data-ttu-id="73989-131">`byte` キャストを使用すると、正しい型が呼び出されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="73989-131">Using the `byte` cast guarantees that the correct type is called, for example:</span></span>  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 <span data-ttu-id="73989-132">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73989-132">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="73989-133">暗黙的な数値変換規則について詳しくは、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="73989-133">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="73989-134">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="73989-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73989-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="73989-135">See Also</span></span>  
 <span data-ttu-id="73989-136"><xref:System.Byte></span><span class="sxs-lookup"><span data-stu-id="73989-136"><xref:System.Byte></span></span>   
 <span data-ttu-id="73989-137">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="73989-137">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="73989-138">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="73989-138">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="73989-139">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="73989-139">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="73989-140">[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="73989-140">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="73989-141">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="73989-141">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="73989-142">[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="73989-142">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="73989-143">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="73989-143">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

