---
title: "LINQ to XML 軸 (C#)"
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
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 65d64b6082942d702444305d7dfed4d05444b59e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="linq-to-xml-axes-c"></a><span data-ttu-id="b45ea-102">LINQ to XML 軸 (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-102">LINQ to XML Axes (C#)</span></span>
<span data-ttu-id="b45ea-103">XML ツリーを作成した後、または XML ドキュメントを XML ツリーに読み込んだ後は、クエリを実行して要素や属性を調べたり、その値を取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="b45ea-103">After you have created an XML tree or loaded an XML document into an XML tree, you can query it to find elements and attributes and retrieve their values.</span></span>  
  
 <span data-ttu-id="b45ea-104">クエリを記述する前に、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 軸について理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b45ea-104">Before you can write any queries, you must understand the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes.</span></span> <span data-ttu-id="b45ea-105">軸メソッドは 2 種類あります。まず、単一の <xref:System.Xml.Linq.XElement> オブジェクト、<xref:System.Xml.Linq.XDocument> オブジェクト、または <xref:System.Xml.Linq.XNode> オブジェクトで呼び出すメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="b45ea-105">There are two kinds of axis methods: First, there are the methods that you call on a single <xref:System.Xml.Linq.XElement> object, <xref:System.Xml.Linq.XDocument> object, or <xref:System.Xml.Linq.XNode> object.</span></span> <span data-ttu-id="b45ea-106">これらのメソッドは、単一のオブジェクトに対して機能し、<xref:System.Xml.Linq.XElement>、<xref:System.Xml.Linq.XAttribute>、または <xref:System.Xml.Linq.XNode> オブジェクトのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-106">These methods operate on a single object and return a collection of <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, or <xref:System.Xml.Linq.XNode> objects.</span></span> <span data-ttu-id="b45ea-107">第 2 に、コレクションに対して機能し、コレクションを返す拡張メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="b45ea-107">Second, there are extension methods that operate on collections and return collections.</span></span> <span data-ttu-id="b45ea-108">拡張メソッドは、ソース コレクションを列挙し、コレクション内の各アイテムに対して適切な軸メソッドを呼び出し、結果を連結します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-108">The extension methods enumerate the source collection, call the appropriate axis method on each item in the collection, and concatenate the results.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b45ea-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b45ea-109">In This Section</span></span>  
  
|<span data-ttu-id="b45ea-110">トピック</span><span class="sxs-lookup"><span data-stu-id="b45ea-110">Topic</span></span>|<span data-ttu-id="b45ea-111">説明</span><span class="sxs-lookup"><span data-stu-id="b45ea-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b45ea-112">LINQ to XML 軸の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-112">LINQ to XML Axes Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|<span data-ttu-id="b45ea-113">軸を定義し、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] クエリのコンテキストにおける使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-113">Defines axes, and explains how they are used in the context of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] queries.</span></span>|  
|[<span data-ttu-id="b45ea-114">方法: 要素のコレクションを取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-114">How to: Retrieve a Collection of Elements (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|<span data-ttu-id="b45ea-115"><xref:System.Xml.Linq.XContainer.Elements%2A> メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-115">Introduces the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span> <span data-ttu-id="b45ea-116">このメソッドは、要素の子要素のコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-116">This method retrieves a collection of the child elements of an element.</span></span>|  
|[<span data-ttu-id="b45ea-117">方法: 要素の値を取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-117">How to: Retrieve the Value of an Element (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|<span data-ttu-id="b45ea-118">要素の値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-118">Shows how to get the values of elements.</span></span>|  
|[<span data-ttu-id="b45ea-119">方法: 要素名をフィルター処理する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-119">How to: Filter on Element Names (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|<span data-ttu-id="b45ea-120">軸を使用する場合に要素名をフィルター処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-120">Shows how to filter on element names when using axes.</span></span>|  
|[<span data-ttu-id="b45ea-121">方法: 軸メソッドの呼び出しを連結する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-121">How to: Chain Axis Method Calls (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|<span data-ttu-id="b45ea-122">軸メソッドの呼び出しを連結する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-122">Shows how to chain calls to axes methods.</span></span>|  
|[<span data-ttu-id="b45ea-123">方法: 単一の子要素を取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-123">How to: Retrieve a Single Child Element (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|<span data-ttu-id="b45ea-124">タグ名を指定して要素の単一の子要素を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-124">Shows how to retrieve a single child element of an element, given the tag name of the child element.</span></span>|  
|[<span data-ttu-id="b45ea-125">方法: 属性のコレクションを取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-125">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|<span data-ttu-id="b45ea-126"><xref:System.Xml.Linq.XElement.Attributes%2A> メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-126">Introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="b45ea-127">このメソッドは、要素の属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-127">This method retrieves the attributes of an element.</span></span>|  
|[<span data-ttu-id="b45ea-128">方法: 単一の属性を取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-128">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|<span data-ttu-id="b45ea-129">属性名を指定して要素の単一の属性を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-129">Shows how to retrieve a single attribute of an element, given the attribute name.</span></span>|  
|[<span data-ttu-id="b45ea-130">方法: 属性の値を取得する (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-130">How to: Retrieve the Value of an Attribute (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|<span data-ttu-id="b45ea-131">属性の値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-131">Shows how to get the values of attributes.</span></span>|  
|[<span data-ttu-id="b45ea-132">方法: 要素の浅い値を取得する (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-132">How to: Retrieve the Shallow Value of an Element (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|<span data-ttu-id="b45ea-133">要素の浅い値を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b45ea-133">Shows how to retrieve the shallow value of an element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b45ea-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b45ea-134">See Also</span></span>  
 <span data-ttu-id="b45ea-135">[拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="b45ea-135">[Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md) </span></span>  
 [<span data-ttu-id="b45ea-136">プログラミング ガイド (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b45ea-136">Programming Guide (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

