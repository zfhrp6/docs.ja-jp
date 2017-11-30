---
title: "方法: バリアを使用して同時実行操作を同期する"
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
helpviewer_keywords: Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b2e32fe3cec30a4da7467447aee625dfe7e379b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>方法: バリアを使用して同時実行操作を同期する
次の例を使用して同時実行タスクを同期する方法を示しています、<xref:System.Threading.Barrier>です。  
  
## <a name="example"></a>例  
 次のプログラムの目的がイテレーション (または段階) の数をカウントするで必要と各検索 を 2 つのスレッドのソリューションの半分同じ段階でランダム化アルゴリズムを使用して、単語をシャッフルします。 各スレッドには、単語がシャッフル後、barrier のフェーズ後の操作は完全な文が正しい単語の順序で表示されたかどうかに表示する 2 つの結果を比較します。  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A<xref:System.Threading.Barrier>オブジェクトにより、すべてのタスクがバリアに到達するまで続行できなく並列操作の個々 のタスクです。 並列操作が、段階的で出現し、各フェーズのタスク間の同期が必要と便利です。 この例では、操作を 2 つのフェーズがあります。 最初のフェーズでは、各タスクは、データを含むバッファーの場合は、そのセクションを設定します。 各タスクでは、そのセクションの入力が完了したら、タスクは、操作を続行する準備ができたバリアし、待機を通知します。 すべてのタスクは、バリアに通知が、ブロックが解除され、2 番目のフェーズが開始されます。 バリアは、2 番目のフェーズでは、各タスクは、このポイントに生成されたすべてのデータへのアクセスである必要があるために必要があります。 バリア、せず、最初のタスクを完了するが入力されていないまだ他のタスクでバッファーからの読み込みしようとする可能性があります。 この方法で各フェーズの任意の数を同期することができます。  
  
## <a name="see-also"></a>関連項目  
 [並列プログラミングのデータ構造](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
