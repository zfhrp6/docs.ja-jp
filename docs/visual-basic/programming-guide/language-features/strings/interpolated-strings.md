---
title: 補間文字列 (Visual Basic)
ms.date: 10/31/2017
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95f79c5cdff1a48da2bb0eaf92229570ced631b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653560"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="34cef-102">補間文字列 (Visual Basic リファレンス)</span><span class="sxs-lookup"><span data-stu-id="34cef-102">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="34cef-103">文字列の作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="34cef-103">Used to construct strings.</span></span>  <span data-ttu-id="34cef-104">挿入文字列は、*挿入式*が含まれているテンプレート文字列のように見えます。</span><span class="sxs-lookup"><span data-stu-id="34cef-104">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="34cef-105">挿入文字列は、含まれる挿入式をその文字列表現に置き換えた文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="34cef-105">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="34cef-106">この機能は、Visual Basic 14 およびそれ以降のバージョンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="34cef-106">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="34cef-107">挿入文字列の引数は、[複合書式指定文字列](../../../../standard/base-types/composite-formatting.md#composite-format-string)よりもわかりやすいものです。</span><span class="sxs-lookup"><span data-stu-id="34cef-107">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="34cef-108">たとえば、挿入文字列には、</span><span class="sxs-lookup"><span data-stu-id="34cef-108">For example, the interpolated string</span></span>  
  
```vb  
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```  
<span data-ttu-id="34cef-109">2 つの挿入式、"{name}" と "{hours:hh}" が含まれています。</span><span class="sxs-lookup"><span data-stu-id="34cef-109">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="34cef-110">同等の複合書式指定文字列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="34cef-110">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours); 
```  

<span data-ttu-id="34cef-111">挿入文字列の構造は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="34cef-111">The structure of an interpolated string is:</span></span>  
  
```vb  
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."  
```  

<span data-ttu-id="34cef-112">ここで、</span><span class="sxs-lookup"><span data-stu-id="34cef-112">where:</span></span> 

- <span data-ttu-id="34cef-113">*field-width* はフィールドの文字数を示す符号付き整数です。</span><span class="sxs-lookup"><span data-stu-id="34cef-113">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="34cef-114">これが正である場合、フィールドは右揃えとなり、負である場合は左揃えとなります。</span><span class="sxs-lookup"><span data-stu-id="34cef-114">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span> 

- <span data-ttu-id="34cef-115">*format-string* は、書式設定されるオブジェクトの種類に適した書式指定文字列です。</span><span class="sxs-lookup"><span data-stu-id="34cef-115">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="34cef-116">たとえば、<xref:System.DateTime>値である可能性があります、[標準の日時書式指定文字列](~/docs/standard/base-types/standard-date-and-time-format-strings.md)"D"または"d"などです。</span><span class="sxs-lookup"><span data-stu-id="34cef-116">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](~/docs/standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34cef-117">`$` と文字列を開始する `"` の間に空白を入れることはできません。</span><span class="sxs-lookup"><span data-stu-id="34cef-117">You cannot have any whitespace between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="34cef-118">これにより、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="34cef-118">Doing so causes a compiler error.</span></span>

 <span data-ttu-id="34cef-119">文字列リテラルを使用できる場所であればどこでも補間文字列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="34cef-119">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="34cef-120">この挿入文字列は、挿入文字列を含むコードが実行されるたびに評価されます。</span><span class="sxs-lookup"><span data-stu-id="34cef-120">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="34cef-121">これにより、挿入文字列の定義と評価を分離することができます。</span><span class="sxs-lookup"><span data-stu-id="34cef-121">This allows you to separate the definition and evaluation of an interpolated string.</span></span>  
  
 <span data-ttu-id="34cef-122">挿入文字列に中かっこ "{" または "}" を含めるには、2 つの中かっこ "{{" または "}}" を使用します。</span><span class="sxs-lookup"><span data-stu-id="34cef-122">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="34cef-123">詳細については、「暗黙の型変換」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34cef-123">See the Implicit Conversions section for more details.</span></span>  

<span data-ttu-id="34cef-124">挿入文字列には、引用符 (")、コロン (:)、コンマ (,) など、特別な意味を持つその他の文字が含まれることがあります。これらの文字がリテラル テキストに出現する場合は、エスケープする必要があります。また、これらの文字が言語要素として挿入式に含まれる場合は、かっこで区切られた式に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="34cef-124">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="34cef-125">次の例では、引用符をエスケープして、結果文字列に引用符を含めています。さらに、かっこを使用して式 `(age == 1 ? "" : "s")` を区切り、コロンが書式指定文字列の先頭として解釈されないようにしています。</span><span class="sxs-lookup"><span data-stu-id="34cef-125">The following example escapes quotation marks to include them in the result string, and it uses parentheses to delimit the expression `(age == 1 ? "" : "s")` so that the colon is not interpreted as beginning a format string.</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]  

## <a name="implicit-conversions"></a><span data-ttu-id="34cef-126">暗黙の型変換</span><span class="sxs-lookup"><span data-stu-id="34cef-126">Implicit Conversions</span></span>  

<span data-ttu-id="34cef-127">挿入文字列から暗黙の型変換を行う方法は 3 種類あります。</span><span class="sxs-lookup"><span data-stu-id="34cef-127">There are three implicit type conversions from an interpolated string:</span></span>  

1. <span data-ttu-id="34cef-128">挿入文字列から <xref:System.String> への変換。</span><span class="sxs-lookup"><span data-stu-id="34cef-128">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="34cef-129">次の例では、挿入文字列式を文字列表現で置き換えた文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="34cef-129">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="34cef-130">例えば:</span><span class="sxs-lookup"><span data-stu-id="34cef-130">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]  

   <span data-ttu-id="34cef-131">これが、文字列解釈の最終的な結果です。</span><span class="sxs-lookup"><span data-stu-id="34cef-131">This is the final result of a string interpretation.</span></span> <span data-ttu-id="34cef-132">二重中かっこ ("{{" および "}}") のすべての発生箇所は、単一の中かっこに変換されます。</span><span class="sxs-lookup"><span data-stu-id="34cef-132">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span> 

2. <span data-ttu-id="34cef-133">挿入文字列から <xref:System.IFormattable> 変数への変換。これは、単一の <xref:System.IFormattable> インスタンスから、カルチャ固有のコンテンツを持った複数の結果文字列の作成を可能にするものです。</span><span class="sxs-lookup"><span data-stu-id="34cef-133">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="34cef-134">これは、個々のカルチャに適切な数値書式や日付形式などの情報を含めるのに便利です。</span><span class="sxs-lookup"><span data-stu-id="34cef-134">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="34cef-135">二重中かっこ ("{{" および "}}") のすべての出現箇所は、明示的または暗黙的に <xref:System.Object.ToString> メソッドを呼び出して文字列を書式指定するまで、二重中かっこのままです。</span><span class="sxs-lookup"><span data-stu-id="34cef-135">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="34cef-136">すべての含まれる補間式に変換する{0}、{1}のようにします。</span><span class="sxs-lookup"><span data-stu-id="34cef-136">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   <span data-ttu-id="34cef-137">次の例では、リフレクションを使用することで、挿入文字列から作成された <xref:System.IFormattable> 変数のフィールドおよびプロパティ値だけでなく、メンバーも表示しています。</span><span class="sxs-lookup"><span data-stu-id="34cef-137">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="34cef-138">また、<xref:System.IFormattable> 変数を <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> メソッドに渡しています。</span><span class="sxs-lookup"><span data-stu-id="34cef-138">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]  

   <span data-ttu-id="34cef-139">挿入文字列の検査には、リフレクションを使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="34cef-139">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="34cef-140">挿入文字列が <xref:System.Console.WriteLine(System.String)> などの文字列書式指定メソッドに渡されると、書式指定項目が解決され、結果文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="34cef-140">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span> 

3. <span data-ttu-id="34cef-141">補間文字列からへの変換、<xref:System.FormattableString>複合書式指定文字列を表す変数です。</span><span class="sxs-lookup"><span data-stu-id="34cef-141">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="34cef-142">たとえば、複合書式指定文字列を検査し、それが結果文字列としてどのように表示されるかを検査すると、クエリを構築する場合にインジェクション攻撃を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="34cef-142">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="34cef-143">A<xref:System.FormattableString>も含まれています。</span><span class="sxs-lookup"><span data-stu-id="34cef-143">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="34cef-144"><xref:System.Globalization.CultureInfo.CurrentCulture> の結果文字列を生成する <xref:System.FormattableString.ToString> オーバーロード。</span><span class="sxs-lookup"><span data-stu-id="34cef-144">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      
      - <span data-ttu-id="34cef-145">A<xref:System.FormattableString.Invariant%2A>の文字列を生成するメソッド、<xref:System.Globalization.CultureInfo.InvariantCulture>です。</span><span class="sxs-lookup"><span data-stu-id="34cef-145">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      
      - <span data-ttu-id="34cef-146">特定のカルチャの結果文字列を生成する <xref:System.FormattableString.ToString(System.IFormatProvider)> メソッド。</span><span class="sxs-lookup"><span data-stu-id="34cef-146">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span> 
  
    <span data-ttu-id="34cef-147">二重中かっこのすべての出現 ("{{"と"}}") 書式指定するまで二重中かっこのままです。</span><span class="sxs-lookup"><span data-stu-id="34cef-147">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="34cef-148">すべての含まれる補間式に変換する{0}、{1}のようにします。</span><span class="sxs-lookup"><span data-stu-id="34cef-148">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>  

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]  

## <a name="see-also"></a><span data-ttu-id="34cef-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="34cef-149">See Also</span></span>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 [<span data-ttu-id="34cef-150">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="34cef-150">Visual Basic Language Reference</span></span>](index.md)  
 