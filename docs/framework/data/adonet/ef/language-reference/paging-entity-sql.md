---
title: "ページング (Entity SQL) | Microsoft Docs"
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
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# ページング (Entity SQL)
物理的なページングは、[ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) 句の [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) サブ句および [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) サブ句を使用して実行できます。  物理的ページングを決定的に実行するには、SKIP と LIMIT を使用する必要があります。  非決定的な方法で結果の行の数を制限するには、[TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md) を使用する必要があります。  TOP および SKIP\/LIMIT は、同時には指定できません。  
  
## TOP の概要  
 SELECT 句には、オプションの ALL\/DISTINCT 修飾子に続けてオプションの TOP サブ句を指定できます。  TOP サブ句は、クエリ結果の先頭から指定した行セットだけを返すよう指定します。  詳細については、「[TOP](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)」を参照してください。  
  
## SKIP\/LIMIT の概要  
 SKIP と LIMIT は ORDER BY 句の一部です。  SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。  たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。  LIMIT 式のサブ句が ORDER BY 句に存在する場合、クエリは並べ替え順序に従って並べ替えられ、結果の行数は LIMIT 式によって制限されます。  たとえば、LIMIT 5 は、結果セットを 5 つのインスタンスまたは行に制限します。  SKIP と LIMIT を同時に使用することはできません。SKIP のみまたは LIMIT のみを ORDER BY 句と一緒に使用できます。  詳細については、次のトピックを参照してください。  
  
-   [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
  
-   [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
  
-   [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)   
 [How to: Page Through Query Results](http://msdn.microsoft.com/ja-jp/ffc0f920-e7de-42e0-9b12-ef356421d030)