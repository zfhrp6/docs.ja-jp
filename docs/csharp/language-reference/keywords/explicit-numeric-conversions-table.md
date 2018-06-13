---
title: 明示的な数値変換の一覧表 (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], explicit numeric
- numeric conversions [C#], explicit
- explicit numeric conversion [C#]
- numeric data types [C#]
- types [C#], explicit numeric conversions
- type conversion [C#], explicit numeric
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
ms.openlocfilehash: 7363df3e4b2449924222745de409fd68349b93de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218385"
---
# <a name="explicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="4a561-102">明示的な数値変換の一覧表 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4a561-102">Explicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="4a561-103">明示的な数値変換は、暗黙的変換がないときに、キャスト式を利用し、任意の数値型を他の数値型に変換するために利用します。</span><span class="sxs-lookup"><span data-stu-id="4a561-103">Explicit numeric conversion is used to convert any numeric type to any other numeric type, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="4a561-104">次の表はこの変換についてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="4a561-104">The following table shows these conversions.</span></span>  
  
 <span data-ttu-id="4a561-105">変換の詳細については、「[キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a561-105">For more information about conversions, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
|<span data-ttu-id="4a561-106">From</span><span class="sxs-lookup"><span data-stu-id="4a561-106">From</span></span>|<span data-ttu-id="4a561-107">終了</span><span class="sxs-lookup"><span data-stu-id="4a561-107">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="4a561-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="4a561-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="4a561-109">`byte`、`ushort`、`uint`、`ulong`、または `char`</span><span class="sxs-lookup"><span data-stu-id="4a561-109">`byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="4a561-110">byte</span><span class="sxs-lookup"><span data-stu-id="4a561-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="4a561-111">`Sbyte` または `char`</span><span class="sxs-lookup"><span data-stu-id="4a561-111">`Sbyte` or `char`</span></span>|  
|[<span data-ttu-id="4a561-112">short</span><span class="sxs-lookup"><span data-stu-id="4a561-112">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="4a561-113">`sbyte`、`byte`、`ushort`、`uint`、`ulong`、または `char`</span><span class="sxs-lookup"><span data-stu-id="4a561-113">`sbyte`, `byte`, `ushort`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="4a561-114">ushort</span><span class="sxs-lookup"><span data-stu-id="4a561-114">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="4a561-115">`sbyte`、`byte`、`short`、または `char`</span><span class="sxs-lookup"><span data-stu-id="4a561-115">`sbyte`, `byte`, `short`, or `char`</span></span>|  
|[<span data-ttu-id="4a561-116">int</span><span class="sxs-lookup"><span data-stu-id="4a561-116">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="4a561-117">`sbyte`、`byte`、`short`、`ushort`、`uint`、`ulong`、または `char`</span><span class="sxs-lookup"><span data-stu-id="4a561-117">`sbyte`, `byte`, `short`, `ushort`, `uint`, `ulong`,or `char`</span></span>|  
|[<span data-ttu-id="4a561-118">uint</span><span class="sxs-lookup"><span data-stu-id="4a561-118">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="4a561-119">`sbyte`、`byte`、`short`、`ushort`、`int`、または `char`</span><span class="sxs-lookup"><span data-stu-id="4a561-119">`sbyte`, `byte`, `short`, `ushort`, `int`, or `char`</span></span>|  
|[<span data-ttu-id="4a561-120">long</span><span class="sxs-lookup"><span data-stu-id="4a561-120">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="4a561-121">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`ulong`、または `char`</span><span class="sxs-lookup"><span data-stu-id="4a561-121">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `ulong`, or `char`</span></span>|  
|[<span data-ttu-id="4a561-122">ulong</span><span class="sxs-lookup"><span data-stu-id="4a561-122">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="4a561-123">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、または `char`</span><span class="sxs-lookup"><span data-stu-id="4a561-123">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, or `char`</span></span>|  
|[<span data-ttu-id="4a561-124">char</span><span class="sxs-lookup"><span data-stu-id="4a561-124">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="4a561-125">`sbyte`、 `byte`、または `short`</span><span class="sxs-lookup"><span data-stu-id="4a561-125">`sbyte`, `byte`, or `short`</span></span>|  
|[<span data-ttu-id="4a561-126">float</span><span class="sxs-lookup"><span data-stu-id="4a561-126">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="4a561-127">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a561-127">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`,or `decimal`</span></span>|  
|[<span data-ttu-id="4a561-128">double</span><span class="sxs-lookup"><span data-stu-id="4a561-128">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="4a561-129">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、または `decimal`</span><span class="sxs-lookup"><span data-stu-id="4a561-129">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`,or `decimal`</span></span>|  
|[<span data-ttu-id="4a561-130">decimal</span><span class="sxs-lookup"><span data-stu-id="4a561-130">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="4a561-131">`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`char`、`float`、または `double`</span><span class="sxs-lookup"><span data-stu-id="4a561-131">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, or `double`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a561-132">コメント</span><span class="sxs-lookup"><span data-stu-id="4a561-132">Remarks</span></span>  
  
-   <span data-ttu-id="4a561-133">明示的な数値変換では、精度が失われたり、例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="4a561-133">The explicit numeric conversion may cause loss of precision or result in throwing exceptions.</span></span>  
  
-   <span data-ttu-id="4a561-134">`decimal` 値を整数型に変換するとき、この値は 0 方向に最も近い整数値に丸められます。</span><span class="sxs-lookup"><span data-stu-id="4a561-134">When you convert a `decimal` value to an integral type, this value is rounded towards zero to the nearest integral value.</span></span> <span data-ttu-id="4a561-135">結果的に生成される整数値が変換先の型の範囲外になった場合、<xref:System.OverflowException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4a561-135">If the resulting integral value is outside the range of the destination type, an <xref:System.OverflowException> is thrown.</span></span>  
  
-   <span data-ttu-id="4a561-136">`double` または `float` 値から整数型に変換するとき、値に切り捨てが行われます。</span><span class="sxs-lookup"><span data-stu-id="4a561-136">When you convert from a `double` or `float` value to an integral type, the value is truncated.</span></span> <span data-ttu-id="4a561-137">結果的に生成される整数値が変換先の値の範囲外になる場合、結果はオーバーフロー チェック コンテキストによって変わります。</span><span class="sxs-lookup"><span data-stu-id="4a561-137">If the resulting integral value is outside the range of the destination value, the result depends on the overflow checking context.</span></span> <span data-ttu-id="4a561-138">チェック済みコンテキストの場合、`OverflowException` がスローされます。未チェック コンテキストの場合、結果は変換先の型の未指定値になります。</span><span class="sxs-lookup"><span data-stu-id="4a561-138">In a checked context, an `OverflowException` is thrown, while in an unchecked context, the result is an unspecified value of the destination type.</span></span>  
  
-   <span data-ttu-id="4a561-139">`double` を `float` に変換すると、`double` 値は最も近い `float` 値に丸められます。</span><span class="sxs-lookup"><span data-stu-id="4a561-139">When you convert `double` to `float`, the `double` value is rounded to the nearest `float` value.</span></span> <span data-ttu-id="4a561-140">`double` 値が小さすぎるか、大きすぎて変換先の型に合わない場合、結果は 0 か無限になります。</span><span class="sxs-lookup"><span data-stu-id="4a561-140">If the `double` value is too small or too large to fit into the destination type, the result will be zero or infinity.</span></span>  
  
-   <span data-ttu-id="4a561-141">`float` または `double` を `decimal` に変換するとき、変換元の値は `decimal` 表現に変換され、必要であれば、28 番目の小数位の後に最も近い数字に丸められます。</span><span class="sxs-lookup"><span data-stu-id="4a561-141">When you convert `float` or `double` to `decimal`, the source value is converted to `decimal` representation and rounded to the nearest number after the 28th decimal place if required.</span></span> <span data-ttu-id="4a561-142">変換元の値によっては、結果は次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="4a561-142">Depending on the value of the source value, one of the following results may occur:</span></span>  
  
    -   <span data-ttu-id="4a561-143">変換元の値が小さすぎて `decimal` として表現できない場合、結果は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="4a561-143">If the source value is too small to be represented as a `decimal`, the result becomes zero.</span></span>  
  
    -   <span data-ttu-id="4a561-144">変換元の値が NaN (Not a Number/数字ではない) か、無限か、大きすぎて `decimal` として表現できない場合、`OverflowException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4a561-144">If the source value is NaN (not a number), infinity, or too large to be represented as a `decimal`, an `OverflowException` is thrown.</span></span>  
  
-   <span data-ttu-id="4a561-145">`decimal` を `float` または `double` に変換すると、`decimal` 値は最も近い `double` または `float` 値に丸められます。</span><span class="sxs-lookup"><span data-stu-id="4a561-145">When you convert `decimal` to `float` or `double`, the `decimal` value is rounded to the nearest `double` or `float` value.</span></span>  
  
 <span data-ttu-id="4a561-146">明示的な変換の詳細については、「C# 言語仕様」の「明示的」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a561-146">For more information on explicit conversion, see Explicit in the C# Language Specification.</span></span> <span data-ttu-id="4a561-147">仕様にアクセスする方法については、「[C# のドラフト言語仕様](../../../csharp/language-reference/language-specification/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a561-147">For more information on how to access the spec, see [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a561-148">参照</span><span class="sxs-lookup"><span data-stu-id="4a561-148">See Also</span></span>  
 [<span data-ttu-id="4a561-149">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="4a561-149">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4a561-150">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="4a561-150">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4a561-151">キャストと型変換</span><span class="sxs-lookup"><span data-stu-id="4a561-151">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="4a561-152">() 演算子</span><span class="sxs-lookup"><span data-stu-id="4a561-152">() Operator</span></span>](../../../csharp/language-reference/operators/invocation-operator.md)  
 [<span data-ttu-id="4a561-153">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="4a561-153">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="4a561-154">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="4a561-154">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="4a561-155">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="4a561-155">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
