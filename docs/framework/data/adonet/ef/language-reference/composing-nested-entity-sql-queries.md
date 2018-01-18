---
title: "入れ子になった Entity SQL クエリの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1946f2b4a2cef8946eb05f995150fafada954d09
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="composing-nested-entity-sql-queries"></a>入れ子になった Entity SQL クエリの作成
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、機能の豊富な関数言語です。 ビルド ブロック[!INCLUDE[esql](../../../../../../includes/esql-md.md)]式を指定します。 従来の SQL とは異なり[!INCLUDE[esql](../../../../../../includes/esql-md.md)]は表形式の結果セットに限定されません。[!INCLUDE[esql](../../../../../../includes/esql-md.md)]リテラル、パラメーター、または入れ子になった式が複雑な式の作成をサポートしています。 式の値は、パラメーター化されたまたは他の式で構成できます。  
  
## <a name="nested-expressions"></a>入れ子になった式  
 入れ子になった式は、その式によって返される型の値が受け入れられる場所であればどこにでも配置できます。 次に例を示します。  
  
```  
-- Returns a hierarchical collection of three elements at top-level.   
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 入れ子になったクエリは、projection 句に配置できます。 次に例を示します。  
  
```  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)   
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)   
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、入れ子になったクエリを次のようにかっこで囲む必要があります。  
  
```  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 次の例では、入れ子内の式に正しく[!INCLUDE[esql](../../../../../../includes/esql-md.md)]:[する方法: 共用体の 2 つのクエリで注文](http://msdn.microsoft.com/en-us/853c583a-eaba-4400-830d-be974e735313)です。  
  
## <a name="nested-queries-in-projection"></a>投影内の入れ子になったクエリ  
 project 句内の入れ子になったクエリは、サーバーでデカルト積に変換されないことがあります。 SLQ Server などの一部のバックエンド サーバーでは、これによって TempDB テーブルのサイズが非常に大きくなり、サーバーのパフォーマンスに悪影響を及ぼす場合があります。  
  
 以下は、このようなクエリの例です。  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>入れ子になったクエリの順序  
 Entity Framework では、入れ子になった式をクエリ内の任意の場所に配置できます。 Entity SQL ではクエリを柔軟に作成できるので、入れ子になったクエリの順序を含むクエリを記述できます。 ただし、入れ子になったクエリの順序は維持されません。  
  
```  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>参照  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
