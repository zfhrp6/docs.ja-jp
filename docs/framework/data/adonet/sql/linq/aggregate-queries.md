---
title: "Aggregate Queries | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Aggregate Queries
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、`Average`、`Count`、`Max`、`Min`、および `Sum` の各集計演算子をサポートしています。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の集計演算子には、次の特性があります。  
  
-   集計クエリは直ちに実行されます。  
  
     詳細については、「[Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)」を参照してください。  
  
-   通常、集計クエリはコレクションではなく 1 つの数値を返します。  
  
     詳細については、「[Aggregation Operations](../../../../../../ocs/visual-basic/programming-guide/concepts/linq/aggregation-operations.md)」を参照してください。  
  
-   匿名型に対して集計を呼び出すことはできません。  
  
 以下のトピックの例は、Northwind サンプル データベースから派生しています。  詳細については、「[Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。  
  
## このセクションの内容  
 [Return the Average Value From a Numeric Sequence](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Average%2A> 演算子を使用する方法を示します。  
  
 [Count the Number of Elements in a Sequence](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <xref:System.Linq.Enumerable.Count%2A> 演算子を使用する方法を示します。  
  
 [Find the Maximum Value in a Numeric Sequence](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Max%2A> 演算子を使用する方法を示します。  
  
 [Find the Minimum Value in a Numeric Sequence](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Min%2A> 演算子を使用する方法を示します。  
  
 [Compute the Sum of Values in a Numeric Sequence](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Sum%2A> 演算子を使用する方法を示します。  
  
## 関連項目  
 [Query Examples](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 Visual Basic および C\# の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリに関するトピックへのリンクを示します。  
  
 [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] での [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] クエリの設計に関する概念について説明するトピックへのリンクを示します。  
  
 [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)  
 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] でクエリが動作するしくみについて説明します。