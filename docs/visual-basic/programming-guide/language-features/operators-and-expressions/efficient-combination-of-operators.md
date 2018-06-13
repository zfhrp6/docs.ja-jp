---
title: 演算子の効率のよい組み合わせ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8ced464cb0cc8e1bec3c3449dccb827575599905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648919"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>演算子の効率のよい組み合わせ (Visual Basic)
複雑な式には、さまざまな演算子を含めることができます。 次に例を示します。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 前の例の 1 などの複雑な式を作成するには、演算子の優先順位の規則の確実な理解が必要です。 詳細については、次を参照してください。 [Visual Basic の演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)です。  
  
## <a name="parenthetical-expressions"></a>かっこで囲んだ式  
 多くの場合、演算子の優先順位によって決定されるとは異なる順序で演算を実行します。 例を次に示します。  
  
 `x = z * y + 4`  
  
 前の例の乗算`z`によって`y`、結果を追加`4`です。 追加する場合は`y`と`4`には、結果を乗算する前に`z`かっこを使用して通常の演算子の優先順位をオーバーライドすることができます。 式をかっこで囲んで、その評価される式を最初に、演算子の優先順位に関係なくを強制します。 最初に実行する追加の前の例を次の例のように書き直すことができます。  
  
 `x = z * (y + 4)`  
  
 上記の例では追加`y`と`4`、によってその合計を乗算`z`です。  
  
### <a name="nested-parenthetical-expressions"></a>入れ子になったかっこで囲んだ式  
 さらに優先順位をオーバーライドするかっこの複数のレベルでの式を入れ子にすることができます。 かっこ内に最も深く入れ子になった式は、最も深く入れ子になったに最も深く入れ子にされた、および最後に式を次に最初に評価されます。 次に例を示します。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 前の例で`z + 2`が評価された最初に、次に、その他のかっこで囲んだ式。 指数演算は、通常は、加算や乗算より高い優先順位をは他の式がかっこで囲まれているために、この例では最終評価されます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Visual Basic における論理/ビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [論理/ビット演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [ブール式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [方法 : 数値を計算する](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)
