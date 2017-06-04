---
title: "正規表現でのその他の構成体 | Microsoft Docs"
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
  - ".NET Framework 正規表現, その他の構成体"
  - "構成体, その他"
  - "正規表現, その他の構成体"
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 正規表現でのその他の構成体
.NET Framework の正規表現には、その他の言語構成要素が 3 つ含まれています。  そのうちの 1 つを使用すると、正規表現パターンの途中で特定の一致オプションを有効または無効にできます。  残りの 2 つを使用すると、正規表現にコメントを含めることができます。  
  
## インライン オプション  
 次の構文を使用すると、正規表現の一部に対して、特定のパターン一致オプションを設定したり、無効にしたりできます。  
  
```  
(?imnsx-imnsx)  
```  
  
 有効にするオプションは疑問符の後に、無効にするオプションはマイナス記号の後に指定します。  各オプションの説明を次の表に示します。  各オプションの詳細については、「[正規表現のオプション](../../../docs/standard/base-types/regular-expression-options.md)」を参照してください。  
  
|オプション|説明|  
|-----------|--------|  
|`i`|大文字と小文字を区別しない一致を指定します。|  
|`m`|複数行モードを指定します。|  
|`n`|明示的なキャプチャのみを指定します。かっこはキャプチャ グループとして機能しません。|  
|`s`|単一行モードを指定します。|  
|`x`|エスケープされない空白を無視し、x モード コメントを許可します。|  
  
 `(?imnsx-imnsx)` 構成体で定義した正規表現オプションの変更は、包含するグループの末尾まで有効です。  
  
> [!NOTE]
>  `(?imnsx-imnsx:` *subexpression* `)` のグループ化構成体は、部分式と同じ機能を提供します。  詳細については、「[グループ化構成体](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)」を参照してください。  
  
 次の例では、`i`、`n`、および `x` の各オプションを使用して、正規表現の途中で、大文字と小文字を区別しないようにし、明示的なキャプチャを有効にし、正規表現パターン内の空白を無視するようにしています。  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 この例では、2 つの正規表現を定義しています。  最初の `\b(D\w+)\s(d\w+)\b` は、大文字の "D" と小文字の "d" で始まる連続する 2 語に一致します。  2 番目の正規表現 `\b(D\w+)(?ixn) \s (d\w+) \b` は、インライン オプションを使用して、このパターンを次の表に示すように変更しています。  結果の比較により、`(?ixn)` 構成要素の効果が確認できます。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`(D\w+)`|大文字の "D" の後に単語に使用される文字が 1 個以上続くパターンに一致します。  これが最初のキャプチャ グループです。|  
|`(?ixn)`|これ以降、比較で大文字と小文字を区別しないようにし、明示的なキャプチャのみを行い、正規表現パターン内の空白を無視します。|  
|`\s`|空白文字と一致します。|  
|`(d\w+)`|大文字または小文字の "d" の後に単語に使用される文字が 1 個以上続くパターンに一致します。  `n` \(明示的なキャプチャ\) オプションが有効になっているため、このグループはキャプチャされません。|  
|`\b`|ワード境界に一致します。|  
  
## インライン コメント  
 `(?#` *comment* `)` 構造体が正規表現にインライン コメントを含めることができます。  コメントのいずれの部分も、正規表現エンジンによるパターン一致に使用されません。ただし、<xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=fullName> メソッドで返される文字列には、コメントが含まれます。  コメントは、最初の閉じかっこで終了します。  
  
 次の例では、前のセクションの例のうち、最初の正規表現パターンを使用しています。  正規表現に 2 つのインライン コメントを追加して、比較で大文字と小文字を区別するかどうかを示しています。  正規表現パターン `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b` は、次のように定義されています。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から開始します。|  
|`(?# case-sensitive comparison)`|コメント。  これは、パターン一致動作に影響しません。|  
|`(D\w+)`|大文字の "D" の後に単語に使用される文字が 1 個以上続くパターンに一致します。  これが最初のキャプチャ グループです。|  
|`\s`|空白文字と一致します。|  
|`(?ixn)`|これ以降、比較で大文字と小文字を区別しないようにし、明示的なキャプチャのみを行い、正規表現パターン内の空白を無視します。|  
|`(?#case-insensitive comparison)`|コメント。  これは、パターン一致動作に影響しません。|  
|`(d\w+)`|大文字または小文字の "d" の後に単語に使用される文字が 1 個以上続くパターンに一致します。  これが 2 番目のキャプチャ グループです。|  
|`\b`|ワード境界に一致します。|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## 行末コメント  
 シャープ記号 \(`#`\) は x モード コメントを示します。このコメントは、正規表現パターンの末尾にあるエスケープされない \# 文字から行末までです。  この構成体を使用するには、`x` オプションを \(インライン オプションで\) 有効にするか、<xref:System.Text.RegularExpressions.Regex> オブジェクトのインスタンス化時または <xref:System.Text.RegularExpressions.Regex> 静的メソッドの呼び出し時に <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 値を `option` パラメーターに指定する必要があります。  
  
 行末コメント構成体を次の例に示します。  この例では、文字列が、1 つ以上の書式指定項目を含む複合書式指定文字列であるかどうかを判断しています。  正規表現パターンの構成要素の説明を次の表に示します。  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|パターン|説明|  
|----------|--------|  
|`\{`|左中かっこ \({\) に一致します。|  
|`\d+`|1 個以上の 10 進数と一致します。|  
|`(,-*\d+)*`|コンマの後に省略可能なマイナス記号、その後に 1 個以上の 10 進数が続くパターンに 0 回または 1 回一致します。|  
|`(\:\w{1,4}?)*`|コロンの後に 1 ～ 4 個の \(できるだけ少ない\) 空白文字が続くパターンに 0 回または 1 回一致します。|  
|`(?#case insensitive comparison)`|インライン コメントです。  これは、パターン一致動作に影響しません。|  
|`\}`|右中かっこ \(}\) に一致します。|  
|`(?x)`|行末コメントが認識されるように、パターンの空白を無視するオプションを有効にします。|  
|`# Looks for a composite format item.`|行末コメントです。|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 正規表現に `(?x)` 構成要素を指定する代わりに、<xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=fullName> メソッドを呼び出して <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 列挙値を渡すことによっても、コメントを認識されるようにすることができます。  
  
## 参照  
 [正規表現言語 \- クイック リファレンス](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)