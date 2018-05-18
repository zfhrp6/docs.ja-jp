---
title: ManualResetEvent と ManualResetEventSlim
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d69336bd9e4f4ec06e8319d19c1cdab5cf6e1c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="manualresetevent-and-manualreseteventslim"></a>ManualResetEvent と ManualResetEventSlim
<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> クラスはローカル待機ハンドル イベントを表します。これは、シグナル状態になった後、手動でリセットする必要があります。 このクラスは、その基底クラス <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> の特殊なケースを表します。 手動リセット イベントの使用方法と機能については、[EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) の概念に関する文書を参照してください。  
  
 <xref:System.Threading.ManualResetEvent> オブジェクトは、<xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> メソッドが呼び出されるまでシグナル状態のままです。 待機スレッド、つまりイベントがシグナル状態になるまで待機するスレッドは、そのオブジェクトがシグナル状態である間にいくつでも解放できます。 <xref:System.Threading.ManualResetEvent> は、`bManualReset` 引数に対して `true` を指定する、Win32 `CreateEvent` 呼び出しに対応します。  
  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、待機時間が非常に短いと予測される場合とイベントがプロセスの境界を越えない場合に、<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> クラスを使用してパフォーマンスを高めることができます。 <xref:System.Threading.ManualResetEventSlim> は、イベントがシグナル状態になるまで待機している間、ビジー スピンを短時間使用します。 待機時間が短い場合、待機ハンドルを使用して待機するより、スピンを使用するほうが負荷が大幅に低くなります。 ただし、特定の期間内にイベントがシグナル状態にならない場合、<xref:System.Threading.ManualResetEventSlim> は通常のイベント ハンドル待機を使用します。  
  
## <a name="see-also"></a>参照  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [待機ハンドル](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Semaphore と SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
