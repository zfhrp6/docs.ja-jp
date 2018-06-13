---
title: $ - 文字列補間 (C# リファレンス)
description: 文字列補間では、従来の複合文字列の書式設定よりも読み取りやすく、便利な構文を書式指定文字列の出力に提供します。
ms.date: 03/26/2018
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 407ca9e4744ea9be45867a08e87c502821226472
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058837"
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="48591-103">$ - 文字列補間 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="48591-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="48591-104">`$` 特殊文字は、リテラル文字列を*挿入文字列*として識別します。</span><span class="sxs-lookup"><span data-stu-id="48591-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="48591-105">挿入文字列は、*挿入式*が含まれている可能性がある文字列リテラルです。</span><span class="sxs-lookup"><span data-stu-id="48591-105">An interpolated string is a string literal that might contain *interpolated expressions*.</span></span> <span data-ttu-id="48591-106">挿入文字列が結果文字列に解決されると、挿入式を含む項目は、式の結果の文字列表現によって置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="48591-106">When an interpolated string is resolved to a result string, items with interpolated expressions are replaced by the string representations of the expression results.</span></span> <span data-ttu-id="48591-107">この機能は C# 6 以降のバージョンの言語で使用できます。</span><span class="sxs-lookup"><span data-stu-id="48591-107">This feature is available in C# 6 and later versions of the language.</span></span>

<span data-ttu-id="48591-108">文字列補間では、[複合文字列の書式設定](../../../standard/base-types/composite-formatting.md)機能よりも読み取りやすく便利な構文を使用して書式指定された文字列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="48591-108">String interpolation provides a more readable and convenient syntax to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="48591-109">次の例では、両方の機能を使用して、同じ出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="48591-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a><span data-ttu-id="48591-110">挿入文字列の構造</span><span class="sxs-lookup"><span data-stu-id="48591-110">Structure of an interpolated string</span></span>

<span data-ttu-id="48591-111">文字列リテラルを挿入文字列として識別するため、先頭に `$` の記号を追加してください。</span><span class="sxs-lookup"><span data-stu-id="48591-111">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="48591-112">`$` と文字列リテラルを開始する `"` の間に空白を入れることはできません。</span><span class="sxs-lookup"><span data-stu-id="48591-112">You cannot have any white space between the `$` and the `"` that starts a string literal.</span></span> <span data-ttu-id="48591-113">空白を入れると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="48591-113">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="48591-114">挿入式を含む項目の構造は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="48591-114">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="48591-115">角かっこ内の要素は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="48591-115">Elements in square brackets are optional.</span></span> <span data-ttu-id="48591-116">次の表は、それぞれの要素の説明です。</span><span class="sxs-lookup"><span data-stu-id="48591-116">The following table describes each element:</span></span>

|<span data-ttu-id="48591-117">要素</span><span class="sxs-lookup"><span data-stu-id="48591-117">Element</span></span>|<span data-ttu-id="48591-118">説明</span><span class="sxs-lookup"><span data-stu-id="48591-118">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="48591-119">書式設定される結果を生成する式です。</span><span class="sxs-lookup"><span data-stu-id="48591-119">The expression that produces a result to be formatted.</span></span> <span data-ttu-id="48591-120">`null` 結果の文字列表現は、<xref:System.String.Empty?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="48591-120">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="48591-121">挿入式の結果の文字列表現で、最小文字数を定義する値を持つ定数式です。</span><span class="sxs-lookup"><span data-stu-id="48591-121">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="48591-122">正の場合は、文字列表現は右揃えで配置され、負の場合は、左揃えで配置されます。</span><span class="sxs-lookup"><span data-stu-id="48591-122">If positive, the string representation is right-aligned; if negative, it's left-aligned.</span></span> <span data-ttu-id="48591-123">詳細については、「[Alignment コンポーネント](../../../standard/base-types/composite-formatting.md#alignment-component)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48591-123">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="48591-124">式の結果の型によってサポートされる書式指定文字列です。</span><span class="sxs-lookup"><span data-stu-id="48591-124">A format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="48591-125">詳細については、「[Format String コンポーネント](../../../standard/base-types/composite-formatting.md#format-string-component)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48591-125">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="48591-126">次の例では、前述したオプションの書式設定コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="48591-126">The following example uses optional formatting components described above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a><span data-ttu-id="48591-127">特殊文字</span><span class="sxs-lookup"><span data-stu-id="48591-127">Special characters</span></span>

<span data-ttu-id="48591-128">挿入文字列で生成された文字列にかっこ "{" または "}" を含めるには、2 つのかっこ "{{" または "}}" を使用します。</span><span class="sxs-lookup"><span data-stu-id="48591-128">To include a brace, "{" or "}", in the text produced by an interpolated string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="48591-129">詳細については、「[エスケープ中かっこ ({})](../../../standard/base-types/composite-formatting.md#escaping-braces)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48591-129">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="48591-130">コロン (":") が挿入式の項目で特別な意味を持つときに、挿入式で[条件演算子](../operators/conditional-operator.md)を使用するには、その式を丸かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="48591-130">As the colon (":") has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="48591-131">次の例では、かっこを結果文字列に含める方法、および挿入式で条件演算子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="48591-131">The following example shows how to include a brace in a result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="48591-132">verbatim 挿入文字列は、`@` 文字が続く `$` 文字で始まります。</span><span class="sxs-lookup"><span data-stu-id="48591-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span> <span data-ttu-id="48591-133">逐語的文字列の詳細については、[string](../keywords/string.md) と [verbatim 識別子](verbatim.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48591-133">For more information about verbatim strings, see the [string](../keywords/string.md) and [verbatim identifier](verbatim.md) topics.</span></span>

> [!NOTE]
> <span data-ttu-id="48591-134">`$` トークンは、逐語的挿入文字列の `@` トークンの前に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="48591-134">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a><span data-ttu-id="48591-135">暗黙的な変換と `IFormatProvider` 実装の指定</span><span class="sxs-lookup"><span data-stu-id="48591-135">Implicit conversions and specifying `IFormatProvider` implementation</span></span>

<span data-ttu-id="48591-136">挿入文字列から暗黙の変換を行う方法は 3 種類あります。</span><span class="sxs-lookup"><span data-stu-id="48591-136">There are three implicit conversions from an interpolated string:</span></span>

1. <span data-ttu-id="48591-137">挿入文字列から <xref:System.String> インスタンスへの変換。これは、適切に書式設定された文字列表現の結果で置き換えられる、挿入式の項目を含む挿入文字列分析の結果です。</span><span class="sxs-lookup"><span data-stu-id="48591-137">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="48591-138">この変換では、現在のカルチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="48591-138">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="48591-139">書式設定される式の結果と、挿入文字列から複合書式指定文字列を表す <xref:System.FormattableString> インスタンスへの変換。</span><span class="sxs-lookup"><span data-stu-id="48591-139">Conversion of an interpolated string to a <xref:System.FormattableString> instance that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="48591-140">これは、単一の <xref:System.FormattableString> インスタンスから、カルチャ固有のコンテンツを持つ複数の結果文字列の作成を可能にするものです。</span><span class="sxs-lookup"><span data-stu-id="48591-140">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="48591-141">そのためには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="48591-141">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="48591-142"><xref:System.Globalization.CultureInfo.CurrentCulture> の結果文字列を生成する <xref:System.FormattableString.ToString> オーバーロード。</span><span class="sxs-lookup"><span data-stu-id="48591-142">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="48591-143"><xref:System.Globalization.CultureInfo.InvariantCulture> の結果文字列を生成する <xref:System.FormattableString.Invariant%2A> メソッド。</span><span class="sxs-lookup"><span data-stu-id="48591-143">An <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="48591-144">特定のカルチャの結果文字列を生成する <xref:System.FormattableString.ToString(System.IFormatProvider)> メソッド。</span><span class="sxs-lookup"><span data-stu-id="48591-144">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="48591-145"><xref:System.FormattableString.ToString(System.IFormatProvider)> メソッドを使用して、カスタム書式設定をサポートする <xref:System.IFormatProvider> インターフェイスのユーザー定義の実装を提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="48591-145">You also can use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to provide a user-defined implementation of the <xref:System.IFormatProvider> interface that supports custom formatting.</span></span> <span data-ttu-id="48591-146">詳細については、「[ICustomFormatter を使用したカスタム書式設定](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48591-146">For more information, see [Custom Formatting with ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).</span></span>

1. <span data-ttu-id="48591-147">挿入文字列から <xref:System.IFormattable> インスタンスへの変換。これは、単一の <xref:System.IFormattable> インスタンスから、カルチャ固有のコンテンツを持つ複数の結果文字列の作成も可能にするものです。</span><span class="sxs-lookup"><span data-stu-id="48591-147">Conversion of an interpolated string to an <xref:System.IFormattable> instance that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="48591-148">次の例では、カルチャ固有の結果の文字列を作成するために、<xref:System.FormattableString> への暗黙の変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="48591-148">The following example uses implicit conversion to <xref:System.FormattableString> to create culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a><span data-ttu-id="48591-149">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="48591-149">Additional resources</span></span>

<span data-ttu-id="48591-150">文字列補間を初めてお使いの場合は、[C# の文字列補完](../../quick-starts/interpolated-strings.yml)に関するクイックスタートを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48591-150">If you are new to string interpolation, see the [String interpolation in C#](../../quick-starts/interpolated-strings.yml) quickstart.</span></span> <span data-ttu-id="48591-151">その他の例については、「[C# における文字列補間](../../tutorials/string-interpolation.md)」チュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="48591-151">For more examples, see the [String interpolation in C#](../../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="see-also"></a><span data-ttu-id="48591-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="48591-152">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="48591-153">複合書式指定</span><span class="sxs-lookup"><span data-stu-id="48591-153">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="48591-154">文字列</span><span class="sxs-lookup"><span data-stu-id="48591-154">Strings</span></span>](../../programming-guide/strings/index.md)  
 [<span data-ttu-id="48591-155">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="48591-155">C# Programming Guide</span></span>](../../programming-guide/index.md)  
 [<span data-ttu-id="48591-156">C# 特殊文字</span><span class="sxs-lookup"><span data-stu-id="48591-156">C# Special Characters</span></span>](index.md)  
 [<span data-ttu-id="48591-157">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="48591-157">C# Reference</span></span>](../index.md)  