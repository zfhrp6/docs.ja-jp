---
title: Visual Basic における比較演算子
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: 873ee31bf9c2ab195d66337d52e4a1bb7075ac76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655142"
---
# <a name="comparison-operators-in-visual-basic"></a>Visual Basic における比較演算子
比較演算子は 2 つの式を比較し、`Boolean`これらの値のリレーションシップを表す値です。 数値、文字列、比較演算子とオブジェクトの比較演算子を比較するための演算子があります。 すべての 3 種類の演算子は、ここで説明します。  
  
## <a name="comparing-numeric-values"></a>数値の値を比較します。  
 Visual Basic では、6 つの数値の比較演算子を使用して、数値を比較します。 各演算子はオペランドとして数値に評価される 2 つの式を受け取ります。 次の表は、演算子の一覧し、それぞれの例を示しています。  
  
|演算子|テスト条件|使用例|  
|--------------|----------------------|--------------|  
|`=` (等価)|最初の式等しいかどうかの値と 2 番目の値には|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (非等値)|最初の式の値と等しくない 2 番目の値にしますか。|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (より小さい)|最初の式の値よりも小さいか、2 番目の値とは|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (より大きい)|最初の式の値が 2 番目の値より大きいですか。|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (以下を)|最初の式の値を 2 番目の値未満ですか。|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (より大きいまたは等しい)|最初の式の値をより大きいか等しい 2 つ目の値には|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>文字列の比較  
 Visual Basic を使用して文字列を比較し、 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)だけでなく、数値比較演算子です。 `Like`演算子では、パターンを指定することができます。 文字列を比較し、パターンと一致した場合、結果は`True`します。 それ以外の場合、結果は`False`します。 比較することは数値演算子`String`値が次の例のように、並べ替え順序に基づいています。  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 前の例で、結果は`True`のため、2 番目の文字列の最初の文字の前に、最初の文字列の最初の文字を並べ替えます。 最初の文字と等しい場合は、比較は、両方の文字列の次の文字は引き続きし、などです。 次の例のように、等値演算子を使用して文字列の等価性をテストすることもできます。  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 1 つの文字列が、別のプレフィックス"aa"と"aaa"などの場合、長い文字列が短い文字列より大きいと見なされます。 次に例を示します。  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 並べ替え順序が、バイナリの比較またはテキストの比較の設定に応じてに基づいて`Option Compare`です。 詳細については、次を参照してください。 [Option Compare ステートメント](../../../../visual-basic/language-reference/statements/option-compare-statement.md)です。  
  
## <a name="comparing-objects"></a>オブジェクトを比較します。  
 Visual Basic での 2 つのオブジェクト参照変数を比較し、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)と[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)です。 これらの演算子のいずれかを使用して、2 つの参照変数が同じオブジェクト インスタンスを参照している場合を判断します。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 この例では、`x Is y`に評価される`True`両方の変数が同じインスタンスを参照しているため、します。 次の例では、この結果を比較してください。  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 前の例で`x Is y`に評価される`False`その種類の異なるインスタンスを参照して、変数は、同じ種類のオブジェクトを参照して、ですが、します。  
  
 同一のインスタンスを指していない 2 つのオブジェクトをテストするときに、`IsNot`演算子の文法的に面倒な組み合わせを回避できます。`Not`と`Is`です。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 この例では、`If a IsNot b`は等価`If Not a Is b`です。  
  
### <a name="comparing-object-type"></a>オブジェクトの型の比較  
 オブジェクトが特定の型ではあるかどうかをテストすることができます、`TypeOf`しています.`Is`式。 構文は次のとおりです。  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 ときに`typename`インターフェイスの型が指定、`TypeOf`しています.`Is`式を返します`True`オブジェクトには、インターフェイスの型が実装されている場合。 ときに`typename`式を返しますが、クラス型`True`場合は、オブジェクトは、指定したクラスのまたは指定したクラスから派生したクラスのインスタンス。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 前の例で、`TypeOf x Is Control`式に評価される`True`ための型`x`は`Button`から継承される`Control`です。  
  
 詳細については、次を参照してください。 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)です。  
  
## <a name="see-also"></a>関連項目  
 [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [比較演算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [演算子](../../../../visual-basic/language-reference/operators/index.md)  
 [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Visual Basic における論理/ビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
