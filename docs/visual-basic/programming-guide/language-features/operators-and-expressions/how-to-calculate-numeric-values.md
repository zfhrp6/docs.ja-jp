---
title: "方法: 数値 (Visual Basic) を計算する |Microsoft ドキュメント"
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
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations, numeric expressions
- precedence, of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
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
ms.openlocfilehash: d844e2af3892d897125e21d3fd7047a8b295d10a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>方法: 数値を計算する (Visual Basic)
数値式を使用して数値の値を計算することができます。 A*数値式*リテラル、定数、および数値を表す変数を含む式を指定し、それらの値に対して作用する演算子です。  
  
## <a name="calculating-numeric-values"></a>数値の計算  
  
#### <a name="to-calculate-a-numeric-value"></a>数値の値を計算するには  
  
-   数値式に&1; つまたは複数の数値リテラル、定数、および変数を結合します。 次の例では、いくつかの有効な数値式を示します。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     最初の&3; つの行は、リテラル、定数、および変数を示します。 1 つは、単独で有効な数値式を形成します。 最後の行は、2 つのリテラルと変数の組み合わせを示しています。  
  
     数値式が完全な形成されていませんが注[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]ステートメント自体でします。 完全なステートメントの一部として式を使用する必要があります。  
  
#### <a name="to-store-a-numeric-value"></a>数値の値を格納するには  
  
-   代入ステートメントを使用すると、次の例に示すように、変数に数値式で表される値を割り当てます。  
  
     [!code-vb[VbVbalrOperators #&82;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     上記の例では、等値演算子の右側にある式の値 (`=`)、変数に割り当てられた`j`、演算子の左側にあるため、 `j` 276 にします。  
  
     詳細については、次を参照してください。[ステートメント](../../../../visual-basic/language-reference/statements/index.md)します。  
  
## <a name="multiple-operators"></a>複数の演算子  
 数値式に複数の演算子が含まれている場合、評価の順序は演算子の優先順位の規則によって決まります。 演算子の優先順位のルールを無効にするには、式をかっこで囲みます、上記の例に示すように囲まれた式は、最初に評価されます。  
  
#### <a name="to-override-normal-operator-precedence"></a>標準の演算子の優先順位をオーバーライドするには  
  
-   かっこを使用して、最初に実行する対象の操作を囲みます。 次の例では、同じオペランドと演算子を持つ&2; つの異なる結果を示します。  
  
     [!code-vb[VbVbalrOperators&#83;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     前の例の計算で`j`加算演算子の実行 (`+`) 最初ため、かっこで囲まれて`(67 + i)`通常の優先順位、およびに割り当てられた値をオーバーライドする`j`276 (4 回 69) は、です。 計算`k`、通常の優先順位の演算子を実行 (`*`する前に`+`)、およびに割り当てられた値`k`270 (268 足す 2) は、です。  
  
     詳細については、次を参照してください。 [Visual Basic の演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)します。  
  
## <a name="see-also"></a>関連項目  
 [演算子よぶ式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [ステートメント](../../../../visual-basic/language-reference/statements/index.md)   
 [Visual Basic の演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [算術演算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
