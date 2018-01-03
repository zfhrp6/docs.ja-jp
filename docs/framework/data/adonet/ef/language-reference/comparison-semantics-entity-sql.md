---
title: "比較セマンティクス (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b36ce28a-2fe4-4236-b782-e5f7c054deae
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2835d2064f1845b55dd3a33abb086c5af0fb9e6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="59f3c-102">比較セマンティクス (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="59f3c-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="59f3c-103">次のいずれかの [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 演算子を実行すると、型インスタンスの比較が行われます。</span><span class="sxs-lookup"><span data-stu-id="59f3c-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="59f3c-104">明示的な比較</span><span class="sxs-lookup"><span data-stu-id="59f3c-104">Explicit comparison</span></span>  
 <span data-ttu-id="59f3c-105">等価演算</span><span class="sxs-lookup"><span data-stu-id="59f3c-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="59f3c-106">!=</span><span class="sxs-lookup"><span data-stu-id="59f3c-106">!=</span></span>  
  
 <span data-ttu-id="59f3c-107">順序付け操作</span><span class="sxs-lookup"><span data-stu-id="59f3c-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="59f3c-108">NULL 値が許容される操作</span><span class="sxs-lookup"><span data-stu-id="59f3c-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="59f3c-109">IS_NULL</span><span class="sxs-lookup"><span data-stu-id="59f3c-109">IS NULL</span></span>  
  
-   <span data-ttu-id="59f3c-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="59f3c-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="59f3c-111">明示的な区別</span><span class="sxs-lookup"><span data-stu-id="59f3c-111">Explicit distinction</span></span>  
 <span data-ttu-id="59f3c-112">等価区別</span><span class="sxs-lookup"><span data-stu-id="59f3c-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="59f3c-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="59f3c-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="59f3c-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="59f3c-114">GROUP BY</span></span>  
  
 <span data-ttu-id="59f3c-115">順序付け区別</span><span class="sxs-lookup"><span data-stu-id="59f3c-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="59f3c-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="59f3c-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="59f3c-117">暗黙的な区別</span><span class="sxs-lookup"><span data-stu-id="59f3c-117">Implicit distinction</span></span>  
 <span data-ttu-id="59f3c-118">設定操作および述語 (等価)</span><span class="sxs-lookup"><span data-stu-id="59f3c-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="59f3c-119">UNION</span><span class="sxs-lookup"><span data-stu-id="59f3c-119">UNION</span></span>  
  
-   <span data-ttu-id="59f3c-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="59f3c-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="59f3c-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="59f3c-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="59f3c-122">SET</span><span class="sxs-lookup"><span data-stu-id="59f3c-122">SET</span></span>  
  
-   <span data-ttu-id="59f3c-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="59f3c-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="59f3c-124">項目述語 (等価)</span><span class="sxs-lookup"><span data-stu-id="59f3c-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="59f3c-125">IN</span><span class="sxs-lookup"><span data-stu-id="59f3c-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="59f3c-126">サポートされている組み合わせ</span><span class="sxs-lookup"><span data-stu-id="59f3c-126">Supported Combinations</span></span>  
 <span data-ttu-id="59f3c-127">次の表は、各種類の型の比較演算子のサポートされているすべての組み合わせを示します。</span><span class="sxs-lookup"><span data-stu-id="59f3c-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="59f3c-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="59f3c-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="59f3c-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="59f3c-129">**!=**</span></span>|<span data-ttu-id="59f3c-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="59f3c-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="59f3c-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="59f3c-131">**DISTINCT**</span></span>|<span data-ttu-id="59f3c-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="59f3c-132">**UNION**</span></span><br /><br /> <span data-ttu-id="59f3c-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="59f3c-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="59f3c-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="59f3c-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="59f3c-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="59f3c-135">**SET**</span></span><br /><br /> <span data-ttu-id="59f3c-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="59f3c-136">**OVERLAPS**</span></span>|<span data-ttu-id="59f3c-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="59f3c-137">**IN**</span></span>|<span data-ttu-id="59f3c-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="59f3c-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="59f3c-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="59f3c-139">**>   >=**</span></span>|<span data-ttu-id="59f3c-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="59f3c-140">**ORDER BY**</span></span>|<span data-ttu-id="59f3c-141">**NULL です。**</span><span class="sxs-lookup"><span data-stu-id="59f3c-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="59f3c-142">**NULL でないです。**</span><span class="sxs-lookup"><span data-stu-id="59f3c-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="59f3c-143">エンティティ型</span><span class="sxs-lookup"><span data-stu-id="59f3c-143">Entity type</span></span>|<span data-ttu-id="59f3c-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="59f3c-145">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="59f3c-146">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="59f3c-147">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="59f3c-148">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-149">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="59f3c-151">複合型</span><span class="sxs-lookup"><span data-stu-id="59f3c-151">Complex type</span></span>|<span data-ttu-id="59f3c-152">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-153">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-154">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-155">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-156">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-157">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-158">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="59f3c-159">行</span><span class="sxs-lookup"><span data-stu-id="59f3c-159">Row</span></span>|<span data-ttu-id="59f3c-160">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="59f3c-161">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="59f3c-162">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="59f3c-163">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-164">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-165">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="59f3c-166">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="59f3c-167">プリミティブ型</span><span class="sxs-lookup"><span data-stu-id="59f3c-167">Primitive type</span></span>|<span data-ttu-id="59f3c-168">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="59f3c-168">Provider-specific</span></span>|<span data-ttu-id="59f3c-169">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="59f3c-169">Provider-specific</span></span>|<span data-ttu-id="59f3c-170">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="59f3c-170">Provider-specific</span></span>|<span data-ttu-id="59f3c-171">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="59f3c-171">Provider-specific</span></span>|<span data-ttu-id="59f3c-172">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="59f3c-172">Provider-specific</span></span>|<span data-ttu-id="59f3c-173">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="59f3c-173">Provider-specific</span></span>|<span data-ttu-id="59f3c-174">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="59f3c-174">Provider-specific</span></span>|  
|<span data-ttu-id="59f3c-175">マルチセット</span><span class="sxs-lookup"><span data-stu-id="59f3c-175">Multiset</span></span>|<span data-ttu-id="59f3c-176">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-177">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-178">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-179">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-180">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-181">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-182">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="59f3c-183">参照</span><span class="sxs-lookup"><span data-stu-id="59f3c-183">Ref</span></span>|<span data-ttu-id="59f3c-184">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="59f3c-185">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="59f3c-186">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="59f3c-187">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="59f3c-188">Throw</span><span class="sxs-lookup"><span data-stu-id="59f3c-188">Throw</span></span>|<span data-ttu-id="59f3c-189">Throw</span><span class="sxs-lookup"><span data-stu-id="59f3c-189">Throw</span></span>|<span data-ttu-id="59f3c-190">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="59f3c-191">関連付け</span><span class="sxs-lookup"><span data-stu-id="59f3c-191">Association</span></span><br /><br /> <span data-ttu-id="59f3c-192">型</span><span class="sxs-lookup"><span data-stu-id="59f3c-192">type</span></span>|<span data-ttu-id="59f3c-193">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-194">Throw</span><span class="sxs-lookup"><span data-stu-id="59f3c-194">Throw</span></span>|<span data-ttu-id="59f3c-195">Throw</span><span class="sxs-lookup"><span data-stu-id="59f3c-195">Throw</span></span>|<span data-ttu-id="59f3c-196">Throw</span><span class="sxs-lookup"><span data-stu-id="59f3c-196">Throw</span></span>|<span data-ttu-id="59f3c-197">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-198">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="59f3c-199">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="59f3c-200"><sup>1</sup>特定のエンティティ型のインスタンスの参照は、暗黙的に比較すると、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="59f3c-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="59f3c-201">エンティティ インスタンスは、明示的な参照に対して比較できません。</span><span class="sxs-lookup"><span data-stu-id="59f3c-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="59f3c-202">明示的な参照に対する比較を行った場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="59f3c-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="59f3c-203">たとえば、次のクエリを実行すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="59f3c-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="59f3c-204"><sup>2</sup>複合型のプロパティが比較可能な (ただし、すべてのプロパティが比較可能な) になるように、ストアに送信される前にフラット化します。</span><span class="sxs-lookup"><span data-stu-id="59f3c-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="59f3c-205">参照してください<sup>4 です。</sup></span><span class="sxs-lookup"><span data-stu-id="59f3c-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="59f3c-206"><sup>3</sup>Entity Framework ランタイムでサポートされていないケースが検出し、プロバイダー/ストアは呼び出されず、意味のある例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="59f3c-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="59f3c-207"><sup>4</sup>試行をすべてのプロパティを比較します。</span><span class="sxs-lookup"><span data-stu-id="59f3c-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="59f3c-208">比較不能な型のプロパティ (text、ntext、image など) がある場合、サーバー例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="59f3c-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="59f3c-209"><sup>5</sup>参照のすべての個々 の要素を比較 (エンティティ セット名およびエンティティ型のすべてのキー プロパティを含む)。</span><span class="sxs-lookup"><span data-stu-id="59f3c-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f3c-210">参照</span><span class="sxs-lookup"><span data-stu-id="59f3c-210">See Also</span></span>  
 [<span data-ttu-id="59f3c-211">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="59f3c-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
