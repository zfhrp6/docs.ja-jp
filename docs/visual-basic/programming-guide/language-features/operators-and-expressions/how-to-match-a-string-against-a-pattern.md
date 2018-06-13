---
title: '方法: 文字列がパターンに一致するかどうかを調べる (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: aef378bfc32d6deff431a2caac1261a6cd7520c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655213"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>方法: 文字列がパターンに一致するかどうかを調べる (Visual Basic)
式かどうかを検索する場合、[文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)を使用して、パターンを満たす、 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)です。  
  
 `Like` 2 つのオペランドを受け取ります。 左のオペランドは、文字列式であり、右のオペランドが、照合に使用するパターンを含む文字列。 `Like` 返します、`Boolean`文字列式が、パターンを満たすかどうかを示す値。  
  
 特定の文字、ワイルドカード文字、文字のリスト、または文字の範囲に対して文字列式内の各文字に一致することができます。 パターン文字列に指定された位置は、文字列式に一致する文字の位置に対応します。  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>特定の文字の文字列式の文字と一致するには  
  
-   特定の文字をパターン文字列に直接配置します。 特定の特殊文字は、角かっこで囲む必要があります (`[ ]`)。 詳細については、次を参照してください。 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)です。  
  
     次の例のテストするかどうか`myString`だけの 1 つの文字から成る`H`です。  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>ワイルドカード文字の文字列式の文字と一致するには  
  
-   疑問符 () の配置 (`?`) パターン文字列にします。 この位置での任意の有効な文字は、検索が成功します。  
  
     次の例のテストかどうか`myString`単一の文字から成る`W`任意の値の 2 つの英文字で構成します。  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>文字の一覧に対して文字列式の文字と一致するには  
  
-   角かっこの配置 (`[ ]`) 文字のリストを置く角かっこ内とパターン文字列にします。 コンマまたはその他の任意の区切り記号の文字を分離されません。 リスト内の任意の 1 文字は、検索が成功します。  
  
     次の例のテストするかどうか`myString`続けて、文字の 1 つだけの任意の有効な文字から成る`A`、 `C`、または`E`です。  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     この照合の大文字小文字を区別に注意してください。  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>文字の範囲に対して文字列式の文字と一致するには  
  
-   角かっこの配置 (`[ ]`)、ハイフンで区切られたパターン文字列に、最低と最高の文字を範囲に、かっこ内 (`–`)。 範囲内の任意の 1 文字は、検索が成功します。  
  
     次の例のテストするかどうか`myString`文字から成る`num`続けて、文字の 1 つだけ`i`、 `j`、 `k`、 `l`、 `m`、または`n`です。  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     この照合の大文字小文字を区別に注意してください。  
  
## <a name="matching-empty-strings"></a>空の文字列に一致します。  
 `Like` シーケンスを扱う`[]`長さ 0 の文字列として (`""`)。 使用することができます`[]`文字列全体の式が空、ですが、文字列式で特定の位置が空かどうかを行うことはできないかどうかをテストします。 空の位置は、オプションのいずれかの場合は、テストする、使用できる必要があります。`Like`も複数回です。  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>一覧の文字または文字の文字列式の文字と一致するには  
  
1.  呼び出す、`Like`演算子と同じで 2 回、式の文字列と接続し、2 つの呼び出しか、[または演算子](../../../../visual-basic/language-reference/operators/or-operator.md)または[OrElse 演算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)です。  
  
2.  最初のパターン文字列に`Like`句、角かっこで囲まれた、文字の一覧が含まれます (`[ ]`)。  
  
3.  2 つ目のパターン文字列に`Like`句を配置しない任意の文字位置にある問題のです。  
  
     次の例では、7 桁の電話番号`phoneNum`3 桁の数字、続けてスペース、ハイフン (`–`)、ピリオド (`.`)、文字、続くなしに 4 桁の数値。  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a>関連項目  
 [比較演算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [演算子および式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [String データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
