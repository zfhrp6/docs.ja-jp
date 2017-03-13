---
title: "RemoveHandler Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.RemoveHandlerMethod"
  - "vb.RemoveHandler"
  - "RemoveHandler"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "RemoveHandler keyword"
  - "RemoveHandler statement"
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# RemoveHandler Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

イベントとイベント ハンドラーの関連付けを解除します。  
  
## 構文  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`event`|処理するイベントの名前。|  
|`eventhandler`|現在イベントを処理しているプロシージャの名前。|  
  
## 解説  
 `AddHandler` ステートメントと `RemoveHandler` ステートメントを使うと、プログラムの実行中にいつでも特定のイベントの処理を開始および停止できます。  
  
> [!NOTE]
>  カスタム イベントの場合は、`RemoveHandler` ステートメントがイベントの `RemoveHandler` アクセサーを呼び出します。  カスタム イベントの詳細については、「[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)」を参照してください。  
  
## 使用例  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## 参照  
 [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)