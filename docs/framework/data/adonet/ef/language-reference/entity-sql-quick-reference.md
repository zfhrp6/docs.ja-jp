---
title: "Entity SQL クイック リファレンス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e53dad9e-5e83-426e-abb4-be3e78e3d6dc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 14d666624ac4572956364b3db3fd5ee7aad8799b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="entity-sql-quick-reference"></a><span data-ttu-id="b1539-102">Entity SQL クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="b1539-102">Entity SQL Quick Reference</span></span>
<span data-ttu-id="b1539-103">このトピックでは、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリのクイック リファレンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b1539-103">This topic provides a quick reference to [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries.</span></span> <span data-ttu-id="b1539-104">このトピック内のクエリは、AdventureWorks Sales model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="b1539-104">The queries in this topic are based on the AdventureWorks Sales model.</span></span>  
  
## <a name="literals"></a><span data-ttu-id="b1539-105">リテラル</span><span class="sxs-lookup"><span data-stu-id="b1539-105">Literals</span></span>  
  
### <a name="string"></a><span data-ttu-id="b1539-106">String</span><span class="sxs-lookup"><span data-stu-id="b1539-106">String</span></span>  
 <span data-ttu-id="b1539-107">Unicode と非 Unicode の文字列リテラルがあります。</span><span class="sxs-lookup"><span data-stu-id="b1539-107">There are Unicode and non-Unicode character string literals.</span></span> <span data-ttu-id="b1539-108">Unicode 文字列には n を付けます。たとえば、`N'hello'`です。</span><span class="sxs-lookup"><span data-stu-id="b1539-108">Unicode strings are prepended with N. For example, `N'hello'`.</span></span>  
  
 <span data-ttu-id="b1539-109">非 Unicode 文字列リテラルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b1539-109">The following is an example of a Non-Unicode string literal:</span></span>  
  
```  
'hello'  
--same as  
"hello"  
```  
  
 <span data-ttu-id="b1539-110">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-110">Output:</span></span>  
  
|<span data-ttu-id="b1539-111">値</span><span class="sxs-lookup"><span data-stu-id="b1539-111">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b1539-112">hello</span><span class="sxs-lookup"><span data-stu-id="b1539-112">hello</span></span>|  
  
### <a name="datetime"></a><span data-ttu-id="b1539-113">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1539-113">DateTime</span></span>  
 <span data-ttu-id="b1539-114">DateTime リテラルでは、日付部分と時刻部分の両方が必須です。</span><span class="sxs-lookup"><span data-stu-id="b1539-114">In DateTime literals, both date and time parts are mandatory.</span></span> <span data-ttu-id="b1539-115">既定値はありません。</span><span class="sxs-lookup"><span data-stu-id="b1539-115">There are no default values.</span></span>  
  
 <span data-ttu-id="b1539-116">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-116">Example:</span></span>  
  
```  
DATETIME '2006-12-25 01:01:00.000'   
--same as  
DATETIME '2006-12-25 01:01'  
```  
  
 <span data-ttu-id="b1539-117">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-117">Output:</span></span>  
  
|<span data-ttu-id="b1539-118">値</span><span class="sxs-lookup"><span data-stu-id="b1539-118">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b1539-119">12/25/2006 1:01:00 AM</span><span class="sxs-lookup"><span data-stu-id="b1539-119">12/25/2006 1:01:00 AM</span></span>|  
  
### <a name="integer"></a><span data-ttu-id="b1539-120">整数</span><span class="sxs-lookup"><span data-stu-id="b1539-120">Integer</span></span>  
 <span data-ttu-id="b1539-121">整数リテラルには Int32 (123) 型、UInt32 (123U) 型、Int64 (123L) 型、および UInt64 (123UL) 型があります。</span><span class="sxs-lookup"><span data-stu-id="b1539-121">Integer literals can be of type Int32 (123), UInt32 (123U), Int64 (123L), and UInt64 (123UL).</span></span>  
  
 <span data-ttu-id="b1539-122">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-122">Example:</span></span>  
  
```  
--a collection of integers  
{1, 2, 3}  
```  
  
 <span data-ttu-id="b1539-123">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-123">Output:</span></span>  
  
|<span data-ttu-id="b1539-124">値</span><span class="sxs-lookup"><span data-stu-id="b1539-124">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b1539-125">1</span><span class="sxs-lookup"><span data-stu-id="b1539-125">1</span></span>|  
|<span data-ttu-id="b1539-126">2</span><span class="sxs-lookup"><span data-stu-id="b1539-126">2</span></span>|  
|<span data-ttu-id="b1539-127">3</span><span class="sxs-lookup"><span data-stu-id="b1539-127">3</span></span>|  
  
### <a name="other"></a><span data-ttu-id="b1539-128">その他</span><span class="sxs-lookup"><span data-stu-id="b1539-128">Other</span></span>  
 <span data-ttu-id="b1539-129">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] でサポートされているその他のリテラルは、Guid、Binary、Float/Double、Decimal、および `null` です。</span><span class="sxs-lookup"><span data-stu-id="b1539-129">Other literals supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are Guid, Binary, Float/Double, Decimal, and `null`.</span></span> <span data-ttu-id="b1539-130">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] の NULL リテラルは、概念モデルのその他すべての型と互換性があると見なされます。</span><span class="sxs-lookup"><span data-stu-id="b1539-130">Null literals in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are considered to be compatible with every other type in the conceptual model.</span></span>  
  
## <a name="type-constructors"></a><span data-ttu-id="b1539-131">型コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b1539-131">Type Constructors</span></span>  
  
### <a name="row"></a><span data-ttu-id="b1539-132">ROW</span><span class="sxs-lookup"><span data-stu-id="b1539-132">ROW</span></span>  
 <span data-ttu-id="b1539-133">[行](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md)ように、構造的に型指定された匿名 (レコード) 値を作成します。`ROW(1 AS myNumber, ‘Name’ AS myName).`</span><span class="sxs-lookup"><span data-stu-id="b1539-133">[ROW](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md) constructs an anonymous, structurally-typed (record) value as in: `ROW(1 AS myNumber, ‘Name’ AS myName).`</span></span>  
  
 <span data-ttu-id="b1539-134">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-134">Example:</span></span>  
  
```  
SELECT VALUE row (product.ProductID as ProductID, product.Name   
    as ProductName) FROM AdventureWorksEntities.Product AS product  
```  
  
 <span data-ttu-id="b1539-135">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-135">Output:</span></span>  
  
|<span data-ttu-id="b1539-136">ProductID</span><span class="sxs-lookup"><span data-stu-id="b1539-136">ProductID</span></span>|<span data-ttu-id="b1539-137">名前</span><span class="sxs-lookup"><span data-stu-id="b1539-137">Name</span></span>|  
|---------------|----------|  
|<span data-ttu-id="b1539-138">1</span><span class="sxs-lookup"><span data-stu-id="b1539-138">1</span></span>|<span data-ttu-id="b1539-139">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b1539-139">Adjustable Race</span></span>|  
|<span data-ttu-id="b1539-140">879</span><span class="sxs-lookup"><span data-stu-id="b1539-140">879</span></span>|<span data-ttu-id="b1539-141">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="b1539-141">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b1539-142">712</span><span class="sxs-lookup"><span data-stu-id="b1539-142">712</span></span>|<span data-ttu-id="b1539-143">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b1539-143">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b1539-144">...</span><span class="sxs-lookup"><span data-stu-id="b1539-144">...</span></span>|<span data-ttu-id="b1539-145">...</span><span class="sxs-lookup"><span data-stu-id="b1539-145">...</span></span>|  
  
### <a name="multiset"></a><span data-ttu-id="b1539-146">MULTISET</span><span class="sxs-lookup"><span data-stu-id="b1539-146">MULTISET</span></span>  
 <span data-ttu-id="b1539-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md)など、コレクションを構築します。</span><span class="sxs-lookup"><span data-stu-id="b1539-147">[MULTISET](../../../../../../docs/framework/data/adonet/ef/language-reference/multiset-entity-sql.md) constructs collections, such as:</span></span>  
  
 <span data-ttu-id="b1539-148">`MULTISET(1,2,2,3)``--same as`-`{1,2,2,3}.`</span><span class="sxs-lookup"><span data-stu-id="b1539-148">`MULTISET(1,2,2,3)` `--same as`-`{1,2,2,3}.`</span></span>  
  
 <span data-ttu-id="b1539-149">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-149">Example:</span></span>  
  
```  
SELECT VALUE product FROM AdventureWorksEntities.Product AS product WHERE product.ListPrice IN MultiSet (125, 300)  
```  
  
 <span data-ttu-id="b1539-150">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-150">Output:</span></span>  
  
|<span data-ttu-id="b1539-151">ProductID</span><span class="sxs-lookup"><span data-stu-id="b1539-151">ProductID</span></span>|<span data-ttu-id="b1539-152">名前</span><span class="sxs-lookup"><span data-stu-id="b1539-152">Name</span></span>|<span data-ttu-id="b1539-153">ProductNumber</span><span class="sxs-lookup"><span data-stu-id="b1539-153">ProductNumber</span></span>|<span data-ttu-id="b1539-154">…</span><span class="sxs-lookup"><span data-stu-id="b1539-154">…</span></span>|  
|---------------|----------|-------------------|-------|  
|<span data-ttu-id="b1539-155">842</span><span class="sxs-lookup"><span data-stu-id="b1539-155">842</span></span>|<span data-ttu-id="b1539-156">Touring-Panniers, Large</span><span class="sxs-lookup"><span data-stu-id="b1539-156">Touring-Panniers, Large</span></span>|<span data-ttu-id="b1539-157">PA-T100</span><span class="sxs-lookup"><span data-stu-id="b1539-157">PA-T100</span></span>|<span data-ttu-id="b1539-158">…</span><span class="sxs-lookup"><span data-stu-id="b1539-158">…</span></span>|  
  
### <a name="object"></a><span data-ttu-id="b1539-159">Object</span><span class="sxs-lookup"><span data-stu-id="b1539-159">Object</span></span>  
 <span data-ttu-id="b1539-160">[型コンス トラクターを名前付き](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md)など、(名前付き) のユーザー定義のオブジェクトを構築`person("abc", 12)`です。</span><span class="sxs-lookup"><span data-stu-id="b1539-160">[Named Type Constructor](../../../../../../docs/framework/data/adonet/ef/language-reference/named-type-constructor-entity-sql.md) constructs (named) user-defined objects, such as `person("abc", 12)`.</span></span>  
  
 <span data-ttu-id="b1539-161">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-161">Example:</span></span>  
  
```  
SELECT VALUE AdventureWorksModel.SalesOrderDetail (o.SalesOrderDetailID, o.CarrierTrackingNumber, o.OrderQty,   
o.ProductID, o.SpecialOfferID, o.UnitPrice, o.UnitPriceDiscount,   
o.rowguid, o.ModifiedDate) FROM AdventureWorksEntities.SalesOrderDetail   
AS o  
```  
  
 <span data-ttu-id="b1539-162">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-162">Output:</span></span>  
  
|<span data-ttu-id="b1539-163">SalesOrderDetailID</span><span class="sxs-lookup"><span data-stu-id="b1539-163">SalesOrderDetailID</span></span>|<span data-ttu-id="b1539-164">CarrierTrackingNumber</span><span class="sxs-lookup"><span data-stu-id="b1539-164">CarrierTrackingNumber</span></span>|<span data-ttu-id="b1539-165">OrderQty</span><span class="sxs-lookup"><span data-stu-id="b1539-165">OrderQty</span></span>|<span data-ttu-id="b1539-166">ProductID</span><span class="sxs-lookup"><span data-stu-id="b1539-166">ProductID</span></span>|<span data-ttu-id="b1539-167">...</span><span class="sxs-lookup"><span data-stu-id="b1539-167">...</span></span>|  
|------------------------|---------------------------|--------------|---------------|---------|  
|<span data-ttu-id="b1539-168">1</span><span class="sxs-lookup"><span data-stu-id="b1539-168">1</span></span>|<span data-ttu-id="b1539-169">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="b1539-169">4911-403C-98</span></span>|<span data-ttu-id="b1539-170">1</span><span class="sxs-lookup"><span data-stu-id="b1539-170">1</span></span>|<span data-ttu-id="b1539-171">776</span><span class="sxs-lookup"><span data-stu-id="b1539-171">776</span></span>|<span data-ttu-id="b1539-172">...</span><span class="sxs-lookup"><span data-stu-id="b1539-172">...</span></span>|  
|<span data-ttu-id="b1539-173">2</span><span class="sxs-lookup"><span data-stu-id="b1539-173">2</span></span>|<span data-ttu-id="b1539-174">4911-403C-98</span><span class="sxs-lookup"><span data-stu-id="b1539-174">4911-403C-98</span></span>|<span data-ttu-id="b1539-175">3</span><span class="sxs-lookup"><span data-stu-id="b1539-175">3</span></span>|<span data-ttu-id="b1539-176">777</span><span class="sxs-lookup"><span data-stu-id="b1539-176">777</span></span>|<span data-ttu-id="b1539-177">...</span><span class="sxs-lookup"><span data-stu-id="b1539-177">...</span></span>|  
|<span data-ttu-id="b1539-178">...</span><span class="sxs-lookup"><span data-stu-id="b1539-178">...</span></span>|<span data-ttu-id="b1539-179">...</span><span class="sxs-lookup"><span data-stu-id="b1539-179">...</span></span>|<span data-ttu-id="b1539-180">...</span><span class="sxs-lookup"><span data-stu-id="b1539-180">...</span></span>|<span data-ttu-id="b1539-181">...</span><span class="sxs-lookup"><span data-stu-id="b1539-181">...</span></span>|<span data-ttu-id="b1539-182">...</span><span class="sxs-lookup"><span data-stu-id="b1539-182">...</span></span>|  
  
## <a name="references"></a><span data-ttu-id="b1539-183">参照</span><span class="sxs-lookup"><span data-stu-id="b1539-183">References</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b1539-184">REF</span><span class="sxs-lookup"><span data-stu-id="b1539-184">REF</span></span>  
 <span data-ttu-id="b1539-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)エンティティ型のインスタンスへの参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1539-185">[REF](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md) creates a reference to an entity type instance.</span></span> <span data-ttu-id="b1539-186">たとえば、次のクエリは、Orders エンティティ セットの各 Order エンティティへの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="b1539-186">For example, the following query returns references to each Order entity in the Orders entity set:</span></span>  
  
```  
SELECT REF(o) AS OrderID FROM Orders AS o  
```  
  
 <span data-ttu-id="b1539-187">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-187">Output:</span></span>  
  
|<span data-ttu-id="b1539-188">値</span><span class="sxs-lookup"><span data-stu-id="b1539-188">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b1539-189">1</span><span class="sxs-lookup"><span data-stu-id="b1539-189">1</span></span>|  
|<span data-ttu-id="b1539-190">2</span><span class="sxs-lookup"><span data-stu-id="b1539-190">2</span></span>|  
|<span data-ttu-id="b1539-191">3</span><span class="sxs-lookup"><span data-stu-id="b1539-191">3</span></span>|  
|<span data-ttu-id="b1539-192">...</span><span class="sxs-lookup"><span data-stu-id="b1539-192">...</span></span>|  
  
 <span data-ttu-id="b1539-193">次の例では、プロパティ抽出演算子 (.) を使用して、エンティティのプロパティにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b1539-193">The following example uses the property extraction operator (.) to access a property of an entity.</span></span> <span data-ttu-id="b1539-194">プロパティ抽出演算子を使用すると、参照は自動的に逆参照されます。</span><span class="sxs-lookup"><span data-stu-id="b1539-194">When the property extraction operator is used, the reference is automatically dereferenced.</span></span>  
  
 <span data-ttu-id="b1539-195">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-195">Example:</span></span>  
  
```  
SELECT VALUE REF(p).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="b1539-196">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-196">Output:</span></span>  
  
|<span data-ttu-id="b1539-197">値</span><span class="sxs-lookup"><span data-stu-id="b1539-197">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b1539-198">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b1539-198">Adjustable Race</span></span>|  
|<span data-ttu-id="b1539-199">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="b1539-199">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b1539-200">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b1539-200">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b1539-201">...</span><span class="sxs-lookup"><span data-stu-id="b1539-201">...</span></span>|  
  
### <a name="deref"></a><span data-ttu-id="b1539-202">DEREF</span><span class="sxs-lookup"><span data-stu-id="b1539-202">DEREF</span></span>  
 <span data-ttu-id="b1539-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)を逆参照の参照値し、結果が逆参照を生成します。</span><span class="sxs-lookup"><span data-stu-id="b1539-203">[DEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md) dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="b1539-204">たとえば、次のクエリは、`SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2` のように、Orders エンティティ セットの各 Order について Order エンティティを生成します。</span><span class="sxs-lookup"><span data-stu-id="b1539-204">For example, the following query produces the Order entities for each Order in the Orders entity set: `SELECT DEREF(o2.r) FROM (SELECT REF(o) AS r FROM LOB.Orders AS o) AS o2`..</span></span>  
  
 <span data-ttu-id="b1539-205">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-205">Example:</span></span>  
  
```  
SELECT VALUE DEREF(REF(p)).Name FROM   
    AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="b1539-206">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-206">Output:</span></span>  
  
|<span data-ttu-id="b1539-207">値</span><span class="sxs-lookup"><span data-stu-id="b1539-207">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b1539-208">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b1539-208">Adjustable Race</span></span>|  
|<span data-ttu-id="b1539-209">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="b1539-209">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b1539-210">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b1539-210">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b1539-211">...</span><span class="sxs-lookup"><span data-stu-id="b1539-211">...</span></span>|  
  
### <a name="createref-and-key"></a><span data-ttu-id="b1539-212">CREATEREF と KEY</span><span class="sxs-lookup"><span data-stu-id="b1539-212">CREATEREF AND KEY</span></span>  
 <span data-ttu-id="b1539-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)キーを渡す参照を作成します。</span><span class="sxs-lookup"><span data-stu-id="b1539-213">[CREATEREF](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md) creates a reference passing a key.</span></span> <span data-ttu-id="b1539-214">[キー](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)型参照を持つ式のキー部分を抽出します。</span><span class="sxs-lookup"><span data-stu-id="b1539-214">[KEY](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md) extracts the key portion of an expression with type reference.</span></span>  
  
 <span data-ttu-id="b1539-215">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-215">Example:</span></span>  
  
```  
SELECT VALUE Key(CreateRef(AdventureWorksEntities.Product, row(p.ProductID)))   
    FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="b1539-216">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-216">Output:</span></span>  
  
|<span data-ttu-id="b1539-217">ProductID</span><span class="sxs-lookup"><span data-stu-id="b1539-217">ProductID</span></span>|  
|---------------|  
|<span data-ttu-id="b1539-218">980</span><span class="sxs-lookup"><span data-stu-id="b1539-218">980</span></span>|  
|<span data-ttu-id="b1539-219">365</span><span class="sxs-lookup"><span data-stu-id="b1539-219">365</span></span>|  
|<span data-ttu-id="b1539-220">771</span><span class="sxs-lookup"><span data-stu-id="b1539-220">771</span></span>|  
|<span data-ttu-id="b1539-221">...</span><span class="sxs-lookup"><span data-stu-id="b1539-221">...</span></span>|  
  
## <a name="functions"></a><span data-ttu-id="b1539-222">関数</span><span class="sxs-lookup"><span data-stu-id="b1539-222">Functions</span></span>  
  
### <a name="canonical"></a><span data-ttu-id="b1539-223">正規</span><span class="sxs-lookup"><span data-stu-id="b1539-223">Canonical</span></span>  
 <span data-ttu-id="b1539-224">名前空間を[正規関数](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)としてでは、Edm、`Edm.Length("string")`です。</span><span class="sxs-lookup"><span data-stu-id="b1539-224">The namespace for [canonical functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md) is Edm, as in `Edm.Length("string")`.</span></span> <span data-ttu-id="b1539-225">正規関数と同じ名前の関数を含んでいる別の名前空間がインポートされない限り、名前空間を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b1539-225">You do not have to specify the namespace unless another namespace is imported that contains a function with the same name as a canonical function.</span></span> <span data-ttu-id="b1539-226">2 つの名前空間に同じ関数が存在する場合は、完全な名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1539-226">If two namespaces have the same function, the user should specific the full name.</span></span>  
  
 <span data-ttu-id="b1539-227">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-227">Example:</span></span>  
  
```  
SELECT Length(c. FirstName) As NameLen FROM   
    AdventureWorksEntities.Contact AS c   
    WHERE c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="b1539-228">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-228">Output:</span></span>  
  
|<span data-ttu-id="b1539-229">NameLen</span><span class="sxs-lookup"><span data-stu-id="b1539-229">NameLen</span></span>|  
|-------------|  
|<span data-ttu-id="b1539-230">6</span><span class="sxs-lookup"><span data-stu-id="b1539-230">6</span></span>|  
|<span data-ttu-id="b1539-231">6</span><span class="sxs-lookup"><span data-stu-id="b1539-231">6</span></span>|  
|<span data-ttu-id="b1539-232">5</span><span class="sxs-lookup"><span data-stu-id="b1539-232">5</span></span>|  
  
### <a name="microsoft-provider-specific"></a><span data-ttu-id="b1539-233">Microsoft プロバイダー固有</span><span class="sxs-lookup"><span data-stu-id="b1539-233">Microsoft Provider-Specific</span></span>  
 <span data-ttu-id="b1539-234">[Microsoft プロバイダー固有の関数](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)では、`SqlServer`名前空間。</span><span class="sxs-lookup"><span data-stu-id="b1539-234">[Microsoft provider-specific functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md) are in the `SqlServer` namespace.</span></span>  
  
 <span data-ttu-id="b1539-235">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-235">Example:</span></span>  
  
```  
SELECT SqlServer.LEN(c.EmailAddress) As EmailLen FROM   
    AdventureWorksEntities.Contact AS c WHERE   
    c.ContactID BETWEEN 10 AND 12  
```  
  
 <span data-ttu-id="b1539-236">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-236">Output:</span></span>  
  
|<span data-ttu-id="b1539-237">EmailLen</span><span class="sxs-lookup"><span data-stu-id="b1539-237">EmailLen</span></span>|  
|--------------|  
|<span data-ttu-id="b1539-238">27</span><span class="sxs-lookup"><span data-stu-id="b1539-238">27</span></span>|  
|<span data-ttu-id="b1539-239">27</span><span class="sxs-lookup"><span data-stu-id="b1539-239">27</span></span>|  
|<span data-ttu-id="b1539-240">26</span><span class="sxs-lookup"><span data-stu-id="b1539-240">26</span></span>|  
  
## <a name="namespaces"></a><span data-ttu-id="b1539-241">名前空間</span><span class="sxs-lookup"><span data-stu-id="b1539-241">Namespaces</span></span>  
 <span data-ttu-id="b1539-242">[使用して](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md)クエリ式で使用される名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="b1539-242">[USING](../../../../../../docs/framework/data/adonet/ef/language-reference/using-entity-sql.md) specifies namespaces used in a query expression.</span></span>  
  
 <span data-ttu-id="b1539-243">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-243">Example:</span></span>  
  
```  
using SqlServer; LOWER('AA');  
```  
  
 <span data-ttu-id="b1539-244">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-244">Output:</span></span>  
  
|<span data-ttu-id="b1539-245">値</span><span class="sxs-lookup"><span data-stu-id="b1539-245">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b1539-246">aa</span><span class="sxs-lookup"><span data-stu-id="b1539-246">aa</span></span>|  
  
## <a name="paging"></a><span data-ttu-id="b1539-247">ページング</span><span class="sxs-lookup"><span data-stu-id="b1539-247">Paging</span></span>  
 <span data-ttu-id="b1539-248">ページングを宣言することで表すことができます、 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)と[制限](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)のサブ句、 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)句。</span><span class="sxs-lookup"><span data-stu-id="b1539-248">Paging can be expressed by declaring a [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses to the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span>  
  
 <span data-ttu-id="b1539-249">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-249">Example:</span></span>  
  
```  
SELECT c.ContactID as ID, c.LastName as Name FROM   
    AdventureWorks.Contact AS c ORDER BY c.ContactID SKIP 9 LIMIT 3;  
```  
  
 <span data-ttu-id="b1539-250">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-250">Output:</span></span>  
  
|<span data-ttu-id="b1539-251">ID</span><span class="sxs-lookup"><span data-stu-id="b1539-251">ID</span></span>|<span data-ttu-id="b1539-252">名前</span><span class="sxs-lookup"><span data-stu-id="b1539-252">Name</span></span>|  
|--------|----------|  
|<span data-ttu-id="b1539-253">10</span><span class="sxs-lookup"><span data-stu-id="b1539-253">10</span></span>|<span data-ttu-id="b1539-254">Adina</span><span class="sxs-lookup"><span data-stu-id="b1539-254">Adina</span></span>|  
|<span data-ttu-id="b1539-255">11</span><span class="sxs-lookup"><span data-stu-id="b1539-255">11</span></span>|<span data-ttu-id="b1539-256">Agcaoili</span><span class="sxs-lookup"><span data-stu-id="b1539-256">Agcaoili</span></span>|  
|<span data-ttu-id="b1539-257">12</span><span class="sxs-lookup"><span data-stu-id="b1539-257">12</span></span>|<span data-ttu-id="b1539-258">Aguilar</span><span class="sxs-lookup"><span data-stu-id="b1539-258">Aguilar</span></span>|  
  
## <a name="grouping"></a><span data-ttu-id="b1539-259">グループ化</span><span class="sxs-lookup"><span data-stu-id="b1539-259">Grouping</span></span>  
 <span data-ttu-id="b1539-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md)クエリによって返されるオブジェクトのグループを指定します ([選択](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) を配置する式は、します。</span><span class="sxs-lookup"><span data-stu-id="b1539-260">[GROUPING BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md) specifies groups into which objects returned by a query ([SELECT](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)) expression are to be placed.</span></span>  
  
 <span data-ttu-id="b1539-261">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-261">Example:</span></span>  
  
```  
SELECT VALUE name FROM AdventureWorksEntities.Product as P   
    GROUP BY P.Name HAVING MAX(P.ListPrice) > 5  
```  
  
 <span data-ttu-id="b1539-262">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-262">Output:</span></span>  
  
|<span data-ttu-id="b1539-263">name</span><span class="sxs-lookup"><span data-stu-id="b1539-263">name</span></span>|  
|----------|  
|<span data-ttu-id="b1539-264">LL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="b1539-264">LL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="b1539-265">ML Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="b1539-265">ML Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="b1539-266">HL Mountain Seat Assembly</span><span class="sxs-lookup"><span data-stu-id="b1539-266">HL Mountain Seat Assembly</span></span>|  
|<span data-ttu-id="b1539-267">...</span><span class="sxs-lookup"><span data-stu-id="b1539-267">...</span></span>|  
  
## <a name="navigation"></a><span data-ttu-id="b1539-268">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="b1539-268">Navigation</span></span>  
 <span data-ttu-id="b1539-269">リレーションシップ ナビゲーション操作を使用すると、開始側のエンティティと終了側のエンティティ間のリレーションシップをナビゲートできます。</span><span class="sxs-lookup"><span data-stu-id="b1539-269">The relationship navigation operator allows you to navigate over the relationship from one entity (from end) to another (to end).</span></span> <span data-ttu-id="b1539-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md)として修飾されるリレーションシップ型では\<名前空間 >.\<<namespace>.<relationship type name >。</span><span class="sxs-lookup"><span data-stu-id="b1539-270">[NAVIGATE](../../../../../../docs/framework/data/adonet/ef/language-reference/navigate-entity-sql.md) takes the relationship type qualified as \<namespace>.\<relationship type name>.</span></span> <span data-ttu-id="b1539-271">移動 Ref を返します\<T > 場合の基数、終了するは 1 です。</span><span class="sxs-lookup"><span data-stu-id="b1539-271">Navigate returns Ref\<T> if the cardinality of the to end is 1.</span></span> <span data-ttu-id="b1539-272">場合の基数、終了が n、コレクション < Ref\<T >> が返されます。</span><span class="sxs-lookup"><span data-stu-id="b1539-272">If the cardinality of the to end is n, the Collection<Ref\<T>> will be returned.</span></span>  
  
 <span data-ttu-id="b1539-273">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-273">Example:</span></span>  
  
```  
SELECT a.AddressID, (SELECT VALUE DEREF(v) FROM   
    NAVIGATE(a, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS v)   
    FROM AdventureWorksEntities.Address AS a  
```  
  
 <span data-ttu-id="b1539-274">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-274">Output:</span></span>  
  
|<span data-ttu-id="b1539-275">AddressID</span><span class="sxs-lookup"><span data-stu-id="b1539-275">AddressID</span></span>|  
|---------------|  
|<span data-ttu-id="b1539-276">1</span><span class="sxs-lookup"><span data-stu-id="b1539-276">1</span></span>|  
|<span data-ttu-id="b1539-277">2</span><span class="sxs-lookup"><span data-stu-id="b1539-277">2</span></span>|  
|<span data-ttu-id="b1539-278">3</span><span class="sxs-lookup"><span data-stu-id="b1539-278">3</span></span>|  
|<span data-ttu-id="b1539-279">...</span><span class="sxs-lookup"><span data-stu-id="b1539-279">...</span></span>|  
  
## <a name="select-value-and-select"></a><span data-ttu-id="b1539-280">SELECT VALUE AND SELECT</span><span class="sxs-lookup"><span data-stu-id="b1539-280">SELECT VALUE AND SELECT</span></span>  
  
### <a name="select-value"></a><span data-ttu-id="b1539-281">SELECT VALUE</span><span class="sxs-lookup"><span data-stu-id="b1539-281">SELECT VALUE</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b1539-282"> には、暗黙の行の構築をスキップする SELECT VALUE 句が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b1539-282"> provides the SELECT VALUE clause to skip the implicit row construction.</span></span> <span data-ttu-id="b1539-283">SELECT VALUE 句には 1 つの項目のみを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b1539-283">Only one item can be specified in a SELECT VALUE clause.</span></span> <span data-ttu-id="b1539-284">このような句を使用して、row ラッパーは構築されず、SELECT 句内の項目と、コレクション、目的の構造を作成できます、たとえば:`SELECT VALUE a`です。</span><span class="sxs-lookup"><span data-stu-id="b1539-284">When such a clause is used, no row wrapper is constructed around the items in the SELECT clause, and a collection of the desired shape can be produced, for example: `SELECT VALUE a`.</span></span>  
  
 <span data-ttu-id="b1539-285">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-285">Example:</span></span>  
  
```  
SELECT VALUE p.Name FROM AdventureWorksEntities.Product as p  
```  
  
 <span data-ttu-id="b1539-286">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-286">Output:</span></span>  
  
|<span data-ttu-id="b1539-287">名前</span><span class="sxs-lookup"><span data-stu-id="b1539-287">Name</span></span>|  
|----------|  
|<span data-ttu-id="b1539-288">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b1539-288">Adjustable Race</span></span>|  
|<span data-ttu-id="b1539-289">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="b1539-289">All-Purpose Bike Stand</span></span>|  
|<span data-ttu-id="b1539-290">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b1539-290">AWC Logo Cap</span></span>|  
|<span data-ttu-id="b1539-291">...</span><span class="sxs-lookup"><span data-stu-id="b1539-291">...</span></span>|  
  
### <a name="select"></a><span data-ttu-id="b1539-292">SELECT</span><span class="sxs-lookup"><span data-stu-id="b1539-292">SELECT</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b1539-293"> には、任意の行を構築するための行コンストラクターも用意されています。</span><span class="sxs-lookup"><span data-stu-id="b1539-293"> also provides the row constructor to construct arbitrary rows.</span></span> <span data-ttu-id="b1539-294">SELECT は、投影内の 1 つまたは複数の要素、および `SELECT a, b, c` などのフィールドを持つデータ レコードの結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="b1539-294">SELECT takes one or more elements in the projection and results in a data record with fields, for example: `SELECT a, b, c`.</span></span>  
  
 <span data-ttu-id="b1539-295">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-295">Example:</span></span>  
  
 <span data-ttu-id="b1539-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-296">SELECT p.Name, p.ProductID FROM AdventureWorksEntities.Product as p Output:</span></span>  
  
|<span data-ttu-id="b1539-297">名前</span><span class="sxs-lookup"><span data-stu-id="b1539-297">Name</span></span>|<span data-ttu-id="b1539-298">ProductID</span><span class="sxs-lookup"><span data-stu-id="b1539-298">ProductID</span></span>|  
|----------|---------------|  
|<span data-ttu-id="b1539-299">Adjustable Race</span><span class="sxs-lookup"><span data-stu-id="b1539-299">Adjustable Race</span></span>|<span data-ttu-id="b1539-300">1</span><span class="sxs-lookup"><span data-stu-id="b1539-300">1</span></span>|  
|<span data-ttu-id="b1539-301">All-Purpose Bike Stand</span><span class="sxs-lookup"><span data-stu-id="b1539-301">All-Purpose Bike Stand</span></span>|<span data-ttu-id="b1539-302">879</span><span class="sxs-lookup"><span data-stu-id="b1539-302">879</span></span>|  
|<span data-ttu-id="b1539-303">AWC Logo Cap</span><span class="sxs-lookup"><span data-stu-id="b1539-303">AWC Logo Cap</span></span>|<span data-ttu-id="b1539-304">712</span><span class="sxs-lookup"><span data-stu-id="b1539-304">712</span></span>|  
|<span data-ttu-id="b1539-305">...</span><span class="sxs-lookup"><span data-stu-id="b1539-305">...</span></span>|<span data-ttu-id="b1539-306">...</span><span class="sxs-lookup"><span data-stu-id="b1539-306">...</span></span>|  
  
## <a name="case-expression"></a><span data-ttu-id="b1539-307">CASE 式</span><span class="sxs-lookup"><span data-stu-id="b1539-307">CASE EXPRESSION</span></span>  
 <span data-ttu-id="b1539-308">[Case 式](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)結果を決定するブール式のセットを評価します。</span><span class="sxs-lookup"><span data-stu-id="b1539-308">The [case expression](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md) evaluates a set of Boolean expressions to determine the result.</span></span>  
  
 <span data-ttu-id="b1539-309">例:</span><span class="sxs-lookup"><span data-stu-id="b1539-309">Example:</span></span>  
  
```  
CASE WHEN AVG({25,12,11}) < 100 THEN TRUE ELSE FALSE END  
```  
  
 <span data-ttu-id="b1539-310">Output:</span><span class="sxs-lookup"><span data-stu-id="b1539-310">Output:</span></span>  
  
|<span data-ttu-id="b1539-311">値</span><span class="sxs-lookup"><span data-stu-id="b1539-311">Value</span></span>|  
|-----------|  
|<span data-ttu-id="b1539-312">true</span><span class="sxs-lookup"><span data-stu-id="b1539-312">TRUE</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1539-313">参照</span><span class="sxs-lookup"><span data-stu-id="b1539-313">See Also</span></span>  
 [<span data-ttu-id="b1539-314">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="b1539-314">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="b1539-315">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="b1539-315">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
