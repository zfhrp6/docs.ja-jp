---
title: "char (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 41f672e9b12481fa5cce78015e95d2c5245a26db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="char-c-reference"></a><span data-ttu-id="1f0b6-102">char (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1f0b6-102">char (C# Reference)</span></span>
<span data-ttu-id="1f0b6-103">`char` キーワードは、Unicode 文字を表すために .NET Framework によって使用される <xref:System.Char?displayProperty=nameWithType> 構造体のインスタンスを宣言するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f0b6-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=nameWithType> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="1f0b6-104">`Char` オブジェクトの値は、16 ビット数 (序数) 値です。</span><span class="sxs-lookup"><span data-stu-id="1f0b6-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>  
  
 <span data-ttu-id="1f0b6-105">Unicode 文字は、世界各国の文字言語の大半を表すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f0b6-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>  
  
|<span data-ttu-id="1f0b6-106">型</span><span class="sxs-lookup"><span data-stu-id="1f0b6-106">Type</span></span>|<span data-ttu-id="1f0b6-107">範囲</span><span class="sxs-lookup"><span data-stu-id="1f0b6-107">Range</span></span>|<span data-ttu-id="1f0b6-108">サイズ</span><span class="sxs-lookup"><span data-stu-id="1f0b6-108">Size</span></span>|<span data-ttu-id="1f0b6-109">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="1f0b6-109">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`char`|<span data-ttu-id="1f0b6-110">U+0000 ～ U+FFFF</span><span class="sxs-lookup"><span data-stu-id="1f0b6-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="1f0b6-111">Unicode 16 ビット文字</span><span class="sxs-lookup"><span data-stu-id="1f0b6-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=nameWithType>|  
  
## <a name="literals"></a><span data-ttu-id="1f0b6-112">リテラル</span><span class="sxs-lookup"><span data-stu-id="1f0b6-112">Literals</span></span>  
 <span data-ttu-id="1f0b6-113">`char` 型の定数は、文字リテラル、16 進数のエスケープ シーケンス、または Unicode 表現として記述できます。</span><span class="sxs-lookup"><span data-stu-id="1f0b6-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="1f0b6-114">また、整数の文字コードをキャストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1f0b6-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="1f0b6-115">次の例では、4 つの `char` 変数が `X` という同じ文字で初期化されています。</span><span class="sxs-lookup"><span data-stu-id="1f0b6-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a><span data-ttu-id="1f0b6-116">変換</span><span class="sxs-lookup"><span data-stu-id="1f0b6-116">Conversions</span></span>  
 <span data-ttu-id="1f0b6-117">`char` は、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、または [decimal](../../../csharp/language-reference/keywords/decimal.md) に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="1f0b6-117">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="1f0b6-118">ただし、他の型から `char` 型へと暗黙的に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="1f0b6-118">However, there are no implicit conversions from other types to the `char` type.</span></span>  
  
 <span data-ttu-id="1f0b6-119"><xref:System.Char?displayProperty=nameWithType> 型では、`char` 値を操作するための静的メソッドがいくつか提供されています。</span><span class="sxs-lookup"><span data-stu-id="1f0b6-119">The <xref:System.Char?displayProperty=nameWithType> type provides several static methods for working with `char` values.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1f0b6-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1f0b6-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f0b6-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f0b6-121">See Also</span></span>  
 <xref:System.Char>  
 [<span data-ttu-id="1f0b6-122">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="1f0b6-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1f0b6-123">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1f0b6-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1f0b6-124">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="1f0b6-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1f0b6-125">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="1f0b6-125">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="1f0b6-126">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="1f0b6-126">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="1f0b6-127">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="1f0b6-127">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="1f0b6-128">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="1f0b6-128">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="1f0b6-129">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="1f0b6-129">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="1f0b6-130">文字列</span><span class="sxs-lookup"><span data-stu-id="1f0b6-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
