---
title: "方法: 複数の文字列を連結する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 21
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
ms.openlocfilehash: b191a61258a496115a4d7045046f9b4a2dbee58c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a><span data-ttu-id="29c6f-102">方法: 複数の文字列を連結する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="29c6f-102">How to: Concatenate Multiple Strings (C# Programming Guide)</span></span>
<span data-ttu-id="29c6f-103">*連結*とは、ある文字列を別の文字列の末尾に追加するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="29c6f-103">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="29c6f-104">`+` 演算子を使用して文字列リテラルまたは文字列定数を連結すると、コンパイラによって 1 つの文字列が作成されます。</span><span class="sxs-lookup"><span data-stu-id="29c6f-104">When you concatenate string literals or string constants by using the `+` operator, the compiler creates a single string.</span></span> <span data-ttu-id="29c6f-105">実行時の連結は発生しません。</span><span class="sxs-lookup"><span data-stu-id="29c6f-105">No run time concatenation occurs.</span></span> <span data-ttu-id="29c6f-106">ただし、文字列変数の場合は実行時にのみ連結できます。</span><span class="sxs-lookup"><span data-stu-id="29c6f-106">However, string variables can be concatenated only at run time.</span></span> <span data-ttu-id="29c6f-107">この場合、方法によるパフォーマンスの違いを理解することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="29c6f-107">In this case, you should understand the performance implications of the various approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29c6f-108">例</span><span class="sxs-lookup"><span data-stu-id="29c6f-108">Example</span></span>  
 <span data-ttu-id="29c6f-109">ソース コードを読みやすくするために、長い文字列リテラルを短い文字列に分割している例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="29c6f-109">The following example shows how to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="29c6f-110">これらの文字列は、コンパイル時に 1 つの文字列に連結されます。</span><span class="sxs-lookup"><span data-stu-id="29c6f-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="29c6f-111">関係する文字列の数に関係なく、実行時にパフォーマンス コストは発生しません。</span><span class="sxs-lookup"><span data-stu-id="29c6f-111">There is no run time performance cost regardless of the number of strings involved.</span></span>  
  
 <span data-ttu-id="29c6f-112">[!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="29c6f-112">[!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="29c6f-113">例</span><span class="sxs-lookup"><span data-stu-id="29c6f-113">Example</span></span>  
 <span data-ttu-id="29c6f-114">文字列変数を連結するには、`+` または `+=` 演算子を使用するか、<xref:System.String.Concat%2A?displayProperty=fullName>、<xref:System.String.Format%2A?displayProperty=fullName>、または <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="29c6f-114">To concatenate string variables, you can use the `+` or `+=` operators, or the <xref:System.String.Concat%2A?displayProperty=fullName>, <xref:System.String.Format%2A?displayProperty=fullName> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName> methods.</span></span> <span data-ttu-id="29c6f-115">`+` 演算子は使い方が簡単で、直感的なコードにすることができます。</span><span class="sxs-lookup"><span data-stu-id="29c6f-115">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="29c6f-116">1 つのステートメントで複数の + 演算子を使用している場合でも、文字列の内容がコピーされるのは 1 回のみです。</span><span class="sxs-lookup"><span data-stu-id="29c6f-116">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="29c6f-117">ただし、ループなどでこの操作を複数回実行すると、効率の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="29c6f-117">But if you repeat this operation multiple times, for example in a loop, it might cause efficiency problems.</span></span> <span data-ttu-id="29c6f-118">たとえば次のようなコードがあるとします。</span><span class="sxs-lookup"><span data-stu-id="29c6f-118">For example, note the following code:</span></span>  
  
 <span data-ttu-id="29c6f-119">[!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="29c6f-119">[!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29c6f-120">C# コンパイラでは、文字列連結操作の null 文字列は空の文字列と同様に扱われますが、元の null 文字列の値は変換されません。</span><span class="sxs-lookup"><span data-stu-id="29c6f-120">In string concatenation operations, the C# compiler treats a null string the same as an empty string, but it does not convert the value of the original null string.</span></span>  
  
 <span data-ttu-id="29c6f-121">(1 つのループ内などで) 多数の文字列を連結しない場合、このコードのパフォーマンス コストはそれほどかからない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="29c6f-121">If you are not concatenating large numbers of strings (for example, in a loop), the performance cost of this code is probably not significant.</span></span> <span data-ttu-id="29c6f-122"><xref:System.String.Concat%2A?displayProperty=fullName> メソッドと <xref:System.String.Format%2A?displayProperty=fullName> メソッドについても同様です。</span><span class="sxs-lookup"><span data-stu-id="29c6f-122">The same is true for the <xref:System.String.Concat%2A?displayProperty=fullName> and <xref:System.String.Format%2A?displayProperty=fullName> methods.</span></span>  
  
 <span data-ttu-id="29c6f-123">ただし、パフォーマンスが重要な場合は、常に <xref:System.Text.StringBuilder> クラスを使用して文字列を連結することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="29c6f-123">However, when performance is important, you should always use the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span> <span data-ttu-id="29c6f-124">次のコードでは、`+` 演算子のチェーン効果を使用せず、<xref:System.Text.StringBuilder> クラスの <xref:System.Text.StringBuilder.Append%2A> メソッドを使用して文字列を連結しています。</span><span class="sxs-lookup"><span data-stu-id="29c6f-124">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings without the chaining effect of the `+` operator.</span></span>  
  
 <span data-ttu-id="29c6f-125">[!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="29c6f-125">[!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c6f-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="29c6f-126">See Also</span></span>  
 <span data-ttu-id="29c6f-127"><xref:System.String></span><span class="sxs-lookup"><span data-stu-id="29c6f-127"><xref:System.String></span></span>   
 <span data-ttu-id="29c6f-128"><xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="29c6f-128"><xref:System.Text.StringBuilder></span></span>   
 <span data-ttu-id="29c6f-129">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="29c6f-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="29c6f-130">文字列</span><span class="sxs-lookup"><span data-stu-id="29c6f-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

