---
title: "マネージ スレッド プール"
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
- cpp
helpviewer_keywords:
- thread pooling [.NET Framework]
- thread pools [.NET Framework]
- threading [.NET Framework], thread pool
- threading [.NET Framework], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e50fd66096d6bd58fb7db692449e7f8654b5ca76
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="the-managed-thread-pool"></a>マネージ スレッド プール
<xref:System.Threading.ThreadPool> クラスを使用すると、システムによって管理されるワーカー スレッドのプールがアプリケーションに提供されます。これを利用すると、開発者は、スレッド管理ではなくアプリケーション タスクに注意を集中できるようになります。 バックグラウンド処理が必要な短いタスクがある場合、マネージ スレッド プールを使用すると、複数のスレッドを簡単に利用できます。 たとえば、[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、スレッド プールのスレッドで非同期タスクを実行する <xref:System.Threading.Tasks.Task> オブジェクトと <xref:System.Threading.Tasks.Task%601> オブジェクトを作成できます。  
  
> [!NOTE]
>  [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)] 以降では、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] の以前のリリースでボトルネックとして識別されていた 3 つの重要な分野 (キューへのタスクの配置、スレッド プールのスレッドのディスパッチ、および I/O 完了スレッドのディスパッチ) において、スレッド プールのスループットが大幅に向上しています。 この機能を使用するには、アプリケーションで [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] 以降を対象とする必要があります。  
  
 ユーザー インターフェイスと対話するバックグラウンド タスクの場合、.NET Framework Version 2.0 では、ユーザー インターフェイス スレッドで生成されたイベントを使用して通信する <xref:System.ComponentModel.BackgroundWorker> クラスも利用できます。  
  
 .NET Framework では、非同期 I/O 完了、タイマー コールバック、登録済みの待機操作、デリゲートを使用した非同期メソッド呼び出し、<xref:System.Net> ソケット接続などのさまざまな目的でスレッド プールのスレッドを使用します。  
  
## <a name="when-not-to-use-thread-pool-threads"></a>スレッド プールのスレッドを使用しない場合  
 次のような場合は、スレッド プールのスレッドを使用する代わりに独自のスレッドを作成して管理する方が適切です。  
  
-   フォア グラウンド スレッドが必要な場合。  
  
-   スレッドに特定の優先順位を設定する必要がある場合。  
  
-   スレッドを長時間にわたってブロックするタスクがある場合。 スレッド プールには最大数のスレッドが存在するため、多数のスレッド プール スレッドがブロックされると、タスクを開始できなくなることがあります。  
  
-   スレッドをシングルスレッド アパートメント内に配置する必要がある場合。 <xref:System.Threading.ThreadPool> スレッドはすべてマルチスレッド アパートメント内にあります。  
  
-   安定した ID をスレッドに関連付ける必要がある場合、またはスレッドを特定のタスク専用にする必要がある場合。  
  
## <a name="thread-pool-characteristics"></a>スレッド プールの特徴  
 スレッド プールのスレッドはバックグラウンド スレッドです。 「[フォアグラウンド スレッドとバックグラウンド スレッド](../../../docs/standard/threading/foreground-and-background-threads.md)」を参照してください。 各スレッドは、既定のスタック サイズを使用し、既定の優先順位で実行されます。また、各スレッドはマルチスレッド アパートメント内にあります。  
  
 プロセスごとにスレッド プールが 1 つだけあります。  
  
### <a name="exceptions-in-thread-pool-threads"></a>スレッド プールのスレッドでの例外  
 スレッド プールのスレッドで未処理の例外が発生すると、プロセスが終了します。 この規則には、次の 3 つの例外があります。  
  
-   <xref:System.Threading.Thread.Abort%2A> が呼び出されたため、スレッド プールのスレッドに <xref:System.Threading.ThreadAbortException> がスローされる。  
  
-   アプリケーション ドメインがアンロードされるため、スレッド プールのスレッドに <xref:System.AppDomainUnloadedException> がスローされる。  
  
-   共通言語ランタイムまたはホスト プロセスがスレッドを終了する。  
  
 詳しくは、「[マネージ スレッドの例外](../../../docs/standard/threading/exceptions-in-managed-threads.md)」をご覧ください。  
  
> [!NOTE]
>  .NET Framework Version 1.0 および 1.1 では、スレッド プールのスレッドの未処理の例外は、共通言語ランタイムによって通知なしにトラップされます。 このため、アプリケーション状態が破損し、最終的にアプリケーションが停止することになり、デバッグが困難になることがあります。  
  
### <a name="maximum-number-of-thread-pool-threads"></a>スレッド プールのスレッドの最大数  
 スレッド プールのキューに配置できる操作の数は、使用できるメモリの容量によってのみ制限されますが、スレッド プールでは、プロセス内で同時にアクティブにできるスレッドの数が制限されます。 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、プロセスのスレッド プールの既定のサイズは、仮想アドレス空間のサイズなど、いくつかの要素によって決まります。 スレッドの数は、プロセスで <xref:System.Threading.ThreadPool.GetMaxThreads%2A> メソッドを呼び出せば確認できます。  
  
 スレッドの最大数を制御するには、<xref:System.Threading.ThreadPool.GetMaxThreads%2A> メソッドと <xref:System.Threading.ThreadPool.SetMaxThreads%2A> メソッドを使用します。  
  
> [!NOTE]
>  .NET Framework Version 1.0 および 1.1 では、スレッド プールのサイズはマネージ コードから設定できません。 共通言語ランタイムをホストするコードでは、mscoree.h で定義された `CorSetMaxThreads` を使用してサイズを設定できます。  
  
### <a name="thread-pool-minimums"></a>スレッド プールの最小値  
 スレッド プールでは、カテゴリごとに指定された最小値に達するまで、要求に応じて新しいワーカー スレッドまたは I/O 完了スレッドが提供されます。 これらの最小値は、<xref:System.Threading.ThreadPool.GetMinThreads%2A> メソッドを使用して取得できます。  
  
> [!NOTE]
>  要求が少ないときは、スレッド プールの実際のスレッド数が最小値を下回る場合があります。  
  
 スレッド プールの最小値に達すると、追加のスレッドが作成されるか、いくつかのタスクが完了するまで待機状態になります。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降では、スループットを最適化するために、スレッド プールでワーカー スレッドの作成と破棄が行われます。スループットは、タスクの単位時間あたりの完了数として定義されます。 スレッドが少なすぎると使用可能なリソースが最適に使用されない可能性があり、スレッドが多すぎるとリソースの競合が増える可能性があります。  
  
> [!CAUTION]
>  アイドル スレッドの最小数は、<xref:System.Threading.ThreadPool.SetMinThreads%2A> メソッドを使用して増やすことができます。 ただし、これらの値を必要以上に大きくすると、パフォーマンスの問題が発生する可能性があります。 同時に開始するタスクの数が多すぎる場合は、すべてのタスクで処理速度が低下する可能性があります。 ほとんどの場合、スレッドを割り当てるためのスレッド プール独自のアルゴリズムを使用することでスレッド プールのパフォーマンスが向上します。  
  
## <a name="skipping-security-checks"></a>セキュリティ チェックのスキップ  
 スレッド プールでは、<xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> メソッドと <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> メソッドも使用できます。 これらのメソッドは、呼び出し元のスタックが、キューに配置されているタスクの実行時に行われるセキュリティ チェックと無関係であることが確認できる場合にのみ使用します。 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> と <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> はどちらも呼び出し元のスタックを取り込みます。このスタックは、スレッドがタスクの実行を開始するときにスレッド プールのスレッドのスタックにマージされます。 セキュリティ チェックが必要な場合は、そのスタック全体をチェックする必要があります。 チェックは安全性を提供しますが、パフォーマンスへの影響もあります。  
  
## <a name="using-the-thread-pool"></a>スレッド プールの使用  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降でスレッド プールを使用する場合は、[タスク並列ライブラリ (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md) を使用すると最も簡単です。 <xref:System.Threading.Tasks.Task> や <xref:System.Threading.Tasks.Task%601> などの並列ライブラリの型では、既定でスレッド プールのスレッドを使用してタスクが実行されます。 また、マネージ コードから <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> (またはアンマネージ コードから `CorQueueUserWorkItem`) を呼び出し、タスクを実行するメソッドを表す <xref:System.Threading.WaitCallback> デリゲートを渡すことによってスレッド プールを使用することもできます。 スレッド プールを使用するもう 1 つの方法として、待機操作の関連ワーク アイテムをキューに置く方法もあります。これには、<xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> メソッドを使用し、<xref:System.Threading.WaitHandle> を渡します。その WaitHandle がシグナル状態になるかタイムアウトになると、<xref:System.Threading.WaitOrTimerCallback> デリゲートによって表されるメソッドが呼び出されます。 スレッド プールのスレッドを使用してコールバック メソッドが呼び出されます。  
  
## <a name="threadpool-examples"></a>ThreadPool の例  
 このセクションのコード例では、<xref:System.Threading.Tasks.Task> クラス、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> メソッド、および <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> メソッドを使用したスレッド プールの例を示します。  
  
-   [タスク並列ライブラリを使用した非同期タスクの実行](#TaskParallelLibrary)  
  
-   [QueueUserWorkItem を使用した非同期のコード実行](#ExecuteCodeWithQUWI)  
  
-   [QueueUserWorkItem へのタスク データの供給](#TaskDataForQUWI)  
  
-   [RegisterWaitForSingleObject の使用](#RegisterWaitForSingleObject)  
  
<a name="TaskParallelLibrary"></a>   
### <a name="executing-asynchronous-tasks-with-the-task-parallel-library"></a>タスク並列ライブラリを使用した非同期タスクの実行  
 次の例では、<xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> メソッドを呼び出すことにより、<xref:System.Threading.Tasks.Task> オブジェクトを作成して使用する方法を示します。 <xref:System.Threading.Tasks.Task%601> クラスを使用して非同期タスクから値を返す方法の例については、「[方法: タスクから値を返す](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)」を参照してください。  
  
 [!code-csharp[System.Threading.Tasks.Task#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.task/cs/startnew.cs#01)]
 [!code-vb[System.Threading.Tasks.Task#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.task/vb/startnew.vb#01)]  
  
<a name="ExecuteCodeWithQUWI"></a>   
### <a name="executing-code-asynchronously-with-queueuserworkitem"></a>QueueUserWorkItem を使用した非同期のコード実行  
 次の例では、`ThreadProc` メソッドで表される単純なタスクを <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドを使用してキューに置きます。  
  
 [!code-cpp[Conceptual.ThreadPool#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.ThreadPool#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source1.cs#1)]
 [!code-vb[Conceptual.ThreadPool#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source1.vb#1)]  
  
<a name="TaskDataForQUWI"></a>   
### <a name="supplying-task-data-for-queueuserworkitem"></a>QueueUserWorkItem へのタスク データの供給  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドを使用してタスクをキューに置き、そのタスクにデータを与えるコード例を次に示します。  
  
 [!code-cpp[Conceptual.ThreadPool#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.ThreadPool#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source2.cs#2)]
 [!code-vb[Conceptual.ThreadPool#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source2.vb#2)]  
  
<a name="RegisterWaitForSingleObject"></a>   
### <a name="using-registerwaitforsingleobject"></a>RegisterWaitForSingleObject の使用  
 次の例では、スレッド処理のいくつかの機能について説明します。  
  
-   <xref:System.Threading.ThreadPool> スレッドで実行するタスクを、<xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A> メソッドを使用してキューに配置します。  
  
-   <xref:System.Threading.AutoResetEvent> を使用して、実行するようにタスクに通知します。 「[EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)」を参照してください。  
  
-   <xref:System.Threading.WaitOrTimerCallback> デリゲートを使用して、タイムアウトと通知の両方を処理します。  
  
-   <xref:System.Threading.RegisteredWaitHandle> を使用して、キューに置かれたタスクを取り消します。  
  
 [!code-cpp[Conceptual.ThreadPool#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.threadpool/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.ThreadPool#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.threadpool/cs/source3.cs#3)]
 [!code-vb[Conceptual.ThreadPool#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.threadpool/vb/source3.vb#3)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.Tasks.Task>  
 <xref:System.Threading.Tasks.Task%601>  
 [タスク並列ライブラリ (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [タスク並列ライブラリ (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [方法: タスクから値を返す](../../../docs/standard/parallel-programming/how-to-return-a-value-from-a-task.md)  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [スレッドおよびスレッド処理](../../../docs/standard/threading/threads-and-threading.md)  
 [非同期ファイル I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [タイマー](../../../docs/standard/threading/timers.md)
