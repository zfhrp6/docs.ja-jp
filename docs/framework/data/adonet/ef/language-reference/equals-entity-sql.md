---
title: = (等しい) (Entity SQL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 27faf6c59afd4de2481f474053812b12182e3f58
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="-equals-entity-sql"></a>= (等しい) (Entity SQL)
2 つの式の等価性を比較します。  
  
## <a name="syntax"></a>構文  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 任意の有効な式。 両方の式とも、暗黙的に変換可能なデータ型でなければなりません。  
  
## <a name="result-types"></a>戻り値の型  
 左の式が右の式と等しい場合は`true` 、等しくない場合は `false`。  
  
## <a name="remarks"></a>コメント  
 == 演算子は = 演算子と同じです。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、= 比較演算子を使用して 2 つの式の等価性を比較します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a>参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
