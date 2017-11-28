---
title: "チュートリアル: クエリの連結 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 44f54444-c4c5-4c23-9d19-986b957b8eda
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 08196f4780e566cc05e36b6cfe78caad3e9c96a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="tutorial-chaining-queries-together-c"></a><span data-ttu-id="43651-102">チュートリアル: クエリの連結 (C#)</span><span class="sxs-lookup"><span data-stu-id="43651-102">Tutorial: Chaining Queries Together (C#)</span></span>
<span data-ttu-id="43651-103">このチュートリアルでは、クエリを連結する際の処理モデルを紹介します。</span><span class="sxs-lookup"><span data-stu-id="43651-103">This tutorial illustrates the processing model when you chain queries together.</span></span> <span data-ttu-id="43651-104">クエリの連結は、関数型変換を記述する際の重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="43651-104">Chaining queries together is a key part of writing functional transformations.</span></span> <span data-ttu-id="43651-105">連結されたクエリがどのように動作するのかを正確に把握することが重要です。</span><span class="sxs-lookup"><span data-stu-id="43651-105">It is important to understand exactly how chained queries work.</span></span>  
  
 <span data-ttu-id="43651-106">Office Open XML ドキュメントを処理するクエリでは、この手法が広範に使用されます。</span><span class="sxs-lookup"><span data-stu-id="43651-106">The queries that process Office Open XML documents use this technique extensively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43651-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="43651-107">In This Section</span></span>  
  
|<span data-ttu-id="43651-108">トピック</span><span class="sxs-lookup"><span data-stu-id="43651-108">Topic</span></span>|<span data-ttu-id="43651-109">説明</span><span class="sxs-lookup"><span data-stu-id="43651-109">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="43651-110">LINQ to XML における遅延実行とレイジー評価 (C#)</span><span class="sxs-lookup"><span data-stu-id="43651-110">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)|<span data-ttu-id="43651-111">遅延実行とレイジー評価の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="43651-111">Describes the concepts of deferred execution and lazy evaluation.</span></span>|  
|[<span data-ttu-id="43651-112">遅延実行の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="43651-112">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)|<span data-ttu-id="43651-113">遅延実行の例について説明します。</span><span class="sxs-lookup"><span data-stu-id="43651-113">Provides an example of deferred execution.</span></span>|  
|[<span data-ttu-id="43651-114">クエリの連結の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="43651-114">Chaining Queries Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)|<span data-ttu-id="43651-115">クエリを連結した場合に遅延実行がどのように動作するのかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="43651-115">Shows how deferred execution works when chaining queries together.</span></span>|  
|[<span data-ttu-id="43651-116">中間結果の具体化 (C#)</span><span class="sxs-lookup"><span data-stu-id="43651-116">Intermediate Materialization (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)|<span data-ttu-id="43651-117">中間結果の具体化のセマンティクスについて説明し、その例を示します。</span><span class="sxs-lookup"><span data-stu-id="43651-117">Identifies and illustrates the semantics of intermediate materialization.</span></span>|  
|[<span data-ttu-id="43651-118">標準クエリ演算子の連結 (C#)</span><span class="sxs-lookup"><span data-stu-id="43651-118">Chaining Standard Query Operators Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/chaining-standard-query-operators-together.md)|<span data-ttu-id="43651-119">標準クエリ演算子のレイジー セマンティクスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="43651-119">Describes the lazy semantics of the standard query operators.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43651-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="43651-120">See Also</span></span>  
 [<span data-ttu-id="43651-121">XML の純粋関数型変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="43651-121">Pure Functional Transformations of XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)
