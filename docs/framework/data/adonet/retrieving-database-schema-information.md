---
title: "データベース スキーマ情報の取得 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# データベース スキーマ情報の取得
データベースからのスキーマ情報の取得は、スキーマの検出プロセスによって行われます。  スキーマの検出により、アプリケーションでは、指定されたデータベースのデータベース スキーマに関する情報を検索して返すように、マネージ プロバイダーに要求できます。データベース スキーマは*メタデータ*としても知られます。  テーブル、列、ストアド プロシージャなどの各種のデータベース スキーマ要素は、スキーマ コレクションを通じて公開されます。  各スキーマ コレクションには、使用されているプロバイダーに固有の各種のスキーマ情報が含まれています。  
  
 それぞれの .NET Framework マネージ プロバイダーは、**Connection** クラスに **GetSchema** メソッドを実装します。また、**GetSchema** メソッドから返されるスキーマ情報は、<xref:System.Data.DataTable> という形式になります。  **GetSchema** メソッドは、返すスキーマ コレクションを指定し、返される情報の量を制限するためのオプション パラメーターを提供する、オーバーロードされたメソッドです。  
  
 .NET Framework Data Providers for OLE DB、.NET Framework Data Providers for ODBC、.NET Framework Data Providers for Oracle、および .NET Framework Data Providers for SqlClient は、**DataReader** の列のメタデータを表す DataTable を返す **GetSchemaTable** メソッドを提供します。  
  
 .NET Framework Data Provider for OLE DB では、<xref:System.Data.OleDb.OleDbConnection> オブジェクトの <xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> メソッドを使ってスキーマ情報を公開します。  **GetOleDbSchemaTable** は、引数として、返すスキーマ情報を識別する <xref:System.Data.OleDb.OleDbSchemaGuid> と、返された列に対する制限の配列を受け取ります。  **GetOleDbSchemaTable** は、要求されたスキーマ情報を格納している <xref:System.Data.DataTable> を返します。  
  
## このセクションの内容  
 [GetSchema およびスキーマ コレクション](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 **GetSchema** メソッドと、このメソッドを使ってデータベースからスキーマ情報を取得して制限する方法について説明します。  
  
 スキーマの制限  
 **GetSchema** で使用できるスキーマの制限について説明します。  
  
 [共通のスキーマ コレクション](../../../../docs/framework/data/adonet/common-schema-collections.md)  
 すべての .NET Framework マネージ プロバイダーでサポートされる共通のスキーマ コレクションについて説明します。  
  
 [SQL Server スキーマ コレクション](../../../../docs/framework/data/adonet/sql-server-schema-collections.md)  
 .NET Framework Provider for SQL Server でサポートされるスキーマ コレクションについて説明します。  
  
 [Oracle スキーマ コレクション](../../../../docs/framework/data/adonet/oracle-schema-collections.md)  
 .NET Framework Provider for Oracle でサポートされるスキーマ コレクションについて説明します。  
  
 [ODBC スキーマ コレクション](../../../../docs/framework/data/adonet/odbc-schema-collections.md)  
 ODBC ドライバーのスキーマ コレクションについて説明します。  
  
 [OLE DB スキーマ コレクション](../../../../docs/framework/data/adonet/ole-db-schema-collections.md)  
 OLE DB プロバイダーのスキーマ コレクションについて説明します。  
  
## 関連項目  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 <xref:System.Data.Common.DbConnection> クラスの **GetSchema** メソッドについて説明します。  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 <xref:System.Data.Odbc.OdbcConnection> クラスの **GetSchema** メソッドについて説明します。  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 <xref:System.Data.OleDb.OleDbConnection> クラスの **GetSchema** メソッドについて説明します。  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 <xref:System.Data.OracleClient.OracleConnection> クラスの **GetSchema** メソッドについて説明します。  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 <xref:System.Data.SqlClient.SqlConnection> クラスの **GetSchema** メソッドについて説明します。  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 <xref:System.Data.Common.DbDataReader> クラスの **GetSchemaTable** メソッドについて説明します。  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 <xref:System.Data.Odbc.OdbcDataReader> クラスの **GetSchemaTable** メソッドについて説明します。  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 <xref:System.Data.OleDb.OleDbDataReader> クラスの **GetSchemaTable** メソッドについて説明します。  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 <xref:System.Data.OracleClient.OracleDataReader> クラスの **GetSchemaTable** メソッドについて説明します。  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 <xref:System.Data.SqlClient.SqlDataReader> クラスの **GetSchemaTable** メソッドについて説明します。  
  
## 参照  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)