---
title: "Managed Threading Basics | Microsoft Docs"
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
  - "multiple threads"
  - "threading [.NET Framework], multiple threads"
  - "threading [.NET Framework], about threading"
  - "managed threading"
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Managed Threading Basics
このセクションの最初の 5 つのトピックでは、どのようなときにマネージ スレッド処理を使うかと、いくつかの基本的な機能について説明します。  追加機能を提供するクラスの詳細については、「[Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)」と「[Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)」を参照してください。  
  
 このセクションの残りのトピックでは、マネージ スレッド処理での Windows オペレーティング システムとのやり取りなど、より詳細な内容について説明します。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、マルチスレッド プログラムでのタスクとデータの並列化に使用できる API が Task Parallel Library および PLINQ に用意されています。  詳細については、「[Parallel Programming](../../../docs/standard/parallel-programming/index.md)」を参照してください。  
  
## このセクションの内容  
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)  
 マルチ スレッドの長所と短所について説明し、スレッドを作成したり、スレッド プールのスレッドを使用したりするシナリオの概要について説明します。  
  
 [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 さまざまなバージョンの .NET Framework のスレッドにおいて未処理の例外の動作について説明します。特にアプリケーションの終了を引き起こす状況について説明します。  
  
 [Synchronizing Data for Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 マルチ スレッドで使用されるクラスのデータを同期する方法について説明します。  
  
 [マネージ スレッドの状態](../../../docs/standard/threading/managed-thread-states.md)  
 基本的なスレッド状態と、スレッドが実行されているかどうかを検出する方法について説明します。  
  
 [Foreground and Background Threads](../../../docs/standard/threading/foreground-and-background-threads.md)  
 フォアグラウンド スレッドとバックグラウンド スレッドの違いについて説明します。  
  
 [Managed and Unmanaged Threading in Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 マネージ スレッド処理とアンマネージ スレッド処理との関係、Windows のスレッド処理 API に対応するマネージ スレッドのメソッド、および COM アパートメントとマネージ スレッドとのやり取りについて説明します。  
  
 [Thread.Suspend, Garbage Collection, and Safe Points](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 スレッドの中断とガベージ コレクションについて説明します。  
  
 [Thread Local Storage: Thread\-Relative Static Fields and Data Slots](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 スレッド相対のストレージ機構について説明します。  
  
 [Cancellation in Managed Threads](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 キャンセル トークンを使用して非同期または長時間にわたる同期操作を取り消す方法について説明します。  
  
## 関連項目  
 <xref:System.Threading.Thread>  
 **Thread** クラスのリファレンス ドキュメントです。このクラスは、アンマネージ コードから作成されたか、マネージ アプリケーションで作成されたかにかかわらず、マネージ スレッドを表します。  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 ユーザー インターフェイス オブジェクトと組み合わせてマルチスレッドを実装する安全な方法を示します。  
  
## 関連項目  
 [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 複数のスレッドのアクティビティを同期するために使用するマネージ クラスについて説明します。  
  
 [Managed Threading Best Practices](../../../docs/standard/threading/managed-threading-best-practices.md)  
 マルチスレッド処理に関連する一般的な問題、およびその問題を回避する方法について説明します。  
  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)  
 非同期のマルチスレッド .NET Framework アプリケーションを簡単に作成できるようにするタスク並列ライブラリおよび PLINQ について説明します。