---
title: "Boolean Expressions (Visual Basic) | Microsoft Docs"
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
  - "short-circuiting"
  - "Boolean expressions"
  - "logical operators, Boolean expressions"
  - "expressions [Visual Basic], Boolean"
  - "expression evaluation, Boolean expressions"
  - "operators [Visual Basic], short-circuiting"
  - "Visual Basic code, operators"
  - "short-circuit evaluation"
  - "logical operators, short-circuiting"
  - "operators [Visual Basic], Boolean"
  - "Visual Basic code, expressions"
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Boolean Expressions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*ブール式*とは、評価結果が [Boolean 型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)の値 \(`True` または `False`\) になる式です。  `Boolean` 式にはいくつかの形式があります。  最も単純な形式では、次のように、`Boolean` 変数の値を `Boolean` リテラルと直接比較します。  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## \= 演算子の 2 つの意味  
 `newCustomer = True` という代入ステートメントは、前述の例に出てきた式と同じに見えますが、機能も使い方も異なります。  前述の例では、`newCustomer = True` という式は Boolean 値を表しているため、`=` 記号は比較演算子として解釈されます。  スタンドアロンのステートメントでは、`=` 記号は代入演算子として解釈され、右の値が左の変数に代入されます。  次に例を示します。  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 詳細については、「[Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)」および「[Statements](../../../../visual-basic/language-reference/statements/index.md)」を参照してください。  
  
## 比較演算子  
 `=`、`<`、`>`、`<>`、`<=`、`>=` などの比較演算子は、演算子の左側の式と右側の式を比較し、その結果を `True` または `False` として評価することでブール式を形成します。  次に例を示します。  
  
 `42 < 81`  
  
 42 は 81 より小さいので、このブール式の評価は `True` になります。  この種類の式の詳細については、「[Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)」を参照してください。  
  
### 比較演算子と論理演算子の組み合わせ  
 論理演算子を使って比較式を組み合わせると、より複雑なブール式を作成できます。  次の例では、比較演算子と論理演算子を組み合わせて使用しています。  
  
 `x > y And x < 1000`  
  
 この式全体の値は、`And` 演算子の両側の式の値によって決まります。  両方の式が `True` の場合は、式全体の評価も `True` になります。  いずれかの式が `False` の場合は、式全体の評価も `False` になります。  
  
## 演算子のショートサーキット  
 `AndAlso` と `OrElse` という論理演算子は、*ショートサーキット*と呼ばれる動作を示します。  ショートサーキット演算子は、左のオペランドを最初に評価します。  左のオペランドによって式全体の値が決まる場合は、右の式が評価されないまま、プログラムの実行が次に進みます。  次に例を示します。  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 この例では、まず左の式 `45 < 12` が評価されます。  左の式の評価は `False` になるので、この論理式全体の評価は `False` になります。  したがって、右の式 `testFunction(3)` は評価されないまま、`If` ブロック内のコードの実行がスキップされます。  この例では、左の式を評価しただけで式全体が false になることが決まるので、`testFunction()` は呼び出されません。  
  
 同様に、`OrElse` を使った論理式の左の式が `True` になる場合も、右の式は評価されないまま次のコード行が実行されます。これは、左の式を評価しただけで式全体が true になることが決まるからです。  
  
### 非ショートサーキット演算子との比較  
 これに対して、`And` 演算子または `Or` 演算子を使用した場合は、論理演算子の両側が評価されます。  次に例を示します。  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 この例では、左の式の評価が `False` になる場合でも、`testFunction()` が呼び出されます。  
  
## かっこを使った式  
 かっこを使うと、ブール式を評価する順序を制御できます。  かっこで囲まれている式が最初に評価されます。  複数のレベルで入れ子になっている場合は、最も内側の式から評価されます。  かっこの中の式は、演算子の優先順位の規則に従って評価されます。  詳細については、「[Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)」を参照してください。  
  
## 参照  
 [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Statements](../../../../visual-basic/programming-guide/language-features/statements.md)   
 [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)