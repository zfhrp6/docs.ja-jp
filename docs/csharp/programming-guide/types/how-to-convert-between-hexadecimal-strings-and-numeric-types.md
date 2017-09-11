---
title: "方法: 16 進文字列と数値型の間で変換する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
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
ms.openlocfilehash: 312b18e6bf30ace166435e51b1b83937b5c6bf38
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="4c68a-102">方法: 16 進文字列と数値型の間で変換する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4c68a-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="4c68a-103">以下の例では、次のタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-103">These examples show you how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="4c68a-104">[string](../../../csharp/language-reference/keywords/string.md) の各文字の 16 進値を取得する。</span><span class="sxs-lookup"><span data-stu-id="4c68a-104">Obtain the hexadecimal value of each character in a [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
-   <span data-ttu-id="4c68a-105">16 進文字列の各値に対応する [char](../../../csharp/language-reference/keywords/char.md) を取得する。</span><span class="sxs-lookup"><span data-stu-id="4c68a-105">Obtain the [char](../../../csharp/language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
-   <span data-ttu-id="4c68a-106">16 進 `string` を [int](../../../csharp/language-reference/keywords/int.md) に変換する。</span><span class="sxs-lookup"><span data-stu-id="4c68a-106">Convert a hexadecimal `string` to an [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
-   <span data-ttu-id="4c68a-107">16 進 `string` を [float](../../../csharp/language-reference/keywords/float.md) に変換する。</span><span class="sxs-lookup"><span data-stu-id="4c68a-107">Convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md).</span></span>  
  
-   <span data-ttu-id="4c68a-108">[バイト](../../../csharp/language-reference/keywords/byte.md)配列を 16 進 `string` に変換する。</span><span class="sxs-lookup"><span data-stu-id="4c68a-108">Convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c68a-109">例</span><span class="sxs-lookup"><span data-stu-id="4c68a-109">Example</span></span>  
 <span data-ttu-id="4c68a-110">この例では、`string` の各文字の 16 進値を出力しています。</span><span class="sxs-lookup"><span data-stu-id="4c68a-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="4c68a-111">まず `string` を解析し、文字配列に変換します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="4c68a-112">次いで、その数値を取得するために、各文字で <xref:System.Convert.ToInt32%28System.Char%29> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="4c68a-113">最後に、その数を 16 進表現で `string` に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 <span data-ttu-id="4c68a-114">[!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c68a-114">[!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c68a-115">例</span><span class="sxs-lookup"><span data-stu-id="4c68a-115">Example</span></span>  
 <span data-ttu-id="4c68a-116">この例は、16 進値の `string` を解析し、各 16 進値に対応する文字を出力しています。</span><span class="sxs-lookup"><span data-stu-id="4c68a-116">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="4c68a-117">まず、[Split(Char\[\])](xref:System.String.Split(System.Char[])) メソッドを呼び出して、各 16 進値を配列内の個別の `string` として取得します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-117">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="4c68a-118">次いで <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> を呼び出し、16 進数値を [int](../../../csharp/language-reference/keywords/int.md) の 10 進数値に変換します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-118">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="4c68a-119">ここでは、その文字コードに対応する文字を取得するための 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4c68a-119">It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="4c68a-120">1 つは、<xref:System.Char.ConvertFromUtf32%28System.Int32%29> を使用する方法です。これは、整数引数に対応する文字を `string` として返します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-120">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="4c68a-121">もう 1 つは、`int` を明示的に [char](../../../csharp/language-reference/keywords/char.md) にキャストする方法です。</span><span class="sxs-lookup"><span data-stu-id="4c68a-121">The second technique explicitly casts the `int` to a [char](../../../csharp/language-reference/keywords/char.md).</span></span>  
  
 <span data-ttu-id="4c68a-122">[!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c68a-122">[!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c68a-123">例</span><span class="sxs-lookup"><span data-stu-id="4c68a-123">Example</span></span>  
 <span data-ttu-id="4c68a-124">この例では、<xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> メソッドを呼び出し、16 進数 `string` を整数に変換する、別の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-124">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 <span data-ttu-id="4c68a-125">[!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c68a-125">[!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c68a-126">例</span><span class="sxs-lookup"><span data-stu-id="4c68a-126">Example</span></span>  
 <span data-ttu-id="4c68a-127">次の例では、<xref:System.BitConverter?displayProperty=fullName> クラスおよび <xref:System.Int32.Parse%2A?displayProperty=fullName> メソッドを使用して、16 進数の `string` を [float](../../../csharp/language-reference/keywords/float.md) に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-127">The following example shows how to convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md) by using the <xref:System.BitConverter?displayProperty=fullName> class and the <xref:System.Int32.Parse%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="4c68a-128">[!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c68a-128">[!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c68a-129">例</span><span class="sxs-lookup"><span data-stu-id="4c68a-129">Example</span></span>  
 <span data-ttu-id="4c68a-130">次の例は、<xref:System.BitConverter?displayProperty=fullName> クラスを使用して [byte](../../../csharp/language-reference/keywords/byte.md) 配列を 16 進文字列に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4c68a-130">The following example shows how to convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=fullName> class.</span></span>  
  
 <span data-ttu-id="4c68a-131">[!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="4c68a-131">[!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c68a-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c68a-132">See Also</span></span>  
 <span data-ttu-id="4c68a-133">[標準の数値書式指定文字列](../../../standard/base-types/standard-numeric-format-strings.md) </span><span class="sxs-lookup"><span data-stu-id="4c68a-133">[Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md) </span></span>  
 <span data-ttu-id="4c68a-134">[型](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="4c68a-134">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 [<span data-ttu-id="4c68a-135">方法: 文字列が数値を表しているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="4c68a-135">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)

