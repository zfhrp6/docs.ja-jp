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
ms.openlocfilehash: f1fd1c21fc4f156bfe7a5abf9f76bd341e2d0f10
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="comparison-semantics-entity-sql"></a><span data-ttu-id="2c541-102">比較セマンティクス (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2c541-102">Comparison Semantics (Entity SQL)</span></span>
<span data-ttu-id="2c541-103">次のいずれかの [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 演算子を実行すると、型インスタンスの比較が行われます。</span><span class="sxs-lookup"><span data-stu-id="2c541-103">Performing any of the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operators involves comparison of type instances:</span></span>  
  
## <a name="explicit-comparison"></a><span data-ttu-id="2c541-104">明示的な比較</span><span class="sxs-lookup"><span data-stu-id="2c541-104">Explicit comparison</span></span>  
 <span data-ttu-id="2c541-105">等価演算</span><span class="sxs-lookup"><span data-stu-id="2c541-105">Equality operations:</span></span>  
  
-   =  
  
-   <span data-ttu-id="2c541-106">!=</span><span class="sxs-lookup"><span data-stu-id="2c541-106">!=</span></span>  
  
 <span data-ttu-id="2c541-107">順序付け操作</span><span class="sxs-lookup"><span data-stu-id="2c541-107">Ordering operations:</span></span>  
  
-   <  
  
-   \<=  
  
-   >  
  
-   \>=  
  
 <span data-ttu-id="2c541-108">NULL 値が許容される操作</span><span class="sxs-lookup"><span data-stu-id="2c541-108">Nullability operations:</span></span>  
  
-   <span data-ttu-id="2c541-109">IS_NULL</span><span class="sxs-lookup"><span data-stu-id="2c541-109">IS NULL</span></span>  
  
-   <span data-ttu-id="2c541-110">IS NOT NULL</span><span class="sxs-lookup"><span data-stu-id="2c541-110">IS NOT NULL</span></span>  
  
## <a name="explicit-distinction"></a><span data-ttu-id="2c541-111">明示的な区別</span><span class="sxs-lookup"><span data-stu-id="2c541-111">Explicit distinction</span></span>  
 <span data-ttu-id="2c541-112">等価区別</span><span class="sxs-lookup"><span data-stu-id="2c541-112">Equality distinction:</span></span>  
  
-   <span data-ttu-id="2c541-113">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="2c541-113">DISTINCT</span></span>  
  
-   <span data-ttu-id="2c541-114">GROUP BY</span><span class="sxs-lookup"><span data-stu-id="2c541-114">GROUP BY</span></span>  
  
 <span data-ttu-id="2c541-115">順序付け区別</span><span class="sxs-lookup"><span data-stu-id="2c541-115">Ordering distinction:</span></span>  
  
-   <span data-ttu-id="2c541-116">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="2c541-116">ORDER BY</span></span>  
  
## <a name="implicit-distinction"></a><span data-ttu-id="2c541-117">暗黙的な区別</span><span class="sxs-lookup"><span data-stu-id="2c541-117">Implicit distinction</span></span>  
 <span data-ttu-id="2c541-118">設定操作および述語 (等価)</span><span class="sxs-lookup"><span data-stu-id="2c541-118">Set operations and predicates (equality):</span></span>  
  
-   <span data-ttu-id="2c541-119">UNION</span><span class="sxs-lookup"><span data-stu-id="2c541-119">UNION</span></span>  
  
-   <span data-ttu-id="2c541-120">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="2c541-120">INTERSECT</span></span>  
  
-   <span data-ttu-id="2c541-121">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="2c541-121">EXCEPT</span></span>  
  
-   <span data-ttu-id="2c541-122">SET</span><span class="sxs-lookup"><span data-stu-id="2c541-122">SET</span></span>  
  
-   <span data-ttu-id="2c541-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="2c541-123">OVERLAPS</span></span>  
  
 <span data-ttu-id="2c541-124">項目述語 (等価)</span><span class="sxs-lookup"><span data-stu-id="2c541-124">Item predicates (equality):</span></span>  
  
-   <span data-ttu-id="2c541-125">IN</span><span class="sxs-lookup"><span data-stu-id="2c541-125">IN</span></span>  
  
## <a name="supported-combinations"></a><span data-ttu-id="2c541-126">サポートされている組み合わせ</span><span class="sxs-lookup"><span data-stu-id="2c541-126">Supported Combinations</span></span>  
 <span data-ttu-id="2c541-127">次の表は、各種類の型の比較演算子のサポートされているすべての組み合わせを示します。</span><span class="sxs-lookup"><span data-stu-id="2c541-127">The following table shows all the supported combinations of comparison operators for each kind of type:</span></span>  
  
|<span data-ttu-id="2c541-128">**Type**</span><span class="sxs-lookup"><span data-stu-id="2c541-128">**Type**</span></span>|**=**<br /><br /> <span data-ttu-id="2c541-129">**!=**</span><span class="sxs-lookup"><span data-stu-id="2c541-129">**!=**</span></span>|<span data-ttu-id="2c541-130">**グループ化**</span><span class="sxs-lookup"><span data-stu-id="2c541-130">**GROUP BY**</span></span><br /><br /> <span data-ttu-id="2c541-131">**DISTINCT**</span><span class="sxs-lookup"><span data-stu-id="2c541-131">**DISTINCT**</span></span>|<span data-ttu-id="2c541-132">**UNION**</span><span class="sxs-lookup"><span data-stu-id="2c541-132">**UNION**</span></span><br /><br /> <span data-ttu-id="2c541-133">**INTERSECT**</span><span class="sxs-lookup"><span data-stu-id="2c541-133">**INTERSECT**</span></span><br /><br /> <span data-ttu-id="2c541-134">**点を除いて**</span><span class="sxs-lookup"><span data-stu-id="2c541-134">**EXCEPT**</span></span><br /><br /> <span data-ttu-id="2c541-135">**設定**</span><span class="sxs-lookup"><span data-stu-id="2c541-135">**SET**</span></span><br /><br /> <span data-ttu-id="2c541-136">**重複しています**</span><span class="sxs-lookup"><span data-stu-id="2c541-136">**OVERLAPS**</span></span>|<span data-ttu-id="2c541-137">**IN**</span><span class="sxs-lookup"><span data-stu-id="2c541-137">**IN**</span></span>|<span data-ttu-id="2c541-138">**<   <=**</span><span class="sxs-lookup"><span data-stu-id="2c541-138">**<   <=**</span></span><br /><br /> <span data-ttu-id="2c541-139">**>   >=**</span><span class="sxs-lookup"><span data-stu-id="2c541-139">**>   >=**</span></span>|<span data-ttu-id="2c541-140">**ORDER BY**</span><span class="sxs-lookup"><span data-stu-id="2c541-140">**ORDER BY**</span></span>|<span data-ttu-id="2c541-141">**NULL です。**</span><span class="sxs-lookup"><span data-stu-id="2c541-141">**IS NULL**</span></span><br /><br /> <span data-ttu-id="2c541-142">**NULL でないです。**</span><span class="sxs-lookup"><span data-stu-id="2c541-142">**IS NOT NULL**</span></span>|  
|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="2c541-143">エンティティ型</span><span class="sxs-lookup"><span data-stu-id="2c541-143">Entity type</span></span>|<span data-ttu-id="2c541-144">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-144">Ref<sup>1</sup></span></span>|<span data-ttu-id="2c541-145">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-145">All properties<sup>2</sup></span></span>|<span data-ttu-id="2c541-146">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-146">All properties<sup>2</sup></span></span>|<span data-ttu-id="2c541-147">すべてのプロパティ<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-147">All properties<sup>2</sup></span></span>|<span data-ttu-id="2c541-148">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-148">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-149">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-149">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-150">Ref<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-150">Ref<sup>1</sup></span></span>|  
|<span data-ttu-id="2c541-151">複合型</span><span class="sxs-lookup"><span data-stu-id="2c541-151">Complex type</span></span>|<span data-ttu-id="2c541-152">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-152">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-153">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-153">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-154">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-154">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-155">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-155">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-156">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-156">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-157">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-157">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-158">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-158">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2c541-159">行</span><span class="sxs-lookup"><span data-stu-id="2c541-159">Row</span></span>|<span data-ttu-id="2c541-160">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-160">All properties<sup>4</sup></span></span>|<span data-ttu-id="2c541-161">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-161">All properties<sup>4</sup></span></span>|<span data-ttu-id="2c541-162">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-162">All properties<sup>4</sup></span></span>|<span data-ttu-id="2c541-163">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-163">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-164">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-164">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-165">すべてのプロパティ<sup>4</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-165">All properties<sup>4</sup></span></span>|<span data-ttu-id="2c541-166">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-166">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2c541-167">プリミティブ型</span><span class="sxs-lookup"><span data-stu-id="2c541-167">Primitive type</span></span>|<span data-ttu-id="2c541-168">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="2c541-168">Provider-specific</span></span>|<span data-ttu-id="2c541-169">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="2c541-169">Provider-specific</span></span>|<span data-ttu-id="2c541-170">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="2c541-170">Provider-specific</span></span>|<span data-ttu-id="2c541-171">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="2c541-171">Provider-specific</span></span>|<span data-ttu-id="2c541-172">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="2c541-172">Provider-specific</span></span>|<span data-ttu-id="2c541-173">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="2c541-173">Provider-specific</span></span>|<span data-ttu-id="2c541-174">プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="2c541-174">Provider-specific</span></span>|  
|<span data-ttu-id="2c541-175">マルチセット</span><span class="sxs-lookup"><span data-stu-id="2c541-175">Multiset</span></span>|<span data-ttu-id="2c541-176">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-176">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-177">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-177">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-178">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-178">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-179">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-179">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-180">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-180">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-181">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-181">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-182">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-182">Throw<sup>3</sup></span></span>|  
|<span data-ttu-id="2c541-183">参照</span><span class="sxs-lookup"><span data-stu-id="2c541-183">Ref</span></span>|<span data-ttu-id="2c541-184">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-184">Yes<sup>5</sup></span></span>|<span data-ttu-id="2c541-185">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-185">Yes<sup>5</sup></span></span>|<span data-ttu-id="2c541-186">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-186">Yes<sup>5</sup></span></span>|<span data-ttu-id="2c541-187">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-187">Yes<sup>5</sup></span></span>|<span data-ttu-id="2c541-188">Throw</span><span class="sxs-lookup"><span data-stu-id="2c541-188">Throw</span></span>|<span data-ttu-id="2c541-189">Throw</span><span class="sxs-lookup"><span data-stu-id="2c541-189">Throw</span></span>|<span data-ttu-id="2c541-190">[はい]<sup>5</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-190">Yes<sup>5</sup></span></span>|  
|<span data-ttu-id="2c541-191">関連付け</span><span class="sxs-lookup"><span data-stu-id="2c541-191">Association</span></span><br /><br /> <span data-ttu-id="2c541-192">型</span><span class="sxs-lookup"><span data-stu-id="2c541-192">type</span></span>|<span data-ttu-id="2c541-193">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-193">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-194">Throw</span><span class="sxs-lookup"><span data-stu-id="2c541-194">Throw</span></span>|<span data-ttu-id="2c541-195">Throw</span><span class="sxs-lookup"><span data-stu-id="2c541-195">Throw</span></span>|<span data-ttu-id="2c541-196">Throw</span><span class="sxs-lookup"><span data-stu-id="2c541-196">Throw</span></span>|<span data-ttu-id="2c541-197">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-197">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-198">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-198">Throw<sup>3</sup></span></span>|<span data-ttu-id="2c541-199">スロー<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-199">Throw<sup>3</sup></span></span>|  
  
 <span data-ttu-id="2c541-200"><sup>1</sup>特定のエンティティ型のインスタンスの参照は、暗黙的に比較すると、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="2c541-200"><sup>1</sup>The references of the given entity type instances are implicitly compared, as shown in the following example:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != p2 OR p1 IS NULL  
```  
  
 <span data-ttu-id="2c541-201">エンティティ インスタンスは、明示的な参照に対して比較できません。</span><span class="sxs-lookup"><span data-stu-id="2c541-201">An entity instance cannot be compared to an explicit reference.</span></span> <span data-ttu-id="2c541-202">明示的な参照に対する比較を行った場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2c541-202">If this is attempted, an exception is thrown.</span></span> <span data-ttu-id="2c541-203">たとえば、次のクエリを実行すると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="2c541-203">For example, the following query will throw an exception:</span></span>  
  
```  
SELECT p1, p2   
FROM AdventureWorksEntities.Product AS p1   
     JOIN AdventureWorksEntities.Product AS p2   
WHERE p1 != REF(p2)  
```  
  
 <span data-ttu-id="2c541-204"><sup>2</sup>複合型のプロパティが比較可能な (ただし、すべてのプロパティが比較可能な) になるように、ストアに送信される前にフラット化します。</span><span class="sxs-lookup"><span data-stu-id="2c541-204"><sup>2</sup>Properties of complex types are flattened out before being sent to the store, so they become comparable (as long as all their properties are comparable).</span></span> <span data-ttu-id="2c541-205">参照してください<sup>4 です。</sup></span><span class="sxs-lookup"><span data-stu-id="2c541-205">Also see <sup>4.</sup></span></span>  
  
 <span data-ttu-id="2c541-206"><sup>3</sup>Entity Framework ランタイムでサポートされていないケースが検出し、プロバイダー/ストアは呼び出されず、意味のある例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="2c541-206"><sup>3</sup>The Entity Framework runtime detects the unsupported case and throws a meaningful exception without engaging the provider/store.</span></span>  
  
 <span data-ttu-id="2c541-207"><sup>4</sup>試行をすべてのプロパティを比較します。</span><span class="sxs-lookup"><span data-stu-id="2c541-207"><sup>4</sup>An attempt is made to compare all properties.</span></span> <span data-ttu-id="2c541-208">比較不能な型のプロパティ (text、ntext、image など) がある場合、サーバー例外がスローされることがあります。</span><span class="sxs-lookup"><span data-stu-id="2c541-208">If there is a property that is of a non-comparable type, such as text, ntext, or image, a server exception might be thrown.</span></span>  
  
 <span data-ttu-id="2c541-209"><sup>5</sup>参照のすべての個々 の要素を比較 (エンティティ セット名およびエンティティ型のすべてのキー プロパティを含む)。</span><span class="sxs-lookup"><span data-stu-id="2c541-209"><sup>5</sup>All individual elements of the references are compared (this includes the entity set name and all the key properties of the entity type).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c541-210">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c541-210">See Also</span></span>  
 [<span data-ttu-id="2c541-211">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="2c541-211">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
