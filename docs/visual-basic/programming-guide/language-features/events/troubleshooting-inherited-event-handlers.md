---
title: "Troubleshooting Inherited Event Handlers in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "troubleshooting events"
  - "inherited events"
  - "troubleshooting Visual Basic, event handlers"
  - "event handling, troubleshooting"
  - "event handlers, troubleshooting"
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Troubleshooting Inherited Event Handlers in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

このトピックでは、継承コンポーネントのイベント ハンドラーで発生する一般的な問題について説明します。  
  
## 手順  
  
#### イベント ハンドラーのコードが呼び出しのたびに 2 回実行される  
  
-   継承されたイベント ハンドラーに [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) 句が含まれてないことを確認してください。  基本クラス内のメソッドが既にイベントと関連付けられている場合は、そのイベントが発生します。  継承されたメソッドから `Handles` 句を削除してください。  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   継承されたメソッドに `Handles` キーワードが含まれていない場合は、コードに余分な [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md)がないこと、または同じイベントを処理する追加のメソッドがないことを確認してください。  
  
## 参照  
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)