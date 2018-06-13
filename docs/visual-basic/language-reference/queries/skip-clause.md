---
title: Skip 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 1810bf4a6573c6fa36f1d8149bf341d45cfd6f52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602828"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="fd1b5-102">Skip 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd1b5-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="fd1b5-103">コレクション内の指定された数の要素をバイパスし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd1b5-104">構文</span><span class="sxs-lookup"><span data-stu-id="fd1b5-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="fd1b5-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="fd1b5-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="fd1b5-106">必須。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-106">Required.</span></span> <span data-ttu-id="fd1b5-107">スキップするシーケンスの要素の数に評価される式または値。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd1b5-108">コメント</span><span class="sxs-lookup"><span data-stu-id="fd1b5-108">Remarks</span></span>  
 <span data-ttu-id="fd1b5-109">`Skip`句によってクエリ結果リストの先頭の要素をバイパスし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="fd1b5-110">スキップする要素の数がによって識別される、`count`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="fd1b5-111">使用することができます、`Skip`句、`Take`句をクエリの任意のセグメントからのデータの範囲を返します。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="fd1b5-112">これを行うには、範囲の最初の要素のインデックスを渡す、`Skip`句と範囲のサイズ、`Take`句。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="fd1b5-113">使用すると、`Skip`クエリ内の句、する必要がありますも順序が有効になります結果が返されるように、`Skip`を意図した結果をバイパスする句。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="fd1b5-114">クエリの結果を順序付けの詳細については、次を参照してください。 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="fd1b5-115">使用することができます、`SkipWhile`句を指定した条件に応じて特定の要素だけを無視することを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd1b5-116">例</span><span class="sxs-lookup"><span data-stu-id="fd1b5-116">Example</span></span>  
 <span data-ttu-id="fd1b5-117">次のコード例では、`Skip`句と共に、`Take`句をページのクエリからデータを返します。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="fd1b5-118">`GetCustomers`関数は、`Skip`値、および使用して、指定した開始インデックスを作成するまで、リスト内の顧客をバイパスする句、`Take`句をインデックス値から顧客のページを返します。</span><span class="sxs-lookup"><span data-stu-id="fd1b5-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fd1b5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd1b5-119">See Also</span></span>  
 [<span data-ttu-id="fd1b5-120">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="fd1b5-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="fd1b5-121">クエリ</span><span class="sxs-lookup"><span data-stu-id="fd1b5-121">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="fd1b5-122">Select 句</span><span class="sxs-lookup"><span data-stu-id="fd1b5-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="fd1b5-123">From 句</span><span class="sxs-lookup"><span data-stu-id="fd1b5-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="fd1b5-124">Order By 句</span><span class="sxs-lookup"><span data-stu-id="fd1b5-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="fd1b5-125">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="fd1b5-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="fd1b5-126">Take 句</span><span class="sxs-lookup"><span data-stu-id="fd1b5-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
