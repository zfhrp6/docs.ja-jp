---
title: "How to: Listen for Cancellation Requests That Have Wait Handles | Microsoft Docs"
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
  - "cancellation, waiting with wait handles"
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Listen for Cancellation Requests That Have Wait Handles
メソッドは、イベントの通知を待機しているときにブロックされると、キャンセル トークンの値を確認できず、適時に応答することもできません。  最初の例では、統合キャンセル フレームワークをネイティブにはサポートしない <xref:System.Threading.ManualResetEvent?displayProperty=fullName> などのイベントを使用している場合にこの問題を解決する方法を示します。  2 番目の例では、統合キャンセルをサポートする <xref:System.Threading.ManualResetEventSlim?displayProperty=fullName> を使用した効率的な方法を示します。  
  
> [!NOTE]
>  \[マイ コードのみ\] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。このエラーは問題にはなりません。  F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。  Visual Studio による処理が最初のエラーで中断しないようにするには、**\[ツール\]** メニューの \[オプション\]、\[デバッグ\] の順にクリックし、\[全般\] で \[マイ コードのみ\] チェック ボックスをオフにします。  
  
## 使用例  
 次の例では、<xref:System.Threading.ManualResetEvent> を使用して、統合キャンセルをサポートしない待機ハンドルのブロックを解除する方法を示します。  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## 使用例  
 次の例では、<xref:System.Threading.ManualResetEventSlim> を使用して、統合キャンセルをサポートするコーディネーション プリミティブのブロックを解除する方法を示します。  <xref:System.Threading.Semaphore>`Slim` や <xref:System.Threading.CountdownEvent> など、その他の軽量なコーディネーション プリミティブで、同じ方法を使用できます。  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## 参照  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)