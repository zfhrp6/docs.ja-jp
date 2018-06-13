---
title: ノード (Visual Basic) を使用したプログラミング
ms.date: 07/20/2015
ms.assetid: d8422a9b-dd37-44a3-8aac-2237ed9561e0
ms.openlocfilehash: 871755ef0293513f07c60b1d5735c47692163b78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648347"
---
# <a name="programming-with-nodes-visual-basic"></a><span data-ttu-id="bf443-102">ノード (Visual Basic) を使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="bf443-102">Programming with Nodes (Visual Basic)</span></span>
<span data-ttu-id="bf443-103">XML エディター、変換システム、レポート作成プログラムなどのプログラムを作成する [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の開発者は、要素や属性よりも細かい粒度レベルで動作するプログラムを作成しなければならないことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="bf443-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] developers who need to write programs such as an XML editor, a transform system, or a report writer often need to write programs that work at a finer level of granularity than elements and attributes.</span></span> <span data-ttu-id="bf443-104">また場合によっては、ノード レベルで、テキスト ノード、処理命令、およびコメントを操作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bf443-104">They often need to work at the node level, manipulating text nodes, processing instructions, and comments.</span></span> <span data-ttu-id="bf443-105">このトピックでは、ノード レベルでのプログラミングについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="bf443-105">This topic provides some details about programming at the node level.</span></span>  
  
## <a name="node-details"></a><span data-ttu-id="bf443-106">ノードの詳細</span><span class="sxs-lookup"><span data-stu-id="bf443-106">Node Details</span></span>  
 <span data-ttu-id="bf443-107">ノード レベルで作業するプログラマが知っておく必要があるプログラミングの詳細事項がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="bf443-107">There are a number of details of programming that a programmer working at the node level should know.</span></span>  
  
### <a name="parent-property-of-children-nodes-of-xdocument-is-set-to-null"></a><span data-ttu-id="bf443-108">XDocument の子ノードの Parent プロパティが Null に設定される</span><span class="sxs-lookup"><span data-stu-id="bf443-108">Parent Property of Children Nodes of XDocument is Set to Null</span></span>  
 <span data-ttu-id="bf443-109"><xref:System.Xml.Linq.XObject.Parent%2A> プロパティには、親ノードではなく親 <xref:System.Xml.Linq.XElement> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bf443-109">The <xref:System.Xml.Linq.XObject.Parent%2A> property contains the parent <xref:System.Xml.Linq.XElement>, not the parent node.</span></span> <span data-ttu-id="bf443-110"><xref:System.Xml.Linq.XDocument> の子ノードには、親 <xref:System.Xml.Linq.XElement> がありません。</span><span class="sxs-lookup"><span data-stu-id="bf443-110">Child nodes of <xref:System.Xml.Linq.XDocument> have no parent <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="bf443-111">これらの子ノードの親はドキュメントであるため、子ノードの <xref:System.Xml.Linq.XObject.Parent%2A> プロパティは null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-111">Their parent is the document, so the <xref:System.Xml.Linq.XObject.Parent%2A> property for those nodes is set to null.</span></span>  
  
 <span data-ttu-id="bf443-112">この動作を次の例で示します。</span><span class="sxs-lookup"><span data-stu-id="bf443-112">The following example demonstrates this:</span></span>  
  
```vb  
Dim doc As XDocument = XDocument.Parse("<!-- a comment --><Root/>")  
Console.WriteLine(doc.Nodes().OfType(Of XComment).First().Parent Is Nothing)  
Console.WriteLine(doc.Root.Parent Is Nothing)  
```  
  
 <span data-ttu-id="bf443-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-113">This example produces the following output:</span></span>  
  
```  
True  
True  
```  
  
### <a name="adjacent-text-nodes-are-possible"></a><span data-ttu-id="bf443-114">隣接するテキスト ノードが存在する可能性がある</span><span class="sxs-lookup"><span data-stu-id="bf443-114">Adjacent Text Nodes are Possible</span></span>  
 <span data-ttu-id="bf443-115">多くの XML プログラミング モデルでは、隣接するテキスト ノードが常に連結されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-115">In a number of XML programming models, adjacent text nodes are always merged.</span></span> <span data-ttu-id="bf443-116">これは、テキスト ノードの正規化と呼ばれることがあります。</span><span class="sxs-lookup"><span data-stu-id="bf443-116">This is sometimes called normalization of text nodes.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="bf443-117"> ではテキスト ノードは正規化されません。</span><span class="sxs-lookup"><span data-stu-id="bf443-117"> does not normalize text nodes.</span></span> <span data-ttu-id="bf443-118">同じ要素に 2 つのテキスト ノードを追加すると、隣接するテキスト ノードになります。</span><span class="sxs-lookup"><span data-stu-id="bf443-118">If you add two text nodes to the same element, it will result in adjacent text nodes.</span></span> <span data-ttu-id="bf443-119">ただし、<xref:System.Xml.Linq.XText> ノードではなく文字列として指定されたコンテンツを追加すると、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] はその文字列を隣接するテキスト ノードに連結します。</span><span class="sxs-lookup"><span data-stu-id="bf443-119">However, if you add content specified as a string rather than as an <xref:System.Xml.Linq.XText> node, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] might merge the string with an adjacent text node.</span></span>  
  
 <span data-ttu-id="bf443-120">この動作を次の例で示します。</span><span class="sxs-lookup"><span data-stu-id="bf443-120">The following example demonstrates this:</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
' This does not add a new text node.  
xmlTree.Add("new content")  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
  
'// This does add a new, adjacent text node.  
xmlTree.Add(New XText("more text"))  
Console.WriteLine(xmlTree.Nodes().OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="bf443-121">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-121">This example produces the following output:</span></span>  
  
```  
1  
1  
2  
```  
  
### <a name="empty-text-nodes-are-possible"></a><span data-ttu-id="bf443-122">空のテキスト ノードが存在する可能性がある</span><span class="sxs-lookup"><span data-stu-id="bf443-122">Empty Text Nodes are Possible</span></span>  
 <span data-ttu-id="bf443-123">一部の XML プログラミング モデルでは、テキスト ノードに空の文字列が含まれないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-123">In some XML programming models, text nodes are guaranteed to not contain the empty string.</span></span> <span data-ttu-id="bf443-124">その理由は、テキスト ノードに空の文字列が含まれていなければ、XML のシリアル化に対して影響が生じないためです。</span><span class="sxs-lookup"><span data-stu-id="bf443-124">The reasoning is that such a text node has no impact on serialization of the XML.</span></span> <span data-ttu-id="bf443-125">ただし、隣接するテキスト ノードの場合と同じ理由で、テキスト ノードの値を空の文字列に設定することによってテキスト ノードからテキストを削除した場合、テキスト ノード自体は削除されません。</span><span class="sxs-lookup"><span data-stu-id="bf443-125">However, for the same reason that adjacent text nodes are possible, if you remove the text from a text node by setting its value to the empty string, the text node itself will not be deleted.</span></span>  
  
```vb  
Dim xmlTree As XElement = <Root>Content</Root>  
Dim textNode As XText = xmlTree.Nodes().OfType(Of XText)().First()  
  
' The following line does not cause the removal of the text node.  
textNode.Value = ""  
  
Dim textNode2 As XText = xmlTree.Nodes().OfType(Of XText)().First()  
Console.WriteLine(">>{0}<<", textNode2)  
```  
  
 <span data-ttu-id="bf443-126">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-126">This example produces the following output:</span></span>  
  
```  
>><<  
```  
  
### <a name="an-empty-text-node-impacts-serialization"></a><span data-ttu-id="bf443-127">空のテキスト ノードがシリアル化に影響する</span><span class="sxs-lookup"><span data-stu-id="bf443-127">An Empty Text Node Impacts Serialization</span></span>  
 <span data-ttu-id="bf443-128">要素に空の子テキスト ノードのみが含まれている場合、その要素は長いタグ構文 `<Child></Child>` でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-128">If an element contains only a child text node that is empty, it is serialized with the long tag syntax: `<Child></Child>`.</span></span> <span data-ttu-id="bf443-129">子ノードがまったく含まれていない要素は、短いタグ構文 `<Child />` でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-129">If an element contains no child nodes whatsoever, it is serialized with the short tag syntax: `<Child />`.</span></span>  
  
```vb  
Dim child1 As XElement = New XElement("Child1", _  
    New XText("") _  
)  
Dim child2 As XElement = New XElement("Child2")  
Console.WriteLine(child1)  
Console.WriteLine(child2)  
```  
  
 <span data-ttu-id="bf443-130">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-130">This example produces the following output:</span></span>  
  
```xml  
<Child1></Child1>  
<Child2 />  
```  
  
### <a name="namespaces-are-attributes-in-the-linq-to-xml-tree"></a><span data-ttu-id="bf443-131">LINQ to XML ツリーでは名前空間が属性になる</span><span class="sxs-lookup"><span data-stu-id="bf443-131">Namespaces are Attributes in the LINQ to XML Tree</span></span>  
 <span data-ttu-id="bf443-132">名前空間宣言の構文は属性と同じですが、XSLT や XPath などの一部のプログラミング インターフェイスでは、名前空間宣言が属性と見なされません。</span><span class="sxs-lookup"><span data-stu-id="bf443-132">Even though namespace declarations have identical syntax to attributes, in some programming interfaces, such as XSLT and XPath, namespace declarations are not considered to be attributes.</span></span> <span data-ttu-id="bf443-133">ただし [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] では、名前空間が <xref:System.Xml.Linq.XAttribute> オブジェクトとして XML ツリーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-133">However, in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], namespaces are stored as <xref:System.Xml.Linq.XAttribute> objects in the XML tree.</span></span> <span data-ttu-id="bf443-134">名前空間宣言を含んでいる要素の属性を反復処理すると、名前空間宣言が、返されるコレクションの項目の 1 つになります。</span><span class="sxs-lookup"><span data-stu-id="bf443-134">If you iterate through the attributes for an element that contains a namespace declaration, you will see the namespace declaration as one of the items in the returned collection.</span></span>  
  
 <span data-ttu-id="bf443-135"><xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> プロパティによって、属性が名前空間宣言であるかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-135">The <xref:System.Xml.Linq.XAttribute.IsNamespaceDeclaration%2A> property indicates whether an attribute is a namespace declaration.</span></span>  
  
```vb  
Dim root As XElement = _   
<Root  
    xmlns='http://www.adventure-works.com'  
    xmlns:fc='www.fourthcoffee.com'  
    AnAttribute='abc'/>  
For Each att As XAttribute In root.Attributes()  
    Console.WriteLine("{0}  IsNamespaceDeclaration:{1}", att, _  
                      att.IsNamespaceDeclaration)  
Next  
```  
  
 <span data-ttu-id="bf443-136">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-136">This example produces the following output:</span></span>  
  
```  
xmlns="http://www.adventure-works.com"  IsNamespaceDeclaration:True  
xmlns:fc="www.fourthcoffee.com"  IsNamespaceDeclaration:True  
AnAttribute="abc"  IsNamespaceDeclaration:False  
```  
  
### <a name="xpath-axis-methods-do-not-return-child-white-space-of-xdocument"></a><span data-ttu-id="bf443-137">XPath 軸メソッドからは XDocument の空白の子ノードが返されない</span><span class="sxs-lookup"><span data-stu-id="bf443-137">XPath Axis Methods Do Not Return Child White Space of XDocument</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="bf443-138"> で処理できる <xref:System.Xml.Linq.XDocument> の子テキスト ノードは、空白のみを含んでいるものに限られます。</span><span class="sxs-lookup"><span data-stu-id="bf443-138"> allows for child text nodes of an <xref:System.Xml.Linq.XDocument>, as long as the text nodes contain only white space.</span></span> <span data-ttu-id="bf443-139">ただし、XPath オブジェクト モデルでは、空白がドキュメントの子ノードとして組み込まれないため、<xref:System.Xml.Linq.XDocument> 軸を使用して <xref:System.Xml.Linq.XContainer.Nodes%2A> の子を反復処理すると、空白のテキスト ノードが返されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-139">However, the XPath object model does not include white space as child nodes of a document, so when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the <xref:System.Xml.Linq.XContainer.Nodes%2A> axis, white space text nodes will be returned.</span></span> <span data-ttu-id="bf443-140">一方、XPath 軸メソッドを使用して <xref:System.Xml.Linq.XDocument> の子を反復処理すると、空白のテキスト ノードが返されません。</span><span class="sxs-lookup"><span data-stu-id="bf443-140">However, when you iterate through the children of an <xref:System.Xml.Linq.XDocument> using the XPath axis methods, white space text nodes will not be returned.</span></span>  
  
```vb  
' Create a document with some white space child nodes of the document.  
Dim root As XDocument = XDocument.Parse( _  
"<?xml version='1.0' encoding='utf-8' standalone='yes'?>" & _  
vbNewLine & "<Root/>" & vbNewLine & "<!--a comment-->" & vbNewLine, _  
LoadOptions.PreserveWhitespace)  
  
' Count the white space child nodes using LINQ to XML.  
Console.WriteLine(root.Nodes().OfType(Of XText)().Count())  
  
' Count the white space child nodes using XPathEvaluate.  
Dim nodes As IEnumerable = CType(root.XPathEvaluate("text()"), IEnumerable)  
Console.WriteLine(nodes.OfType(Of XText)().Count())  
```  
  
 <span data-ttu-id="bf443-141">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-141">This example produces the following output:</span></span>  
  
```  
3  
0  
```  
  
### <a name="xdeclaration-objects-are-not-nodes"></a><span data-ttu-id="bf443-142">XDeclaration オブジェクトはノードではない</span><span class="sxs-lookup"><span data-stu-id="bf443-142">XDeclaration Objects are not Nodes</span></span>  
 <span data-ttu-id="bf443-143"><xref:System.Xml.Linq.XDocument> の子ノードを反復処理しても、XML 宣言オブジェクトは生成されません。</span><span class="sxs-lookup"><span data-stu-id="bf443-143">When you iterate through the children nodes of an <xref:System.Xml.Linq.XDocument>, you will not see the XML declaration object.</span></span> <span data-ttu-id="bf443-144">これはドキュメントのプロパティであって、ドキュメントの子ノードではありません。</span><span class="sxs-lookup"><span data-stu-id="bf443-144">It is a property of the document, not a child node of it.</span></span>  
  
```vb  
Dim doc As XDocument = _  
<?xml version='1.0' encoding='utf-8' standalone='yes'?>  
<Root/>  
  
doc.Save("Temp.xml")  
Console.WriteLine(File.ReadAllText("Temp.xml"))  
  
' This shows that there is only one child node of the document.  
Console.WriteLine(doc.Nodes().Count())  
```  
  
 <span data-ttu-id="bf443-145">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bf443-145">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root />  
1  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf443-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf443-146">See Also</span></span>  
 [<span data-ttu-id="bf443-147">高度な LINQ to XML プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf443-147">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
