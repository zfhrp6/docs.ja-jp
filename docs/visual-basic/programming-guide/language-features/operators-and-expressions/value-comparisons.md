---
title: 値の比較 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 6e1eda09784814d139ef94b6720b538aef30e5e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649608"
---
# <a name="value-comparisons-visual-basic"></a>値の比較 (Visual Basic)
比較演算子は、数値変数の値を比較する式を構築するために使用できます。 これらの式を返す、`Boolean`値かどうかに基づいて、比較は true または false です。 このような式の例は次のとおりです。  
  
 `45 > 26`  
  
 `26 > 45`  
  
 最初の式の評価が`True`45 は 26 より大きいため、します。 2 番目の例を評価する`False`26 は 45 より大きいため、します。  
  
 この方法での数値式を比較することもできます。 式を比較する自体には、次の例のように、複雑な式。  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 この複合式には、リテラル、変数、および関数の呼び出しが含まれています。 比較演算子の両辺の式が評価され、結果として得られる値が使用して比較されます、`>=`比較演算子です。 左側の式の値がより大きいか、右の式の値と等しい、全体の式の評価が`True`以外の場合、評価結果が`False`です。  
  
 値を比較する式で最もよく使用`If...Then`次の例のように、構築します。  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 `=`符号は、比較演算子だけでなく、代入演算子。 比較演算子として使用する場合は、次の例で示すように、左側の値が、右側の値と等しいかどうかを評価します。  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 任意の場所、比較式を使用することも、`Boolean`値などで、必要なは、 `If`、 `While`、 `Loop`、または`ElseIf`ステートメントを割り当てるかに値を渡すときや、`Boolean`変数。 次の例では、比較式によって返される値が割り当てられている、`Boolean`変数。  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [ブール式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [演算子および式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [方法 : 数値を計算する](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)
