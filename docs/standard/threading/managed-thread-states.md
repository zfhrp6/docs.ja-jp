---
title: "マネージ スレッドの状態"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 073fb19ef34ba32ccb5d5664413718a436563770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="managed-thread-states"></a>マネージ スレッドの状態
プロパティ<xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType>スレッドの現在の状態を示すビット マスクを提供します。 スレッドは、 <xref:System.Threading.ThreadState> 列挙型に含まれる状態のうち、常に少なくとも 1 つの状態となり、同時に複数の状態になることもあります。  
  
> [!IMPORTANT]
>  スレッドの状態は、いくつかのデバッグ シナリオでのみ必要になります。 スレッドの動作を同期化する目的でコード内でスレッドの状態を使用しないでください。  
  
 マネージ スレッドを作成すると、そのスレッドは <xref:System.Threading.ThreadState.Unstarted> 状態になります。 スレッドは、オペレーティング システムによって起動状態にされるまで、 <xref:System.Threading.ThreadState.Unstarted> 状態のままです。 <xref:System.Threading.Thread.Start%2A> を呼び出すと、スレッドを開始できることをオペレーティング システムに通知できますが、スレッドの状態は変化しません。  
  
 マネージ環境に入ってくるアンマネージ スレッドは、既に起動状態になっています。 スレッドがいったん起動状態になると、さまざまなアクションによってスレッドの状態が変更される可能性があります。 状態が変更される原因となるアクションと、対応する新しい状態を次の表に示します。  
  
|アクション|変更後の新しい状態|  
|------------|-------------------------|  
|<xref:System.Threading.Thread> クラスのコンストラクターが呼び出される。|<xref:System.Threading.ThreadState.Unstarted>|  
|別のスレッド呼び出し<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>です。|<xref:System.Threading.ThreadState.Unstarted>|  
|スレッドが応答する<xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>して実行を開始します。|<xref:System.Threading.ThreadState.Running>|  
|スレッドの呼び出し<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>です。|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|スレッドの呼び出し<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>別のオブジェクトにします。|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|スレッドの呼び出し<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>別のスレッドでします。|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|別のスレッド呼び出し<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>です。|<xref:System.Threading.ThreadState.SuspendRequested>|  
|スレッドが応答する、<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>要求します。|<xref:System.Threading.ThreadState.Suspended>|  
|別のスレッド呼び出し<xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>です。|<xref:System.Threading.ThreadState.Running>|  
|別のスレッド呼び出し<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>です。|<xref:System.Threading.ThreadState.AbortRequested>|  
|スレッドが応答する、<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>です。|<xref:System.Threading.ThreadState.Aborted>の後 <xref:System.Threading.ThreadState.Stopped>|  
  
 <xref:System.Threading.ThreadState.Running> 状態の値は 0 のため、ビット テストを実行しても、この状態を検出できません。 代わりに、擬似コードによる次のテストを実行できます。  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 スレッドは、どの時点でも複数の状態にあることがよくあります。 などのスレッドがブロックされている場合、<xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>呼び出しと別のスレッドの呼び出し<xref:System.Threading.Thread.Abort%2A>その同じスレッドでスレッドされます両方で、<xref:System.Threading.ThreadState.WaitSleepJoin>と<xref:System.Threading.ThreadState.AbortRequested>同時状態です。 この場合、スレッドは、 <xref:System.Threading.Monitor.Wait%2A> への呼び出しから戻るか中断されるとすぐに、 <xref:System.Threading.ThreadAbortException>を受け取ります。  
  
 スレッドは、 <xref:System.Threading.ThreadState.Unstarted> への呼び出しの結果として <xref:System.Threading.Thread.Start%2A>状態から出ると、 <xref:System.Threading.ThreadState.Unstarted> 状態に戻ることはできません。 また、スレッドは <xref:System.Threading.ThreadState.Stopped> 状態から出ることはできません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [スレッド化](../../../docs/standard/threading/index.md)
