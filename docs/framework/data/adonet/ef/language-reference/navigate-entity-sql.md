---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: c374261ad3702294f5720edb7881e21ba79d85bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764737"
---
# <a name="navigate-entity-sql"></a>NAVIGATE (Entity SQL)
エンティティ間で確立されたリレーションシップをナビゲートします。  
  
## <a name="syntax"></a>構文  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a>引数  
 `instance-expresssion`  
 エンティティのインスタンス。  
  
 `relationship-type`  
 概念スキーマ定義言語 (CSDL) ファイルで指定されたリレーションシップの種類の名前。 `relationship-type`として修飾\<名前空間 >.\<<namespace>.<relationship type name >。  
  
 `to`  
 リレーションシップの終端エンティティ。  
  
 `from`  
 リレーションシップの開始エンティティ。  
  
## <a name="return-value"></a>戻り値  
 終端のカーディナリティが 1 の場合、戻り値は `Ref<T>` になります。 終端のカーディナリティが n の場合、戻り値は `Collection<Ref<T>>` になります。  
  
## <a name="remarks"></a>コメント  
 リレーションシップは、 [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM) における最上位の構造です。 リレーションシップは、複数のエンティティ型の間で確立され、ユーザーはエンティティ間のリレーションシップをナビゲートできます。 `from` と `to` は、リレーションシップ内の名前解決があいまいでない場合の条件付きのオプションです。  
  
 NAVIGATE は、O および C 空間で有効です。  
  
 ナビゲーション構造の一般的な形式は次のようになります。  
  
 navigate(`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ] ] )  
  
 次に例を示します。  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 ここで、OrderCustomer は `relationship`であり、Customer と Order はリレーションシップの `to-end` (顧客) と `from-end` (注文) です。 OrderCustomer が n:1 リレーションシップ、ナビゲーション式の結果型が Ref\<顧客 >。  
  
 この式をより簡略化すると、次のようになります。  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 同様に、クエリでは、次の形式のナビゲーション式は collection < Ref\<順序 >> です。  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 インスタンス式は、エンティティ/参照型になる必要があります。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、NAVIGATE 演算子を使用して、Address エンティティ型と SalesOrderHeader エンティティ型間で確立されたリレーションシップをナビゲートします。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「 [StructuralType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a>関連項目  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [方法: 移動との関係演算子を移動します。](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
