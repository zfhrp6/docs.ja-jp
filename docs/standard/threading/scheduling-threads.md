---
title: "Scheduling Threads | Microsoft Docs"
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
  - "threading [.NET Framework], scheduling"
  - "scheduling threads"
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Scheduling Threads
すべてのスレッドには、スレッド優先順位が割り当てられます。  共通言語ランタイム内で作成されたスレッドには、初期状態で **ThreadPriority.Normal** の優先順位が割り当てられます。  ランタイムがの外部で作成されたスレッドは、マネージ環境に入る前に設定されていた優先順位が維持されます。  任意のスレッドの優先順位を取得または設定するには、**Thread.Priority** プロパティを使用します。  
  
 スレッドの実行は、優先順位に基づいてスケジュールされます。  スレッドがランタイム内で実行されている場合でも、オペレーティング システムは、すべてのスレッドにプロセッサ タイム スライスを割り当てます。  スレッドの実行順序を決定するために使用されるスケジューリング アルゴリズムの詳細は、オペレーティング システムによって異なります。  オペレーティング システムによっては、実行可能なスレッドの中で最も優先順位の高いスレッドが常に最初に実行されるようにスケジュールされます。  同じ優先順位を持つ複数のスレッドがすべて実行可能である場合、スケジューラは、その優先順位にあるスレッド間を循環することで各スレッドに一定の実行用タイム スライスを与えます。  より優先順位の高いスレッドが実行可能である限り、それよりも優先順位の低いスレッドは実行されません。  特定の優先順位を持つ実行可能なスレッドがなくなると、スケジューラは次に低い優先順位に移り、その優先順位にあるスレッドの実行をスケジュールします。  より優先順位の高いスレッドが実行可能になった場合も、それよりも優先順位の低いスレッドの代わりに優先順位の高いスレッドが実行されます。  また、オペレーティング システムは、アプリケーションのユーザー インターフェイスをフォアグラウンドとバックグラウンド間で移動させながら、スレッドの優先順位を動的に調整することもできます。  オペレーティング システムによっては、別のスケジューリング アルゴリズムが使用される場合があります。  
  
## 参照  
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)   
 [Managed and Unmanaged Threading in Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)