---
title: "Value Comparisons (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], comparing values"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "comparison operators, comparing expressions"
  - "numeric expressions"
  - "operators [Visual Basic], comparison"
  - "expressions [Visual Basic], comparing"
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Value Comparisons (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

比較演算子を使うと、数値変数の値を比較する式を作成できます。  比較演算子を使って作成した式は、比較の真偽に基づく `Boolean` 値を返します。  このような式の例は次のようになります。  
  
 `45 > 26`  
  
 `26 > 45`  
  
 45 は 26 より大きいため、1 番目の式は `True` になります。  26 は 45 より小さいため、2 番目の式は `False` になります。  
  
 この方法で、数式も比較できます。  比較の対象となる式は、次のような複合式であってもかまいません。  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 この複合式には、リテラル、変数、および関数呼び出しが含まれています。  まず比較演算子の両側の式を計算し、その結果値を比較演算子 `>=` を使って比較します。  左側の式の値が右側の式の値以上である場合は、上の式全体が `True` になり、それ以外の場合は `False` になります。  
  
 値を比較する式は、次のような `If...Then` 構築で最もよく使用されます。  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 等号 \(`=`\) は、代入演算子としてだけでなく、比較演算子としても使用されます。  比較演算子として使用された場合は、左側の値が右側の値と等しいかどうかを評価します。たとえば、次のように使います。  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 比較式は、この他にも、`Boolean` 値が必要な場合 \(`If`、`While`、`Loop`、または `ElseIf` などのステートメントの中など\) や、`Boolean` 変数に値を代入したり渡したりする場合などに使用できます。  次の例では、比較式によって返される値が `Boolean` 変数に代入されています。  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## 参照  
 [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [How to: Calculate Numeric Values](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)