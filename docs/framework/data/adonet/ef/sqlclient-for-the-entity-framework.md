---
title: "Entity Framework 用 SqlClient"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5d6d39-d955-43a5-a5c2-931c239398f1
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e2d95b1c63cf751a694051e5def09e20dd7ab7a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="sqlclient-for-the-entity-framework"></a>Entity Framework 用 SqlClient
このセクションでは、.NET Framework Data Provider for SQL Server (SqlClient) について説明します。これによって、Microsoft SQL Server 上で Entity Framework が機能できるようになります。  
  
## <a name="provider-schema-attribute"></a>Provider スキーマ属性  
 `Provider` は、ストア スキーマ定義言語 (SSDL) の `Schema` 要素の属性です。  
  
 SqlClient を使用するには、文字列 "System.Data.SqlClient" を `Provider` 要素の `Schema` 属性に割り当てます。  
  
## <a name="providermanifesttoken-schema-attribute"></a>ProviderManifestToken スキーマ属性  
 `ProviderManifestToken` は、SSDL の`Schema` 要素の必須の属性です。 このトークンは、オフライン シナリオ用のプロバイダー マニフェストを読み込むために使用されます。 詳細については`ProviderManifestToken`属性は、「[スキーマ要素 (SSDL)](http://msdn.microsoft.com/en-us/fec75ae4-7f16-4421-9265-9dac61509222)です。  
  
 SqlClient は、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] の各バージョンのデータ プロバイダーとして使用できます。 これらのバージョンでは機能が異なります。 たとえば、[!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] では、`varchar(max)` で導入された `nvarchar(max)` 型および [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)] 型をサポートしていません。  
  
 SqlClient は、SQL Server の各バージョンに対応する次のプロバイダー マニフェスト トークンを生成し、受け取ります。  
  
|SQL Server 2000|SQL Server 2005|SQL Server 2008|  
|-|-|-|  
|2000|2005|2008|  
  
> [!NOTE]
>  以降で[!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)]2010、 [ADO.NET Entity Data Model ツール](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)SQL Server 2000 をサポートしていません。  
  
## <a name="provider-namespace-name"></a>プロバイダーの名前空間名  
 すべてのプロバイダーで名前空間を指定する必要があります。 このプロパティによって、型や関数など、プロバイダーが特定のコンストラクターに使用するプレフィックスを Entity Framework に通知できます。 SqlClient プロバイダー マニフェストの名前空間は `SqlServer` です。 名前空間の詳細については、次を参照してください。[名前空間](../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)です。  
  
## <a name="types"></a>種類  
 Entity Framework 用の SqlClient プロバイダーは、概念モデルの型と SQL Server 型の間のマッピング情報を提供します。 詳細については、次を参照してください。 [Entity Framework 用 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)です。  
  
## <a name="functions"></a>関数  
 Entity Framework 用の SqlClient プロバイダーは、プロバイダーがサポートする関数の一覧を定義します。 サポートされている関数の一覧は、次を参照してください。 [Framework 用 SqlClient エンティティ関数](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Entity Framework 用 SqlClient 関数](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)  
  
 [Entity Framework 型用 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md)  
  
 [Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題](../../../../../docs/framework/data/adonet/ef/known-issues-in-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>参照  
 [Entity SQL 言語](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [言語リファレンス](../../../../../docs/framework/data/adonet/ef/language-reference/index.md)  
 [Entity Framework 用の SqlClient プロバイダーに関する既知の問題](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
