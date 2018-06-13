---
title: Boolean 式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: ff5843c815658468ac69fe5d62a9ea4cac2be830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655799"
---
# <a name="boolean-expressions-visual-basic"></a>Boolean 式 (Visual Basic)
A*ブール式*の値に評価される式を指定、[ブールのデータ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md):`True`または`False`です。 `Boolean` 式は、いくつかの形式を取ります。 単純な形式の値を直接比較、`Boolean`変数を`Boolean`リテラルで、次の例に示すようにします。  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a>2 つの意味、= 演算子  
 注意して代入ステートメント`newCustomer = True`前の例では、内の式と同じように見えますが、別の関数を実行して別々 に使用されます。 前の例では、式で`newCustomer = True`ブール値を表す、`=`記号は、比較演算子として解釈されます。 スタンドアロンのステートメントで、`=`記号、代入演算子と解釈され、左側にある変数の右側にある値を割り当てます。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 詳細については、次を参照してください。[値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)と[ステートメント](../../../../visual-basic/language-reference/statements/index.md)です。  
  
## <a name="comparison-operators"></a>比較演算子  
 比較演算子など`=`、 `<`、 `>`、 `<>`、 `<=`、および`>=`右側にある式を演算子の左辺の式を比較することでブール式を生成演算子と、結果としての評価の`True`または`False`です。 次に例を示します。  
  
 `42 < 81`  
  
 前の例でブール式の評価が 42 は 81 未満であるため、`True`です。 この種類の式の詳細については、次を参照してください。[値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)です。  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>論理演算子と組み合わせて使用する比較演算子  
 比較式より複雑なブール式を生成するために論理演算子を使用して結合できます。 次の例では、論理演算子で組み合わせて比較演算子の使用を示します。  
  
 `x > y And x < 1000`  
  
 前の例で、全体的な式の値がのそれぞれの側に式の値に依存、`And`演算子。 両方の式が場合`True`、全体的な式に評価し、`True`です。 いずれかの式が場合`False`、全体の式に評価し、`False`です。  
  
## <a name="short-circuiting-operators"></a>ショート サーキット演算子  
 論理演算子`AndAlso`と`OrElse`と呼ばれる現象が発生*ショート サーキット*です。 ショート サーキット演算子は、まず、左側のオペランドを評価します。 左側のオペランドでは、式全体の値を決定、右の式を評価することがなくプログラムの実行が処理されます。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 前の例で、演算子は左の式を評価`45 < 12`です。 左の式が評価されるため`False`、全体の論理式を評価する`False`です。 プログラムの実行がそのためのコードの実行をスキップ、`If`右の式を評価することがなくブロック`testFunction(3)`です。 この例は呼び出しません`testFunction()`左の式が式全体を falsifies ためです。  
  
 同様に場合、左の式を使用して、論理式で`OrElse`に評価される`True`、左の式が既に全体を検証するため、右の式を評価することがなく次のコード行に実行されます式。  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>非ショート サーキット演算子との比較  
 これに対し、論理演算子の両側が評価されるときに、論理演算子`And`と`Or`使用されます。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 上記の例では、 `testFunction()` 、左の式を評価する場合でも`False`です。  
  
## <a name="parenthetical-expressions"></a>かっこで囲んだ式  
 ブール式の評価の順序を制御するのにかっこを使用することができます。 かっこで囲まれた式が最初に評価されます。 複数のレベルの入れ子では、優先順位が最も深く入れ子になった式に付与されます。 かっこ内では、演算子の優先順位の規則に従って評価が続行されます。 詳細については、次を参照してください。 [Visual Basic の演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における論理/ビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [ステートメント](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [比較演算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Boolean データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
