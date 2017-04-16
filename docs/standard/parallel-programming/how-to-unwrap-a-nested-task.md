---
title: "How to: Unwrap a Nested Task | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tasks, how to unwrap nested tasks"
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Unwrap a Nested Task
次の例に示すように、メソッドからタスクを返し、その後待機するか、またはそのタスクから処理を続行することができます。  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 前の例では、<xref:System.Threading.Tasks.Task%601.Result%2A> プロパティは `string` \(Visual Basic では `String`\) 型です。  
  
 しかし、シナリオによっては、タスクを別のタスク内で作成し、入れ子のタスクを返す必要がある場合があります。  この場合、外側のタスクの `TResult` は、それ自体がタスクです。  次の例では、Result プロパティは C\# では `Task<Task<string>>`、Visual Basic では `Task(Of Task(Of String))` です。  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 外側のタスクのラップを解除し、元のタスクとその <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティを取得するコードを記述することもできますが、例外とキャンセル要求を処理する必要があるため、そのようなコードを記述するのは容易ではありません。  この状況では、次の例に示すように、いずれかの <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 拡張メソッドを使用することをお勧めします。  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> メソッドを使用して、任意の `Task<Task>` または `Task<Task<TResult>>` \(Visual Basic では `Task(Of Task)` または `Task(Of Task(Of TResult))`\) を `Task` または `Task<TResult>` \(Visual Basic では `Task(Of TResult)`\) に変換できます。  新しいタスクは、入れ子の内側のタスクを完全に表し、キャンセル状態とすべての例外を含みます。  
  
## 使用例  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 拡張メソッドを使用する方法を次の例に示します。  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## 参照  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=fullName>   
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)