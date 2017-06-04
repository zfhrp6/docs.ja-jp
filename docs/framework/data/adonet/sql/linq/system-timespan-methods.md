---
title: "System.TimeSpan Methods | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# System.TimeSpan Methods
<xref:System.TimeSpan?displayProperty=fullName> のメンバー サポートは、使用している .NET Framework と Microsoft SQL Server のバージョンに大きく依存します。  
  
 メソッド、演算子、またはプロパティがサポートされていなければ、LINQ to SQL でメンバーを変換して SQL Server で実行することができません。  それでもこれらのメンバーをコードで使用することはできますが、  クエリが Transact\-SQL に変換される前か、データベースから結果が取得された後で評価する必要があります。  
  
## 以前の制限  
 .NET Framework 3.5 SP1 より前のバージョンの .NET Framework で LINQ to SQL を使用すると、SQL Server のデータベース フィールドを <xref:System.TimeSpan?displayProperty=fullName> にマッピングできません。  ただし、<xref:System.TimeSpan> 値を <xref:System.DateTime> 減算から返したり、リテラル変数またはバインド変数として式に取り込んだりできるため、<xref:System.TimeSpan> の操作はサポートされています。  
  
## サポートされている System.TimeSpan メソッド  
 LINQ to SQL でサポートされている以下のメソッド、演算子、およびプロパティは、LINQ to SQL のクエリで使用できます。  オブジェクト モデルまたは外部マッピング ファイルにマッピングされると、LINQ to SQL クエリ内で <xref:System.TimeSpan?displayProperty=fullName> メンバーの多くを呼び出すことができます。  
  
|サポートされている <xref:System.TimeSpan> メソッド|サポートされている <xref:System.TimeSpan> 演算子|サポートされている <xref:System.TimeSpan> プロパティ|  
|---------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue%2A>|  
  
> [!NOTE]
>  LINQ to SQL で <xref:System.TimeSpan?displayProperty=fullName> を SQL の `TIME` 列にマッピングする機能を使用するには、.NET Framework 3.5 SP1 以降が必要です。  SQL の `TIME` データ型は Microsoft SQL Server 2008 以降でのみ使用可能です。  
  
### 加算と減算  
 加算と減算は、CLR の <xref:System.TimeSpan?displayProperty=fullName> 型ではサポートされていますが、SQL の `TIME` 型ではサポートされていません。  そのため、LINQ to SQL クエリにより、SQL の `TIME` 型にマッピングしたときに加算や減算を試みると、エラーが発生します。  SQL の日付\/時刻型の操作に関するその他の注意点については、「[SQL\-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)」を参照してください。  
  
## 参照  
 [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)   
 [Creating the Object Model](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)   
 [SQL\-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)   
 [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)