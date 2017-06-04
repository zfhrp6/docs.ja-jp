---
title: "HAVING (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b5d52d97-8372-4335-beac-2d0b79dc3707
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# HAVING (Entity SQL)
グループまたは集計の検索条件を指定します。  
  
## 構文  
  
```  
  
[ HAVING search_condition ]  
```  
  
## 引数  
 `search_condition`  
 グループまたは集計の検索条件を指定します。 HAVING 句を GROUP BY ALL と共に使用した場合、HAVING 句により ALL は無効になります。  
  
## 解説  
 HAVING 句は、グループ化の結果について追加的なフィルター処理条件を指定する場合に使用します。 クエリ式で GROUP BY 句が指定されていないと、暗黙的な単独セットのグループになります。  
  
> [!NOTE]
>  HAVING は、[SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md) ステートメントと共にのみ使用できます。[GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) を使用しない場合、HAVING は WHERE 句と同様に動作します。  
  
 GROUP BY 操作後に適用される場合を除いて、HAVING 句は WHERE 句と同様に動作します。 つまり、次の例のように、HAVING 句は別名および集計のグループ化のみを参照できます。  
  
```  
SELECT Name, SUM(o.Price * o.Quantity) AS Total FROM orderLines AS o GROUP BY o.Product AS Name  
HAVING SUM(o.Quantity) > 1  
```  
  
 前述のグループは、複数の製品を含むグループのみに制限されています。  
  
## 使用例  
 次の Entity SQL のクエリでは、HAVING および GROUP BY 操作を使用して、グループまたは集計の検索条件を指定します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1.  「[PrimitiveType 結果を返すクエリの実行方法](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)」の手順に従います。  
  
2.  次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#HAVING](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#having)]  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [クエリ式](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)