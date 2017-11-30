---
title: "Entity Framework データ プロバイダーの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6cbb6d4c11c06c1771cb32021c6c148564a6034a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="3aff2-102">Entity Framework データ プロバイダーの作成</span><span class="sxs-lookup"><span data-stu-id="3aff2-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="3aff2-103">ここでは、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 以外のデータ ソースをサポートする [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] プロバイダーの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3aff2-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3aff2-104">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] には、[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] をサポートするプロバイダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3aff2-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="3aff2-105">Entity Framework プロバイダー モデルの概要</span><span class="sxs-lookup"><span data-stu-id="3aff2-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="3aff2-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] はデータベースに依存しません。ADO.NET プロバイダー モデルを使用して、さまざまなデータ ソースに接続するプロバイダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3aff2-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="3aff2-107">ADO.NET データ プロバイダー モデルを使用して構築された Entity Framework データ プロバイダーは、次の機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="3aff2-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="3aff2-108">Entity Data Model (EDM) プリミティブ型をプロバイダー型にマップします。</span><span class="sxs-lookup"><span data-stu-id="3aff2-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="3aff2-109">プロバイダー固有の関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="3aff2-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="3aff2-110">指定された DbQueryCommandTree に対してプロバイダー固有のコマンドを生成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] クエリをサポートします。</span><span class="sxs-lookup"><span data-stu-id="3aff2-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="3aff2-111">指定された DbModificationCommandTree に対してプロバイダー固有の更新コマンドを生成して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] を介した更新をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3aff2-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="3aff2-112">ストア スキーマ定義のマッピング ファイルを公開して、データベースに基づくモデルの生成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3aff2-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="3aff2-113">概念モデルを使用してメタデータ (テーブルとビューなど) を公開します。</span><span class="sxs-lookup"><span data-stu-id="3aff2-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="3aff2-114">![b42a7a5c &#45; 0ac0 &#45; 4911 &#45; 86be &#45; 0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="3aff2-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="3aff2-115">サンプル</span><span class="sxs-lookup"><span data-stu-id="3aff2-115">Sample</span></span>  
 <span data-ttu-id="3aff2-116">参照してください、 [Entity Framework サンプル プロバイダー](http://go.microsoft.com/fwlink/?LinkId=180616)のサンプルについては、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]以外のデータ ソースをサポートするプロバイダー[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="3aff2-116">See the [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3aff2-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3aff2-117">In This Section</span></span>  
 [<span data-ttu-id="3aff2-118">SQL 生成</span><span class="sxs-lookup"><span data-stu-id="3aff2-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="3aff2-119">変更 SQL 生成</span><span class="sxs-lookup"><span data-stu-id="3aff2-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="3aff2-120">プロバイダー マニフェストの仕様</span><span class="sxs-lookup"><span data-stu-id="3aff2-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="3aff2-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3aff2-121">See Also</span></span>  
 [<span data-ttu-id="3aff2-122">データ プロバイダーの操作</span><span class="sxs-lookup"><span data-stu-id="3aff2-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
