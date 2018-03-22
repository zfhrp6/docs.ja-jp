---
title: '- (減算)(Entity SQL)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 5ca2bc8cb34d99421962289930c26de84eaa68e2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="--subtract-entity-sql"></a>- (減算) (Entity SQL)
2 つの値の間で減算をします。  
  
## <a name="syntax"></a>構文  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 任意の数値データ型の有効な式。  
  
## <a name="result-types"></a>戻り値の型  
 2 つの引数の暗黙の型の昇格の結果であるデータ型。 暗黙的な型の昇格の詳細については、次を参照してください。[型システム](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)です。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、- 算術演算子を使用して 2 つの数値の間で減算をします。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a>参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
