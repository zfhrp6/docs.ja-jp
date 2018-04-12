---
title: Skip 句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="81eec-102">Skip 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81eec-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="81eec-103">コレクション内の指定された数の要素をバイパスし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="81eec-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81eec-104">構文</span><span class="sxs-lookup"><span data-stu-id="81eec-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="81eec-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="81eec-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="81eec-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="81eec-106">Required.</span></span> <span data-ttu-id="81eec-107">スキップするシーケンスの要素の数に評価される式または値。</span><span class="sxs-lookup"><span data-stu-id="81eec-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81eec-108">コメント</span><span class="sxs-lookup"><span data-stu-id="81eec-108">Remarks</span></span>  
 <span data-ttu-id="81eec-109">`Skip`句によってクエリ結果リストの先頭の要素をバイパスし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="81eec-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="81eec-110">スキップする要素の数がによって識別される、`count`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="81eec-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="81eec-111">使用することができます、`Skip`句、`Take`句をクエリの任意のセグメントからのデータの範囲を返します。</span><span class="sxs-lookup"><span data-stu-id="81eec-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="81eec-112">これを行うには、範囲の最初の要素のインデックスを渡す、`Skip`句と範囲のサイズ、`Take`句。</span><span class="sxs-lookup"><span data-stu-id="81eec-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="81eec-113">使用すると、`Skip`クエリ内の句、する必要がありますも順序が有効になります結果が返されるように、`Skip`を意図した結果をバイパスする句。</span><span class="sxs-lookup"><span data-stu-id="81eec-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="81eec-114">クエリの結果を順序付けの詳細については、次を参照してください。 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)です。</span><span class="sxs-lookup"><span data-stu-id="81eec-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="81eec-115">使用することができます、`SkipWhile`句を指定した条件に応じて特定の要素だけを無視することを指定します。</span><span class="sxs-lookup"><span data-stu-id="81eec-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81eec-116">例</span><span class="sxs-lookup"><span data-stu-id="81eec-116">Example</span></span>  
 <span data-ttu-id="81eec-117">次のコード例では、`Skip`句と共に、`Take`句をページのクエリからデータを返します。</span><span class="sxs-lookup"><span data-stu-id="81eec-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="81eec-118">`GetCustomers`関数は、`Skip`値、および使用して、指定した開始インデックスを作成するまで、リスト内の顧客をバイパスする句、`Take`句をインデックス値から顧客のページを返します。</span><span class="sxs-lookup"><span data-stu-id="81eec-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="81eec-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="81eec-119">See Also</span></span>  
 [<span data-ttu-id="81eec-120">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="81eec-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="81eec-121">クエリ</span><span class="sxs-lookup"><span data-stu-id="81eec-121">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="81eec-122">Select 句</span><span class="sxs-lookup"><span data-stu-id="81eec-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="81eec-123">From 句</span><span class="sxs-lookup"><span data-stu-id="81eec-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="81eec-124">Order By 句</span><span class="sxs-lookup"><span data-stu-id="81eec-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="81eec-125">Skip While 句</span><span class="sxs-lookup"><span data-stu-id="81eec-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="81eec-126">Take 句</span><span class="sxs-lookup"><span data-stu-id="81eec-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
