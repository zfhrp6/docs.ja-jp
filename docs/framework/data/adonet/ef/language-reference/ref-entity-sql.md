---
title: REF (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1836b91876ac3c993f07902a644c130dda76f158
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ref-entity-sql"></a>REF (Entity SQL)
エンティティ インスタンスへの参照を返します。  
  
## <a name="syntax"></a>構文  
  
```  
REF( expression )   
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 エンティティ型のインスタンスを生成する任意の有効な式。  
  
## <a name="return-value"></a>戻り値  
 指定されたエンティティ インスタンスへの参照。  
  
## <a name="remarks"></a>コメント  
 エンティティ参照は、エンティティ キーとエンティティ セット名で構成されます。 異なるエンティティ セットが同じエンティティ型に基づくことができるので、特定のエンティティ キーが複数のエンティティ セットで使用される場合があります。 ただし、エンティティ参照は常に一意です。 入力式が永続エンティティを表す場合、このエンティティへの参照が返されます。 入力式が永続エンティティではない場合は、NULL 参照が返されます。  
  
 プロパティ抽出演算子 (.) を使用してエンティティのプロパティにアクセスすると、参照は自動的に逆参照されます。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリは、REF 演算子を使用して入力エンティティ引数の参照を返します。 プロパティ抽出演算子 (.) を使用して Product エンティティのプロパティにアクセスすることにより、同じクエリでこの参照が逆参照されます。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  」の手順に従って[する方法: PrimitiveType 結果が返されますそのクエリを実行する](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)です。  
  
2.  次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#REF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref)]  
  
## <a name="see-also"></a>参照  
 [DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
 [CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [型定義](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)
