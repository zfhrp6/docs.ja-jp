---
title: "データベース スキーマ情報の取得"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79038d52-f122-4fd4-9bfb-aaa22d6a114b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 19fee0f90c1f460d253cfdc865035a6b8aa3db48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-database-schema-information"></a>データベース スキーマ情報の取得
データベースからのスキーマ情報の取得は、スキーマの検出プロセスによって行われます。 スキーマの検出により、アプリケーションはマネージ プロバイダーを検索するとも呼ばれるデータベース スキーマに関する情報を返すことを要求する*メタデータ*、特定のデータベースです。 テーブル、列、ストアド プロシージャなどの各種のデータベース スキーマ要素は、スキーマ コレクションを通じて公開されます。 各スキーマ コレクションには、使用されているプロバイダーに固有の各種のスキーマ情報が含まれています。  
  
 .NET Framework マネージ プロバイダーの実装の各、 **GetSchema**メソッドで、**接続**クラス、およびから返されるスキーマ情報、 **GetSchema**メソッドは、の形式では、<xref:System.Data.DataTable>です。 **GetSchema**メソッドが戻るには、スキーマ コレクションを指定し、返される情報の量を制限するための省略可能なパラメーターを提供するオーバー ロードされたメソッドです。  
  
 OLE DB、ODBC、Oracle、および SqlClient 用の .NET Framework データ プロバイダーの提供、 **GetSchemaTable**の列のメタデータを表す DataTable を返すメソッド、 **DataReader**です。  
  
 .NET Framework Data Provider for OLE DB では、<xref:System.Data.OleDb.OleDbConnection.GetOleDbSchemaTable%2A> オブジェクトの <xref:System.Data.OleDb.OleDbConnection> メソッドを使ってスキーマ情報を公開します。 引数として、 **GetOleDbSchemaTable**受け取り、<xref:System.Data.OleDb.OleDbSchemaGuid>スキーマ情報を返すを識別して、これらの制限の配列には、列が返されます。 **GetOleDbSchemaTable**を返します、<xref:System.Data.DataTable>要求されたスキーマ情報が設定されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [GetSchema およびスキーマ コレクション](../../../../docs/framework/data/adonet/getschema-and-schema-collections.md)  
 について説明します、 **GetSchema**メソッドとそれを使用して、取得し、データベースからスキーマ情報を制限する方法です。  
  
 スキーマの制限  
 使用できるスキーマの制限について説明します**GetSchema**です。  
  
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
  
## <a name="reference"></a>参照  
 <xref:System.Data.Common.DbConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.Common.DbConnection>クラスです。  
  
 <xref:System.Data.Odbc.OdbcConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.Odbc.OdbcConnection>クラスです。  
  
 <xref:System.Data.OleDb.OleDbConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.OleDb.OleDbConnection>クラスです。  
  
 <xref:System.Data.OracleClient.OracleConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.OracleClient.OracleConnection>クラスです。  
  
 <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>  
 について説明します、 **GetSchema**のメソッド、<xref:System.Data.SqlClient.SqlConnection>クラスです。  
  
 <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.Common.DbDataReader>クラスです。  
  
 <xref:System.Data.Odbc.OdbcDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.Odbc.OdbcDataReader>クラスです。  
  
 <xref:System.Data.OleDb.OleDbDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.OleDb.OleDbDataReader>クラスです。  
  
 <xref:System.Data.OracleClient.OracleDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.OracleClient.OracleDataReader>クラスです。  
  
 <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>  
 について説明します、 **GetSchemaTable**のメソッド、<xref:System.Data.SqlClient.SqlDataReader>クラスです。  
  
## <a name="see-also"></a>参照  
 [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
