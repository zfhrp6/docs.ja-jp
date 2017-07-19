---
title: "Entity Framework 用 SqlClient | Microsoft Docs"
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
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Entity Framework 用 SqlClient
このセクションでは、.NET Framework Data Provider for SQL Server \(SqlClient\) について説明します。これによって、Microsoft SQL Server 上で Entity Framework が機能できるようになります。  
  
## Provider スキーマ属性  
 `Provider` は、ストア スキーマ定義言語 \(SSDL\) の `Schema` 要素の属性です。  
  
 SqlClient を使用するには、文字列 "System.Data.SqlClient" を `Schema` 要素の `Provider` 属性に割り当てます。  
  
## ProviderManifestToken スキーマ属性  
 `ProviderManifestToken` は、SSDL の`Schema` 要素の必須の属性です。  このトークンは、オフライン シナリオ用のプロバイダー マニフェストを読み込むために使用されます。  `ProviderManifestToken` 属性の詳細については、「[Schema Element \(SSDL\)](http://msdn.microsoft.com/ja-jp/fec75ae4-7f16-4421-9265-9dac61509222)」を参照してください。  
  
 SqlClient は、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] の各バージョンのデータ プロバイダーとして使用できます。  これらのバージョンでは機能が異なります。  たとえば、[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] では、[!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] で導入された `varchar(max)` 型および `nvarchar(max)` 型をサポートしていません。  
  
 SqlClient は、SQL Server の各バージョンに対応する次のプロバイダー マニフェスト トークンを生成し、受け取ります。  
  
||||  
|-|-|-|  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|2000|2005|2008|  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] 2010 以降では、[ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/ja-jp/91076853-0881-421b-837a-f582f36be527) は、SQL Server 2000 をサポートしません。  
  
## プロバイダーの名前空間名  
 すべてのプロバイダーで名前空間を指定する必要があります。  このプロパティによって、型や関数など、プロバイダーが特定のコンストラクターに使用するプレフィックスを Entity Framework に通知できます。  SqlClient プロバイダー マニフェストの名前空間は `SqlServer` です。  名前空間の詳細については、「[名前空間](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)」を参照してください。  
  
## 型  
 Entity Framework 用の SqlClient プロバイダーは、概念モデルの型と SQL Server 型の間のマッピング情報を提供します。  詳細については、「[Entity Framework 用 SqlClient の型](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)」を参照してください。  
  
## 関数  
 Entity Framework 用の SqlClient プロバイダーは、プロバイダーがサポートする関数の一覧を定義します。  サポートされる関数の一覧については、「[Entity Framework 用 SqlClient 関数](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)」を参照してください。  
  
## このセクションの内容  
 [Entity Framework 用 SqlClient 関数](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Entity Framework 用 SqlClient の型](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Entity Framework 用の SqlClient の既知の問題](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## 参照  
 [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)   
 [言語リファレンス](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)   
 [Known Issues in SqlClient Provider for Entity Framework](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)