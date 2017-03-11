---
title: "Decision Structures (Visual Basic) | Microsoft Docs"
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
  - "statements [Visual Basic], control flow"
  - "If statement, decision structures"
  - "If statement, If...Then...Else"
  - "control flow, decision structures"
  - "decision structures"
  - "conditional statements, decision structures"
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# Decision Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、条件を調べ、その結果に応じた処理を実行できます。  条件のテスト結果は、真偽値、式のさまざまな値、または一連のステートメントを実行したときに生成されるさまざまな例外として得ることができます。  
  
 次の図は、条件が真かどうかをテストし、真か偽かによって異なる処理を実行する条件判断構造を示しています。  
  
 ![If...Then...Else 構造のフロー チャート](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
条件が真である場合と偽である場合とで異なる処理を実行  
  
## If...Then...Else 構造  
 `If...Then...Else` 構造では、1 つ以上の条件をテストし、各条件に応じて 1 つ以上のステートメントを実行できます。  次の方法で条件をテストし、処理を実行できます。  
  
-   条件が `True` の場合に、1 つ以上のステートメントを実行します。  
  
-   条件が `False` の場合に、1 つ以上のステートメントを実行します。  
  
-   ある条件が `True` で、他の条件が `False` の場合に、いくつかのステートメントを実行します。  
  
-   先行する条件が `False` の場合に、追加の条件をテストします。  
  
 これらのすべての機能を持つ制御構造が、[If...Then...Else Statement](../../../../visual-basic/language-reference/statements/if-then-else-statement.md) です。  1 つのテストおよび 1 つのステートメントだけを実行する場合は、単一行のバージョンを使用できます。  条件およびアクションがより複雑な場合は、複数行のバージョンを使用します。  
  
## Select...Case 構造  
 `Select...Case` 構造では、式を 1 回評価し、想定されるさまざまな値に基づいて異なる一連のステートメントを実行できます。  詳細については、「[Select...Case Statement](../../../../visual-basic/language-reference/statements/select-case-statement.md)」を参照してください。  
  
## Try...Catch...Finally 構造  
 `Try...Catch...Finally` 構造では、いずれかのステートメントで例外が発生した場合に、制御を継続できる環境で一連のステートメントを実行できます。  さまざまな例外に応じて異なるアクションを実行できます。  オプションで、どのような状況でも関係なく `Try...Catch...Finally` 構造全体を終了する前に必ず実行するコード ブロックを指定できます。  詳細については、「[Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。  
  
> [!NOTE]
>  多くの制御構造では、キーワードをクリックすると、その構造体のキーワードがすべて強調表示されます。  たとえば、`If...Then...Else` 構造の `If` をクリックすると、その構造の `If`、`Then`、`ElseIf`、`Else`、および `End If` のすべてのインスタンスが強調表示されます。  強調表示された次のキーワード、または前のキーワードに移動するには、Ctrl キーと Shift キーを押しながら↑キーを押すか、Ctrl キーと Shift キーを押しながら↓キーを押します。  
  
## 参照  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md)