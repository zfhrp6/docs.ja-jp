---
title: "Like Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Like"
  - "vb.Like"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "similar to"
  - "pattern matching"
  - "Like operator [Visual Basic]"
  - "? symbol, wildcard character"
  - "string comparison [Visual Basic], Like operator"
  - "strings [Visual Basic], comparing"
  - "comparison operators"
  - "symbols, wildcard"
  - "wildcards, Like operator"
  - "strings [Visual Basic], matching"
  - "string comparison [Visual Basic], sorting data"
  - "data [Visual Basic], sorting"
  - "text [Visual Basic], comparing"
  - "operators [Visual Basic], pattern-matching"
  - "data [Visual Basic], string comparisons"
  - "string comparison [Visual Basic], Like operators"
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Like Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

文字列をパターンと比較します。  
  
## 構文  
  
```  
  
result = string Like pattern  
```  
  
## 指定項目  
 `result`  
 必ず指定します。  任意のブール型 \(`Boolean`\) の変数を指定します。  結果は、引数 `string` が引数 `pattern` に一致するかどうかを示す `Boolean` 値です。  
  
 `string`  
 必ず指定します。  任意のブール型 \(`String`\) の式を指定します。  
  
 `pattern`  
 必ず指定します。  パターン一致規則に適合させる任意の文字列 \(`String`\) 式を指定します。規則については「解説」で説明します。  
  
## 解説  
 `string` の値が、`pattern` に含まれるパターンに一致する場合、`result` は `True` です。  文字列がパターンに一致しない場合、`result` は `False` です。  `string` と `pattern` の両方が空白文字列の場合、結果は `True` になります。  
  
## 比較メソッド  
 `Like` 演算子の動作は、[Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) によって決まります。  各ソース ファイルの既定の文字列比較メソッドは `Option Compare Binary` です。  
  
## パターン オプション  
 組み込みのパターン一致は、さまざまな文字列比較に利用できます。  パターン一致機能では、`string` 内の各文字を特定の文字、ワイルドカード文字、文字のリスト、文字の範囲と比較できます。  `pattern` に使用できる文字と、それに一致する文字を次の表に示します。  
  
|`pattern` 内の文字|`string` の一致|  
|--------------------|------------------|  
|`?`|任意の 1 文字|  
|`*`|0 個以上の文字|  
|`#`|任意の 1 桁 \(0–9\)|  
|`[` `charlist` `]`|`charlist` に含まれる任意の 1 文字|  
|`[!` `charlist` `]`|`charlist` に含まれない任意の 1 文字|  
  
## 文字のリスト  
 1 文字以上のグループ \(`charlist`\) を角かっこ \(`[ ]`\) で囲むことで、`string` に含まれる任意の 1 文字に一致する文字を検索できます。このグループには、数字など、任意の文字コードを含めることができます。  
  
 `charlist` の先頭に感嘆符 \(`!`\) を付けると、`charlist` に含まれる文字以外の任意の文字が `string` 内にあるかどうかを検索することになります。  角かっこの外側に感嘆符がある場合は、感嘆符自体を検索します。  
  
## 特殊文字  
 特殊文字の左角かっこ \(`[`\)、疑問符 \(`?`\)、シャープ記号 \(`#`\)、およびアスタリスク \(`*`\) に一致させるには、これらの文字を角かっこで囲む必要があります。  右角かっこ \(`]`\) をグループ内に使用して、その文字自体を比較することはできませんが、グループの外で独立した文字として使用することはできます。  
  
 `[]` という文字列は、長さ 0 の文字列 \(`""`\) と見なされます。  しかし、角かっこで囲まれた文字リストに含めることはできません。  `string` 内の位置に、いずれかの文字グループが含まれているか、それとも文字が含まれていないかをチェックするには、`Like` を 2 回使用します。  例については、「[How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)」を参照してください。  
  
## 文字の範囲  
 ハイフン \(`–`\) を使って範囲の上限と下限を設定することで、`charlist` に文字の範囲を指定できます。  たとえば、`[A–Z]` と指定すると、`string` 内の文字の位置に `A` から `Z` までの文字のいずれかが含まれている場合に一致となります。`[!H–L]` と指定すると、対応する文字の位置に `H` から `L` までの範囲に含まれない文字がある場合に一致となります。  
  
 文字の範囲を指定する場合、文字は昇順で指定する必要があります。  つまり、`[A–Z]` は有効なパターンですが、`[Z–A]` は無効なパターンです  
  
### 複数の文字範囲  
 同じ文字位置に対して複数の範囲を指定するには、同じ角かっこの中に、デリミターなしで範囲を指定します。  たとえば、`[A–CX–Z]` と指定すると、`string` 内の対応する文字位置に `A` から `C` まで、および `X` から `Z` までの文字が含まれているときに一致となります。  
  
### ハイフンの使用  
 ハイフン \(`–` が `charlist` の先頭 \(感嘆符がある場合はその直後\) または末尾にある場合は、ハイフン自体を検索します。  他の場所にハイフンがある場合は、ハイフンの両側の文字を上限および下限とする、文字の範囲を表します。  
  
## 照合シーケンス  
 指定した範囲の意味は、実行時に有効な文字順序により異なります。つまり、`Option` `Compare` と、コードが実行されるシステムのロケール設定で決まります。  `Option` `Compare` `Binary` では、`[A–E]` という範囲は `A`、`B`、`C`、`D`、および `E` に一致します。  `Option` `Compare` `Text` では、`[A–E]` は `A`、`a`、`À`、`à`、`B`、`b`、`C`、`c`、`D`、`d`、`E`、および `e` に一致します。  アクセント付き文字の並べ替え順序はアクセントなしの文字よりも後なので、この範囲は `Ê` および `ê` には一致しません。  
  
## Digraph 文字  
 言語によっては、独立した 2 文字を表す文字がアルファベットに含まれています。  たとえば、いくつかの言語では `æ` という文字が使用されます。これは、`a` と `e` が連続する場合に、その 2 文字を表す文字です。  `Like` 演算子では、この digraph 文字 1 文字と独立した 2 文字が同じものとして認識されます。  
  
 digraph 文字を使用する言語がシステム ロケール設定に指定されている場合、`pattern` または `string` のどちらかにその digraph 文字 1 文字が含まれると、他方の文字列では、同じ意味を持つ連続した 2 文字を検索します。  同様に、角かっこ内の `pattern` に digraph 文字 1 文字が含まれると、`string` 内では同じ意味を持つ連続した 2 文字を検索します。  
  
## オーバーロード  
 `Like` 演算子は *オーバーロード* できます。つまり、オペランドがそのクラスまたは構造体の型であれば、クラスまたは構造体がこの動作を再定義できます。  このようなクラスまたは構造体でこの演算子を使用している場合、再定義された動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 使用例  
 `Like` 演算子を使って、文字列をさまざまなパターンと比較する例を次に示します。  結果は、各文字列がパターンに一致したかどうかを示す `Boolean` 変数で表されます。  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Operators and Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)