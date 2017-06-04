---
title: "CountdownEvent | Microsoft Docs"
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
  - "synchronization primitives, CountdownEvent"
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=fullName> は、一定回数シグナル状態になった後で、その待機スレッドのブロックを解除する同期プリミティブです。  <xref:System.Threading.CountdownEvent> は、イベントをシグナル状態にする前に手動で変数をデクリメントする必要があり、通常は <xref:System.Threading.ManualResetEvent> または <xref:System.Threading.ManualResetEventSlim> を使用するようなシナリオを想定して設計されています。  たとえば、fork\/join シナリオでは、シグナル カウントが 5 の <xref:System.Threading.CountdownEvent> を作成し、スレッド プールで 5 つの作業項目を開始して、各作業項目の完了時に <xref:System.Threading.CountdownEvent.Signal%2A> を呼び出すようにします。  <xref:System.Threading.CountdownEvent.Signal%2A> が呼び出されるたびに、シグナル カウントは 1 ずつ減少します。  メイン スレッドでは、シグナル カウントが 0 になるまで <xref:System.Threading.CountdownEvent.Wait%2A> の呼び出しがブロックされます。  
  
> [!NOTE]
>  レガシ バージョンの .NET Framework の同期 API と対話する必要のないコードでは、より簡単な方法で fork\/join 並列化の表現を実現できる <xref:System.Threading.Tasks.Task?displayProperty=fullName> オブジェクトと <xref:System.Threading.Tasks.Parallel.Invoke%2A> メソッドのいずれかまたはその両方の使用を検討してください。  
  
 <xref:System.Threading.CountdownEvent> には、次のような追加機能があります。  
  
-   キャンセル トークンを使用して待機操作を取り消すことができます。  
  
-   インスタンスの作成後にシグナル カウントをインクリメントできます。  
  
-   <xref:System.Threading.CountdownEvent.Reset%2A> メソッドの呼び出しによって <xref:System.Threading.CountdownEvent.Wait%2A> から戻った後に、インスタンスを再利用できます。  
  
-   インスタンスは <xref:System.Threading.WaitHandle> を公開するため、<xref:System.Threading.WaitHandle.WaitAll%2A> などの他の .NET Framework 同期 API と統合できます。  
  
## 基本的な使用法  
 <xref:System.Threading.ThreadPool> 作業項目と共に <xref:System.Threading.CountdownEvent> を使用する方法を次の例に示します。  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## キャンセルを有効にした CountdownEvent  
 キャンセル トークンを使用して <xref:System.Threading.CountdownEvent> に対する待機操作を取り消す方法を次の例に示します。  基本的なパターンは、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] で導入された統合キャンセルのモデルに従っています。  詳細については、「[Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)」を参照してください。  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 待機操作が、そのシグナル状態を設定するスレッドを取り消しているのではない点に注意してください。  通常、キャンセルは論理的な操作に対して適用されます。これには、イベントの待機と、その待機によって同期されるすべての作業項目が含まれることがあります。  この例では、作業項目がキャンセル要求に応答できるように、同一のキャンセル トークンのコピーが各作業項目に渡されます。  
  
## 参照  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)