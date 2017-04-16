---
title: "比較セマンティクス (Entity SQL) | Microsoft Docs"
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
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 比較セマンティクス (Entity SQL)
次のいずれかの [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 演算子を実行すると、型インスタンスの比較が行われます。  
  
## 明示的な比較  
 等価演算  
  
-   \=  
  
-   \!\=  
  
 順序付け操作  
  
-   \<  
  
-   \<\=  
  
-   \>  
  
-   \>\=  
  
 NULL 値が許容される操作  
  
-   IS\_NULL  
  
-   IS NOT NULL  
  
## 明示的な区別  
 等価区別  
  
-   DISTINCT  
  
-   GROUP BY  
  
 順序付け区別  
  
-   ORDER BY  
  
## 暗黙的な区別  
 設定操作および述語 \(等価\)  
  
-   UNION  
  
-   INTERSECT  
  
-   EXCEPT  
  
-   SET  
  
-   OVERLAPS  
  
 項目述語 \(等価\)  
  
-   IN  
  
## サポートされている組み合わせ  
 次の表は、各種類の型の比較演算子のサポートされているすべての組み合わせを示します。  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|**種類**|**\=**<br /><br /> **\!\=**|**GROUP BY**<br /><br /> **DISTINCT**|**UNION**<br /><br /> **INTERSECT**<br /><br /> **EXCEPT**<br /><br /> **SET**<br /><br /> **OVERLAPS**|**IN**|**\<   \<\=**<br /><br /> **\>   \>\=**|**ORDER BY**|**IS\_NULL**<br /><br /> **IS NOT NULL**|  
|エンティティ型|参照<sup>1</sup>|すべてのプロパティ<sup>2</sup>|すべてのプロパティ<sup>2</sup>|すべてのプロパティ<sup>2</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|参照<sup>1</sup>|  
|複合型|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
|行|すべてのプロパティ<sup>4</sup>|すべてのプロパティ<sup>4</sup>|すべてのプロパティ<sup>4</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|すべてのプロパティ<sup>4</sup>|スロー<sup>3</sup>|  
|プリミティブ型|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|プロバイダー固有|  
|マルチセット|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
|参照|○<sup>5</sup>|○<sup>5</sup>|○<sup>5</sup>|○<sup>5</sup>|Throw|Throw|○<sup>5</sup>|  
|関連付け<br /><br /> 型|スロー<sup>3</sup>|Throw|Throw|Throw|スロー<sup>3</sup>|スロー<sup>3</sup>|スロー<sup>3</sup>|  
  
 <sup>1</sup>次の例に示すように、エンティティ型インスタンスの参照は暗黙的に比較されます。  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 エンティティ インスタンスは、明示的な参照に対して比較できません。  明示的な参照に対する比較を行った場合は、例外がスローされます。  たとえば、次のクエリを実行すると、例外がスローされます。  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <sup>2</sup>複合型のプロパティは、ストアに送信される前にフラット化されるので、比較が可能になります \(すべてのプロパティが比較可能である場合\)。  <sup>4</sup> も参照してください。  
  
 <sup>3</sup>Entity Framework ランタイムでは、サポートされていないケースが検出され、プロバイダー\/ストアは呼び出されずに、意味のある例外がスローされます。  
  
 <sup>4</sup>すべてのプロパティの比較が試行されます。  比較不能な型のプロパティ \(text、ntext、image など\) がある場合、サーバー例外がスローされることがあります。  
  
 <sup>5</sup>参照のすべての個々の要素 \(エンティティ セット名およびエンティティ型のすべてのキー プロパティを含む\) が比較されます。  
  
## 参照  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)