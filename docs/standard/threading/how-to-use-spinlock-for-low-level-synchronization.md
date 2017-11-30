---
title: "方法: 下位レベルの同期に SpinLock を使用する"
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
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>方法: 下位レベルの同期に SpinLock を使用する
次の例で使用する方法、<xref:System.Threading.SpinLock>です。  
  
## <a name="example"></a>例  
 この例ではクリティカル セクションには最小限の作業は、これはにとって適切な候補を実行、<xref:System.Threading.SpinLock>です。 少量の作業を増やすとパフォーマンスが向上、<xref:System.Threading.SpinLock>標準的なロックを比較します。 ただし、SpinLock が標準ロックよりも高負荷になるポイントがあります。 プロファイリング ツールで同時実行プロファイリング機能を使用して、どのタイプのロックを使用すればプログラムのパフォーマンスが高まるかを確認できます。 詳細については、「[同時実行ビジュアライザー](/visualstudio/profiling/concurrency-visualizer)」を参照してください。  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock>共有リソースのロックが保持されるを行わない場合に便利な場合あります非常に長いです。 そのような場合、マルチコア コンピューターでは、ロックが解除されるまで数回のサイクルの間、ブロックされたスレッドをスピンさせると効率が高まることがあります。 スピンするとスレッドはブロックされなくなりますが、これは CPU 負荷の高いプロセスです。 <xref:System.Threading.SpinLock>論理プロセッサまたはハイパー スレッディングのシステムで優先順位の逆転の枯渇を防ぐために特定の条件下でスピンは停止されます。  
  
 この例では、<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>クラスは、マルチ スレッド アクセスをユーザーの同期が必要です。 アプリケーションで .NET Framework version 4 を対象とする、別のオプションが使用する、<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>ユーザーのすべてのロックは不要です。  
  
 使用に注意してください`false`(`False` Visual Basic で) への呼び出しで<xref:System.Threading.SpinLock.Exit%2A>です。 これにより、最適なパフォーマンスを得られます。 メモリ フェンスを使用するには、IA64 アーキテクチャで `true` (`True`) を指定します。これにより、書き込みバッファーがフラッシュされるので、ロックを使用して他のスレッドを終了できるようになります。  
  
## <a name="see-also"></a>関連項目  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)
