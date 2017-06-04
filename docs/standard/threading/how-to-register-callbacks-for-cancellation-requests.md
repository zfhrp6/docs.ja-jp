---
title: "How to: Register Callbacks for Cancellation Requests | Microsoft Docs"
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
  - "cancellation, how to register callbacks"
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Register Callbacks for Cancellation Requests
次の例では、トークンを作成したオブジェクトに対する <xref:System.Threading.CancellationTokenSource.Cancel%2A> の呼び出しにより <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> プロパティが true になったときに呼び出されるデリゲートを登録する方法を示します。  この方法は、統合キャンセル フレームワークをネイティブにはサポートしていない非同期操作を取り消す場合や、非同期操作の終了を待機している可能性のあるメソッドのブロックを解除する場合に使用できます。  
  
> [!NOTE]
>  \[マイ コードのみ\] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。 このエラーは問題にはなりません。  F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。  Visual Studio による処理が最初のエラーで中断しないようにするには、**\[ツール\] メニューの \[オプション\]、\[デバッグ\] の順にクリックし、\[全般\]** で \[マイ コードのみ\] チェック ボックスをオフにします。  
  
## 使用例  
 次の例では、<xref:System.Net.WebClient.CancelAsync%2A> メソッドを、キャンセル トークンを通じてキャンセルが要求されたときに呼び出されるメソッドとして登録します。  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 コールバックを登録するときにキャンセルが既に要求されていても、コールバックは必ず呼び出されます。  このような場合、進行中の非同期操作がないと <xref:System.Net.WebClient.CancelAsync%2A> メソッドは何も実行しないので、このメソッドの呼び出しは常に安全です。  
  
## 参照  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)