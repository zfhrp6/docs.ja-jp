---
title: "System.Math Methods | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# System.Math Methods
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の <xref:System.Math> メソッドをサポートしていません。  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=fullName>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=fullName>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=fullName>  
  
## .NET との相違  
 .NET Framework で使用される丸めセマンティクスは SQL Server とは異なります。  .NET Framework の <xref:System.Math.Round%2A> メソッドは*銀行型丸め*を実行します。銀行型丸めでは、.5 で終わる数値は次の桁に切り上げられるのではなく、最も近い偶数になるように丸められます。  たとえば、2.5 は 2 に丸められ、3.5 は 4 に丸められます   \(この方法は、大規模なデータ トランザクションで、値が大きくなる組織的バイアスの回避に役立ちます\)。  
  
 SQL では、`ROUND` 関数は常に、0 から遠ざかる方向に丸めを実行します。  したがって、2.5 は 3 に丸められます。これは、2 に丸められる .NET Framework とは対照的です。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、SQL の `ROUND` セマンティクスに到達するため、銀行型丸めを実装しようとしません。  
  
## 参照  
 [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)