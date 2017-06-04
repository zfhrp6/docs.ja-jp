---
title: "NULL 比較 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ef88af8c-8dfe-4556-8b56-81df960a900b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# NULL 比較
データ ソースの `null` 値は不明な値を表します。  [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリでは、NULL 値をチェックして、必ず NULL でない有効なデータを持つ行に特定の計算または比較を行うようにすることができます。  ただし、CLR の NULL セマンティクスは、データ ソースの NULL セマンティクスとは異なる場合があります。  ほとんどのデータベースでは、3 値論理を使用して NULL 比較を処理します。  つまり、NULL 値との比較は `true` にも `false` にも評価されず、`unknown` に評価されます。  これは、多くの場合は ANSI NULL の実装ですが、そうでない場合もあります。  
  
 SQL Server の既定では、NULL \= NULL の比較は NULL 値を返します。  次の例では、`ShipDate` が NULL である行が結果セットから除外され、[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] ステートメントは 0 行を返します。  
  
```  
-- Find order details and orders with no ship date.  
SELECT h.SalesOrderID  
FROM Sales.SalesOrderHeader h  
JOIN Sales.SalesOrderDetail o ON o.SalesOrderID = h.SalesOrderID  
WHERE h.ShipDate IS Null  
```  
  
 これは、NULL \= NULL の比較が true を返す CLR の NULL セマンティクスとは大きく異なります。  
  
 次の LINQ クエリは CLR で表されますが、データ ソースで実行されます。  CLR セマンティクスがデータ ソースで使用される保証はないため、動作は予測できません。  
  
 [!code-csharp[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#joinonnull)]
 [!code-vb[DP L2E Conceptual Examples#JoinOnNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#joinonnull)]  
  
## キー セレクター  
 *キー セレクター*とは、要素からキーを抽出するために標準クエリ演算子で使用される関数です。  キー セレクター関数では、式を定数と比較できます。  式が NULL 定数と比較される場合、または 2 つの NULL 定数が比較される場合、CLR の NULL セマンティクスが使用されます。  データ ソースの NULL 値を持つ 2 つの列が比較される場合は、ストア NULL セマンティクスが使用されます。  キー セレクターは、<xref:System.Linq.Queryable.GroupBy%2A> など、グループ化や並べ替えの標準クエリ演算子で使用される場合が多く、クエリ結果の並べ替えやグループ化に使用するキーを選択できます。  
  
## NULL オブジェクトの NULL プロパティ  
 [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] では、NULL オブジェクトのプロパティは NULL です。  CLR で NULL オブジェクトのプロパティを参照しようとすると、<xref:System.NullReferenceException> が返されます。  LINQ クエリに NULL オブジェクトのプロパティが含まれている場合、動作の一貫性が失われることがあります。  
  
 たとえば、次のクエリでは、`NewProduct` へのキャストはコマンド ツリー レイヤーで行われ、`Introduced` プロパティが NULL になる可能性があります。  <xref:System.DateTime> の比較が true に評価されるように NULL 比較がデータベースで定義されている場合に、その行が含められます。  
  
 [!code-csharp[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#castresultsisnull)]
 [!code-vb[DP L2E Conceptual Examples#CastResultsIsNull](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#castresultsisnull)]  
  
## 集計関数に NULL コレクションを渡す  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] では、`IQueryable` をサポートするコレクションを集計関数に渡すと、データベースで集計演算が実行されます。  メモリで実行されたクエリとデータベースで実行されたクエリの結果は、異なる可能性があります。  メモリ内のクエリでは、一致するものがなければ 0 が返されます。  データベースでは、これと同じクエリから `null` が返されます。  `null` 値が LINQ 集計関数に渡されると、例外がスローされます。  `null` 値を受け入れるには、型、およびクエリ結果を受け取るその型のプロパティを Null 許容型にキャストします。  
  
## 参照  
 [LINQ to Entities クエリ内の式](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)