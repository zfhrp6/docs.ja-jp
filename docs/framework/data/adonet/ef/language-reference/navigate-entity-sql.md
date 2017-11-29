---
title: NAVIGATE (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6c82149fb5d76ac7b95198ce2b29550eade54b48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="e2b7e-102">NAVIGATE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e2b7e-102">NAVIGATE (Entity SQL)</span></span>
<span data-ttu-id="e2b7e-103">エンティティ間で確立されたリレーションシップをナビゲートします。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-103">Navigates over the relationship established between entities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2b7e-104">構文</span><span class="sxs-lookup"><span data-stu-id="e2b7e-104">Syntax</span></span>  
  
```  
navigate(instance-expresssion, [relationship-type], [to-end [, from-end] ])  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2b7e-105">引数</span><span class="sxs-lookup"><span data-stu-id="e2b7e-105">Arguments</span></span>  
 `instance-expresssion`  
 <span data-ttu-id="e2b7e-106">エンティティのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-106">An instance of an entity.</span></span>  
  
 `relationship-type`  
 <span data-ttu-id="e2b7e-107">概念スキーマ定義言語 (CSDL) ファイルで指定されたリレーションシップの種類の名前。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-107">The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="e2b7e-108">`relationship-type`として修飾\<名前空間 >.\<<namespace>.<relationship type name >。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>  
  
 `to`  
 <span data-ttu-id="e2b7e-109">リレーションシップの終端エンティティ。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-109">The end of the relationship.</span></span>  
  
 `from`  
 <span data-ttu-id="e2b7e-110">リレーションシップの開始エンティティ。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-110">The beginning of the relationship.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2b7e-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="e2b7e-111">Return Value</span></span>  
 <span data-ttu-id="e2b7e-112">終端の基数が 1 の場合、戻り値は `Ref<T>`になります。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="e2b7e-113">終端の基数が n の場合、戻り値は `Collection<Ref<T>>`になります。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2b7e-114">コメント</span><span class="sxs-lookup"><span data-stu-id="e2b7e-114">Remarks</span></span>  
 <span data-ttu-id="e2b7e-115">リレーションシップは、 [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM) における最上位の構造です。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-115">Relationships are first-class constructs in the [!INCLUDE[adonet_edm](../../../../../../includes/adonet-edm-md.md)] (EDM).</span></span> <span data-ttu-id="e2b7e-116">リレーションシップは、複数のエンティティ型の間で確立され、ユーザーはエンティティ間のリレーションシップをナビゲートできます。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="e2b7e-117">`from` と `to` は、リレーションシップ内の名前解決があいまいでない場合の条件付きのオプションです。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>  
  
 <span data-ttu-id="e2b7e-118">NAVIGATE は、O および C 空間で有効です。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-118">NAVIGATE is valid in O and C space.</span></span>  
  
 <span data-ttu-id="e2b7e-119">ナビゲーション構造の一般的な形式は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-119">The general form of a navigation construct is the following:</span></span>  
  
 <span data-ttu-id="e2b7e-120">navigate(`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span><span class="sxs-lookup"><span data-stu-id="e2b7e-120">navigate(`instance-expresssion`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>  
  
 <span data-ttu-id="e2b7e-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-121">For example:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer, Customer, Order)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="e2b7e-122">ここで、OrderCustomer は `relationship`であり、Customer と Order はリレーションシップの `to-end` (顧客) と `from-end` (注文) です。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="e2b7e-123">OrderCustomer が n:1 リレーションシップ、ナビゲーション式の結果型が Ref\<顧客 >。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>  
  
 <span data-ttu-id="e2b7e-124">この式をより簡略化すると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-124">The simpler form of this expression is the following:</span></span>  
  
```  
Select o.Id, navigate(o, OrderCustomer)  
From LOB.Orders as o  
```  
  
 <span data-ttu-id="e2b7e-125">同様に、クエリでは、次の形式のナビゲーション式は collection < Ref\<順序 >> です。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>  
  
```  
Select c.Id, navigate(c, OrderCustomer, Order, Customer)  
From LOB.Customers as c  
```  
  
 <span data-ttu-id="e2b7e-126">インスタンス式は、エンティティ/参照型になる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-126">The instance-expression must be an entity/ref type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2b7e-127">例</span><span class="sxs-lookup"><span data-stu-id="e2b7e-127">Example</span></span>  
 <span data-ttu-id="e2b7e-128">次の Entity SQL クエリでは、NAVIGATE 演算子を使用して、Address エンティティ型と SalesOrderHeader エンティティ型間で確立されたリレーションシップをナビゲートします。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="e2b7e-129">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e2b7e-130">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-130">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e2b7e-131">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e2b7e-132">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]  
  
## <a name="see-also"></a><span data-ttu-id="e2b7e-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2b7e-133">See Also</span></span>  
 [<span data-ttu-id="e2b7e-134">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="e2b7e-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="e2b7e-135">方法: 移動との関係演算子を移動します。</span><span class="sxs-lookup"><span data-stu-id="e2b7e-135">How to: Navigate Relationships with Navigate Operator</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)
