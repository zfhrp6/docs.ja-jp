---
title: Thread.Suspend、ガベージ コレクション、およびセーフ ポイント
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ded5c057b1c257e8bcf3c8427f5810720eaf0947
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a>Thread.Suspend、ガベージ コレクション、およびセーフ ポイント
スレッドで <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> を呼び出すと、システムはスレッドの中断が要求されたことを示し、スレッドを実際に中断する前にセーフ ポイントに到達するまでスレッドを実行することができます。 スレッドのセーフ ポイントは、ガベージ コレクションを実行できる実行ポイントです。  
  
 セーフ ポイントに到達すると、ランタイムにより、中断されたスレッドがマネージ コードで続行されないことが保証されます。 マネージ コードの外部で実行中のスレッドは、通常、ガベージ コレクションでは安全であり、その実行はマネージ コードの実行再開が試行されるまで続行します。  
  
> [!NOTE]
>  ガベージ コレクションを実行するために、ランタイムはコレクションを実行中のスレッドを除くすべてのスレッドを中断する必要があります。 各スレッドを中断するには、セーフ ポイントに移動する必要があります。  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [自動メモリ管理](../../../docs/standard/automatic-memory-management.md)
