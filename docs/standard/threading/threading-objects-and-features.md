---
title: "スレッド処理オブジェクトと機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a73e5c60a661c171e9e46e6307484cf5e0e6b80
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="threading-objects-and-features"></a>スレッド処理オブジェクトと機能
.NET Framework には、マルチスレッド アプリケーションの作成と管理に役立つ多くのオブジェクトが用意されています。 マネージ スレッドは、<xref:System.Threading.Thread> クラスによって表されます。 <xref:System.Threading.ThreadPool> クラスを使用すると、マルチスレッドのバックグラウンド タスクを簡単に作成し、管理できます。 <xref:System.ComponentModel.BackgroundWorker> クラスは、ユーザー インターフェイスと対話するタスクについてそれと同じことを実現します。 <xref:System.Threading.Timer> クラスは、指定された間隔でバックグラウンド タスクを実行します。  
  
 さらに、.NET Framework Version 2.0 で導入された <xref:System.Threading.Semaphore> クラスや <xref:System.Threading.EventWaitHandle> クラスなど、スレッドの活動を同期するクラスも数多くあります。 これらのクラスの機能の比較については、「[同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [マネージ スレッド プール](../../../docs/standard/threading/the-managed-thread-pool.md)  
 **ThreadPool** クラスについて説明します。このクラスを利用すると、開発者はスレッド管理を意識する必要なく、スレッドにタスクの実行を要求できます。  
  
 [タイマー](../../../docs/standard/threading/timers.md)  
 **Timer** を使用して、指定された時間に呼び出されるデリゲートを指定する方法を説明します。  
  
 [モニター](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 **Monitor** クラスを使用してメンバーへのアクセスを同期したり、独自の種類のスレッド管理を構築したりする方法を説明します。  
  
 [待機ハンドル](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle> クラスについて説明します。このクラスは、イベント待機ハンドル、ミューテックス、およびセマフォ用の抽象基底クラスで、複数の同期イベントを待機できるようにします。  
  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 通知を行ったり通知を待機したりすることによりスレッドの活動を同期するために使用するマネージ イベント待機ハンドルについて説明します。  
  
 [ミューテックス](../../../docs/standard/threading/mutexes.md)  
 使用する方法について説明します、<xref:System.Threading.Mutex>オブジェクトへのアクセスを同期するために、または独自の同期機構を構築します。  
  
 [インタロックされた操作](../../../docs/standard/threading/interlocked-operations.md)  
 <xref:System.Threading.Interlocked> クラスを使用して、値の増減と値の格納をアトミックな 1 回の操作で実行する方法を説明します。  
  
 [読み取り/書き込みロック](../../../docs/standard/threading/reader-writer-locks.md)  
 単一ライター/複数リーダーのセマンティクスを実装するロックを定義します。  
  
 [Semaphore と SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <xref:System.Threading.Semaphore> オブジェクトについて説明し、このオブジェクトを使用して、制限されたリソースへのアクセスを制御する方法を示します。  
  
 [同期プリミティブの概要](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 マネージ スレッドをロックおよび同期するために用意されている .NET Framework のクラスの機能を比較します。  
  
 [バリア](../../../docs/standard/threading/barrier.md)  
 段階的な操作におけるスレッドの調整のためのバリア パターンを実装する <xref:System.Threading.Barrier> オブジェクトについて説明します。  
  
 [SpinLock](../../../docs/standard/threading/spinlock.md)  
 特定の下位レベルのシナリオで Monitor クラスの代わりに軽量のプリミティブとして使用できる <xref:System.Threading.SpinLock> について説明します。  
  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 カーネル ベースの待機を開始する前にビジー スピンを実行する下位レベルの同期プリミティブである <xref:System.Threading.SpinWait> について説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.Threading.Thread>  
 **Thread** クラスのリファレンス ドキュメントです。このクラスは、アンマネージ コードから作成されたか、マネージ アプリケーションで作成されたかにかかわらず、マネージ スレッドを表します。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 ユーザー インターフェイスと対話し、ユーザー インターフェイス スレッドで生成されるイベントを介して通信するバックグラウンド タスクを有効にします。  
  
## <a name="related-sections"></a>関連項目  
 [非同期ファイル I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
 入力/出力操作が完了した場合にのみ非同期 I/O 完了ポートがスレッド プールを使用して処理を要求する方法について説明します。  
  
 [タスク並列ライブラリ (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降でマルチスレッド プログラミングのための推奨される方法について説明します。
