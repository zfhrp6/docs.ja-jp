---
title: "クエリのリモート実行とローカル実行"
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
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7a794c25e0dd7fd0f7169c31da18ce4d6f085503
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="remote-vs-local-execution"></a><span data-ttu-id="23a28-102">クエリのリモート実行とローカル実行</span><span class="sxs-lookup"><span data-stu-id="23a28-102">Remote vs. Local Execution</span></span>
<span data-ttu-id="23a28-103">クエリは、リモートで実行することも (データベース エンジンによるデータベースに対するクエリの実行)、ローカルに実行することも ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によるローカル キャッシュに対するクエリの実行) できます。</span><span class="sxs-lookup"><span data-stu-id="23a28-103">You can decide to execute your queries either remotely (that is, the database engine executes the query against the database) or locally ([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] executes the query against a local cache).</span></span>  
  
## <a name="remote-execution"></a><span data-ttu-id="23a28-104">リモート実行</span><span class="sxs-lookup"><span data-stu-id="23a28-104">Remote Execution</span></span>  
 <span data-ttu-id="23a28-105">次のクエリがあるとします。</span><span class="sxs-lookup"><span data-stu-id="23a28-105">Consider the following query:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 <span data-ttu-id="23a28-106">データベース内に大量の行がある場合は、小さなサブセットを処理するためにすべての行を取得するのは望ましくありません。</span><span class="sxs-lookup"><span data-stu-id="23a28-106">If your database has thousands of rows of orders, you do not want to retrieve them all to process a small subset.</span></span> <span data-ttu-id="23a28-107">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Data.Linq.EntitySet%601> クラスに <xref:System.Linq.IQueryable> インターフェイスが実装されています。</span><span class="sxs-lookup"><span data-stu-id="23a28-107">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the <xref:System.Data.Linq.EntitySet%601> class implements the <xref:System.Linq.IQueryable> interface.</span></span> <span data-ttu-id="23a28-108">これにより、このようなクエリをリモートで実行することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="23a28-108">This approach makes sure that such queries can be executed remotely.</span></span> <span data-ttu-id="23a28-109">この方法には、次の 2 つの大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="23a28-109">Two major benefits flow from this technique:</span></span>  
  
-   <span data-ttu-id="23a28-110">不要なデータは取得されません。</span><span class="sxs-lookup"><span data-stu-id="23a28-110">Unnecessary data is not retrieved.</span></span>  
  
-   <span data-ttu-id="23a28-111">多くの場合、データベース エンジンによって実行されるクエリは、データベース インデックスの効果でより効率的になります。</span><span class="sxs-lookup"><span data-stu-id="23a28-111">A query executed by the database engine is often more efficient because of the database indexes.</span></span>  
  
## <a name="local-execution"></a><span data-ttu-id="23a28-112">ローカル実行</span><span class="sxs-lookup"><span data-stu-id="23a28-112">Local Execution</span></span>  
 <span data-ttu-id="23a28-113">一方、関連するエンティティ全体をローカル キャッシュに取り込むことが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="23a28-113">In other situations, you might want to have the complete set of related entities in the local cache.</span></span> <span data-ttu-id="23a28-114">この目的から、<xref:System.Data.Linq.EntitySet%601> には、<xref:System.Data.Linq.EntitySet%601.Load%2A> のすべてのメンバーを明示的に読み込む <xref:System.Data.Linq.EntitySet%601> メソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="23a28-114">For this purpose, <xref:System.Data.Linq.EntitySet%601> provides the <xref:System.Data.Linq.EntitySet%601.Load%2A> method to explicitly load all the members of the <xref:System.Data.Linq.EntitySet%601>.</span></span>  
  
 <span data-ttu-id="23a28-115"><xref:System.Data.Linq.EntitySet%601> が既に読み込まれている場合、それ以降のクエリはローカルに実行されます。</span><span class="sxs-lookup"><span data-stu-id="23a28-115">If an <xref:System.Data.Linq.EntitySet%601> is already loaded, subsequent queries are executed locally.</span></span> <span data-ttu-id="23a28-116">この方法は、次の 2 つの点で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="23a28-116">This approach helps in two ways:</span></span>  
  
-   <span data-ttu-id="23a28-117">データ全体をローカルで使用する必要がある場合、または複数回使用する必要がある場合に、リモート クエリおよびそれに伴う待機時間を回避できます。</span><span class="sxs-lookup"><span data-stu-id="23a28-117">If the complete set must be used locally or multiple times, you can avoid remote queries and associated latencies.</span></span>  
  
-   <span data-ttu-id="23a28-118">エンティティ全体をシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="23a28-118">The entity can be serialized as a complete entity.</span></span>  
  
 <span data-ttu-id="23a28-119">次のコードは、ローカル実行を行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="23a28-119">The following code fragment illustrates how local execution can be obtained:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## <a name="comparison"></a><span data-ttu-id="23a28-120">比較</span><span class="sxs-lookup"><span data-stu-id="23a28-120">Comparison</span></span>  
 <span data-ttu-id="23a28-121">この 2 種類の実行方法は、強力なオプションの組み合わせになります。つまり、大規模なコレクションではリモート実行を、小規模なコレクションまたは完全なコレクションが必要な場合はローカル実行を選択できます。</span><span class="sxs-lookup"><span data-stu-id="23a28-121">These two capabilities provide a powerful combination of options: remote execution for large collections and local execution for small collections or where the complete collection is needed.</span></span> <span data-ttu-id="23a28-122">リモート実行は <xref:System.Linq.IQueryable> を使用して実装し、ローカル実行はメモリ内の <xref:System.Collections.Generic.IEnumerable%601> コレクションに対して行います。</span><span class="sxs-lookup"><span data-stu-id="23a28-122">You implement remote execution through <xref:System.Linq.IQueryable>, and local execution against an in-memory <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="23a28-123">ローカル実行を強制する (つまり、 <xref:System.Collections.Generic.IEnumerable%601>) を参照してください[汎用 IEnumerable への型を変換](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md)です。</span><span class="sxs-lookup"><span data-stu-id="23a28-123">To force local execution (that is, <xref:System.Collections.Generic.IEnumerable%601>), see [Convert a Type to a Generic IEnumerable](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).</span></span>  
  
### <a name="queries-against-unordered-sets"></a><span data-ttu-id="23a28-124">順序なしのセットに対するクエリ</span><span class="sxs-lookup"><span data-stu-id="23a28-124">Queries Against Unordered Sets</span></span>  
 <span data-ttu-id="23a28-125">実装するローカル コレクションに重要な違いに注意してください<xref:System.Collections.Generic.List%601>およびコレクションに対して実行されるリモート クエリが*セットを順序なし*リレーショナル データベースにします。</span><span class="sxs-lookup"><span data-stu-id="23a28-125">Note the important difference between a local collection that implements <xref:System.Collections.Generic.List%601> and a collection that provides remote queries executed against *unordered sets* in a relational database.</span></span> <span data-ttu-id="23a28-126">インデックス値を使用するメソッドなど、<xref:System.Collections.Generic.List%601> のメソッドにはリストのセマンティクスが必要ですが、これは通常、順序なしのセットに対するリモート クエリからは得られません。</span><span class="sxs-lookup"><span data-stu-id="23a28-126"><xref:System.Collections.Generic.List%601> methods such as those that use index values require list semantics, which typically cannot be obtained through a remote query against an unordered set.</span></span> <span data-ttu-id="23a28-127">このため、このようなメソッドでは、ローカル実行を可能にするために暗黙的に <xref:System.Data.Linq.EntitySet%601> が読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="23a28-127">For this reason, such methods implicitly load the <xref:System.Data.Linq.EntitySet%601> to allow local execution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23a28-128">参照</span><span class="sxs-lookup"><span data-stu-id="23a28-128">See Also</span></span>  
 [<span data-ttu-id="23a28-129">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="23a28-129">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
