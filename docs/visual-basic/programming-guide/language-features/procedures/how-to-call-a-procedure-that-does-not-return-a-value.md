---
title: "How to: Call a Procedure that Does Not Return a Value (Visual Basic) | Microsoft Docs"
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
  - "procedure calls, returning values"
  - "Visual Basic code, procedures"
  - "procedures, calling"
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# How to: Call a Procedure that Does Not Return a Value (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Sub` プロシージャは、呼び出し元のコードに値を返しません。  このプロシージャは、スタンドアロンの呼び出しステートメントを使って明示的に呼び出す必要があります。  式の中で名前を指定するだけでは、呼び出すことができません。  
  
### Sub プロシージャを呼び出すには  
  
1.  `Sub` プロシージャの名前を指定します。  
  
2.  プロシージャ名に、かっこで囲んだ引数リストを指定します。  指定する引数がない場合は、かっこを省略することもできます。  しかし、かっこを使用した方がコードが読みやすくなります。  
  
3.  かっこ内の引数リストに、引数をコンマで区切って指定します。  引数は、`Sub` プロシージャの対応するパラメーターの定義と同じ順序で指定する必要があります。  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 関数を呼び出して、アプリケーション ウィンドウをアクティブにする例を次に示します。  <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> は、唯一の引数としてウィンドウ タイトルを受け取ります。  呼び出し元のコードに値は返されません。  メモ帳のプロセスが実行中でない場合、この例は <xref:System.ArgumentException> をスローします。  アプリケーションの実行に `Shell` プロシージャを使用していますが、指定されたパスにアプリケーションの実行プログラムが保存されていない場合は、アプリケーションを実行することはできません。  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:System.ArgumentException>   
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [How to: Create a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [How to: Call a Procedure That Returns a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-returns-a-value.md)   
 [How to: Call an Event Handler in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-event-handler.md)