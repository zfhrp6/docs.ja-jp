---
title: "正規表現での量指定子 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "正規表現、量指定子"
  - "メタ文字、量指定子"
  - "最小一致の量指定子"
  - "量指定子 (正規表現)"
  - ".NET Framework 正規表現、量指定子"
  - "量指定子"
  - "最短一致の量指定子"
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# 正規表現での量指定子
量指定子は、一致と見なすために、入力中に文字、グループ、または文字クラスがいくつ存在しなければならないかを指定します。.NET Framework でサポートされている量指定子を次の表に示します。  
  
|最長一致の量指定子|最短一致の量指定子|説明|  
|---------------|---------------|--------|  
|`*`|`*?`|0 回以上の繰り返しに一致します。|  
|`+`|`+?`|1 回以上の繰り返しに一致します。|  
|`?`|`??`|0 回または 1 回の繰り返しに一致します。|  
|`{` *n* `}`|`{` *n* `}?`|*n* の繰り返しに一致します。|  
|`{` *n* `,}`|`{` *n* `,}?`|少なくとも *n* の繰り返しに一致します。|  
|`{` *n* `,` *m* `}`|`{` *n* `,` *m* `}?`|*n* から *m* の繰り返しに一致します。|  
  
 量 `n` および `m` は、整数定数です。  通常、量指定子は最長一致です。最長一致の場合、正規表現エンジンでは、特定のパターンの繰り返しができるだけ多くなるように照合が行われます。  量指定子に `?` 文字を付けると最短一致になります。最短一致の場合は、繰り返しができるだけ少なくなるように照合が行われます。  最長一致の量指定子と最短一致の量指定子の違いの詳細については、このトピックの「[最長一致の量指定子と最短一致の量指定子](#Greedy)」のセクションを参照してください。  
  
> [!IMPORTANT]
>  量指定子を入れ子にすると \(正規表現パターン `(a*)*` などの場合\)、入力文字列の文字数に応じて指数関数的に、正規表現エンジンで実行する必要がある比較の回数が増加する可能性があります。  この動作と回避方法の詳細については、「[バックトラッキング](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)」を参照してください。  
  
## 正規表現の量指定子  
 以降のセクションでは、.NET Framework の正規表現でサポートされている量指定子について説明します。  
  
> [!NOTE]
>  正規表現エンジンでは、正規表現パターンで \*、\+、?、{、および } の各文字を検出すると、[文字クラス](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)に含まれているもの以外は量指定子または量指定子構造の一部として解釈します。  文字クラスの外側でこれらをリテラル文字として解釈するには、文字の前に円記号を付けてエスケープする必要があります。  たとえば、正規表現パターン内の `\*` という文字列は、リテラルのアスタリスク \("\*"\) 文字と解釈されます。  
  
### 0 回以上の繰り返しに一致: \*  
 `*` 量指定子は、直前の要素の 0 回以上の繰り返しに一致します。  これは `{0,}` 指定子と同じです。  `*` は最長一致の量指定子であり、最短一致でこれに対応するのは `*?` です。  
  
 以下の例はこの正規表現を示しています。  入力文字列の 9 つの数字のうち、5 つがパターンに一致し、4 つ \(`95`、`929`、`9129`、および `9919`\) が一致しません。  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`91*`|"9" の後に文字 "1" が 0 個以上続くパターンに一致します。|  
|`9*`|0 個以上の文字 "9" に一致します。|  
|`\b`|ワード境界で終了します。|  
  
### 1 回以上の繰り返しに一致: \+  
 `+` 量指定子は、直前の要素の 1 回以上の繰り返しに一致します。  これは `{1,}` と同じです。  `+` は最長一致の量指定子であり、最短一致でこれに対応するのは `+?` です。  
  
 たとえば、正規表現 `\ban+\w*?\b` は、文字 `a` で始まり、文字 `n` が 1 回以上繰り返されるすべての単語に一致を試みます。  以下の例はこの正規表現を示しています。  この正規表現は、単語 `an`、`annual`、`announcement`、および `antique` に一致し、`autumn` と `all` では正しく不一致となります。  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`an+`|"a" の後に文字 "n" が 1 個以上続くパターンに一致します。|  
|`\w*?`|単語に使用される文字の 0 回以上の繰り返しに一致しますが、できるだけ少ない繰り返しを探します。|  
|`\b`|ワード境界で終了します。|  
  
### 0 回または 1 回の繰り返しに一致: ?  
 `?` 量指定子は、直前の要素の 0 回または 1 回の繰り返しに一致します。  これは `{0,1}` と同じです。  `?` は最長一致の量指定子であり、最短一致でこれに対応するのは `??` です。  
  
 たとえば、正規表現 `\ban?\b` は、文字 `a` で始まり、文字 `n` が 0 回または 1 回繰り返されるすべての単語に一致を試みます。  つまり、単語 `a` と `an` に一致を試みます。  以下の例はこの正規表現を示しています。  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`an?`|"a" の後に文字 "n" が 0 個または 1 個続くパターンに一致します。|  
|`\b`|ワード境界で終了します。|  
  
### ちょうど n 回の繰り返しに一致: {n}  
 `{` *n* `}` の量指定子は *n* が整数である要素の *n* の前の場合に一致します。  `{`*n*`}` は 遅延が等価 `{`*n*`}?`の最長一致の量指定子です。  
  
 たとえば、正規表現 `\b\d+\,\d{3}\b` は、ワード境界、1 つ以上の数字、3 つの数字、ワード境界の順に続く文字列に一致を試みます。  以下の例はこの正規表現を示しています。  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`\d+`|1 個以上の 10 進数と一致します。|  
|`\,`|コンマ文字と一致します。|  
|`\d{3}`|3 個の 10 進数と一致します。|  
|`\b`|ワード境界で終了します。|  
  
### n 回以上の繰り返しに一致: {n,}  
 `{` *n* `,}` の量指定子は、要素の *n* が整数である一つ以上 *n* に先行する時に一致します。  `{`*n*`,}` は 遅延が等価 `{`*n*`}?`の最長一致の量指定子です。  
  
 たとえば、正規表現 `\b\d{2,}\b\D+` は、ワード境界、2 つ以上の数字、ワード境界、数字以外の文字の順に続く文字列に一致を試みます。  以下の例はこの正規表現を示しています。  この正規表現は、`"7 days"` という語句に一致しません。これは、10 進数字が 1 つしか含まれていないためです。しかし、`"10 weeks and 300 years"` という語句には正常に一致します。  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`\d{2,}`|2 個以上の 10 進数と一致します。|  
|`\b`|ワード境界に一致します。|  
|`\D+`|1 個以上の 10 進数以外の文字と一致します。|  
  
### n 回以上 m 回以下の繰り返しに一致: {n,m}  
 `{` *n* `,` *m* `}` の量指定子は、要素の少なくとも *n* の先行するときに、*n* と *m* が整数である *m* 時間よりも一致しませんが。  `{`*n*`,`*m*`}` は遅延 が等価 `{`*n*`,`*m*`}?`の最長一致の量指定子です。  
  
 次の例では、正規表現 `(00\s){2,4}` は、2 つの 0 とスペースが、2 回以上 4 回以下だけ現れる文字列に一致を試みます。  入力文字列の最後の部分には、このパターンが最大の 4 回ではなく 5 回含まれていることに注意してください。  しかし、この部分文字列の最初の部分 \(5 つ目の 0 のペアの前のスペースまで\) だけが、正規表現パターンに一致します。  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### 0 回以上の繰り返しに一致 \(最短一致\): \*?  
 `*?` 量指定子は、直前の要素の 0 回以上の繰り返しに一致しますが、できるだけ少ない繰り返しを探します。  これは、最長一致の量指定子 `*` に対応する、最短一致の量指定子です。  
  
 次の例では、正規表現 `\b\w*?oo\w*?\b` は、文字列 `oo` を含むすべての単語に一致します。  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`\w*?`|0 個以上の単語に使用される文字と一致しますが、できるだけ少ない繰り返しを探します。|  
|`oo`|文字列 "oo" と一致します。|  
|`\w*?`|0 個以上の単語に使用される文字と一致しますが、できるだけ少ない繰り返しを探します。|  
|`\b`|ワード境界で終了します。|  
  
### 1 回以上の繰り返しに一致 \(最短一致\): \+?  
 `+?` 量指定子は、直前の要素の 1 回以上の繰り返しに一致しますが、できるだけ少ない繰り返しを探します。  これは、最長一致の量指定子 `+` に対応する、最短一致の量指定子です。  
  
 たとえば、正規表現 `\b\w+?\b` は、ワード境界で区切られた 1 つ以上の文字に一致します。  以下の例はこの正規表現を示しています。  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### 0 回または 1 回の繰り返しに一致 \(最短一致\): ??  
 `??` 量指定子は、直前の要素の 0 回または 1 回の繰り返しに一致しますが、できるだけ少ない繰り返しを探します。  これは、最長一致の量指定子 `?` に対応する、最短一致の量指定子です。  
  
 たとえば、正規表現 `^\s*(System.)??Console.Write(Line)??\(??` は、文字列 "Console.Write" または "Console.WriteLine" に一致します。  この文字列には、"Console" の前に "System." が含まれていてもよく、最後に左かっこがあってもかまいません。  文字列は行の先頭にある必要がありますが、その前に空白があってもかまいません。  以下の例はこの正規表現を示しています。  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`^`|入力ストリームの先頭と一致します。|  
|`\s*`|0 個以上の空白文字と一致します。|  
|`(System.)??`|文字列 "System." の 0 回または 1 回の繰り返しに一致します。|  
|`Console.Write`|文字列 "Console.Write" と一致します。|  
|`(Line)??`|文字列 "Line" の 0 回または 1 回の繰り返しに一致します。|  
|`\(??`|左かっこの 0 回または 1 回の繰り返しに一致します。|  
  
### ちょうど n 回の繰り返しに一致 \(最短一致\): {n}?  
 `{` *n* `}?` の量指定子は *n* が整数である要素の `n` の前の場合に一致します。  これは、最長一致の量指定子 `{`*n*`}+`のこれに相当します。  
  
 次の例では、正規表現 `\b(\w{3,}?\.){2}?\w{3,}?\b` を使用して Web サイトのアドレスを識別します。  "www.microsoft.com" と "msdn.microsoft.com" には一致しますが、"mywebsite" や "mycompany.com" には一致しない点に注意してください。  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`(\w{3,}?\.)`|3 個以上の単語に使用される文字の後にドット \(ピリオド\) 文字が続くパターンに一致しますが、できるだけ少ない繰り返しを探します。  これが最初のキャプチャ グループです。|  
|`(\w{3,}?\.){2}?`|最初のグループのパターンの 2 回の繰り返しに一致しますが、できるだけ少ない繰り返しを探します。|  
|`\b`|ワード境界で照合を終了します。|  
  
### n 回以上の繰り返しに一致 \(最短一致\): {n,}?  
 `{` *n* `,}?` の量指定子は、一致します要素の *n* が整数\)、できるだけ少ないと一致します `n` 少なくともに先行する時に。  これは、最長一致の量指定子 `{`*n*`,}`のこれに相当します。  
  
 図の前のセクションで `{`*n*`}?` の量指定子の例を参照してください。  この例の正規表現はピリオドが続く少なくとも 3 文字が続く文字列に一致させるために `{`*n*`,}` の量指定子を使用します。  
  
### n 回以上 m 回以下の繰り返しに一致 \(最短一致\): {n,m}?  
 `{` *n* `,` *m* `}?` の量指定子は `n` と *n* と *m* は整数ですが、できるだけ少ない回数\) して直前の要素にも一致します `m` の時間 \(。  これは、最長一致の量指定子 `{`*n*`,`*m*`}`のこれに相当します。  
  
 次の例では、正規表現 `\b[A-Z](../../../amples/snippets/visualbasic/VS_Snippets_Remoting/SoapAttributes1/VB/s.vb){1,10}?[.!?]` は、1 個以上 10 個以下の単語を含んだ文に一致します。  これは、18 個の単語が含まれている 1 つの文を除き、入力文字列中のすべての文に一致します。  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`[A-Z]`|A から Z の大文字と一致します。|  
|`(\w*\s+)`|0 個以上の単語に使用される文字の後に空白文字が 1 個以上続くパターンに一致します。  これが最初のキャプチャ グループです。|  
|`{1,10}?`|最初のパターンの 1 回以上 10 回以下の繰り返しに一致しますが、できるだけ少ない繰り返しを探します。|  
|`[.!?]`|区切り文字 "."、"\!"、"?" のいずれか 1 文字と一致します。|  
  
<a name="Greedy"></a>   
## 最長一致の量指定子と最短一致の量指定子  
 いくつかの量指定子には以下の 2 つのバージョンがあります。  
  
-   最長一致バージョン  
  
     最長一致の量指定子は、要素をできるだけ多く一致させようとします。  
  
-   最短一致バージョン  
  
     最短一致の量指定子は、要素をできるだけ少なく一致させようとします。  最長一致の量指定子に `?` を追加するだけで最短一致の量指定子にすることができます。  
  
 クレジット カード番号などの数値の列から最後の 4 つの数字を取り出す、単純な正規表現について考えてみます。  最長一致の量指定子 `*` を使用するバージョンの正規表現は、`\b.*([0-9]{4})\b` です。  しかし、2 つの数値が含まれている文字列の場合、この正規表現は、以下の例に示すように 2 番目の数値の最後の 4 つの数字だけに一致します。  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 この正規表現は最初の数値の一致に失敗します。量指定子 `*` では、直前の要素をできるだけ頻繁に文字列全体に一致させようとし、文字列の最後まで一致と見なされるためです。  
  
 これは期待した動作ではありません。  この場合は、以下の例に示すように、代わりに最短一致の `*?` ``  量指定子を使用すると、両方の数値から数字を抽出できます。  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 多くの場合、最長一致と最短一致の量指定子を使用した正規表現は、同じ一致結果を返します。  異なる結果を返すことが最も多いのは、どの文字にも一致するメタ文字のワイルドカード \(`.`\) を使用した場合です。  
  
## 量指定子と空一致  
 キャプチャの最小数は量指定子 `*`、`+`と `{`*n*`,`*m*`}` とこれに対応するメソッドは空一致の後には繰り返されません。  この規則により、可能なグループ キャプチャの最大回数が無限またはほぼ無限のときに、量指定子が空の部分式一致の無限ループに入ることを回避できます。  
  
 たとえば、次のコードは、0 個以上の文字 "a" と 0 回以上一致する正規表現パターン `(a?)*` を指定して <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=fullName> メソッドを呼び出した結果を表示します。  単一のキャプチャ グループによって各 "a" および <xref:System.String.Empty?displayProperty=fullName> がキャプチャされますが、2 番目の空一致はないことに注意してください。これは、最初の空一致により量指定子が繰り返しを停止するためです。  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 キャプチャの最大回数および最小回数を定義するキャプチャ グループとキャプチャの固定回数を定義するキャプチャ グループとの実際の違いを確認するために、正規表現パターンの `(a\1|(?(1)\1)){0,2}` と `(a\1|(?(1)\1)){2}` について検討します。  どちらの正規表現も、次の表に示すように定義される単一のキャプチャ グループで構成されています。  
  
|パターン|説明|  
|----------|--------|  
|`(a\1`|"a" と最初のキャプチャ グループの値に一致します。|  
|`&#124;(?(1)`|または、最初のキャプチャ グループが定義されているかどうかをテストします\(`(?(1)` 構成要素ではキャプチャ グループは定義されないことに注意してください\)。|  
|`\1))`|最初のキャプチャ グループが存在する場合、その値と一致します。  グループが存在しない場合、そのグループは <xref:System.String.Empty?displayProperty=fullName> と一致します。|  
  
 最初の正規表現では、0 ～ 2 回、このパターンとの照合が行われます。2 番目の正規表現では、厳密に 2 回です。  最初のパターンは <xref:System.String.Empty?displayProperty=fullName> の最初のキャプチャでキャプチャの最小回数に達するため、`a\1` との照合は繰り返されません。`{0,2}` 量指定子では、最後の反復処理の空一致だけが許可されます。  一方、2 番目の正規表現では、2 回目の `a\1` が評価されるため、"a" に一致します。反復の最小回数は 2 で、空一致の後でエンジンが繰り返さなければならない回数になります。  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## 参照  
 [正規表現言語 \- クイック リファレンス](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)   
 [バックトラッキング](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)