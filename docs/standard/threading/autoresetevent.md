---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent>クラスはシグナルを受け取ると、1 つの待機中のスレッドを解放した後に自動的にリセットするローカルの待機ハンドルのイベントを表します。 このクラスは、その基本クラスの特殊なケースを表します<xref:System.Threading.EventWaitHandle>です。 自動リセット イベントの使用方法と機能については、[EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) の概念に関する文書を参照してください。  
  
 <xref:System.Threading.AutoResetEvent>オブジェクトが自動的にリセットを非シグナル、システムによって 1 つの待機中のスレッドが解放された後です。 待機しているスレッドがない場合でも、イベント オブジェクトの状態はシグナルのままです。 <xref:System.Threading.AutoResetEvent>Win32 に対応する`CreateEvent`を呼び出すと、指定する`false`の`bManualReset`引数。  
  
 使用する例については<xref:System.Threading.AutoResetEvent>を参照してください[モニター](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [待機ハンドル](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
