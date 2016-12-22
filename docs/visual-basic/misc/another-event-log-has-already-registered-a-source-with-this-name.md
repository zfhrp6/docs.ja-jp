---
title: "別のイベント ログが、既にこの名前のソースを登録しています | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 別のイベント ログが、既にこの名前のソースを登録しています
イベント ログにエントリを書き込もうとしましたが、指定のソースは別のイベント ログに登録されています。  
  
 <xref:System.Diagnostics.EventLog> コンポーネントのインスタンスの <xref:System.Diagnostics.EventLog.Source%2A> プロパティを設定しておかなければ、コンポーネントはログにエントリを書き込めません。 書き込み時、システムは、指定したソースがコンポーネントの書き込み先のイベント ログに登録されているかどうかを確認し、必要に応じて <xref:System.Diagnostics.EventLog.CreateEventSource%2A> を呼び出します。  
  
### このエラーを解決するには  
  
1.  <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> または <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> メソッドを使用して、最初のログに対するソースの関連付けを削除します。  
  
2.  ソースを新しいログに登録します。  
  
## 参照  
 [My.Application.Log オブジェクト](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [How to: Remove an Event Source](http://msdn.microsoft.com/ja-jp/bc66c900-4b8a-426a-b8e2-17031a20167e)   
 [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/ja-jp/948ff920-a739-4e66-a191-ee951512d42c)