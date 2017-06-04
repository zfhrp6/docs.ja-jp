---
title: "System.DateTimeOffset Methods | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# System.DateTimeOffset Methods
オブジェクト モデルまたは外部マッピング ファイルにマッピングされると、<xref:System.DateTimeOffset?displayProperty=fullName> メソッド、演算子、プロパティのほとんどを LINQ to SQL のクエリ内から呼び出すことができます。  
  
 サポートされていないメソッドは、`Finalize`、`GetHashCode`、`GetType`、`MemberwiseClone` など、LINQ to SQL クエリ内のコンテキストで意味を持たない <xref:System.Object?displayProperty=fullName> から継承されたメソッドだけです。  これらのメソッドは LINQ to SQL で変換して SQL Server で実行することができないため、サポートされていません。  
  
> [!NOTE]
>  共通言語ランタイム \(CLR\) の <xref:System.DateTimeOffset?displayProperty=fullName> 構造体、およびそれを LINQ to SQL で SQL の `DATETIMEOFFSET` 列にマッピングする機能を使用するには、.NET Framework 3.5 SP1 以降が必要です。  SQL の `DATETIMEOFFSET` 列は、Microsoft SQL Server 2008 以降でのみ使用できます。  
  
## SQLMethods の日付と時刻のメソッド  
 LINQ to SQL では、<xref:System.DateTimeOffset> 構造体で提供されるメソッドの他に、次の表に示すように、日付と時刻を操作する <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=fullName> クラスのメソッドも提供しています。  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## 参照  
 [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)   
 [Creating the Object Model](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)   
 [SQL\-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)