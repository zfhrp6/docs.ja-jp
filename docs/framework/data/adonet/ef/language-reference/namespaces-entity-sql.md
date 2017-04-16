---
title: "名前空間 (Entity SQL) | Microsoft Docs"
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
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 名前空間 (Entity SQL)
型名、エンティティ セット、関数など、グローバル識別子の名前の競合を防ぐために、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] には名前空間が採用されています。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] における名前空間のサポートは、[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] における名前空間のサポートと似ています。  
  
 次の例のように、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、2 とおりの形式で USING 句を指定できます。1 つは略称的な別名を指定する修飾名前空間、もう 1 つは別名を指定しない非修飾名前空間です。  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## 名前解決ルール  
 識別子がローカル スコープ内で解決されない場合、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] はグローバル スコープ \(名前空間\) で名前を検索します。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、まず識別子 \(プレフィックス\) と修飾名前空間の 1 つを照合します。  一致が見つかった場合、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、指定された名前空間で、その識別子の残りの部分を解決しようと試みます。  一致が見つからなかった場合は、例外がスローされます。  
  
 次に、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、すべての \(プロローグに指定された\) 非修飾名前空間から識別子を検索することを試みます。  その識別子が属している名前空間を一意に特定できた場合は、その場所が返されます。  同じ識別子に対して複数の名前空間が見つかった場合は、例外がスローされます。  識別子に対応する名前空間を特定できなかった場合、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、次の例のように、識別子の名前を 1 つ外側のスコープ \(<xref:System.Data.Common.DbCommand> オブジェクトまたは <xref:System.Data.Common.DbConnection> オブジェクト\) に渡します。  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## .NET Framework との違い  
 [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] では、部分修飾名前空間を使用できますが、  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では使用できません。  
  
## ADO.NET の使用法  
 クエリは、ADO.NET の <xref:System.Data.Common.DbCommand> オブジェクトを使用して表されます。  <xref:System.Data.Common.DbCommand> オブジェクトは、<xref:System.Data.Common.DbConnection> オブジェクトに対して構築できます。  名前空間を <xref:System.Data.Common.DbCommand> オブジェクトや <xref:System.Data.Common.DbConnection> オブジェクトの一部として指定することもできます。  [!INCLUDE[esql](../../../../../../includes/esql-md.md)] がクエリ内で識別子を解決できなかった場合、同様のルールに従って、外側の名前空間が調査されます。  
  
## 参照  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)