---
title: Like 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: a9c672a397510c69c9ee67358689feff80d8831a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605421"
---
# <a name="like-operator-visual-basic"></a>Like 演算子 (Visual Basic)
文字列をパターンと比較します。  
  
## <a name="syntax"></a>構文  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 どの`Boolean`変数。 結果は、`Boolean`を示す値かどうか、`string`満たす、`pattern`です。  
  
 `string`  
 必須。 任意のブール型 (`String`) の式を指定します。  
  
 `pattern`  
 必須。 どの`String`「解説」で説明したパターン マッチの規則に適合させる式  
  
## <a name="remarks"></a>コメント  
 場合の値`string`に含まれているパターンを満たす`pattern`、`result`は`True`します。 文字列は、パターンが満たされない場合`result`は`False`します。 両方`string`と`pattern`空の文字列は、結果は`True`します。  
  
## <a name="comparison-method"></a>比較メソッド  
 動作、`Like`演算子によって異なります、 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)です。 各ソース ファイルの既定の文字列比較メソッドが`Option Compare Binary`です。  
  
## <a name="pattern-options"></a>パターンのオプション  
 組み込みのパターンに一致する文字列比較のための多機能なツールを提供します。 内の各文字に一致することは、パターン マッチング機能`string`に対して特定の文字やワイルドカード文字、文字一覧は、文字の範囲です。 次の表で使用できる文字`pattern`一致したとします。  
  
|内の文字 `pattern`|内の一致 `string`|  
|-----------------------------|-------------------------|  
|`?`|任意の 1 文字|  
|`*`|0 個以上の文字|  
|`#`|任意の 1 つの数字 (0 ~ 9)|  
|`[charlist]`|内の任意の 1 文字 `charlist`|  
|`[!charlist]`|内にない任意の 1 文字 `charlist`|  
  
## <a name="character-lists"></a>文字の一覧  
 1 つ以上の文字グループ (`charlist`) 角かっこで囲む (`[ ]`) 任意の 1 文字に一致に使用できる`string`桁の数字を含む、ほぼすべての文字コードを含めることができます。  
  
 感嘆符 (`!`) の先頭に`charlist`内の文字を除く任意の文字の場合、一致が行われたことを意味`charlist`で見つかった`string`です。 使用すると、角かっこの外側、感嘆符文字自体と一致します。  
  
## <a name="special-characters"></a>特殊文字  
 特殊文字の左角かっこの一致するように (`[`)、疑問符 (?) (`?`)、番号記号 (`#`)、およびアスタリスク (`*`)、角かっこで囲みます。 右の角かっこ (`]`) 自体を一致するように、グループ内で使用できませんが、グループの外側で個々 の文字として使用することができます。  
  
 文字シーケンス`[]`は長さ 0 の文字列と見なされます (`""`)。 ただし、角かっこで囲まれた文字の一覧の一部にすることはできません。 内の位置かどうかを確認する場合`string`1 つを使用できる文字または文字のグループの`Like`2 回クリックします。 例については、次を参照してください。[する方法: 文字列をパターンに一致](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)です。  
  
## <a name="character-ranges"></a>文字範囲  
 ハイフンを使用して (`–`) 下と、範囲の上限を分離する`charlist`文字の範囲を指定できます。 たとえば、`[A–Z]`場合は、対応する文字の位置で一致する結果`string`範囲内で任意の文字が含まれています`A`–`Z`、および`[!H–L]`結果と一致する場合は、対応する文字の位置範囲外の任意の文字を含む`H`–`L`です。  
  
 文字の範囲を指定する場合は、昇順で並べ替え、つまり、昇順に表示する必要があります。 したがって、`[A–Z]`は有効なパターンが`[Z–A]`はありません。  
  
### <a name="multiple-character-ranges"></a>複数の文字範囲  
 同じ文字の位置の複数の範囲を指定するには、区切り記号は任意の同じ角かっこ内でそれらを配置します。 たとえば、`[A–CX–Z]`場合は、対応する文字の位置で一致する結果`string`、いずれかの範囲内の任意の文字が含まれています`A`–`C`または範囲`X`–`Z`です。  
  
### <a name="usage-of-the-hyphen"></a>ハイフンの使用  
 ハイフン (`–`) が先頭 (感嘆符、存在する場合)、またはの最後に表示される`charlist`自体を一致するようにします。 その他の任意の場所では、ハイフンはハイフンの両側の文字が区切り文字の範囲を識別します。  
  
## <a name="collating-sequence"></a>照合順序  
 指定された範囲の意味は、文字によって決定される、実行時に順序によって異なります。`Option``Compare`システムのロケール設定で、コードが実行されているとします。 `Option``Compare``Binary`、範囲`[A–E]`と一致する`A`、 `B`、 `C`、 `D`、および`E`です。 `Option``Compare``Text`、`[A–E]`と一致する`A`、 `a`、 `À`、 `à`、 `B`、 `b`、 `C`、 `c`、 `D`、 `d`、 `E`、および`e`です。 範囲と一致しません`Ê`または`ê`アクセント記号付き文字が並べ替え順序でアクセントのない文字の後に照合します。  
  
## <a name="digraph-characters"></a>Digraph 文字  
 一部の言語では、2 つの文字を表すアルファベットの文字があります。 たとえば、複数の言語が文字を使用して`æ`、文字を表す`a`と`e`一緒に表示されます。 `Like`演算子は、1 つ digraph 文字と 2 つの個別の文字が同等であるを認識します。  
  
 Digraph 文字を使用する言語がシステムのロケール設定で指定されている場合、いずれかで 1 つ digraph 文字の発生`pattern`または`string`他の文字列で同等の 2 文字シーケンスと一致します。 同様に、digraph の文字`pattern`角かっこで囲む (単独で、一覧、または範囲) に同等の 2 文字のシーケンスと一致`string`です。  
  
## <a name="overloading"></a>オーバーロード  
 `Like`演算子を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体を再定義できますその動作オペランドは、そのクラスまたは構造体の型を持つときにします。 コードは、このようなクラスまたは構造体で、この演算子を使用する場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
## <a name="example"></a>例  
 この例では、`Like`をさまざまなパターン文字列を比較する演算子です。 結果が入ります、`Boolean`各文字列がパターンを満たすかどうかを示す変数。  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [方法 : 文字列がパターンに一致するかを調べる](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
