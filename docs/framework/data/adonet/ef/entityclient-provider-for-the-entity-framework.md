---
title: "Entity Framework 用の EntityClient プロバイダー | Microsoft Docs"
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
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Entity Framework 用の EntityClient プロバイダー
EntityClient プロバイダーは、概念モデルで記述されているデータにアクセスするために Entity Framework アプリケーションで使用するデータ プロバイダーです。  概念モデルの詳細については、「[モデリングとマッピング](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)」を参照してください。  EntityClient は、他の .NET Framework データ プロバイダーを使用してデータ ソースにアクセスします。  たとえば、EntityClient は、SQL Server データベースにアクセスするときは .NET Framework Data Provider for SQL Server \(SqlClient\) を使用します。  SqlClient プロバイダーの詳細については、「[Entity Framework 用 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)」を参照してください。  EntityClient プロバイダーは <xref:System.Data.EntityClient> 名前空間で実装されます。  
  
## 接続の管理  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、基になるデータ プロバイダーおよびリレーショナル データベースに <xref:System.Data.EntityClient.EntityConnection> を提供することにより、ストレージ固有の [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] データ プロバイダーに基づいて構築されます。  <xref:System.Data.EntityClient.EntityConnection> オブジェクトを構築するには、必要なモデルとマッピング、さらにストレージ固有のデータ プロバイダー名と接続文字列を含んだ一連のメタデータを参照する必要があります。  <xref:System.Data.EntityClient.EntityConnection> を確立すると、概念モデルから生成されたクラスを使用してエンティティにアクセスできます。  
  
 app.config ファイルの接続文字列を指定できます。  
  
 <xref:System.Data.EntityClient> には、<xref:System.Data.EntityClient.EntityConnectionStringBuilder> クラスも含まれています。  このクラスを使用すると、開発者はこのクラスのプロパティおよびメソッドを使用することによって、正しい構文の接続文字列をプログラムで作成し、既存の接続文字列の解析や再作成を行うことができます。  詳細については、「[EntityConnection の接続文字列を作成する方法](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)」を参照してください。  
  
## クエリの作成  
 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 言語は、エンティティの概念スキーマを直接操作し、継承やリレーションシップなどの Entity Data Model 概念をサポートする、ストレージの影響を受けない SQL の言語です。  エンティティ モデルに対して [!INCLUDE[esql](../../../../../includes/esql-md.md)] コマンドを実行するには、<xref:System.Data.EntityClient.EntityCommand> クラスを使用します。  <xref:System.Data.EntityClient.EntityCommand> オブジェクトを構築する場合は、ストアド プロシージャ名またはクエリ テキストを指定できます。  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、ストレージ固有のデータ プロバイダーと連携し、汎用的な [!INCLUDE[esql](../../../../../includes/esql-md.md)] をストレージ固有のクエリに変換します。  [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリ記述の詳細については、「[Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)」を参照してください。  
  
 次の例では、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを作成し、[!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリ テキストを <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=fullName> プロパティに割り当てます。  この [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリは、概念モデルから表示価格で並べ替えた製品を要求します。  次のコードでは、ストレージ モデルが認識されません。  
  
 `EntityCommand cmd = conn.CreateCommand();`  
  
 `cmd.CommandText = @"` `SELECT VALUE p`  
  
 `FROM AdventureWorksEntities.Product AS p`  
  
 `ORDER BY p.ListPrice ";`  
  
## クエリの実行  
 クエリを実行すると、そのクエリが解析され、正規コマンド ツリーに変換されます。  すべての後続の処理は、コマンド ツリーで行われます。  コマンド ツリーは <xref:System.Data.SqlClient> など、<xref:System.Data.EntityClient> と基になる [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] データ プロバイダー間の通信手段です。  
  
 概念モデルに対する <xref:System.Data.EntityClient.EntityCommand> の実行結果は、<xref:System.Data.EntityClient.EntityDataReader> によって公開されます。  <xref:System.Data.EntityClient.EntityDataReader> を返すコマンドを実行するには、<xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> を呼び出します。  <xref:System.Data.EntityClient.EntityDataReader> は、構造化されたさまざまな結果を記述するための <xref:System.Data.IExtendedDataRecord> を実装します。  
  
## トランザクションの管理  
 Entity Framework では、自動トランザクションと明示的トランザクションという 2 つの使用方法があります。  自動トランザクションでは <xref:System.Transactions> 名前空間を使用し、明示的トランザクションでは <xref:System.Data.EntityClient.EntityTransaction> クラスを使用します。  
  
 概念モデル経由で公開されたデータを更新するには、「[How to: Manage Transactions in the Entity Framework](http://msdn.microsoft.com/ja-jp/4a55eb7f-f826-4a48-9df1-aebe2352ebef)」を参照してください。  
  
## このセクションの内容  
 [EntityConnection の接続文字列を作成する方法](../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [PrimitiveType 結果を返すクエリの実行方法](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [StructuralType 結果を返すクエリの実行方法](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [RefType 結果を返すクエリの実行方法](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [複合型を返すクエリの実行方法](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [入れ子になったコレクションを返すクエリの実行方法](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する方法](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する方法](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [ポリモーフィック クエリを実行する方法](../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [Navigate 演算子でリレーションシップをナビゲートする方法](../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## 参照  
 [Managing Connections and Transactions](http://msdn.microsoft.com/ja-jp/b6659d2a-9a45-4e98-acaa-d7a8029e5b99)   
 [ADO.NET Entity Framework](../../../../../docs/framework/data/adonet/ef/index.md)   
 [言語リファレンス](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)