---
title: "ビット単位の正規関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 993868ca-16e3-47b6-9915-c29cd63b0a21
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a20f9675af5a67291d95a9297b1ffa1c81a80522
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="bitwise-canonical-functions"></a><span data-ttu-id="3c20c-102">ビット単位の正規関数</span><span class="sxs-lookup"><span data-stu-id="3c20c-102">Bitwise Canonical Functions</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3c20c-103"> にはビット単位の正規関数があります。</span><span class="sxs-lookup"><span data-stu-id="3c20c-103"> includes bitwise canonical functions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c20c-104">コメント</span><span class="sxs-lookup"><span data-stu-id="3c20c-104">Remarks</span></span>  
 <span data-ttu-id="3c20c-105">次の表に、ビット単位の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 正規関数を示します。</span><span class="sxs-lookup"><span data-stu-id="3c20c-105">The following table shows the bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span> <span data-ttu-id="3c20c-106">これらの関数が返す`Null`場合`Null`入力を提供します。</span><span class="sxs-lookup"><span data-stu-id="3c20c-106">These functions will return `Null` if `Null` input is provided.</span></span> <span data-ttu-id="3c20c-107">戻り値の型は、引数の型と同じです。</span><span class="sxs-lookup"><span data-stu-id="3c20c-107">The return type of the functions is the same as the argument type(s).</span></span> <span data-ttu-id="3c20c-108">複数の引数を関数が受け取る場合、それらの引数は同じ型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c20c-108">Arguments must be of the same type, if the function takes more than one argument.</span></span> <span data-ttu-id="3c20c-109">異なる型でビット単位の演算を実行するには、明示的に同じ型にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c20c-109">To perform bitwise operations across different types, you need to cast to the same type explicitly.</span></span>  
  
|<span data-ttu-id="3c20c-110">関数</span><span class="sxs-lookup"><span data-stu-id="3c20c-110">Function</span></span>|<span data-ttu-id="3c20c-111">説明</span><span class="sxs-lookup"><span data-stu-id="3c20c-111">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="3c20c-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="3c20c-112">`BitWiseAnd (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="3c20c-113">`value1` と `value2` のビット単位の論理積を `value1` と `value2` の型で返します。</span><span class="sxs-lookup"><span data-stu-id="3c20c-113">Returns the bitwise conjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="3c20c-114">**引数**</span><span class="sxs-lookup"><span data-stu-id="3c20c-114">**Arguments**</span></span><br /><br /> <span data-ttu-id="3c20c-115">A `Byte`、 `Int16`、 `Int32`、および`Int64`です。</span><span class="sxs-lookup"><span data-stu-id="3c20c-115">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="3c20c-116">**例**</span><span class="sxs-lookup"><span data-stu-id="3c20c-116">**Example**</span></span><br /><br /> `-- The following example returns 1.`<br /><br /> `BitWiseAnd(1,3)`|  
|<span data-ttu-id="3c20c-117">`BitWiseNot (` `value` `)`</span><span class="sxs-lookup"><span data-stu-id="3c20c-117">`BitWiseNot (` `value` `)`</span></span>|<span data-ttu-id="3c20c-118">`value` のビット単位の否定を返します。</span><span class="sxs-lookup"><span data-stu-id="3c20c-118">Returns the bitwise negation of `value`.</span></span><br /><br /> <span data-ttu-id="3c20c-119">**引数**</span><span class="sxs-lookup"><span data-stu-id="3c20c-119">**Arguments**</span></span><br /><br /> <span data-ttu-id="3c20c-120">A `Byte`、 `Int16`、 `Int32`、および`Int64`です。</span><span class="sxs-lookup"><span data-stu-id="3c20c-120">A `Byte`, `Int16`, `Int32`, and `Int64`.</span></span><br /><br /> <span data-ttu-id="3c20c-121">**例**</span><span class="sxs-lookup"><span data-stu-id="3c20c-121">**Example**</span></span><br /><br /> `-- The following example returns -4.`<br /><br /> `BitWiseNot(3)`|  
|<span data-ttu-id="3c20c-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="3c20c-122">`BitWiseOr (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="3c20c-123">`value1` と `value2` のビット単位の論理和を `value1` と `value2` の型で返します。</span><span class="sxs-lookup"><span data-stu-id="3c20c-123">Returns the bitwise disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="3c20c-124">**引数**</span><span class="sxs-lookup"><span data-stu-id="3c20c-124">**Arguments**</span></span><br /><br /> <span data-ttu-id="3c20c-125">A `Byte`、 `Int16`、`Int32`と`Int64`です。</span><span class="sxs-lookup"><span data-stu-id="3c20c-125">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="3c20c-126">**例**</span><span class="sxs-lookup"><span data-stu-id="3c20c-126">**Example**</span></span><br /><br /> `-- The following example returns 3.`<br /><br /> `BitWiseOr(1,3)`|  
|<span data-ttu-id="3c20c-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span><span class="sxs-lookup"><span data-stu-id="3c20c-127">`BitWiseXor (` `value1` `,`  `value2` `)`</span></span>|<span data-ttu-id="3c20c-128">`value1` と `value2` のビット単位の排他的論理和を `value1` と `value2` の型で返します。</span><span class="sxs-lookup"><span data-stu-id="3c20c-128">Returns the bitwise exclusive disjunction of `value1` and `value2` as the type of `value1` and `value2`.</span></span><br /><br /> <span data-ttu-id="3c20c-129">**引数**</span><span class="sxs-lookup"><span data-stu-id="3c20c-129">**Arguments**</span></span><br /><br /> <span data-ttu-id="3c20c-130">A `Byte`、 `Int16`、`Int32`と`Int64`です。</span><span class="sxs-lookup"><span data-stu-id="3c20c-130">A `Byte`, `Int16`, `Int32` and `Int64`.</span></span><br /><br /> <span data-ttu-id="3c20c-131">**例**</span><span class="sxs-lookup"><span data-stu-id="3c20c-131">**Example**</span></span><br /><br /> `-- The following example returns 2.`<br /><br /> `BitWiseXor (1,3)`|  
  
## <a name="see-also"></a><span data-ttu-id="3c20c-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c20c-132">See Also</span></span>  
 [<span data-ttu-id="3c20c-133">正規関数</span><span class="sxs-lookup"><span data-stu-id="3c20c-133">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
