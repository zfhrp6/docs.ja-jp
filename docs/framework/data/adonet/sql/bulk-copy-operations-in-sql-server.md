---
title: "SQL Server でのバルク コピー操作 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# SQL Server でのバルク コピー操作
Microsoft SQL Server には、サイズの大きなファイルをテーブルに高速でバルク コピーしたり、SQL Server データベースのデータを表示したりするための **bcp** という一般的なコマンド ライン ユーティリティが用意されています。  <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用すると、同様の機能を備えたマネージ コード ソリューションを作成できます。  SQL Server のテーブルにデータを読み込むには、INSERT ステートメントを使用するなどの方法もありますが、<xref:System.Data.SqlClient.SqlBulkCopy> を使用すれば他の方法よりもパフォーマンス面で大幅に有利になります。  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用すると、SQL Server のテーブルにのみデータを書き込むことができます。  ただし、データ ソースについては SQL Server に限定されているわけではありません。<xref:System.Data.DataTable> インスタンスのデータの読み込み、または、<xref:System.Data.IDataReader> インスタンスによるデータの読み取りであれば、任意のデータ ソースを使用することができます。  
  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用すると、次のことを実行できます。  
  
-   単一のバルク コピー操作  
  
-   複数のバルク コピー操作  
  
-   トランザクション内でのバルク コピー操作  
  
> [!NOTE]
>  <xref:System.Data.SqlClient.SqlBulkCopy> クラスがサポートされていない、バージョン 1.1 以前の .NET Framework では、<xref:System.Data.SqlClient.SqlCommand> オブジェクトを使用して、SQL Server Transact\-SQL **BULK INSERT** ステートメントを実行できます。  
  
## このセクションの内容  
 [バルク コピー サンプルのセットアップ](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 バルク コピーの例で使用されるテーブルについて説明します。また、AdventureWorks データベースにテーブルを作成する SQL スクリプトを提供します。  
  
 [バルク コピー操作の単一実行](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用して、SQL Server のインスタンスにデータをバルク コピーする単一の方法を説明します。また、Transact\-SQL ステートメントと <xref:System.Data.SqlClient.SqlCommand> クラスを使用したバルク コピー操作の実行方法も説明します。  
  
 [複数のバルク コピー操作](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <xref:System.Data.SqlClient.SqlBulkCopy> クラスを使用して、SQL Server のインスタンスにデータのバルク コピー操作を行う複数の方法を説明します。  
  
 [トランザクションとバルク コピー操作](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 トランザクション内でのバルク コピー操作の実行方法を説明します。トランザクションのコミットやロールバックの方法も説明します。  
  
## 参照  
 [SQL Server と ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)