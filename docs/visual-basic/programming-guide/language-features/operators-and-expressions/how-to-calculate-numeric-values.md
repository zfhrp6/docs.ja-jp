---
title: "How to: Calculate Numeric Values (Visual Basic) | Microsoft Docs"
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
  - "operator precedence"
  - "operators [Visual Basic]"
  - "expressions [Visual Basic], numeric"
  - "calculations, numeric expressions"
  - "precedence, of operators"
  - "Visual Basic code, operators"
  - "Visual Basic code, expressions"
  - "numeric expressions"
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Calculate Numeric Values (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

数式を使って数値を計算できます。  *数式*とは、数値を表すリテラル、定数、変数、およびそれらの値に対して働く演算子を含む式です。  
  
## 数値の計算  
  
#### 数値を計算するには  
  
-   数値リテラル、定数、および変数を結合して数式にします。  有効な数式の例を次に示します。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     最初の 3 行は、順にリテラル、定数、および変数です。  どの行も単独で有効な式です。  最後の行は、1 つの変数と 2 つのリテラルを組み合わせた式です。  
  
     数式は単独では完全な [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ステートメントにならないことに注意してください。  式は完全なステートメントの一部として使用する必要があります。  
  
#### 数値を格納するには  
  
-   数式で表される値を変数に代入するには、次のコード例のように代入ステートメントを使用します。  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     上記の例では、等値演算子 \(`=`\) の右側にある式の値が、演算子の左側にある変数 `j` に代入されるので、`j` の値は 276 となります。  
  
     詳細については、「[Statements](../../../../visual-basic/language-reference/statements/index.md)」を参照してください。  
  
## 複数の演算子  
 数式に複数の演算子が含まれている場合、演算子の計算順序は、演算子の優先規則によって決まっています。  この順序を変更するには、上の例のように式をかっこで囲みます。かっこで囲まれた式が最初に計算されます。  
  
#### 演算子の通常の優先順位をオーバーライドするには  
  
-   最初に実行する演算子をかっこで囲みます。  次のコード例は、同じオペランドと演算子で結果が異なる 2 つの式を示しています。  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     この例では、`j` を計算する際に、`(67 + i)` を囲むかっこにより通常の優先順位がオーバーライドされるため加算演算子 \(`+`\) が最初に実行され、`j` に代入される値は 276 \(4 掛ける 69\) になります。  `k` を計算する際には、演算子は通常の優先順位 \(`+` の前に `*`\) で実行され、`k` に代入される値は 270 \(268 足す 2\) になります。  
  
     詳細については、「[Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)」を参照してください。  
  
## 参照  
 [Operators and Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Statements](../../../../visual-basic/language-reference/statements/index.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Arithmetic Operators](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)