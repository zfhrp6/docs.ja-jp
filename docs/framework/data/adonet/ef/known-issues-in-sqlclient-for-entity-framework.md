---
title: "Entity Framework 用の SqlClient の既知の問題 | Microsoft Docs"
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
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Entity Framework 用の SqlClient の既知の問題
ここでは、.NET Framework Data Provider for SQL Server \(SqlClient\) に関連する既知の問題について説明します。  
  
## 文字列関数の末尾のスペース  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] では、文字列値の末尾のスペースは無視されます。  そのため、文字列の末尾にスペースを挿入すると、予期できない結果が生じたり、場合によってはエラーが発生することもあります。  
  
 文字列の末尾にスペースを挿入する必要がある場合は、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] が文字列を切り捨てることがないように、空白文字を挿入することを検討してください。  末尾のスペースが不要である場合は、クエリ パイプラインに渡す前にスペースを削除してください。  
  
## RIGHT 関数  
 `RIGHT(nvarchar(max)`, 0`)` または `RIGHT(varchar(max)`, 0`)` に、最初の引数として `null` 以外の値を、2 番目の引数として 0 を渡すと、`empty` 文字列の代わりに `NULL` 値が返されます。  
  
## CROSS APPLY 演算子および OUTER APPLY 演算子  
 CROSS APPLY 演算子および OUTER APPLY 演算子は [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] で導入されました。  場合によっては、クエリ パイプラインにより、CROSS APPLY 演算子または OUTER APPLY 演算子を含む Transact\-SQL ステートメントが生成されることがあります。  一部のバックエンド プロバイダー \([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] より古いバージョンの [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] など\) では、これらの演算子がサポートされていません。したがって、このようなクエリをこれらのバックエンド プロバイダーで実行することはできません。  
  
 CROSS APPLY 演算子または OUTER APPLY 演算子を含むクエリの生成につながる可能性がある一般的なシナリオを次に示します。  
  
-   ページングを使用した相関サブクエリ  
  
-   相関サブクエリ全体、またはナビゲーションによって生成されたコレクション全体を対象とした `AnyElement`  
  
-   要素セレクターを受け取るグループ化メソッドを使用する LINQ クエリ  
  
-   CROSS APPLY 演算子または OUTER APPLY 演算子が明示的に指定されたクエリ  
  
-   REF コンストラクターを引数に取る DEREF コンストラクターを含むクエリ。  
  
## SKIP 演算子  
 [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] を使用している場合、キー以外の列で ORDER BY と共に SKIP を使用すると、不適切な結果が返されることがあります。  キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。  これは、[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] 用に SKIP が変換される方法によるものです。  たとえば、次のクエリでは、`E.NonKeyColumn` に重複値が存在する場合、5 行を超える行はスキップされます。  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## 適切なバージョンの SQL Server を対象としたクエリの実行  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、SQL Server のバージョンに基づいて実行対象の [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] クエリを決定します。このバージョンは、ストレージ モデル \(.ssdl\) ファイルの Schema 要素の `ProviderManifestToken` 属性で指定されたものです。  このバージョンは、実際に接続する SQL Server のバージョンとは異なる場合があります。  たとえば、使用している SQL Server のバージョンが 2005 であるのに、`ProviderManifestToken` 属性が 2008 に設定されている場合、生成された [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] クエリがサーバーで実行されないことがあります。たとえば、SQL Server 2008 で導入された新しい日時型を使用するクエリは、以前のバージョンの SQL Server では実行されません。  使用している SQL Server のバージョンが 2005 で、`ProviderManifestToken` 属性が 2000 に設定されている場合、生成された [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] クエリが十分に最適化されなかったり、クエリがサポートされていないことを示す例外が発生することがあります。  詳細については、このトピックの「CROSS APPLY 演算子および OUTER APPLY 演算子」を参照してください。  
  
 データベースの一部の動作は、データベースの互換性レベルの設定に依存します。  使用している SQL Server のバージョンが 2005 で、`ProviderManifestToken` 属性が 2005 に、データベースの互換性レベルが "80" \(SQL Server 2000\) に設定されている場合、生成された [!INCLUDE[tsql](../../../../../includes/tsql-md.md)] の実行対象は SQL Server 2005 になりますが、互換性レベルの設定が原因で予期したとおりに実行されないことがあります。  たとえば、ORDER BY リストの列名とセレクターの列名が一致する場合、順序付けが失われることがあります。  
  
## 投影内の入れ子になったクエリ  
 projection 句内の入れ子になったクエリは、サーバーでデカルト積に変換されないことがあります。  SLQ Server などの一部のバックエンド サーバーでは、これによって TempDB テーブルのサイズが非常に大きくなり、  サーバーのパフォーマンスが低下する可能性があります。  
  
 projection 句内の入れ子になったクエリの例を次に示します。  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## サーバー生成の GUID ID 値  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、サーバー生成の GUID 型 ID 値がサポートされますが、プロバイダーは、サーバー生成の ID 値を行の挿入後に返す動作をサポートする必要があります。  [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2005 以降、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] データベース内のサーバー生成 GUID 型を [OUTPUT 句](http://go.microsoft.com/fwlink/?LinkId=169400) で返すことができるようになりました。  
  
## 参照  
 [Entity Framework 用 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)   
 [LINQ to Entities の既知の問題および注意点](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)