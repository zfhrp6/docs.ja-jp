---
title: "演算子の優先順位 (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92e4ca5-2889-4266-9625-47f0eb01a948
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 537c9ae7c92c6abcbe597970f2b0ec29e399bc62
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="operator-precedence-entity-sql"></a><span data-ttu-id="4f9e9-102">演算子の優先順位 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4f9e9-102">Operator Precedence (Entity SQL)</span></span>
<span data-ttu-id="4f9e9-103">ときに、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]クエリが複数の演算子、演算子の優先順位は、操作が実行される順序を決定します。</span><span class="sxs-lookup"><span data-stu-id="4f9e9-103">When an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query has multiple operators, operator precedence determines the sequence in which the operations are performed.</span></span> <span data-ttu-id="4f9e9-104">実行される順序により、クエリ結果の値は大きく変わります。</span><span class="sxs-lookup"><span data-stu-id="4f9e9-104">The order of execution can significantly affect the query result.</span></span>  
  
 <span data-ttu-id="4f9e9-105">演算子には、次の表に示す優先順位レベルが定義されています。</span><span class="sxs-lookup"><span data-stu-id="4f9e9-105">Operators have the precedence levels shown in the following table.</span></span> <span data-ttu-id="4f9e9-106">優先順位が高い演算子は、優先順位が低い演算子よりも前に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4f9e9-106">An operator with a higher level is evaluated before an operator with a lower level.</span></span>  
  
|<span data-ttu-id="4f9e9-107">レベル</span><span class="sxs-lookup"><span data-stu-id="4f9e9-107">Level</span></span>|<span data-ttu-id="4f9e9-108">演算の種類</span><span class="sxs-lookup"><span data-stu-id="4f9e9-108">Operation type</span></span>|<span data-ttu-id="4f9e9-109">演算子</span><span class="sxs-lookup"><span data-stu-id="4f9e9-109">Operator</span></span>|  
|-----------|--------------------|--------------|  
|<span data-ttu-id="4f9e9-110">1</span><span class="sxs-lookup"><span data-stu-id="4f9e9-110">1</span></span>|<span data-ttu-id="4f9e9-111">1 次式</span><span class="sxs-lookup"><span data-stu-id="4f9e9-111">Primary</span></span>|`. , [] ()`|  
|<span data-ttu-id="4f9e9-112">2</span><span class="sxs-lookup"><span data-stu-id="4f9e9-112">2</span></span>|<span data-ttu-id="4f9e9-113">単項</span><span class="sxs-lookup"><span data-stu-id="4f9e9-113">Unary</span></span>|`! not`|  
|<span data-ttu-id="4f9e9-114">3</span><span class="sxs-lookup"><span data-stu-id="4f9e9-114">3</span></span>|<span data-ttu-id="4f9e9-115">乗法</span><span class="sxs-lookup"><span data-stu-id="4f9e9-115">Multiplicative</span></span>|`* / %`|  
|<span data-ttu-id="4f9e9-116">4</span><span class="sxs-lookup"><span data-stu-id="4f9e9-116">4</span></span>|<span data-ttu-id="4f9e9-117">加法</span><span class="sxs-lookup"><span data-stu-id="4f9e9-117">Additive</span></span>|`+ -`|  
|<span data-ttu-id="4f9e9-118">5</span><span class="sxs-lookup"><span data-stu-id="4f9e9-118">5</span></span>|<span data-ttu-id="4f9e9-119">並べ替え</span><span class="sxs-lookup"><span data-stu-id="4f9e9-119">Ordering</span></span>|`< > <= >=`|  
|<span data-ttu-id="4f9e9-120">6</span><span class="sxs-lookup"><span data-stu-id="4f9e9-120">6</span></span>|<span data-ttu-id="4f9e9-121">等価比較</span><span class="sxs-lookup"><span data-stu-id="4f9e9-121">Equality</span></span>|`= != <>`|  
|<span data-ttu-id="4f9e9-122">7</span><span class="sxs-lookup"><span data-stu-id="4f9e9-122">7</span></span>|<span data-ttu-id="4f9e9-123">条件 AND</span><span class="sxs-lookup"><span data-stu-id="4f9e9-123">Conditional AND</span></span>|`and &&`|  
|<span data-ttu-id="4f9e9-124">8</span><span class="sxs-lookup"><span data-stu-id="4f9e9-124">8</span></span>|<span data-ttu-id="4f9e9-125">条件 OR</span><span class="sxs-lookup"><span data-stu-id="4f9e9-125">Conditional OR</span></span>|`or &#124;&#124;`|  
  
 <span data-ttu-id="4f9e9-126">式の中の 2 つの演算子が同じ優先順位レベルである場合は、クエリの中での位置に従って演算子は左から右へと評価されます。</span><span class="sxs-lookup"><span data-stu-id="4f9e9-126">When two operators in an expression have the same operator precedence level, they are evaluated left to right, based on their position in the query.</span></span> <span data-ttu-id="4f9e9-127">たとえば、`x+y-z` は `(x+y)-z` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="4f9e9-127">For example, `x+y-z` is evaluated as `(x+y)-z`.</span></span>  
  
 <span data-ttu-id="4f9e9-128">クエリの中で演算子の定義済みの優先順位を無効にするには、かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="4f9e9-128">You can use parentheses to override the defined precedence of the operators in a query.</span></span> <span data-ttu-id="4f9e9-129">この場合、かっこ内のすべての演算が評価され、1 つの結果が作成されてから、かっこ外の演算子でこの結果が使用されます。</span><span class="sxs-lookup"><span data-stu-id="4f9e9-129">Everything within parentheses is evaluated first to yield a single result before that result can be used by any operator outside the parentheses.</span></span> <span data-ttu-id="4f9e9-130">たとえば、`x+y*z`乗算`y`によって`z`し、追加`x`が`(x+y)*z`追加`x`に`y`には、結果を乗算し、`z`です。</span><span class="sxs-lookup"><span data-stu-id="4f9e9-130">For example, `x+y*z` multiplies `y` by `z` and then adds `x`, but `(x+y)*z` adds `x` to `y` and then multiplies the result by `z`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f9e9-131">参照</span><span class="sxs-lookup"><span data-stu-id="4f9e9-131">See Also</span></span>  
 [<span data-ttu-id="4f9e9-132">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="4f9e9-132">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
