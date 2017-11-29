---
title: "集計クエリ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb1f26ec1fb8e5344946938206bb2418eeb6cd2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="aggregate-queries"></a>集計クエリ
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、`Average`、`Count`、`Max`、`Min`、および `Sum` の各集計演算子をサポートしています。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の集計演算子には、次の特性があります。  
  
-   集計クエリは直ちに実行されます。  
  
     詳細については、「[LINQ クエリの概要 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。  
  
-   通常、集計クエリはコレクションではなく 1 つの数値を返します。  
  
     詳細については、次を参照してください。[集計操作](http://msdn.microsoft.com/library/36d97c83-5de5-457d-971d-10a69365e7c4)です。  
  
-   匿名型に対して集計を呼び出すことはできません。  
  
 以下のトピックの例は、Northwind サンプル データベースから派生しています。 詳細については、次を参照してください。[サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [数値のシーケンスからの平均値を返す](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Average%2A> 演算子を使用する方法を示します。  
  
 [シーケンス内の要素の数をカウントします。](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <xref:System.Linq.Enumerable.Count%2A> 演算子を使用する方法を示します。  
  
 [数値のシーケンスの最大値を検索します。](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Max%2A> 演算子を使用する方法を示します。  
  
 [数値のシーケンスの最小値を検索します。](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Min%2A> 演算子を使用する方法を示します。  
  
 [数値のシーケンス値の合計を計算します。](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Sum%2A> 演算子を使用する方法を示します。  
  
## <a name="related-sections"></a>関連項目  
 [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 Visual Basic および C# の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリに関するトピックへのリンクを示します。  
  
 [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] での [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリの設計に関する概念について説明するトピックへのリンクを示します。  
  
 [LINQ クエリの概要 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] でクエリが動作するしくみについて説明します。
