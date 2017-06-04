---
title: "ManualResetEvent and ManualResetEventSlim | Microsoft Docs"
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
  - "threading [.NET Framework], ManualResetEvent class"
  - "ManualResetEvent class, about ManualResetEvent class"
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# ManualResetEvent and ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=fullName> クラスは、シグナル状態になった後に手動でリセットする必要があるローカル待機ハンドル イベントを表します。  このクラスが表すのは、基本クラス <xref:System.Threading.EventWaitHandle?displayProperty=fullName> の特殊なケースです。  手動リセット イベントの使用方法と機能については、[EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) の概念についてのトピックを参照してください。  
  
 <xref:System.Threading.ManualResetEvent> オブジェクトは、その <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=fullName> メソッドが呼び出されるまで、シグナル状態のままです。  待機スレッド、つまりイベントがシグナル状態になるまで待機するスレッドは、そのオブジェクトがシグナル状態である間にいくつでも解放できます。  <xref:System.Threading.ManualResetEvent> は、`bManualReset` 引数を `true` に指定する Win32 `CreateEvent` 呼び出しと同じです。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]では、待機時間が非常に短くなると予測される場合、およびイベントがプロセスの境界を通過しない場合にパフォーマンスが向上するように<xref:System.Threading.ManualResetEventSlim?displayProperty=fullName> クラスを使用できます。  <xref:System.Threading.ManualResetEventSlim> は シグナル状態にするためにイベントを待機している間、以下の間にビジー スピンを使用します。  待機時間が短い場合は、待機ハンドルよりもスピンを使用する方が負荷が大幅に低くなります。  ただし、一定期間内にイベントがシグナル状態にならない場合、<xref:System.Threading.ManualResetEventSlim> では通常のイベント ハンドル待機を使用します。  
  
## 参照  
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Wait Handles](../Topic/Wait%20Handles.md)   
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)   
 [SpinWait](../../../docs/standard/threading/spinwait.md)   
 [Semaphore and SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)