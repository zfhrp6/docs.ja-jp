---
title: "方法: ポーリングによりキャンセル要求を待機する"
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
helpviewer_keywords: cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f0e05e3f66d591a28d7e84d358934959764dab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>方法: ポーリングによりキャンセル要求を待機する
次の例では、ユーザー コードは、呼び出し元のスレッドから取り消しが要求されているかどうかを定期的にキャンセル トークンをポーリングすることを 1 つの方法を示します。 この例では、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>によって直接作成された非同期の操作に適用されますが、同様のパターン、<xref:System.Threading.ThreadPool?displayProperty=nameWithType>型または<xref:System.Threading.Thread?displayProperty=nameWithType>型です。  
  
## <a name="example"></a>例  
 ポーリングが必要、ブール型の値を読み取ることができる定期的にコードをループまたは再帰的な<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>プロパティです。 使用している場合、<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>の呼び出し元のスレッドが完了するタスクを待機している型にして、使用することができます、<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>プロパティを調べて、例外をスローするメソッド。 このメソッドを使用するは、要求への応答に正しい例外がスローされたことを確認します。 使用している場合、 <xref:System.Threading.Tasks.Task>、手動でスローよりはこのメソッドを呼び出す、<xref:System.OperationCanceledException>です。 例外をスローする必要はありませんし、先ほどプロパティをチェックし、プロパティは、メソッドから戻ることができるかどうか`true`です。  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 呼び出す<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>は非常に高速とループにかなりのオーバーヘッドを導入していません。  
  
 呼び出す場合<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>、のみを明示的にチェックする必要がある、<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>プロパティ例外をスローしてだけでなく、取り消しに応答を行うには、その他の作業がある場合。 この例では、コードは、実際にはプロパティにアクセスします 2 回を確認できます: 明示的なアクセス権とで再度、<xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>メソッドです。 読み取りの act、<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>プロパティは、1 つだけの揮発性アクセスごとの命令を読み取り、二重のアクセスは、パフォーマンスの観点から重要ではありません。 手動でをスローするのではなく、メソッドを呼び出して引き続き方が、<xref:System.OperationCanceledException>です。  
  
## <a name="see-also"></a>関連項目  
 [マネージ スレッドのキャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)
