---
title: '|| (OR) (Entity SQL)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: b44934aa0db73f872f0ab27a4c36c5c615855de1
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="-or-entity-sql"></a>|| (OR) (Entity SQL)
2 つの `Boolean` 式を結合します。  
  
## <a name="syntax"></a>構文  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a>引数  
 `boolean_expression`  
 `Boolean`値を返す任意の有効な式。  
  
## <a name="return-value"></a>戻り値  
 いずれかの条件が`true` の場合は `true`、それ以外の場合は `false`。  
  
## <a name="remarks"></a>コメント  
 OR は [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の論理演算子です。 2 つの条件を結合する場合に使用します。 1 つのステートメント内に複数の論理演算子が使われている場合、OR 演算子は AND 演算子の次に評価されます。 ただし、かっこを使うと、演算の順序を変更することができます。  
  
 二重の縦棒 (&#124;&#124;)、OR 演算子と同じ機能があります。  
  
 使用可能な入力値と戻り値の型を次の表に示します。  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|true|TRUE|TRUE|  
|`FALSE`|TRUE|FALSE|NULL|  
|`NULL`|TRUE|NULL|NULL|  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、OR 演算子を使用して 2 つの `Boolean` 式を結合します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
