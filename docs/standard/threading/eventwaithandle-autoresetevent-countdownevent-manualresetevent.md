---
title: "EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6c545f9ebc924c0a12ee2e76fdb6c725c25e2353
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent
イベント待機ハンドルを使用して、スレッドでお互いにシグナル通知し、それぞれのシグナルを待機することで、スレッドの動作を同期できます。 これらの同期イベントは Win32 待機ハンドルに基づいており、通知を受けると自動的にリセットされるものと、手動でリセットされるものの 2 種類があります。  
  
 イベント待機ハンドルは、<xref:System.Threading.Monitor> クラスと同じ多くの同期シナリオで有用です。 イベント待機ハンドルは、多くの場合、<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> および <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> メソッドより使いやすく、シグナル化を細かく制御できます。 名前付きのイベント待機ハンドルを使用して、アプリケーション ドメイン間やプロセス間で動作を同期させるためにも使用できます。これに対し、モニターはアプリケーション ドメインに対してローカルです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle> クラスは、自動または手動のリセット イベントを表します。また、ローカル イベントまたは名前付きのシステム イベントのいずれかです。  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent> クラスは <xref:System.Threading.EventWaitHandle> から派生し、自動的にリセットされるローカル イベントを表します。  
  
 [ManualResetEvent と ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent> クラスは <xref:System.Threading.EventWaitHandle> から派生し、手動でリセットする必要があるローカル イベントを表します。 <xref:System.Threading.ManualResetEventSlim> クラスは軽量で高速なバージョンであり、同じプロセス内のイベントに使用できます。  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent> クラスは、待機ハンドルを使用するコード内の fork/join 並列処理パターンを簡単に実装する簡素化された方法を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [待機ハンドル](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle> クラスは、<xref:System.Threading.EventWaitHandle>、<xref:System.Threading.Semaphore>、<xref:System.Threading.Mutex> クラスの基底クラスです。 すべての種類の待機ハンドルを操作する場合に便利な <xref:System.Threading.WaitHandle.SignalAndWait%2A> や <xref:System.Threading.WaitHandle.WaitAll%2A> などの静的メソッドが含まれます。  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [マネージ スレッド処理の基本](../../../docs/standard/threading/managed-threading-basics.md)
