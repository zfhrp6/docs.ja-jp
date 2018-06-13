---
title: '方法: PLINQ クエリのパフォーマンスを測定する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c662c442f7f2cea23e1afe131704585e7a9bca7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584606"
---
# <a name="how-to-measure-plinq-query-performance"></a>方法: PLINQ クエリのパフォーマンスを測定する
この例では、<xref:System.Diagnostics.Stopwatch> クラスを使用して、PLINQ クエリの実行にかかる時間を測定する方法を示します。  
  
## <a name="example"></a>例  
 この例では、空の `foreach` ループ (Visual Basic では `For Each`) を使用して、クエリの実行にかかる時間を計測します。 実際のコードでは、ループには通常、クエリの合計実行時間への加算という追加の処理手順が含まれます。 ループでクエリの実行が開始されるため、ループの直前までストップウォッチが開始されないことに注目してください。 さらにきめ細かい測定値が必要な場合は、`ElapsedMilliseconds` ではなく、`ElapsedTicks` プロパティを使用することができます。  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 合計実行時間は、クエリの実装を試すときに便利なメトリックですが、これだけでは全貌が明らかにならない場合もあります。 クエリ スレッド同士およびクエリ スレッドと他の実行中のプロセスとのやり取りをより深くより豊かに視覚化するには、同時実行ビジュアライザーを使用します。 詳細については、「[同時実行ビジュアライザー](/visualstudio/profiling/concurrency-visualizer)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
