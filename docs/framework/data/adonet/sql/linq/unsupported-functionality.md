---
title: "Unsupported Functionality | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Unsupported Functionality
LINQ to SQL では、次の SQL 機能は、既存の共通言語ランタイム \(CLR\) および .NET Framework の構成要素の変換からは公開できません。  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     `LIKE` は直接変換によってサポートされませんが、同様の機能が <xref:System.Data.Linq.SqlClient.SqlMethods> クラスにあります。  詳細については、「[M:System.Data.Linq.SqlClient.SqlMethods.Like\(System.String,System.String](assetId:///M:System.Data.Linq.SqlClient.SqlMethods.Like(System.String,System.String?qualifyHint=True&autoUpgrade=True)」を参照してください。  
  
-   `DATEDIFF`  
  
     LINQ to SQL では、`DATEDIFF` のサポートが制限されています。  同様の機能が [SqlMethods](assetId:///T:System.Data.Linq.SqlClient.SqlMethods?qualifyHint=False&autoUpgrade=True) クラスにあります。  
  
-   `ROUND`  
  
     LINQ to SQL では、`ROUND` のサポートが制限されています。  詳細については、「[System.Math Methods](../Topic/System.Math%20Methods.md)」を参照してください。  
  
## 参照  
 [Data Types and Functions](../Topic/Data%20Types%20and%20Functions.md)