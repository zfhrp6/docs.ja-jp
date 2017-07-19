---
title: "Data Structures for Parallel Programming | Microsoft Docs"
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
  - "data structures, multi-threading"
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Data Structures for Parallel Programming
.NET Framework Version 4 では、並列プログラミングに役立つ新しい型がいくつか導入されています。たとえば、一連の同時実行コレクション クラス、軽量な同期プリミティブ、限定的な初期化などです。  これらの型は、タスク並列ライブラリや PLINQ などのマルチスレッド アプリケーション コードで使用できます。  
  
## 同時実行コレクション クラス  
 <xref:System.Collections.Concurrent?displayProperty=fullName> 名前空間のコレクション クラスには、スレッド セーフな追加操作と削除操作が用意されており、できる限りロックを回避する一方で、ロックが必要な場合は粒度の細かいロックを使用できます。  .NET Framework Version 1.0 および 2.0 で導入されたコレクションとは異なり、同時実行コレクション クラスでは、項目にアクセスするときにロックを取得するユーザー コードを必要としません。  同時実行コレクション クラスでは、複数のスレッドが 1 つのコレクションに項目を追加したり、コレクションから項目を削除したりする場合に、<xref:System.Collections.ArrayList?displayProperty=fullName>、<xref:System.Collections.Generic.List%601?displayProperty=fullName> などの型で \(ユーザーが実装したロックを使用して\) パフォーマンスを大幅に向上させることができます。  
  
 次の表は、新しい同時実行コレクション クラスの一覧です。  
  
|型|説明|  
|-------|--------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=fullName>|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=fullName> を実装するスレッド セーフなコレクションに、ブロッキングと範囲指定の機能を提供します。  スロットが使用できないか、コレクションがいっぱいになった場合に、producer スレッドがブロックを実行します。  コレクションが空の場合、consumer スレッドがブロックを実行します。  また、この型は consumer と producer によってブロックされないアクセスもサポートしています。  <xref:System.Collections.Concurrent.BlockingCollection%601> は、<xref:System.Collections.Generic.IEnumerable%601> をサポートするコレクション クラスにブロッキングおよび境界を提供する基本クラスまたはバッキング ストアとして使用できます。|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=fullName>|スケーラブルな操作の追加と取得を提供するスレッド セーフなバッグの実装。|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=fullName>|同時実行されるスケーラブルなディクショナリ型。|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=fullName>|同時実行されるスケーラブルな FIFO キュー。|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=fullName>|同時実行されるスケーラブルな LIFO スタック。|  
  
 詳細については、「[スレッド セーフなコレクション](../../../docs/standard/collections/thread-safe/index.md)」を参照してください。  
  
## 同期プリミティブ  
 従来のマルチスレッド コードに見られる負荷の高いロック機構を使用する代わりに <xref:System.Threading?displayProperty=fullName> 名前空間の新しい同期プリミティブを使用すると、粒度の細かい同時実行とパフォーマンスの向上が実現されます。  <xref:System.Threading.Barrier?displayProperty=fullName>、<xref:System.Threading.CountdownEvent?displayProperty=fullName> などの新しい型の場合、.NET Framework の以前のリリースには同等の型がありません。  
  
 新しい同期型の一覧を次に示します。  
  
|型|説明|  
|-------|--------|  
|<xref:System.Threading.Barrier?displayProperty=fullName>|各タスクが到着を通知してから一部またはすべてのタスクが到着するまでブロックするポイントを指定して、複数のスレッドが並列のアルゴリズムで実行できるようにします。  詳細については、「[Barrier](../../../docs/standard/threading/barrier.md)」を参照してください。|  
|<xref:System.Threading.CountdownEvent?displayProperty=fullName>|容易な連結方法を提供して、フォークと結合の方法を簡略化します。  詳細については、「[CountdownEvent](../../../docs/standard/threading/countdownevent.md)」を参照してください。|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=fullName>|<xref:System.Threading.ManualResetEvent?displayProperty=fullName> に似た同期プリミティブです。  <xref:System.Threading.ManualResetEventSlim> は軽量ですが、プロセス間通信での使用に限定されます。  詳細については、「[ManualResetEvent and ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)」を参照してください。|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=fullName>|リソースまたはリソースのプールに同時にアクセスできるスレッドの数を制限する同期プリミティブです。  詳細については、「[Semaphore and SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)」を参照してください。|  
|<xref:System.Threading.SpinLock?displayProperty=fullName>|クォンタムを生成するまでの一定期間内に、ループまたは*スピン*で待機するロックの取得を試みるスレッドを発生させるロック プリミティブで、一度に 1 つしか指定できません。  ロックの待機時間が短いことが予測される場合、<xref:System.Threading.SpinLock> ではその他の形式のロックよりも高いパフォーマンスが得られます。  詳細については、「[SpinLock](../../../docs/standard/threading/spinlock.md)」を参照してください。|  
|<xref:System.Threading.SpinWait?displayProperty=fullName>|指定された時刻にスピンし、スピン カウントが超過した場合は最終的にスレッドを待機状態にする、小さくて軽量な型です。詳細については、「[SpinWait](../../../docs/standard/threading/spinwait.md)」を参照してください。|  
  
 詳細については、次のトピックを参照してください。  
  
-   [How to: Use SpinLock for Low\-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## 限定的な初期化クラス  
 限定的な初期化を使用すると、オブジェクトのメモリは必要になるまで割り当てられません。  限定的な初期化では、プログラムの有効期間内でオブジェクトの割り当てを均等に展開することによって、パフォーマンスが向上します。  <xref:System.Lazy%601> の型をラップすることにより、任意のカスタム型の限定的な初期化を有効にできます。  
  
 限定的な初期化の型の一覧を次に示します。  
  
|型|説明|  
|-------|--------|  
|<xref:System.Lazy%601?displayProperty=fullName>|軽量でスレッド セーフな限定的な初期化を提供します。|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=fullName>|初期化関数を限定的に呼び出す各スレッドで、スレッドごとに限定的に初期化された値を提供します。|  
|<xref:System.Threading.LazyInitializer?displayProperty=fullName>|専用の限定的な初期化インスタンスを割り当てる必要を回避する静的メソッドを提供します。  代わりに、参照を使用して、ターゲットがアクセスされるときに初期化されていることを確認します。|  
  
 詳細については、「[限定的な初期化](../../../docs/framework/performance/lazy-initialization.md)」を参照してください。  
  
## 例外の集約  
 <xref:System.AggregateException?displayProperty=fullName> 型を使用して、別のスレッドで同時にスローされた複数の例外をキャプチャし、単一の例外として連結しているスレッドに返すことができます。  <xref:System.Threading.Tasks.Task?displayProperty=fullName> 型、<xref:System.Threading.Tasks.Parallel?displayProperty=fullName> 型、および PLINQ は、この目的で幅広く <xref:System.AggregateException> を使用します。  詳細については、「[NIB: How to: Handle Exceptions Thrown by Tasks](http://msdn.microsoft.com/ja-jp/d6c47ec8-9de9-4880-beb3-ff19ae51565d)」および「[How to: Handle Exceptions in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)」を参照してください。  
  
## 参照  
 <xref:System.Collections.Concurrent?displayProperty=fullName>   
 <xref:System.Threading?displayProperty=fullName>   
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)