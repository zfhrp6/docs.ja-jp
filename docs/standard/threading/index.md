---
title: "Managed Threading | Microsoft Docs"
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
  - "threading [.NET Framework], about threading"
  - "managed threading"
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Managed Threading
アプリケーションを開発する場合、プロセッサがシングルまたはマルチのいずれの場合でも、アプリケーションにユーザーとの迅速な対話を提供する必要があります。これはアプリケーションがほかの処理の実行中であっても同じことです。  アプリケーションによるユーザーへの迅速な応答を維持すると同時に、ユーザー イベントの合間やその処理中にプロセッサを使用する最も強力な方法は、複数の実行スレッドを使用することです。  ここでは、スレッド処理の基本概念について、マネージ スレッド処理の概念と使用方法を中心に説明します。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、<xref:System.Threading.Tasks.Parallel?displayProperty=fullName> クラスと <xref:System.Threading.Tasks.Task?displayProperty=fullName> クラス、[Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)、<xref:System.Collections.Concurrent?displayProperty=fullName> 名前空間の新しい同時実行コレクション クラス、およびスレッドではなくタスクの概念に基づく新しいプログラミング モデルによって、マルチスレッド プログラミングが大幅に簡略化されます。  詳細については、「[Parallel Programming](../../../docs/standard/parallel-programming/index.md)」を参照してください。  
  
## このセクションの内容  
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)  
 マネージ スレッド処理の概要と、マルチ スレッドをどのようなときに使用するかについて説明します。  
  
 [Using Threads and Threading](../../../docs/standard/threading/using-threads-and-threading.md)  
 スレッドの作成、開始、一時停止、再開、および中止について説明します。  
  
 [Managed Threading Best Practices](../../../docs/standard/threading/managed-threading-best-practices.md)  
 同期のレベル、デッドロックと競合状態の回避方法、シングル プロセッサのコンピューターとマルチ プロセッサのコンピューターの問題など、スレッド処理の各種の注意点について説明します。  
  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)  
 スレッドの動作や、別のスレッドによってアクセスされるオブジェクトのデータを同期するために使用するマネージ クラスについて説明し、スレッド プールのスレッドの概要を示します。  
  
## 関連項目  
 <xref:System.Threading>  
 マネージ スレッドを使用したり同期したりするためのクラスを含みます。  
  
 <xref:System.Collections.Concurrent>  
 複数のスレッドで使用する安全なコレクション クラスを含みます。  
  
 <xref:System.Threading.Tasks>  
 同時処理タスクを作成およびスケジュールするためのクラスを含みます。  
  
## 関連項目  
 [アプリケーション ドメイン](../../../docs/framework/app-domains/application-domains.md)  
 アプリケーション ドメインの概要と共通言語基盤によるアプリケーション ドメインの使用について説明します。  
  
 [非同期ファイル I\/O](../../../docs/standard/io/非同期ファイル-i-o.md)  
 非同期 I\/O のパフォーマンス上の利点と基本的な操作について説明します。  
  
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 非同期プログラミングの概要を説明します。  
  
 [Calling Synchronous Methods Asynchronously](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 デリゲートの組み込み機能を使用してスレッド プールのスレッドでメソッドを呼び出す方法を示します。  
  
 [Parallel Programming](../../../docs/standard/parallel-programming/index.md)  
 アプリケーションで複数のスレッドを簡単に使用できるようにする並列プログラミング ライブラリについて説明します。  
  
 [Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 複数のプロセッサを利用するために、クエリを並列で実行するシステムについて説明します。