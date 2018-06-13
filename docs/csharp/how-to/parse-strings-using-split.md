---
title: '方法: String.Split を使用して文字列を解析する (C# ガイド)'
description: String.Split は、一連の区切り記号で分割された文字列の配列を返します。 文字列を解析する簡単な方法です。
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: e2d788b27f54ac068922f0ebe558a2aea8a475ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212343"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a><span data-ttu-id="37ef5-104">方法: String.Split を使用して文字列を解析する (C# ガイド)</span><span class="sxs-lookup"><span data-stu-id="37ef5-104">How to: Parse Strings Using String.Split (C# Guide)</span></span>

<span data-ttu-id="37ef5-105"><xref:System.String.Split%2A?displayProperty=nameWithType> メソッドは、1 つまたは複数の区切り記号に基づいて入力文字列を分割することで部分文字列の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="37ef5-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="37ef5-106">多くの場合、単語の境界で文字列を分割する最も簡単な方法になります。</span><span class="sxs-lookup"><span data-stu-id="37ef5-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="37ef5-107">他の特定の文字や文字列で文字列を分割する際にも利用されます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="37ef5-108">次のコードは一般的なフレーズを単語ごとの文字列の配列に分割します。</span><span class="sxs-lookup"><span data-stu-id="37ef5-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="37ef5-109">区切り文字のインスタンスごとに、返される配列で値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="37ef5-110">連続する区切り文字により、返される配列の値として空の文字列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span>  <span data-ttu-id="37ef5-111">次の例でこれを確認できます。次の例では区切り文字としてスペースが使用されています。</span><span class="sxs-lookup"><span data-stu-id="37ef5-111">You can see this in the following example, which uses space as a separator:</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="37ef5-112">この動作により、コンマ区切り値 (CSV) ファイルなどの形式で表形式データを簡単に表すことができます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-112">This behavior makes it easier for formats like comma separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="37ef5-113">連続するコンマは空の列を表します。</span><span class="sxs-lookup"><span data-stu-id="37ef5-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="37ef5-114">任意の <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> パラメーターを渡し、返される配列で空の文字列を除外できます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="37ef5-115">返されるコレクションの処理が複雑な場合、[LINQ](../programming-guide/concepts/linq/index.md) を使用し、結果のシーケンスを操作できます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>    

<span data-ttu-id="37ef5-116"><xref:System.String.Split%2A?displayProperty=nameWithType> では、複数の区切り文字を使用できます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span> <span data-ttu-id="37ef5-117">次の例ではスペース、コンマ、ピリオド、コロン、タブを使用しています。すべて、これらの区切り文字を格納した配列で <xref:System.String.Split%2A> に渡されます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="37ef5-118">コードの一番下にあるループは、返される配列の各単語を表示します。</span><span class="sxs-lookup"><span data-stu-id="37ef5-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="37ef5-119">区切りの連続するインスタンスにより、出力配列で空の文字列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="37ef5-120"><xref:System.String.Split%2A?displayProperty=nameWithType> は、文字列の配列 (1 つの文字ではなく、対象の文字列を解析するための区切り記号として機能する文字シーケンス) を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="37ef5-121">[GitHub リポジトリ](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)のコードを見て、これらのサンプルを試すことができます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="37ef5-122">または、サンプルを [zip ファイルとして](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)ダウンロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="37ef5-122">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="37ef5-123">参照</span><span class="sxs-lookup"><span data-stu-id="37ef5-123">See Also</span></span>  
 [<span data-ttu-id="37ef5-124">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="37ef5-124">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="37ef5-125">文字列</span><span class="sxs-lookup"><span data-stu-id="37ef5-125">Strings</span></span>](../programming-guide/strings/index.md)  
 [<span data-ttu-id="37ef5-126">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="37ef5-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
