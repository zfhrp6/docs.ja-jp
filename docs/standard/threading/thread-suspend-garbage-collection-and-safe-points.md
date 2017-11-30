---
title: "Thread.Suspend、ガベージ コレクション、およびセーフ ポイント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend、ガベージ コレクション、およびセーフ ポイント
呼び出すと<xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>システム ノートのスレッドの中断が要求されているし、により、実際には、スレッドを中断する前に、安全なポイントに達するまで実行するスレッドのスレッドでします。 スレッド セーフである点で、ガベージ コレクションを実行できる実行ポイントです。  
  
 セーフ ポイントに達すると、ランタイムはように中断されたスレッドは注意が必要、さらに進行状況のマネージ コードに保証されます。 マネージ コードの外部で実行中のスレッドがガベージ コレクションでは常に、その実行をマネージ コードの実行を再開しようとするまで続行します。  
  
> [!NOTE]
>  ガベージ コレクションを実行するために、ランタイムは、コレクションの実行スレッドを除くすべてのスレッドを中断する必要があります。 各スレッドは、中断する前に、セーフ ポイントに移動する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [自動メモリ管理](../../../docs/standard/automatic-memory-management.md)
