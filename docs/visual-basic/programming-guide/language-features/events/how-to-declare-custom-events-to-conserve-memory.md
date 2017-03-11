---
title: "How to: Declare Custom Events To Conserve Memory (Visual Basic) | Microsoft Docs"
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
  - "declaring events, custom"
  - "events [Visual Basic], custom"
  - "custom events"
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Declare Custom Events To Conserve Memory (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

アプリケーションによるメモリの使用量を低く抑えることが重要になる場面はいくつもあります。  カスタム イベントを使うと、アプリケーションは自分が処理するイベントに対してのみメモリを使用できます。  
  
 既定では、クラスでイベントが宣言されると、コンパイラはイベント情報を格納するフィールドのためにメモリを割り当てます。  クラスに未使用のイベントが多数含まれると、メモリが不必要に消費されます。  
  
 Visual Basic に用意されている既定のイベントの実装を使うのではなく、カスタム イベントを使用することで、メモリの使用量を注意深く管理できます。  
  
## 使用例  
 次の例では、クラスが <xref:System.ComponentModel.EventHandlerList> クラスの 1 つのインスタンスを `Events` フィールドに格納して使用します。ここには使用中のイベントに関する情報が格納されます。  <xref:System.ComponentModel.EventHandlerList> クラスはデリゲートを保持するための、最適化されたリスト クラスです。  
  
 このクラスのすべてのイベントは、`Events` フィールドを使用して、各イベントをどのメソッドが処理しているかを持続的に追跡します。  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#22)]  
  
## 参照  
 <xref:System.ComponentModel.EventHandlerList>   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)