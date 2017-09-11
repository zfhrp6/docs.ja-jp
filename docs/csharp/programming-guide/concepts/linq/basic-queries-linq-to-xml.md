---
title: "基本的なクエリ (LINQ to XML) (C#)"
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
ms.assetid: d333bb7d-20c1-448a-95b7-e5ba07915744
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 272cfadeccb505960f7872274a2af8c18efc3679
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="basic-queries-linq-to-xml-c"></a><span data-ttu-id="8ffb4-102">基本的なクエリ (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-102">Basic Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8ffb4-103">ここでは、基本的な [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリの例について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-103">This section provides examples of basic [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ffb4-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8ffb4-104">In This Section</span></span>  
  
|<span data-ttu-id="8ffb4-105">トピック</span><span class="sxs-lookup"><span data-stu-id="8ffb4-105">Topic</span></span>|<span data-ttu-id="8ffb4-106">説明</span><span class="sxs-lookup"><span data-stu-id="8ffb4-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8ffb4-107">方法: 特定の属性を持つ要素を検索する (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-107">How to: Find an Element with a Specific Attribute (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-attribute.md)|<span data-ttu-id="8ffb4-108">特定の値を含む属性を持つ特定の要素を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-108">Shows how to find a particular element that has an attribute that has a specific value.</span></span>|  
|[<span data-ttu-id="8ffb4-109">方法: 特定の子要素を持つ要素を検索する (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-109">How to: Find an Element with a Specific Child Element (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-child-element.md)|<span data-ttu-id="8ffb4-110">特定の値を含む子要素を持つ特定の要素を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-110">Shows how to find a particular element that has a child element that has a specific value.</span></span>|  
|[<span data-ttu-id="8ffb4-111">XDocument のクエリと XElement のクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-111">Querying an XDocument vs. Querying an XElement (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-an-xdocument-vs-querying-an-xelement.md)|<span data-ttu-id="8ffb4-112"><xref:System.Xml.Linq.XElement> をルートとする XML ツリーに対するクエリの記述と、<xref:System.Xml.Linq.XDocument> をルートとする XML ツリーに対するクエリの記述の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-112">Explains the differences between writing queries on an XML tree that is rooted in <xref:System.Xml.Linq.XElement> and writing queries on an XML tree that is rooted in <xref:System.Xml.Linq.XDocument>.</span></span>|  
|[<span data-ttu-id="8ffb4-113">方法: 特定の要素名を持つ子孫を検索する (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-113">How to: Find Descendants with a Specific Element Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-descendants-with-a-specific-element-name.md)|<span data-ttu-id="8ffb4-114">特定の名前を持つ要素のすべての子孫を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-114">Shows how to find all the descendants of an element that have a specific name.</span></span> <span data-ttu-id="8ffb4-115">この例では、<xref:System.Xml.Linq.XContainer.Descendants%2A> 軸を使用します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-115">This example uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>|  
|[<span data-ttu-id="8ffb4-116">方法: Descendants メソッドを使用して単一の子孫を検索する (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-116">How to: Find a Single Descendant Using the Descendants Method (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-a-single-descendant-using-the-descendants-method.md)|<span data-ttu-id="8ffb4-117"><xref:System.Xml.Linq.XContainer.Descendants%2A> 軸メソッドを使用して一意の名前を持つ単一の要素を検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-117">Shows how to use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to find a single uniquely named element.</span></span>|  
|[<span data-ttu-id="8ffb4-118">方法: 複雑なフィルターを使用してクエリを記述する (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-118">How to: Write Queries with Complex Filtering (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-write-queries-with-complex-filtering.md)|<span data-ttu-id="8ffb4-119">複雑なフィルターを使用してクエリを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-119">Shows how to write a query with a more complex filter.</span></span>|  
|[<span data-ttu-id="8ffb4-120">方法: 省略可能な要素をフィルター処理する (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-120">How to: Filter on an Optional Element (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-an-optional-element.md)|<span data-ttu-id="8ffb4-121">不規則な形のツリーでノードを検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-121">Shows how to find nodes in an irregularly shaped tree.</span></span>|  
|[<span data-ttu-id="8ffb4-122">方法: 名前空間内のすべてのノードを検索する (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-122">How to: Find All Nodes in a Namespace (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-all-nodes-in-a-namespace.md)|<span data-ttu-id="8ffb4-123">特定の名前空間内のすべてのノードを検索する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-123">Shows how to find all nodes that are in a specific namespace.</span></span>|  
|[<span data-ttu-id="8ffb4-124">方法: 要素を並べ替える (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-124">How to: Sort Elements (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-elements.md)|<span data-ttu-id="8ffb4-125">結果を並べ替えるクエリを記述する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-125">Shows how to write a query that sorts its results.</span></span>|  
|[<span data-ttu-id="8ffb4-126">方法: 複数のキーに基づいて要素を並べ替える (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-126">How to: Sort Elements on Multiple Keys (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-elements-on-multiple-keys.md)|<span data-ttu-id="8ffb4-127">複数のキーに基づく並べ替えの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-127">Shows how to sort on multiple keys.</span></span>|  
|[<span data-ttu-id="8ffb4-128">方法: 中間値を計算する (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-128">How to: Calculate Intermediate Values (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-calculate-intermediate-values.md)|<span data-ttu-id="8ffb4-129">`Let` 句を使って [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリの中間値を計算する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-129">Shows how to use the `Let` clause to calculate intermediate values in a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query.</span></span>|  
|[<span data-ttu-id="8ffb4-130">方法: コンテキストに基づいて要素を検索するクエリを記述する (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-130">How to: Write a Query that Finds Elements Based on Context (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-write-a-query-that-finds-elements-based-on-context.md)|<span data-ttu-id="8ffb4-131">ツリー内の他の要素に基づいて要素を選択する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-131">Shows how to select elements based on other elements in the tree.</span></span>|  
|[<span data-ttu-id="8ffb4-132">方法: 空のクエリ結果セットをデバッグする (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-132">How to: Debug Empty Query Results Sets (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-debug-empty-query-results-sets.md)|<span data-ttu-id="8ffb4-133">既定の名前空間の XML に対するクエリをデバッグする際の適切な修正方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ffb4-133">Shows the appropriate fix when debugging queries on XML that is in a default namespace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ffb4-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ffb4-134">See Also</span></span>  
 [<span data-ttu-id="8ffb4-135">XML ツリーのクエリ (C#)</span><span class="sxs-lookup"><span data-stu-id="8ffb4-135">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)

