---
title: "集計正規関数 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 集計正規関数
集計とは、一連の入力値をまとまった値 \(単一の値など\) に変換する式を指します。  集計は SELECT 式の GROUP BY 句と組み合わせて使用されるのが一般的であり、どこで使用できるかについては制約があります。  
  
 次の表に、集計 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数を示します。  
  
|関数|説明|  
|--------|--------|  
|`Avg(` `expression` `)`|NULL 以外の値の平均を返します。<br /><br /> **引数**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **戻り値**<br /><br /> `expression` の型。  すべての入力値が `null` の場合は `Null` です。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
 [!code-sql[DP EntityServices Concepts#EDM_AVG](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]|  
|`BigCount(` `expression` `)`|NULL 値および重複値を含む集計のサイズを返します。<br /><br /> **引数**<br /><br /> 任意の型。<br /><br /> **戻り値**<br /><br /> `Int64`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
 [!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]|  
|`Count(` `expression` `)`|NULL 値および重複値を含む集計のサイズを返します。<br /><br /> **引数**<br /><br /> 任意の型。<br /><br /> **戻り値**<br /><br /> `Int32`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
 [!code-sql[DP EntityServices Concepts#EDM_COUNT](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]|  
|`Max(` `expression` `)`|NULL 以外の値の最大値を返します。<br /><br /> **引数**<br /><br /> `Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。<br /><br /> **戻り値**<br /><br /> `expression` の型。  すべての入力値が `null` の場合は `Null` です。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
 [!code-sql[DP EntityServices Concepts#EDM_MAX](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]|  
|`Min(` `expression` `)`|NULL 以外の値の最小値を返します。<br /><br /> **引数**<br /><br /> `Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。<br /><br /> **戻り値**<br /><br /> `expression` の型。  すべての入力値が `null` の場合は `Null` です。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
 [!code-sql[DP EntityServices Concepts#EDM_MIN](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]|  
|`StDev(` `expression` `)`|NULL 以外の値の標準偏差を返します。<br /><br /> **引数**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **戻り値**<br /><br /> `Double` すべての入力値が `null` の場合は `Null` です。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
 [!code-sql[DP EntityServices Concepts#EDM_STDEV](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]|  
|`StDevP(` `expression` `)`|すべての値の母集団の標準偏差を返します。<br /><br /> **引数**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **戻り値**<br /><br /> `Double` すべての入力値が `null` の場合は `Null` です。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
 [!code-sql[DP EntityServices Concepts#EDM_STDEVP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]|  
|`Sum(` `expression` `)`|NULL 以外の値の合計を返します。<br /><br /> **引数**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **戻り値**<br /><br /> `Double` すべての入力値が `null` の場合は `Null` です。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
 [!code-sql[DP EntityServices Concepts#EDM_SUM](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]|  
|`Var(` `expression` `)`|すべての null 以外の値の分散を返します。<br /><br /> **引数**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **戻り値**<br /><br /> `Double` すべての入力値が `null` の場合は `Null` です。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
 [!code-sql[DP EntityServices Concepts#EDM_VAR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]|  
|`VarP(` `expression` `)`|すべての null 以外の値の母集団の分散を返します。<br /><br /> **引数**<br /><br /> `Int32`、`Int64`、`Double`、`Decimal`。<br /><br /> **戻り値**<br /><br /> `Double` すべての入力値が `null` の場合は `Null` です。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
 [!code-sql[DP EntityServices Concepts#EDM_VARP](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]|  
  
 同等の機能は、Microsoft SQL クライアント マネージ プロバイダーでも利用できます。  詳細については、「[Entity Framework 用 SqlClient 関数](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)」を参照してください。  
  
## コレクションベースの集計  
 コレクションベースの集計 \(コレクション関数\) は、コレクションに対して演算を実行して、値を返します。  たとえば、ORDERS がすべての注文のコレクションである場合、次の式を使って、最も早い出荷日を計算できます。  
  
```  
min(select value o.ShipDate from LOB.Orders as o)  
```  
  
 コレクションベースの集計では、現在の周囲の名前解決スコープ内で式が評価されます。  
  
## グループベースの集計  
 グループベースの集計では、GROUP BY 句によって定義されたグループごとに計算が実行されます。  その結果の各グループについて、それぞれのグループ内の要素を、集計計算の入力として使って別個の集計が計算されます。  select 式で group by 句を使用した場合、投影または order by 句で使用できるのは、グループ化式の名前、集計式、または定数式だけです。  
  
 次の例では、製品ごとの平均発注数量を計算しています。  
  
```  
select p, avg(ol.Quantity) from LOB.OrderLines as ol  
  group by ol.Product as p  
```  
  
 SELECT 式に明示的な group by 句を指定せずに、グループベースの集計を行うこともできます。  この場合、すべての要素が単一のグループとして扱われます。  これは、定数に基づくグループ化を指定した場合と同等です。  たとえば、次のような式があったとします。  
  
```  
select avg(ol.Quantity) from LOB.OrderLines as ol  
```  
  
 これは、次の指定と同じです。  
  
```  
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1  
```  
  
 グループベースの集計内の式は、WHERE 句式から可視である名前解決スコープ内で評価されます。  
  
 [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] の場合と同様、グループベースの集計には、ALL または DISTINCT の修飾子を指定することもできます。  DISTINCT 修飾子が指定された場合、集計を計算する前に、集計の入力コレクションから重複が除外されます。  ALL 修飾子が指定された場合 \(または修飾子が指定されなかった場合\)、重複は除外されません。  
  
## 参照  
 [正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)