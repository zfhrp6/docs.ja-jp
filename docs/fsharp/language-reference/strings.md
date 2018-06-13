---
title: 文字列 (F#)
description: F# 'string' 型が変更できないテキストを Unicode 文字のシーケンスとして表現する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: bdd1d1a542e70bcd95fce51e75d0c1ddffceb008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564860"
---
# <a name="strings"></a>文字列

> [!NOTE]
この記事の API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

`string`型は、変更できないテキストを Unicode 文字のシーケンスとして表現します。 `string` は、.NET Framework の `System.String` のエイリアスです。

## <a name="remarks"></a>コメント
文字列リテラルは引用符 (") 文字で区切られます。 円記号 (\)特定の特殊文字をエンコードするために使用します。 円記号と、次の文字の組み合わせと呼ばれる、*エスケープ シーケンス*です。 サポートされるエスケープ シーケンス f# 文字列リテラルは、次の表に表示されます。

|文字|エスケープ シーケンス|
|---------|---------------|
|バックスペース|\b|
|改行|\n|
|キャリッジ リターン|\r|
|タブ|\t|
|円記号|\\|
|引用符|\"|
|アポストロフィ|\'|
|Unicode 文字|\u*XXXX*または \U*XXXXXXXX* (ここで*X* 16 進数の数字を示します)|

前にある場合、@ 記号、リテラルは、逐語的文字列。 つまり、2 つの引用符文字が 1 つの引用符の文字として解釈されることを除き、エスケープ シーケンスを無視することです。

さらに、文字列は、三重引用符で囲むことがあります。 この場合、すべてのエスケープ シーケンスは無視されます、二重引用符文字も含まれます。 含む埋め込み文字列を引用符で囲まれた文字列を指定するには、逐語的文字列または三重引用符で囲まれた文字列か、使用できます。 逐語的文字列を使用する場合は、単一引用符文字を示すために 2 つの引用符文字を指定する必要があります。 三重引用符で囲まれた文字列を使用する場合は、文字列の末尾として解析されることがなく、単一引用符文字を使用できます。 この手法は、XML または埋め込まれた引用符を含むその他の構造を使用するときに役に立ちます。

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

コードでは、文字列は、改行が受け入れられ、改行として解釈されます、改行文字として、円記号が改行の前に、最後の文字でない限り。 次の行の先頭の空白文字には、バック スラッシュ文字を使用する場合は無視されます。 次のコードは、文字列を生成`str1`値を持つ`"abc\n     def"`および文字列`str2`値を持つ`"abcdef"`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

文字列内の個々 の文字は、次のように配列に似た構文を使用してアクセスできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

出力は `b`になります。

または、次のコードに示すように、配列スライス構文を使用して部分文字列を抽出することができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

出力は次のとおりです。

```
abc
def
```

型の符号なしバイトの配列で ASCII 文字列を表すことができる`byte[]`です。 サフィックスを追加する`B`を ASCII 文字列であることを示すリテラル文字列。 ASCII 文字列リテラルがバイト配列を使用では、Unicode のエスケープ シーケンスを除くの Unicode 文字列として同じエスケープ シーケンスをサポートします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a>文字列演算子
文字列を連結する 2 つの方法があります: を使用して、`+`演算子またはを使用して、`^`演算子。 `+`演算子は、機能を処理する .NET Framework の文字列との互換性を維持します。

次の例は、文字列の連結を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a>String クラス
F# の文字列型は .NET Framework では実際にため`System.String`すべての入力、`System.String`メンバーは、使用します。 これが含まれています、`+`演算子を使用する場合は、文字列を連結する、`Length`プロパティ、および`Chars`プロパティで、文字列を Unicode 文字の配列として返します。 文字列の詳細については、次を参照してください。`System.String`です。

使用して、`Chars`プロパティ`System.String`文字列内の個々 の文字は、次のコードに示すように、インデックスを指定することによってアクセスできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a>String モジュール
文字列を処理するための追加機能が含まれる、`String`内のモジュール、`FSharp.Core`名前空間。 詳細については、次を参照してください。 [Core.String モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)です。

## <a name="see-also"></a>関連項目
[F# 言語リファレンス](index.md)
