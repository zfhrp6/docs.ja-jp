---
title: LINQ to XML およびDOM (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: f62b7564e9ba7adfe1aa83c5d0336d7a43e7c362
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652774"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="5cd5f-102">LINQ to XML およびDOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cd5f-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="5cd5f-103">このセクションでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] と、現在主流の XML プログラミング API である W3C ドキュメント オブジェクト モデル (DOM) との主な違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="5cd5f-104">XML ツリーを構築するための新しい方法</span><span class="sxs-lookup"><span data-stu-id="5cd5f-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="5cd5f-105">W3C DOM では、XML ツリーをボトムアップ方式で作成します。つまり、ドキュメントを作成し、要素を作成して、要素をドキュメントに追加することによって作成します。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="5cd5f-106">たとえば、Microsoft の DOM の実装である <xref:System.Xml.XmlDocument> を使用して XML ツリーを作成する場合、一般的な方法は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 <span data-ttu-id="5cd5f-107">このコーディング スタイルでは、XML ツリーの構造の多くを視覚的に認識できません。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-108"> では、このような XML ツリーの構築方法をサポートしていますが、別の方法として*関数型構築*もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="5cd5f-109">Visual basic では、関数型構築は、XML ツリーを構築するのに XML リテラルを使用します。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="5cd5f-110">上記の例と同じ XML ツリーを [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の関数型構築を使用して構築すると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 <span data-ttu-id="5cd5f-111">このように、XML ツリーを構築するコードのインデントにより、基になる XML の構造が示されます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="5cd5f-112">詳細については、次を参照してください。 [XML ツリーを作成する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)です。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="5cd5f-113">XML 要素の直接操作</span><span class="sxs-lookup"><span data-stu-id="5cd5f-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="5cd5f-114">一般に、XML によるプログラミングで重視されるのは XML 要素であり、その属性が重要となる場合が多くあります。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="5cd5f-115">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] では、XML 要素と XML 属性を直接操作できます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="5cd5f-116">たとえば、次のようなことが可能です。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="5cd5f-117">ドキュメント オブジェクトを一切使用せずに XML 要素を作成する。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="5cd5f-118">これにより、XML ツリーのフラグメントを操作する際のプログラミングが単純化されます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="5cd5f-119">`T:System.Xml.Linq.XElement` オブジェクトを直接 XML ファイルから読み込む。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="5cd5f-120">`T:System.Xml.Linq.XElement` オブジェクトをファイルやストリームにシリアル化する。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="5cd5f-121">これに対して、XML ドキュメントが XML ツリーの論理的コンテナーとして使用される W3C DOM では、</span><span class="sxs-lookup"><span data-stu-id="5cd5f-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="5cd5f-122">XML ノード (要素や属性を含む) は XML ドキュメントのコンテキストで作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="5cd5f-123">DOM で name 要素を作成するコード フラグメントを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="5cd5f-124">要素を複数のドキュメントで使用する場合は、ノードをドキュメント間でインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-125"> では、こうした複雑さを回避できます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="5cd5f-126">LINQ to XML を使用する場合、<xref:System.Xml.Linq.XDocument> クラスを使用するのは、ドキュメントのルート レベルにコメントや処理命令を追加する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="5cd5f-127">名前と名前空間の処理の単純化</span><span class="sxs-lookup"><span data-stu-id="5cd5f-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="5cd5f-128">一般に XML プログラミングでは、名前、名前空間、および名前空間プレフィックスの処理が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-129"> を使用すると、名前空間プレフィックスを処理する必要がなくなるため、名前と名前空間が単純化されます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="5cd5f-130">必要に応じて名前空間プレフィックスを制御することはできますが、</span><span class="sxs-lookup"><span data-stu-id="5cd5f-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="5cd5f-131">明示的に制御しないようにすることもできます。その場合、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] がシリアル中に名前空間プレフィックスを必要に応じて割り当てます。必要ない場合は、既定の名前空間を使用してシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="5cd5f-132">既定の名前空間が使用された場合は、結果のドキュメントには名前空間プレフィックスは含まれません。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="5cd5f-133">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の操作](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)です。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-133">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="5cd5f-134">DOM にはその他に、ノードの名前を変更できないという問題もあります。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="5cd5f-135">ノード名の変更が必要な場合は、新しいノードを作成し、そこにすべての子ノードをコピーする必要があります。この場合、元のノード固有の特性は失われます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-136"> では、この問題を回避するために、ノードに対して <xref:System.Xml.Linq.XName> プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="5cd5f-137">XML を読み込むための静的メソッドのサポート</span><span class="sxs-lookup"><span data-stu-id="5cd5f-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-138"> では、インスタンス メソッドの代わりに静的メソッドを使用して XML を読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="5cd5f-139">これにより、読み込みと解析が簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="5cd5f-140">詳細については、次を参照してください。[する方法: ファイル (Visual Basic) から XML を読み込み](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)です。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-140">For more information, see [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="5cd5f-141">DTD の構成要素に関するサポートの削除</span><span class="sxs-lookup"><span data-stu-id="5cd5f-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-142"> では、XML プログラミングのさらなる簡略化のために、エンティティとエンティティ参照のサポートが削除されています。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="5cd5f-143">エンティティの管理は複雑で、ほとんど利用されていません。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="5cd5f-144">これらのサポートを削除することにより、パフォーマンスが向上し、プログラミング インターフェイスが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="5cd5f-145">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ツリーが設定されると、すべての DTD エンティティが展開されます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="5cd5f-146">フラグメントのサポート</span><span class="sxs-lookup"><span data-stu-id="5cd5f-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-147"> には、`XmlDocumentFragment` クラスに対応する要素はありません。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="5cd5f-148">ただし、`XmlDocumentFragment` の概念は、多くの場合、<xref:System.Xml.Linq.XNode> の <xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> として型指定されたクエリの結果によって処理できます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="5cd5f-149">XPathNavigator のサポート</span><span class="sxs-lookup"><span data-stu-id="5cd5f-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-150"> では、<xref:System.Xml.XPath?displayProperty=nameWithType> 名前空間の拡張メソッドによって <xref:System.Xml.XPath.XPathNavigator> がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="5cd5f-151">詳細については、「<xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="5cd5f-152">空白とインデントのサポート</span><span class="sxs-lookup"><span data-stu-id="5cd5f-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-153"> では、空白の処理が DOM より単純化されています。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="5cd5f-154">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="5cd5f-155">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="5cd5f-156">これが [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="5cd5f-157">もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="5cd5f-158">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="5cd5f-159">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-160"> では、空白は <xref:System.Xml.Linq.XText> ノードとして格納されます。DOM とは違って、特殊なノード型である <xref:System.Xml.XmlNodeType.Whitespace> は使用されません。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="5cd5f-161">注釈のサポート</span><span class="sxs-lookup"><span data-stu-id="5cd5f-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-162"> 要素は、注釈の拡張可能なセットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="5cd5f-163">このサポートは、スキーマの情報、要素が UI にバインドされているかどうかの情報、またはアプリケーション固有のその他の情報など、要素に関するさまざまな情報を追跡する場合に利用できます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="5cd5f-164">詳細については、「[LINQ to XML 注釈](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-164">For more information, see [LINQ to XML Annotations](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="5cd5f-165">スキーマ情報のサポート</span><span class="sxs-lookup"><span data-stu-id="5cd5f-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="5cd5f-166"> では、<xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間の拡張メソッドによって XSD 検証がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="5cd5f-167">これにより、XML ツリーが XSD に準拠しているかどうかを検証できます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="5cd5f-168">また、スキーマ検証後の情報セット (PSVI) を使用して XML ツリーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="5cd5f-169">詳細については、「[方法: XSD を使用して検証する](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b)」および「<xref:System.Xml.Schema.Extensions>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cd5f-169">For more information, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd5f-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cd5f-170">See Also</span></span>  
 [<span data-ttu-id="5cd5f-171">はじめに (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5cd5f-171">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
