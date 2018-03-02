---
title: "正規表現での前方参照構成体"
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
- backreferences
- constructs, backreference
- .NET Framework regular expressions, backreference constructs
- regular expressions, backreference constructs
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2ec92933bdf123412a3d489fc493d76c4a0dc0d0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="backreference-constructs-in-regular-expressions"></a>正規表現での前方参照構成体
前方参照は、文字列内の繰り返しの文字または部分文字列を識別するために便利な方法を提供します。 たとえば、入力文字列に複数回出現する任意の部分文字列が含まれている場合は、キャプチャ グループを使用して最初の一致を検出し、前方参照を使用して部分文字列の後続の出現箇所を見つけます。  
  
> [!NOTE]
>  別の構文を使用して、置換文字列内の名前付きおよび番号付きのキャプチャ グループを参照します。 詳細については、「 [Substitutions](substitutions-in-regular-expressions.md)」を参照してください。  
  
 .NET では、番号付きおよび名前付きのキャプチャ グループを参照する個別の言語要素が定義されています。 キャプチャ グループの詳細については、「[グループ化コンストラクト](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)」を参照してください。  
  
## <a name="numbered-backreferences"></a>番号付き前方参照  
 番号付き前方参照は、次の構文を使用します。  
  
 `\` *number*  
  
 ここで、*number* は、正規表現でのキャプチャ グループの位置を表す序数です。 たとえば、`\4` は 4 番目のキャプチャ グループの内容と一致します。 *number* が正規表現パターンで定義されていない場合は、解析エラーが発生し、正規表現エンジンが <xref:System.ArgumentException> をスローします。 たとえば、正規表現 `\b(\w+)\s\1` は有効です (`(\w+)` が式の中の最初で唯一のキャプチャ グループであるため)。 これに対して、`\b(\w+)\s\2` は無効であり、引数の例外がスローされます (`\2` という番号のキャプチャ グループは存在しないため)。  
  
 同じ表記法を使用した、8 進数のエスケープ コード (`\16` など) と `\`*number* 前方参照との間には、あいまいさがあることに注意してください。 このあいまいさは、次のように解決されます。  
  
-   `\1` から `\9` までの式は、8 進数コードとしてではなく、常に前方参照として解釈されます。  
  
-   複数桁の式の最初の桁が 8 または 9 (`\80`や `\91`) の場合、式はリテラルとして解釈されます。  
  
-   `\10` 以降の式は、その番号に対応する前方参照がある場合、前方参照として解釈されます。それ以外の場合は、8 進数のコードとして解釈されます。  
  
-   正規表現に未定義のグループ番号への前方参照が含まれる場合、解析エラーが発生し、正規表現エンジンが <xref:System.ArgumentException> をスローします。  
  
 あいまいさが問題になる場合は、`\k<`*name*`>` という表記を使用できます。この表記はあいまいではなく、8 進数の文字コードと混同することはありません。 同様に、`\xdd` などの 16 進数コードはあいまいではなく、前方参照と混同することはありません。  
  
 次の例では、文字列内の単語に使用される重複した文字を検索します。 例で定義している正規表現 `(\w)\1` は、次の要素で構成されています。  
  
|要素|説明|  
|-------------|-----------------|  
|`(\w)`|単語文字を検出し、最初のキャプチャ グループに割り当てます。|  
|`\1`|最初のキャプチャ グループの値と同じ次の文字を検出します。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## <a name="named-backreferences"></a>名前付き前方参照  
 名前付き前方参照は、次の構文を使用して定義します。  
  
 `\k<` *name* `>`  
  
 または  
  
 `\k'` *name* `'`  
  
 ここで、*name* は正規表現パターンで定義されたキャプチャ グループの名前です。 *name* が正規表現パターンで定義されていない場合は、解析エラーが発生し、正規表現エンジンが <xref:System.ArgumentException> をスローします。  
  
 次の例では、文字列内の単語に使用される重複した文字を検索します。 例で定義している正規表現 `(?<char>\w)\k<char>` は、次の要素で構成されています。  
  
|要素|説明|  
|-------------|-----------------|  
|`(?<char>\w)`|単語文字を検出し、`char` という名前のキャプチャ グループに割り当てます。|  
|`\k<char>`|`char` キャプチャ グループの値と同じ次の文字を検出します。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 *name* は数字の文字列表現とすることもできます。 たとえば、次の例では正規表現 `(?<2>\w)\k<2>` を使用して、文字列内の単語の重複した文字を検索します。  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## <a name="what-backreferences-match"></a>前方参照と一致する内容  
 前方参照は、グループの最新の定義 (左から右に検出する場合は、すぐ左にある定義) を参照します。 1 つのグループで複数のキャプチャが発生した場合、前方参照は最新のキャプチャを参照します。  
  
 次の例には、正規表現パターン `(?<1>a)(?<1>\1b)*` が含まれています。このパターンは \1 の名前付きグループを再定義します。 正規表現の各パターンは、次の表に示すように定義されています。  
  
|パターン|説明|  
|-------------|-----------------|  
|`(?<1>a)`|文字 "a" を検出し、結果を `1` という名前のキャプチャ グループに割り当てます。|  
|`(?<1>\1b)*`|`1` という名前のグループの 0 個または 1 個の出現箇所を "b" と共に検出し、結果を `1` という名前のキャプチャ グループに割り当てます。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 正規表現を入力文字列 ("aababb") と比較する際、正規表現エンジンは次の操作を実行します。  
  
1.  文字列の先頭から開始し、式 `(?<1>a)` で "a" を検出します。 グループ `1` の値が "a" になります。  
  
2.  次の文字に進み、式 `\1b` で文字列 "ab" を検出します。 次に、その結果 "ab" を `\1` に割り当てます。  
  
3.  これにより 4 番目の文字に進みます。 式 `(?<1>\1b)` を 0 回以上照合し、式 `\1b` で文字列 "abb" を検出します。 その結果 "abb" を `\1` に割り当てます。  
  
 この例では、`*` はループ量指定子であり、正規表現エンジンが定義したパターンを照合できなくなるまで、繰り返し評価されます。 ループ量指定子によってグループの定義はクリアされません。  
  
 グループで部分文字列がキャプチャされなかった場合、そのグループへの前方参照は未定義になり、一致することはありません。 次のように定義されている正規表現パターン `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` を例として示します。  
  
|パターン|説明|  
|-------------|-----------------|  
|`\b`|ワード境界から照合を開始します。|  
|`(\p{Lu}{2})`|2 つの大文字と一致します。 これが最初のキャプチャ グループです。|  
|`(\d{2})?`|2 桁の 10 進数の 0 回または 1 回の出現と一致します。 これが 2 番目のキャプチャ グループです。|  
|`(\p{Lu}{2})`|2 つの大文字と一致します。 これが 3 番目のキャプチャ グループです。|  
|`\b`|ワード境界で照合を終了します。|  
  
 2 番目のキャプチャ グループによって定義されている 2 桁の 10 進数が存在しない場合でも、入力文字列はこの正規表現を照合できます。 次の例では、一致が見つかった場合でも、成功した 2 つのキャプチャ グループの間に空のキャプチャ グループが検出されます。  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## <a name="see-also"></a>参照  
 [正規表現言語 - クイック リファレンス](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
