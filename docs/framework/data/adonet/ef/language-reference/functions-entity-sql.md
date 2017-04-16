---
title: "関数 (Entity SQL) | Microsoft Docs"
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
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 関数 (Entity SQL)
Entity SQL では、ユーザー定義関数、正規の関数、およびプロバイダー固有の関数がサポートされています。  ユーザー定義関数は、概念モデルまたはクエリでインラインで指定されます。  詳細については、「[ユーザー定義関数](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)」を参照してください。  
  
 正規の関数は Entity Framework で定義済みであり、データ プロバイダーによってサポートされています。  プロバイダーによってサポートされていない関数を呼び出すと、Entity SQL コマンドは失敗します。  そのため、通常は、プロバイダー固有の名前空間にあるストア固有の関数よりも正規の関数が推奨されます。  詳細については、「[正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)」を参照してください。  
  
 Microsoft SQL クライアント マネージ プロバイダーは、プロバイダー固有の一連の関数を提供しています。  詳細については、「[Entity Framework 用 SqlClient 関数](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)」を参照してください。  
  
## このセクションの内容  
 [ユーザー定義関数](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)  
  
 [関数のオーバーロードの解決方法](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md)  
  
 [集計関数](../../../../../../docs/framework/data/adonet/ef/aggregate-functions-sqlclient-for-entity-framework.md)  
  
## 参照  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)