---
title: "複数のバルク コピー操作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 複数のバルク コピー操作
<xref:System.Data.SqlClient.SqlBulkCopy> クラスのインスタンスを 1 つ使用すると、バルク コピー操作を複数回実行できます。  コピー元とコピー先の間の操作パラメーターが変更になる場合は \(たとえば、コピー先のテーブル名など\)、**WriteToServer** メソッドを続けて呼び出す前に、次の例で示すようにパラメーターを更新する必要があります。  明示的に変更されている場合を除き、すべてのプロパティ値は、任意のインスタンスに対する前回のバルク コピー操作の状態のまま残っています。  
  
> [!NOTE]
>  通常、バルク コピー操作を複数回実行する場合は、同じ <xref:System.Data.SqlClient.SqlBulkCopy> のインスタンスを使用する方が各操作ごとに別のインスタンスを使用するよりも効率的です。  
  
 同じ <xref:System.Data.SqlClient.SqlBulkCopy> オブジェクトを使用してバルク コピー操作を複数回実行する場合は、コピー元またはコピー先の情報が各操作ごとに一致しているかまたは異なっているかどうかは制限されません。  ただし、サーバーに書き込み処理を行うときは、列の関連情報を毎回正しく設定する必要があります。  
  
> [!IMPORTANT]
>  このサンプルは、「[バルク コピー サンプルのセットアップ](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)」で説明しているように作業テーブルを作成してからでないと動作しません。  このコードでは、**SqlBulkCopy** だけを使用した構文について説明します。  コピー元およびコピー先のテーブルが同一の SQL Server インスタンス内に存在する場合、Transact\-SQL `INSERT … SELECT` ステートメントを使用すれば簡単かつ高速にデータをコピーすることができます。  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## 参照  
 [SQL Server でのバルク コピー操作](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)