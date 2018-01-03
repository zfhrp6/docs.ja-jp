---
title: "2 つのシーケンスの連結"
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
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8bcb20f5d057c3b54e49e2fac81e9799ac42b1f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="concatenate-two-sequences"></a>2 つのシーケンスの連結
2 つのシーケンスを連結するには、<xref:System.Linq.Queryable.Concat%2A> 演算子を使用します。  
  
 <xref:System.Linq.Queryable.Concat%2A> 演算子は、受信側と引数の順序が同じである、順序付けされたマルチセットに対して定義されます。  
  
 SQL での順序付けは、結果が作成される前の最終段階です。 このため、<xref:System.Linq.Queryable.Concat%2A> 演算子は `UNION ALL` を使用して実装され、その引数の順序を保持しません。 結果内での順序付けを正しく行うには、結果の順序を明示的に指定する必要があります。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Linq.Queryable.Concat%2A> を使用して、すべての `Customer` と `Employee` の電話番号と FAX 番号のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>例  
 この例では、<xref:System.Linq.Queryable.Concat%2A> を使用して、すべての `Customer` と `Employee` の名前と電話番号のマッピングのシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>参照  
 [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [標準クエリ演算子の変換](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
