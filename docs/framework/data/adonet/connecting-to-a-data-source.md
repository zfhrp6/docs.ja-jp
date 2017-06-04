---
title: "ADO.NET でのデータ ソースへの接続 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ADO.NET でのデータ ソースへの接続
ADO.NET では、**Connection** オブジェクトを使用して、接続文字列に必要な認証情報を指定することにより、特定のデータ ソースに接続します。  どの **Connection** オブジェクトを使用するかは、データ ソースの種類によって異なります。  
  
 .NET Framework に含まれている各 .NET Framework データ プロバイダーは、<xref:System.Data.Common.DbConnection> オブジェクトを持っています。.NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbConnection> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlConnection> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcConnection> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleConnection> があります。  
  
## このセクションの内容  
 [接続の確立](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 **Connection** オブジェクトを使用して、データ ソースとの接続を確立する方法について説明します。  
  
 [接続イベント](../../../../docs/framework/data/adonet/connection-events.md)  
 **InfoMessage** イベントを使用してデータ ソースから情報メッセージを取得する方法について説明します。  
  
## 参照  
 [接続文字列](../../../../docs/framework/data/adonet/connection-strings.md)   
 [接続プール](../../../../docs/framework/data/adonet/connection-pooling.md)   
 [コマンドとパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)   
 [ADO.NET Managed Providers and DataSet Developer Center \(ADO.NET マネージ プロバイダーと DataSet デベロッパー センター\)](http://go.microsoft.com/fwlink/?LinkId=217917)