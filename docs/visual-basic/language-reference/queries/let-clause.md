---
title: "Let 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70e47517a62f58dcababd31c26277417b62eab66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="0e98b-102">Let 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e98b-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="0e98b-103">値を計算し、クエリ内で新しい変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="0e98b-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e98b-104">構文</span><span class="sxs-lookup"><span data-stu-id="0e98b-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="0e98b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="0e98b-105">Parts</span></span>  
  
|<span data-ttu-id="0e98b-106">用語</span><span class="sxs-lookup"><span data-stu-id="0e98b-106">Term</span></span>|<span data-ttu-id="0e98b-107">定義</span><span class="sxs-lookup"><span data-stu-id="0e98b-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="0e98b-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="0e98b-108">Required.</span></span> <span data-ttu-id="0e98b-109">指定した式の結果を参照に使用できるエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="0e98b-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="0e98b-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="0e98b-110">Required.</span></span> <span data-ttu-id="0e98b-111">評価し、指定された変数に割り当てられている式です。</span><span class="sxs-lookup"><span data-stu-id="0e98b-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e98b-112">コメント</span><span class="sxs-lookup"><span data-stu-id="0e98b-112">Remarks</span></span>  
 <span data-ttu-id="0e98b-113">`Let`句では、計算値はそれぞれのクエリの結果とエイリアスを使用してそれらを参照することができます。</span><span class="sxs-lookup"><span data-stu-id="0e98b-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="0e98b-114">エイリアスをなどの他の句で使用できます、`Where`句。</span><span class="sxs-lookup"><span data-stu-id="0e98b-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="0e98b-115">`Let`句では、クエリに含まれる式の句の別名を指定し、式の句が使用されるたびに、エイリアスに置き換えるために読みやすくクエリ ステートメントを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0e98b-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="0e98b-116">任意の数を含めることができます`variable`と`expression`の割り当て、`Let`句。</span><span class="sxs-lookup"><span data-stu-id="0e98b-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="0e98b-117">コンマ (,) では、各割り当てを区切ります。</span><span class="sxs-lookup"><span data-stu-id="0e98b-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e98b-118">例</span><span class="sxs-lookup"><span data-stu-id="0e98b-118">Example</span></span>  
 <span data-ttu-id="0e98b-119">次のコード例では、`Let`句の製品に 10% の割引を計算します。</span><span class="sxs-lookup"><span data-stu-id="0e98b-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0e98b-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e98b-120">See Also</span></span>  
 [<span data-ttu-id="0e98b-121">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="0e98b-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="0e98b-122">クエリ</span><span class="sxs-lookup"><span data-stu-id="0e98b-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="0e98b-123">Select 句</span><span class="sxs-lookup"><span data-stu-id="0e98b-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="0e98b-124">From 句</span><span class="sxs-lookup"><span data-stu-id="0e98b-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="0e98b-125">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="0e98b-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
