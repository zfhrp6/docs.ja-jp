---
title: "ストアド プロシージャでのデータの変更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ストアド プロシージャでのデータの変更
ストアド プロシージャは、入力パラメーターとしてデータを受け取り、出力パラメーター、結果セット、または戻り値としてデータを返すことができます。  以下のサンプルでは、入力パラメーター、出力パラメーター、および戻り値が ADO.NET によってどのようにやり取りされるかを示したものです。  この例では、主キー列が SQL Server データベースの ID 列であるテーブルに新しいレコードを挿入しています。  
  
> [!NOTE]
>  SQL Server のストアド プロシージャで、<xref:System.Data.SqlClient.SqlDataAdapter> を使用してデータを編集または削除する場合、ストアド プロシージャの定義に SET NOCOUNT ON は使用しないでください。  処理された行数がゼロとして返され、`DataAdapter` によって同時実行の競合として解釈されてしまいます。  この場合、<xref:System.Data.DBConcurrencyException> がスローされます。  
  
## 例  
 この例では、次のストアド プロシージャを使用して、**Northwind** **Categories** テーブルに新しいカテゴリを挿入します。  このストアド プロシージャは **CategoryName** 列の値を入力パラメーターとして受け取り、SCOPE\_IDENTITY\(\) 関数を使用して ID フィールド **CategoryID** の新しい値を取得し、その値を出力パラメーター内に返します。  RETURN ステートメントは、@@ROWCOUNT 関数を使用して、挿入された行の数を返します。  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 上述の `InsertCategory` ストアド プロシージャを <xref:System.Data.SqlClient.SqlDataAdapter> の <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> のソースとして使用する例を次に示します。  `@Identity` 出力パラメーターは、<xref:System.Data.SqlClient.SqlDataAdapter> の `Update` メソッドが呼び出され、データベースにレコードが挿入された後で <xref:System.Data.DataSet> に反映されます。  戻り値も取得されます。  
  
> [!NOTE]
>  <xref:System.Data.OleDb.OleDbDataAdapter> を使用する場合、**ReturnValue** の <xref:System.Data.ParameterDirection> を含むパラメーターを他のパラメーターより先に指定する必要があります。  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## 参照  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [コマンドの実行](../../../../docs/framework/data/adonet/executing-a-command.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)