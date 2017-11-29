---
title: "複数テーブルにまたがるクエリ (LINQ to DataSet)"
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
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d0b829840257dc2b3b4bbf0b8c3a294a77060e2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cross-table-queries-linq-to-dataset"></a>複数テーブルにまたがるクエリ (LINQ to DataSet)
[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、1 つのテーブルを対象とするクエリに加え、複数テーブルにまたがるクエリを実行できます。 使用してこれは、*結合*です。 結合とは、あるデータ ソース内のオブジェクトを、他方のデータ ソース内で共通の属性 (たとえば製品や連絡先 ID) を持つオブジェクトと関連付けることです。 オブジェクト指向プログラミングでは、それぞれのオブジェクトは別のオブジェクトを参照するメンバーを持つため、オブジェクト間のリレーションシップのナビゲーションは比較的簡単です。 ただし、外部データベース テーブル内でのリレーションシップのナビゲーションは単純ではありません。 データベース テーブルは、組み込みのリレーションシップを持ちません。 このようなケースでは、結合操作を使用して、互いのソースの要素を対応付けることができます。 たとえば、製品情報と売上情報が 2 つのテーブルに格納されている場合、結合操作を使用して、同じ販売注文の売上情報と製品を対応付けることができます。  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]フレームワークは、2 つの結合演算子は、<xref:System.Linq.Enumerable.Join%2A>と<xref:System.Linq.Enumerable.GroupJoin%2A>です。 これらの演算子実行*等結合*: つまり、2 つのデータの一致の結合ソースをキーが等しい場合のみです。 (これに対し、[!INCLUDE[tsql](../../../../includes/tsql-md.md)] では、`equals` 以外に `less than` 演算子などの結合演算子がサポートされます)。  
  
 リレーショナル データベース用語では、<xref:System.Linq.Enumerable.Join%2A> は内部結合を実行します。 内部結合とは、対応するデータセット内で一致するオブジェクトがあるオブジェクトのみが返される結合です。  
  
 <xref:System.Linq.Enumerable.GroupJoin%2A>演算子リレーショナル データベース用語で同等の軸がありません。 内部結合、左外部結合のスーパー セットを実装しています。 2 番目のコレクションでは相関関係を持つ要素があるない場合でも、左外部結合を最初の (左側) のコレクションの各要素を返す結合であります。  
  
 結合の詳細については、次を参照してください。[の結合操作](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)です。  
  
## <a name="example"></a>例  
 次の例では、AdventureWorks サンプル データベースの `SalesOrderHeader` テーブルと `SalesOrderDetail` テーブルを従来の方法で結合し、8 月以降のオンラインでの注文を取得します。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a>関連項目  
 [Dataset のクエリ](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [単一テーブルのクエリ](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 [型指定されたデータセットのクエリを実行します。](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [結合演算](http://msdn.microsoft.com/library/442d176d-028c-4beb-8d22-407d4ef89107)  
 [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
