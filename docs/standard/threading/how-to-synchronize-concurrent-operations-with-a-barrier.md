---
title: "How to: Synchronize Concurrent Operations with a Barrier | Microsoft Docs"
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
  - "Barrier, how to use"
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# How to: Synchronize Concurrent Operations with a Barrier
以下の例では、<xref:System.Threading.Barrier> を使用して同時実行タスクを同期する方法を示します。  
  
## 使用例  
 以下のプログラムの目的は、ランダム化アルゴリズムを使用して単語を再シャッフルすることにより、同じフェーズで 2 つのスレッドがそれぞれソリューションの半分を探すために必要なイテレーション \(またはフェーズ\) の数をカウントすることです。  各スレッドで単語がシャッフルされた後、バリアのフェーズ後の操作によって、文中の単語の表示順序が正しいかどうかを確認するために 2 つの結果が比較されます。  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <xref:System.Threading.Barrier> は、すべてのタスクがバリアに到達するまで、並行操作の個々のタスクが続行されないようにするオブジェクトです。  これは、1 つの並行操作が複数のフェーズで行われ、各フェーズでタスク間の同期が必要となる場合に便利です。  この例では、操作に 2 つのフェーズがあります。  最初のフェーズでは、各タスクはバッファーの対応する領域をデータで埋めます。  各タスクは、その領域を埋め終わると、続行できる状態になったことをバリアに通知し、待機します。  すべてのタスクがバリアに通知すると、ブロックが解除され、2 番目のフェーズが開始されます。  2 番目のフェーズでは、各タスクからすべてのデータにアクセスするため、その時点までにすべてのデータが生成されている必要があります。バリアが必要になるのはこのためです。  バリアがないと、最初に完了したタスクが、他のタスクがまだ埋め終わっていないバッファーから読み取ろうとする可能性があります。  同様の方法で、任意の数のフェーズを同期できます。  
  
## 参照  
 [Data Structures for Parallel Programming](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)