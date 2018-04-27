---
title: Entity Framework データ プロバイダーの作成
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: cb969589afd4474d9bdfa3a475d8325c1717ab13
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="writing-an-entity-framework-data-provider"></a>Entity Framework データ プロバイダーの作成
このセクションで説明を記述する方法、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server 以外のデータ ソースをサポートするプロバイダー。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server をサポートするプロバイダーが含まれています。  
  
## <a name="introducing-the-entity-framework-provider-model"></a>Entity Framework プロバイダー モデルの概要  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] はデータベースに依存しません。ADO.NET プロバイダー モデルを使用して、さまざまなデータ ソースに接続するプロバイダーを作成できます。  
  
 ADO.NET データ プロバイダー モデルを使用して構築された Entity Framework データ プロバイダーは、次の機能を実行します。  
  
-   Entity Data Model (EDM) プリミティブ型をプロバイダー型にマップします。  
  
-   プロバイダー固有の関数を公開します。  
  
-   指定された DbQueryCommandTree に対してプロバイダー固有のコマンドを生成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] クエリをサポートします。  
  
-   指定された DbModificationCommandTree に対してプロバイダー固有の更新コマンドを生成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を介した更新をサポートします。  
  
-   ストア スキーマ定義のマッピング ファイルを公開して、データベースに基づくモデルの生成をサポートします。  
  
-   概念モデルを使用してメタデータ (テーブルとビューなど) を公開します。  
  
 ![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")  
  
## <a name="sample"></a>サンプル  
 参照してください、 [Entity Framework サンプル プロバイダー](http://go.microsoft.com/fwlink/?LinkId=180616)のサンプルについては、 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] SQL Server 以外のデータ ソースをサポートするプロバイダー。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [SQL 生成](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [変更 SQL 生成](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [プロバイダー マニフェストの仕様](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a>関連項目  
 [データ プロバイダーの操作](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
