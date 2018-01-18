---
title: "バルク コピー操作の複数実行"
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
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8a753357719f451ce7acc2d7f42c0493ca2357ab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="multiple-bulk-copy-operations"></a>バルク コピー操作の複数実行
<xref:System.Data.SqlClient.SqlBulkCopy> クラスのインスタンスを 1 つ使用すると、バルク コピー操作を複数回実行できます。 後続の呼び出しの前に更新する必要があります (たとえば、レプリケーション先テーブルの名前) のコピー間で操作のパラメーターを変更する場合、 **WriteToServer**メソッドは、次の例で示したようにします。 明示的に変更されている場合を除き、すべてのプロパティ値は、任意のインスタンスに対する前回のバルク コピー操作の状態のまま残っています。  
  
> [!NOTE]
>  通常、バルク コピー操作を複数回実行する場合は、同じ <xref:System.Data.SqlClient.SqlBulkCopy> のインスタンスを使用する方が各操作ごとに別のインスタンスを使用するよりも効率的です。  
  
 同じ <xref:System.Data.SqlClient.SqlBulkCopy> オブジェクトを使用してバルク コピー操作を複数回実行する場合は、コピー元またはコピー先の情報が各操作ごとに一致しているかまたは異なっているかどうかは制限されません。 ただし、サーバーに書き込み処理を行うときは、列の関連情報を毎回正しく設定する必要があります。  
  
> [!IMPORTANT]
>  」の説明に従って、作業テーブルを作成していない限り、このサンプルは実行されません[バルク コピー サンプルのセットアップ](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)です。 使用する構文を示すためにこのコードが提供される**SqlBulkCopy**のみです。 コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact-SQL `INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>参照  
 [SQL Server でのバルク コピー操作](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
