---
title: "Compute the Sum of Values in a Numeric Sequence | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Compute the Sum of Values in a Numeric Sequence
<xref:System.Linq.Enumerable.Sum%2A> 演算子を使用すると、シーケンス内の数値の合計を計算できます。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の `Sum` 演算子には、次の特性があります。  
  
-   標準クエリ演算子の集計演算子 `Sum` では、空のシーケンスや null のみを含むシーケンスはゼロに評価されます。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、SQL のセマンティクスは維持されます。  したがって、空のシーケンスまたは null のみを含むシーケンスについては、`Sum` 演算子は 0 ではなく null に評価します。  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] での集計には、中間結果に対する SQL の制限が適用されます。  64 ビットの結果を使って 32 ビット整数の合計値を計算することはできません。[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] による `Sum` の変換で、オーバーフローが発生する可能性があります。  これは、標準クエリ演算子の実装で、対応するメモリ内シーケンスでオーバーフローが発生しない場合でも起こる可能性があります。  
  
## 使用例  
 `Order` テーブルに含まれるすべての注文の運賃の合計を求める例を次に示します。  
  
 Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`64942.6900` です。  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## 使用例  
 すべての製品の受注単位の合計を求める例を次に示します。  
  
 Northwind サンプル データベースに対してこのクエリを実行した場合の出力は、`780` です。  
  
 `Sum` には `short` 型のオーバーロードがないため、short 型 \(`UnitsOnOrder` など\) をキャストする必要があります。  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## 参照  
 [Aggregate Queries](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)   
 [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)