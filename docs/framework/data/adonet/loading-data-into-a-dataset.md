---
title: "DataSet へのデータの読み込み"
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
ms.assetid: a53e5dc1-9669-49d4-828d-efa633237066
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: afb05055d67a4430909a657fc0ee90c97d3ebfb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="loading-data-into-a-dataset"></a>DataSet へのデータの読み込み
<xref:System.Data.DataSet> で [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] オブジェクトに対するクエリを実行するには、まずデータセットにデータを読み込んでおく必要があります。 <xref:System.Data.DataSet> には、複数の方法でデータを読み込むことができます。 たとえば、使用することができます[!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]データベース クエリを読み込むには結果を<xref:System.Data.DataSet>です。 詳細については、「[LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)」を参照してください。  
  
 データを <xref:System.Data.DataSet> に読み込む一般的な方法としては、他にも <xref:System.Data.Common.DataAdapter> クラスを使用してデータベースからデータを取得する方法もあります。 この例を次に示します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Data.Common.DataAdapter> を使用して、2002 年度の売上情報を照会するクエリを AdventureWorks データベースに対して実行し、その結果を <xref:System.Data.DataSet> に読み込んでいます。 <xref:System.Data.DataSet> への読み込みが完了した後、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] を使用して、そのデータセットに対するクエリを作成できます。 `FillDataSet`でクエリの例でこの例ではメソッドが使用される[LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)です。 詳細については、次を参照してください。[データセットのクエリを実行する](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)です。  
  
 [!code-csharp[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#filldataset)]
 [!code-vb[DP LINQ to DataSet Examples#FillDataSet](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#filldataset)]  
  
## <a name="see-also"></a>関連項目  
 [LINQ to DataSet の概要](../../../../docs/framework/data/adonet/linq-to-dataset-overview.md)  
 [Dataset のクエリ](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)  
 [LINQ to DataSet の例](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
