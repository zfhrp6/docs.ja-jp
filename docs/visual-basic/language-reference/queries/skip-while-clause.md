---
title: Skip While 句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="829d2-102">Skip While 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="829d2-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="829d2-103">指定された条件が `true` である限り、コレクションの要素をバイパスし、残りの要素を返します。</span><span class="sxs-lookup"><span data-stu-id="829d2-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="829d2-104">構文</span><span class="sxs-lookup"><span data-stu-id="829d2-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="829d2-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="829d2-105">Parts</span></span>  
  
|<span data-ttu-id="829d2-106">用語</span><span class="sxs-lookup"><span data-stu-id="829d2-106">Term</span></span>|<span data-ttu-id="829d2-107">定義</span><span class="sxs-lookup"><span data-stu-id="829d2-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="829d2-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="829d2-108">Required.</span></span> <span data-ttu-id="829d2-109">要素をテストするための条件を表す式。</span><span class="sxs-lookup"><span data-stu-id="829d2-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="829d2-110">式を返す必要があります、`Boolean`値またはそれと同等の機能など、`Integer`として評価される、`Boolean`です。</span><span class="sxs-lookup"><span data-stu-id="829d2-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="829d2-111">コメント</span><span class="sxs-lookup"><span data-stu-id="829d2-111">Remarks</span></span>  
 <span data-ttu-id="829d2-112">`Skip While`句が指定されたまで、クエリ結果の先頭から要素をバイパス`expression`返します`false`です。</span><span class="sxs-lookup"><span data-stu-id="829d2-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="829d2-113">後に`expression`返します`false`クエリが、残りのすべての要素を返します。</span><span class="sxs-lookup"><span data-stu-id="829d2-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="829d2-114">`expression`残りの結果は無視されます。</span><span class="sxs-lookup"><span data-stu-id="829d2-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="829d2-115">`Skip While`句とは異なります、`Where`を内の句、`Where`を特定の条件を満たさないクエリからすべての要素を除外する句を使用できます。</span><span class="sxs-lookup"><span data-stu-id="829d2-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="829d2-116">`Skip While`句は、条件が満たされていない最初の時刻までの要素を除外します。</span><span class="sxs-lookup"><span data-stu-id="829d2-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="829d2-117">`Skip While`句は、順序付けられたクエリ結果を使用しているときに最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="829d2-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="829d2-118">使用して特定のクエリ結果の先頭からの結果数を省略することができます、`Skip`句。</span><span class="sxs-lookup"><span data-stu-id="829d2-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="829d2-119">例</span><span class="sxs-lookup"><span data-stu-id="829d2-119">Example</span></span>  
 <span data-ttu-id="829d2-120">次のコード例では、`Skip While`米国から最初の顧客が見つかるまで、結果をバイパスする句。</span><span class="sxs-lookup"><span data-stu-id="829d2-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="829d2-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="829d2-121">See Also</span></span>  
 [<span data-ttu-id="829d2-122">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="829d2-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="829d2-123">クエリ</span><span class="sxs-lookup"><span data-stu-id="829d2-123">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="829d2-124">Select 句</span><span class="sxs-lookup"><span data-stu-id="829d2-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="829d2-125">From 句</span><span class="sxs-lookup"><span data-stu-id="829d2-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="829d2-126">Skip 句</span><span class="sxs-lookup"><span data-stu-id="829d2-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="829d2-127">Take While 句</span><span class="sxs-lookup"><span data-stu-id="829d2-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="829d2-128">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="829d2-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
