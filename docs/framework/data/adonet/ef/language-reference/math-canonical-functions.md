---
title: "数値演算正規関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 33c8b500002b46d720533f681807889955de5982
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
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
  
## <a name="see-also"></a>参照  
 [正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
