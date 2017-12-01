---
title: "ManualResetEvent と ManualResetEventSlim"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f663dd17b063f77e2f9ce6bd4bbd0f8859ba4116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent と ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>クラスを表します。 ローカルの待機ハンドルのイベントがシグナル通知された後に手動でリセットする必要があります。 このクラスは、その基本クラスの特殊なケースを表します<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>です。 手動リセット イベントの使用方法と機能については、[EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) の概念に関する文書を参照してください。  
  
 A<xref:System.Threading.ManualResetEvent>オブジェクトはまでシグナル状態のまま、<xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType>メソッドが呼び出されます。 待機スレッド、つまりイベントがシグナル状態になるまで待機するスレッドは、そのオブジェクトがシグナル状態である間にいくつでも解放できます。 <xref:System.Threading.ManualResetEvent>Win32 に対応する`CreateEvent`を呼び出すと、指定する`true`の`bManualReset`引数。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]、使用することができます、<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>パフォーマンス向上のため、クラスの待機時間が非常に短くなると予想される場合、およびイベントは、プロセス境界を越えないです。 <xref:System.Threading.ManualResetEventSlim>シグナル状態になるイベントを待機している間、短い時間スピン ビジー状態であるを使用します。 待機時間が短い場合、待機ハンドルを使用して待機するより、スピンを使用するほうが負荷が大幅に低くなります。 ただし、イベントが一定期間内でシグナル状態になるいない場合は、<xref:System.Threading.ManualResetEventSlim>正規イベント ハンドルの待機を使用します。  
  
## <a name="see-also"></a>関連項目  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [待機ハンドル](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Semaphore と SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
