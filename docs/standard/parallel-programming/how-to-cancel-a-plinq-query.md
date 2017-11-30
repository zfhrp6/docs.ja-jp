---
title: "方法: PLINQ クエリを取り消す"
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
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8031758462df45c030b8b75a3507f1bfb44bfd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-plinq-query"></a>方法: PLINQ クエリを取り消す
次の例では、PLINQ クエリを取り消すための 2 つの方法を示します。 最初の例では、データ移動のほとんどの場合で構成されているクエリをキャンセルする方法を示します。 2 番目の例では、ユーザー関数は計算コストが高いを含むクエリをキャンセルする方法を示します。  
  
> [!NOTE]
>  「マイ コードのみ」を有効にすると、Visual Studio は例外をスローする行で中断し、「で処理されない例外ユーザー コードです」というエラー メッセージを表示 このエラーは問題にはなりません。 F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。 Visual Studio の最初のエラーの処理は中断を防ぐために下にある [マイ コードのみ] チェック ボックスをオフにだけ**ツール、オプション、デバッグ、一般的な**します。  
>   
>  この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。 高速化の詳細については、次を参照してください。 [PLINQ で高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)です。  
  
## <a name="example"></a>例  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 PLINQ フレームワークは、1 つをロールバックできません<xref:System.OperationCanceledException>に、 <xref:System.AggregateException?displayProperty=nameWithType>;<xref:System.OperationCanceledException>個別の catch ブロックで処理する必要があります。 1 つまたは複数のユーザー デリゲート、OperationCanceledException(externalCT) をスローした場合 (外部を使用して、 <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) として定義されていないその他の例外、およびクエリ`AsParallel().WithCancellation(externalCT)`、PLINQ は、1 つを発行し、 <xref:System.OperationCanceledException> (externalCT) ではなく、<xref:System.AggregateException?displayProperty=nameWithType>. ただし、1 人のユーザーの委任をスロー、 <xref:System.OperationCanceledException>、別のデリゲートを別の種類の例外をスローし、両方の例外にロールバックされます、<xref:System.AggregateException>です。  
  
 取り消しの一般的なガイダンスは次のとおりです。  
  
1.  ユーザー デリゲートの取り消し処理を実行する場合は、外部について PLINQ を通知する必要があります<xref:System.Threading.CancellationToken>をスローし、 <xref:System.OperationCanceledException>(externalCT)。  
  
2.  取り消しが発生したその他の例外がスローされなかった場合は、し、処理、<xref:System.OperationCanceledException>ではなく、<xref:System.AggregateException>です。  
  
## <a name="example"></a>例  
 次の例では、ユーザー コードで計算コストが高い関数があるときに取り消しを処理する方法を示します。  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 ユーザー コードでキャンセルを処理する場合を使用する必要はありません<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>クエリ定義にします。 ただし、お勧めするこれを行うため<xref:System.Linq.ParallelEnumerable.WithCancellation%2A>クエリのパフォーマンスに影響を与えませんし、クエリ演算子と、ユーザー コードで処理するキャンセル可能になります。  
  
 システムの応答性を確保できるように、ことをお勧めミリ秒ごとに 1 回の周囲のキャンセルをチェックします。ただし、10 ミリ秒までの任意の期間の許容と見なされます。 この頻度では、コードのパフォーマンスに悪影響を与えるを必要はありません。  
  
 列挙子が破棄されると、コードがクエリ結果を反復処理する foreach (Visual Basic では各) For ループ外分割される場合など、クエリがキャンセルされるが例外はスローされません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.ParallelEnumerable>  
 [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [マネージ スレッドのキャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)
