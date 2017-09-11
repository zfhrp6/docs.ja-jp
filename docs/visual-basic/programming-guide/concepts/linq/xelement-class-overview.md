---
title: "XElement クラスの概要 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 78a72effa021408943b9248546106c6fd655ac0b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="b3dc4-102">XElement クラスの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3dc4-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="b3dc4-103"><xref:System.Xml.Linq.XElement>クラスは、基礎クラスのいずれかの[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span></span> <span data-ttu-id="b3dc4-104">これは XML 要素を表します。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-104">It represents an XML element.</span></span> <span data-ttu-id="b3dc4-105">このクラスを使用すると、要素の作成、要素のコンテンツの変更、子要素の追加、変更、削除、要素への属性の追加、および要素のコンテンツのテキスト形式へのシリアル化を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="b3dc4-106">他のクラスと相互運用することも<xref:System.Xml?displayProperty=fullName>など<xref:System.Xml.XmlReader>、 <xref:System.Xml.XmlWriter>、 <xref:System.Xml.Xsl.XslCompiledTransform>.</xref:System.Xml.Xsl.XslCompiledTransform> </xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> </xref:System.Xml?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b3dc4-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=fullName>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="b3dc4-107">XElement の機能</span><span class="sxs-lookup"><span data-stu-id="b3dc4-107">XElement Functionality</span></span>  
 <span data-ttu-id="b3dc4-108">このトピックの<xref:System.Xml.Linq.XElement>クラス</xref:System.Xml.Linq.XElement>によって提供される機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="b3dc4-109">XML ツリーの構築</span><span class="sxs-lookup"><span data-stu-id="b3dc4-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="b3dc4-110">次のようなさまざまな方法で XML ツリーを構築できます。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="b3dc4-111">コードで XML ツリーを構築できます。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="b3dc4-112">詳細については、次を参照してください。 [XML ツリーを作成する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)します。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="b3dc4-113">などのさまざまなソースから XML を解析して、 <xref:System.IO.TextReader>、テキスト ファイル、または Web アドレス (URL).</xref:System.IO.TextReader></span><span class="sxs-lookup"><span data-stu-id="b3dc4-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="b3dc4-114">詳細については、次を参照してください。 [XML の解析 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-114">For more information, see [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="b3dc4-115">使用することができます、<xref:System.Xml.XmlReader>ツリーを設定します</xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="b3dc4-116">詳細については、 <xref:System.Xml.Linq.XNode.ReadFrom%2A>。</xref:System.Xml.Linq.XNode.ReadFrom%2A>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="b3dc4-117">コンテンツを書き込むことができるモジュールがあるかどうか、 <xref:System.Xml.XmlWriter>、使用することができます、<xref:System.Xml.Linq.XContainer.CreateWriter%2A>ライターを作成され、このライターをモジュールに渡しに書き込まれたコンテンツが使用するメソッド、 <xref:System.Xml.XmlWriter>XML ツリーを作成する</xref:System.Xml.XmlWriter></xref:System.Xml.Linq.XContainer.CreateWriter%2A></xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="b3dc4-118">しかし、XML ツリーを作成する最も一般的な方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="b3dc4-119">結果を使用して XML ツリーを作成するもう&1; つの一般的な方法では、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]の次の例に示すように、XML ツリーを設定するクエリ。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="b3dc4-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="b3dc4-121">XML ツリーのシリアル化</span><span class="sxs-lookup"><span data-stu-id="b3dc4-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="b3dc4-122">XML ツリーをシリアル化することができます、 <xref:System.IO.File>、 <xref:System.IO.TextWriter>、または<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="b3dc4-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="b3dc4-123">詳細については、次を参照してください。 [XML ツリーをシリアル化する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)します。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-123">For more information, see [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="b3dc4-124">軸メソッドによる XML データの取得</span><span class="sxs-lookup"><span data-stu-id="b3dc4-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="b3dc4-125">軸メソッドを使用すると、属性、子要素、子孫要素、および祖先要素を取得できます。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]<span data-ttu-id="b3dc4-126"> クエリは、軸メソッドに対して機能し、XML ツリーを操作して処理するための、柔軟で強力な複数の機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-126"> queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="b3dc4-127">詳細については、次を参照してください。 [LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)します。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-127">For more information, see [LINQ to XML Axes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="b3dc4-128">XML ツリーのクエリ</span><span class="sxs-lookup"><span data-stu-id="b3dc4-128">Querying XML Trees</span></span>  
 <span data-ttu-id="b3dc4-129">記述する[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]XML ツリーからデータを抽出するクエリ。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-129">You can write [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="b3dc4-130">詳細については、次を参照してください。 [(Visual Basic) の XML ツリーのクエリを実行する](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)です。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-130">For more information, see [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="b3dc4-131">XML ツリーの変更</span><span class="sxs-lookup"><span data-stu-id="b3dc4-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="b3dc4-132">要素を変更するには、そのコンテンツや属性を変更するなど、さまざまな方法があります。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="b3dc4-133">要素を親から削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="b3dc4-134">詳細については、次を参照してください。 [XML ツリーの変更 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="b3dc4-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3dc4-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3dc4-135">See Also</span></span>  
 [<span data-ttu-id="b3dc4-136">LINQ to XML プログラミングの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3dc4-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
