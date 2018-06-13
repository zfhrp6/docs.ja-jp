---
title: LINQ to XML クラスの概要 (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 619bf59c2b10cbb699f8e5b177991da9a0a2b238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329895"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="b9e31-102">LINQ to XML クラスの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="b9e31-102">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="b9e31-103">このトピックでは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 名前空間内の <xref:System.Xml.Linq> クラスの一覧を示し、各クラスについて簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="b9e31-104">LINQ to XML クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="b9e31-105">XAttribute クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-105">XAttribute Class</span></span>  
 <span data-ttu-id="b9e31-106"><xref:System.Xml.Linq.XAttribute> は XML 属性を表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="b9e31-107">詳細と例については、「[XAttribute クラスの概要 (C#)](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9e31-107">For detailed information and examples, see [XAttribute Class Overview (C#)](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="b9e31-108">XCData クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-108">XCData Class</span></span>  
 <span data-ttu-id="b9e31-109"><xref:System.Xml.Linq.XCData> は、CDATA テキスト ノードを表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="b9e31-110">XComment クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-110">XComment Class</span></span>  
 <span data-ttu-id="b9e31-111"><xref:System.Xml.Linq.XComment> は XML コメントを表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="b9e31-112">XContainer クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-112">XContainer Class</span></span>  
 <span data-ttu-id="b9e31-113"><xref:System.Xml.Linq.XContainer> は、子ノードを持つ可能性があるすべてのノードの抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="b9e31-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="b9e31-114"><xref:System.Xml.Linq.XContainer> からは次のクラスが派生します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="b9e31-115">XDeclaration クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-115">XDeclaration Class</span></span>  
 <span data-ttu-id="b9e31-116"><xref:System.Xml.Linq.XDeclaration> は、XML 宣言を表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="b9e31-117">XML 宣言は、ドキュメントの XML バージョンとエンコーディングを宣言するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9e31-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="b9e31-118">また、XML 宣言では、XML ドキュメントがスタンドアロンかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="b9e31-119">ドキュメントがスタンドアロンである場合、外部 DTD、または内部サブセットから参照されている外部パラメーター エンティティのいずれかに外部マークアップ宣言がありません。</span><span class="sxs-lookup"><span data-stu-id="b9e31-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="b9e31-120">XDocument クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-120">XDocument Class</span></span>  
 <span data-ttu-id="b9e31-121"><xref:System.Xml.Linq.XDocument> は、XML ドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="b9e31-122">詳細と例については、「[XDocument クラスの概要 (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9e31-122">For detailed information and examples, see [XDocument Class Overview (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="b9e31-123">XDocumentType クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-123">XDocumentType Class</span></span>  
 <span data-ttu-id="b9e31-124"><xref:System.Xml.Linq.XDocumentType> は、XML ドキュメント型定義 (DTD) を表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="b9e31-125">XElement クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-125">XElement Class</span></span>  
 <span data-ttu-id="b9e31-126"><xref:System.Xml.Linq.XElement> は、XML 要素を表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="b9e31-127">詳細と例については、「[XElement クラスの概要 (C#)](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9e31-127">For detailed information and examples, see [XElement Class Overview (C#)](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="b9e31-128">XName クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-128">XName Class</span></span>  
 <span data-ttu-id="b9e31-129"><xref:System.Xml.Linq.XName> は、要素の名前 (<xref:System.Xml.Linq.XElement>) および属性 (<xref:System.Xml.Linq.XAttribute>) を表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="b9e31-130">詳細と例については、「[XDocument クラスの概要 (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9e31-130">For detailed information and examples, see [XDocument Class Overview (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b9e31-131"> は、XML 名ができる限り単純になるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="b9e31-131"> is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="b9e31-132">XML 名は、その複雑さのために XML の高度な領域として扱われることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="b9e31-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="b9e31-133">この複雑さの原因として考えられるのは、開発者がプログラミングで通常使用する名前空間ではなく、名前空間プレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="b9e31-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="b9e31-134">名前空間プレフィックスは、XML を入力するときに必要なキー ストロークを減らしたり、XML を読みやすくしたりするために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b9e31-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="b9e31-135">しかし、プレフィックスは、完全な XML 名前空間を使用するためのショートカットに過ぎないことが多く、必要ない場合がほとんどです。</span><span class="sxs-lookup"><span data-stu-id="b9e31-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b9e31-136"> では、すべてのプレフィックスを対応する XML 名前空間に解決することで、XML 名を簡素化しています。</span><span class="sxs-lookup"><span data-stu-id="b9e31-136"> simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="b9e31-137">プレフィックスが必要であれば、<xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> メソッドを介して使用できます。</span><span class="sxs-lookup"><span data-stu-id="b9e31-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="b9e31-138">必要に応じて名前空間プレフィックスを制御することができます。</span><span class="sxs-lookup"><span data-stu-id="b9e31-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="b9e31-139">XSLT や XAML などの他の XML システムを使用する場合は、状況によって名前空間プレフィックスを制御する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9e31-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="b9e31-140">たとえば、名前空間プレフィックスを使用し、XSLT スタイルシートに組み込まれている XPath 式がある場合は、XPath 式内で使用しているものと一致する名前空間プレフィックスで XML ドキュメントがシリアル化されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9e31-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="b9e31-141">XNamespace クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-141">XNamespace Class</span></span>  
 <span data-ttu-id="b9e31-142"><xref:System.Xml.Linq.XNamespace> は、<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XAttribute> の名前空間を表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="b9e31-143">名前空間は、<xref:System.Xml.Linq.XName> のコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="b9e31-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="b9e31-144">XNode クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-144">XNode Class</span></span>  
 <span data-ttu-id="b9e31-145"><xref:System.Xml.Linq.XNode> は、XML ツリーのノードを表す抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="b9e31-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="b9e31-146"><xref:System.Xml.Linq.XNode> からは次のクラスが派生します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="b9e31-147">XNodeDocumentOrderComparer クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="b9e31-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> には、ノードをドキュメント順で比較する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b9e31-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="b9e31-149">XNodeEqualityComparer クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="b9e31-150"><xref:System.Xml.Linq.XNodeEqualityComparer> には、ノードを値の等価性で比較する機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b9e31-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="b9e31-151">XObject クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-151">XObject Class</span></span>  
 <span data-ttu-id="b9e31-152"><xref:System.Xml.Linq.XObject> は、<xref:System.Xml.Linq.XNode> および <xref:System.Xml.Linq.XAttribute> の抽象基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="b9e31-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="b9e31-153">このクラスには、注釈およびイベント機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="b9e31-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="b9e31-154">XObjectChange クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-154">XObjectChange Class</span></span>  
 <span data-ttu-id="b9e31-155"><xref:System.Xml.Linq.XObjectChange> は、<xref:System.Xml.Linq.XObject> に対してイベントが生成されるときのイベントの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="b9e31-156">XObjectChangeEventArgs クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="b9e31-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> には、<xref:System.Xml.Linq.XObject.Changing> イベントと <xref:System.Xml.Linq.XObject.Changed> イベントのデータが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b9e31-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="b9e31-158">XProcessingInstruction クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="b9e31-159"><xref:System.Xml.Linq.XProcessingInstruction> は、XML 処理命令を表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="b9e31-160">処理命令は、XML を処理するアプリケーションに情報を伝達します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="b9e31-161">XText クラス</span><span class="sxs-lookup"><span data-stu-id="b9e31-161">XText Class</span></span>  
 <span data-ttu-id="b9e31-162"><xref:System.Xml.Linq.XText> は、テキスト ノードを表します。</span><span class="sxs-lookup"><span data-stu-id="b9e31-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="b9e31-163">このクラスを使用する必要はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="b9e31-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="b9e31-164">このクラスは、主に混合コンテンツに使用されます。</span><span class="sxs-lookup"><span data-stu-id="b9e31-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e31-165">参照</span><span class="sxs-lookup"><span data-stu-id="b9e31-165">See Also</span></span>  
 [<span data-ttu-id="b9e31-166">LINQ to XML プログラミングの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="b9e31-166">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
