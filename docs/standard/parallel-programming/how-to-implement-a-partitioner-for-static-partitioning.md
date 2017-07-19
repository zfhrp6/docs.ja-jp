---
title: "How to: Implement a Partitioner for Static Partitioning | Microsoft Docs"
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
  - "tasks, how to create a static partitioner"
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# How to: Implement a Partitioner for Static Partitioning
静的パーティション分割を実行する、PLINQ 用の簡単なカスタム パーティショナーを実装する方法の 1 つを次の例に示します。  このパーティショナーは動的パーティションをサポートしないため、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> からは使用できません。  このパーティショナーは、各要素により処理時間が増大するデータ ソースでは、既定の範囲パーティショナーよりも速度が向上する場合があります。  
  
## 使用例  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 この例のパーティションは、各要素により処理時間が直線的に増加するという前提に基づいています。  実際には、この方法で処理時間を予測するのは困難な場合があります。  特定のデータ ソースで静的パーティショナーを使用する場合、ソース用にパーティション分割式を最適化するか、負荷分散ロジックを追加するか、または「[How to: Implement Dynamic Partitions](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)」に示すチャンク パーティション分割方法を使用できます。  
  
## 参照  
 [Custom Partitioners for PLINQ and TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)