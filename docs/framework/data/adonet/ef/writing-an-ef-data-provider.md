---
title: "Entity Framework データ プロバイダーの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Entity Framework データ プロバイダーの作成
このセクションでは、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 以外のデータ ソースをサポートする [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] プロバイダーの作成方法について説明します。[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] には、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] をサポートするプロバイダーが含まれています。  
  
## Entity Framework プロバイダー モデルの概要  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] はデータベースに依存しません。ADO.NET プロバイダー モデルを使用して、さまざまなデータ ソースに接続するプロバイダーを作成できます。  
  
 ADO.NET データ プロバイダー モデルを使用して構築された Entity Framework データ プロバイダーは、次の機能を実行します。  
  
-   Entity Data Model \(EDM\) プリミティブ型をプロバイダー型にマップします。  
  
-   プロバイダー固有の関数を公開します。  
  
-   指定された DbQueryCommandTree に対してプロバイダー固有のコマンドを生成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] クエリをサポートします。  
  
-   指定された DbModificationCommandTree に対してプロバイダー固有の更新コマンドを生成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を介した更新をサポートします。  
  
-   ストア スキーマ定義のマッピング ファイルを公開して、データベースに基づくモデルの生成をサポートします。  
  
-   概念モデルを使用してメタデータ \(テーブルとビューなど\) を公開します。  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c\-0ac0\-4911\-86be\-0460a78760ba")  
  
## サンプル  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 以外のデータ ソースをサポートする [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] プロバイダーのサンプルについては、「[エンティティ フレームワークのサンプル プロバイダー](http://go.microsoft.com/fwlink/?LinkId=180616)」を参照してください。  
  
## このセクションの内容  
 [SQL 生成](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [変更 SQL 生成](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [プロバイダー マニフェストの仕様](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## 参照  
 [データ プロバイダーの操作](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)