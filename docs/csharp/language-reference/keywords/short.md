---
title: "short (C# リファレンス)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
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
ms.openlocfilehash: ab3ccfdeb8d8a67b5fcd60b1ad6eee4dcafc9691
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="short-c-reference"></a><span data-ttu-id="46c7b-102">short (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="46c7b-102">short (C# Reference)</span></span>

<span data-ttu-id="46c7b-103">`short` は、次の表に示すサイズと範囲で値を格納する整数データ型を示します。</span><span class="sxs-lookup"><span data-stu-id="46c7b-103">`short` denotes an integral data type that stores values according to the size and range shown in the following table.</span></span>  
  
|<span data-ttu-id="46c7b-104">型</span><span class="sxs-lookup"><span data-stu-id="46c7b-104">Type</span></span>|<span data-ttu-id="46c7b-105">範囲</span><span class="sxs-lookup"><span data-stu-id="46c7b-105">Range</span></span>|<span data-ttu-id="46c7b-106">サイズ</span><span class="sxs-lookup"><span data-stu-id="46c7b-106">Size</span></span>|<span data-ttu-id="46c7b-107">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="46c7b-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`short`|<span data-ttu-id="46c7b-108">-32,768 ～ 32,767</span><span class="sxs-lookup"><span data-stu-id="46c7b-108">-32,768 to 32,767</span></span>|<span data-ttu-id="46c7b-109">符号付き 16 ビット整数</span><span class="sxs-lookup"><span data-stu-id="46c7b-109">Signed 16-bit integer</span></span>|<xref:System.Int16?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="46c7b-110">リテラル</span><span class="sxs-lookup"><span data-stu-id="46c7b-110">Literals</span></span>  

<span data-ttu-id="46c7b-111">`short` 変数を宣言し、10 進リテラル、16 進リテラル、または (C# 7 以降) バイナリ リテラルを割り当てることによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="46c7b-111">You can declare and initialize a `short` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span>  <span data-ttu-id="46c7b-112">整数リテラルが `short` の範囲外にある場合 (つまり、<xref:System.Int16.MinValue?displayProperty=fullName> より小さいか、<xref:System.Int16.MaxValue?displayProperty=fullName> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="46c7b-112">If the integer literal is outside the range of `short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=fullName> or greater than <xref:System.Int16.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span> 

<span data-ttu-id="46c7b-113">次の例では、整数 1,034 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[int](../../../csharp/language-reference/keywords/int.md) から `short` 値に暗黙的に変換されています。</span><span class="sxs-lookup"><span data-stu-id="46c7b-113">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `short` values.</span></span>  
  
<span data-ttu-id="46c7b-114">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]</span><span class="sxs-lookup"><span data-stu-id="46c7b-114">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="46c7b-115">16 進リテラルを表すにはプレフィックス `0x` または `0X` を使い、バイナリ リテラルを表すにはプレフィックス `0b` または `0B` を使います。</span><span class="sxs-lookup"><span data-stu-id="46c7b-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="46c7b-116">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="46c7b-116">Decimal literals have no prefix.</span></span>

<span data-ttu-id="46c7b-117">C# 7 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="46c7b-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="46c7b-118">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]</span><span class="sxs-lookup"><span data-stu-id="46c7b-118">[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]</span></span>  
 
## <a name="compiler-overload-resolution"></a><span data-ttu-id="46c7b-119">コンパイラのオーバーロード解決</span><span class="sxs-lookup"><span data-stu-id="46c7b-119">Compiler overload resolution</span></span>

 <span data-ttu-id="46c7b-120">オーバーロードされたメソッドを呼び出すときは、キャストを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46c7b-120">A cast must be used when calling overloaded methods.</span></span> <span data-ttu-id="46c7b-121">たとえば、`short` パラメーターと [int](../../../csharp/language-reference/keywords/int.md) パラメーターを使用するオーバーロードされたメソッドがあるとします。</span><span class="sxs-lookup"><span data-stu-id="46c7b-121">Consider, for example, the following overloaded methods that use `short` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 <span data-ttu-id="46c7b-122">`short` キャストを使用すると、正しい型が呼び出されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="46c7b-122">Using the `short` cast guarantees that the correct type is called, for example:</span></span>  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a><span data-ttu-id="46c7b-123">変換</span><span class="sxs-lookup"><span data-stu-id="46c7b-123">Conversions</span></span>  

 <span data-ttu-id="46c7b-124">`short` から [int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) への、定義済みの暗黙的な変換が組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="46c7b-124">There is a predefined implicit conversion from `short` to [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="46c7b-125">記憶領域が大きなリテラル以外の数値型を暗黙的に `short` に変換することはできません (整数型の記憶領域については、「[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="46c7b-125">You cannot implicitly convert nonliteral numeric types of larger storage size to `short` (see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) for the storage sizes of integral types).</span></span> <span data-ttu-id="46c7b-126">たとえば、2 つの `short` 変数 `x` と `y` があるとします。</span><span class="sxs-lookup"><span data-stu-id="46c7b-126">Consider, for example, the following two `short` variables `x` and `y`:</span></span>  
  
```csharp  
short x = 5, y = 12;  
```  
  
 <span data-ttu-id="46c7b-127">次の代入ステートメントは、代入演算子の右側にある算術式が既定で [int](../../../csharp/language-reference/keywords/int.md) に評価されるため、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="46c7b-127">The following assignment statement produces a compilation error because the arithmetic expression on the right-hand side of the assignment operator evaluates to [int](../../../csharp/language-reference/keywords/int.md) by default.</span></span>  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 <span data-ttu-id="46c7b-128">この問題を解決するには、キャストを使用します。</span><span class="sxs-lookup"><span data-stu-id="46c7b-128">To fix this problem, use a cast:</span></span>  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 <span data-ttu-id="46c7b-129">次のステートメントを使うこともできます。このステートメントでは、変換先の変数の記憶領域サイズは元のサイズ以上になります。</span><span class="sxs-lookup"><span data-stu-id="46c7b-129">It is also possible to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="46c7b-130">浮動小数点型から `short` への暗黙的な変換は行われません。</span><span class="sxs-lookup"><span data-stu-id="46c7b-130">There is no implicit conversion from floating-point types to `short`.</span></span> <span data-ttu-id="46c7b-131">たとえば、次のステートメントは、明示的なキャストを使用しない限り、コンパイル エラーになります。</span><span class="sxs-lookup"><span data-stu-id="46c7b-131">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 <span data-ttu-id="46c7b-132">浮動小数点型と整数型の混在する算術式の詳細については、「[float](../../../csharp/language-reference/keywords/float.md)」と「[double](../../../csharp/language-reference/keywords/double.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46c7b-132">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="46c7b-133">暗黙的な数値変換規則について詳しくは、「[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="46c7b-133">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="46c7b-134">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="46c7b-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46c7b-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="46c7b-135">See Also</span></span>  
 <span data-ttu-id="46c7b-136"><xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="46c7b-136"><xref:System.Int16></span></span>   
 <span data-ttu-id="46c7b-137">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="46c7b-137">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="46c7b-138">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="46c7b-138">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="46c7b-139">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="46c7b-139">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="46c7b-140">[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="46c7b-140">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="46c7b-141">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="46c7b-141">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="46c7b-142">[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="46c7b-142">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="46c7b-143">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="46c7b-143">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

