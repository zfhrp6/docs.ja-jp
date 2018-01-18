---
title: "方法 : シーケンスを配列に変換する"
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
ms.assetid: bf0af444-890d-43e2-aeca-98589dd74ddf
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c4846a45b0a49de102cab05857a69476680198a0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="convert-a-sequence-to-an-array"></a>方法 : シーケンスを配列に変換する
シーケンスから配列を作成するには、<xref:System.Linq.Enumerable.ToArray%2A> を使用します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Linq.Enumerable.ToArray%2A> を使用して、クエリを直ちに配列に評価し、3 番目の要素を取得します。  
  
 [!code-csharp[DLinqQueryExamples#44](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#44)]
 [!code-vb[DLinqQueryExamples#44](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#44)]  
  
## <a name="see-also"></a>参照  
 [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
