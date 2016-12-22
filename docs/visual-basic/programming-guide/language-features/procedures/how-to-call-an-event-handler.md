---
title: "How to: Call an Event Handler in Visual Basic | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "event handlers, calling"
  - "event handlers"
  - "procedures, event handlers"
  - "procedures, calling"
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Call an Event Handler in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

*イベント*とは、なんらかのプログラム コンポーネントによって認識される動作または事象で、たとえば、マウス クリックやクレジットの上限への到達などがあります。このようなイベントに応答するためのコードを記述できます。  *イベント ハンドラー*は、イベントに応答するために作成するコードです。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] では、イベント ハンドラーは `Sub` プロシージャとして作成します。  ただし、他の `Sub` プロシージャと同じ方法で呼び出すのではなく、  通常はイベントに対するハンドラーとしてこのプロシージャを指定します。  これには [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) 句と [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) 変数を使うか、または [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) を使います。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の既定の方法では、`Handles` 句を使ってイベント ハンドラーを宣言します。  統合開発環境 \(IDE\) でプログラムを作成する場合は、この方法でイベント ハンドラーを記述することになります。  `AddHandler` ステートメントは、実行時にイベントを動的に発生させるのに適しています。  
  
 イベントが発生すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はイベント ハンドラーのプロシージャを自動的に呼び出します。  イベントにアクセスできるコードであればどこからでも、[RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md) を実行してイベントを発生させることができます。  
  
 同じイベントに複数のイベント ハンドラーを関連付けることも可能です。  場合によっては、ハンドラーをイベントから切り離すこともできます。  詳細については、「[Events](../../../../visual-basic/programming-guide/language-features/events/events.md)」を参照してください。  
  
### Handles と WithEvents を使用してイベント ハンドラーを呼び出すには  
  
1.  イベントが [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md) を使って宣言されていることを確認します。  
  
2.  [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) キーワードを使用して、オブジェクト変数をモジュール レベルまたはクラス レベルで宣言します。  この変数の `As` 句では、イベントを発生させるクラスを指定する必要があります。  
  
3.  イベントを処理する `Sub` プロシージャの宣言で、`WithEvents` 変数とイベント名を指定する [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) 句を追加します。  
  
4.  イベントが発生すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はこの `Sub` プロシージャを自動的に呼び出します。  イベントを発生させるには、`RaiseEvent` ステートメントを使用してコードを記述します。  
  
     イベントの定義例と、イベントを発生させるクラスを参照する `WithEvents` 変数の定義例を次に示します。  イベントを処理する `Sub` プロシージャでは `Handles` 句を使用して、クラスおよびプロシージャが処理するイベントが指定されています。  
  
     [!code-vb[VbVbcnProcedures#4](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### AddHandler を使用してイベント ハンドラーを呼び出すには  
  
1.  イベントが `Event` ステートメントを使って宣言されていることを確認します。  
  
2.  [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)を実行して、イベントを処理する `Sub` プロシージャをイベントに動的に関連付けます。  
  
3.  イベントが発生すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はこの `Sub` プロシージャを自動的に呼び出します。  イベントを発生させるには、`RaiseEvent` ステートメントを使用してコードを記述します。  
  
     次の例に定義された `Sub` プロシージャは、フォームの <xref:System.Windows.Forms.Form.Closing> イベントを処理します。  次に、[AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)を使って `catchClose` プロシージャを <xref:System.Windows.Forms.Form.Closing> のイベント ハンドラーとして関連付けています。  
  
     [!code-vb[VbVbcnProcedures#5](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md)を実行すると、イベント ハンドラーをイベントから切り離すことができます。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)   
 [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [AddressOf Operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [How to: Create a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-procedure.md)   
 [How to: Call a Procedure that Does Not Return a Value](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-procedure-that-does-not-return-a-value.md)