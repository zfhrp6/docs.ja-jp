---
title: "スレッドの一時中断と再開"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resuming threads
- threading [.NET Framework], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b146987d2491f044e1f5794eba17d02d8f5e478c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="pausing-and-resuming-threads"></a>スレッドの一時中断と再開
スレッドの活動を同期する最も一般的な方法は、スレッドのブロックと解放を行うか、コード領域またはオブジェクトをロックすることです。 ロックとブロックのしくみの詳細については、「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
 また、スレッドそのものをスリープ状態にすることもできます。 スレッドがブロックされているかまたはスリープ状態の場合は、<xref:System.Threading.ThreadInterruptedException> を使用して待機状態を解除できます。  
  
## <a name="the-threadsleep-method"></a>Thread.Sleep メソッド  
 呼び出す、<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>メソッドが現在のスレッド (ミリ秒) か、メソッドに渡す時間間隔の数をすぐにブロックして、別のスレッドに自らのタイム スライスの残りの部分が生成されます。 時間が経過すると、スリープ状態のスレッドは実行を再開します。  
  
 もう一方のスレッドが他方のスレッドに対して <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> を呼び出すことはできません。  <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>常に現在のスレッドがスリープ状態の原因となる静的メソッドです。  
  
 呼び出す<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>の値を持つ<xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType>スレッドを呼び出す別のスレッドによって中断されるまで、スリープ状態を<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>メソッドへの呼び出しによって停止されるまでまたはスリープ状態のスレッドでその<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>メソッドです。  次の例は、スリープ状態のスレッドを中断する両方の方法を示しています。  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a>スレッドの中断  
 呼び出して待機中のスレッドを中断することができます、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>をスローする、ブロックされたスレッド上のメソッド、 <xref:System.Threading.ThreadInterruptedException>、ブロッキング呼び出しからスレッドを中断します。 スレッドは、<xref:System.Threading.ThreadInterruptedException> をキャッチし、操作を継続するために適切な処理を行う必要があります。 スレッドがこの例外を無視した場合は、ランタイムがこの例外をキャッチし、そのスレッドを停止します。  
  
> [!NOTE]
>  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> が呼び出されたときに対象となるスレッドがブロックされていない場合、スレッドはブロックされるまで中断されません。 スレッドがまったくブロックされない場合は、中断されることなく完了することがあります。  
  
 待機がマネージ待機である場合、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> と <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> はどちらもすぐにスレッドを起動します。 待機がアンマネージ待機の場合 (など、プラットフォーム呼び出しに Win32 [WaitForSingleObject](https://msdn.microsoft.com/library/windows/desktop/ms687032\(v=vs.85\).aspx)関数)、どちらも<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>も<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>戻るか、またはマネージ コードを呼び出すまで、スレッドの制御が可能にします。 マネージ コードの動作は次のとおりです。  
  
-   <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> はスレッドをどのような待機からも起動し、これによって起動先のスレッドで <xref:System.Threading.ThreadInterruptedException> がスローされます。  
  
-   <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>スレッドによりしている可能性がありますすべての待機をスリープ状態を解除、<xref:System.Threading.ThreadAbortException>スレッドでスローされます。 詳細については、「[スレッドの破棄](../../../docs/standard/threading/destroying-threads.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadInterruptedException>  
 <xref:System.Threading.ThreadAbortException>  
 [スレッド化](../../../docs/standard/threading/index.md)  
 [スレッドの使用とスレッド処理](../../../docs/standard/threading/using-threads-and-threading.md)  
 [同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)
