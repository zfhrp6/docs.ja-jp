---
title: "char (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 27
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c6601a58804d6ecfcbedbc19da09560884e54e7f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="char-c-reference"></a><span data-ttu-id="72c4c-102">char (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="72c4c-102">char (C# Reference)</span></span>
<span data-ttu-id="72c4c-103">`char` キーワードは、Unicode 文字を表すために .NET Framework によって使用される <xref:System.Char?displayProperty=fullName> 構造体のインスタンスを宣言するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="72c4c-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=fullName> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="72c4c-104">`Char` オブジェクトの値は、16 ビット数 (序数) 値です。</span><span class="sxs-lookup"><span data-stu-id="72c4c-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>  
  
 <span data-ttu-id="72c4c-105">Unicode 文字は、世界各国の文字言語の大半を表すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="72c4c-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>  
  
|<span data-ttu-id="72c4c-106">型</span><span class="sxs-lookup"><span data-stu-id="72c4c-106">Type</span></span>|<span data-ttu-id="72c4c-107">範囲</span><span class="sxs-lookup"><span data-stu-id="72c4c-107">Range</span></span>|<span data-ttu-id="72c4c-108">サイズ</span><span class="sxs-lookup"><span data-stu-id="72c4c-108">Size</span></span>|<span data-ttu-id="72c4c-109">.NET Framework 型</span><span class="sxs-lookup"><span data-stu-id="72c4c-109">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`char`|<span data-ttu-id="72c4c-110">U+0000 ～ U+FFFF</span><span class="sxs-lookup"><span data-stu-id="72c4c-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="72c4c-111">Unicode 16 ビット文字</span><span class="sxs-lookup"><span data-stu-id="72c4c-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="72c4c-112">リテラル</span><span class="sxs-lookup"><span data-stu-id="72c4c-112">Literals</span></span>  
 <span data-ttu-id="72c4c-113">`char` 型の定数は、文字リテラル、16 進数のエスケープ シーケンス、または Unicode 表現として記述できます。</span><span class="sxs-lookup"><span data-stu-id="72c4c-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="72c4c-114">また、整数の文字コードをキャストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="72c4c-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="72c4c-115">次の例では、4 つの `char` 変数が `X` という同じ文字で初期化されています。</span><span class="sxs-lookup"><span data-stu-id="72c4c-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>  
  
 <span data-ttu-id="72c4c-116">[!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="72c4c-116">[!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="72c4c-117">変換</span><span class="sxs-lookup"><span data-stu-id="72c4c-117">Conversions</span></span>  
 <span data-ttu-id="72c4c-118">`char` は、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、または [decimal](../../../csharp/language-reference/keywords/decimal.md) に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="72c4c-118">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="72c4c-119">ただし、他の型から `char` 型へと暗黙的に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="72c4c-119">However, there are no implicit conversions from other types to the `char` type.</span></span>  
  
 <span data-ttu-id="72c4c-120"><xref:System.Char?displayProperty=fullName> 型では、`char` 値を操作するための静的メソッドがいくつか提供されています。</span><span class="sxs-lookup"><span data-stu-id="72c4c-120">The <xref:System.Char?displayProperty=fullName> type provides several static methods for working with `char` values.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="72c4c-121">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="72c4c-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="72c4c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="72c4c-122">See Also</span></span>  
 <span data-ttu-id="72c4c-123"><xref:System.Char></span><span class="sxs-lookup"><span data-stu-id="72c4c-123"><xref:System.Char></span></span>   
 <span data-ttu-id="72c4c-124">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="72c4c-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="72c4c-125">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="72c4c-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="72c4c-126">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="72c4c-126">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="72c4c-127">[整数型の一覧表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="72c4c-127">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="72c4c-128">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="72c4c-128">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="72c4c-129">[暗黙的な数値変換の一覧表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="72c4c-129">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 <span data-ttu-id="72c4c-130">[明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="72c4c-130">[Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span></span>  
 <span data-ttu-id="72c4c-131">[Null 許容型](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="72c4c-131">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="72c4c-132">文字列</span><span class="sxs-lookup"><span data-stu-id="72c4c-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

