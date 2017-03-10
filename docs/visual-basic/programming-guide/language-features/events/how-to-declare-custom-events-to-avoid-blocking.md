---
title: "How to: Declare Custom Events To Avoid Blocking (Visual Basic) | Microsoft Docs"
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
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Declare Custom Events To Avoid Blocking (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

イベント ハンドラーが後続のイベント ハンドラーをブロックしないことが重視される状況があります。  カスタム イベントを使うと、イベントから自身のイベント ハンドラーを非同期に呼び出すことができます。  
  
 既定では、イベント宣言のバッキング ストア フィールドは、すべてのイベント ハンドラーが連続的に結合されたマルチキャスト デリゲートです。  つまり、実行の完了に時間がかかるハンドラーがあると、それが完了するまで他のハンドラーはブロックされます。  \(実行に時間がかかったり、操作をブロックする可能性があったりするイベント ハンドラーは、設計を見直すことをお勧めします。\)  
  
 Visual Basic に用意された既定のイベント実装を使う代わりに、カスタム イベントを使うと、イベント ハンドラーを非同期に実行できます。  
  
## 使用例  
 次のコード例では、`AddHandler` アクセサーによって、`Click` イベントの各ハンドラーのデリゲートが `EventHandlerList` フィールドに格納されている <xref:System.Collections.ArrayList> に追加されます。  
  
 コードで `Click` イベントが生成されると、`RaiseEvent` アクセサーから、<xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A> メソッドを使ってすべてのイベント ハンドラー デリゲートが非同期に呼び出されます。  このメソッドは、各ハンドラーをワーカー スレッドに呼び出してから、すぐに制御を返すので、ハンドラーが別のハンドラーをブロックすることはありません。  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#27)]  
  
## 参照  
 <xref:System.Collections.ArrayList>   
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)