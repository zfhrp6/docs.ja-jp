---
title: "Other Control Structures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "statements [Visual Basic], control flow"
  - "control structures"
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Other Control Structures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] には、リソースを破棄するために、または 1 つのオブジェクトを繰り返し参照する回数を減らすために役立つ制御構造があります。  
  
## Using...End Using 構造  
 `Using...End Using` 構造は、ステートメント ブロックを構築し、SQL 接続などのリソースをそのブロック内で利用できるようにします。  `Using` ステートメントでは、オプションでリソースを取得することもできます。  `Using` ブロックを終了すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] によって自動的にリソースが解放され、他のコードでそのリソースを使用できるようになります。  リソースは、ローカルであり、破棄可能である必要があります。  詳細については、「[Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
## With...End With 構造  
 `With...End With` 構造では、オブジェクト参照を 1 回だけ指定してから、そのメンバーにアクセスする一連のステートメントを実行できます。  これによりコードが簡単になります。また、オブジェクトにアクセスするステートメントのたびに [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] が参照を再度確立する必要がなくなるため、パフォーマンスを向上できます。  詳細については、「[With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)」を参照してください。  
  
## 参照  
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)   
 [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)