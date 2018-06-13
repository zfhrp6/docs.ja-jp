---
title: C# における文字列補間
description: C# の文字列補間を使用した結果文字列に書式設定された式の結果を含める方法について説明します。
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 447e87cd4aae49896f0efbb8ece6097181079266
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058940"
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="b22fe-103">C# における文字列補間</span><span class="sxs-lookup"><span data-stu-id="b22fe-103">String interpolation in C#</span></span> #

<span data-ttu-id="b22fe-104">このチュートリアルは、[文字列補間](../language-reference/tokens/interpolated.md)を使用して結果文字列に式の結果を書式設定したものを含める方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b22fe-104">This tutorial shows you how to use [string interpolation](../language-reference/tokens/interpolated.md) to format and include expression results in a result string.</span></span> <span data-ttu-id="b22fe-105">例では、基本的な C# の概念と .NET の型の書式設定について理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="b22fe-105">The examples assume that you are familiar with basic C# concepts and .NET type formatting.</span></span> <span data-ttu-id="b22fe-106">文字列補間や .NET の型の書式設定の経験がない場合は、最初に[対話型の文字列補間に関するクイックスタート](../quick-starts/interpolated-strings.yml)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b22fe-106">If you are new to string interpolation or .NET type formatting, check out the [interactive string interpolation quickstart](../quick-starts/interpolated-strings.yml) first.</span></span> <span data-ttu-id="b22fe-107">.NET の型の書式設定の詳細については、「[.NET での型の書式設定](../../standard/base-types/formatting-types.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b22fe-107">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) topic.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a><span data-ttu-id="b22fe-108">はじめに</span><span class="sxs-lookup"><span data-stu-id="b22fe-108">Introduction</span></span>

<span data-ttu-id="b22fe-109">[文字列補間](../language-reference/tokens/interpolated.md)機能は、[複合書式設定](../../standard/base-types/composite-formatting.md)機能の上に構築されていて、結果文字列に書式設定された式の結果を含めるためのより読みやすく、便利な構文を提供します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-109">The [string interpolation](../language-reference/tokens/interpolated.md) feature is built on top of the [composite formatting](../../standard/base-types/composite-formatting.md) feature and provides a more readable and convenient syntax to include formatted expression results in a result string.</span></span>

<span data-ttu-id="b22fe-110">文字列リテラルを挿入文字列として識別するため、先頭に `$` の記号を追加してください。</span><span class="sxs-lookup"><span data-stu-id="b22fe-110">To identify a string literal as an interpolated string, prepend it with the `$` symbol.</span></span> <span data-ttu-id="b22fe-111">挿入文字列の値を返す、有効な C# の式を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="b22fe-111">You can embed any valid C# expression that returns a value in an interpolated string.</span></span> <span data-ttu-id="b22fe-112">次の例では、式が評価されるとすぐにその結果が文字列に変換され、結果文字列に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b22fe-112">In the following example, as soon as an expression is evaluated, its result is converted into a string and included in a result string:</span></span>

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

<span data-ttu-id="b22fe-113">例に示すように、式を中かっこで囲むことで挿入文字列に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="b22fe-113">As the example shows, you include an expression in an interpolated string by enclosing it with braces:</span></span>

```
{<interpolatedExpression>}
```

<span data-ttu-id="b22fe-114">コンパイル時には通常、挿入文字列が <xref:System.String.Format%2A?displayProperty=nameWithType> メソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="b22fe-114">At compile time, an interpolated string is typically transformed into a <xref:System.String.Format%2A?displayProperty=nameWithType> method call.</span></span> <span data-ttu-id="b22fe-115">これにより、[文字列の複合書式設定](../../standard/base-types/composite-formatting.md)のすべての機能が、挿入文字列でも使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b22fe-115">That makes all the capabilities of the [string composite formatting](../../standard/base-types/composite-formatting.md) feature available to you to use with interpolated strings as well.</span></span>

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a><span data-ttu-id="b22fe-116">挿入文字列の書式設定文字列を指定する方法</span><span class="sxs-lookup"><span data-stu-id="b22fe-116">How to specify a format string for an interpolated expression</span></span>

<span data-ttu-id="b22fe-117">コロン (":") と書式設定文字列を持つ挿入式に従って、式の結果の型でサポートされる書式設定文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-117">You specify a format string that is supported by the type of the expression result by following the interpolated expression with a colon (":") and the format string:</span></span>

```
{<interpolatedExpression>:<formatString>}
```

<span data-ttu-id="b22fe-118">次の例は、日時や数値による結果を生成する式の標準とカスタムの書式設定文字列を指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b22fe-118">The following example shows how to specify standard and custom format strings for expressions that produce date and time or numeric results:</span></span>

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

<span data-ttu-id="b22fe-119">詳細については、「[複合書式設定](../../standard/base-types/composite-formatting.md)」トピックの「[Format String コンポーネント](../../standard/base-types/composite-formatting.md#format-string-component)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b22fe-119">For more information, see the [Format String Component](../../standard/base-types/composite-formatting.md#format-string-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span> <span data-ttu-id="b22fe-120">このセクションでは、.NET の基本データ型でサポートされる標準とカスタムの書式設定文字列について説明するトピックへのリンクを提供しています。</span><span class="sxs-lookup"><span data-stu-id="b22fe-120">That section provides links to the topics that describe standard and custom format strings supported by .NET base types.</span></span>

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a><span data-ttu-id="b22fe-121">書式設定された挿入式のフィールドの幅と配置を制御する方法</span><span class="sxs-lookup"><span data-stu-id="b22fe-121">How to control the field width and alignment of the formatted interpolated expression</span></span>

<span data-ttu-id="b22fe-122">コンマ (",") と定数式を持つ挿入式に従って、書式設定された式の結果の最小フィールド幅と配置を指定します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-122">You specify the minimum field width and the alignment of the formatted expression result by following the interpolated expression with a comma (",") and the constant expression:</span></span>

```
{<interpolatedExpression>,<alignment>}
```

<span data-ttu-id="b22fe-123">*alignment* の値が正の値である場合、書式設定された式の結果は右揃えになります。負の値である場合は、左揃えになります。</span><span class="sxs-lookup"><span data-stu-id="b22fe-123">If the *alignment* value is positive, the formatted expression result is right-aligned; if negative, it's left-aligned.</span></span>

<span data-ttu-id="b22fe-124">配置と書式設定文字列の両方を指定する必要がある場合は、alignment コンポーネントから開始します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-124">If you need to specify both alignment and a format string, start with the alignment component:</span></span>

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

<span data-ttu-id="b22fe-125">次の例は、配置を指定する方法を示し、テキスト フィールドを区切るためにパイプ文字 ("|") を使用しています。</span><span class="sxs-lookup"><span data-stu-id="b22fe-125">The following example shows how to specify alignment and uses pipe characters ("|") to delimit text fields:</span></span>

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

<span data-ttu-id="b22fe-126">出力例が示すように、書式設定された式の結果の長さが指定したフィールドの幅を超える場合、*alignment* の値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b22fe-126">As the example output shows, if the length of the formatted expression result exceeds specified field width, the *alignment* value is ignored.</span></span>

<span data-ttu-id="b22fe-127">詳細については、「[複合書式設定](../../standard/base-types/composite-formatting.md)」トピックの「[Alignment コンポーネント](../../standard/base-types/composite-formatting.md#alignment-component)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b22fe-127">For more information, see the [Alignment Component](../../standard/base-types/composite-formatting.md#alignment-component) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a><span data-ttu-id="b22fe-128">挿入文字列でエスケープ シーケンスを使用する方法</span><span class="sxs-lookup"><span data-stu-id="b22fe-128">How to use escape sequences in an interpolated string</span></span>

<span data-ttu-id="b22fe-129">挿入文字列は、通常の文字列リテラルで使用できるすべてのエスケープ シーケンスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="b22fe-129">Interpolated strings support all escape sequences that can be used in ordinary string literals.</span></span> <span data-ttu-id="b22fe-130">詳細については、「[文字列のエスケープ シーケンス](../programming-guide/strings/index.md#string-escape-sequences)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b22fe-130">For more information, see [String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).</span></span>

<span data-ttu-id="b22fe-131">エスケープ シーケンスをリテラルで解釈するには、[verbatim](../language-reference/tokens/verbatim.md) 文字列リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-131">To interpret escape sequences literally, use a [verbatim](../language-reference/tokens/verbatim.md) string literal.</span></span> <span data-ttu-id="b22fe-132">verbatim 挿入文字列は、`@` 文字が続く `$` 文字で始まります。</span><span class="sxs-lookup"><span data-stu-id="b22fe-132">A verbatim interpolated string starts with the `$` character followed by the `@` character.</span></span>

<span data-ttu-id="b22fe-133">中かっこ "{" または "}" を結果文字列に含める場合は、2 つの中かっこ "{{" または "}}" を使用します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-133">To include a brace, "{" or "}", in a result string, use two braces, "{{" or "}}".</span></span> <span data-ttu-id="b22fe-134">詳細については、「[複合書式設定](../../standard/base-types/composite-formatting.md)」トピックの「[エスケープ中かっこ ({})](../../standard/base-types/composite-formatting.md#escaping-braces)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b22fe-134">For more information, see the [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) section of the [Composite Formatting](../../standard/base-types/composite-formatting.md) topic.</span></span>

<span data-ttu-id="b22fe-135">次の例は、結果文字列に中かっこを含め、verbatim 挿入文字列を作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b22fe-135">The following example shows how to include braces in a result string and construct a verbatim interpolated string:</span></span>

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a><span data-ttu-id="b22fe-136">挿入式で三項条件演算子 `?:` を使用する方法</span><span class="sxs-lookup"><span data-stu-id="b22fe-136">How to use a ternary conditional operator `?:` in an interpolated expression</span></span>

<span data-ttu-id="b22fe-137">コロン (":") が挿入式の項目で特別な意味を持つときに、式で[条件演算子](../language-reference/operators/conditional-operator.md)を使用するには、次の例が示すようにその式をかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="b22fe-137">As the colon (":") has special meaning in an item with an interpolated expression, in order to use a [conditional operator](../language-reference/operators/conditional-operator.md) in an expression, enclose it in parentheses, as the following example shows:</span></span>

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a><span data-ttu-id="b22fe-138">文字列補間を使用してカルチャ固有の結果文字列を作成する方法</span><span class="sxs-lookup"><span data-stu-id="b22fe-138">How to create a culture-specific result string with string interpolation</span></span>

<span data-ttu-id="b22fe-139">既定では、挿入文字列は、すべての書式設定操作に対して <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> プロパティで定義された現在のカルチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-139">By default, an interpolated string uses the current culture defined by the <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> property for all formatting operations.</span></span> <span data-ttu-id="b22fe-140">カルチャ固有の結果文字列を作成するには、<xref:System.FormattableString?displayProperty=nameWithType> インスタンスへの挿入文字列の暗黙的変換を使用し、その <xref:System.FormattableString.ToString(System.IFormatProvider)> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-140">Use implicit conversion of an interpolated string to a <xref:System.FormattableString?displayProperty=nameWithType> instance and call its <xref:System.FormattableString.ToString(System.IFormatProvider)> method to create a culture-specific result string.</span></span> <span data-ttu-id="b22fe-141">その方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-141">The following example shows how to do that:</span></span>

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

<span data-ttu-id="b22fe-142">例に示すように、<xref:System.FormattableString> インスタンスを 1 回使用して、さまざまなカルチャに対する複数の結果文字列を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="b22fe-142">As the example shows, you can use one <xref:System.FormattableString> instance to generate multiple result strings for various cultures.</span></span>

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a><span data-ttu-id="b22fe-143">インバリアント カルチャを使用して結果文字列を作成する方法</span><span class="sxs-lookup"><span data-stu-id="b22fe-143">How to create a result string using the invariant culture</span></span>

<span data-ttu-id="b22fe-144"><xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> メソッドと共に静的な <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> メソッドを使用して、<xref:System.Globalization.CultureInfo.InvariantCulture> の結果文字列に挿入文字列を解決することができます。</span><span class="sxs-lookup"><span data-stu-id="b22fe-144">Along with the <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> method, you can use the static <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> method to resolve an interpolated string to a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span> <span data-ttu-id="b22fe-145">その方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="b22fe-145">The following example shows how to do that:</span></span>

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a><span data-ttu-id="b22fe-146">まとめ</span><span class="sxs-lookup"><span data-stu-id="b22fe-146">Conclusion</span></span>

<span data-ttu-id="b22fe-147">このチュートリアルでは、文字列補間の使用に関する一般的なシナリオについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="b22fe-147">This tutorial describes common scenarios of string interpolation usage.</span></span> <span data-ttu-id="b22fe-148">文字列補間の詳細については、[文字列補間](../language-reference/tokens/interpolated.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b22fe-148">For more information about string interpolation, see the [String interpolation](../language-reference/tokens/interpolated.md) topic.</span></span> <span data-ttu-id="b22fe-149">.NET の型の書式設定の詳細については、「[.NET での型の書式設定](../../standard/base-types/formatting-types.md)」および「[複合書式設定](../../standard/base-types/composite-formatting.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b22fe-149">For more information about formatting types in .NET, see the [Formatting Types in .NET](../../standard/base-types/formatting-types.md) and [Composite formatting](../../standard/base-types/composite-formatting.md) topics.</span></span>

## <a name="see-also"></a><span data-ttu-id="b22fe-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="b22fe-150">See also</span></span>

<xref:System.String.Format%2A?displayProperty=nameWithType>  
<xref:System.FormattableString?displayProperty=nameWithType>  
<xref:System.IFormattable?displayProperty=nameWithType>  
[<span data-ttu-id="b22fe-151">文字列</span><span class="sxs-lookup"><span data-stu-id="b22fe-151">Strings</span></span>](../programming-guide/strings/index.md)  
