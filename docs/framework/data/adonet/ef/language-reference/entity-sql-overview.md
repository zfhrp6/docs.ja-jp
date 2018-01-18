---
title: "Entity SQL の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0bb8120-e709-40a3-ac1e-5520dc47477d
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 37390d97325d6532624cd6ffe14c2d6c37ba2084
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="entity-sql-overview"></a><span data-ttu-id="7ef80-102">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="7ef80-102">Entity SQL Overview</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="7ef80-103"> は、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 内の概念モデルに対するクエリの実行に使用できる SQL に似た言語です。</span><span class="sxs-lookup"><span data-stu-id="7ef80-103"> is a SQL-like language that enables you to query conceptual models in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="7ef80-104">概念モデルでは、データを表すエンティティおよびリレーションシップとしてと[!INCLUDE[esql](../../../../../../includes/esql-md.md)]それらのエンティティとリレーションシップ SQL を使用しているユーザーになじみのある形式のクエリを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="7ef80-104">Conceptual models represent data as entities and relationships, and [!INCLUDE[esql](../../../../../../includes/esql-md.md)] allows you to query those entities and relationships in a format that is familiar to those who have used SQL.</span></span>  
  
 <span data-ttu-id="7ef80-105">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] は、ストレージ固有のデータ プロバイダーと連携し、汎用的な [!INCLUDE[esql](../../../../../../includes/esql-md.md)] をストレージ固有のクエリに変換します。</span><span class="sxs-lookup"><span data-stu-id="7ef80-105">The [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="7ef80-106">EntityClient プロバイダーには、エンティティ モデルに対して [!INCLUDE[esql](../../../../../../includes/esql-md.md)] コマンドを実行し、スカラー結果、結果セット、オブジェクト グラフなど、さまざまなデータ型を返すための手段が用意されています。</span><span class="sxs-lookup"><span data-stu-id="7ef80-106">The EntityClient provider supplies a way to execute an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] command against an entity model and return rich types of data including scalar results, result sets, and object graphs.</span></span> <span data-ttu-id="7ef80-107"><xref:System.Data.EntityClient.EntityCommand> オブジェクトを構築する場合は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] のクエリ文字列を <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> プロパティに割り当てることで、ストアド プロシージャの名前またはクエリのテキストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7ef80-107">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or the text of a query by assigning an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query string to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7ef80-108">EDM に対する <xref:System.Data.EntityClient.EntityDataReader> の実行結果は、<xref:System.Data.EntityClient.EntityCommand> によって公開されます。</span><span class="sxs-lookup"><span data-stu-id="7ef80-108">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against an EDM.</span></span> <span data-ttu-id="7ef80-109"><xref:System.Data.EntityClient.EntityDataReader> を返すコマンドを実行するには、<xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7ef80-109">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span>  
  
 <span data-ttu-id="7ef80-110">EntityClient プロバイダーだけでなく [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] でも、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] を使用して概念モデルに対するクエリを実行し、エンティティ型のインスタンスである厳密に型指定された CLR オブジェクトとしてデータを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="7ef80-110">In addition to the EntityClient provider, the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] enables you to use [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to execute queries against a conceptual model and return data as strongly-typed CLR objects that are instances of entity types.</span></span> <span data-ttu-id="7ef80-111">詳細については、次を参照してください。[オブジェクトの操作](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md)です。</span><span class="sxs-lookup"><span data-stu-id="7ef80-111">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="7ef80-112">ここでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ef80-112">This section provides conceptual information about [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7ef80-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7ef80-113">In This Section</span></span>  
 [<span data-ttu-id="7ef80-114">Entity SQL と Transact-SQL の相違点</span><span class="sxs-lookup"><span data-stu-id="7ef80-114">How Entity SQL Differs from Transact-SQL</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-entity-sql-differs-from-transact-sql.md)  
  
 [<span data-ttu-id="7ef80-115">Entity SQL クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="7ef80-115">Entity SQL Quick Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-quick-reference.md)  
  
 [<span data-ttu-id="7ef80-116">型システム</span><span class="sxs-lookup"><span data-stu-id="7ef80-116">Type System</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-117">型定義</span><span class="sxs-lookup"><span data-stu-id="7ef80-117">Type Definitions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/type-definitions-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-118">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="7ef80-118">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-119">クエリ プランのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="7ef80-119">Query Plan Caching</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-plan-caching-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-120">名前空間</span><span class="sxs-lookup"><span data-stu-id="7ef80-120">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-121">識別子</span><span class="sxs-lookup"><span data-stu-id="7ef80-121">Identifiers</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-122">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7ef80-122">Parameters</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-123">変数</span><span class="sxs-lookup"><span data-stu-id="7ef80-123">Variables</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-124">サポートされていない式</span><span class="sxs-lookup"><span data-stu-id="7ef80-124">Unsupported Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/unsupported-expressions-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-125">リテラル</span><span class="sxs-lookup"><span data-stu-id="7ef80-125">Literals</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-126">NULL リテラルと型推論</span><span class="sxs-lookup"><span data-stu-id="7ef80-126">Null Literals and Type Inference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/null-literals-and-type-inference-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-127">入力文字セット</span><span class="sxs-lookup"><span data-stu-id="7ef80-127">Input Character Set</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/input-character-set-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-128">クエリ式</span><span class="sxs-lookup"><span data-stu-id="7ef80-128">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-129">関数</span><span class="sxs-lookup"><span data-stu-id="7ef80-129">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-130">演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="7ef80-130">Operator Precedence</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/operator-precedence-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-131">ページング</span><span class="sxs-lookup"><span data-stu-id="7ef80-131">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-132">比較セマンティクス</span><span class="sxs-lookup"><span data-stu-id="7ef80-132">Comparison Semantics</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-semantics-entity-sql.md)  
  
 [<span data-ttu-id="7ef80-133">入れ子になった Entity SQL クエリの作成</span><span class="sxs-lookup"><span data-stu-id="7ef80-133">Composing Nested Entity SQL Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/composing-nested-entity-sql-queries.md)  
  
 [<span data-ttu-id="7ef80-134">NULL 値が許容される構造化型</span><span class="sxs-lookup"><span data-stu-id="7ef80-134">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ef80-135">参照</span><span class="sxs-lookup"><span data-stu-id="7ef80-135">See Also</span></span>  
 [<span data-ttu-id="7ef80-136">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="7ef80-136">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="7ef80-137">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="7ef80-137">Entity SQL Language</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)  
 [<span data-ttu-id="7ef80-138">CSDL、SSDL、および MSL 仕様</span><span class="sxs-lookup"><span data-stu-id="7ef80-138">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
