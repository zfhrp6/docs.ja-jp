---
title: "クエリの例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 137f8677-494c-4d49-95ce-c17742f2d01f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 91ff476ed8f6060975c6adc1fe01a6db9c199969
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="query-examples"></a>クエリの例
このセクションでは、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] および C# で一般的な [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] クエリの例を示して説明します。 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、「サンプル」セクションに多数のサンプル ソリューションが用意されています。 詳細については、次を参照してください。[サンプル](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)です。  
  
> [!IMPORTANT]
>  *db*のコード例でよく使用されて[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ドキュメント。 *db*のインスタンスであると見なされます、 *Northwind*から継承されるクラスが<xref:System.Data.Linq.DataContext>です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [集計クエリ](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A> などの使用方法について説明します。  
  
 [シーケンスの最初の要素の取得](../../../../../../docs/framework/data/adonet/sql/linq/return-the-first-element-in-a-sequence.md)  
 <xref:System.Linq.Enumerable.First%2A> の使用例を示して説明します。  
  
 [シーケンスの要素の取得またはスキップ](../../../../../../docs/framework/data/adonet/sql/linq/return-or-skip-elements-in-a-sequence.md)  
 <xref:System.Linq.Enumerable.Take%2A> および <xref:System.Linq.Enumerable.Skip%2A> の使用例を示して説明します。  
  
 [シーケンスの要素の並べ替え](../../../../../../docs/framework/data/adonet/sql/linq/sort-elements-in-a-sequence.md)  
 <xref:System.Linq.Enumerable.OrderBy%2A> の使用例を示して説明します。  
  
 [シーケンスの要素のグループ化](../../../../../../docs/framework/data/adonet/sql/linq/group-elements-in-a-sequence.md)  
 <xref:System.Linq.Enumerable.GroupBy%2A> の使用例を示して説明します。  
  
 [シーケンスからの重複する要素の削除](../../../../../../docs/framework/data/adonet/sql/linq/eliminate-duplicate-elements-from-a-sequence.md)  
 <xref:System.Linq.Enumerable.Distinct%2A> の使用例を示して説明します。  
  
 [シーケンスのすべての要素が条件を満たしているかどうかの確認](../../../../../../docs/framework/data/adonet/sql/linq/determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition.md)  
 <xref:System.Linq.Enumerable.All%2A> および <xref:System.Linq.Enumerable.Any%2A> の使用例を示して説明します。  
  
 [2 つのシーケンスの連結](../../../../../../docs/framework/data/adonet/sql/linq/concatenate-two-sequences.md)  
 <xref:System.Linq.Enumerable.Concat%2A> の使用例を示して説明します。  
  
 [2 つのシーケンスの差集合の取得](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-difference-between-two-sequences.md)  
 <xref:System.Linq.Enumerable.Except%2A> の使用例を示して説明します。  
  
 [2 つのシーケンスの積集合の取得](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-intersection-of-two-sequences.md)  
 <xref:System.Linq.Enumerable.Intersect%2A> の使用例を示して説明します。  
  
 [2 つのシーケンスの和集合の取得](../../../../../../docs/framework/data/adonet/sql/linq/return-the-set-union-of-two-sequences.md)  
 <xref:System.Linq.Enumerable.Union%2A> の使用例を示して説明します。  
  
 [方法 : シーケンスを配列に変換する](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-an-array.md)  
 <xref:System.Linq.Enumerable.ToArray%2A> の使用例を示して説明します。  
  
 [ジェネリック リストへのシーケンスの変換](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-sequence-to-a-generic-list.md)  
 <xref:System.Linq.Enumerable.ToList%2A> の使用例を示して説明します。  
  
 [汎用 IEnumerable への型の変換](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)  
 <xref:System.Linq.Enumerable.AsEnumerable%2A> の使用例を示して説明します。  
  
 [結合およびクロス積クエリの作成](../../../../../../docs/framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)  
 `from` 句、`where` 句、および `select` 句で外部キーを移動する方法の例を示して説明します。  
  
 [射影の作成](../../../../../../docs/framework/data/adonet/sql/linq/formulate-projections.md)  
 結合の例を示します`select`と他の機能 (たとえば、*匿名型*) クエリ射影を作成します。  
  
## <a name="related-sections"></a>関連項目  
 [標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)  
 標準クエリ演算子の概念について説明します。  
  
 [クエリの概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 クエリに関する概念が [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] でどのように使用されるかを説明します。  
  
 [プログラミング ガイド](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に関連するプログラミングの概念を説明するトピックへのポータルです。
