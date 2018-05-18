---
title: 同期プリミティブの概要
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e35c2337ff7e416cb5f2c869f8ede160e05d369f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="overview-of-synchronization-primitives"></a>同期プリミティブの概要
<a name="top"></a>.NET Framework には、スレッドの相互作用を制御したり競合状態を回避したりするためのさまざまな同期プリミティブが用意されています。 これらは、大きくは 3 つのカテゴリ (ロック、シグナリング、インタロックされた操作) に分類することができます。  
  
 これらのカテゴリはきちんと整理されたものでも、明確に定義されたものでもありません。つまり、複数のカテゴリの特性を持つ同期機構もあります。たとえば、1 つのスレッドを同時に解放するイベントは、機能的にロックに似ています。また、ロックの解放はシグナルと考えることができます。インタロックされた操作を使用してロックを作成できます。 しかし、これらのカテゴリは有用です。  
  
 スレッド同期は協調的であるということを忘れないようにするのが重要です。 1 つのスレッドが同期機構をバイパスして、保護リソースに直接アクセスしただけで、その同期機構は有効でなくなります。  
  
 この概要は、次のセクションで構成されています。  
  
-   [ロック](#locking)  
  
-   [シグナリング](#signaling)  
  
-   [軽量の同期型](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [インタロックされた操作](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>ロック  
 ロックは、リソースの制御を一度に 1 つのスレッドに渡したり、指定された数のスレッドに渡したりします。 ロックが使用されているときに排他ロックを要求したスレッドは、ロックが使用可能になるまでブロックされます。  
  
### <a name="exclusive-locks"></a>排他ロック  
 ロックの最も単純な形式は、C# では `lock` ステートメントであり、Visual Basic では `SyncLock` ステートメントです。これらのステートメントは、コード ブロックへのアクセスを制御します。 このようなブロックはしばしば、クリティカル セクションと呼ばれます。 `lock` ステートメントは <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> メソッドと <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> メソッドを使用して実装され、`try…catch…finally` ブロックを使用してロックが解放されるようにします。  
  
 一般的に、`lock` ステートメントまたは `SyncLock` ステートメントを使用して小さいコード ブロックを保護して、1 つのメソッドより広げないようにするのが、<xref:System.Threading.Monitor> クラスを使用するための最適な方法です。 <xref:System.Threading.Monitor> クラスは強力ですが、孤立したロックやデッドロックが発生しやすくなります。  
  
#### <a name="monitor-class"></a>Monitor クラス  
 <xref:System.Threading.Monitor> クラスは、`lock` ステートメントと併せて使用できる追加機能を備えています。  
  
-   <xref:System.Threading.Monitor.TryEnter%2A> メソッドは、ブロックされている間に指定時間間隔後にリソースが解放されるのを待機するスレッドを可能にします。 このメソッドは、成功または失敗を示すブール値を返します。この値を使用して、デッドロックの可能性を検出して回避できます。  
  
-   <xref:System.Threading.Monitor.Wait%2A> メソッドは、クリティカル セクション内のスレッドで呼び出されます。 このメソッドは、リソースが再び使用可能になるまでリソースの制御を放棄し、ブロックされます。  
  
-   <xref:System.Threading.Monitor.Pulse%2A> メソッドと <xref:System.Threading.Monitor.PulseAll%2A> メソッドは、ロックを解放しようとしているスレッドや、1 つ以上のスレッドを実行待ちキューに入れるために <xref:System.Threading.Monitor.Wait%2A> を呼び出そうとしているスレッドを可能にして、それらのスレッドがロックを取得できるようにします。  
  
 <xref:System.Threading.Monitor.Wait%2A> メソッドのオーバーロードでのタイムアウトは、待機中のスレッドが実行待ちキューにエスケープすることを可能にします。  
  
 <xref:System.Threading.Monitor> クラスは、ロックに使用されるオブジェクトが <xref:System.MarshalByRefObject> から派生していれば、複数のアプリケーション ドメインでロックを提供できます。  
  
 <xref:System.Threading.Monitor> にはスレッド アフィニティがあります。 つまり、モニターに入ったスレッドは、<xref:System.Threading.Monitor.Exit%2A> または <xref:System.Threading.Monitor.Wait%2A> を呼び出すことによって終了しなければなりません。  
  
 <xref:System.Threading.Monitor> クラスはインスタンス化可能ではありません。 このメソッドは静的 (Visual Basic では `Shared`) であり、インスタンス化可能ロック オブジェクトに対して作用します。  
  
 概念的概要については、「[モニター](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)」を参照してください。  
  
#### <a name="mutex-class"></a>Mutex クラス  
 スレッドは、<xref:System.Threading.Mutex> をその <xref:System.Threading.WaitHandle.WaitOne%2A> メソッドのオーバーロードを呼び出すことによって要求します。 スレッドが待機を中止することができるように、タイムアウトを使用するオーバーロードが用意されています。 <xref:System.Threading.Monitor> クラスとは異なり、ミューテックスはローカルもグローバルも可能です。 グローバル ミューテックスは名前付きミューテックスとも呼ばれ、オペレーティング システム全体で可視です。したがって、複数のアプリケーション ドメインまたはプロセス内のスレッドの同期化に使用できます。 ローカル ミューテックスは <xref:System.MarshalByRefObject> から派生し、アプリケーション ドメインの境界を越えて使用できます。  
  
 さらに、<xref:System.Threading.Mutex> は <xref:System.Threading.WaitHandle> から派生します。これは、<xref:System.Threading.WaitHandle.WaitAll%2A> メソッド、<xref:System.Threading.WaitHandle.WaitAny%2A> メソッド、<xref:System.Threading.WaitHandle.SignalAndWait%2A> メソッドなど、<xref:System.Threading.WaitHandle> が提供するシグナリング機構とともに使用できることを意味します。  
  
 <xref:System.Threading.Monitor> と同様に、<xref:System.Threading.Mutex> にはスレッド アフィニティがあります。 <xref:System.Threading.Monitor> とは異なり、<xref:System.Threading.Mutex> はインスタンス化可能オブジェクトです。  
  
 概念的概要については、「[ミューテックス](../../../docs/standard/threading/mutexes.md)」を参照してください。  
  
#### <a name="spinlock-class"></a>SpinLock クラス  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降、<xref:System.Threading.Monitor> にとって必要なオーバーヘッドのためにパフォーマンスが低下する場合は、<xref:System.Threading.SpinLock> クラスを使用できるようになりました。 <xref:System.Threading.SpinLock> は、ロックされたクリティカル セクションを検出すると、ロックが使用可能になるまで単にループ内をスピンします。 ロックが保持される時間が非常に短い場合は、ブロックよりもスピンのほうがパフォーマンスがよいことがあります。 ただし、ロックが保持される期間が数十サイクル以上の場合、<xref:System.Threading.SpinLock> は <xref:System.Threading.Monitor> と同様のパフォーマンスを示しますが、使用する CPU サイクルが多くなるため、他のスレッドやプロセスのパフォーマンスが低下する可能性があります。  
  
### <a name="other-locks"></a>他のロック  
 ロックは排他的である必要はありません。 多くの場合、限定された数のスレッドがリソースに同時にアクセスすることを許可すると有用です。 セマフォおよびリーダー/ライター ロックは、このようなプールされたリソース アクセスを制御することを意図して設計されています。  
  
#### <a name="readerwriterlock-class"></a>ReaderWriterLock クラス  
 <xref:System.Threading.ReaderWriterLockSlim> クラスは、データを変更するスレッド (ライター) がリソースへの排他アクセスを必要とするケースに対処します。 ライターがアクティブでない場合は、任意の数のリーダーが (たとえば <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A> メソッドを呼び出して) リソースにアクセスできます。 スレッドが (たとえば <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A> メソッドを呼び出して) 排他アクセスを要求すると、後続のリーダーの要求は、既存のすべてのリーダーがロックを終了し、ライターがロックに参加して終了するまでブロックされます。  
  
 <xref:System.Threading.ReaderWriterLockSlim> にはスレッド アフィニティがあります。  
  
 概念的概要については、「[読み取り/書き込みロック](../../../docs/standard/threading/reader-writer-locks.md)」を参照してください。  
  
#### <a name="semaphore-class"></a>Semaphore クラス  
 <xref:System.Threading.Semaphore> クラスは、指定した数のスレッドがリソースにアクセスできるようにします。 リソースを要求する追加のスレッドは、スレッドがセマフォを解放するまでブロックされます。  
  
 <xref:System.Threading.Mutex> クラスと同様に、<xref:System.Threading.Semaphore> は <xref:System.Threading.WaitHandle> から派生します。 また、<xref:System.Threading.Mutex> と同様に、<xref:System.Threading.Semaphore> はローカルもグローバルも可能です。 アプリケーション ドメインの境界を越えて使用できます。  
  
 <xref:System.Threading.Monitor>、<xref:System.Threading.Mutex>、<xref:System.Threading.ReaderWriterLock> とは異なり、<xref:System.Threading.Semaphore> にはスレッド アフィニティがありません。 これは、1 つのスレッドがセマフォを取得して別のスレッドがそれを解放するシナリオで使用できることを意味します。  
  
 概念的概要については、「[Semaphore と SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)」を参照してください。  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> は、1 つのプロセス境界内の同期化のための軽量セマフォです。  
  
 [ページのトップへ](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>シグナリング  
 別のスレッドからのシグナルを待機する最も簡単な方法は、<xref:System.Threading.Thread.Join%2A> メソッドを呼び出すことです。これにより、他方のスレッドが完了するまでブロックされます。 <xref:System.Threading.Thread.Join%2A> には、ブロックされたスレッドが指定時間間隔経過後に待機から抜け出すことを許可する 2 つのオーバーロードがあります。  
  
 待機ハンドルは、待機機能とシグナリング機能の非常に豊富なセットを提供します。  
  
### <a name="wait-handles"></a>待機ハンドル  
 待機ハンドルは <xref:System.Threading.WaitHandle> クラスから派生し、このクラスは <xref:System.MarshalByRefObject> から派生します。 したがって、待機ハンドルを使用して、アプリケーション ドメインの境界を越えてスレッドのアクティビティを同期させることができます。  
  
 インスタンス メソッド <xref:System.Threading.WaitHandle.WaitOne%2A> か、静的メソッド <xref:System.Threading.WaitHandle.WaitAll%2A>、<xref:System.Threading.WaitHandle.WaitAny%2A>、<xref:System.Threading.WaitHandle.SignalAndWait%2A> のいずれかを呼び出すことによって、スレッドは待機ハンドルでブロックされます。 それらがどのように解放されるかは、呼び出されたメソッドと待機ハンドルの種類に応じて決まります。  
  
 概念的概要については、「[待機ハンドル](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)」を参照してください。  
  
#### <a name="event-wait-handles"></a>イベント待機ハンドル  
 イベント待機ハンドルには、<xref:System.Threading.EventWaitHandle> クラスとその派生クラスの <xref:System.Threading.AutoResetEvent> および <xref:System.Threading.ManualResetEvent> が含まれます。 <xref:System.Threading.EventWaitHandle.Set%2A> メソッドを呼び出すか <xref:System.Threading.WaitHandle.SignalAndWait%2A> メソッドを使用してイベント待機ハンドルに通知されると、スレッドはイベント待機ハンドルから解放されます。  
  
 イベント待機ハンドルは、通知されるたびにスレッドが 1 つだけ通過できるようにする回転ドアのように、自身を自動的にリセットします。あるいは、通知されるまで閉じていてだれかが閉じるまで開いているゲートのように、手動でリセットされる必要があります。 名前が示すとおり、<xref:System.Threading.AutoResetEvent> と <xref:System.Threading.ManualResetEvent> はそれぞれ前者と後者を表します。 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> は、1 つのプロセス境界内の同期化のための軽量イベントです。  
  
 <xref:System.Threading.EventWaitHandle> はイベントのいずれかの種類を表すことができ、ローカルもグローバルも可能です。 派生クラスの <xref:System.Threading.AutoResetEvent> と <xref:System.Threading.ManualResetEvent> は常にローカルです。  
  
 イベント待機ハンドルにはスレッド アフィニティがありません。 どのスレッドもイベント待機ハンドルに通知できます。  
  
 概念的概要については、「[EventWaitHandle、AutoResetEvent、および ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)」を参照してください。  
  
#### <a name="mutex-and-semaphore-classes"></a>Mutex クラスと Semaphore クラス  
 <xref:System.Threading.Mutex> クラスと <xref:System.Threading.Semaphore> クラスは、<xref:System.Threading.WaitHandle> から派生するので、<xref:System.Threading.WaitHandle> の静的メソッドとともに使用できます。 たとえば、スレッドは <xref:System.Threading.WaitHandle.WaitAll%2A> メソッドを使用して、「<xref:System.Threading.EventWaitHandle> に通知された」、「<xref:System.Threading.Mutex> が解放された」、「<xref:System.Threading.Semaphore> が解放された」の 3 つの条件がすべて該当するまで待機できます。 同じように、スレッドは <xref:System.Threading.WaitHandle.WaitAny%2A> メソッドを使用して、それらの条件のいずれか 1 つが該当するまで待機することができます。  
  
 <xref:System.Threading.Mutex> または <xref:System.Threading.Semaphore> にとって、通知されるということは解放されるということを意味します。 いずれかの種類が <xref:System.Threading.WaitHandle.SignalAndWait%2A> メソッドの最初の引数として使用されると、それが解放されます。 スレッド アフィニティのある <xref:System.Threading.Mutex> については、呼び出し元のスレッドがミューテックスを所有していなければ、例外がスローされます。 既に説明したように、セマフォにはスレッド アフィニティがありません。  
  
#### <a name="barrier"></a>バリア  
 <xref:System.Threading.Barrier> クラスは、複数のスレッドを周期的に同期させるようにするためのものです。その結果、それらすべてが同じポイントでブロックされ、他のすべてのスレッドが完了するのを待機するようになります。 バリアは、1 つまたは複数のスレッドが、アルゴリズムの次のフェーズに進む前に別のスレッドの結果を必要とする場合に有用です。 詳細については、「[バリア](../../../docs/standard/threading/barrier.md)」を参照してください  
  
 [ページのトップへ](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>軽量の同期型  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降、高速パフォーマンスが得られる同期プリミティブを使用できるようになりました。この場合、待機ハンドルなど Win32 カーネル オブジェクトへの高コストの依存が可能な限り回避されます。 これらのタイプは一般に、待機時間が短く、かつオリジナルの同期タイプを試してみて満足できないことがわかったときだけ使用するようにしてください。 プロセス間通信を必要とするシナリオでは、軽量タイプを使用できません。  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> は <xref:System.Threading.Semaphore?displayProperty=nameWithType> の軽量バージョンです。  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> は <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> の軽量バージョンです。  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> は、そのカウントが 0 になると通知されるようになるイベントを表します。  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType> は、マスター スレッドによる制御を必要とせずに複数のスレッドを相互に同期させることができるようにします。 バリアは、指定されたポイントにすべてのスレッドが達するまで各スレッドが続行するのを防止します。  
  
 [ページのトップへ](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降、<xref:System.Threading.SpinWait?displayProperty=nameWithType> 構造体を使用できるようになりました。この構造体は、イベントが通知されるか条件が満たされるのをスレッドが待機する必要があるが、待機ハンドルを使用するかあるいは現在のスレッドをブロックする際に必要な待機時間よりも実際の待機時間が短いと思われる場合に使用します。 <xref:System.Threading.SpinWait> を使用することにより、待機中はスピンし、指定した時間内に条件が満たされなかった場合のみ (たとえば待機またはスリープして) 譲渡するための短い時間を指定できます。  
  
 [ページのトップへ](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>インタロックされた操作  
 インタロックされた操作とは、<xref:System.Threading.Interlocked> クラスの静的メソッドによって実行される、メモリ位置に対する単純なアトミック操作のことです。 それらのアトミック操作としては、32 ビット プラットフォーム上の 64 ビット値を対象とした追加、インクリメントとデクリメント、交換、比較による条件付き交換、読み取りの各操作があります。  
  
> [!NOTE]
>  アトミック性の保証は個々 の操作に限定されます。複数の操作を 1 つの単位として実行する必要がある場合は、より粒度の粗い同期機構を使用する必要があります。  
  
 これらの操作は、どれもロックやシグナルではありませんが、ロックやシグナルの作成に使用できます。 これらは Windows オペレーティング システムのネイティブなので、インタロックされた操作は非常に高速です。  
  
 インタロックされた操作を揮発性メモリの保証下で使用して、強力な非ブロッキング同時実行を示すアプリケーションを作成できます。 ただし、高度な低レベル プログラミングが必要になるので、ほとんどの目的では、単純ロックを選択したほうが適切です。  
  
 概念的概要については、「[インタロックされた操作](../../../docs/standard/threading/interlocked-operations.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [マルチスレッド処理のためのデータの同期](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [モニター](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [ミューテックス](../../../docs/standard/threading/mutexes.md)  
 [Semaphore と SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [待機ハンドル](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [インタロックされた操作](../../../docs/standard/threading/interlocked-operations.md)  
 [読み取り/書き込みロック](../../../docs/standard/threading/reader-writer-locks.md)  
 [バリア](../../../docs/standard/threading/barrier.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
