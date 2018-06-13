---
title: 集計クエリ
ms.date: 03/30/2017
ms.assetid: 13ec5580-05ce-4a1f-9d3d-8660be7891a2
ms.openlocfilehash: e4d5e0a9dc1ffb0bf1857fee788d46947f3901d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358844"
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
 [一連の数値の平均値の取得](../../../../../../docs/framework/data/adonet/sql/linq/return-the-average-value-from-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Average%2A> 演算子を使用する方法を示します。  
  
 [シーケンス内の要素数のカウント](../../../../../../docs/framework/data/adonet/sql/linq/count-the-number-of-elements-in-a-sequence.md)  
 <xref:System.Linq.Enumerable.Count%2A> 演算子を使用する方法を示します。  
  
 [一連の数値の中の最大値の検出](../../../../../../docs/framework/data/adonet/sql/linq/find-the-maximum-value-in-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Max%2A> 演算子を使用する方法を示します。  
  
 [一連の数値の中の最小値の検出](../../../../../../docs/framework/data/adonet/sql/linq/find-the-minimum-value-in-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Min%2A> 演算子を使用する方法を示します。  
  
 [数値のシーケンスの合計の計算](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)  
 <xref:System.Linq.Enumerable.Sum%2A> 演算子を使用する方法を示します。  
  
## <a name="related-sections"></a>関連項目  
 [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 Visual Basic および C# の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリに関するトピックへのリンクを示します。  
  
 [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] での [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリの設計に関する概念について説明するトピックへのリンクを示します。  
  
 [LINQ クエリの概要 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] でクエリが動作するしくみについて説明します。
