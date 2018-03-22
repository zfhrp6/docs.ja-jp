---
title: MULTISET (Entity SQL)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
caps.latest.revision: ''
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 6389051ae1244a2a38699704c67217d9807fe7e4
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)
値のリストからマルチセットのインスタンスを作成します。 MULTISET コンストラクターの値はすべて、互換性のある型 `T`である必要があります。 空のマルチセット コンストラクターは使用できません。  
  
## <a name="syntax"></a>構文  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 任意の有効な値のリスト。  
  
## <a name="return-value"></a>戻り値  
 型 MULTISET のコレクション\<T > です。  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] には、行コンストラクター、オブジェクト コンストラクター、およびマルチセット (またはコレクション) コンストラクターの 3 種類のコンストラクターが用意されています。 詳細については、次を参照してください。[の構築型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)です。  
  
 マルチセット コンストラクターは、値のリストからマルチセットのインスタンスを作成します。 このコンストラクターの値はすべて、互換性のある型である必要があります。  
  
 たとえば、次の式は整数のマルチセットを作成します。  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  入れ子になったマルチセット リテラルは、 `{{1, 2, 3}}`のように、外側のマルチセットに含まれているマルチセット要素が 1 つである場合にのみサポートされます。 複数のマルチセット要素が外側のマルチセットに含まれている場合 ( `{{1, 2}, {3, 4}}`など)、入れ子になったマルチセット リテラルはサポートされません。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、MULTISET 演算子を使用して、値のリストからマルチセットのインスタンスを作成します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>参照  
 [コンストラクター](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
