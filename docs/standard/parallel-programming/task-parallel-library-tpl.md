---
title: "Task Parallel Library (TPL) | Microsoft Docs"
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
  - ".NET, concurrency in"
  - ".NET, parallel programming in"
  - "Parallel Programming"
ms.assetid: b8f99f43-9104-45fd-9bff-385a20488a23
caps.latest.revision: 37
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 37
---
# Task Parallel Library (TPL)
タスク並列ライブラリ \(TPL: Task Parallel Library\) は、<xref:System.Threading?displayProperty=fullName> 名前空間および <xref:System.Threading.Tasks?displayProperty=fullName> 名前空間におけるパブリック型と API のセットです。  TPL の目的は、アプリケーションに並列処理と同時実行を追加するプロセスを簡略化して、開発者の生産性を高めることです。  TPL は、使用可能なすべてのプロセッサを最も効率的に使用するように、同時実行の程度を動的に拡大します。  さらに TPL は、作業のパーティション分割、<xref:System.Threading.ThreadPool> 上のスレッドのスケジュール、キャンセルのサポート、状態管理、および他の低水準の詳細を処理します。  TPL を使用すると、コードのパフォーマンスが大幅に向上し、目的を達成するためのプログラミング作業に集中できます。  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降では、マルチスレッド コードおよび並列コードを作成するときに TPL をお勧めします。  ただし、すべてのコードが並列化に適している訳ではありません。ループの各反復処理で少量の作業のみを実行する場合、または多数の反復処理のために実行しない場合、並列化のオーバーヘッドによってコードの実行が遅くなる可能性があります。  さらに、マルチスレッド コードのような並列化によって、プログラムの実行がより複雑になります。  TPL はマルチスレッドのシナリオを簡略化しますが、たとえばロック、デッドロックおよび競合状態のスレッド処理の基本的な概念を理解し、TPL を効率的に使用することをお勧めします。  
  
## 関連トピック  
  
|||  
|-|-|  
|Title|説明|  
|[Data Parallelism](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)|並列の `for` ループおよび `foreach` ループ \(Visual Basic では `For` および `For Each`\) を作成する方法について説明します。|  
|[Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)|<xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=fullName> を使用して暗黙的にタスクを作成および実行する方法、または <xref:System.Threading.Tasks.Task> オブジェクトを直接使用して明示的にタスクを作成および実行する方法について説明します。|  
|[データフロー](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)|相互に非同期通信を行う必要がある複数の操作を処理する場合、またはデータが使用可能になったときにデータを処理する場合に、TPL データ フロー ライブラリのデータ フロー コンポーネントを使用する方法について説明します。|  
|[Using TPL with Other Asynchronous Patterns](../../../docs/standard/parallel-programming/using-tpl-with-other-asynchronous-patterns.md)|TPL と他の非同期パターンを .NET で使用する方法について説明します。|  
|[Potential Pitfalls in Data and Task Parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)|一般的な落とし穴とその回避方法について説明します。|  
|[Parallel LINQ \(PLINQ\)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|LINQ クエリでデータの並列化を達成する方法について説明します。|  
|[Parallel Programming](../../../docs/standard/parallel-programming/index.md)|.NET 並列プログラミングのトップ レベル ノード。|  
  
## 参照  
 [Samples for Parallel Programming with the .NET Framework \(.NET Framework による並列プログラミングのサンプル\)](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)