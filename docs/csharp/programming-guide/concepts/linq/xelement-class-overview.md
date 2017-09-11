---
title: "XElement クラスの概要 (C#)"
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
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
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
ms.openlocfilehash: 20c6c7aed7d00b26d08f3733147616313ad851f3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="31c19-102">XElement クラスの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="31c19-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="31c19-103"><xref:System.Xml.Linq.XElement> クラスは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の基礎クラスの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="31c19-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="31c19-104">これは XML 要素を表します。</span><span class="sxs-lookup"><span data-stu-id="31c19-104">It represents an XML element.</span></span> <span data-ttu-id="31c19-105">このクラスを使用すると、要素の作成、要素のコンテンツの変更、子要素の追加、変更、削除、要素への属性の追加、および要素のコンテンツのテキスト形式へのシリアル化を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="31c19-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="31c19-106"><xref:System.Xml?displayProperty=fullName>、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> などの、<xref:System.Xml.Xsl.XslCompiledTransform> の他のクラスと相互運用することもできます。</span><span class="sxs-lookup"><span data-stu-id="31c19-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=fullName>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="31c19-107">XElement の機能</span><span class="sxs-lookup"><span data-stu-id="31c19-107">XElement Functionality</span></span>  
 <span data-ttu-id="31c19-108">このトピックでは、<xref:System.Xml.Linq.XElement> クラスによって提供される機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="31c19-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="31c19-109">XML ツリーの構築</span><span class="sxs-lookup"><span data-stu-id="31c19-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="31c19-110">次のようなさまざまな方法で XML ツリーを構築できます。</span><span class="sxs-lookup"><span data-stu-id="31c19-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="31c19-111">コードで XML ツリーを構築できます。</span><span class="sxs-lookup"><span data-stu-id="31c19-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="31c19-112">詳しくは、「[XML ツリーの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31c19-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="31c19-113"><xref:System.IO.TextReader>、テキスト ファイル、Web アドレス (URL) など、さまざまなソースから XML を解析できます。</span><span class="sxs-lookup"><span data-stu-id="31c19-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="31c19-114">詳しくは、「[XML の解析 (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31c19-114">For more information, see [Parsing XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="31c19-115"><xref:System.Xml.XmlReader> を使用してツリーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="31c19-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="31c19-116">詳細については、「<xref:System.Xml.Linq.XNode.ReadFrom%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31c19-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="31c19-117"><xref:System.Xml.XmlWriter> にコンテンツを書き込むことができるモジュールがある場合は、<xref:System.Xml.Linq.XContainer.CreateWriter%2A> メソッドを使用してライターを作成し、このライターをモジュールに渡し、<xref:System.Xml.XmlWriter> に書き込まれたコンテンツを使用して XML ツリーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="31c19-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="31c19-118">しかし、XML ツリーを作成する最も一般的な方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="31c19-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),   
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="31c19-119">XML ツリーを作成するもう 1 つの一般的な方法では、次の例に示すように、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリの結果を使用して XML ツリーを設定します。</span><span class="sxs-lookup"><span data-stu-id="31c19-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="31c19-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="31c19-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="31c19-121">XML ツリーのシリアル化</span><span class="sxs-lookup"><span data-stu-id="31c19-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="31c19-122">XML ツリーは、<xref:System.IO.File>、<xref:System.IO.TextWriter>、または <xref:System.Xml.XmlWriter> にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="31c19-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="31c19-123">詳しくは、「[XML ツリーのシリアル化 (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31c19-123">For more information, see [Serializing XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="31c19-124">軸メソッドによる XML データの取得</span><span class="sxs-lookup"><span data-stu-id="31c19-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="31c19-125">軸メソッドを使用すると、属性、子要素、子孫要素、および祖先要素を取得できます。</span><span class="sxs-lookup"><span data-stu-id="31c19-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="31c19-126"> クエリは、軸メソッドに対して機能し、XML ツリーを操作して処理するための、柔軟で強力な複数の機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="31c19-126"> queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="31c19-127">詳しくは、「[LINQ to XML 軸 (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31c19-127">For more information, see [LINQ to XML Axes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="31c19-128">XML ツリーのクエリ</span><span class="sxs-lookup"><span data-stu-id="31c19-128">Querying XML Trees</span></span>  
 <span data-ttu-id="31c19-129">XML ツリーからデータを抽出する [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを記述できます。</span><span class="sxs-lookup"><span data-stu-id="31c19-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="31c19-130">詳しくは、「[XML ツリーのクエリ (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31c19-130">For more information, see [Querying XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="31c19-131">XML ツリーの変更</span><span class="sxs-lookup"><span data-stu-id="31c19-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="31c19-132">要素を変更するには、そのコンテンツや属性を変更するなど、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="31c19-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="31c19-133">要素を親から削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="31c19-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="31c19-134">詳しくは、「[XML ツリーの変更 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="31c19-134">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31c19-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="31c19-135">See Also</span></span>  
 [<span data-ttu-id="31c19-136">LINQ to XML プログラミングの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="31c19-136">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

