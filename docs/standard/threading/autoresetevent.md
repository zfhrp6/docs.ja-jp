---
title: "AutoResetEvent | Microsoft Docs"
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
  - "threading [.NET Framework], AutoResetEvent class"
  - "AutoResetEvent class"
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# AutoResetEvent
<xref:System.Threading.AutoResetEvent> クラスは、ローカル待機ハンドル イベントを表します。これは、待機中の 1 つのスレッドが解放された後、シグナル状態になったときに自動的にリセットされます。  このクラスは、基本クラス <xref:System.Threading.EventWaitHandle> の特殊なケースです。  自動的にリセットされるイベントの使用と特徴については、[EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) の概念を説明したドキュメントを参照してください。  
  
 待機中の 1 つのスレッドが解放されると、<xref:System.Threading.AutoResetEvent> オブジェクトはシステムによって自動的に非シグナル状態にリセットされます。  待機中のスレッドがない場合、イベント オブジェクトはシグナル状態のままです。  <xref:System.Threading.AutoResetEvent> は、`bManualReset` 引数を `false` に指定する Win32 `CreateEvent` 呼び出しと同じです。  
  
 <xref:System.Threading.AutoResetEvent> の使用例については、「[Monitor](../Topic/Monitors.md)」を参照してください。  
  
## 参照  
 <xref:System.Threading.ManualResetEvent>   
 <xref:System.Threading.Monitor>   
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)   
 [Threading](../../../docs/standard/threading/index.md)   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Wait Handles](../Topic/Wait%20Handles.md)