---
title: "System.Object Methods | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5397fca0-689e-443e-802f-e1cbdc866427
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# System.Object Methods
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の <xref:System.Object> メソッドをサポートしています。  
  
|||  
|-|-|  
|<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>|<xref:System.Object.Equals%28System.Object%2CSystem.Object%29?displayProperty=fullName>|  
|<xref:System.Object.ToString?displayProperty=fullName>||  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の <xref:System.Object> メソッドをサポートしていません。  
  
|||  
|-|-|  
|<xref:System.Object.GetHashCode?displayProperty=fullName>|<xref:System.Object.ReferenceEquals%28System.Object%2CSystem.Object%29?displayProperty=fullName>|  
|<xref:System.Object.MemberwiseClone?displayProperty=fullName>|<xref:System.Object.GetType?displayProperty=fullName>|  
|`BINARY`、`VARBINARY`、`IMAGE`、`TIMESTAMP` などのバイナリ型の <xref:System.Object.ToString?displayProperty=fullName>||  
  
## .NET との相違  
 SQL では、double 型に対する <xref:System.Object.ToString?displayProperty=fullName> の出力で、SQL `CONVERT`\(NVARCHAR\(30\), @x, 2\) を使用します。  このとき、SQL は常に 16 桁と指数表記を使用します \(たとえば、0 に対して "0.000000000000000e\+000" を使用\)。  そのため、<xref:System.Object.ToString?displayProperty=fullName> 変換では、.NET Framework 内の <xref:System.Convert.ToString%2A?displayProperty=fullName> と同じ文字列は作成されません。  
  
## 参照  
 [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)