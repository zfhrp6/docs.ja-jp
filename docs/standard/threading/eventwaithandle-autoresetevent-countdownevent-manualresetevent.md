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
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c0bcb27ed9c8981665a50c129dfbd824c9612f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent
イベント待機ハンドルを使用して、スレッドでお互いにシグナル通知し、それぞれのシグナルを待機することで、スレッドの動作を同期できます。 これらの同期イベントは Win32 待機ハンドルに基づいており、通知を受けると自動的にリセットされるものと、手動でリセットされるものの 2 種類があります。  
  
 イベント待機ハンドルは、同じ同期シナリオの多くに便利な<xref:System.Threading.Monitor>クラスです。 イベント待機ハンドルがより使いやすく、多くの場合、<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>と<xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>メソッド、および、シグナリングより詳細に制御を提供します。 名前付きのイベント待機ハンドルを使用して、アプリケーション ドメイン間やプロセス間で動作を同期させるためにも使用できます。これに対し、モニターはアプリケーション ドメインに対してローカルです。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle>クラスは、自動のいずれかを表すことができるか、手動リセット イベントと、ローカル イベントまたはシステム イベントの名前します。  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent>クラスから派生<xref:System.Threading.EventWaitHandle>ローカル イベントに自動的にリセットを表すとします。  
  
 [ManualResetEvent と ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent>クラスから派生<xref:System.Threading.EventWaitHandle>手動でリセットする必要があるローカル イベントを表します。 <xref:System.Threading.ManualResetEventSlim>クラスは軽量で高速のバージョンで、同一プロセス内のイベントに使用することができます。  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent>クラスには、待機ハンドルを使用しているコードの分岐および結合の並列処理のパターンを実装する簡単な方法が用意されています。  
  
## <a name="related-sections"></a>関連項目  
 [待機ハンドル](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle>クラスは、基本クラスの<xref:System.Threading.EventWaitHandle>、 <xref:System.Threading.Semaphore>、および<xref:System.Threading.Mutex>クラスです。 などの静的メソッドがある<xref:System.Threading.WaitHandle.SignalAndWait%2A>と<xref:System.Threading.WaitHandle.WaitAll%2A>待機ハンドルのすべての型を使用する場合に便利です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [マネージ スレッド処理の基本](../../../docs/standard/threading/managed-threading-basics.md)
