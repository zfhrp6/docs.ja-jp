---
title: 数学関数
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 9dfd1faf9bdab995b19c38e32f64a88ed67cb280
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766973"
---
# <a name="mathematical-functions"></a>数学関数
.NET Framework Data Provider for SQL Server (SqlClient) には、引数として指定された入力値に対して計算を実行し、数値結果を返す数学関数が用意されています。 これらの関数は、SqlClient の SqlServer 名前空間に存在します。 Entity Framework は、プロバイダーの名前空間プロパティを使用することにより、型や関数など、特定のコンストラクターに対してこのプロバイダーによってどのプレフィックスが使用されているかを特定できます。次の表に、SqlClient の数学関数を示します。  
  
|関数|説明|  
|--------------|-----------------|  
|`ABS(` `expression` `)`|絶対値を求める関数です。<br /><br /> **引数**<br /><br /> `expression`: `Int32`、`Int64`、`Double`、または `Decimal`。<br /><br /> **戻り値**<br /><br /> 指定された式の絶対値。<br /><br /> **例**<br /><br /> `SqlServer.ABS(-2)`|  
|`ACOS(` `expression` `)`|指定された式のアークコサイン (逆余弦) 値を返します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.ACOS(.9)`|  
|`ASIN(` `expression` `)`|指定された式のアークサイン (逆正弦) 値を返します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.ASIN(.9)`|  
|`ATAN(` `expression` `)`|指定された数値式のアークタンジェント (逆正接) 値を返します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.ATAN(9)`|  
|`ATN2(` `expression`, `expression``)`|指定された 2 つの数値式の商がタンジェント (正接) となる角度をラジアンで返します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.ATN2(9, 8)`|  
|`CEILING(` `expression` `)`|指定された式をその式以上の最小整数に変換します。<br /><br /> **引数**<br /><br /> `expression`: `Int32`、`Int64`、`Double`、または `Decimal`。<br /><br /> **戻り値**<br /><br /> `Int32`、 `Int64`、 `Double`、または`Decimal`です。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]|  
|`COS(` `expression` `)`|ラジアンで指定された角度のコサイン (余弦) を計算します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.COS(45)`|  
|`COT(` `expression` `)`|ラジアンで指定された角度のコタンジェント (余接) を計算します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.COT(60)`|  
|`DEGREES(` `radians` `)`|対応する角度を度数で返します。<br /><br /> **引数**<br /><br /> `expression`: `Int32`、`Int64`、`Double`、または `Decimal`。<br /><br /> **戻り値**<br /><br /> `Int32`、 `Int64`、 `Double`、または`Decimal`です。<br /><br /> **例**<br /><br /> `SqlServer.DEGREES(3.1)`|  
|`EXP(` `expression` `)`|指定された数値式の指数値を計算します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.EXP(1)`|  
|`FLOOR(` `expression` `)`|指定された式をその式以下の最大整数に変換します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]|  
|`LOG(` `expression` `)`|指定された `float` 型の式の自然対数を計算します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.LOG(100)`|  
|`LOG10(` `expression` `)`|指定された `Double` 型の式の 10 を底とした対数を返します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.LOG10(100)`|  
|`PI()`|π の定数値を `Double` として返します。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.PI()`|  
|`POWER(` `numeric_expression, power_expression` `)`|指定された式の指定されたべき乗を計算します。<br /><br /> **引数**<br /><br /> `numeric_expression`: `Int32`、`Int64`、`Double`、または `Decimal`。<br /><br /> `power_expression`: `Double` のべき乗値を表す `numeric_expression` 型の値。<br /><br /> **戻り値**<br /><br /> 指定された `numeric_expression` を指定された `power_expression` でべき乗した値。<br /><br /> **例**<br /><br /> `SqlServer.POWER(2,7)`|  
|`RADIANS(` `expression` `)`|角度をラジアンに変換します。<br /><br /> **引数**<br /><br /> `expression`: `Int32`、`Int64`、`Double`、または `Decimal`。<br /><br /> **戻り値**<br /><br /> `Int32`、 `Int64`、<br /><br /> `Double`、または <br /><br /> `Decimal`。<br /><br /> **例**<br /><br /> `SqlServer.RADIANS(360.0)`|  
|`RAND(`[シード]`)`|0 から 1 までの範囲の乱数を返します。<br /><br /> **引数**<br /><br /> シード値を `Int32` として返します。 シードを指定しない場合は、SQL Server データベース エンジンによってシード値がランダムに割り当てられます。 指定したシード値について、返される結果は常に同じです。<br /><br /> **戻り値**<br /><br /> 0 から 1 までの範囲の `Double` 型の乱数。<br /><br /> **例**<br /><br /> `SqlServer.RAND()`|  
|`ROUND(` `numeric_expression, length` [ ,`function` ]`)`|指定された長さまたは有効桁数に丸めた数値式を返します。<br /><br /> **引数**<br /><br /> `numeric_expression`: `Int32`、`Int64`、`Double`、または `Decimal`。<br /><br /> `length`: `Int32` を丸めた後の有効桁数を表す `numeric_expression`。 `length` に正の値を指定した場合、`numeric_expression` は `length` で指定した小数点以下桁数に丸められます。 `length` に負の値を指定した場合、`numeric_expression` は `length` で指定した小数点の左側の位置で丸められます。<br /><br /> `function`: (省略可能)、`Int32`を実行する操作の種類を表すです。 関数が省略されているか、0 (既定値) の値を持つとき`numeric_expression`は丸められます。 以外の値 0 が指定した場合、`numeric_expression`が切り詰められています。<br /><br /> **戻り値**<br /><br /> 指定された `numeric_expression` を指定された `power_expression` でべき乗した値。<br /><br /> **例**<br /><br /> `SqlServer.ROUND(748.58, -3)`|  
|`SIGN(` `expression` `)`|指定した式の符号として、正 (+1)、負 (-1)、ゼロ (0) のいずれかを返します。<br /><br /> **引数**<br /><br /> `expression`: `Int32`、`Int64`、`Double`、または `Decimal`<br /><br /> **戻り値**<br /><br /> `Int32`、 `Int64`、 `Double`、または`Decimal`です。<br /><br /> **例**<br /><br /> `SqlServer.SIGN(-10)`|  
|`SIN(` `expression` `)`|ラジアンで指定された角度のサイン (正弦) を計算し、`Double` 式を返します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.SIN(20)`|  
|`SQRT(` `expression` `)`|指定された式の平方根を返します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.SQRT(3600)`|  
|`SQUARE(` `expression` `)`|指定された式の 2 乗値を返します。<br /><br /> **引数**<br /><br /> `expression`: `Double`。<br /><br /> **戻り値**<br /><br /> `Double`。<br /><br /> **例**<br /><br /> `SqlServer.SQUARE(25)`|  
|`TAN(` `expression` `)`|指定された式のタンジェントを計算します。<br /><br /> **引数**<br /><br /> `expression`: `Double`<br /><br /> **戻り値**<br /><br /> `Double`<br /><br /> **例**<br /><br /> `SqlServer.TAN(45.0)`|  
  
 SqlClient でサポートされる数学関数の詳細については、SqlClient プロバイダー マニフェストで指定した SQL Server のバージョンのドキュメントを参照してください。  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|---------------------|---------------------|---------------------|  
|[数学関数 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115913)|[数学関数 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115911)|[数学関数 (TRANSACT-SQL)](http://go.microsoft.com/fwlink/?LinkId=115912)|  
  
## <a name="see-also"></a>関連項目  
 [Entity Framework 用 SqlClient 関数](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)
