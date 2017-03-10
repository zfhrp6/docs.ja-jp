---
title: "If...Then...Else Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ElseIf"
  - "vb.Then"
  - "vb.If"
  - "vb.EndIf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ElseIf statement, If...Then...Else"
  - "Then statement, If...Then...Else"
  - "control flow, branching"
  - "execution, conditional"
  - "TypeOf...Is expression, and If...Then...Else statements"
  - "If...Then...Else statements"
  - "If statement, If...Then...Else"
  - "If statement"
  - "Is operator [Visual Basic], in If...Then...Else statements"
  - "If Operator [Visual Basic]"
  - "branching, conditional"
  - "IIf function, and If...Then...Else statements"
  - "Else statement [Visual Basic]"
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# If...Then...Else Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

式の値に応じてステートメント グループを条件付きで実行します。  
  
## 構文  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## 指定項目  
 `condition`  
 必須。  式を指定します。  式の結果は、`True` または `False`、あるいは暗黙的に `Boolean` に変換可能なデータ型である必要があります。  
  
 [何も](../../../visual-basic/language-reference/nothing.md)式がに評価される [&#91;NULL 値の使用&#93;](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` の変数の場合は、条件式が `True`ではなく、`Else` のブロックが実行されますように処理され。  
  
 `Then`  
 単一行の構文の場合は必ず指定します。複数行の構文の場合は省略可能です。  
  
 `statements`  
 省略可能。  `condition` が真 \(`True`\) の場合に実行されるステートメントを、`If`...`Then` の後ろに続けて指定します。  
  
 `elseifcondition`  
 `ElseIf` が定義されている場合は必ず指定します。  式を指定します。  式の結果は、`True` または `False`、あるいは暗黙的に `Boolean` に変換可能なデータ型である必要があります。  
  
 `elseifstatements`  
 省略可能。  `elseifcondition` が真 \(`True`\) の場合に実行されるステートメントを、`ElseIf`...`Then` の後ろに続けて指定します。  
  
 `elsestatements`  
 省略可能。  それ以前の `condition` や `elseifcondition` の式がどれも真 \(`True`\) でない場合に実行される一連のステートメントを指定します。  
  
 `End If`  
 `If`...`Then`...`Else` ブロックを終了します。  
  
## 解説  
  
## 複数行の構文  
 `If`...`Then`...`Else` ステートメントに到達すると、`condition` がテストされます。  `condition` が真 \(`True`\) の場合、`Then` の次のステートメントが実行されます。  `condition` が偽 \(`False`\) の場合は、各 `ElseIf` ステートメント \(ある場合\) が順に評価されます。  真 \(`True`\) に評価される `elseifcondition` が見つかると、その `ElseIf` の直後に指定されたステートメントが実行されます。  どの `elseifcondition` も `True` にならないか、`ElseIf` ステートメントが 1 つも定義されていない場合は、`Else` の次のステートメントが実行されます。  `Then`、`ElseIf`、または `Else` に続くステートメントの実行が終わると、`End If` の次のステートメントからプログラムの実行が続けられます。  
  
 `ElseIf` 句と `Else` 句はどちらも必要に応じて定義します。  また、`If`...`Then`...`Else` ステートメントでは、`ElseIf` 句はいくつ指定してもかまいません。ただし、`ElseIf` 句は、`Else` 句の後ろには指定できません。  `If`...`Then`...`Else` ステートメントは互いに入れ子にすることができます。  
  
 複数行の構文の場合は、`If` ステートメントのみを最初の行に定義する必要があります。  `ElseIf`、`Else`、および `End If` の各ステートメントの前に記述できるのは、行ラベルだけです。  `If`...`Then`...`Else` ブロックの終わりには、`End If` ステートメントを指定してください。  
  
> [!TIP]
>  評価する 1 つの式が、さまざまな値になる場合は、[Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) の方が適しています。  
  
## 単一行の構文  
 単一行の構文は、短く簡単な条件判断を行うときに使用します。  ただし、複数行の構文の方がより構造化された柔軟な記述ができます。また、コードの読みやすさや保守性が向上し、デバッグもしやすくなります。  
  
 ステートメントが単一行の `If` かどうかを判断するために、`Then` キーワードの後ろに何が続くかが調べられます。  同じ行内の `Then` キーワードの後ろにコメント以外の記述があると、単一行の `If` ステートメントと判断されます。  `Then` がない場合は、必ず複数行の `If`...`Then`...`Else` の先頭です。  
  
 単一行の構文の場合は、`If`...`Then` で判断した結果として、複数のステートメントを実行できます。  すべてのステートメントを、コロンで区切って同じ行に記述する必要があります。  
  
## 使用例  
 次の例は、`If`...`Then`...`Else` ステートメントの複数行の構文の使用方法を示しています。  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/if-then-else-statement_1.vb)]  
  
## 使用例  
 次の例では、入れ子になった `If`...`Then`...`Else` ステートメントを使用しています。  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/if-then-else-statement_2.vb)]  
  
## 使用例  
 次の例は、単一行の構文の使用方法を示しています。  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/if-then-else-statement_3.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)   
 [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Decision Structures](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)