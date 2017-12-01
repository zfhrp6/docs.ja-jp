---
title: "ADO.NET でのデータ ソースへの接続"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9abc3f92-1be3-4e1a-b360-762dc689650e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0d21c571b659e9d7aef65893db18b034d614e2af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="connecting-to-a-data-source-in-adonet"></a>ADO.NET でのデータ ソースへの接続
ADO.NET で使用して、**接続**接続文字列に必要な認証情報を入力して、特定のデータ ソースに接続するオブジェクト。 **接続**オブジェクトを使用するデータ ソースの種類によって異なります。  
  
 .NET Framework に含まれている各 .NET Framework データ プロバイダーは、<xref:System.Data.Common.DbConnection> オブジェクトを持っています。.NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbConnection> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlConnection> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcConnection> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleConnection> があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [接続を確立します。](../../../../docs/framework/data/adonet/establishing-the-connection.md)  
 使用する方法について説明します、**接続**オブジェクト データ ソースへの接続を確立します。  
  
 [接続イベント](../../../../docs/framework/data/adonet/connection-events.md)  
 使用する方法について説明します、 **InfoMessage**データ ソースから情報メッセージを取得するイベントです。  
  
## <a name="see-also"></a>関連項目  
 [接続文字列](../../../../docs/framework/data/adonet/connection-strings.md)  
 [接続プール](../../../../docs/framework/data/adonet/connection-pooling.md)  
 [コマンドおよびパラメーター](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Dataadapter と Datareader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
