---
title: "方法 : クエリで複合キーを処理する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2b0954d4659d1cc39cead0658fbd21dcd6dd12e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-composite-keys-in-queries"></a>方法 : クエリで複合キーを処理する
演算子によっては、引数を 1 つしか受け取らないものがあります。 1 つの演算子にデータベースの複数の列を含めるには、その組み合わせを表す匿名型を作成する必要があります。  
  
## <a name="example"></a>例  
 `GroupBy` 演算子を使用するクエリを次の例に示します。この演算子は、1 つの `key` 引数だけを受け取ることができます。  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>例  
 次の例に示すように、結合の場合も同様です。  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>参照  
 [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
