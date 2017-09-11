---
title: "LINQ to XML およびDOM (C#)"
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
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
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
ms.openlocfilehash: e27bf46390bca80ca573ab557953f70f591c9ae2
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="f8d31-102">LINQ to XML およびDOM (C#)</span><span class="sxs-lookup"><span data-stu-id="f8d31-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="f8d31-103">このセクションでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] と、現在主流の XML プログラミング API である W3C ドキュメント オブジェクト モデル (DOM) との主な違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f8d31-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="f8d31-104">XML ツリーを構築するための新しい方法</span><span class="sxs-lookup"><span data-stu-id="f8d31-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="f8d31-105">W3C DOM では、XML ツリーをボトムアップ方式で作成します。つまり、ドキュメントを作成し、要素を作成して、要素をドキュメントに追加することによって作成します。</span><span class="sxs-lookup"><span data-stu-id="f8d31-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="f8d31-106">たとえば、Microsoft の DOM の実装である <xref:System.Xml.XmlDocument> を使用して XML ツリーを作成する場合、一般的な方法は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f8d31-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";          
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";          
XmlElement street1 = doc.CreateElement("Street1");          
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 <span data-ttu-id="f8d31-107">このコーディング スタイルでは、XML ツリーの構造の多くを視覚的に認識できません。</span><span class="sxs-lookup"><span data-stu-id="f8d31-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-108"> では、このような XML ツリーの構築方法をサポートしていますが、別の方法として*関数型構築*もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f8d31-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="f8d31-109">関数型構築では、<xref:System.Xml.Linq.XElement> コンストラクターと <xref:System.Xml.Linq.XAttribute> コンストラクターを使用して XML ツリーを構築します。</span><span class="sxs-lookup"><span data-stu-id="f8d31-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="f8d31-110">上記の例と同じ XML ツリーを [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の関数型構築を使用して構築すると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f8d31-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144",   
                new XAttribute("Type", "Home")),  
            new XElement("phone", "425-555-0145",  
                new XAttribute("Type", "Work")),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="f8d31-111">このように、XML ツリーを構築するコードのインデントにより、基になる XML の構造が示されます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="f8d31-112">詳細については、「[XML ツリーの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8d31-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="f8d31-113">XML 要素の直接操作</span><span class="sxs-lookup"><span data-stu-id="f8d31-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="f8d31-114">一般に、XML によるプログラミングで重視されるのは XML 要素であり、その属性が重要となる場合が多くあります。</span><span class="sxs-lookup"><span data-stu-id="f8d31-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="f8d31-115">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] では、XML 要素と XML 属性を直接操作できます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="f8d31-116">たとえば、次のようなことが可能です。</span><span class="sxs-lookup"><span data-stu-id="f8d31-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="f8d31-117">ドキュメント オブジェクトを一切使用せずに XML 要素を作成する。</span><span class="sxs-lookup"><span data-stu-id="f8d31-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="f8d31-118">これにより、XML ツリーのフラグメントを操作する際のプログラミングが単純化されます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="f8d31-119">`T:System.Xml.Linq.XElement` オブジェクトを直接 XML ファイルから読み込む。</span><span class="sxs-lookup"><span data-stu-id="f8d31-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="f8d31-120">`T:System.Xml.Linq.XElement` オブジェクトをファイルやストリームにシリアル化する。</span><span class="sxs-lookup"><span data-stu-id="f8d31-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="f8d31-121">これに対して、XML ドキュメントが XML ツリーの論理的コンテナーとして使用される W3C DOM では、</span><span class="sxs-lookup"><span data-stu-id="f8d31-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="f8d31-122">XML ノード (要素や属性を含む) は XML ドキュメントのコンテキストで作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8d31-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="f8d31-123">DOM で name 要素を作成するコード フラグメントを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="f8d31-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="f8d31-124">要素を複数のドキュメントで使用する場合は、ノードをドキュメント間でインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8d31-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-125"> では、こうした複雑さを回避できます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="f8d31-126">LINQ to XML を使用する場合、<xref:System.Xml.Linq.XDocument> クラスを使用するのは、ドキュメントのルート レベルにコメントや処理命令を追加する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="f8d31-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="f8d31-127">名前と名前空間の処理の単純化</span><span class="sxs-lookup"><span data-stu-id="f8d31-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="f8d31-128">一般に XML プログラミングでは、名前、名前空間、および名前空間プレフィックスの処理が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="f8d31-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-129"> を使用すると、名前空間プレフィックスを処理する必要がなくなるため、名前と名前空間が単純化されます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="f8d31-130">必要に応じて名前空間プレフィックスを制御することはできますが、</span><span class="sxs-lookup"><span data-stu-id="f8d31-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="f8d31-131">明示的に制御しないようにすることもできます。その場合、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] がシリアル中に名前空間プレフィックスを必要に応じて割り当てます。必要ない場合は、既定の名前空間を使用してシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="f8d31-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="f8d31-132">既定の名前空間が使用された場合は、結果のドキュメントには名前空間プレフィックスは含まれません。</span><span class="sxs-lookup"><span data-stu-id="f8d31-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="f8d31-133">詳細については、「[XML 名前空間の使用 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8d31-133">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="f8d31-134">DOM にはその他に、ノードの名前を変更できないという問題もあります。</span><span class="sxs-lookup"><span data-stu-id="f8d31-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="f8d31-135">ノード名の変更が必要な場合は、新しいノードを作成し、そこにすべての子ノードをコピーする必要があります。この場合、元のノード固有の特性は失われます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-136"> では、この問題を回避するために、ノードに対して <xref:System.Xml.Linq.XName> プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="f8d31-137">XML を読み込むための静的メソッドのサポート</span><span class="sxs-lookup"><span data-stu-id="f8d31-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-138"> では、インスタンス メソッドの代わりに静的メソッドを使用して XML を読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="f8d31-139">これにより、読み込みと解析が簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="f8d31-140">詳細については、「[方法: ファイルから XML を読み込む](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8d31-140">For more information, see [How to: Load XML from a File (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="f8d31-141">DTD の構成要素に関するサポートの削除</span><span class="sxs-lookup"><span data-stu-id="f8d31-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-142"> では、XML プログラミングのさらなる簡略化のために、エンティティとエンティティ参照のサポートが削除されています。</span><span class="sxs-lookup"><span data-stu-id="f8d31-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="f8d31-143">エンティティの管理は複雑で、ほとんど利用されていません。</span><span class="sxs-lookup"><span data-stu-id="f8d31-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="f8d31-144">これらのサポートを削除することにより、パフォーマンスが向上し、プログラミング インターフェイスが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="f8d31-145">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ツリーが設定されると、すべての DTD エンティティが展開されます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="f8d31-146">フラグメントのサポート</span><span class="sxs-lookup"><span data-stu-id="f8d31-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-147"> には、`XmlDocumentFragment` クラスに対応する要素はありません。</span><span class="sxs-lookup"><span data-stu-id="f8d31-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="f8d31-148">ただし、`XmlDocumentFragment` の概念は、多くの場合、<xref:System.Xml.Linq.XNode> の <xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Xml.Linq.XElement> の <xref:System.Collections.Generic.IEnumerable%601> として型指定されたクエリの結果によって処理できます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="f8d31-149">XPathNavigator のサポート</span><span class="sxs-lookup"><span data-stu-id="f8d31-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-150"> では、<xref:System.Xml.XPath?displayProperty=fullName> 名前空間の拡張メソッドによって <xref:System.Xml.XPath.XPathNavigator> がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f8d31-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="f8d31-151">詳細については、「<xref:System.Xml.XPath.Extensions?displayProperty=fullName>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8d31-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="f8d31-152">空白とインデントのサポート</span><span class="sxs-lookup"><span data-stu-id="f8d31-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-153"> では、空白の処理が DOM より単純化されています。</span><span class="sxs-lookup"><span data-stu-id="f8d31-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="f8d31-154">一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。</span><span class="sxs-lookup"><span data-stu-id="f8d31-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="f8d31-155">書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="f8d31-156">これが [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="f8d31-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="f8d31-157">もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。</span><span class="sxs-lookup"><span data-stu-id="f8d31-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="f8d31-158">場合によっては、このインデントを一切変更しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8d31-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="f8d31-159">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。</span><span class="sxs-lookup"><span data-stu-id="f8d31-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-160"> では、空白は <xref:System.Xml.Linq.XText> ノードとして格納されます。DOM とは違って、特殊なノード型である <xref:System.Xml.XmlNodeType.Whitespace> は使用されません。</span><span class="sxs-lookup"><span data-stu-id="f8d31-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="f8d31-161">注釈のサポート</span><span class="sxs-lookup"><span data-stu-id="f8d31-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-162"> 要素は、注釈の拡張可能なセットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f8d31-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="f8d31-163">このサポートは、スキーマの情報、要素が UI にバインドされているかどうかの情報、またはアプリケーション固有のその他の情報など、要素に関するさまざまな情報を追跡する場合に利用できます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="f8d31-164">詳細については、「[LINQ to XML 注釈](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8d31-164">For more information, see [LINQ to XML Annotations](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="f8d31-165">スキーマ情報のサポート</span><span class="sxs-lookup"><span data-stu-id="f8d31-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f8d31-166"> では、<xref:System.Xml.Schema?displayProperty=fullName> 名前空間の拡張メソッドによって XSD 検証がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f8d31-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="f8d31-167">これにより、XML ツリーが XSD に準拠しているかどうかを検証できます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="f8d31-168">また、スキーマ検証後の情報セット (PSVI) を使用して XML ツリーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f8d31-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="f8d31-169">詳細については、「[方法: XSD を使用して検証する](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b)」および「<xref:System.Xml.Schema.Extensions>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8d31-169">For more information, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8d31-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8d31-170">See Also</span></span>  
 [<span data-ttu-id="f8d31-171">はじめに (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f8d31-171">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

