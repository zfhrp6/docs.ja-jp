---
title: "正規表現での前方参照構成体 | Microsoft Docs"
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
  - ".NET Framework 正規表現, 前方参照構成体"
  - "逆参照"
  - "構成体, 前方参照"
  - "正規表現, 前方参照構成体"
ms.assetid: 567a4b8d-0e79-49dc-8df9-f4b1aa376a2a
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 正規表現での前方参照構成体
前方参照を使用すると、文字列内で繰り返し出現する文字や部分文字列を簡単に特定できます。  たとえば、入力文字列に任意の部分文字列が複数回出現する場合は、最初の出現箇所をキャプチャ グループで一致させた後に、前方参照を使用してそれ以降の出現箇所を一致させることができます。  
  
> [!NOTE]
>  置換文字列の名前付きのキャプチャ グループと番号付きのキャプチャ グループの参照には、別の構文が使用されます。  詳細については、「[置換](../../../docs/standard/base-types/substitutions-in-regular-expressions.md)」を参照してください。  
  
 .NET Framework では、番号付きのキャプチャ グループと名前付きのキャプチャ グループを参照する個別の言語要素が定義されています。  キャプチャ グループの詳細については、「[グループ化構成体](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md)」を参照してください。  
  
## 番号付き前方参照  
 番号付き前方参照では、次の構文を使用します。  
  
 `\` *number*  
  
 *number* は、正規表現のキャプチャ グループの位置です。  たとえば、`\4` を使用すると、4 番目のキャプチャ グループの内容と一致します。  *number* が正規表現パターンで定義されていない場合は、解析エラーが発生し、正規表現エンジンは <xref:System.ArgumentException>をスローします。  たとえば、正規表現 `\b(\w+)\s\1` は、`(\w+)` が式の 1 番目の唯一のキャプチャ グループであるので有効です。  これに対して、`\b(\w+)\s\2` は、`\2` の番号が付けられたキャプチャ グループが存在しないので無効であり、引数の例外がスローされます。  
  
 同じ表記を使用する `\`*number* の前方参照と 8 のエスケープ コードがあいまいです \(`\16`など\) にします。  このあいまいさは次のように解決されます。  
  
-   `\1` から `\9` までの式は常に前方参照と解釈され、8 進コードとは解釈されません。  
  
-   複数桁の式の最初の桁が 8 または 9 の場合 \(`\80` や `\91` など\)、その式はリテラルと解釈されます。  
  
-   `\10` 以降の式は、その番号に対応する前方参照がある場合には、前方参照と見なされます。それ以外の場合は、8 進コードと解釈されます。  
  
-   未定義のグループ番号への前方参照が正規表現にある場合は、解析エラーが発生し、正規表現エンジンから <xref:System.ArgumentException> がスローされます。  
  
 あいまいさが問題になる場合は、明確、8 進文字コードと混同できない `\k<`*name*`>` 表記法を使用できます。  同様に、`\xdd` などの 16 進コードにもあいまいさがないため、前方参照と混同されることはありません。  
  
 次の例では、文字列内で、単語に使用される文字のうち重複する文字を検索します。  この例では、次の要素で構成される正規表現 `(\w)\1` が定義されています。  
  
|要素|説明|  
|--------|--------|  
|`(\w)`|単語に使用される文字と一致し、その文字を 1 番目のキャプチャ グループに代入します。|  
|`\1`|次に出現した、1 番目のキャプチャ グループの値と同じ文字と一致します。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference1.cs#1)]
 [!code-vb[RegularExpressions.Language.Backreferences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference1.vb#1)]  
  
## 名前付き前方参照  
 名前付き前方参照は、次の構文を使用して定義します。  
  
 `\k<` *name* `>`  
  
 または  
  
 `\k'` *name* `'`  
  
 *name* が正規表現パターンで定義されているキャプチャ グループの名前です。  *name* が正規表現パターンで定義されていない場合は、解析エラーが発生し、正規表現エンジンは <xref:System.ArgumentException>をスローします。  
  
 次の例では、文字列内で、単語に使用される文字のうち重複する文字を検索します。  この例では、次の要素で構成される正規表現 `(?<char>\w)\k<char>` が定義されています。  
  
|要素|説明|  
|--------|--------|  
|`(?<char>\w)`|単語に使用される文字と一致し、その文字を `char` という名前のキャプチャ グループに代入します。|  
|`\k<char>`|次に出現した、`char` キャプチャ グループの値と同じ文字と一致します。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference2.cs#2)]
 [!code-vb[RegularExpressions.Language.Backreferences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference2.vb#2)]  
  
 *name* には、数値の文字列形式である場合があることに注意してください。  たとえば、次の例では、正規表現 `(?<2>\w)\k<2>` を使用して、文字列内で、単語に使用される文字のうち重複する文字を検索します。  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference3.cs#3)]
 [!code-vb[RegularExpressions.Language.Backreferences#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference3.vb#3)]  
  
## 前方参照で一致する対象  
 前方参照は、最も近いグループ定義 \(左から右に検索する場合、左側の最も近いところにある定義\) を参照します。  1 つのグループで複数のキャプチャが行われる場合、前方参照は最も近いキャプチャを参照します。  
  
 次の例では、\\1 名前付きグループを再定義する正規表現パターン `(?<1>a)(?<1>\1b)*` を使用しています。  この正規表現の各パターンの説明を次の表に示します。  
  
|パターン|説明|  
|----------|--------|  
|`(?<1>a)`|文字 "a" と一致し、結果を `1` という名前のキャプチャ グループに代入します。|  
|`(?<1>\1b)*`|`1` という名前のグループに "b" を加えた文字列に 0 回または 1 回一致し、結果を `1` という名前のキャプチャ グループに代入します。|  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference4.cs#4)]
 [!code-vb[RegularExpressions.Language.Backreferences#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference4.vb#4)]  
  
 正規表現と入力文字列 \("aababb"\) の比較時、正規表現エンジンは次の操作を実行します。  
  
1.  文字列の先頭から開始し、"a" と式 `(?<1>a)` の一致に成功します。  `1` グループの値は "a" になります。  
  
2.  2 番目の文字に進み、文字列 "ab" と式 `\1b` \(つまり "ab"\) の一致に成功します。  結果の "ab" を `\1` に代入します。  
  
3.  4 番目の文字に進みます。  式 `(?<1>\1b)` は 0 回以上一致するので、文字列 "abb" と式 `\1b` の一致に成功します。  結果の "abb" を `\1` に代入します。  
  
 この例では、`*` はループ量指定子であるので、定義されているパターンと一致する文字列がなくなるまで、繰り返し評価されます。  量指定子によるループが行われても、グループ定義はクリアされません。  
  
 あるグループによってキャプチャされる部分文字列がない場合は、そのグループへの前方参照は未定義になるため、一致する文字列は見つかりません。  このことを、次のように定義される正規表現パターン `\b(\p{Lu}{2})(\d{2})?(\p{Lu}{2})\b` を使用して示します。  
  
|パターン|説明|  
|----------|--------|  
|`\b`|ワード境界から照合を開始します。|  
|`(\p{Lu}{2})`|2 個の大文字と一致します。  これが最初のキャプチャ グループです。|  
|`(\d{2})?`|2 桁の 10 進数と 0 回または 1 回一致します。  これが 2 番目のキャプチャ グループです。|  
|`(\p{Lu}{2})`|2 個の大文字と一致します。  これが 3 番目のキャプチャ グループです。|  
|`\b`|ワード境界で照合を終了します。|  
  
 2 番目のキャプチャ グループで定義されている 2 桁の 10 進数が存在しない場合でも、入力文字列とこの正規表現を一致させることができます。  次の例では、一致する対象は見つかりますが、一致する対象が見つかった 2 つのキャプチャ グループの間には空のキャプチャ グループがあります。  
  
 [!code-csharp[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.backreferences/cs/backreference5.cs#5)]
 [!code-vb[RegularExpressions.Language.Backreferences#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.backreferences/vb/backreference5.vb#5)]  
  
## 参照  
 [正規表現言語 \- クイック リファレンス](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)