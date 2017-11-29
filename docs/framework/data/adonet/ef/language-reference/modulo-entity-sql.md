---
title: "(剰余) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cff0e4eaadf601b7a90f3caa0ecd9cf2f48feab0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="modulo-entity-sql"></a>(剰余) (Entity SQL)
ある式を別の式で除算した結果の余りを返します。  
  
## <a name="syntax"></a>構文  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>引数  
 `dividend`  
 除算する数値式。 `dividend` は、任意の数値データ型の有効な式です。  
  
 `divisor`  
 被除数を除算する数値式。 `divisor` は、任意の数値データ型の有効な式です。  
  
## <a name="result-types"></a>戻り値の型  
 Edm.Int32  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、% 算術演算子を使用して、特定の式を別の式で除算した結果の余りを返します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
