---
title: "名前付きの型コンストラクター (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 549dea04-d93d-4c87-a292-f81b1598dbfd
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 72a19094beb03982448a102a4c7362a026d9e611
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="named-type-constructor-entity-sql"></a>名前付きの型コンストラクター (Entity SQL)
エンティティ型や複合型など、概念モデル標準型のインスタンスの作成に使用します。  
  
## <a name="syntax"></a>構文  
  
```  
[{identifier. }] identifier( [expression [{, expression }]] )  
```  
  
## <a name="arguments"></a>引数  
 `identifier`  
 単純な識別子および引用符で囲まれた識別子の値。 詳細については、「[識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 `expression`  
 型の宣言に表示される順序と同じ順序であると見なされる型の属性。  
  
## <a name="return-value"></a>戻り値  
 名前付きの複合型とエンティティ型のインスタンス。  
  
## <a name="remarks"></a>コメント  
 次の例は、標準型と複合型を作成する方法を示しています。  
  
 次の式は、 `Person` 型のインスタンスを作成する式です。  
  
 `Person("abc", 12)`  
  
 次の式は、複合型のインスタンスを作成する式です。  
  
 `MyModel.ZipCode(‘98118’, ‘4567’)`  
  
 次の式は、入れ子になった複合型のインスタンスを作成する式です。  
  
 `MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567'))`  
  
 次の式は、入れ子になった複合型を持つエンティティのインスタンスを作成する式です。  
  
 `MyModel.Person("Bill", MyModel.AddressInfo('My street address', 'Seattle', 'WA', MyModel.ZipCode('98118', '4567')))`  
  
 次の例は、複合型のプロパティを null に初期化する方法を示しています。`MyModel.ZipCode(‘98118’, null)`  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、名前付きの型コンストラクターを使用して、概念モデル型のインスタンスを作成します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#NAMED_TYPE_CONSTRUCTOR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#named_type_constructor)]  
  
## <a name="see-also"></a>関連項目  
 [コンス トラクター](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
