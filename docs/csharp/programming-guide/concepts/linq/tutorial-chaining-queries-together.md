---
title: "チュートリアル: クエリの連結 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6048ce6a5b477daef5271f75ea1e988725452fcd
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="dd064-102">チュートリアル: クエリの連結 (C#)</span><span class="sxs-lookup"><span data-stu-id="dd064-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="dd064-103">このチュートリアルでは、クエリを連結する際の処理モデルを紹介します。</span><span class="sxs-lookup"><span data-stu-id="dd064-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="dd064-104">クエリの連結は、関数型変換を記述する際の重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="dd064-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="dd064-105">連結されたクエリがどのように動作するのかを正確に把握することが重要です。</span><span class="sxs-lookup"><span data-stu-id="dd064-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="dd064-106">Office Open XML ドキュメントを処理するクエリでは、この手法が広範に使用されます。</span><span class="sxs-lookup"><span data-stu-id="dd064-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd064-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="dd064-107">In This Section</span></span>  
  
|<span data-ttu-id="dd064-108">トピック</span><span class="sxs-lookup"><span data-stu-id="dd064-108">Topic</span></span>|<span data-ttu-id="dd064-109">説明</span><span class="sxs-lookup"><span data-stu-id="dd064-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dd064-110">LINQ to XML における遅延実行とレイジー評価 (C#)</span><span class="sxs-lookup"><span data-stu-id="dd064-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="dd064-111">遅延実行とレイジー評価の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd064-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="dd064-112">遅延実行の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="dd064-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="dd064-113">遅延実行の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="dd064-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="dd064-114">クエリの連結の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="dd064-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="dd064-115">クエリを連結した場合に遅延実行がどのように動作するのかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dd064-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="dd064-116">中間結果の具体化 (C#)</span><span class="sxs-lookup"><span data-stu-id="dd064-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="dd064-117">中間結果の具体化のセマンティクスについて説明し、その例を示します。</span><span class="sxs-lookup"><span data-stu-id="dd064-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="dd064-118">標準クエリ演算子の連結 (C#)</span><span class="sxs-lookup"><span data-stu-id="dd064-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="dd064-119">標準クエリ演算子のレイジー セマンティクスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dd064-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd064-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd064-120">See Also</span></span>  
 [<span data-ttu-id="dd064-121">XML の純粋関数型変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="dd064-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)

