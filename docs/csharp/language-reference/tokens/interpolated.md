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
ms.openlocfilehash: cabb40c9c449780c8c2a504aad3e53938e2ed957
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="---string-interpolation-c-reference"></a>$ - 文字列補間 (C# リファレンス)

`$` 特殊文字は、リテラル文字列を*挿入文字列*として識別します。 挿入文字列は、*挿入式*が含まれているテンプレート文字列のように見えます。 挿入文字列が結果文字列に解決されると、挿入式を含む項目は、式の結果の文字列表現によって置き換えられます。 この機能は C# 6 以降のバージョンで使用できます。

文字列補間では、[複合文字列の書式設定](../../../standard/base-types/composite-formatting.md)機能よりも読み取りやすく便利な構文を使用して書式指定された文字列を作成できます。 次の例では、両方の機能を使用して、同じ出力を生成します。

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> `$` と文字列を開始する `"` の間に空白を入れることはできません。 空白を入れると、コンパイル時エラーが発生します。

挿入式を含む項目の構造は、次のとおりです。

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

角かっこ内の要素は省略可能です。 次の表は、それぞれの要素の説明です。

|要素|説明|
|-------------|-----------------|
|`interpolatedExpression`|書式設定される結果を取得するために、評価される式です。 `null` 結果の文字列表現は、<xref:System.String.Empty?displayProperty=nameWithType> です。|
|`alignment`|挿入式の結果の文字列表現で、最小文字数を定義する値を持つ定数式です。 正の場合は、文字列表現は右揃えで配置され、負の場合は、左揃えで配置されます。 詳細については、「[Alignment コンポーネント](../../../standard/base-types/composite-formatting.md#alignment-component)」を参照してください。|
|`formatString`|式の結果の型によってサポートされる、標準またはカスタムの書式指定文字列です。 詳細については、「[Format String コンポーネント](../../../standard/base-types/composite-formatting.md#format-string-component)」を参照してください。|

次の例では、前述したオプションの書式設定コンポーネントを使用します。

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

挿入文字列で生成された文字列にかっこ "{" または "}" を含めるには、2 つのかっこ "{{" または "}}" を使用します。 詳細については、「[エスケープ中かっこ ({})](../../../standard/base-types/composite-formatting.md#escaping-braces)」を参照してください。

コロン (:) が挿入式の項目で特別な意味を持つときに、挿入式で[条件演算子](../operators/conditional-operator.md)を使用するには、その式をかっこで囲みます。

次の例では、かっこを結果文字列に含める方法、および挿入式で条件演算子を使用する方法を示します。

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

逐語的挿入文字列では、後に `@` 文字が続く `$` 文字を使用します。 逐語的文字列の詳細については、[string](../keywords/string.md) に関するトピックを参照してください。

> [!NOTE]
> `$` トークンは、逐語的挿入文字列の `@` トークンの前に置く必要があります。

挿入文字列から暗黙の変換を行う方法は 3 種類あります。

1. 挿入文字列から <xref:System.String> インスタンスへの変換。これは、適切に書式設定された文字列表現の結果で置き換えられる、挿入式の項目を含む挿入文字列分析の結果です。 この変換では、現在のカルチャを使用します。

1. 書式設定される式の結果と、挿入文字列から複合書式指定文字列を表す <xref:System.FormattableString> インスタンスへの変換。 これは、単一の <xref:System.FormattableString> インスタンスから、カルチャ固有のコンテンツを持つ複数の結果文字列の作成を可能にするものです。 そのためには、次のいずれかのメソッドを呼び出します。

      - <xref:System.Globalization.CultureInfo.CurrentCulture> の結果文字列を生成する <xref:System.FormattableString.ToString> オーバーロード。
      - <xref:System.Globalization.CultureInfo.InvariantCulture> の結果文字列を生成する <xref:System.FormattableString.Invariant%2A> メソッド。
      - 特定のカルチャの結果文字列を生成する <xref:System.FormattableString.ToString(System.IFormatProvider)> メソッド。

1. 挿入文字列から <xref:System.IFormattable> インスタンスへの変換。これは、単一の <xref:System.IFormattable> インスタンスから、カルチャ固有のコンテンツを持つ複数の結果文字列の作成も可能にするものです。

次の例では、カルチャ固有の結果の文字列を作成するために、<xref:System.FormattableString> への暗黙の変換を使用します。

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

文字列補間を初めてお使いの場合は、[C# の文字列補完](../../quick-starts/interpolated-strings.yml)に関するクイックスタートを参照してください。 詳細については、「[文字列補間](../../tutorials/string-interpolation.md)」のチュートリアルを参照してください。

## <a name="see-also"></a>関連項目  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [複合書式指定](../../../standard/base-types/composite-formatting.md)  
 [文字列](../../../csharp/programming-guide/strings/index.md)  
 [C# 特殊文字](../../../csharp/language-reference/tokens/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# リファレンス](../../../csharp/language-reference/index.md)  