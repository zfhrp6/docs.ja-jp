---
title: "AddHandler Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AddHandlerMethod"
  - "addhandler"
  - "vb.addhandler"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "AddHandler statement"
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# AddHandler Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

実行時にイベントをイベント ハンドラーに関連付けます。  
  
## 構文  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## 指定項目  
 `event`  
 処理するイベントの名前。  
  
 `eventhandler`  
 イベントを処理するプロシージャの名前。  
  
## 解説  
 `AddHandler` ステートメントと `RemoveHandler` ステートメントを使うと、プログラムの実行中にいつでもイベント処理を開始および停止できます。  
  
 `eventhandler` プロシージャのシグネチャは、`event` イベントのシグネチャと一致する必要があります。  
  
 `Handles` キーワードと `AddHandler` ステートメントは、どちらも特定のイベントを特定のプロシージャで処理するよう指定する方法ですが、いくつか相違点があります。  `AddHandler` ステートメントは、実行時にイベントをプロシージャに関連付けます。  特定のイベントを処理するプロシージャを定義するときには、`Handles` キーワードを使用します。  詳細については、「[Handles](../../../visual-basic/language-reference/statements/handles-clause.md)」を参照してください。  
  
> [!NOTE]
>  カスタム イベントの場合は、`AddHandler` ステートメントはイベントの `AddHandler` アクセサーを呼び出します。  カスタム イベントの詳細については、「[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)」を参照してください。  
  
## 使用例  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## 参照  
 [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)