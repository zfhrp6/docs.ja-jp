---
title: "Determine if Any or All Elements in a Sequence Satisfy a Condition | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Determine if Any or All Elements in a Sequence Satisfy a Condition
<xref:System.Linq.Enumerable.All%2A> 演算子は、シーケンスのすべての要素が条件を満たす場合に `true` を返します。  
  
 <xref:System.Linq.Queryable.Any%2A> 演算子は、シーケンスの要素が 1 つでも条件を満たす場合に `true` を返します。  
  
## 使用例  
 次の例では、最低 1 件の注文がある顧客のシーケンスを返します。  `Where`\/`where` 句は、指定された `Customer` に `Order` がある場合に `true` に評価されます。  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## 使用例  
 次の Visual Basic コードでは、注文がない顧客のリストを調べ、リストに記載されている顧客に連絡先名があることを確認します。  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## 使用例  
 次の C\# コードでは、注文の `ShipCity` が "C" で始まる顧客のシーケンスを返します。  注文のない顧客も結果に含まれます。  \(<xref:System.Linq.Queryable.All%2A> 演算子はシーケンスが空の場合に `true` を返すように設計されています\)。注文のない顧客を削除してコンソールに出力するには、`Count` 演算子を使用します。  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## 参照  
 [Query Examples](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)