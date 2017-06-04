---
title: "How to: Listen for Cancellation Requests by Polling | Microsoft Docs"
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
  - "cancellation, how to poll for requests"
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# How to: Listen for Cancellation Requests by Polling
次の例では、ユーザー コードでキャンセル トークンを一定の間隔でポーリングして、呼び出し元のスレッドからキャンセルが要求されたかどうかを確認する 1 つの方法を示します。  この例では <xref:System.Threading.Tasks.Task?displayProperty=fullName> 型を使用しますが、<xref:System.Threading.ThreadPool?displayProperty=fullName> 型または <xref:System.Threading.Thread?displayProperty=fullName> 型によって直接作成された非同期操作にも同じパターンが適用されます。  
  
## 使用例  
 ポーリングには、ブール型の <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティの値を定期的に読み取ることができる、ある種のループまたは再帰コードが必要です。  <xref:System.Threading.Tasks.Task?displayProperty=fullName> 型を使用し、呼び出し元のスレッドでタスクが完了するのを待つ場合は、<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> メソッドを使用して、プロパティを確認し、例外をスローできます。  このメソッドを使用すると、要求への応答として正しい例外をスローすることができます。  <xref:System.Threading.Tasks.Task> を使用する場合は、<xref:System.OperationCanceledException> を手動でスローするよりもこのメソッドを呼び出す方が良い方法です。  例外をスローする必要がない場合は、プロパティを確認し、プロパティが `true` のときはメソッドから制御を戻すだけです。  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> の呼び出しは非常に高速で、ループのオーバーヘッドが大きくなることはありません。  
  
 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> を呼び出す場合、キャンセルへの応答として行う作業が例外のスロー以外にもあるときは、<xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティを明示的に確認するだけで済みます。  この例では、実際にはコードからプロパティに 2 回アクセスすることがわかります。1 回は明示的なアクセスで、もう 1 回は <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> メソッドです。  ただし、<xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティの読み取り操作にはアクセスごとに volatile の読み取り命令が 1 つあるだけなので、2 回のアクセスはパフォーマンスの観点からも特に問題ではありません。  やはり、<xref:System.OperationCanceledException> を手動でスローするよりもこのメソッドを呼び出すことをお勧めします。  
  
## 参照  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)