---
title: "Loop Structures (Visual Basic) | Microsoft Docs"
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
  - "control flow, loops"
  - "For keyword [Visual Basic], loop structures"
  - "loops"
  - "loop structures"
  - "statements [Visual Basic], loop"
  - "Do statement, Do loops"
  - "conditional statements, loop structures"
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Loop Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のループ構造を使うと、1 行または複数行のコードを繰り返し実行できます。  ループ構造のステートメントは、条件が `True` になるまで、条件が `False` になるまで、指定した回数、またはコレクションの各要素について 1 回ずつ繰り返すことができます。  
  
 次の図は、一連のステートメントを、条件が真になるまで実行するループ構造を示しています。  
  
 ![Do...Until ループのフロー チャート](../../../../visual-basic/programming-guide/language-features/control-flow/media/dountilloop.gif "DoUntilLoop")  
条件が真になるまで一連のステートメントを実行  
  
## WHILE ループ  
 `While` ステートメントで指定した条件が `True` である限り、`While`...`End While` 構造によって、一連のステートメントが実行されます。  詳細については、「[While...End While Statement](../../../../visual-basic/language-reference/statements/while-end-while-statement.md)」を参照してください。  
  
## Do ループ  
 `Do`...`Loop` 構造により、ループ構造の先頭または末尾のいずれかにある条件をテストできます。  また、条件が `True` のままである間、または `True` になるまで、ループを繰り返すかどうかを指定することもできます。  詳細については、「[Do...Loop Statement](../../../../visual-basic/language-reference/statements/do-loop-statement.md)」を参照してください。  
  
## FOR ループ  
 `For`...`Next` 構造では、設定した回数のループが実行されます。  繰り返しの追跡には、*カウンター*と呼ばれるループ制御変数が使用されます。  このカウンターに開始値および終了値を指定します。また、オプションで、1 回の繰り返しから次回の繰り返しへの増分を指定できます。  詳細については、「[For...Next ステートメント](../../../../visual-basic/language-reference/statements/for-next-statement.md)」を参照してください。  
  
## For Each ループ  
 `For Each`...`Next` 構造により、コレクション内の各要素に対して、一連のステートメントが 1 回実行されます。  ループ制御変数を指定しますが、開始値または終了値を決める必要はありません。  詳細については、「[For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)」を参照してください。  
  
## 参照  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)