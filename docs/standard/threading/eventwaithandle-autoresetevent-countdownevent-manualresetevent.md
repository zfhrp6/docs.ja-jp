---
title: "EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent | Microsoft Docs"
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
  - "wait handles"
  - "threading [.NET Framework], EventWaitHandle class"
  - "event wait handles [.NET Framework]"
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
イベント待機ハンドルにより、スレッドは相互に通知を行い、相手の通知を待機して動作を同期できます。  これらの同期イベントは Win32 待機ハンドルに基づいており、通知されたときに自動的にリセットされるイベントと手動でリセットするイベントの 2 種類に分けられます。  
  
 イベント待機ハンドルは、<xref:System.Threading.Monitor> クラスと同様の多くの同期シナリオで有効です。  イベント待機ハンドルは、多くの場合、<xref:System.Threading.Monitor.Wait%2A?displayProperty=fullName> メソッドや <xref:System.Threading.Monitor.Pulse%2A?displayProperty=fullName> メソッドよりも簡単に使用でき、通知をより細かく制御できます。  名前付きイベント待機ハンドルは、アプリケーション ドメイン間やプロセス間で動作を同期させるためにも使用できます。これに対し、モニターはアプリケーション ドメインに対してローカルです。  
  
## このセクションの内容  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle> クラスは、自動または手動のリセット イベントを表します。また、ローカル イベントまたは名前付きシステム イベントのいずれかです。  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent> クラスは <xref:System.Threading.EventWaitHandle> から派生し、自動的にリセットされるローカル イベントを表します。  
  
 [ManualResetEvent and ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent> クラスは <xref:System.Threading.EventWaitHandle> から派生し、手動でリセットする必要があるローカル イベントを表します。  <xref:System.Threading.ManualResetEventSlim> クラスは、同じプロセス内のイベントに使用できる軽量でさらに高速なバージョンです。  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent> クラスは、待機ハンドルを使用するコードで fork\/join 並列化パターンを実装する簡単な方法を提供します。  
  
## 関連項目  
 [Wait Handles](../Topic/Wait%20Handles.md)  
 <xref:System.Threading.WaitHandle> クラスは、<xref:System.Threading.EventWaitHandle>、<xref:System.Threading.Semaphore>、および <xref:System.Threading.Mutex> クラスの基本クラスです。  すべての種類の待機ハンドルを使用する場合に役立つ <xref:System.Threading.WaitHandle.SignalAndWait%2A> や <xref:System.Threading.WaitHandle.WaitAll%2A> などの静的メソッドを含みます。  
  
## 参照  
 <xref:System.Threading.EventWaitHandle>   
 <xref:System.Threading.WaitHandle>   
 <xref:System.Threading.AutoResetEvent>   
 <xref:System.Threading.ManualResetEvent>   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)