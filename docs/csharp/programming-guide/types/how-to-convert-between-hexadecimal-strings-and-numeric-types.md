---
title: '方法: 16 進文字列と数値型の間で変換する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 1a5bde0a9169a78e179a69c7a2f4080e5a465f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="8124d-102">方法: 16 進文字列と数値型の間で変換する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="8124d-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="8124d-103">以下の例では、次のタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8124d-103">These examples show you how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="8124d-104">[string](../../../csharp/language-reference/keywords/string.md) の各文字の 16 進値を取得する。</span><span class="sxs-lookup"><span data-stu-id="8124d-104">Obtain the hexadecimal value of each character in a [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
-   <span data-ttu-id="8124d-105">16 進文字列の各値に対応する [char](../../../csharp/language-reference/keywords/char.md) を取得する。</span><span class="sxs-lookup"><span data-stu-id="8124d-105">Obtain the [char](../../../csharp/language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
-   <span data-ttu-id="8124d-106">16 進 `string` を [int](../../../csharp/language-reference/keywords/int.md) に変換する。</span><span class="sxs-lookup"><span data-stu-id="8124d-106">Convert a hexadecimal `string` to an [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
-   <span data-ttu-id="8124d-107">16 進 `string` を [float](../../../csharp/language-reference/keywords/float.md) に変換する。</span><span class="sxs-lookup"><span data-stu-id="8124d-107">Convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md).</span></span>  
  
-   <span data-ttu-id="8124d-108">[バイト](../../../csharp/language-reference/keywords/byte.md)配列を 16 進 `string` に変換する。</span><span class="sxs-lookup"><span data-stu-id="8124d-108">Convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8124d-109">例</span><span class="sxs-lookup"><span data-stu-id="8124d-109">Example</span></span>  
 <span data-ttu-id="8124d-110">この例では、`string` の各文字の 16 進値を出力しています。</span><span class="sxs-lookup"><span data-stu-id="8124d-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="8124d-111">まず `string` を解析し、文字配列に変換します。</span><span class="sxs-lookup"><span data-stu-id="8124d-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="8124d-112">次いで、その数値を取得するために、各文字で <xref:System.Convert.ToInt32%28System.Char%29> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8124d-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="8124d-113">最後に、その数を 16 進表現で `string` に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="8124d-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8124d-114">例</span><span class="sxs-lookup"><span data-stu-id="8124d-114">Example</span></span>  
 <span data-ttu-id="8124d-115">この例は、16 進値の `string` を解析し、各 16 進値に対応する文字を出力しています。</span><span class="sxs-lookup"><span data-stu-id="8124d-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="8124d-116">まず、[Split(Char\[\])](xref:System.String.Split(System.Char[])) メソッドを呼び出して、各 16 進値を配列内の個別の `string` として取得します。</span><span class="sxs-lookup"><span data-stu-id="8124d-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="8124d-117">次いで <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> を呼び出し、16 進数値を [int](../../../csharp/language-reference/keywords/int.md) の 10 進数値に変換します。ここでは、その文字コードに対応する文字を取得するための 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8124d-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../../csharp/language-reference/keywords/int.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="8124d-118">1 つは、<xref:System.Char.ConvertFromUtf32%28System.Int32%29> を使用する方法です。これは、整数引数に対応する文字を `string` として返します。</span><span class="sxs-lookup"><span data-stu-id="8124d-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="8124d-119">もう 1 つは、`int` を明示的に [char](../../../csharp/language-reference/keywords/char.md) にキャストする方法です。</span><span class="sxs-lookup"><span data-stu-id="8124d-119">The second technique explicitly casts the `int` to a [char](../../../csharp/language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="8124d-120">例</span><span class="sxs-lookup"><span data-stu-id="8124d-120">Example</span></span>  
 <span data-ttu-id="8124d-121">この例では、<xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> メソッドを呼び出し、16 進数 `string` を整数に変換する、別の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8124d-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="8124d-122">例</span><span class="sxs-lookup"><span data-stu-id="8124d-122">Example</span></span>  
 <span data-ttu-id="8124d-123">次の例では、<xref:System.BitConverter?displayProperty=nameWithType> クラスおよび <xref:System.Int32.Parse%2A?displayProperty=nameWithType> メソッドを使用して、16 進数の `string` を [float](../../../csharp/language-reference/keywords/float.md) に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8124d-123">The following example shows how to convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.Int32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="8124d-124">例</span><span class="sxs-lookup"><span data-stu-id="8124d-124">Example</span></span>  
 <span data-ttu-id="8124d-125">次の例は、<xref:System.BitConverter?displayProperty=nameWithType> クラスを使用して [byte](../../../csharp/language-reference/keywords/byte.md) 配列を 16 進文字列に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8124d-125">The following example shows how to convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8124d-126">参照</span><span class="sxs-lookup"><span data-stu-id="8124d-126">See Also</span></span>  
 [<span data-ttu-id="8124d-127">標準の数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="8124d-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="8124d-128">型</span><span class="sxs-lookup"><span data-stu-id="8124d-128">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="8124d-129">方法: 文字列が数値を表しているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="8124d-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
