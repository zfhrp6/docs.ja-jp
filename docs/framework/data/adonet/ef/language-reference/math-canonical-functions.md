---
title: 数値演算正規関数
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9d823eb45babca4b8f5dd717b4fb92c1984d1c8c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765101"
---
# <a name="math-canonical-functions"></a>数値演算正規関数
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] には数学正規関数が含まれます。  
  
 次の表に、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 数学正規関数を示します。  
  
|関数|説明|  
|--------------|-----------------|  
|`Abs(` `value` `)`|`value` の絶対値を返します。<br /><br /> **引数**<br /><br /> `Int16`、 `Int32`、 `Int64`、 `Byte`、 `Single`、 `Double`、および`Decimal`です。<br /><br /> **戻り値**<br /><br /> `value` の型。<br /><br /> **例**<br /><br /> `Abs(-2)`|  
|`Ceiling(` `value` `)`|`value` 以上で最小の整数値を返します。<br /><br /> **引数**<br /><br /> A `Single`、 `Double`、および`Decimal`です。<br /><br /> **戻り値**<br /><br /> `value` の型。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
 [!code-sql[DP EntityServices Concepts#EDM_CEILING](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]|  
|`Floor(` `value` `)`|`value` 以下で最大の整数値を返します。<br /><br /> **引数**<br /><br /> A `Single`、 `Double`、および`Decimal`です。<br /><br /> **戻り値**<br /><br /> `value` の型。<br /><br /> **例**<br /><br /> [!code-csharp[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
 [!code-sql[DP EntityServices Concepts#EDM_FLOOR](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]|  
|`Power(` `value`, `exponent``)`|指定された `value` を指定された `exponent` でべき乗した結果を返します。<br /><br /> **引数**<br /><br /> `value``Int32, Int64, Double`、または`Decimal`です。<br /><br /> `exponent``Int64``, Double`、または`Decimal`です。<br /><br /> **戻り値**<br /><br /> `value` の型。<br /><br /> **例**<br /><br /> `Power(748.58,2)`|  
|`Round(` `value` `)`|最も近い整数に丸められた `value` の整数部分を返します。<br /><br /> **引数**<br /><br /> A `Single`、 `Double`、および`Decimal`です。<br /><br /> **戻り値**<br /><br /> `value` の型。<br /><br /> **例**<br /><br /> `Round(748.58)`|  
|`Round(` `value`, `digits``)`|`value` を指定された最も近い `digits` に丸めて返します。<br /><br /> **引数**<br /><br /> `value`: `Double` または `Decimal`。<br /><br /> `digits`: `Int16` または `Int32`。<br /><br /> **戻り値**<br /><br /> `value` の型。<br /><br /> **例**<br /><br /> `Round(748.58,1)`|  
|`Truncate(` `value`, `digits``)`|`value` を指定された最も近い `digits` に切り詰めて返します。<br /><br /> **引数**<br /><br /> `value`: `Double` または `Decimal`。<br /><br /> `digits`: `Int16` または `Int32`。<br /><br /> **戻り値**<br /><br /> `value` の型。<br /><br /> **例**<br /><br /> `Truncate(748.58,1)`|  
  
 `null` が入力された場合、これらの関数は `null` を返します。  
  
 同等の機能は、Microsoft SQL クライアント マネージ プロバイダーでも利用できます。 詳細については、次を参照してください。 [Framework 用 SqlClient エンティティ関数](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)です。  
  
## <a name="see-also"></a>関連項目  
 [正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
