---
title: ANYELEMENT (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 475a9ad6-8c8d-4f49-9970-af273e5360f1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 518ac4bc1ba6842a4b5e5f3b1f0771495752859c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
  
1.  「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#ANYELEMENT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#anyelement)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Null 許容の構造化型](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
