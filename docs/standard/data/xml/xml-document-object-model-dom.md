---
title: "XML ドキュメント オブジェクト モデル (DOM)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ff91e929876ceec8512e962b88795b6a8a29f3d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-document-object-model-dom"></a><span data-ttu-id="5ad24-102">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="5ad24-102">XML Document Object Model (DOM)</span></span>
<span data-ttu-id="5ad24-103">XML ドキュメント オブジェクト モデル (DOM) クラスは、XML ドキュメントのメモリ内表現です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-103">The XML Document Object Model (DOM) class is an in-memory representation of an XML document.</span></span> <span data-ttu-id="5ad24-104">DOM を使用すると、XML ドキュメントの読み込み、操作、および変更をプログラムから実行できます。</span><span class="sxs-lookup"><span data-stu-id="5ad24-104">The DOM allows you to programmatically read, manipulate, and modify an XML document.</span></span> <span data-ttu-id="5ad24-105">**XmlReader**クラスも XML を読み取ります。 ただし、非キャッシュ、順方向専用、読み取り専用アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5ad24-105">The **XmlReader** class also reads XML; however, it provides non-cached, forward-only, read-only access.</span></span> <span data-ttu-id="5ad24-106">つまり、属性の値または要素、または挿入し、使用してノードを削除する機能の内容を編集する機能がないこと、 **XmlReader**です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-106">This means that there are no capabilities to edit the values of an attribute or content of an element, or the ability to insert and remove nodes with the **XmlReader**.</span></span> <span data-ttu-id="5ad24-107">DOM の主な機能は編集です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-107">Editing is the primary function of the DOM.</span></span> <span data-ttu-id="5ad24-108">XML データは、通常、メモリ上では構造的に表現されますが、実際の XML データをファイルに保存したり、別のオブジェクトから取り込む場合は、直線的な形式で格納されます。</span><span class="sxs-lookup"><span data-stu-id="5ad24-108">It is the common and structured way that XML data is represented in memory, although the actual XML data is stored in a linear fashion when in a file or coming in from another object.</span></span> <span data-ttu-id="5ad24-109">XML データの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5ad24-109">The following is XML data.</span></span>  
  
## <a name="input"></a><span data-ttu-id="5ad24-110">入力</span><span class="sxs-lookup"><span data-stu-id="5ad24-110">Input</span></span>  
  
```xml  
<?xml version="1.0"?>  
  <books>  
    <book>  
        <author>Carson</author>  
        <price format="dollar">31.95</price>  
        <pubdate>05/01/2001</pubdate>  
    </book>  
    <pubinfo>  
        <publisher>MSPress</publisher>  
        <state>WA</state>  
    </pubinfo>  
  </books>   
```  
  
 <span data-ttu-id="5ad24-111">この XML データが DOM 構造に読み込まれるとき、メモリがどのように構造化されるかを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="5ad24-111">The following illustration shows how memory is structured when this XML data is read into the DOM structure.</span></span>  
  
 <span data-ttu-id="5ad24-112">![XML ドキュメントの構造](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")</span><span class="sxs-lookup"><span data-stu-id="5ad24-112">![XML document structure](../../../../docs/standard/data/xml/media/xml-to-domtree.gif "XML_To_DOMTree")</span></span>  
<span data-ttu-id="5ad24-113">XML ドキュメントの構造</span><span class="sxs-lookup"><span data-stu-id="5ad24-113">XML document structure</span></span>  
  
 <span data-ttu-id="5ad24-114">この図では、各円と呼ばれるノードを表す XML ドキュメントの構造内で、 **XmlNode**オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5ad24-114">Within the XML document structure, each circle in this illustration represents a node, which is called an **XmlNode** object.</span></span> <span data-ttu-id="5ad24-115">**XmlNode**オブジェクトが、DOM ツリーの基本オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="5ad24-115">The **XmlNode** object is the basic object in the DOM tree.</span></span> <span data-ttu-id="5ad24-116">**XmlDocument**を拡張するクラス**XmlNode**が全体として (たとえばをメモリに読み込むか、XML をファイルに保存ドキュメントに対する操作を実行するためのメソッドをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5ad24-116">The **XmlDocument** class, which extends **XmlNode**, supports methods for performing operations on the document as a whole (for example, loading it into memory or saving the XML to a file.</span></span> <span data-ttu-id="5ad24-117">さらに、 **XmlDocument**を表示して、XML ドキュメント全体のノードを操作する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="5ad24-117">In addition, **XmlDocument** provides a means to view and manipulate the nodes in the entire XML document.</span></span> <span data-ttu-id="5ad24-118">両方**XmlNode**と**XmlDocument**パフォーマンスと使いやすさの拡張機能がありするメソッドとプロパティ。</span><span class="sxs-lookup"><span data-stu-id="5ad24-118">Both **XmlNode** and **XmlDocument** have performance and usability enhancements and have methods and properties to:</span></span>  
  
-   <span data-ttu-id="5ad24-119">要素ノード、エンティティ参照ノードなど、DOM に固有のノードへのアクセスと変更。</span><span class="sxs-lookup"><span data-stu-id="5ad24-119">Access and modify nodes specific to the DOM, such as element nodes, entity reference nodes, and so on.</span></span>  
  
-   <span data-ttu-id="5ad24-120">要素ノードのテキストなど、ノードに格納されている情報およびノード全体の取得。</span><span class="sxs-lookup"><span data-stu-id="5ad24-120">Retrieve entire nodes, in addition to the information the node contains, such as the text in an element node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ad24-121">構造体、または編集、DOM によって提供される機能がアプリケーションに必要としない場合、 **XmlReader**と**XmlWriter**クラスは、XML を非キャッシュ、前方参照専用のストリーム アクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="5ad24-121">If an application does not require the structure or editing capabilities provided by the DOM, the **XmlReader** and **XmlWriter** classes provide non-cached, forward-only stream access to XML.</span></span> <span data-ttu-id="5ad24-122">詳細については、<xref:System.Xml.XmlReader> および <xref:System.Xml.XmlWriter> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ad24-122">For more information, see <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="5ad24-123">**ノード**オブジェクト メソッドとプロパティと同様の基本的なと適切に定義された特徴セットがあります。</span><span class="sxs-lookup"><span data-stu-id="5ad24-123">**Node** objects have a set of methods and properties, as well as basic and well-defined characteristics.</span></span> <span data-ttu-id="5ad24-124">オブジェクトが持つ特性のいくつかを次に示します。</span><span class="sxs-lookup"><span data-stu-id="5ad24-124">Some of these characteristics are:</span></span>  
  
-   <span data-ttu-id="5ad24-125">ノードは 1 つの親ノードを持っています。親ノードはノードの 1 つ上のノードです。</span><span class="sxs-lookup"><span data-stu-id="5ad24-125">Nodes have a single parent node, a parent node being a node directly above them.</span></span> <span data-ttu-id="5ad24-126">ドキュメント ルートは最上位のノードであり、ドキュメント自身とドキュメント フラグメントしか格納されていないため、親ノードを持っていないノードはドキュメント ルートだけです。</span><span class="sxs-lookup"><span data-stu-id="5ad24-126">The only nodes that do not have a parent is the Document root, as it is the top-level node and contains the document itself and document fragments.</span></span>  
  
-   <span data-ttu-id="5ad24-127">ほとんどのノードは、複数の子ノードを持つことができます。子ノードは、ノードの 1 つ下のノードです。</span><span class="sxs-lookup"><span data-stu-id="5ad24-127">Most nodes can have multiple child nodes, which are nodes directly below them.</span></span> <span data-ttu-id="5ad24-128">子ノードを持つことができるノード型の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5ad24-128">The following is a list of node types that can have child nodes.</span></span>  
  
    -   <span data-ttu-id="5ad24-129">**ドキュメント**</span><span class="sxs-lookup"><span data-stu-id="5ad24-129">**Document**</span></span>  
  
    -   <span data-ttu-id="5ad24-130">**Documentfragment**</span><span class="sxs-lookup"><span data-stu-id="5ad24-130">**DocumentFragment**</span></span>  
  
    -   <span data-ttu-id="5ad24-131">**EntityReference**</span><span class="sxs-lookup"><span data-stu-id="5ad24-131">**EntityReference**</span></span>  
  
    -   <span data-ttu-id="5ad24-132">**要素**</span><span class="sxs-lookup"><span data-stu-id="5ad24-132">**Element**</span></span>  
  
    -   <span data-ttu-id="5ad24-133">**属性**</span><span class="sxs-lookup"><span data-stu-id="5ad24-133">**Attribute**</span></span>  
  
     <span data-ttu-id="5ad24-134">**XmlDeclaration**、**表記**、**エンティティ**、 **CDATASection**、**テキスト**、 **コメント**、 **ProcessingInstruction**、および**DocumentType**ノードに子ノードがありません。</span><span class="sxs-lookup"><span data-stu-id="5ad24-134">The **XmlDeclaration**, **Notation**, **Entity**, **CDATASection**, **Text**, **Comment**, **ProcessingInstruction**, and **DocumentType** nodes do not have child nodes.</span></span>  
  
-   <span data-ttu-id="5ad24-135">ダイアグラム ビューで表される、同じレベルにあるノード、 **book**と**pubinfo**は兄弟です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-135">Nodes that are at the same level, represented in the diagram by the **book** and **pubinfo** nodes, are siblings.</span></span>  
  
 <span data-ttu-id="5ad24-136">DOM の特性の 1 つは、属性の取り扱い方法にあります。</span><span class="sxs-lookup"><span data-stu-id="5ad24-136">One characteristic of the DOM is how it handles attributes.</span></span> <span data-ttu-id="5ad24-137">属性は、互いに親子関係や兄弟関係を持つノードではありません。</span><span class="sxs-lookup"><span data-stu-id="5ad24-137">Attributes are not nodes that are part of the parent, child, and sibling relationships.</span></span> <span data-ttu-id="5ad24-138">属性は要素ノードのプロパティと見なされ、名前と値ペアから構成されます。</span><span class="sxs-lookup"><span data-stu-id="5ad24-138">Attributes are considered a property of the element node and are made up of a name and a value pair.</span></span> <span data-ttu-id="5ad24-139">たとえば、要素 `format="dollar` に関連付けられている `price`" という形式の XML データがある場合は、単語 `format` が名前になり、`format` 属性の値は `dollar` になります。</span><span class="sxs-lookup"><span data-stu-id="5ad24-139">For example, if you have XML data consisting of `format="dollar`" associated with the element `price`, the word `format` is the name, and the value of the `format` attribute is `dollar`.</span></span> <span data-ttu-id="5ad24-140">取得する、`format="dollar"`の属性、**価格** ノードを呼び出す、 **GetAttribute**メソッドにカーソルがあるときに、`price`要素ノードです。</span><span class="sxs-lookup"><span data-stu-id="5ad24-140">To retrieve the `format="dollar"` attribute of the **price** node, you call the **GetAttribute** method when the cursor is located at the `price` element node.</span></span> <span data-ttu-id="5ad24-141">詳細については、次を参照してください。 [、DOM 内の属性へのアクセス](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-141">For more information, see [Accessing Attributes in the DOM](../../../../docs/standard/data/xml/accessing-attributes-in-the-dom.md).</span></span>  
  
 <span data-ttu-id="5ad24-142">XML をメモリに読み込むと、ノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="5ad24-142">As XML is read into memory, nodes are created.</span></span> <span data-ttu-id="5ad24-143">ただし、すべてのノードが同じタイプというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="5ad24-143">However, not all nodes are the same type.</span></span> <span data-ttu-id="5ad24-144">XML の要素の規則と構文は、処理命令の規則と構文とは異なります。</span><span class="sxs-lookup"><span data-stu-id="5ad24-144">An element in XML has different rules and syntax than a processing instruction.</span></span> <span data-ttu-id="5ad24-145">したがって、さまざまなデータが読み込まれるときに、個々のノードにノード型が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="5ad24-145">Therefore, as various data is read, a node type is assigned to each node.</span></span> <span data-ttu-id="5ad24-146">このノード型によって、ノードの特性と機能が決定されます。</span><span class="sxs-lookup"><span data-stu-id="5ad24-146">This node type determines the characteristics and functionality of the node.</span></span>  
  
 <span data-ttu-id="5ad24-147">メモリ内で生成されるノードの種類の詳細については、次を参照してください。 [XML ノードの種類](../../../../docs/standard/data/xml/types-of-xml-nodes.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-147">For more information on the types of nodes generated in memory, see [Types of XML Nodes](../../../../docs/standard/data/xml/types-of-xml-nodes.md).</span></span> <span data-ttu-id="5ad24-148">ノード ツリーに作成されたオブジェクトの詳細については、次を参照してください。[オブジェクト階層の XML データへのマップ](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-148">For more information on the objects created in the node tree, see [Mapping the Object Hierarchy to XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).</span></span>  
  
 <span data-ttu-id="5ad24-149">Microsoft では、XML ドキュメントの操作を容易にするために、W3C (World Wide Web Consortium) DOM Level 1 および Level 2 で規定されている API を拡張しています。</span><span class="sxs-lookup"><span data-stu-id="5ad24-149">Microsoft has extended the APIs that are available in the World Wide Web Consortium (W3C) DOM Level 1 and Level 2 to make it easier to work with an XML document.</span></span> <span data-ttu-id="5ad24-150">W3C の標準を完全にサポートする一方で、追加のクラス、メソッド、プロパティにより、W3C の XML DOM で実現できる以上の機能が付加されています。</span><span class="sxs-lookup"><span data-stu-id="5ad24-150">While fully supporting the W3C standards, the additional classes, methods, and properties add functionality beyond what can be done using the W3C XML DOM.</span></span> <span data-ttu-id="5ad24-151">新しいクラスを使用すると、リレーショナル データにアクセスし、ADO.NET との同期をとりながら、データを XML として公開できます。</span><span class="sxs-lookup"><span data-stu-id="5ad24-151">New classes enable you to access relational data, giving you methods for synchronizing with ADO.NET data, simultaneously exposing data as XML.</span></span> <span data-ttu-id="5ad24-152">詳細については、次を参照してください。 [DataSet と XmlDataDocument の同期](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-152">For more information, see [Synchronizing a DataSet with an XmlDataDocument](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).</span></span>  
  
 <span data-ttu-id="5ad24-153">DOM が最も役に立つのは、XML データをメモリに読み込み、その構造を変更したり、ノードを追加または削除したり、要素内のテキストとしてノードが保持しているデータを変更したりする場合です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-153">The DOM is most useful for reading XML data into memory to change its structure, to add or remove nodes, or to modify the data held by a node as in the text contained by an element.</span></span> <span data-ttu-id="5ad24-154">ただし、他のクラスも用意されており、シナリオによっては DOM より高速になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="5ad24-154">However, other classes are available that are faster than the DOM in other scenarios.</span></span> <span data-ttu-id="5ad24-155">XML へのアクセスを高速かつ非キャッシュで順方向専用ストリームを使用して、 **XmlReader**と**XmlWriter**です。</span><span class="sxs-lookup"><span data-stu-id="5ad24-155">For fast, non-cached, forward-only stream access to XML, use the **XmlReader** and **XmlWriter**.</span></span> <span data-ttu-id="5ad24-156">カーソル モデルとランダム アクセスを必要がある場合と**XPath**を使用して、 **XPathNavigator**クラスです。</span><span class="sxs-lookup"><span data-stu-id="5ad24-156">If you need random access with a cursor model and **XPath**, use the **XPathNavigator** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ad24-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ad24-157">See Also</span></span>  
 [<span data-ttu-id="5ad24-158">XML ノードの種類</span><span class="sxs-lookup"><span data-stu-id="5ad24-158">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
 [<span data-ttu-id="5ad24-159">オブジェクト階層の XML データへのマップ</span><span class="sxs-lookup"><span data-stu-id="5ad24-159">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)
