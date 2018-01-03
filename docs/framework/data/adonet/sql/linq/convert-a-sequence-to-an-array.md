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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8739a939e3ad5ce8c3277120755fb72f77b3e175
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="convert-a-sequence-to-an-array"></a>方法 : シーケンスを配列に変換する
シーケンスから配列を作成するには、<xref:System.Linq.Enumerable.ToArray%2A> を使用します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Linq.Enumerable.ToArray%2A> を使用して、クエリを直ちに配列に評価し、3 番目の要素を取得します。  
  
 [!code-csharp[DLinqQueryExamples#44](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#44)]
 [!code-vb[DLinqQueryExamples#44](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#44)]  
  
## <a name="see-also"></a>参照  
 [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
