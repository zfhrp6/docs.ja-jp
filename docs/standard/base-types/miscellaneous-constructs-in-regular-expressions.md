---
title: "正規表現でのその他の構成体"
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
- constructs, miscellaneous
- .NET Framework regular expressions, miscellaneous constructs
- regular expressions, miscellaneous constructs
ms.assetid: 7d10d11f-680f-4721-b047-fb136316b4cd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9b33d196a7af9bc5a1f81c1624bbd98fea074319
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="miscellaneous-constructs-in-regular-expressions"></a>正規表現でのその他の構成体
.NET の正規表現には、次の 3 つのその他の言語コンストラクトが含まれます。 1 つは、正規表現パターンの途中で特定の一致オプションを有効または無効にすることができます。 残りの 2 つは、正規表現にコメントを含めることができます。  
  
## <a name="inline-options"></a>インライン オプション  
 この構文を使用して、正規表現の一部の特定のパターン一致オプションを設定または無効にできます。  
  
```  
(?imnsx-imnsx)  
```  
  
 疑問符の後に有効にするオプション、マイナス記号の後に無効にするオプションを指定します。 各オプションの説明を次の表に示します。 各オプションの詳細については、「[正規表現のオプション](../../../docs/standard/base-types/regular-expression-options.md)」を参照してください。  
  
|オプション|説明|  
|------------|-----------------|  
|`i`|大文字と小文字を区別しない一致。|  
|`m`|複数行モードを指定します。|  
|`n`|明示的なキャプチャのみ (かっこはキャプチャ グループとして機能しません)。|  
|`s`|単一行モード。|  
|`x`|エスケープされていない空白を無視し、x モード コメントを許可します。|  
  
 によって定義された正規表現のオプションを変更しても、`(?imnsx-imnsx)`外側のグループが終了するまで有効ではままを構築します。  
  
> [!NOTE]
>  `(?imnsx-imnsx:` *Subexpression* `)`グループ化構成体は、部分式と同じ機能を提供します。 詳しくは、「[正規表現でのグループ化構成体](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)」をご覧ください。  
  
 次の例では、 `i`、 `n`、および`x`オプションの大文字小文字を区別しないと、明示的なキャプチャを有効にして、正規表現の途中で正規表現パターンの空白を無視します。  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous1.cs#1)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous1.vb#1)]  
  
 この例では、2 つの正規表現を定義しています。 最初の `\b(D\w+)\s(d\w+)\b` は、大文字の "D" と小文字の "d" で始まる 2 つの連続した単語に一致します。 2 つ目の正規表現 `\b(D\w+)(?ixn) \s (d\w+) \b` は、次の表に示すように、インライン オプションを使用して、このパターンを変更します。 結果の比較で、`(?ixn)` コンストラクトの効果を確認します。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`(D\w+)`|大文字 "D" の後に 1 つ以上の単語の文字が続くパターンに一致します。 これが最初のキャプチャ グループです。|  
|`(?ixn)`|この時点から、大文字と小文字を区別しない比較を行い、明示的なキャプチャのみを行って、正規表現パターン内の空白を無視します。|  
|`\s`|空白文字と一致します。|  
|`(d\w+)`|大文字または小文字 "d" の後に 1 つ以上の単語の文字が続くパターンに一致します。 このグループはキャプチャされません、 `n` (明示的なキャプチャ) オプションが有効になっている.|  
|`\b`|ワード境界に一致します。|  
  
## <a name="inline-comment"></a>インライン コメント  
 `(?#` *コメント*`)`コンストラクトでは、正規表現で、インライン コメントを追加できます。 によって返される文字列にコメントが含まれています、正規表現エンジンが、パターン マッチでコメントの任意の部分を使用しない、<xref:System.Text.RegularExpressions.Regex.ToString%2A?displayProperty=nameWithType>メソッドです。 コメントは、最初の閉じかっこで終了します。  
  
 次の例では、前のセクションの例の最初の正規表現パターンを繰り返しています。 比較で大文字小文字を区別するかどうかを示す 2 つのインライン コメントを正規表現に追加しています。 正規表現パターン `\b((?# case-sensitive comparison)D\w+)\s((?#case-insensitive comparison)d\w+)\b` は、次のように定義されます。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から開始します。|  
|`(?# case-sensitive comparison)`|コメント。 これは、パターンマッチング動作に影響を与えません。|  
|`(D\w+)`|大文字 "D" の後に 1 つ以上の単語の文字が続くパターンに一致します。 これが最初のキャプチャ グループです。|  
|`\s`|空白文字と一致します。|  
|`(?ixn)`|この時点から、大文字と小文字を区別しない比較を行い、明示的なキャプチャのみを行って、正規表現パターン内の空白を無視します。|  
|`(?#case-insensitive comparison)`|コメント。 これは、パターンマッチング動作に影響を与えません。|  
|`(d\w+)`|大文字または小文字 "d" の後に 1 つ以上の単語の文字が続くパターンに一致します。 これが 2 番目のキャプチャ グループです。|  
|`\b`|ワード境界に一致します。|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous2.cs#2)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous2.vb#2)]  
  
## <a name="end-of-line-comment"></a>行末のコメント  
 番号記号 (`#`)、正規表現パターンの末尾にエスケープされていない # 文字から開始され、行の末尾まで続きます x モード コメントをマークします。 このコンストラクトを使用する必要がありますか有効にする、 `x` (インライン オプション) を介してオプションかを指定、<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>値を`option`パラメーターをインスタンス化するときに、<xref:System.Text.RegularExpressions.Regex>オブジェクトまたは静的なを呼び出して<xref:System.Text.RegularExpressions.Regex>メソッドです。  
  
 次の例は、行末のコメント コンストラクトを示しています。 これは、1 つ以上の書式指定項目を含む複合書式文字列かどうかを判断します。 次の表に、正規表現パターン内のコンストラクトを説明しています。  
  
 `\{\d+(,-*\d+)*(\:\w{1,4}?)*\}(?x) # Looks for a composite format item.`  
  
|パターン|説明|  
|-------------|-----------------|  
|`\{`|左中かっこと一致します。|  
|`\d+`|1 個以上の 10 進数と一致します。|  
|`(,-*\d+)*`|0 個または 1 つのコンマの後にオプションのマイナス記号が続き、その後に 1 つ以上の 10 進数が続くパターンと一致します。|  
|`(\:\w{1,4}?)*`|0 個または 1 つのコロンの後に 1 ～ 4 個の、ただし可能な限り少ない空白文字が続くパターンと一致します。|  
|`(?#case insensitive comparison)`|インライン コメント。 これは、パターンマッチング動作に影響を与えません。|  
|`\}`|右中かっこと一致します。|  
|`(?x)`|行末のコメントが認識されるように、パターンの空白を無視するオプションを有効にします。|  
|`# Looks for a composite format item.`|行末のコメント。|  
  
 [!code-csharp[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.miscellaneous/cs/miscellaneous3.cs#3)]
 [!code-vb[RegularExpressions.Language.Miscellaneous#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.miscellaneous/vb/miscellaneous3.vb#3)]  
  
 なお、提供する代わりに、`(?x)`構築、正規表現内で、コメントでしたも認識されたを呼び出して、<xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>メソッドを渡すこと、<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>列挙値。  
  
## <a name="see-also"></a>関連項目  
 [正規表現言語 - クイック リファレンス](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
