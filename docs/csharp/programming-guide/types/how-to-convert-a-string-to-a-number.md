---
title: "方法: 文字列を数値に変換する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: 34
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
ms.openlocfilehash: 08d13e40a385ce8e9011b508b04361b2e050f904
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="a456c-102">方法: 文字列を数値に変換する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="a456c-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="a456c-103"><xref:System.Convert> クラスのメソッドを使用するか、さまざまな数値型 (int、long、float など) にある `TryParse` メソッドを使用して、[文字列](../../../csharp/language-reference/keywords/string.md)を数値に変換できます。</span><span class="sxs-lookup"><span data-stu-id="a456c-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="a456c-104">文字列では、`TryParse` メソッド (たとえば `int.TryParse("11")`) を呼び出すのがいくらか効率的で簡単です。</span><span class="sxs-lookup"><span data-stu-id="a456c-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, `int.TryParse("11")`).</span></span>  <span data-ttu-id="a456c-105"><xref:System.IConvertible> を実装している一般的なオブジェクトでは、`Convert` メソッドを使用するのがより便利です。</span><span class="sxs-lookup"><span data-stu-id="a456c-105">Using a `Convert` method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="a456c-106">文字列に含まれていると思われる数値型 (<xref:System.Int32?displayProperty=fullName> 型など) の `Parse` または `TryParse` メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a456c-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=fullName> type.</span></span>  <span data-ttu-id="a456c-107"><xref:System.Convert.ToUInt32%2A?displayProperty=fullName> メソッドは、<xref:System.Int32.Parse%2A> を内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="a456c-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=fullName> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="a456c-108">文字列の形式が無効である場合、`Parse` が例外をスローするのに対し、`TryParse` は [false](../../../csharp/language-reference/keywords/false.md) を返します。</span><span class="sxs-lookup"><span data-stu-id="a456c-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a456c-109">例</span><span class="sxs-lookup"><span data-stu-id="a456c-109">Example</span></span>  
 <span data-ttu-id="a456c-110">文字列の先頭と末尾の空白文字は、`Parse` と `TryParse` メソッドによって無視されますが、その他のすべての文字は、適切な数値型 (int、long、ulong、float、decimal など) を形成する文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a456c-110">The `Parse` and `TryParse` methods ignore whitespace at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="a456c-111">数値を形成する一連の文字内に空白文字があると、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="a456c-111">Any whitespace within the characters that form the number cause an error.</span></span>  <span data-ttu-id="a456c-112">たとえば、"10"、"10.3"、"  10  " を解析するために `decimal.TryParse` を使用することはできますが、"10X"、"1 0" (スペースに注意)、"10 .3" (スペースに注意)、"10e1" (この場合は `float.TryParse` を使用) などからこのメソッドを使用して 10 を解析することはできません。</span><span class="sxs-lookup"><span data-stu-id="a456c-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="a456c-113">以下は、`Parse` および `TryParse` の呼び出しの成功例と失敗例の両方を示しています。</span><span class="sxs-lookup"><span data-stu-id="a456c-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 <span data-ttu-id="a456c-114">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a456c-114">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span></span>  
<span data-ttu-id="a456c-115">[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="a456c-115">[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]</span></span>  
<span data-ttu-id="a456c-116">[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="a456c-116">[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]</span></span>  
<span data-ttu-id="a456c-117">[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="a456c-117">[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]</span></span>  
<span data-ttu-id="a456c-118">[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="a456c-118">[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]</span></span>  
<span data-ttu-id="a456c-119">[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="a456c-119">[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="a456c-120">例</span><span class="sxs-lookup"><span data-stu-id="a456c-120">Example</span></span>  
 <span data-ttu-id="a456c-121">使用できる <xref:System.Convert> クラスのメソッドの例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="a456c-121">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="a456c-122">数値型</span><span class="sxs-lookup"><span data-stu-id="a456c-122">Numeric Type</span></span>|<span data-ttu-id="a456c-123">メソッド</span><span class="sxs-lookup"><span data-stu-id="a456c-123">Method</span></span>|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 <span data-ttu-id="a456c-124">この例では、<xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> メソッドを呼び出して、入力の [string](../../../csharp/language-reference/keywords/string.md) を [int](../../../csharp/language-reference/keywords/int.md) に変換します。</span><span class="sxs-lookup"><span data-stu-id="a456c-124">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="a456c-125">コードは、このメソッドからスローされる最も一般的な 2 種類の例外 (<xref:System.FormatException> と <xref:System.OverflowException>) をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="a456c-125">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="a456c-126">整数の格納場所がオーバーフローすることなく数字をインクリメントできる場合、プログラムは結果に 1 を加算し、出力を印刷します。</span><span class="sxs-lookup"><span data-stu-id="a456c-126">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 <span data-ttu-id="a456c-127">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a456c-127">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span></span>  
<span data-ttu-id="a456c-128">[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="a456c-128">[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a456c-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a456c-129">See Also</span></span>  
 <span data-ttu-id="a456c-130">[型](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="a456c-130">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="a456c-131">[方法: 文字列が数値を表しているかどうかを確認する](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md) </span><span class="sxs-lookup"><span data-stu-id="a456c-131">[How to: Determine Whether a String Represents a Numeric Value](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md) </span></span>  
 [<span data-ttu-id="a456c-132">.NET Framework 4 の書式指定ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="a456c-132">.NET Framework 4 Formatting Utility</span></span>](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)

