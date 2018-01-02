---
title: "クエリ結果"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5ff674cbbe0a5d52a4bc4b4de55e0ae3c49395d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="query-results"></a><span data-ttu-id="0ea30-102">クエリ結果</span><span class="sxs-lookup"><span data-stu-id="0ea30-102">Query Results</span></span>
<span data-ttu-id="0ea30-103">[!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] クエリをコマンド ツリーに変換して実行すると、通常、次のいずれかの形でクエリの結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="0ea30-103">After a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query is converted to command trees and executed, the query results are usually returned as one of the following:</span></span>  
  
-   <span data-ttu-id="0ea30-104">0 個以上の型指定されたエンティティ オブジェクトのコレクション、または概念モデルの複合型のプロジェクション。</span><span class="sxs-lookup"><span data-stu-id="0ea30-104">A collection of zero or more typed entity objects or a projection of complex types in the conceptual model.</span></span>  
  
-   <span data-ttu-id="0ea30-105">概念モデルでサポートされる CLR 型。</span><span class="sxs-lookup"><span data-stu-id="0ea30-105">CLR types supported by the conceptual model.</span></span>  
  
-   <span data-ttu-id="0ea30-106">インライン コレクション。</span><span class="sxs-lookup"><span data-stu-id="0ea30-106">Inline collections.</span></span>  
  
-   <span data-ttu-id="0ea30-107">匿名型。</span><span class="sxs-lookup"><span data-stu-id="0ea30-107">Anonymous types.</span></span>  
  
 <span data-ttu-id="0ea30-108">データ ソースに対してクエリを実行すると、その結果は CLR 型に具体化されてクライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="0ea30-108">When the query has executed against the data source, the results are materialized into CLR types and returned to the client.</span></span> <span data-ttu-id="0ea30-109">オブジェクトの具体化は、すべて [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="0ea30-109">All object materialization is performed by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="0ea30-110">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] と CLR の間のマッピングができないことが原因でエラーが発生すると、オブジェクトの具体化中に例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0ea30-110">Any errors that result from an inability to map between the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] and the CLR will cause exceptions to be thrown during object materialization.</span></span>  
  
 <span data-ttu-id="0ea30-111">プリミティブ概念モデル型を返すクエリを実行した場合、その結果は、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] から切り離されたスタンドアロンの CLR 型で構成されます。</span><span class="sxs-lookup"><span data-stu-id="0ea30-111">If the query execution returns primitive conceptual model types, the results consist of CLR types that are stand-alone and disconnected from the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="0ea30-112">ただし、クエリが <xref:System.Data.Objects.ObjectQuery%601> によって表されるエンティティ オブジェクトのコレクションを返す場合、これらの型はオブジェクト コンテキストによって追跡されます。</span><span class="sxs-lookup"><span data-stu-id="0ea30-112">However, if the query returns a collection of typed entity objects, represented by <xref:System.Data.Objects.ObjectQuery%601>, those types are tracked by the object context.</span></span> <span data-ttu-id="0ea30-113">すべてのオブジェクトの動作 (子/親のコレクション、変更の追跡、多態性など) で定義されているは、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="0ea30-113">All object behavior (such as child/parent collections, change tracking, polymorphism, and so on) are as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="0ea30-114">この機能は、[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] で定義されるようにその機能の範囲内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ea30-114">This functionality can be used in its capacity, as defined in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="0ea30-115">詳細については、次を参照してください。[オブジェクトの操作](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md)です。</span><span class="sxs-lookup"><span data-stu-id="0ea30-115">For more information, see [Working with Objects](../../../../../../docs/framework/data/adonet/ef/working-with-objects.md).</span></span>  
  
 <span data-ttu-id="0ea30-116">クエリから返される構造型 (匿名型、NULL 値が許容される複合型など) は、`null` 値になります。</span><span class="sxs-lookup"><span data-stu-id="0ea30-116">Struct types returned from queries (such as anonymous types and nullable complex types) can be of `null` value.</span></span> <span data-ttu-id="0ea30-117">返されたエンティティの <xref:System.Data.Objects.DataClasses.EntityCollection%601> プロパティも `null` 値になります。</span><span class="sxs-lookup"><span data-stu-id="0ea30-117">An <xref:System.Data.Objects.DataClasses.EntityCollection%601> property of a returned entity can also be of `null` value.</span></span> <span data-ttu-id="0ea30-118">これは、要素を持たない `null` に対する <xref:System.Linq.Queryable.FirstOrDefault%2A> の呼び出しなど、<xref:System.Data.Objects.ObjectQuery%601> 値になっているエンティティのコレクション プロパティが投影されるためです。</span><span class="sxs-lookup"><span data-stu-id="0ea30-118">This can result from projecting the collection property of an entity that is of `null` value, such as calling <xref:System.Linq.Queryable.FirstOrDefault%2A> on an <xref:System.Data.Objects.ObjectQuery%601> that has no elements.</span></span>  
  
 <span data-ttu-id="0ea30-119">場合によっては、特定のクエリで実行中に具体化された結果が生成されることもありますが、クエリはサーバー上で実行され、CLR でエンティティ オブジェクトが具体化されることはありません。</span><span class="sxs-lookup"><span data-stu-id="0ea30-119">In certain situations, a query might appear to generate a materialized result during its execution, but the query will be executed on the server and the entity object will never be materialized in the CLR.</span></span> <span data-ttu-id="0ea30-120">オブジェクトが具体化された場合、その結果に依存すると、問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0ea30-120">This can cause problems if you are depending on side effects of object materialization.</span></span>  
  
 <span data-ttu-id="0ea30-121">次の例には、`MyContact` プロパティがあるカスタム クラス `LastName` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0ea30-121">The following example contains a custom class, `MyContact`, with a `LastName` property.</span></span> <span data-ttu-id="0ea30-122">`LastName` プロパティを設定すると、`count` 変数が増加します。</span><span class="sxs-lookup"><span data-stu-id="0ea30-122">When the `LastName` property is set, a `count` variable is incremented.</span></span> <span data-ttu-id="0ea30-123">次の 2 つのクエリを実行した場合、最初のクエリによって `count` が増加しますが、2 つ目のクエリでは増加しません。</span><span class="sxs-lookup"><span data-stu-id="0ea30-123">If you execute the two following queries, the first query will increment `count` while the second query will not.</span></span> <span data-ttu-id="0ea30-124">これは、ストアでクエリを実行する必要がないため、2 つ目のクエリで結果から `LastName` プロパティが投影され、`MyContact` クラスが作成されないことが、その理由です。</span><span class="sxs-lookup"><span data-stu-id="0ea30-124">This is because in the second query the `LastName` property is projected from the results and the `MyContact` class is never created, because it is not required to execute the query on the store.</span></span>  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
