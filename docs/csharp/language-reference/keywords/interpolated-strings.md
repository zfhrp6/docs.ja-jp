---
title: "挿入文字列 (C#)"
ms.date: 10/18/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 324f267e-1c61-431a-97ed-852c1530742d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0569636bde875d2d0d8921a544273f3214d05188
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2018
---
# <a name="interpolated-strings-c-reference"></a><span data-ttu-id="8dc7e-102">挿入文字列 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8dc7e-102">Interpolated Strings (C# Reference)</span></span>

<span data-ttu-id="8dc7e-103">文字列の作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-103">Used to construct strings.</span></span>  <span data-ttu-id="8dc7e-104">挿入文字列は、*挿入式*が含まれているテンプレート文字列のように見えます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="8dc7e-105">挿入文字列は、含まれる挿入式をその文字列表現に置き換えた文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="8dc7e-106">この機能は C# 6 以降のバージョンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-106">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="8dc7e-107">挿入文字列の引数は、[複合書式指定文字列](../../../standard/base-types/composite-formatting.md#composite-format-string)よりもわかりやすいものです。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="8dc7e-108">たとえば、挿入文字列には、</span><span class="sxs-lookup"><span data-stu-id="8dc7e-108">For example, the interpolated string</span></span>  
  
```csharp  
Console.WriteLine($"Name = {name}, hours = {hours:hh}");
```  
<span data-ttu-id="8dc7e-109">2 つの挿入式、"{name}" と "{hours:hh}" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="8dc7e-110">同等の複合書式指定文字列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-110">The equivalent composite format string is:</span></span>

```csharp
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="8dc7e-111">挿入文字列の構造は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-111">The structure of an interpolated string is:</span></span>  
  
```  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="8dc7e-112">ここで、</span><span class="sxs-lookup"><span data-stu-id="8dc7e-112">where:</span></span> 

- <span data-ttu-id="8dc7e-113">*field-width* はフィールドの文字数を示す符号付き整数です。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="8dc7e-114">これが正である場合、フィールドは右揃えとなり、負である場合は左揃えとなります。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="8dc7e-115">*format-string* は、書式設定されるオブジェクトの種類に適した書式指定文字列です。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="8dc7e-116">たとえば、<xref:System.DateTime> の値の場合、"D" または "d" などの、標準の日付と時刻の書式指定文字列になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-116">For example, for a <xref:System.DateTime> value, it could be a standard date and time format string such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8dc7e-117">`$` と文字列を開始する `"` の間に空白を入れることはできません。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="8dc7e-118">空白を入れると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-118">Doing so causes a compile time error.</span></span>

 <span data-ttu-id="8dc7e-119">文字列リテラルを使用できる場所であればどこでも補間文字列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="8dc7e-120">この挿入文字列は、挿入文字列を含むコードが実行されるたびに評価されます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="8dc7e-121">これにより、挿入文字列の定義と評価を分離することができます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="8dc7e-122">挿入文字列に中かっこ "{" または "}" を含めるには、2 つの中かっこ "{{" または "}}" を使用します。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="8dc7e-123">詳細については、「暗黙の型変換」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="8dc7e-124">挿入文字列には、引用符 (")、コロン (:)、コンマ (,) など、特別な意味を持つその他の文字が含まれることがあります。これらの文字がリテラル テキストに出現する場合は、エスケープする必要があります。また、これらの文字が言語要素として挿入式に含まれる場合は、かっこで区切られた式に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="8dc7e-125">次の例では、引用符をエスケープして、結果文字列に引用符を含めています。さらに、かっこを使用して式 `(age == 1 ? "" : "s")` を区切り、コロンが書式指定文字列の先頭として解釈されないようにしています。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings4.cs#1)]  

<span data-ttu-id="8dc7e-126">逐語的挿入文字列では、後に `@` 文字が続く `$` 文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-126">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="8dc7e-127">逐語的文字列の詳細については、[string](string.md) に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-127">For more information about verbatim strings, see the [string](string.md) topic.</span></span> <span data-ttu-id="8dc7e-128">次のコードは、逐語的挿入文字列を使用する前述のスニペットを変更したものです。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-128">The following code is a modified version of the previous snippet using a verbatim interpolated string:</span></span>

[!code-csharp[interpolated-strings4](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings5.cs#1)]  

<span data-ttu-id="8dc7e-129">逐語的文字列が `\` エスケープ シーケンスに従っていないため、書式設定の変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-129">The formatting changes are necessary because verbatim strings do not obey `\` escape sequences.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8dc7e-130">`$` トークンは、逐語的挿入文字列の `@` トークンの前に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-130">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>


## <a name="implicit-conversions"></a><span data-ttu-id="8dc7e-131">暗黙の型変換</span><span class="sxs-lookup"><span data-stu-id="8dc7e-131">Implicit Conversions</span></span>  

<span data-ttu-id="8dc7e-132">挿入文字列から暗黙の型変換を行う方法は 3 種類あります。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-132">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="8dc7e-133">挿入文字列から <xref:System.String> への変換。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-133">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="8dc7e-134">次の例では、挿入文字列式を文字列表現で置き換えた文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-134">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="8dc7e-135">例:</span><span class="sxs-lookup"><span data-stu-id="8dc7e-135">For example:</span></span>

   [!code-csharp[interpolated-strings1](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings1.cs#1)]  

   <span data-ttu-id="8dc7e-136">これが、文字列解釈の最終的な結果です。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-136">This is the final result of a string interpretation.</span></span> <span data-ttu-id="8dc7e-137">二重中かっこ ("{{" および "}}") のすべての発生箇所は、単一の中かっこに変換されます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-137">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="8dc7e-138">挿入文字列から <xref:System.IFormattable> 変数への変換。これは、単一の <xref:System.IFormattable> インスタンスから、カルチャ固有のコンテンツを持った複数の結果文字列の作成を可能にするものです。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-138">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="8dc7e-139">これは、個々のカルチャに適切な数値書式や日付形式などの情報を含めるのに便利です。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-139">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="8dc7e-140">二重中かっこ ("{{" および "}}") のすべての出現箇所は、明示的または暗黙的に <xref:System.Object.ToString> メソッドを呼び出して文字列を書式指定するまで、二重中かっこのままです。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-140">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="8dc7e-141">含まれるすべての補間式は、{0}、\{1\} などに変換されます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-141">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="8dc7e-142">次の例では、リフレクションを使用することで、挿入文字列から作成された <xref:System.IFormattable> 変数のフィールドおよびプロパティ値だけでなく、メンバーも表示しています。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-142">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="8dc7e-143">また、<xref:System.IFormattable> 変数を <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> メソッドに渡しています。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-143">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-csharp[interpolated-strings2](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings2.cs#1)]  

   <span data-ttu-id="8dc7e-144">挿入文字列の検査には、リフレクションを使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-144">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="8dc7e-145">挿入文字列が <xref:System.Console.WriteLine(System.String)> などの文字列書式指定メソッドに渡されると、書式指定項目が解決され、結果文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-145">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="8dc7e-146">挿入文字列から複合書式指定文字列を表す <xref:System.FormattableString> 変数への変換。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-146">Conversion of an interpolated string to an <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="8dc7e-147">たとえば、複合書式指定文字列を検査し、それが結果文字列としてどのように表示されるかを検査すると、クエリを構築する場合にインジェクション攻撃を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-147">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="8dc7e-148"><xref:System.FormattableString> には、<xref:System.Globalization.CultureInfo.InvariantCulture> と <xref:System.Globalization.CultureInfo.CurrentCulture> の結果文字列を生成できる <xref:System.FormattableString.ToString> オーバーロードも含まれています。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-148"><xref:System.FormattableString> also includes <xref:System.FormattableString.ToString> overloads that let you produce result strings for the <xref:System.Globalization.CultureInfo.InvariantCulture> and <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>  <span data-ttu-id="8dc7e-149">二重中かっこ ("{{" および "}}") のすべての出現箇所は、書式指定するまで二重中かっこのままです。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-149">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces, until you format.</span></span>  <span data-ttu-id="8dc7e-150">含まれるすべての補間式は、{0}、\{1\} などに変換されます。</span><span class="sxs-lookup"><span data-stu-id="8dc7e-150">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-csharp[interpolated-strings3](../../../../samples/snippets/csharp/language-reference/keywords/interpolated-strings3.cs#1)]  

## <a name="language-specification"></a><span data-ttu-id="8dc7e-151">言語仕様</span><span class="sxs-lookup"><span data-stu-id="8dc7e-151">Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8dc7e-152">参照</span><span class="sxs-lookup"><span data-stu-id="8dc7e-152">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="8dc7e-153">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="8dc7e-153">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8dc7e-154">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="8dc7e-154">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
