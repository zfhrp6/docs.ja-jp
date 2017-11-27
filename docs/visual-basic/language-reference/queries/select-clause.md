---
title: "Select 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a9d8cabcbd8554ca2aee639eaac8a52f0485a266
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="select-clause-visual-basic"></a><span data-ttu-id="86c4c-102">Select 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86c4c-102">Select Clause (Visual Basic)</span></span>
<span data-ttu-id="86c4c-103">クエリの結果を定義します。</span><span class="sxs-lookup"><span data-stu-id="86c4c-103">Defines the result of a query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86c4c-104">構文</span><span class="sxs-lookup"><span data-stu-id="86c4c-104">Syntax</span></span>  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="86c4c-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="86c4c-105">Parts</span></span>  
 `var1`  
 <span data-ttu-id="86c4c-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="86c4c-106">Optional.</span></span> <span data-ttu-id="86c4c-107">列の式の結果を参照に使用できるエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="86c4c-107">An alias that can be used to reference the results of the column expression.</span></span>  
  
 `fieldName1`  
 <span data-ttu-id="86c4c-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="86c4c-108">Required.</span></span> <span data-ttu-id="86c4c-109">クエリの結果で返されるフィールドの名前。</span><span class="sxs-lookup"><span data-stu-id="86c4c-109">The name of the field to return in the query result.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86c4c-110">コメント</span><span class="sxs-lookup"><span data-stu-id="86c4c-110">Remarks</span></span>  
 <span data-ttu-id="86c4c-111">使用することができます、`Select`句をクエリから返される結果を定義します。</span><span class="sxs-lookup"><span data-stu-id="86c4c-111">You can use the `Select` clause to define the results to return from a query.</span></span> <span data-ttu-id="86c4c-112">これにより、クエリによって作成される新しい匿名型のメンバーを定義するか、またはクエリによって返される名前付きの型のメンバーを対象にすることができます。</span><span class="sxs-lookup"><span data-stu-id="86c4c-112">This enables you to either define the members of a new anonymous type that is created by a query, or to target the members of a named type that is returned by a query.</span></span> <span data-ttu-id="86c4c-113">`Select`句は、クエリの必要はありません。</span><span class="sxs-lookup"><span data-stu-id="86c4c-113">The `Select` clause is not required for a query.</span></span> <span data-ttu-id="86c4c-114">ない場合は`Select`句を指定すると、現在のスコープで示されている範囲変数のすべてのメンバーに基づいた型が返されます。</span><span class="sxs-lookup"><span data-stu-id="86c4c-114">If no `Select` clause is specified, the query will return a type based on all members of the range variables identified for the current scope.</span></span> <span data-ttu-id="86c4c-115">詳細については、「[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86c4c-115">For more information, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span> <span data-ttu-id="86c4c-116">クエリでは、名前付きの型を作成するときの型の結果が返されます。<xref:System.Collections.Generic.IEnumerable%601>場所`T`は、作成された型です。</span><span class="sxs-lookup"><span data-stu-id="86c4c-116">When a query creates a named type, it will return a result of type <xref:System.Collections.Generic.IEnumerable%601> where `T` is the created type.</span></span>  
  
 <span data-ttu-id="86c4c-117">`Select`句は、現在のスコープ内のどの変数を参照できます。</span><span class="sxs-lookup"><span data-stu-id="86c4c-117">The `Select` clause can reference any variables in the current scope.</span></span> <span data-ttu-id="86c4c-118">これで示されている範囲変数が含まれます、`From`句 (または`From`句)。</span><span class="sxs-lookup"><span data-stu-id="86c4c-118">This includes range variables identified in the `From` clause (or `From` clauses).</span></span> <span data-ttu-id="86c4c-119">別名によって作成された新しい変数も含まれています、 `Aggregate`、 `Let`、 `Group By`、または`Group Join`句、または、以前の変数`Select`クエリ式内の句。</span><span class="sxs-lookup"><span data-stu-id="86c4c-119">It also includes any new variables created with an alias by the `Aggregate`, `Let`, `Group By`, or `Group Join` clauses, or variables from a previous `Select` clause in the query expression.</span></span> <span data-ttu-id="86c4c-120">`Select`句では、静的な値を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="86c4c-120">The `Select` clause can also include static values.</span></span> <span data-ttu-id="86c4c-121">次のコード例は、クエリ式を示しますたとえば、`Select`句は、4 つのメンバーを持つ新しい匿名型として、クエリの結果を定義します。 `ProductName`、 `Price`、 `Discount`、および`DiscountedPrice`です。</span><span class="sxs-lookup"><span data-stu-id="86c4c-121">For example, the following code example shows a query expression in which the `Select` clause defines the query result as a new anonymous type with four members: `ProductName`, `Price`, `Discount`, and `DiscountedPrice`.</span></span> <span data-ttu-id="86c4c-122">`ProductName`と`Price`メンバー値で定義されている製品の範囲変数から取得されますが、`From`句。</span><span class="sxs-lookup"><span data-stu-id="86c4c-122">The `ProductName` and `Price` member values are taken from the product range variable that is defined in the `From` clause.</span></span> <span data-ttu-id="86c4c-123">`DiscountedPrice`でメンバーの値を計算、`Let`句。</span><span class="sxs-lookup"><span data-stu-id="86c4c-123">The `DiscountedPrice` member value is calculated in the `Let` clause.</span></span> <span data-ttu-id="86c4c-124">`Discount`メンバーは、静的な値です。</span><span class="sxs-lookup"><span data-stu-id="86c4c-124">The `Discount` member is a static value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 <span data-ttu-id="86c4c-125">`Select`句が後続のクエリ句の範囲変数の新しいセットを紹介し、前の範囲変数がスコープ内に不要になった。</span><span class="sxs-lookup"><span data-stu-id="86c4c-125">The `Select` clause introduces a new set of range variables for subsequent query clauses, and previous range variables are no longer in scope.</span></span> <span data-ttu-id="86c4c-126">最後の`Select`句をクエリ式では、クエリの戻り値を決定します。</span><span class="sxs-lookup"><span data-stu-id="86c4c-126">The last `Select` clause in a query expression determines the return value of the query.</span></span> <span data-ttu-id="86c4c-127">たとえば、次のクエリ ID を返します、会社名と注文合計が 500 を超えるすべての顧客注文の。</span><span class="sxs-lookup"><span data-stu-id="86c4c-127">For example, the following query returns the company name and order ID for every customer order for which the total exceeds 500.</span></span> <span data-ttu-id="86c4c-128">最初の`Select`句は指定の範囲変数、`Where`句と、2 つ目`Select`句。</span><span class="sxs-lookup"><span data-stu-id="86c4c-128">The first `Select` clause identifies the range variables for the `Where` clause and the second `Select` clause.</span></span> <span data-ttu-id="86c4c-129">2 番目`Select`句は、新しい匿名型として、クエリによって返される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="86c4c-129">The second `Select` clause identifies the values returned by the query as a new anonymous type.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 <span data-ttu-id="86c4c-130">場合、`Select`句を返す 1 つの項目を識別する、クエリ式は、その 1 つの項目の種類のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="86c4c-130">If the `Select` clause identifies a single item to return, the query expression returns a collection of the type of that single item.</span></span> <span data-ttu-id="86c4c-131">場合、`Select`句を返す複数の項目を識別する、クエリ式は、選択したアイテムに基づいて、新しい匿名型のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="86c4c-131">If the `Select` clause identifies multiple items to return, the query expression returns a collection of a new anonymous type, based on the selected items.</span></span> <span data-ttu-id="86c4c-132">たとえば、次の 2 つのクエリがに基づいて 2 つの異なる型のコレクションを返す、`Select`句。</span><span class="sxs-lookup"><span data-stu-id="86c4c-132">For example, the following two queries return collections of two different types based on the `Select` clause.</span></span> <span data-ttu-id="86c4c-133">最初のクエリでは、会社名の文字列としてのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="86c4c-133">The first query returns a collection of company names as strings.</span></span> <span data-ttu-id="86c4c-134">2 番目のクエリのコレクションを返します`Customer`と会社名とアドレス情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="86c4c-134">The second query returns a collection of `Customer` objects populated with the company names and address information.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="86c4c-135">例</span><span class="sxs-lookup"><span data-stu-id="86c4c-135">Example</span></span>  
 <span data-ttu-id="86c4c-136">次のクエリ式は、`From`範囲変数を宣言する句`cust`の`customers`コレクション。</span><span class="sxs-lookup"><span data-stu-id="86c4c-136">The following query expression uses a `From` clause to declare a range variable `cust` for the `customers` collection.</span></span> <span data-ttu-id="86c4c-137">`Select`句は、顧客名と ID 値を選択し、設定、`CompanyName`と`CustomerID`新しい範囲変数の列です。</span><span class="sxs-lookup"><span data-stu-id="86c4c-137">The `Select` clause selects the customer name and ID value and populates the `CompanyName` and `CustomerID` columns of the new range variable.</span></span> <span data-ttu-id="86c4c-138">`For Each`ステートメントが返された各オブジェクトをループ処理し、表示、`CompanyName`と`CustomerID`各レコードの列です。</span><span class="sxs-lookup"><span data-stu-id="86c4c-138">The `For Each` statement loops over each returned object and displays the `CompanyName` and `CustomerID` columns for each record.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="86c4c-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="86c4c-139">See Also</span></span>  
 [<span data-ttu-id="86c4c-140">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="86c4c-140">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="86c4c-141">クエリ</span><span class="sxs-lookup"><span data-stu-id="86c4c-141">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="86c4c-142">From 句</span><span class="sxs-lookup"><span data-stu-id="86c4c-142">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="86c4c-143">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="86c4c-143">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="86c4c-144">Order By 句</span><span class="sxs-lookup"><span data-stu-id="86c4c-144">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="86c4c-145">匿名型</span><span class="sxs-lookup"><span data-stu-id="86c4c-145">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
