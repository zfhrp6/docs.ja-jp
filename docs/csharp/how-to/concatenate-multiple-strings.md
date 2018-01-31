---
title: "方法: 複数の文字列を連結する (C# ガイド)"
description: "C# で文字列を連結する方法は複数あります。 各選択のオプションと、それを選ぶ理由も示します。"
ms.date: 01/11/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4bc5e04edba48065746b96841b628ec5843c5e9
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="a1955-104">方法: 複数の文字列を連結する (C# ガイド)</span><span class="sxs-lookup"><span data-stu-id="a1955-104">How to: Concatenate Multiple Strings (C# Guide)</span></span>

<span data-ttu-id="a1955-105">*連結*とは、ある文字列を別の文字列の末尾に追加するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="a1955-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="a1955-106">文字列を連結するには、+ 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="a1955-106">You concatenate strings by using the + operator.</span></span> <span data-ttu-id="a1955-107">文字列リテラルと文字列定数の場合、連結はコンパイル時に行われ、実行時には行われません。</span><span class="sxs-lookup"><span data-stu-id="a1955-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="a1955-108">文字列変数の連結は実行時にのみ行われます。</span><span class="sxs-lookup"><span data-stu-id="a1955-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="a1955-109">次の例では、ソース コードを読みやすくするために、連結を使用して長い文字列リテラルを短い文字列に分割しています。</span><span class="sxs-lookup"><span data-stu-id="a1955-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="a1955-110">これらの文字列は、コンパイル時に 1 つの文字列に連結されます。</span><span class="sxs-lookup"><span data-stu-id="a1955-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="a1955-111">関係する文字列の数に関係なく、実行時にパフォーマンス コストは発生しません。</span><span class="sxs-lookup"><span data-stu-id="a1955-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

<span data-ttu-id="a1955-112">文字列変数を連結するには、`+` または `+=` 演算子を使用するか、[文字列補間](../tutorials/string-interpolation.md) を使用するか、<xref:System.String.Concat%2A?displayProperty=nameWithType> メソッド、<xref:System.String.Format%2A?displayProperty=nameWithType> メソッド、または <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1955-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../tutorials/string-interpolation.md) or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="a1955-113">`+` 演算子は使い方が簡単で、直感的なコードにすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1955-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="a1955-114">1 つのステートメントで複数の + 演算子を使用している場合でも、文字列の内容がコピーされるのは 1 回のみです。</span><span class="sxs-lookup"><span data-stu-id="a1955-114">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="a1955-115">次のコードは、`+` 演算子を使用して文字列を連結する 2 つの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="a1955-115">The following code shows two examples of using the `+` operator to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="a1955-116">式によっては、次のコードに示すように、文字列補間を使用して文字列を連結する方が簡単な場合があります。</span><span class="sxs-lookup"><span data-stu-id="a1955-116">In some expressions, it is easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  <span data-ttu-id="a1955-117">文字列連結操作において、C# コンパイラでは null 文字列は空の文字列と同様に扱われます。</span><span class="sxs-lookup"><span data-stu-id="a1955-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="a1955-118">文字列を連結する他のメソッドとして、<xref:System.String.Concat%2A?displayProperty=nameWithType> および <xref:System.String.Format%2A?displayProperty=nameWithType> があります。</span><span class="sxs-lookup"><span data-stu-id="a1955-118">Other methods to concatenate strings are <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a1955-119">これらのメソッドは、少ない数のコンポーネント文字列で文字列を作成する場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="a1955-119">These methods work well when you are building a string from a small number of component strings.</span></span> <span data-ttu-id="a1955-120">これらのメソッドは、連結した文字列を構成する文字列の数がわかっている場合にも有効です。</span><span class="sxs-lookup"><span data-stu-id="a1955-120">These methdos are also a great choice when you know the number of strings that make up your concatenated string.</span></span>

<span data-ttu-id="a1955-121">他にも、ループ内の文字列を結合する場合があります。このケースでは、結合するソース文字列の数はわからず、ソース文字列の実際の数は非常に大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a1955-121">In other cases you may be combining strings in a loop, where you don't know how many source strings you are combining, and the actual number of source strings may be quite large.</span></span> <span data-ttu-id="a1955-122"><xref:System.Text.StringBuilder> クラスは、このようなシナリオのために設計されています。</span><span class="sxs-lookup"><span data-stu-id="a1955-122">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="a1955-123">次のコードでは、<xref:System.Text.StringBuilder> クラスの <xref:System.Text.StringBuilder.Append%2A> メソッドを使用して文字列を連結しています。</span><span class="sxs-lookup"><span data-stu-id="a1955-123">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="a1955-124">[文字列の連結または `StringBuilder` クラスを選択する理由](xref:System.Text.StringBuilder#StringAndSB)に関するページで詳細をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="a1955-124">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB)</span></span>

<span data-ttu-id="a1955-125">コレクションからの文字列を結合する別のオプションとして、[LINQ](../programming-guide/concepts/linq/index.md) および <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> メソッドを使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="a1955-125">Another option to join strings from a collection is to use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a1955-126">このメソッドは、ラムダ式を使用してソース文字列を結合します。</span><span class="sxs-lookup"><span data-stu-id="a1955-126">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="a1955-127">ラムダ式は、各文字列を既存の蓄積に追加する処理を行います。</span><span class="sxs-lookup"><span data-stu-id="a1955-127">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="a1955-128">次の例では、配列内の各単語の間にスペースを追加することによって単語の配列を結合します。</span><span class="sxs-lookup"><span data-stu-id="a1955-128">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]  


## <a name="see-also"></a><span data-ttu-id="a1955-129">参照</span><span class="sxs-lookup"><span data-stu-id="a1955-129">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="a1955-130">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a1955-130">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="a1955-131">文字列</span><span class="sxs-lookup"><span data-stu-id="a1955-131">Strings</span></span>](../programming-guide/strings/index.md)
