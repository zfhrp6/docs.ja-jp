---
title: $ - 文字列補間 (C# リファレンス)
description: 文字列補間では、従来の複合文字列の書式設定よりも読み取りやすく、便利な構文を書式指定文字列の出力に提供します。
ms.date: 03/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6873c3b419323fa9f5523143ad607289b6fd6e2
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="---string-interpolation-c-reference"></a><span data-ttu-id="da445-103">$ - 文字列補間 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="da445-103">$ - string interpolation (C# Reference)</span></span>

<span data-ttu-id="da445-104">`$` 特殊文字は、リテラル文字列を*挿入文字列*として識別します。</span><span class="sxs-lookup"><span data-stu-id="da445-104">The `$` special character identifies a string literal as an *interpolated string*.</span></span> <span data-ttu-id="da445-105">挿入文字列は、*挿入式*が含まれているテンプレート文字列のように見えます。</span><span class="sxs-lookup"><span data-stu-id="da445-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span> <span data-ttu-id="da445-106">挿入文字列が解決されると、たとえば代入ステートメントまたはメソッド呼び出し内で、結果文字列を生成するために、挿入式が結果の文字列表現によって置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="da445-106">When the interpolated string is resolved, for example in an assignment statement or a method call, interpolated expressions are replaced by the string representations of their results to produce the result string.</span></span> <span data-ttu-id="da445-107">この機能は C# 6 以降のバージョンで使用できます。</span><span class="sxs-lookup"><span data-stu-id="da445-107">This feature is available in C# 6 and later versions.</span></span>

<span data-ttu-id="da445-108">文字列補間は、[複合文字列の書式設定](../../../standard/base-types/composite-formatting.md)機能よりも読み取りやすく、便利な書式指定された文字列を作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="da445-108">String interpolation is a more readable and convenient way to create formatted strings than a [string composite formatting](../../../standard/base-types/composite-formatting.md) feature.</span></span> <span data-ttu-id="da445-109">次の例では、両方の機能を使用して、同じ出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="da445-109">The following example uses both features to produce the same output:</span></span>

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> <span data-ttu-id="da445-110">`$` と文字列を開始する `"` の間に空白を入れることはできません。</span><span class="sxs-lookup"><span data-stu-id="da445-110">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="da445-111">空白を入れると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="da445-111">Doing so causes a compile-time error.</span></span>

<span data-ttu-id="da445-112">挿入式を含む項目の構造は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="da445-112">The structure of an item with an interpolated expression is as follows:</span></span>

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

<span data-ttu-id="da445-113">角かっこ内の要素は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="da445-113">Elements in square brackets are optional.</span></span> <span data-ttu-id="da445-114">次の表は、それぞれの要素の説明です。</span><span class="sxs-lookup"><span data-stu-id="da445-114">The following table describes each element.</span></span>

|<span data-ttu-id="da445-115">要素</span><span class="sxs-lookup"><span data-stu-id="da445-115">Element</span></span>|<span data-ttu-id="da445-116">説明</span><span class="sxs-lookup"><span data-stu-id="da445-116">Description</span></span>|
|-------------|-----------------|
|`interpolatedExpression`|<span data-ttu-id="da445-117">書式設定される結果を取得するために、評価される式です。</span><span class="sxs-lookup"><span data-stu-id="da445-117">The expression to evaluate to get a result to be formatted.</span></span> <span data-ttu-id="da445-118">`null` 結果の文字列表現は、<xref:System.String.Empty?displayProperty=nameWithType> です。</span><span class="sxs-lookup"><span data-stu-id="da445-118">String representation of the `null` result is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|
|`alignment`|<span data-ttu-id="da445-119">挿入式の結果の文字列表現で、最小文字数を定義する値を持つ定数式です。</span><span class="sxs-lookup"><span data-stu-id="da445-119">The constant expression whose value defines the minimum number of characters in the string representation of the result of the interpolated expression.</span></span> <span data-ttu-id="da445-120">正の場合は、文字列表現は右揃えで配置され、負の場合は、左揃えで配置されます。</span><span class="sxs-lookup"><span data-stu-id="da445-120">If positive, the string representation is right-aligned; if negative, it is left-aligned.</span></span> <span data-ttu-id="da445-121">詳細については、「[Alignment コンポーネント](../../../standard/base-types/composite-formatting.md#alignment-component)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da445-121">For more information, see [Alignment Component](../../../standard/base-types/composite-formatting.md#alignment-component).</span></span>|
|`formatString`|<span data-ttu-id="da445-122">式の結果の型によってサポートされる、標準またはカスタムの書式指定文字列です。</span><span class="sxs-lookup"><span data-stu-id="da445-122">A standard or custom format string that is supported by the type of the expression result.</span></span> <span data-ttu-id="da445-123">詳細については、「[Format String コンポーネント](../../../standard/base-types/composite-formatting.md#format-string-component)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da445-123">For more information, see [Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).</span></span>|

<span data-ttu-id="da445-124">次の例では、上記の表で説明されているオプションの書式設定コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="da445-124">The following example uses optional formatting components described in the table above:</span></span>

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

<span data-ttu-id="da445-125">挿入文字列で生成された文字列に中かっこ "{" または "}" を含めるには、2 つの中かっこ "{{" または "}}" を使用します。</span><span class="sxs-lookup"><span data-stu-id="da445-125">To include a curly brace ("{" or "}") in the text produced by an interpolated string, use two curly braces, "{{" or "}}".</span></span> <span data-ttu-id="da445-126">詳細については、「[エスケープ中かっこ ({})](../../../standard/base-types/composite-formatting.md#escaping-braces)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da445-126">For more information, see [Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).</span></span>

<span data-ttu-id="da445-127">コロン (:) が挿入式の項目で特別な意味を持つときに、挿入式で[条件演算子](../operators/conditional-operator.md)を使用するには、その式をかっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="da445-127">As the colon (:) has special meaning in an interpolated expression item, in order to use a [conditional operator](../operators/conditional-operator.md) in an interpolated expression, enclose that expression in parentheses.</span></span>

<span data-ttu-id="da445-128">次の例では、中かっこを結果文字列に含める方法、および挿入式で条件演算子を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="da445-128">The following example shows how to include a curly brace into the result string and how to use a conditional operator in an interpolated expression:</span></span>

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

<span data-ttu-id="da445-129">逐語的挿入文字列では、後に `@` 文字が続く `$` 文字を使用します。</span><span class="sxs-lookup"><span data-stu-id="da445-129">Verbatim interpolated strings use the `$` character followed by the `@` character.</span></span> <span data-ttu-id="da445-130">逐語的文字列の詳細については、[string](../keywords/string.md) に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="da445-130">For more information about verbatim strings, see the [string](../keywords/string.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="da445-131">`$` トークンは、逐語的挿入文字列の `@` トークンの前に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="da445-131">The `$` token must appear before the `@` token in a verbatim interpolated string.</span></span>

## <a name="implicit-conversions"></a><span data-ttu-id="da445-132">暗黙の変換</span><span class="sxs-lookup"><span data-stu-id="da445-132">Implicit conversions</span></span>

<span data-ttu-id="da445-133">挿入文字列から暗黙の型変換を行う方法は 3 種類あります。</span><span class="sxs-lookup"><span data-stu-id="da445-133">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="da445-134">挿入文字列から <xref:System.String> インスタンスへの変換。これは、適切に書式設定された文字列表現の結果で置き換えられる、挿入式の項目を含む挿入文字列分析の結果です。</span><span class="sxs-lookup"><span data-stu-id="da445-134">Conversion of an interpolated string to a <xref:System.String> instance that is the result of interpolated string resolution with interpolated expression items being replaced with the properly formatted string representations of their results.</span></span> <span data-ttu-id="da445-135">この変換では、現在のカルチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="da445-135">This conversion uses the current culture.</span></span>

1. <span data-ttu-id="da445-136">書式設定される式の結果と、挿入文字列から複合書式指定文字列を表す <xref:System.FormattableString> 変数への変換。</span><span class="sxs-lookup"><span data-stu-id="da445-136">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string along with the expression results to be formatted.</span></span> <span data-ttu-id="da445-137">これは、単一の <xref:System.FormattableString> インスタンスから、カルチャ固有のコンテンツを持つ複数の結果文字列の作成を可能にするものです。</span><span class="sxs-lookup"><span data-stu-id="da445-137">That allows you to create multiple result strings with culture-specific content from a single <xref:System.FormattableString> instance.</span></span> <span data-ttu-id="da445-138">そのためには、次のいずれかのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="da445-138">To do that call one of the following methods:</span></span>

      - <span data-ttu-id="da445-139"><xref:System.Globalization.CultureInfo.CurrentCulture> の結果文字列を生成する <xref:System.FormattableString.ToString> オーバーロード。</span><span class="sxs-lookup"><span data-stu-id="da445-139">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>
      - <span data-ttu-id="da445-140"><xref:System.Globalization.CultureInfo.InvariantCulture> の結果文字列を生成する <xref:System.FormattableString.Invariant%2A> メソッド。</span><span class="sxs-lookup"><span data-stu-id="da445-140">A <xref:System.FormattableString.Invariant%2A> method that produces a result string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>
      - <span data-ttu-id="da445-141">特定のカルチャの結果文字列を生成する <xref:System.FormattableString.ToString(System.IFormatProvider)> メソッド。</span><span class="sxs-lookup"><span data-stu-id="da445-141">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

1. <span data-ttu-id="da445-142">挿入文字列から <xref:System.IFormattable> 変数への変換。これは、単一の <xref:System.IFormattable> インスタンスから、カルチャ固有のコンテンツを持つ複数の結果文字列の作成も可能にするものです。</span><span class="sxs-lookup"><span data-stu-id="da445-142">Conversion of an interpolated string to an <xref:System.IFormattable> variable that also allows you to create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span>

<span data-ttu-id="da445-143">次の例では、カルチャ固有の結果の文字列を作成するために、<xref:System.FormattableString> への暗黙の変換を使用します。</span><span class="sxs-lookup"><span data-stu-id="da445-143">The following example uses implicit conversion to <xref:System.FormattableString> for creating culture-specific result strings:</span></span>

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-reading"></a><span data-ttu-id="da445-144">その他の参考資料</span><span class="sxs-lookup"><span data-stu-id="da445-144">Additional reading</span></span>

<span data-ttu-id="da445-145">文字列補間を初めてお使いの場合は、[挿入文字列のクイック スタート](../../quick-starts//interpolated-strings.yml)に関するページを確認してください。</span><span class="sxs-lookup"><span data-stu-id="da445-145">If you are new to the string interpolation, check the [interpolated strings quickstart](../../quick-starts//interpolated-strings.yml).</span></span> <span data-ttu-id="da445-146">詳細については、「[文字列補間](../../tutorials/string-interpolation.md)」のチュートリアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="da445-146">For more examples, see the [string interpolation tutorial](../../tutorials/string-interpolation.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="da445-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="da445-147">See also</span></span>  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [<span data-ttu-id="da445-148">複合書式指定</span><span class="sxs-lookup"><span data-stu-id="da445-148">Composite formatting</span></span>](../../../standard/base-types/composite-formatting.md)  
 [<span data-ttu-id="da445-149">文字列</span><span class="sxs-lookup"><span data-stu-id="da445-149">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="da445-150">C# 特殊文字</span><span class="sxs-lookup"><span data-stu-id="da445-150">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)  
 [<span data-ttu-id="da445-151">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="da445-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="da445-152">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="da445-152">C# Reference</span></span>](../../../csharp/language-reference/index.md)  