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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c6d22b72e05e6293a7fd3bcf7ddfba6e116e441f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="329e1-102">比較セマンティクス (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="329e1-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="329e1-103">次のいずれかの [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 演算子を実行すると、型インスタンスの比較が行われます。</span><span class="sxs-lookup"><span data-stu-id="329e1-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="329e1-104">明示的な比較</span><span class="sxs-lookup"><span data-stu-id="329e1-104">Explicit comparison</span></span>  
 <span data-ttu-id="329e1-105">等価演算</span><span class="sxs-lookup"><span data-stu-id="329e1-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="329e1-106">!=</span><span class="sxs-lookup"><span data-stu-id="329e1-106">!=</span></span>  
  
 <span data-ttu-id="329e1-107">順序付け操作</span><span class="sxs-lookup"><span data-stu-id="329e1-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="329e1-108">NULL 値が許容される操作</span><span class="sxs-lookup"><span data-stu-id="329e1-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="329e1-109">IS_NULL</span><span class="sxs-lookup"><span data-stu-id="329e1-109">IS NULL</span></span>  
  
-   <span data-ttu-id="329e1-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="329e1-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="329e1-111">明示的な区別</span><span class="sxs-lookup"><span data-stu-id="329e1-111">Explicit distinction</span></span>  
 <span data-ttu-id="329e1-112">等価区別</span><span class="sxs-lookup"><span data-stu-id="329e1-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="329e1-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="329e1-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="329e1-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="329e1-114">GROUP BY</span></span>  
  
 <span data-ttu-id="329e1-115">順序付け区別</span><span class="sxs-lookup"><span data-stu-id="329e1-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="329e1-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="329e1-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="329e1-117">暗黙的な区別</span><span class="sxs-lookup"><span data-stu-id="329e1-117">Implicit distinction</span></span>  
 <span data-ttu-id="329e1-118">設定操作および述語 (等価)</span><span class="sxs-lookup"><span data-stu-id="329e1-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="329e1-119">UNION</span><span class="sxs-lookup"><span data-stu-id="329e1-119">UNION</span></span>  
  
-   <span data-ttu-id="329e1-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="329e1-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="329e1-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="329e1-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="329e1-122">SET</span><span class="sxs-lookup"><span data-stu-id="329e1-122">SET</span></span>  
  
-   <span data-ttu-id="329e1-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="329e1-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="329e1-124">項目述語 (等価)</span><span class="sxs-lookup"><span data-stu-id="329e1-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="329e1-125">IN</span><span class="sxs-lookup"><span data-stu-id="329e1-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="329e1-126">サポートされている組み合わせ</span><span class="sxs-lookup"><span data-stu-id="329e1-126">Supported Combinations</span></span>  
 <span data-ttu-id="329e1-127">次の表は、各種類の型の比較演算子のサポートされているすべての組み合わせを示します。</span><span class="sxs-lookup"><span data-stu-id="329e1-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="329e1-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="329e1-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="329e1-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="329e1-129">**!=**</span></span>|<span data-ttu-id="329e1-130">**GROUP BY**</span><span class="sxs-lookup"><span data-stu-id="329e1-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="329e1-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="329e1-131">**DISTINCT**</span></span>|<span data-ttu-id="329e1-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="329e1-132">**UNION**</span></span><br /><br /> <span data-ttu-id="329e1-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="329e1-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="329e1-134">**EXCEPT**</span><span class="sxs-lookup"><span data-stu-id="329e1-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="329e1-135">**SET**</span><span class="sxs-lookup"><span data-stu-id="329e1-135">**SET**</span></span><br /><br /> <span data-ttu-id="329e1-136">**OVERLAPS**</span><span class="sxs-lookup"><span data-stu-id="329e1-136">**OVERLAPS**</span></span>|<span data-ttu-id="329e1-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="329e1-137">**IN**</span></span>|<span data-ttu-id="329e1-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="329e1-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="329e1-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="329e1-139">**>   >=**</span></span>|<span data-ttu-id="329e1-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="329e1-140">**ORDER BY**</span></span>|<span data-ttu-id="329e1-141">**IS NULL**</span><span class="sxs-lookup"><span data-stu-id="329e1-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="329e1-142">**NULL でないです。**</span><span class="sxs-lookup"><span data-stu-id="329e1-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="329e1-143">エンティティ型</span><span class="sxs-lookup"><span data-stu-id="329e1-143">Entity type</span></span>|<span data-ttu-id="329e1-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="329e1-145">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="329e1-146">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="329e1-147">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="329e1-148">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-149">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="329e1-151">複合型</span><span class="sxs-lookup"><span data-stu-id="329e1-151">Complex type</span></span>|<span data-ttu-id="329e1-152">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-153">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-154">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-155">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-156">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-157">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-158">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="329e1-159">行</span><span class="sxs-lookup"><span data-stu-id="329e1-159">Row</span></span>|<span data-ttu-id="329e1-160">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="329e1-161">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="329e1-162">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="329e1-163">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-164">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-165">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="329e1-166">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="329e1-167">プリミティブ型</span><span class="sxs-lookup"><span data-stu-id="329e1-167">Primitive type</span></span>|<span data-ttu-id="329e1-168">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="329e1-168">Provider-specific</span></span>|<span data-ttu-id="329e1-169">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="329e1-169">Provider-specific</span></span>|<span data-ttu-id="329e1-170">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="329e1-170">Provider-specific</span></span>|<span data-ttu-id="329e1-171">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="329e1-171">Provider-specific</span></span>|<span data-ttu-id="329e1-172">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="329e1-172">Provider-specific</span></span>|<span data-ttu-id="329e1-173">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="329e1-173">Provider-specific</span></span>|<span data-ttu-id="329e1-174">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="329e1-174">Provider-specific</span></span>|  
|<span data-ttu-id="329e1-175">マルチセット</span><span class="sxs-lookup"><span data-stu-id="329e1-175">Multiset</span></span>|<span data-ttu-id="329e1-176">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-177">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-178">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-179">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-180">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-181">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-182">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="329e1-183">参照</span><span class="sxs-lookup"><span data-stu-id="329e1-183">Ref</span></span>|<span data-ttu-id="329e1-184">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="329e1-185">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="329e1-186">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="329e1-187">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="329e1-188">Throw</span><span class="sxs-lookup"><span data-stu-id="329e1-188">Throw</span></span>|<span data-ttu-id="329e1-189">Throw</span><span class="sxs-lookup"><span data-stu-id="329e1-189">Throw</span></span>|<span data-ttu-id="329e1-190">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="329e1-191">関連付け</span><span class="sxs-lookup"><span data-stu-id="329e1-191">Association</span></span><br /><br /> <span data-ttu-id="329e1-192">型</span><span class="sxs-lookup"><span data-stu-id="329e1-192">type</span></span>|<span data-ttu-id="329e1-193">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-194">Throw</span><span class="sxs-lookup"><span data-stu-id="329e1-194">Throw</span></span>|<span data-ttu-id="329e1-195">Throw</span><span class="sxs-lookup"><span data-stu-id="329e1-195">Throw</span></span>|<span data-ttu-id="329e1-196">Throw</span><span class="sxs-lookup"><span data-stu-id="329e1-196">Throw</span></span>|<span data-ttu-id="329e1-197">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-198">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="329e1-199">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="329e1-200"><sup>1</sup>特定のエンティティ型のインスタンスの参照は、暗黙的に比較すると、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="329e1-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="329e1-201">エンティティ インスタンスは、明示的な参照に対して比較できません。</span><span class="sxs-lookup"><span data-stu-id="329e1-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="329e1-202">明示的な参照に対する比較を行った場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="329e1-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="329e1-203">たとえば、次のクエリを実行すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="329e1-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="329e1-204"><sup>2</sup>複合型のプロパティが比較可能な (ただし、すべてのプロパティが比較可能な) になるように、ストアに送信される前にフラット化します。</span><span class="sxs-lookup"><span data-stu-id="329e1-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="329e1-205">参照してください<sup>4 です。</sup></span><span class="sxs-lookup"><span data-stu-id="329e1-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="329e1-206"><sup>3</sup>Entity Framework ランタイムでサポートされていないケースが検出し、プロバイダー/ストアは呼び出されず、意味のある例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="329e1-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="329e1-207"><sup>4</sup>試行をすべてのプロパティを比較します。</span><span class="sxs-lookup"><span data-stu-id="329e1-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="329e1-208">比較不能な型のプロパティ (text、ntext、image など) がある場合、サーバー例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="329e1-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="329e1-209"><sup>5</sup>参照のすべての個々 の要素を比較 (エンティティ セット名およびエンティティ型のすべてのキー プロパティを含む)。</span><span class="sxs-lookup"><span data-stu-id="329e1-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="329e1-210">参照</span><span class="sxs-lookup"><span data-stu-id="329e1-210">See Also</span></span>  
 [<span data-ttu-id="329e1-211">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="329e1-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
