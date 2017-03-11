---
title: "Handles Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "Handles"
  - "vb.Handles"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Handles keyword"
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Handles Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャが指定されたイベントを処理することを宣言します。  
  
## 構文  
  
```  
  
proceduredeclaration Handles eventlist  
```  
  
## 指定項目  
 `proceduredeclaration`  
 イベントを処理するプロシージャの `Sub` プロシージャ宣言。  
  
 `eventlist`  
 コンマで区切られた、`proceduredeclaration` が処理するイベントの一覧。  イベントは、現在のクラスの基底クラス、または `WithEvents` キーワードを使用して宣言されたオブジェクトによって発生する必要があります。  
  
## 解説  
 プロシージャ宣言の最後で `Handles` キーワードを使用すると、`WithEvents` キーワードで宣言されたオブジェクト変数によって発生したイベントが処理されるようになります。  また、`Handles` キーワードを派生クラスで使用すると、基底クラスからのイベントを処理することもできます。  
  
 `Handles` キーワードと `AddHandler` ステートメントはどちらも特定のプロシージャで特定のイベントを処理するように指定できますが、両者には違いがあります。  `Handles` キーワードは、プロシージャの定義時に特定のイベントを処理するよう指定する場合に使用します。  `AddHandler` ステートメントは、実行時にプロシージャをイベントに接続します。  詳細については、「[AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md)」を参照してください。  
  
 カスタム イベントの場合、アプリケーションは、プロシージャをイベント ハンドラーとして追加するときにイベントの `AddHandler` アクセサーを呼び出します。  カスタム イベントの詳細については、「[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)」を参照してください。  
  
## 使用例  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#2)]  
  
 派生クラスで `Handles` ステートメントを使用して基底クラスからのイベントを処理する方法を次の例に示します。  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#3)]  
  
## 使用例  
 **WPF アプリケーション** プロジェクトの 2 つのボタン イベント ハンドラーの例を次に示します。  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/class3.vb#41)]  
  
## 使用例  
 次の例は、前の例と同じです。  `Handles` 句の `eventlist` には 2 つのボタンのイベントが含まれています。  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/class3.vb#42)]  
  
## 参照  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)   
 [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [RaiseEvent Statement](../../../visual-basic/language-reference/statements/raiseevent-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)