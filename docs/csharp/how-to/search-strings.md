---
title: '方法: 文字列を検索する (C# ガイド)'
ms.date: 02/21/2018
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with String methods
- strings [C#], searching with regular expressions
ms.assetid: fb1d9a6d-598d-4a35-bd5f-b86012edcb2b
ms.openlocfilehash: d1e132093cc59c7b41a3f7d5b522fca2e224f779
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219041"
---
# <a name="how-to-search-strings"></a><span data-ttu-id="ee380-102">方法: 文字列を検索する</span><span class="sxs-lookup"><span data-stu-id="ee380-102">How to: search strings</span></span>

<span data-ttu-id="ee380-103">2 つの主な戦略を使用して、文字列のテキストを検索することができます。</span><span class="sxs-lookup"><span data-stu-id="ee380-103">You can use two main strategies to search for text in strings.</span></span> <span data-ttu-id="ee380-104"><xref:System.String> クラスのメソッドは特定のテキストを検索します。</span><span class="sxs-lookup"><span data-stu-id="ee380-104">Methods of the <xref:System.String> class search for specific text.</span></span> <span data-ttu-id="ee380-105">正規表現はテキストのパターンを検索します。</span><span class="sxs-lookup"><span data-stu-id="ee380-105">Regular expressions search for patterns in text.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="ee380-106">[string](../language-reference/keywords/string.md) 型は、<xref:System.String?displayProperty=nameWithType> クラスのエイリアスであり、文字列の内容を検索するための多数の便利なメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee380-106">The [string](../language-reference/keywords/string.md) type, which is an alias for the <xref:System.String?displayProperty=nameWithType> class, provides a number of useful methods for searching the contents of a string.</span></span> <span data-ttu-id="ee380-107">その中に <xref:System.String.Contains%2A>、<xref:System.String.StartsWith%2A>、<xref:System.String.EndsWith%2A>、<xref:System.String.IndexOf%2A>、<xref:System.String.LastIndexOf%2A> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee380-107">Among them are <xref:System.String.Contains%2A>, <xref:System.String.StartsWith%2A>, <xref:System.String.EndsWith%2A>, <xref:System.String.IndexOf%2A>, <xref:System.String.LastIndexOf%2A>.</span></span> <span data-ttu-id="ee380-108"><xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> クラスでは、テキストのパターンを検索するための豊富なボキャブラリが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ee380-108">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class provides a rich vocabulary to search for patterns in text.</span></span> <span data-ttu-id="ee380-109">この記事では、これらの手法と、ニーズに最適なメソッドを選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee380-109">In this article, you learn these techniques and how to choose the best method for your needs.</span></span>

## <a name="does-a-string-contain-text"></a><span data-ttu-id="ee380-110">文字列にテキストが含まれていますか?</span><span class="sxs-lookup"><span data-stu-id="ee380-110">Does a string contain text?</span></span>

<span data-ttu-id="ee380-111"><xref:System.String.Contains%2A?displayProperty=nameWithType>、<xref:System.String.StartsWith%2A?displayProperty=nameWithType> および <xref:System.String.EndsWith%2A?displayProperty=nameWithType>メソッドでは、特定のテキストの文字列を検索します。</span><span class="sxs-lookup"><span data-stu-id="ee380-111">The <xref:System.String.Contains%2A?displayProperty=nameWithType>, <xref:System.String.StartsWith%2A?displayProperty=nameWithType> and <xref:System.String.EndsWith%2A?displayProperty=nameWithType> methods search a string for specific text.</span></span> <span data-ttu-id="ee380-112">次の例は、これらの各メソッドと、大文字と小文字を区別しない検索を使用するバリエーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="ee380-112">The following example shows each of these methods and a variation that uses a case insensitive search:</span></span>

[!code-csharp-interactive[search strings using methods](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#1)]

<span data-ttu-id="ee380-113">上の例は、これらのメソッドを使用する重要なポイントを示しています。</span><span class="sxs-lookup"><span data-stu-id="ee380-113">The preceding example demonstrates an important point for using these methods.</span></span> <span data-ttu-id="ee380-114">既定では、検索で**大文字と小文字が区別**されます。</span><span class="sxs-lookup"><span data-stu-id="ee380-114">Searches are **case-sensitive** by default.</span></span> <span data-ttu-id="ee380-115">大文字と小文字を区別しない検索を指定する場合は、<xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> 列挙値を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee380-115">You use the <xref:System.StringComparison.CurrentCultureIgnoreCase?displayProperty=nameWithType> enum value to specify a case insensitive search.</span></span>

## <a name="where-does-the-sought-text-occur-in-a-string"></a><span data-ttu-id="ee380-116">検索対象テキストは文字列のどこにありますか?</span><span class="sxs-lookup"><span data-stu-id="ee380-116">Where does the sought text occur in a string?</span></span>

<span data-ttu-id="ee380-117"><xref:System.String.IndexOf%2A> および <xref:System.String.LastIndexOf%2A> メソッドでは、文字列のテキストも検索します。</span><span class="sxs-lookup"><span data-stu-id="ee380-117">The <xref:System.String.IndexOf%2A> and <xref:System.String.LastIndexOf%2A> methods also search for text in strings.</span></span> <span data-ttu-id="ee380-118">これらのメソッドは、検索されるテキストの場所を返します。</span><span class="sxs-lookup"><span data-stu-id="ee380-118">These methods return the location of the text being sought.</span></span> <span data-ttu-id="ee380-119">テキストが見つからない場合は、`-1` が返されます。</span><span class="sxs-lookup"><span data-stu-id="ee380-119">If the text isn't found, they return `-1`.</span></span> <span data-ttu-id="ee380-120">次の例では、"methods" という単語の最初と最後の出現箇所の検索を示し、その間のテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="ee380-120">The following example shows a search for the first and last occurrence of the word "methods" and displays the text in between.</span></span>
  
[!code-csharp-interactive[search strings for indices](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#2)]

## <a name="finding-specific-text-using-regular-expressions"></a><span data-ttu-id="ee380-121">正規表現を使用する特定のテキストの検索</span><span class="sxs-lookup"><span data-stu-id="ee380-121">Finding specific text using regular expressions</span></span>

<span data-ttu-id="ee380-122">文字列の検索には、<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee380-122">The <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> class can be used to search strings.</span></span> <span data-ttu-id="ee380-123">これらの検索の複雑さは、単純なテキスト パターンから複雑なテキスト パターンまでさまざまです。</span><span class="sxs-lookup"><span data-stu-id="ee380-123">These searches can range in complexity from simple to complicated text patterns.</span></span>

<span data-ttu-id="ee380-124">次のコード例では、文章内の "the" または "their" という単語を検索します (大文字と小文字の区別は無視されます)。</span><span class="sxs-lookup"><span data-stu-id="ee380-124">The following code example searches for the word "the" or "their" in a sentence, ignoring case.</span></span> <span data-ttu-id="ee380-125">静的メソッドの <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> で検索を実行します。</span><span class="sxs-lookup"><span data-stu-id="ee380-125">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> performs the search.</span></span> <span data-ttu-id="ee380-126">検索対象の文字列と、検索パターンを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee380-126">You give it the string to search and a search pattern.</span></span> <span data-ttu-id="ee380-127">この例では、3 番目の引数で大文字と小文字を区別しない検索を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee380-127">In this case, a third argument specifies case-insensitive search.</span></span> <span data-ttu-id="ee380-128">詳細については、「<xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee380-128">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.</span></span>  

<span data-ttu-id="ee380-129">検索パターンで検索対象のテキストを説明します。</span><span class="sxs-lookup"><span data-stu-id="ee380-129">The search pattern describes the text you search for.</span></span> <span data-ttu-id="ee380-130">次の表では、検索パターンの各要素について説明します </span><span class="sxs-lookup"><span data-stu-id="ee380-130">The following table describes each element of the search pattern.</span></span> <span data-ttu-id="ee380-131">(以下の表では、C# 文字列で `\\` としてエスケープされる必要がある、単一の `\` を使用します)。</span><span class="sxs-lookup"><span data-stu-id="ee380-131">(The table below uses the single `\` which must be escaped as `\\` in a C# string).</span></span>

| <span data-ttu-id="ee380-132">pattern</span><span class="sxs-lookup"><span data-stu-id="ee380-132">pattern</span></span>  | <span data-ttu-id="ee380-133">説明</span><span class="sxs-lookup"><span data-stu-id="ee380-133">Meaning</span></span>     |
| -------- |-------------|
| <span data-ttu-id="ee380-134">the</span><span class="sxs-lookup"><span data-stu-id="ee380-134">the</span></span>      | <span data-ttu-id="ee380-135">テキスト "the" と一致</span><span class="sxs-lookup"><span data-stu-id="ee380-135">match the text "the"</span></span> |
| <span data-ttu-id="ee380-136">(eir)?</span><span class="sxs-lookup"><span data-stu-id="ee380-136">(eir)?</span></span>   | <span data-ttu-id="ee380-137">"eir" の 0 個または 1 個の出現箇所と一致</span><span class="sxs-lookup"><span data-stu-id="ee380-137">match 0 or 1 occurence of "eir"</span></span> |
| <span data-ttu-id="ee380-138">\s</span><span class="sxs-lookup"><span data-stu-id="ee380-138">\s</span></span>       | <span data-ttu-id="ee380-139">空白文字と一致</span><span class="sxs-lookup"><span data-stu-id="ee380-139">match a white-space character</span></span>    |
  
[!code-csharp-interactive[Search using regular expressions](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#3)]
  
> [!TIP]
> <span data-ttu-id="ee380-140">`string` メソッドは、通常、正確な文字列を検索するときに選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ee380-140">The `string` methods are usually better choices when you are searching for an exact string.</span></span> <span data-ttu-id="ee380-141">正規表現は、ソース文字列でいくつかのパターンを検索する場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="ee380-141">Regular expressions are better when you are searching for some pattern is a source string.</span></span>

## <a name="does-a-string-follow-a-pattern"></a><span data-ttu-id="ee380-142">文字列はパターンに従っていますか?</span><span class="sxs-lookup"><span data-stu-id="ee380-142">Does a string follow a pattern?</span></span>

<span data-ttu-id="ee380-143">次のコードでは正規表現を使用して、配列の各文字列の形式を検証します。</span><span class="sxs-lookup"><span data-stu-id="ee380-143">The following code uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="ee380-144">各文字列が電話番号の形式であることが検証されます。つまり、3 グループの数値がダッシュで区切られ、最初の 2 グループには 3 桁の数値が含まれ、3 つ目のグループには 4 桁の数値が含まれることが検証されます。</span><span class="sxs-lookup"><span data-stu-id="ee380-144">The validation requires that each string have the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="ee380-145">検索パターンでは正規表現の `^\\d{3}-\\d{3}-\\d{4}$` を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee380-145">The search pattern uses the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="ee380-146">詳細については、「[正規表現言語 - クイック リファレンス](../../standard/base-types/regular-expression-language-quick-reference.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee380-146">For more information, see [Regular Expression Language - Quick Reference](../../standard/base-types/regular-expression-language-quick-reference.md).</span></span>

| <span data-ttu-id="ee380-147">pattern</span><span class="sxs-lookup"><span data-stu-id="ee380-147">pattern</span></span>  | <span data-ttu-id="ee380-148">説明</span><span class="sxs-lookup"><span data-stu-id="ee380-148">Meaning</span></span>                             |
| -------- |-------------------------------------|
| ^        | <span data-ttu-id="ee380-149">文字列の先頭と一致</span><span class="sxs-lookup"><span data-stu-id="ee380-149">matches the beginning of the string</span></span> |
| <span data-ttu-id="ee380-150">\d{3}</span><span class="sxs-lookup"><span data-stu-id="ee380-150">\d{3}</span></span>    | <span data-ttu-id="ee380-151">3 桁の文字と完全に一致</span><span class="sxs-lookup"><span data-stu-id="ee380-151">matches exactly 3 digit characters</span></span>  |
| -        | <span data-ttu-id="ee380-152">'-' 文字と一致</span><span class="sxs-lookup"><span data-stu-id="ee380-152">matches the '-' character</span></span>           |
| <span data-ttu-id="ee380-153">\d{3}</span><span class="sxs-lookup"><span data-stu-id="ee380-153">\d{3}</span></span>    | <span data-ttu-id="ee380-154">3 桁の文字と完全に一致</span><span class="sxs-lookup"><span data-stu-id="ee380-154">matches exactly 3 digit characters</span></span>  |
| -        | <span data-ttu-id="ee380-155">'-' 文字と一致</span><span class="sxs-lookup"><span data-stu-id="ee380-155">matches the '-' character</span></span>           |
| <span data-ttu-id="ee380-156">\d{4}</span><span class="sxs-lookup"><span data-stu-id="ee380-156">\d{4}</span></span>    | <span data-ttu-id="ee380-157">4 桁の文字と完全に一致</span><span class="sxs-lookup"><span data-stu-id="ee380-157">matches exactly 4 digit characters</span></span>  |
| $        | <span data-ttu-id="ee380-158">文字列の末尾と一致</span><span class="sxs-lookup"><span data-stu-id="ee380-158">matches the end of the string</span></span>       |


[!code-csharp-interactive[csProgGuideStrings#4](../../../samples/snippets/csharp/how-to/strings/SearchStrings.cs#4)]

<span data-ttu-id="ee380-159">この単一の検索パターンは多くの有効な文字列と一致します。</span><span class="sxs-lookup"><span data-stu-id="ee380-159">This single search pattern matches many valid strings.</span></span> <span data-ttu-id="ee380-160">単一のテキスト文字列ではなく、パターンの検索やパターンに対する検証を行う場合は、正規表現が適しています。</span><span class="sxs-lookup"><span data-stu-id="ee380-160">Regular expressions are better to search for or validate against a pattern, rather than a single text string.</span></span>

<span data-ttu-id="ee380-161">[GitHub リポジトリ](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)のコードを見て、これらのサンプルを試すことができます。</span><span class="sxs-lookup"><span data-stu-id="ee380-161">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="ee380-162">または、サンプルを [zip ファイルとして](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)ダウンロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="ee380-162">Or you can download the samples [as a zip file](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee380-163">参照</span><span class="sxs-lookup"><span data-stu-id="ee380-163">See Also</span></span>  

 [<span data-ttu-id="ee380-164">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ee380-164">C# Programming Guide</span></span>](../programming-guide/index.md)  
 [<span data-ttu-id="ee380-165">文字列</span><span class="sxs-lookup"><span data-stu-id="ee380-165">Strings</span></span>](../programming-guide/strings/index.md)  
 <span data-ttu-id="ee380-166">[LINQ と文字列](../programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="ee380-166">[LINQ and Strings](../programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>     
 <span data-ttu-id="ee380-167">[.NET Framework 正規表現](../../standard/base-types/regular-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="ee380-167">[.NET Framework Regular Expressions](../../standard/base-types/regular-expressions.md) </span></span>  
 <span data-ttu-id="ee380-168">[正規表現言語 - クイック リファレンス](../../standard/base-types/regular-expression-language-quick-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ee380-168">[Regular Expression Language - Quick Reference](../../standard/base-types/regular-expression-language-quick-reference.md) </span></span>  
 [<span data-ttu-id="ee380-169">.NET の文字列を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="ee380-169">Best practices for using strings in .NET</span></span>](../../standard/base-types/best-practices-strings.md)  
