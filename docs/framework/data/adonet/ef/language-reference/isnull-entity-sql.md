---
title: ISNULL (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 57e90f013227f08ce365262da633a79d7abb5a8d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="f30c7-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f30c7-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="f30c7-103">クエリ式が NULL かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="f30c7-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f30c7-104">構文</span><span class="sxs-lookup"><span data-stu-id="f30c7-104">Syntax</span></span>  
  
```  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="f30c7-105">引数</span><span class="sxs-lookup"><span data-stu-id="f30c7-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f30c7-106">任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="f30c7-106">Any valid query expression.</span></span> <span data-ttu-id="f30c7-107">コレクションにすることはできません。また、コレクション メンバーや、コレクション型のプロパティを持つレコード型を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="f30c7-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="f30c7-108">NOT</span><span class="sxs-lookup"><span data-stu-id="f30c7-108">NOT</span></span>  
 <span data-ttu-id="f30c7-109">IS NULL の EDM.Boolean の結果を否定します。</span><span class="sxs-lookup"><span data-stu-id="f30c7-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f30c7-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="f30c7-110">Return Value</span></span>  
 <span data-ttu-id="f30c7-111">`true` によって NULL が返される場合は `expression`、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="f30c7-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f30c7-112">コメント</span><span class="sxs-lookup"><span data-stu-id="f30c7-112">Remarks</span></span>  
 <span data-ttu-id="f30c7-113">外部結合の要素が NULL かどうかを確認するには、`IS NULL` を使用します。</span><span class="sxs-lookup"><span data-stu-id="f30c7-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```  
select c   
      from LOB.Customers as c left outer join LOB.Orders as o   
                              on c.ID = o.CustomerID    
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="f30c7-114">メンバーに実際の値が含まれているかどうかを確認するには、`IS NULL` を使用します。</span><span class="sxs-lookup"><span data-stu-id="f30c7-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="f30c7-115">次の表は、いくつかのパターンにおける `IS NULL` の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="f30c7-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="f30c7-116">すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f30c7-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="f30c7-117">パターン</span><span class="sxs-lookup"><span data-stu-id="f30c7-117">Pattern</span></span>|<span data-ttu-id="f30c7-118">動作</span><span class="sxs-lookup"><span data-stu-id="f30c7-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="f30c7-119">null IS NULL</span><span class="sxs-lookup"><span data-stu-id="f30c7-119">null IS NULL</span></span>|<span data-ttu-id="f30c7-120">`true` を返します。</span><span class="sxs-lookup"><span data-stu-id="f30c7-120">Returns `true`.</span></span>|  
|<span data-ttu-id="f30c7-121">TREAT (null AS EntityType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="f30c7-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="f30c7-122">`true` を返します。</span><span class="sxs-lookup"><span data-stu-id="f30c7-122">Returns `true`.</span></span>|  
|<span data-ttu-id="f30c7-123">TREAT (null AS ComplexType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="f30c7-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="f30c7-124">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="f30c7-124">Throws an error.</span></span>|  
|<span data-ttu-id="f30c7-125">TREAT (null AS RowType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="f30c7-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="f30c7-126">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="f30c7-126">Throws an error.</span></span>|  
|<span data-ttu-id="f30c7-127">EntityType IS NULL</span><span class="sxs-lookup"><span data-stu-id="f30c7-127">EntityType IS NULL</span></span>|<span data-ttu-id="f30c7-128">`true` または `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="f30c7-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="f30c7-129">ComplexType IS NULL</span><span class="sxs-lookup"><span data-stu-id="f30c7-129">ComplexType IS NULL</span></span>|<span data-ttu-id="f30c7-130">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="f30c7-130">Throws an error.</span></span>|  
|<span data-ttu-id="f30c7-131">RowType IS NULL</span><span class="sxs-lookup"><span data-stu-id="f30c7-131">RowType IS NULL</span></span>|<span data-ttu-id="f30c7-132">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="f30c7-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f30c7-133">例</span><span class="sxs-lookup"><span data-stu-id="f30c7-133">Example</span></span>  
 <span data-ttu-id="f30c7-134">次[!INCLUDE[esql](../../../../../../includes/esql-md.md)]クエリでは、IS NOT NULL 演算子を使用して、クエリ式が null でないかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="f30c7-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="f30c7-135">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f30c7-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f30c7-136">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f30c7-136">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f30c7-137">「 [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f30c7-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="f30c7-138">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="f30c7-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ISNULL](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="f30c7-139">参照</span><span class="sxs-lookup"><span data-stu-id="f30c7-139">See Also</span></span>  
 [<span data-ttu-id="f30c7-140">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="f30c7-140">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
