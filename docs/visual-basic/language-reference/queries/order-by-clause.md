---
title: Order By 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryOrderBy
- vb.QueryAscending
- vb.QueryDescending
helpviewer_keywords:
- queries [Visual Basic], Order By
- Order By clause [Visual Basic]
- Order By statement [Visual Basic]
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
ms.openlocfilehash: 7c60156ee81618530b42d5f61dbcac6f59c4f675
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604121"
---
# <a name="order-by-clause-visual-basic"></a><span data-ttu-id="c321e-102">Order By 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c321e-102">Order By Clause (Visual Basic)</span></span>
<span data-ttu-id="c321e-103">クエリ結果の並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="c321e-103">Specifies the sort order for a query result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c321e-104">構文</span><span class="sxs-lookup"><span data-stu-id="c321e-104">Syntax</span></span>  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="c321e-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c321e-105">Parts</span></span>  
 `orderExp1`  
 <span data-ttu-id="c321e-106">必須。</span><span class="sxs-lookup"><span data-stu-id="c321e-106">Required.</span></span> <span data-ttu-id="c321e-107">1 つまたは複数のフィールド現在のクエリ結果からを返される値を順序付ける方法を示すです。</span><span class="sxs-lookup"><span data-stu-id="c321e-107">One or more fields from the current query result that identify how to order the returned values.</span></span> <span data-ttu-id="c321e-108">フィールド名は、コンマ (,) で区切る必要があります。</span><span class="sxs-lookup"><span data-stu-id="c321e-108">The field names must be separated by commas (,).</span></span> <span data-ttu-id="c321e-109">昇順または降順に並べ替えを使用して、ソート済みとして、各フィールドを識別することができます、`Ascending`または`Descending`キーワード。</span><span class="sxs-lookup"><span data-stu-id="c321e-109">You can identify each field as sorted in ascending or descending order by using the `Ascending` or `Descending` keywords.</span></span> <span data-ttu-id="c321e-110">ない場合は`Ascending`または`Descending`キーワードを指定すると、既定の並べ替え順序は昇順です。</span><span class="sxs-lookup"><span data-stu-id="c321e-110">If no `Ascending` or `Descending` keyword is specified, the default sort order is ascending.</span></span> <span data-ttu-id="c321e-111">並べ替え順序フィールドには、左から右への優先順位が与えられます。</span><span class="sxs-lookup"><span data-stu-id="c321e-111">The sort order fields are given precedence from left to right.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c321e-112">コメント</span><span class="sxs-lookup"><span data-stu-id="c321e-112">Remarks</span></span>  
 <span data-ttu-id="c321e-113">使用することができます、`Order By`句、クエリの結果の並べ替えにします。</span><span class="sxs-lookup"><span data-stu-id="c321e-113">You can use the `Order By` clause to sort the results of a query.</span></span> <span data-ttu-id="c321e-114">`Order By`句では、現在のスコープの範囲変数に基づく結果を並べ替えることができますのみです。</span><span class="sxs-lookup"><span data-stu-id="c321e-114">The `Order By` clause can only sort a result based on the range variable for the current scope.</span></span> <span data-ttu-id="c321e-115">たとえば、`Select`句にそのスコープに対する新しい反復変数によりクエリ式で、新しいスコープが導入されています。</span><span class="sxs-lookup"><span data-stu-id="c321e-115">For example, the `Select` clause introduces a new scope in a query expression with new iteration variables for that scope.</span></span> <span data-ttu-id="c321e-116">範囲変数の前に定義されている、`Select`後に使用できるクエリの句は、`Select`句。</span><span class="sxs-lookup"><span data-stu-id="c321e-116">Range variables defined before a `Select` clause in a query are not available after the `Select` clause.</span></span> <span data-ttu-id="c321e-117">したがってでは使用できませんのフィールドで、結果の並べ替えをする場合、`Select`句を付ける必要があります、`Order By`句の前に、`Select`句。</span><span class="sxs-lookup"><span data-stu-id="c321e-117">Therefore, if you want to order your results by a field that is not available in the `Select` clause, you must put the `Order By` clause before the `Select` clause.</span></span> <span data-ttu-id="c321e-118">1 つはしなければならない場合の例は、結果の一部として返されないフィールドで、クエリの並べ替えを行うときにします。</span><span class="sxs-lookup"><span data-stu-id="c321e-118">One example of when you would have to do this is when you want to sort your query by fields that are not returned as part of the result.</span></span>  
  
 <span data-ttu-id="c321e-119">昇順と降順の実装によって、フィールドを特定の順序、<xref:System.IComparable>フィールドのデータ型のインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="c321e-119">Ascending and descending order for a field is determined by the implementation of the <xref:System.IComparable> interface for the data type of the field.</span></span> <span data-ttu-id="c321e-120">データ型を実装しない場合、<xref:System.IComparable>インターフェイス、並べ替え順序は無視されます。</span><span class="sxs-lookup"><span data-stu-id="c321e-120">If the data type does not implement the <xref:System.IComparable> interface, the sort order is ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c321e-121">例</span><span class="sxs-lookup"><span data-stu-id="c321e-121">Example</span></span>  
 <span data-ttu-id="c321e-122">次のクエリ式は、`From`範囲変数を宣言する句`book`の`books`コレクション。</span><span class="sxs-lookup"><span data-stu-id="c321e-122">The following query expression uses a `From` clause to declare a range variable `book` for the `books` collection.</span></span> <span data-ttu-id="c321e-123">`Order By`句が昇順 (既定) に価格を指定して、クエリの結果を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="c321e-123">The `Order By` clause sorts the query result by price in ascending order (the default).</span></span> <span data-ttu-id="c321e-124">書籍の価格が同じ順序の昇順のタイトルに基づいて並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="c321e-124">Books with the same price are sorted by title in ascending order.</span></span> <span data-ttu-id="c321e-125">`Select`句を選択、`Title`と`Price`プロパティとして、クエリによって返される値。</span><span class="sxs-lookup"><span data-stu-id="c321e-125">The `Select` clause selects the `Title` and `Price` properties as the values returned by the query.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="c321e-126">例</span><span class="sxs-lookup"><span data-stu-id="c321e-126">Example</span></span>  
 <span data-ttu-id="c321e-127">次のクエリ式は、`Order By`価格の降順でクエリ結果を並べ替えるための句。</span><span class="sxs-lookup"><span data-stu-id="c321e-127">The following query expression uses the `Order By` clause to sort the query result by price in descending order.</span></span> <span data-ttu-id="c321e-128">書籍の価格が同じ順序の昇順のタイトルに基づいて並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="c321e-128">Books with the same price are sorted by title in ascending order.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="c321e-129">例</span><span class="sxs-lookup"><span data-stu-id="c321e-129">Example</span></span>  
 <span data-ttu-id="c321e-130">次のクエリ式は、`Select`書籍のタイトルを選択して、価格、発行日、および作成する句。</span><span class="sxs-lookup"><span data-stu-id="c321e-130">The following query expression uses a `Select` clause to select the book title, price, publish date, and author.</span></span> <span data-ttu-id="c321e-131">設定し、 `Title`、 `Price`、 `PublishDate`、および`Author`新しいスコープの範囲変数のフィールドです。</span><span class="sxs-lookup"><span data-stu-id="c321e-131">It then populates the `Title`, `Price`, `PublishDate`, and `Author` fields of the range variable for the new scope.</span></span> <span data-ttu-id="c321e-132">`Order By`句の作成者名、ブック タイトル、および price によって新しい範囲変数の順序。</span><span class="sxs-lookup"><span data-stu-id="c321e-132">The `Order By` clause orders the new range variable by author name, book title, and then price.</span></span> <span data-ttu-id="c321e-133">各列は、既定の順序 (昇順) で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="c321e-133">Each column is sorted in the default order (ascending).</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c321e-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="c321e-134">See Also</span></span>  
 [<span data-ttu-id="c321e-135">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="c321e-135">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="c321e-136">クエリ</span><span class="sxs-lookup"><span data-stu-id="c321e-136">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="c321e-137">Select 句</span><span class="sxs-lookup"><span data-stu-id="c321e-137">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="c321e-138">From 句</span><span class="sxs-lookup"><span data-stu-id="c321e-138">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
