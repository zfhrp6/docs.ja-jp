---
title: '方法: 文字列を数値に変換する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 55ff87ef51f00a803276083052d4d86960e702e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="d2b15-102">方法: 文字列を数値に変換する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="d2b15-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="d2b15-103"><xref:System.Convert> クラスのメソッドを使用するか、さまざまな数値型 (int、long、float など) にある `TryParse` メソッドを使用して、[文字列](../../../csharp/language-reference/keywords/string.md)を数値に変換できます。</span><span class="sxs-lookup"><span data-stu-id="d2b15-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="d2b15-104">文字列では、`TryParse` メソッド (たとえば `int.TryParse("11")`) を呼び出すのがいくらか効率的で簡単です。</span><span class="sxs-lookup"><span data-stu-id="d2b15-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, `int.TryParse("11")`).</span></span>  <span data-ttu-id="d2b15-105"><xref:System.IConvertible> を実装している一般的なオブジェクトでは、`Convert` メソッドを使用するのがより便利です。</span><span class="sxs-lookup"><span data-stu-id="d2b15-105">Using a `Convert` method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="d2b15-106">文字列に含まれていると思われる数値型 (<xref:System.Int32?displayProperty=nameWithType> 型など) の `Parse` または `TryParse` メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d2b15-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="d2b15-107"><xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> メソッドは、<xref:System.Int32.Parse%2A> を内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="d2b15-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="d2b15-108">文字列の形式が無効である場合、`Parse` が例外をスローするのに対し、`TryParse` は [false](../../../csharp/language-reference/keywords/false.md) を返します。</span><span class="sxs-lookup"><span data-stu-id="d2b15-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2b15-109">例</span><span class="sxs-lookup"><span data-stu-id="d2b15-109">Example</span></span>  
 <span data-ttu-id="d2b15-110">文字列の先頭と末尾の空白文字は、`Parse` と `TryParse` メソッドによって無視されますが、その他のすべての文字は、適切な数値型 (int、long、ulong、float、decimal など) を形成する文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2b15-110">The `Parse` and `TryParse` methods ignore white space at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="d2b15-111">数値を形成する一連の文字内に空白文字があると、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="d2b15-111">Any white space within the characters that form the number cause an error.</span></span>  <span data-ttu-id="d2b15-112">たとえば、"10"、"10.3"、"  10  " を解析するために `decimal.TryParse` を使用することはできますが、"10X"、"1 0" (スペースに注意)、"10 .3" (スペースに注意)、"10e1" (この場合は `float.TryParse` を使用) などからこのメソッドを使用して 10 を解析することはできません。</span><span class="sxs-lookup"><span data-stu-id="d2b15-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="d2b15-113">以下は、`Parse` および `TryParse` の呼び出しの成功例と失敗例の両方を示しています。</span><span class="sxs-lookup"><span data-stu-id="d2b15-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="d2b15-114">例</span><span class="sxs-lookup"><span data-stu-id="d2b15-114">Example</span></span>  
 <span data-ttu-id="d2b15-115">使用できる <xref:System.Convert> クラスのメソッドの例を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="d2b15-115">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="d2b15-116">数値型</span><span class="sxs-lookup"><span data-stu-id="d2b15-116">Numeric Type</span></span>|<span data-ttu-id="d2b15-117">メソッド</span><span class="sxs-lookup"><span data-stu-id="d2b15-117">Method</span></span>|  
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
  
 <span data-ttu-id="d2b15-118">この例では、<xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> メソッドを呼び出して、入力の [string](../../../csharp/language-reference/keywords/string.md) を [int](../../../csharp/language-reference/keywords/int.md) に変換します。</span><span class="sxs-lookup"><span data-stu-id="d2b15-118">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="d2b15-119">コードは、このメソッドからスローされる最も一般的な 2 種類の例外 (<xref:System.FormatException> と <xref:System.OverflowException>) をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="d2b15-119">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="d2b15-120">整数の格納場所がオーバーフローすることなく数字をインクリメントできる場合、プログラムは結果に 1 を加算し、出力を印刷します。</span><span class="sxs-lookup"><span data-stu-id="d2b15-120">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d2b15-121">参照</span><span class="sxs-lookup"><span data-stu-id="d2b15-121">See Also</span></span>  
 [<span data-ttu-id="d2b15-122">型</span><span class="sxs-lookup"><span data-stu-id="d2b15-122">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="d2b15-123">方法: 文字列が数値を表しているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="d2b15-123">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [<span data-ttu-id="d2b15-124">.NET Framework 4 の書式指定ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="d2b15-124">.NET Framework 4 Formatting Utility</span></span>](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
