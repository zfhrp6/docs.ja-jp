---
title: "Barrier (.NET Framework) | Microsoft Docs"
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
  - "synchronization primitives, Barrier"
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Barrier (.NET Framework)
*バリア*とは、複数のスレッド \(*参加要素*と呼ばれます\) が段階的に 1 つのアルゴリズムで同時に動作できるようにするユーザー定義の同期プリミティブです。  各参加要素は、コードのバリア ポイントに到達するまで実行されます。  バリアは、作業の 1 つのフェーズの終了を表します。  参加要素は、バリアに到達すると、すべての参加要素が同じバリアに到達するまでブロックされます。  すべての参加要素がバリアに到達した後、必要に応じて、フェーズ後の処理を呼び出すことができます。  フェーズ後の処理を使用すると、他のすべてのスレッドがブロックされた状態のまま 1 つのスレッドでアクションを実行できます。  アクションが実行された後、参加要素のブロックはすべて解除されます。  
  
 基本的なバリア パターンを次のコード スニペットに示します。  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 コード例全体については、「[How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)」を参照してください。  
  
## 参加要素の追加と削除  
 <xref:System.Threading.Barrier> を作成するときは、参加要素の数を指定します。  また、参加要素は、いつでも動的に追加または削除できます。  たとえば、1 つの参加要素がその処理を終えた場合に、結果を保存し、そのスレッドの実行を停止してから、<xref:System.Threading.Barrier.RemoveParticipant%2A> を呼び出してバリアの参加要素の数を 1 つ減らすことができます。  <xref:System.Threading.Barrier.AddParticipant%2A> を呼び出して参加要素を追加すると、戻り値によって現在のフェーズ数が示されます。この値は、追加した新しい参加要素の作業を初期化するのに役立つことがあります。  
  
## 破損したバリア  
 いずれかの参加要素がバリアに到達できない場合、デッドロックが発生することがあります。  このようなデッドロックを避けるには、<xref:System.Threading.Barrier.SignalAndWait%2A> メソッドのオーバーロードを使用して、タイムアウト期間とキャンセル トークンを指定します。  すべての参加要素は、次のフェーズに進む前に、これらのオーバーロードから返されるブール値をチェックできます。  
  
## フェーズ後の例外  
 フェーズ後のデリゲートから例外がスローされる場合、その例外は <xref:System.Threading.BarrierPostPhaseException> オブジェクトでラップされ、このオブジェクトがすべての参加要素に伝達されます。  
  
## バリアと ContinueWhenAll  
 バリアは、スレッドで複数のフェーズをループ処理する場合に特に便利です。  コードで作業のフェーズが 1 つか 2 つしか必要ない場合は、次のような何らかの暗黙的な結合と共に <xref:System.Threading.Tasks.Task?displayProperty=fullName> オブジェクトを使用することを検討してください。  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 詳細については、「[Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)」を参照してください。  
  
## 参照  
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)   
 [How to: Synchronize Concurrent Operations with a Barrier](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)