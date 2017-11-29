---
title: "集計関数 (Entity Framework 用 SqlClient)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b60cffd357022454de001986a48ef06bdd1fe3f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a>集計関数 (Entity Framework 用 SqlClient)
.NET Framework Data Provider for SQL Server (SqlClient) には、集計関数が用意されています。 集計関数は、一連の入力値に対して計算を実行し、値を返します。 これらの関数は、SqlClient の SqlServer 名前空間に存在します。 Entity Framework は、プロバイダーの名前空間プロパティを使用することにより、型や関数など、特定のコンストラクターに対してこのプロバイダーによってどのプレフィックスが使用されているかを特定できます。  
  
 次の表に、SqlClient の集計関数を示します。  
  
|関数|説明|  
|--------------|-----------------|  
|`AVG(` `expression` `)`|コレクション内の値の平均値を返します。<br /><br /> NULL 値は無視されます。<br /><br /> **引数**<br /><br /> `Int32`、 `Int64`、 `Double`、および`Decimal`です。<br /><br /> **戻り値**<br /><br /> `expression` の型。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]|  
|`CHECKSUM_AGG(` `collection` `)`|コレクション内にある値のチェックサムを返します。<br /><br /> NULL 値は無視されます。<br /><br /> **引数**<br /><br /> Collection (`Int32`)。<br /><br /> **戻り値**<br /><br /> `Int32`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]|  
|`COUNT(` `expression` `)`|コレクション内のアイテムの数を `Int32` 型の値として返します。<br /><br /> **引数**<br /><br /> Collection (T)。ここで、T は次のいずれかの型になります。<br /><br /> `Guid` (SQL Server 2000 では返されません)、<br /><br /> `Boolean`、`Double`、`DateTime`、`DateTimeOffset`、`Time`、`String`、または `Binary`。<br /><br /> **戻り値**<br /><br /> `Int32`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]|  
|`COUNT_BIG(` `expression` `)`|コレクション内のアイテムの数を `bigint` 型の値として返します。<br /><br /> **引数**<br /><br /> Collection (T)。ここで、T は次のいずれかの型になります。<br /><br /> `Guid` (SQL Server 2000 では返されません)、`Boolean`、`Double`、`DateTime`、`DateTimeOffset`、`Time`、`String`、または `Binary`。<br /><br /> **戻り値**<br /><br /> `Int64`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]|  
|`MAX(` `expression` `)`|コレクション内の最大値を返します。<br /><br /> **引数**<br /><br /> Collection (T)。ここで、T は `Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary` のいずれかの型になります。<br /><br /> **戻り値**<br /><br /> `expression` の型。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]|  
|`MIN(` `expression` `)`|コレクション内の最小値を返します。<br /><br /> **引数**<br /><br /> Collection (T)。ここで、T は `Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String` のいずれかの型になります。<br /><br /> `Binary`。<br /><br /> **戻り値**<br /><br /> `expression` の型。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]|  
|`STDEV(` `expression` `)`|指定された式のすべての値の統計的標準偏差を返します。<br /><br /> **引数**<br /><br /> Collection (`Double`)。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]|  
|`STDEVP(` `expression` `)`|指定された式のすべての値を母集団として統計的標準偏差を返します。<br /><br /> **引数**<br /><br /> Collection (`Double`)。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]|  
|`SUM(` `expression` `)`|コレクション内のすべての値の合計を返します。<br /><br /> **引数**<br /><br /> Collection (T)。ここで、T は `Int32`、`Int64`、`Double`、`Decimal` のいずれかの型になります。<br /><br /> **戻り値**<br /><br /> `expression` の型。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]|  
|`VAR(` `expression` `)`|指定された式のすべての値の統計的分散を返します。<br /><br /> **引数**<br /><br /> Collection (`Double`)。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]|  
|`VARP(` `expression` `)`|指定した式のすべての値について、母集団に対する統計的変位を返します。<br /><br /> **引数**<br /><br /> Collection (`Double`)。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]|  
  
 SqlClient でサポートされる集計関数の詳細については、SqlClient プロバイダー マニフェストで指定した SQL Server のバージョンのドキュメントを参照してください。  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[集計関数 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115906)|[集計関数 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkID=115903)|[集計関数 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115907)|  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [集計正規関数](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
