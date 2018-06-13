---
title: ANYELEMENT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
ms.openlocfilehash: 11d1dd4b09ff07519f3435d313de72c5b9a3edf4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761845"
---
# <a name="anyelement-entity-sql"></a>ANYELEMENT (Entity SQL)
複数値のコレクションから要素を抽出します。  
  
## <a name="syntax"></a>構文  
  
```  
ANYELEMENT ( expression )  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 要素の抽出元のコレクションを返す任意の有効なクエリ式。  
  
## <a name="return-value"></a>戻り値  
 コレクションに複数の要素が存在する場合はコレクション内の単一の要素 (任意の要素) が、コレクションが空の場合は `null`が返されます。 場合`collection`型のコレクションは、 `Collection<T>`、し`ANYELEMENT(collection)`型のインスタンスを生成する有効な式です`T`です。  
  
## <a name="remarks"></a>コメント  
 ANYELEMENT では、複数値のコレクションから任意の要素が抽出されます。 たとえば、次の例では、 `Customers`という集合から単一の要素が抽出されます。  
  
```  
ANYELEMENT(Customers)  
```  
  
## <a name="example"></a>例  
 次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、ANYELEMENT 演算子を使用して、複数値のコレクションから要素を抽出します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [NULL 値が許容される構造化型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
