---
title: "Group By 句 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
dev_langs:
- VB
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement
- Group By clause
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a27e2f15e61456b2e7ac0ede81c66cdb4e8fd612
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="e553a-102">Group By 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e553a-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="e553a-103">クエリ結果の要素をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="e553a-103">Groups the elements of a query result.</span></span> <span data-ttu-id="e553a-104">これを使用して、グループごとに集計関数を適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e553a-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="e553a-105">グループ化操作は、1 つ以上のキーに基づきます。</span><span class="sxs-lookup"><span data-stu-id="e553a-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e553a-106">構文</span><span class="sxs-lookup"><span data-stu-id="e553a-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="e553a-107">指定項目</span><span class="sxs-lookup"><span data-stu-id="e553a-107">Parts</span></span>  
  
-   <span data-ttu-id="e553a-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="e553a-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="e553a-109">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e553a-109">Optional.</span></span> <span data-ttu-id="e553a-110">グループ化された結果に含めるフィールドを明示的に示す、クエリ変数の&1; つ以上のフィールドです。</span><span class="sxs-lookup"><span data-stu-id="e553a-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="e553a-111">フィールドを指定しない場合、グループ化された結果にはクエリ変数のすべてのフィールドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e553a-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
-   `keyExp1`  
  
     <span data-ttu-id="e553a-112">必須です。</span><span class="sxs-lookup"><span data-stu-id="e553a-112">Required.</span></span> <span data-ttu-id="e553a-113">要素のグループを決定するために使用するキーを識別する式です。</span><span class="sxs-lookup"><span data-stu-id="e553a-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="e553a-114">複数のキーを指定して、複合キーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e553a-114">You can specify more than one key to specify a composite key.</span></span>  
  
-   `keyExp2`  
  
     <span data-ttu-id="e553a-115">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e553a-115">Optional.</span></span> <span data-ttu-id="e553a-116">`keyExp1` と結合して複合キーを作成する&1; つ以上の追加キーです。</span><span class="sxs-lookup"><span data-stu-id="e553a-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
-   `aggregateList`  
  
     <span data-ttu-id="e553a-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="e553a-117">Required.</span></span> <span data-ttu-id="e553a-118">グループの集計方法を示す&1; つ以上の式です。</span><span class="sxs-lookup"><span data-stu-id="e553a-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="e553a-119">グループ化された結果のメンバー名を示すには、次のいずれかの形式で、 `Group` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="e553a-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="e553a-120">または</span><span class="sxs-lookup"><span data-stu-id="e553a-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="e553a-121">グループに適用する集計関数を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="e553a-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e553a-122">コメント</span><span class="sxs-lookup"><span data-stu-id="e553a-122">Remarks</span></span>  
 <span data-ttu-id="e553a-123">`Group By` 句を使用して、クエリの結果をグループに分割できます。</span><span class="sxs-lookup"><span data-stu-id="e553a-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="e553a-124">グループ化は、1 つのキー、または複数のキーで構成される複合キーに基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="e553a-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="e553a-125">一致するキー値と関連付けられた要素は、同じグループに入れられます。</span><span class="sxs-lookup"><span data-stu-id="e553a-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="e553a-126">グループの参照に使用するメンバー名を示すには、 `aggregateList` 句の `Into` パラメーターと `Group` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="e553a-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="e553a-127">`Into` 句に集計関数を含めることで、グループ化された要素の値を計算することもできます。</span><span class="sxs-lookup"><span data-stu-id="e553a-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="e553a-128">標準の集計関数の一覧は、次を参照してください。 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)します。</span><span class="sxs-lookup"><span data-stu-id="e553a-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e553a-129">例</span><span class="sxs-lookup"><span data-stu-id="e553a-129">Example</span></span>  
 <span data-ttu-id="e553a-130">以下のコード例では、場所 (国) に基づいて顧客の一覧をグループ化し、各グループ内の顧客の数を返します。</span><span class="sxs-lookup"><span data-stu-id="e553a-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="e553a-131">結果は、国名によって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="e553a-131">The results are ordered by country name.</span></span> <span data-ttu-id="e553a-132">グループ化した結果は、市区町村名によって並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="e553a-132">The grouped results are ordered by city name.</span></span>  
  
 <span data-ttu-id="e553a-133">[!code-vb[VbSimpleQuerySamples&#11;](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e553a-133">[!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e553a-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="e553a-134">See Also</span></span>  
 <span data-ttu-id="e553a-135">[Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="e553a-135">[Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="e553a-136"> [クエリ](../../../visual-basic/language-reference/queries/queries.md) </span><span class="sxs-lookup"><span data-stu-id="e553a-136"> [Queries](../../../visual-basic/language-reference/queries/queries.md) </span></span>  
<span data-ttu-id="e553a-137"> [Select 句](../../../visual-basic/language-reference/queries/select-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e553a-137"> [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md) </span></span>  
<span data-ttu-id="e553a-138"> [From 句](../../../visual-basic/language-reference/queries/from-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e553a-138"> [From Clause](../../../visual-basic/language-reference/queries/from-clause.md) </span></span>  
<span data-ttu-id="e553a-139"> [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e553a-139"> [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md) </span></span>  
<span data-ttu-id="e553a-140"> [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span><span class="sxs-lookup"><span data-stu-id="e553a-140"> [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md) </span></span>  
<span data-ttu-id="e553a-141"> [Group Join 句](../../../visual-basic/language-reference/queries/group-join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="e553a-141"> [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)</span></span>
