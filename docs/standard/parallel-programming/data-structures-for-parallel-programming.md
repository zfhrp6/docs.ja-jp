---
title: "並列プログラミングのデータ構造"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f35c5382455021f0a001604367e59204ce4ad93c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="data-structures-for-parallel-programming"></a>並列プログラミングのデータ構造
.NET Framework version 4 には、同時実行コレクション クラス、軽量な同期プリミティブ、および遅延初期化の種類のセットなどの並列プログラミングに役立ついくつかの新しい型が導入されています。 タスク並列ライブラリおよび PLINQ を含めて、マルチ スレッド アプリケーション コードでこれらの型を使用することができます。  
  
## <a name="concurrent-collection-classes"></a>同時実行コレクション クラス  
 内のコレクション クラス、<xref:System.Collections.Concurrent?displayProperty=nameWithType>スレッド セーフを提供する名前空間を追加、削除可能な場合は、ロックを回避する操作とロックが必要な粒度の細かいロックを使用します。 .NET Framework のバージョン 1.0 および 2.0 で導入されたコレクションとは異なり、同時実行コレクション クラスに項目にアクセスするときに、すべてのロックを実行するユーザー コードは必要ありません。 同時実行コレクション クラスが大幅にパフォーマンスが向上種類など<xref:System.Collections.ArrayList?displayProperty=nameWithType>と<xref:System.Collections.Generic.List%601?displayProperty=nameWithType>(ロックを使用してユーザー実装) では複数のスレッドが追加し、コレクションから項目を削除します。  
  
 次の表は、新しい同時実行コレクション クラスを示します。  
  
|型|説明|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> を実装するスレッド セーフなコレクションに、ブロッキングと範囲指定の機能を提供します。 利用できるスロットがない場合、またはコレクションがいっぱいの場合は、producer スレッドがブロックされます。 コレクションが空の場合、コンシューマーのスレッドがブロックします。 この型には、コンシューマーとプロデューサーによって非ブロッキング アクセスもサポートしています。 <xref:System.Collections.Concurrent.BlockingCollection%601>基底クラスとして使用できますか、バッキング ストアに、ブロッキングとをサポートする任意のコレクション クラスの境界を提供する<xref:System.Collections.Generic.IEnumerable%601>です。|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|スケーラビリティを提供するスレッド セーフであるバッグの実装では、追加し、操作を取得します。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|スケーラブルな同時実行ディクショナリ型。|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|同時実行と拡張性の高い FIFO キューです。|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|同時実行と拡張性の高い LIFO スタック。|  
  
 詳しくは、「[スレッド セーフなコレクション](../../../docs/standard/collections/thread-safe/index.md)」を参照してください。  
  
## <a name="synchronization-primitives"></a>同期プリミティブ  
 新しい同期プリミティブ、<xref:System.Threading?displayProperty=nameWithType>名前空間が従来のマルチ スレッド コード内で見つかった高コストのロック メカニズムを回避することで粒度の細かい同時実行性と高速なパフォーマンスを有効にします。 いくつか、新しい型のように<xref:System.Threading.Barrier?displayProperty=nameWithType>と<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>.NET Framework の以前のリリースに対応するがあるないです。  
  
 次の表は、新しい同期型を示します。  
  
|型|説明|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|アルゴリズムで並行してポイントする各タスクは到着を通知して、一部またはすべてのタスクが到着するまでのブロックを指定して作業する複数のスレッドを有効にします。 詳細については、「[バリア](../../../docs/standard/threading/barrier.md)」を参照してください|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Rendezvous の簡単なメカニズムを提供することで、フォークと結合のシナリオを簡略化します。 詳細については、次を参照してください。 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)です。|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|ような同期プリミティブ<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>です。 <xref:System.Threading.ManualResetEventSlim>軽量がプロセス間通信用にのみ使用できます。 詳細については、次を参照してください。 [ManualResetEvent と ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)です。|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|同期プリミティブは、リソースを同時にアクセスできるスレッドの数またはリソースのプールを制限します。 詳細については、次を参照してください。 [Semaphore と SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)です。|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|スレッドを原因となった相互排他ロック プリミティブが、ループ内で待機するロックを取得しようとしてまたは*スピン*クォンタムを生成する前に、期間。 ここで、ロックを待機できると予想される短いシナリオで<xref:System.Threading.SpinLock>オファー ロックの他の形式よりもパフォーマンスが向上します。 詳細については、次を参照してください。[スピンロック](../../../docs/standard/threading/spinlock.md)です。|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|小型、軽量の型で、スピン、指定した時間と最終的には、スピン カウントが超過した場合、待機状態に、スレッドを配置します。  詳細については、次を参照してください。 [SpinWait](../../../docs/standard/threading/spinwait.md)です。|  
  
 詳細については次を参照してください:  
  
-   [方法: 下位レベルの同期に SpinLock を使用する](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [方法: バリアと同時実行操作を同期](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)です。  
  
## <a name="lazy-initialization-classes"></a>遅延初期化クラス  
 限定的な初期化が必要になるまで、オブジェクトのメモリには割り当てられません。 限定的な初期化は、オブジェクトの割り当てをプログラムの有効期間に均等に分散させることによってパフォーマンスを向上できます。 型をラッピングするを任意のカスタム型の限定的な初期化を有効にする<xref:System.Lazy%601>です。  
  
 次の表は、遅延初期化の種類を示します。  
  
|型|説明|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|軽量のスレッド セーフである限定的な初期化を提供します。|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|スレッドごとの単位で限定的に呼び出す初期化関数の各スレッドで遅延初期化の値を提供します。|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|遅延初期化の専用インスタンスを割り当てる必要を避けるための静的メソッドを提供します。 代わりに、参照を使用してアクセスされたときのみ、ターゲットが初期化されているを確認してください。|  
  
 詳細については、「[限定的な初期化](../../../docs/framework/performance/lazy-initialization.md)」を参照してください。  
  
## <a name="aggregate-exceptions"></a>例外の集約  
 <xref:System.AggregateException?displayProperty=nameWithType>型は、別のスレッドで同時にスローされ、1 つの例外として連結されたスレッドに戻すことを複数の例外をキャプチャするために使用できます。 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>と<xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>型および PLINQ を使用して<xref:System.AggregateException>この目的で広範囲にします。 詳細については、次を参照してください。 [NIB: 方法: タスクによってスローされた例外を処理](http://msdn.microsoft.com/en-us/d6c47ec8-9de9-4880-beb3-ff19ae51565d)と[する方法: PLINQ クエリの例外を処理](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Threading?displayProperty=nameWithType>  
 [並列プログラミング](../../../docs/standard/parallel-programming/index.md)
