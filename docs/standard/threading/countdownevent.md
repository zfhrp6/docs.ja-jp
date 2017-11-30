---
title: CountdownEvent
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
helpviewer_keywords: synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f953f6477abf1f4e0d6aaf79e67005172ff1144
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>待機中のスレッドのブロックが解除された後に同期プリミティブの通知回数だけです。 <xref:System.Threading.CountdownEvent>シナリオではそれ以外の場合があるを使用するよう設計されていますが、<xref:System.Threading.ManualResetEvent>または<xref:System.Threading.ManualResetEventSlim>と手動でイベントを通知する前に、変数をデクリメントします。 たとえば、分岐および結合のシナリオでのみ作成できます、 <xref:System.Threading.CountdownEvent> 5 のシグナルのカウントを持つと 5 つの作業項目、スレッドの開始をプールし、作業項目の各呼び出しがある<xref:System.Threading.CountdownEvent.Signal%2A>完了時にします。 各呼び出し<xref:System.Threading.CountdownEvent.Signal%2A>信号カウントを 1 だけデクリメントします。 メイン スレッドへの呼び出しで<xref:System.Threading.CountdownEvent.Wait%2A>シグナル カウントがゼロになるまでブロックします。  
  
> [!NOTE]
>  従来の .NET Framework の同期 Api と対話する必要はありませんコード、使用を検討して<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>オブジェクトまたは<xref:System.Threading.Tasks.Parallel.Invoke%2A>分岐と結合の並列処理の表現をさらに簡単なアプローチのメソッドです。  
  
 <xref:System.Threading.CountdownEvent>これらの追加機能があります。  
  
-   キャンセル トークンを使用して、待機操作をキャンセルできます。  
  
-   インスタンスが作成された後、その信号カウントをインクリメントできます。  
  
-   インスタンスが後に再利用できる<xref:System.Threading.CountdownEvent.Wait%2A>呼び出しで返されるが、<xref:System.Threading.CountdownEvent.Reset%2A>メソッドです。  
  
-   インスタンスを公開、<xref:System.Threading.WaitHandle>他の .NET Framework の同期 Api と統合するためなど<xref:System.Threading.WaitHandle.WaitAll%2A>です。  
  
## <a name="basic-usage"></a>基本的な使用方法  
 次の例で使用する方法、<xref:System.Threading.CountdownEvent>で<xref:System.Threading.ThreadPool>作業項目です。  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>キャンセルを CountdownEvent  
 次の例での待機操作をキャンセルする方法を示しています。<xref:System.Threading.CountdownEvent>キャンセル トークンを使用しています。 基本的なパターンが統一されたキャンセルで導入されたのモデルを採用[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]です。 詳細については、次を参照してください。[マネージ スレッドのキャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)です。  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 待ち操作がそのシグナル状態のスレッドをキャンセルしていないことに注意してください。 通常、取り消しは、論理操作に適用され、待機を同期しているすべての作業項目と同様に、イベントで待機していることを含めることができます。 この例では、各作業項目は、同じキャンセル トークンのコピーには、キャンセル要求に応答できるようにします。  
  
## <a name="see-also"></a>関連項目  
 [EventWaitHandle、AutoResetEvent、CountdownEvent、ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
