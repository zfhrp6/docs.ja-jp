---
title: "Cross-Table Queries (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Cross-Table Queries (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、1 つのテーブルを対象とするクエリに加え、複数のテーブルを対象とするクエリを実行できます。このようなクエリは、*統合*を使用して実現されます。  結合とは、あるデータ ソース内のオブジェクトを、他方のデータ ソース内で共通の属性 \(たとえば製品や連絡先 ID\) を持つオブジェクトと関連付けることです。  オブジェクト指向プログラミングでは、それぞれのオブジェクトが別のオブジェクトを参照するメンバーを持つため、オブジェクト間のリレーションシップを比較的簡単にナビゲートできます。ただし、外部データベース テーブル内でのリレーションシップは、これほど簡単にはナビゲートできません。  データベース テーブルには、組み込みのリレーションシップがありません。このようなケースでは、結合操作を使用して、互いのソースの要素を対応付けることができます。  たとえば、製品情報と売上情報が 2 つのテーブルに格納されている場合、結合操作を使用して、同じ販売注文の売上情報と製品を対応付けることができます。  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] フレームワークには、<xref:System.Linq.Enumerable.Join%2A> と <xref:System.Linq.Enumerable.GroupJoin%2A> の 2 つの結合演算子が用意されています。これらの演算子は、キーが等しいときだけ 2 つのデータ ソースを対応付ける結合方法である*等結合*を実行します   \(これに対し、[!INCLUDE[tsql](../../../../includes/tsql-md.md)] では、`equals` 以外に `less than` 演算子などの結合演算子がサポートされます\)。  
  
 リレーショナル データベース用語では、<xref:System.Linq.Enumerable.Join%2A> は内部結合を実行します。  内部結合とは、対応するデータセット内で一致するオブジェクトがあるオブジェクトのみが返される結合です。  
  
 リレーショナル データベース用語で <xref:System.Linq.Enumerable.GroupJoin%2A> 演算子に相当するものはありません。この演算子は、内部結合と左外部結合のスーパーセットを実装します。左外部結合とは、関連のある要素が 2 つ目のコレクションに存在しない場合でも 1 つ目 \(左側\) のコレクションの各要素を返す結合です。  
  
 結合の詳細については、「[Join Operations](../../../../ocs/visual-basic/programming-guide/concepts/linq/join-operations.md)」を参照してください。  
  
## 例  
 次の例では、AdventureWorks サンプル データベースの `SalesOrderHeader` テーブルと `SalesOrderDetail` テーブルを従来の方法で結合し、8 月以降のオンラインでの注文を取得します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## 参照  
 [Querying DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [Single\-Table Queries](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)   
 [Querying Typed DataSets](../../../../docs/framework/data/adonet/querying-typed-datasets.md)   
 [Join Operations](../../../../ocs/visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [LINQ to DataSet Examples](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)