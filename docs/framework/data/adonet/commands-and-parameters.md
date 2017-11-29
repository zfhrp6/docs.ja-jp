---
title: "コマンドおよびパラメーター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e1bfd3e88df4bd90cbcebfa645c2a50159f836db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="commands-and-parameters"></a>コマンドおよびパラメーター
データ ソースへの接続を確立した後、<xref:System.Data.Common.DbCommand> オブジェクトを使用してコマンドを実行し、データ ソースから結果を返すことができます。 コマンドは、使用している .NET Framework データ プロバイダーのいずれかのコマンド コンストラクターで作成できます。 コンストラクターには、データ ソースで実行する SQL ステートメント、<xref:System.Data.Common.DbConnection> オブジェクト、<xref:System.Data.Common.DbTransaction> オブジェクトなど、オプションの引数を渡すことができます。 これらのオブジェクトをコマンドのプロパティとして構成することもできます。 また、<xref:System.Data.Common.DbConnection.CreateCommand%2A> オブジェクトの `DbConnection` メソッドを使用して、特定の接続用のコマンドを作成することもできます。 コマンドによって実行される SQL ステートメントは、<xref:System.Data.Common.DbCommand.CommandText%2A> プロパティを使って構成できます。  
  
 .NET Framework に含まれている各 .NET Framework データ プロバイダーは、`Command` オブジェクトを持ちます。 .NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbCommand> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlCommand> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcCommand> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleCommand> があります。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [コマンドの実行](../../../../docs/framework/data/adonet/executing-a-command.md)  
 ADO.NET の `Command` オブジェクトと、それを使用してデータ ソースに対してクエリやコマンドを実行する方法について説明します。  
  
 [パラメーターとパラメーターのデータ型の構成](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 `Command` のパラメーターの使用 (方向、データ型、パラメーター構文など) について説明します。  
  
 [Commandbuilder でのコマンドを生成します。](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 `DataAdapter` に単一テーブルを対象とする SELECT コマンドが割り当てられているときに、コマンド ビルダーを使用して INSERT、UPDATE、DELETE の各コマンドを自動的に生成する方法について説明します。  
  
 [データベースから 1 つの値を取得します。](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 `ExecuteScalar` オブジェクトの `Command` メソッドを使用してデータベース クエリから単一の値を返す方法について説明します。  
  
 [コマンドを使用してデータを変更するには](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 データ プロバイダーを使用して、ストアド プロシージャまたはデータ定義言語 (DDL) のステートメントを実行する方法について説明します。  
  
## <a name="see-also"></a>関連項目  
 [Dataadapter と Datareader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSet、DataTable、および DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [データ ソースへの接続](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
