---
title: "遅延読み込みと即時読み込み"
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
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 992d9a018f81bbd3f0c9204168f513024769e079
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="deferred-versus-immediate-loading"></a><span data-ttu-id="4d2db-102">遅延読み込みと即時読み込み</span><span class="sxs-lookup"><span data-stu-id="4d2db-102">Deferred versus Immediate Loading</span></span>
<span data-ttu-id="4d2db-103">オブジェクトに対してクエリを実行すると、要求したオブジェクトだけが実際に取得されます。</span><span class="sxs-lookup"><span data-stu-id="4d2db-103">When you query for an object, you actually retrieve only the object you requested.</span></span> <span data-ttu-id="4d2db-104">*関連*オブジェクトは自動的に同時にフェッチされません。</span><span class="sxs-lookup"><span data-stu-id="4d2db-104">The *related* objects are not automatically fetched at the same time.</span></span> <span data-ttu-id="4d2db-105">(詳細については、次を参照してください[リレーションシップ間でクエリを実行する](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md)。)。ただし、関連オブジェクトにアクセスしようとすると、それらを取得する要求が生成されるため、関連オブジェクトがまだ読み込まれていない状態を識別することはできません。</span><span class="sxs-lookup"><span data-stu-id="4d2db-105">(For more information, see [Querying Across Relationships](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).) You cannot see the fact that the related objects are not already loaded, because an attempt to access them produces a request that retrieves them.</span></span>  
  
 <span data-ttu-id="4d2db-106">たとえば、特定の注文のセットを取得するクエリを実行し、ときおり特定の顧客に電子メール通知を送信しようとしているとします。</span><span class="sxs-lookup"><span data-stu-id="4d2db-106">For example, you might want to query for a particular set of orders and then only occasionally send an e-mail notification to particular customers.</span></span> <span data-ttu-id="4d2db-107">最初から注文ごとにすべての顧客データを取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4d2db-107">You would not necessarily need initially to retrieve all customer data with every order.</span></span> <span data-ttu-id="4d2db-108">遅延読み込みを使用すると、関連情報が実際に必要になるまで、その情報の取得を遅らせることができます。</span><span class="sxs-lookup"><span data-stu-id="4d2db-108">You can use deferred loading to defer retrieval of extra information until you absolutely have to.</span></span> <span data-ttu-id="4d2db-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4d2db-109">Consider the following example:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 <span data-ttu-id="4d2db-110">その反対も同様です。</span><span class="sxs-lookup"><span data-stu-id="4d2db-110">The opposite might also be true.</span></span> <span data-ttu-id="4d2db-111">顧客データと注文データを同時に表示する必要のあるアプリケーションがあるとします。</span><span class="sxs-lookup"><span data-stu-id="4d2db-111">You might have an application that has to view customer and order data at the same time.</span></span> <span data-ttu-id="4d2db-112">両方のデータが必要であることがわかっています。</span><span class="sxs-lookup"><span data-stu-id="4d2db-112">You know you need both sets of data.</span></span> <span data-ttu-id="4d2db-113">このアプリケーションでは、結果を取得するのと同時に、各顧客の注文情報が必要になります。</span><span class="sxs-lookup"><span data-stu-id="4d2db-113">You know your application needs order information for each customer as soon as you get the results.</span></span> <span data-ttu-id="4d2db-114">すべての顧客について注文を照会する個別のクエリを発行するのは適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="4d2db-114">You would not want to submit individual queries for orders for every customer.</span></span> <span data-ttu-id="4d2db-115">ここで必要なのは、注文データと顧客データを同時に収集することです。</span><span class="sxs-lookup"><span data-stu-id="4d2db-115">What you really want is to retrieve the order data together with the customers.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 <span data-ttu-id="4d2db-116">1 つのクエリでクロス積によって顧客データと注文データを結合し、すべての関連データを大きな 1 つの投影として取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="4d2db-116">You can also join customers and orders in a query by forming the cross-product and retrieving all the relative bits of data as one large projection.</span></span> <span data-ttu-id="4d2db-117">ただし、このような結果はエンティティではありません </span><span class="sxs-lookup"><span data-stu-id="4d2db-117">But these results are not entities.</span></span> <span data-ttu-id="4d2db-118">(詳細については、次を参照してください。 [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md))。</span><span class="sxs-lookup"><span data-stu-id="4d2db-118">(For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)).</span></span> <span data-ttu-id="4d2db-119">エンティティとは、識別子を持ち、変更が可能なオブジェクトですが、これらの結果は投影であり、変更や永続化はできません。</span><span class="sxs-lookup"><span data-stu-id="4d2db-119">Entities are objects that have identity and that you can modify, whereas these results would be projections that cannot be changed and persisted.</span></span> <span data-ttu-id="4d2db-120">さらに、平坦な結合出力では、注文ごとに各顧客が繰り返し現れるため、余分なデータが大量に取得されることになります。</span><span class="sxs-lookup"><span data-stu-id="4d2db-120">Even worse, you would be retrieving lots of redundant data as each customer repeats for each order in the flattened join output.</span></span>  
  
 <span data-ttu-id="4d2db-121">ここで必要なのは、関連オブジェクトのセットを同時に取得することです。</span><span class="sxs-lookup"><span data-stu-id="4d2db-121">What you really need is a way to retrieve a set of related objects at the same time.</span></span> <span data-ttu-id="4d2db-122">このセットは、目的の用途に必要十分なデータだけを取得できるように、グラフ上に線引きされた区画に相当します。</span><span class="sxs-lookup"><span data-stu-id="4d2db-122">The set is a delineated section of a graph so that you would never be retrieving more or less than was necessary for your intended use.</span></span> <span data-ttu-id="4d2db-123">このため、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]提供<xref:System.Data.Linq.DataLoadOptions>オブジェクト モデルの領域の即時読み込みします。</span><span class="sxs-lookup"><span data-stu-id="4d2db-123">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides <xref:System.Data.Linq.DataLoadOptions> for immediate loading of a region of your object model.</span></span> <span data-ttu-id="4d2db-124">次のメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="4d2db-124">Methods include:</span></span>  
  
-   <span data-ttu-id="4d2db-125"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> メソッド。メイン ターゲットに関連するデータを即時に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="4d2db-125">The  <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method, to immediately load data related to the main target.</span></span>  
  
-   <span data-ttu-id="4d2db-126"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッド。特定のリレーションシップに対して取得されるオブジェクトにフィルターを適用します。</span><span class="sxs-lookup"><span data-stu-id="4d2db-126">The <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method, to filter objects retrieved for a particular relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d2db-127">参照</span><span class="sxs-lookup"><span data-stu-id="4d2db-127">See Also</span></span>  
 [<span data-ttu-id="4d2db-128">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="4d2db-128">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
