---
title: "バリア (.NET Framework)"
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
helpviewer_keywords: synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a8111cc9f2798ff96be8b128f22a75d21b441178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="barrier-net-framework"></a>バリア (.NET Framework)
A*バリア*ユーザー定義の同期プリミティブを複数のスレッドを有効にする (と呼ばれる*参加者*) フェーズで、アルゴリズムに同時に動作します。 各参加要素は、コードのバリア ポイントに到達するまで実行されます。 バリアは、作業の 1 つのフェーズの終了を表します。 参加要素は、バリアに到達すると、すべての参加要素が同じバリアに到達するまでブロックされます。 すべての参加要素がバリアに到達した後、必要に応じて、フェーズ後の処理を呼び出すことができます。 フェーズ後の処理を使用すると、他のすべてのスレッドがブロックされた状態のまま 1 つのスレッドでアクションを実行できます。 アクションが実行された後、参加要素のブロックはすべて解除されます。  
  
 基本的なバリア パターンを次のコード スニペットに示します。  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 完全な例では、次を参照してください。[する方法: バリアの同時実行の操作を同期](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)です。  
  
## <a name="adding-and-removing-participants"></a>参加要素の追加と削除  
 <xref:System.Threading.Barrier> を作成するときは、参加要素の数を指定します。 また、参加要素は、いつでも動的に追加または削除できます。 たとえば、1 人の参加者は、その一部の問題を解決する場合は、結果、実行を停止し、そのスレッドを呼び出すを格納できます<xref:System.Threading.Barrier.RemoveParticipant%2A>バリアの参加要素の数をデクリメントします。 <xref:System.Threading.Barrier.AddParticipant%2A> を呼び出して参加要素を追加すると、戻り値によって現在のフェーズ数が示されます。この値は、追加した新しい参加要素の作業を初期化するのに役立つことがあります。  
  
## <a name="broken-barriers"></a>破損したバリア  
 いずれかの参加要素がバリアに到達できない場合、デッドロックが発生することがあります。 このようなデッドロックを避けるには、<xref:System.Threading.Barrier.SignalAndWait%2A> メソッドのオーバーロードを使用して、タイムアウト期間とキャンセル トークンを指定します。 すべての参加要素は、次のフェーズに進む前に、これらのオーバーロードから返されるブール値をチェックできます。  
  
## <a name="post-phase-exceptions"></a>フェーズ後の例外  
 フェーズ後のデリゲートから例外がスローされる場合、その例外は <xref:System.Threading.BarrierPostPhaseException> オブジェクトでラップされ、このオブジェクトがすべての参加要素に伝達されます。  
  
## <a name="barrier-versus-continuewhenall"></a>バリアと ContinueWhenAll  
 バリアは、スレッドで複数のフェーズをループ処理する場合に特に便利です。 コードで作業のフェーズが 1 つか 2 つしか必要ない場合は、次のような何らかの暗黙的な結合と共に <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトを使用することを検討してください。  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 詳細については、「[継続タスクを使用したタスクの連結](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [スレッド処理オブジェクトと機能](../../../docs/standard/threading/threading-objects-and-features.md)  
 [方法: バリアを使用して同時実行操作を同期する](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
