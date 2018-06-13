---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: bab31ca0a6fd37f5179412b7a4936d564620135e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761774"
---
# <a name="between-entity-sql"></a>BETWEEN (Entity SQL)
式の結果が指定の範囲内の値になるかどうかを判断します。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN 式は、TRANSACT-SQL の BETWEEN 式と同じ機能です。  
  
## <a name="syntax"></a>構文  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 `begin_expression` と `end_expression` で定義される範囲についてテストするための任意の有効な式。 `expression` は、`begin_expression` と `end_expression` の両方と同じ型にする必要があります。  
  
 `begin_expression`  
 任意の有効な式。 `begin_expression` は、`expression` と `end_expression` の両方と同じ型にする必要があります。 `begin_expression` は、`end_expression` 未満でなければなりません。それ以外の場合、戻り値は否定されます。  
  
 `end_expression`  
 任意の有効な式。 `end_expression` は、`expression` と `begin_expression` の両方と同じ型にする必要があります。  
  
 NOT  
 BETWEEN の結果を否定することを指定します。  
  
 AND  
 `expression` と `begin_expression` で表される範囲内で `end_expression` をテストする必要があることを示すプレースホルダーです。  
  
## <a name="return-value"></a>戻り値  
 `true` が、`expression` と `begin_expression` で指定される範囲内にある場合は `end_expression`。それ以外の場合は `false`。 `null` が `expression` であるか、`null` または `begin_expression` が `end_expression` である場合は、`null` が返されます。  
  
## <a name="remarks"></a>コメント  
 両端を除いた範囲を指定するには、BETWEEN の代わりに、より大きい (>) とより小さい (<) を意味する演算子を使用します。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、BETWEEN 演算子を使用して、式の結果が指定の範囲内の値になるかどうかを調べます。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
