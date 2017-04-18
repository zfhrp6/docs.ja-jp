---
title: "Visual Basic における比較演算子 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- comparison operators, comparing strings
- comparison operators, comparing objects
- strings [Visual Basic], comparing
- comparison operators
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers, comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values, comparing
- comparison operators, comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6185d1676f2cd160c9c3e855cce4a6d2bbe2ffb4
ms.lasthandoff: 03/13/2017

---
# <a name="comparison-operators-in-visual-basic"></a>Comparison Operators in Visual Basic
比較演算子は&2; つの式を比較し、`Boolean`これらの値のリレーションシップを表す値。 数値、文字列を比較するための演算子、およびオブジェクトを比較する演算子を比較するための演算子があります。 ここでは、すべての&3; 種類の演算子を説明します。  
  
## <a name="comparing-numeric-values"></a>数値の比較  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]6 つの数値の比較演算子を使用して、数値を比較します。 各演算子は、オペランドとして数値に評価される&2; つの式を取得します。 次の表は、演算子の一覧し、それぞれの例を示しています。  
  
|演算子|テスト条件|例|  
|--------------|----------------------|--------------|  
|`=`(等値)|最初の式と等しい値を&2; 番目の値とは|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>`(非等値)|値ではない最初の式の&2; つ目の値と等しいか。|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<`(より小さい)|最初の式の値未満、2 番目の値とは|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>`(より大きい)|最初の式の値は、2 番目の値よりも大きいですか|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=`(より小さいまたは等しい)|最初の式の値を&2; 番目の値以下ですか。|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=`(より大きいまたは等しい)|最初の式の値は、2 番目の値以下でしょうか。|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>文字列の比較  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]使用して文字列を比較し、 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)だけでなく、数値比較演算子です。 `Like`演算子では、パターンを指定することができます。 文字列は、比較、パターンと一致した場合、結果は`True`です。 それ以外の場合、結果は`False`です。 数値演算子で比較を使用する`String`値は次の例のように、並べ替え順序に基づいています。  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 前の例では、結果は`True`最初の文字列の最初の文字が&2; 番目の文字列の最初の文字の前になるためです。 最初の文字と等しい場合は、比較を両方の文字列では、次の文字を続行しにします。 次の例のように、等値演算子を使用して文字列の等価性をテストすることもできます。  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 1 つの文字列が"aa"や"aaa"など、別のプレフィックスである場合より長い文字列は短いほうの文字列よりも大きくすると見なされます。 次に例を示します。  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 並べ替え順序が、バイナリの比較またはテキストの比較の設定に応じてに基づいて`Option Compare`します。 詳細については、次を参照してください。 [Option Compare ステートメント](../../../../visual-basic/language-reference/statements/option-compare-statement.md)します。  
  
## <a name="comparing-objects"></a>オブジェクトを比較します。  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]2 つの比較はオブジェクト参照変数と、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)と[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)します。 これらの演算子のいずれかを使用して、2 つの参照変数が同じオブジェクト インスタンスを参照している場合を判断します。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators #&65;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 前の例で`x Is y`に評価`True`、両方の変数が同じインスタンスを参照してください。 次の例では、この結果を比較してください。  
  
 [!code-vb[VbVbalrOperators #&66;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 前の例で`x Is y`に評価`False`、その種類の異なるインスタンス変数を同じ型のオブジェクト、参照が表しているためです。  
  
 同じインスタンスを指していない&2; つのオブジェクトをテストするときに、`IsNot`演算子の文法的に不器用な組み合わせを回避できます。`Not`と`Is`です。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators #&67;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 前の例で`If a IsNot b`は`If Not a Is b`です。  
  
### <a name="comparing-object-type"></a>オブジェクトの種類を比較します。  
 オブジェクトが特定の型にするかどうかをテストする、 `TypeOf`.`Is`式です。 構文は次のとおりです。  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 `typename`インターフェイスの種類を指定し、 `TypeOf`.`Is`式を返します。`True`オブジェクトは、インターフェイス型を実装している場合。 `typename` 、式から返されるクラス型が`True`場合は、オブジェクトは、指定したクラスのまたは指定したクラスから派生したクラスのインスタンス。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators #&68;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 前の例で、`TypeOf x Is Control`式に評価される`True`ための型`x`は`Button`から継承される`Control`します。  
  
 詳細については、次を参照してください。 [TypeOf 演算子](../../../../visual-basic/language-reference/operators/typeof-operator.md)します。  
  
## <a name="see-also"></a>関連項目  
 [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [比較演算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [演算子](../../../../visual-basic/language-reference/operators/index.md)   
 [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Visual Basic での論理/ビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
