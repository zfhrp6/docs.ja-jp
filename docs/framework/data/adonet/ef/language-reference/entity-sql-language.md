---
title: Entity SQL 言語
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: dbc44189634f4548b97647d19465e28ee343635d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="entity-sql-language"></a><span data-ttu-id="2a248-102">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="2a248-102">Entity SQL Language</span></span>
<span data-ttu-id="2a248-103">Entity SQL は、ストレージに依存しない SQL と似たクエリ言語です。</span><span class="sxs-lookup"><span data-stu-id="2a248-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="2a248-104">Entity SQL を使用すると、オブジェクトとして、または表形式でエンティティ データに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="2a248-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="2a248-105">次の場合には Entity SQL の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="2a248-105">You should consider using Entity SQL in the following cases:</span></span>  
  
-   <span data-ttu-id="2a248-106">クエリを実行時に動的に作成する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="2a248-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="2a248-107">その場合、実行時に Entity SQL クエリ文字列を作成する代わりに、<xref:System.Data.Objects.ObjectQuery%601> のクエリ ビルダー メソッドを使用することも検討してください。</span><span class="sxs-lookup"><span data-stu-id="2a248-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
-   <span data-ttu-id="2a248-108">モデル定義の一部としてクエリを定義する場合。</span><span class="sxs-lookup"><span data-stu-id="2a248-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="2a248-109">データ モデルでは Entity SQL のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2a248-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="2a248-110">詳細については、次を参照してください[QueryView 要素 (MSL)。](http://msdn.microsoft.com/library/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span><span class="sxs-lookup"><span data-stu-id="2a248-110">For more information, see [QueryView Element (MSL)](http://msdn.microsoft.com/library/f0426b34-45cb-4fd7-9777-e0570c5e0e80)</span></span>  
  
-   <span data-ttu-id="2a248-111">EntityClient で <xref:System.Data.EntityClient.EntityDataReader> を使用して行セットとして読み取り専用エンティティ データを返す場合。</span><span class="sxs-lookup"><span data-stu-id="2a248-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="2a248-112">詳細については、次を参照してください。 [Entity Framework の EntityClient プロバイダー](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a248-112">For more information, see [EntityClient Provider for the Entity Framework](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>  
  
-   <span data-ttu-id="2a248-113">SQL ベースのクエリ言語に詳しい場合、Entity SQL の使用が最も適切に思われるでしょう。</span><span class="sxs-lookup"><span data-stu-id="2a248-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="2a248-114">Entity SQL と EntityClient プロバイダーの使用</span><span class="sxs-lookup"><span data-stu-id="2a248-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="2a248-115">Entity SQL を EntityClient プロバイダーと一緒に使用する際の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a248-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="2a248-116">Entity Framework 用の EntityClient プロバイダー</span><span class="sxs-lookup"><span data-stu-id="2a248-116">EntityClient Provider for the Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="2a248-117">EntityConnection の接続文字列を作成する方法</span><span class="sxs-lookup"><span data-stu-id="2a248-117">How to: Build an EntityConnection Connection String</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="2a248-118">PrimitiveType 結果を返すクエリの実行方法</span><span class="sxs-lookup"><span data-stu-id="2a248-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="2a248-119">StructuralType 結果を返すクエリの実行方法</span><span class="sxs-lookup"><span data-stu-id="2a248-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="2a248-120">RefType 結果を返すクエリの実行方法</span><span class="sxs-lookup"><span data-stu-id="2a248-120">How to: Execute a Query that Returns RefType Results</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="2a248-121">複合型を返すクエリの実行方法</span><span class="sxs-lookup"><span data-stu-id="2a248-121">How to: Execute a Query that Returns Complex Types</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="2a248-122">入れ子になったコレクションを返すクエリの実行方法</span><span class="sxs-lookup"><span data-stu-id="2a248-122">How to: Execute a Query that Returns Nested Collections</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="2a248-123">EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する方法</span><span class="sxs-lookup"><span data-stu-id="2a248-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="2a248-124">EntityCommand を使用してパラメーター化されたストアド プロシージャを実行する方法</span><span class="sxs-lookup"><span data-stu-id="2a248-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="2a248-125">ポリモーフィック クエリを実行する方法</span><span class="sxs-lookup"><span data-stu-id="2a248-125">How to: Execute a Polymorphic Query</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="2a248-126">Navigate 演算子でリレーションシップをナビゲートする方法</span><span class="sxs-lookup"><span data-stu-id="2a248-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="2a248-127">Entity SQL とオブジェクト クエリの使用</span><span class="sxs-lookup"><span data-stu-id="2a248-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="2a248-128">Entity SQL をオブジェクト クエリと一緒に使用する際の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a248-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="2a248-129">方法: エンティティ型のオブジェクトを返すクエリを実行</span><span class="sxs-lookup"><span data-stu-id="2a248-129">How to: Execute a Query that Returns Entity Type Objects</span></span>](http://msdn.microsoft.com/library/f73e137d-1534-42bb-9e31-99ca42c19b48)  
  
 [<span data-ttu-id="2a248-130">方法: パラメーター化クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="2a248-130">How to: Execute a Parameterized Query</span></span>](http://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)  
  
 [<span data-ttu-id="2a248-131">方法: ナビゲーション プロパティを使用するリレーションシップの移動</span><span class="sxs-lookup"><span data-stu-id="2a248-131">How to: Navigate Relationships Using Navigation Properties</span></span>](http://msdn.microsoft.com/library/b1d71c7d-16a7-4b46-96ac-690176bd5057)  
  
 [<span data-ttu-id="2a248-132">方法: ユーザー定義関数を呼び出す</span><span class="sxs-lookup"><span data-stu-id="2a248-132">How to: Call a User-Defined Function</span></span>](http://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)  
  
 [<span data-ttu-id="2a248-133">方法: データをフィルター処理</span><span class="sxs-lookup"><span data-stu-id="2a248-133">How to: Filter Data</span></span>](http://msdn.microsoft.com/library/776f8556-3350-4572-804a-b1513515c1b2)  
  
 [<span data-ttu-id="2a248-134">方法: データの並べ替え</span><span class="sxs-lookup"><span data-stu-id="2a248-134">How to: Sort Data</span></span>](http://msdn.microsoft.com/library/c05f2506-cb9d-4ebc-822b-300042ad53e7)  
  
 [<span data-ttu-id="2a248-135">方法: データをグループ化</span><span class="sxs-lookup"><span data-stu-id="2a248-135">How to: Group Data</span></span>](http://msdn.microsoft.com/library/df801d9d-9a8a-4157-97a6-5016b18998e1)  
  
 [<span data-ttu-id="2a248-136">方法: データを集計します。</span><span class="sxs-lookup"><span data-stu-id="2a248-136">How to: Aggregate Data</span></span>](http://msdn.microsoft.com/library/4cf04ce8-3c0f-4f88-9d97-8fac8622598d)  
  
 [<span data-ttu-id="2a248-137">方法: 匿名型のオブジェクトを返すクエリを実行</span><span class="sxs-lookup"><span data-stu-id="2a248-137">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/library/3b264025-e911-4d73-90ce-992d2b9d189d)  
  
 [<span data-ttu-id="2a248-138">方法: プリミティブ型のコレクションを返すクエリを実行</span><span class="sxs-lookup"><span data-stu-id="2a248-138">How to: Execute a Query that Returns a Collection of Primitive Types</span></span>](http://msdn.microsoft.com/library/115b52c0-4f27-4253-8991-284b450000b5)  
  
 [<span data-ttu-id="2a248-139">方法: EntityCollection 内の関連オブジェクトをクエリ</span><span class="sxs-lookup"><span data-stu-id="2a248-139">How to: Query Related Objects in an EntityCollection</span></span>](http://msdn.microsoft.com/library/11ce946f-16f8-4c1d-9d80-f740853807ba)  
  
 [<span data-ttu-id="2a248-140">方法: 2 つのクエリの和集合を注文</span><span class="sxs-lookup"><span data-stu-id="2a248-140">How to: Order the Union of Two Queries</span></span>](http://msdn.microsoft.com/library/853c583a-eaba-4400-830d-be974e735313)  
  
 [<span data-ttu-id="2a248-141">方法: 結果をクエリ ページング</span><span class="sxs-lookup"><span data-stu-id="2a248-141">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
  
## <a name="in-this-section"></a><span data-ttu-id="2a248-142">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2a248-142">In This Section</span></span>  
 [<span data-ttu-id="2a248-143">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="2a248-143">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [<span data-ttu-id="2a248-144">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="2a248-144">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="2a248-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a248-145">See Also</span></span>  
 [<span data-ttu-id="2a248-146">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2a248-146">ADO.NET Entity Framework</span></span>](../../../../../../docs/framework/data/adonet/ef/index.md)  
 [<span data-ttu-id="2a248-147">言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="2a248-147">Language Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
