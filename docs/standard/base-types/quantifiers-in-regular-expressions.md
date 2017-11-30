---
title: "量指定子 (正規表現)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab06aa0c331c8cbd4c8986cced29334046f30264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="quantifiers-in-regular-expressions"></a>量指定子 (正規表現)
量指定子は、一致と見なされるために入力中に存在する必要がある文字、グループ、または文字クラスの出現数を指定します。  次の表に、.NET でサポートされている量指定子の一覧を示します。  
  
|最長一致の量指定子|最短一致の量指定子|説明|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|0 回以上の繰り返しに一致します。|  
|`+`|`+?`|1 回以上の繰り返しに一致します。|  
|`?`|`??`|0 回または 1 回の繰り返しに一致します。|  
|`{` *n* `}`|`{` *n* `}?`|完全に一致 *n* 回です。|  
|`{` *n* `,}`|`{` *n* `,}?`|以上に一致する *n* 回です。|  
|`{` *n* `,` *分* `}`|`{` *n* `,` *分* `}?`|一致 *n* に*m*回です。|  
  
 数量`n`と`m`整数定数であります。 通常、量指定子は最長一致です。最長一致の場合、正規表現エンジンでは、特定のパターンの繰り返しができるだけ多くなるように照合が行われます。 量指定子に `?` 文字を付けると最短一致になります。最短一致の場合、正規表現エンジンでは、特定のパターンの繰り返しができるだけ少なくなるように照合が行われます。 最長一致と最短一致の量指定子の違いの詳細については、このトピックの「[最長一致と最短一致の量指定子](#Greedy)」のセクションをご覧ください。  
  
> [!IMPORTANT]
>  量指定子を入れ子にすると (たとえば、正規表現パターン `(a*)*` など)、入力文字列の文字数に応じて指数関数的に、正規表現エンジンで実行する必要がある比較の回数が増加する可能性があります。 この動作とその回避策の詳細については、次を参照してください。[バックトラッ キング](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)です。  
  
## <a name="regular-expression-quantifiers"></a>正規表現の量指定子  
 以降のセクションでは、.NET の正規表現でサポートされている量指定子について説明します。  
  
> [!NOTE]
>  場合、*、+、?、{と} の文字が、正規表現パターンの検出、正規表現エンジンでは、解釈に量指定子または量指定子構造の一部として含まれている場合を除き、[文字クラス](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)です。 文字クラスの外側でこれらをリテラル文字として解釈するには、文字の前に円記号を付けてエスケープする必要があります。 たとえば、文字列`\*`では、正規表現パターンはリテラルのアスタリスクとして解釈されます ("\*") 文字です。  
  
### <a name="match-zero-or-more-times-"></a>0 回以上の繰り返しに一致: *  
 `*` 量指定子は、直前の要素の 0 回以上の繰り返しに一致します。 等価である、`{0,}`量指定子です。 `*`最長一致の量指定子がレイジー該当するショートカットは`*?`します。  
  
 次の例は、この正規表現を示しています。 入力文字列の 9 個の数字のうち、5 個がパターンに一致し、4 個 (`95`、`929`、`9129`、および `9919`) が一致しません。  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`91*`|"9" の後に文字 "1" が 0 個以上続くパターンに一致します。|  
|`9*`|0 個以上の文字 "9" に一致します。|  
|`\b`|ワード境界で終了します。|  
  
### <a name="match-one-or-more-times-"></a>1 回以上の繰り返しに一致: +  
 `+`量化子により、直前の要素が 1 回以上一致します。 等価である`{1,}`です。 `+`最長一致の量指定子がレイジー該当するショートカットは`+?`します。  
  
 たとえば、正規表現 `\ban+\w*?\b` は、文字 `a` で始まり、文字 `n` が 1 回以上繰り返されるすべての単語に一致を試みます。 次の例は、この正規表現を示しています。 この正規表現は、単語 `an`、`annual`、`announcement`、および `antique` に一致し、`autumn` と `all` では不一致となります。  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`an+`|"a" の後に文字 "n" が 1 個以上続くパターンに一致します。|  
|`\w*?`|単語に含まれる文字の 0 回以上の繰り返しのうち、最も少ない繰り返しに一致します。|  
|`\b`|ワード境界で終了します。|  
  
### <a name="match-zero-or-one-time-"></a>0 回または 1 回の繰り返しに一致: ?  
 `?`量が直前の要素の 0 または 1 回一致します。 等価である`{0,1}`です。 `?`最長一致の量指定子がレイジー該当するショートカットは`??`します。  
  
 たとえば、正規表現 `\ban?\b` は、文字 `a` で始まり、文字 `n` が 0 回または 1 回繰り返されるすべての単語に一致を試みます。 つまり、単語 `a` と `an` に一致を試みます。 次の例は、この正規表現を示しています。  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`an?`|"a" の後に文字 "n" が 0 個または 1 個続くパターンに一致します。|  
|`\b`|ワード境界で終了します。|  
  
### <a name="match-exactly-n-times-n"></a>n 回の繰り返しに一致: {n}  
 `{`  *n*  `}`量指定子は、直前の要素を正確に一致 *n* 回 *n* は任意の整数。 `{`*n*`}`最長一致の量指定子がレイジー該当するショートカットは`{`  *n* `}?`です。  
  
 たとえば、正規表現 `\b\d+\,\d{3}\b` は、ワード境界、1 個以上の 10 進数、3 個の 10 進数、ワード境界の順に続く文字に一致を試みます。 次の例は、この正規表現を示しています。  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`\d+`|1 個以上の 10 進数と一致します。|  
|`\,`|コンマ文字と一致します。|  
|`\d{3}`|3 個の 10 進数と一致します。|  
|`\b`|ワード境界で終了します。|  
  
### <a name="match-at-least-n-times-n"></a>n 回以上の繰り返しに一致: {n,}  
 `{`  *n*  `,}`量指定子は、少なくとも直前の要素を一致 *n* 回 *n* は任意の整数。 `{`*n*`,}`最長一致の量指定子がレイジー該当するショートカットは`{`  *n* `}?`です。  
  
 たとえば、正規表現 `\b\d{2,}\b\D+` は、ワード境界、2 個以上の 10 進数、ワード境界、数字以外の文字の順に続く文字に一致を試みます。 次の例は、この正規表現を示しています。 語句に一致する正規表現が失敗した`"7 days"`1 つの 10 進数字が含まれていますが、正常には、語句が一致するので`"10 weeks and 300 years"`です。  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`\d{2,}`|2 個以上の 10 進数と一致します。|  
|`\b`|ワード境界に一致します。|  
|`\D+`|1 個以上の 10 進数以外の数字と一致します。|  
  
### <a name="match-between-n-and-m-times-nm"></a>n 回から m 回までの繰り返しに一致: {n,m}  
 `{`  *n*  `,` *M* `}`量指定子は、少なくとも直前の要素を一致 *n* 時間、超える*m*回 *n* と*m*の整数です。 `{`*n*`,`*m* `}`は最長一致の量指定子がレイジー該当するショートカットは`{`  *n*  `,` *m*`}?`です。  
  
 次の例では、正規表現 `(00\s){2,4}` は、2 個の 0 と 1 個のスペースが、2 回以上 4 回以下だけ現れる文字列に一致を試みます。 入力文字列の最後の部分には、このパターンが最大の 4 回ではなく 5 回含まれていることに注意してください。 この部分文字列の最初の部分 (スペースと 5 つ目の 0 のペアまで) だけが正規表現パターンに一致します。  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a>0 回以上の繰り返しに一致 (最短一致): *?  
 `*?`量指定子は 0 回以上、できるだけがだけ少ない回数を直前の要素に一致します。 対応する最長一致の量指定子の`*`します。  
  
 次の例では、正規表現 `\b\w*?oo\w*?\b` は、文字列 `oo` を含むすべての単語に一致します。  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`\w*?`|単語に含まれる 0 個以上の文字のうち、最も少ない文字に一致します。|  
|`oo`|文字列 "oo" と一致します。|  
|`\w*?`|単語に含まれる 0 個以上の文字のうち、最も少ない文字に一致します。|  
|`\b`|ワード境界で終了します。|  
  
### <a name="match-one-or-more-times-lazy-match-"></a>1 回以上の繰り返しに一致 (最短一致): +?  
 `+?`量指定子と 1 つまたは複数回、できるだけがだけ少ない回数直前の要素に一致します。 対応する最長一致の量指定子の`+`します。  
  
 たとえば、正規表現 `\b\w+?\b` は、ワード境界で区切られた 1 つ以上の文字に一致します。 次の例は、この正規表現を示しています。  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a>0 回または 1 回の繰り返しに一致 (最短一致): ??  
 `??`量には、直前の要素の 0 または 1 回限りがだけ少ない回数が一致します。 対応する最長一致の量指定子の`?`します。  
  
 たとえば、正規表現 `^\s*(System.)??Console.Write(Line)??\(??` は、文字列 "Console.Write" または "Console.WriteLine" に一致を試みます。 文字列には、"Console" の前に "System." が含まれていてもよく、最後に左かっこがあってもかまいません。 文字列は行の先頭にある必要がありますが、文字列の前に空白があってもかまいません。 次の例は、この正規表現を示しています。  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`^`|入力ストリームの先頭と一致します。|  
|`\s*`|0 個以上の空白文字と一致します。|  
|`(System.)??`|文字列 "System." の 0 回または 1 回の繰り返しに一致します。|  
|`Console.Write`|文字列 "Console.Write" と一致します。|  
|`(Line)??`|文字列 "Line" の 0 回または 1 回の繰り返しに一致します。|  
|`\(??`|左かっこの 0 回または 1 回の繰り返しに一致します。|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a>n 回の繰り返しに一致 (最短一致): {n}?  
 `{`  *n*  `}?`量指定子は、直前の要素を正確に一致`n`回 *n* は任意の整数。 対応する最長一致の量指定子の`{`  *n* `}+`です。  
  
 次の例では、正規表現 `\b(\w{3,}?\.){2}?\w{3,}?\b` を使用して Web サイトのアドレスを識別します。 "www.microsoft.com" と "msdn.microsoft.com" には一致しますが、"mywebsite" や "mycompany.com" には一致しない点に注意してください。  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`(\w{3,}?\.)`|単語に含まれる 3 個以上の文字のうち、最も少ない文字の後に、ドット (ピリオド) 文字が続くパターンに一致します。 これが最初のキャプチャ グループです。|  
|`(\w{3,}?\.){2}?`|最初のグループのパターンの 2 回の繰り返しのうち、最も少ない繰り返しに一致します。|  
|`\b`|ワード境界で照合を終了します。|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a>n 回以上の繰り返しに一致 (最短一致): {n,}?  
 `{`  *n*  `,}?`量指定子は、少なくとも直前の要素を一致`n`回 *n* はできるだけ少ない回数を任意の整数には考えられる。 対応する最長一致の量指定子の`{`  *n* `,}`です。  
  
 例を参照して、 `{`  *n*  `}?`図については、前のセクションでは、量指定子です。 例では、正規表現を使用して、 `{`  *n*  `,}`量指定子を持つ 3 つ以上の文字がピリオドが続く文字列を一致するようにします。  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a>n 回から m 回までの繰り返しに一致 (最短一致): {n,m}?  
 `{`  *n*  `,` *M* `}?`量指定子の間で直前の要素に一致`n`と`m`回*n* と*m*の整数では、できるだけがだけ少ない回数。 対応する最長一致の量指定子の`{`  *n*  `,` *m*`}`です。  
  
 次の例では、正規表現 `\b[A-Z](\w*\s+){1,10}?[.!?]` は、1 個以上 10 個以下の単語が含まれる文に一致します。 18 個の単語が含まれている 1 つの文を除き、入力文字列中のすべての文に一致します。  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 正規表現パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`[A-Z]`|A から Z の大文字と一致します。|  
|`(\w*\s+)`|単語に含まれる 0 個以上の文字の後に空白文字が 1 個以上続くパターンと一致します。 これが最初のキャプチャ グループです。|  
|`{1,10}?`|前のパターンの 1 回以上 10 回以下の繰り返しのうち、最も少ない繰り返しに一致します。|  
|`[.!?]`|区切り文字 "."、"!"、"?" のいずれか 1 文字と一致します。|  
  
<a name="Greedy"></a>   
## <a name="greedy-and-lazy-quantifiers"></a>最長一致と最短一致の量指定子  
 いくつかの量指定子には次の 2 つのバージョンがあります。  
  
-   最長一致バージョン。  
  
     最長一致の量指定子は、要素をできるだけ多く一致させようとします。  
  
-   最短一致 (または遅延) のバージョンです。  
  
     最短一致の量指定子は、要素をできるだけ少なく一致させようとします。 追加するだけで、最短に最短一致の量指定子を有効にすることができます、`?`です。  
  
 クレジット カード番号などの数値の列から最後の 4 桁の数字を取り出す、単純な正規表現について考えてみます。 使用する正規表現のバージョン、`*`最長一致の量指定子は`\b.*([0-9]{4})\b`します。 しかし、2 個の数値が含まれている文字列の場合、この正規表現は、次の例に示すように 2 番目の数値の最後の 4 桁の数字だけに一致します。  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 最初の数値を照合するために、正規表現が失敗した、`*`全体の文字列では、可能な回数だけ直前の要素を一致させようとして、文字列の末尾に一致するものを検索するためです。  
  
 これは期待した動作ではありません。 代わりに、使用することができます、`*?`量指定子を次の例のように、両方の数値から桁の数字を抽出します。  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 多くの場合、最長一致と最短一致の量指定子を使用した正規表現は、同じ一致結果を返します。 ワイルドカードを使用するときに最もよく異なる結果を返すこと (`.`) メタ文字、任意の文字に一致します。  
  
## <a name="quantifiers-and-empty-matches"></a>量指定子と空一致  
 量指定子`*`、 `+`、および`{`  *n*  `,` *m* `}`対応遅延することはありませんごとに繰り返す空とキャプチャの最小数が見つかった場合に一致します。 この規則により、可能なグループ キャプチャの最大回数が無限またはほぼ無限のときに、量指定子が空の部分式一致の無限ループに入ることを回避できます。  
  
 たとえば、次のコードはへの呼び出しの結果を示しています。、<xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType>正規表現パターンを持つメソッド`(a?)*`、0 回以上"a"の 0 個または 1 つの文字に一致します。 注を単一のキャプチャ グループをキャプチャ"a"とも<xref:System.String.Empty?displayProperty=nameWithType>が、その最初の空一致により、量化子を終了するため、2 つ目の空一致はありません。  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 最小回数と最大回数のキャプチャを定義するキャプチャ グループと固定回数のキャプチャを定義するキャプチャ グループとの間の実際の違いを確認するために、正規表現パターンの `(a\1|(?(1)\1)){0,2}` と `(a\1|(?(1)\1)){2}` について検討します。 どちらの正規表現も、次の表に示すように定義される単一のキャプチャ グループで構成されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`(a\1`|"a" と最初のキャプチャ グループの値に一致します …|  
|`&#124;(?(1)`|… または、最初のキャプチャ グループが定義されているかどうかをテストします。 (なお、`(?(1)`構成体はキャプチャ グループが定義されていません)。|  
|`\1))`|最初のキャプチャ グループが存在する場合、その値と一致します。 グループが存在しない場合、グループが一致<xref:System.String.Empty?displayProperty=nameWithType>です。|  
  
 最初の正規表現では 0 ～ 2 回、このパターンとの照合が行われます。2 番目の正規表現では、厳密に 2 回です。 最初のパターンがの最初のキャプチャとキャプチャの最小数に達したため<xref:System.String.Empty?displayProperty=nameWithType>、一致を試みることはありませんが繰り返される`a\1`;`{0,2}`量指定子は、前回のイテレーションで空一致だけを許可します。 一方、2 番目の正規表現では、2 回目の `a\1` が評価されるため、"a" に一致します。繰り返しの最小回数は 2 で、空一致の後でエンジンが繰り返さなければならない回数になります。  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [正規表現言語 - クイック リファレンス](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)  
 [バックトラッキング](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)
