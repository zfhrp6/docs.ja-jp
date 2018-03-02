---
title: "XML ノードの種類"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0fd196f4aed5d4faa3e703f639b927f001b50174
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="types-of-xml-nodes"></a><span data-ttu-id="5166f-102">XML ノードの種類</span><span class="sxs-lookup"><span data-stu-id="5166f-102">Types of XML Nodes</span></span>
<span data-ttu-id="5166f-103">XML ドキュメントがノードのツリーとしてメモリに読み込まれると、ノードの作成時にノード型が決まります。</span><span class="sxs-lookup"><span data-stu-id="5166f-103">When an XML document is read into memory as a tree of nodes, the node types for the nodes are decided when the nodes are created.</span></span> <span data-ttu-id="5166f-104">XML ドキュメント オブジェクト モデル (DOM) では複数のノード型が定義されています。これらのノード型は W3C (World Wide Web Consortium) で規定されているもので、セクション 1.1.1「The DOM Structure Model」に記載されています。</span><span class="sxs-lookup"><span data-stu-id="5166f-104">The XML Document Object Model (DOM) has several kinds of node types, determined by the World Wide Web Consortium (W3C) and listed in section 1.1.1 The DOM Structure Model.</span></span> <span data-ttu-id="5166f-105">ノード型、ノード型に割り当てられるオブジェクト、およびそれぞれの簡単な説明を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="5166f-105">The following table lists the node types, the object assigned to that node type, and a short description of each.</span></span>  
  
|<span data-ttu-id="5166f-106">DOM ノード型</span><span class="sxs-lookup"><span data-stu-id="5166f-106">DOM node type</span></span>|<span data-ttu-id="5166f-107">Object</span><span class="sxs-lookup"><span data-stu-id="5166f-107">Object</span></span>|<span data-ttu-id="5166f-108">説明</span><span class="sxs-lookup"><span data-stu-id="5166f-108">Description</span></span>|  
|-------------------|------------|-----------------|  
|<span data-ttu-id="5166f-109">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="5166f-109">Document</span></span>|<xref:System.Xml.XmlDocument>|<span data-ttu-id="5166f-110">ツリー内のすべてのノードのコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="5166f-110">The container of all the nodes in the tree.</span></span> <span data-ttu-id="5166f-111">ドキュメントのルートとも呼ばれますが、常にルート要素と一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="5166f-111">It is also known as the document root, which is not always the same as the root element.</span></span>|  
|<span data-ttu-id="5166f-112">DocumentFragment</span><span class="sxs-lookup"><span data-stu-id="5166f-112">DocumentFragment</span></span>|<xref:System.Xml.XmlDocumentFragment>|<span data-ttu-id="5166f-113">1 つ以上のノードを非ツリー構造で格納する一時的なバッグです。</span><span class="sxs-lookup"><span data-stu-id="5166f-113">A temporary bag containing one or more nodes without any tree structure.</span></span>|  
|<span data-ttu-id="5166f-114">DocumentType</span><span class="sxs-lookup"><span data-stu-id="5166f-114">DocumentType</span></span>|<xref:System.Xml.XmlDocumentType>|<span data-ttu-id="5166f-115">`<!DOCTYPE…>` ノードを表します。</span><span class="sxs-lookup"><span data-stu-id="5166f-115">Represents the `<!DOCTYPE…>` node.</span></span>|  
|<span data-ttu-id="5166f-116">EntityReference</span><span class="sxs-lookup"><span data-stu-id="5166f-116">EntityReference</span></span>|<xref:System.Xml.XmlEntityReference>|<span data-ttu-id="5166f-117">展開されていないエンティティ参照テキストを表します。</span><span class="sxs-lookup"><span data-stu-id="5166f-117">Represents the non-expanded entity reference text.</span></span>|  
|<span data-ttu-id="5166f-118">要素</span><span class="sxs-lookup"><span data-stu-id="5166f-118">Element</span></span>|<xref:System.Xml.XmlElement>|<span data-ttu-id="5166f-119">要素ノードを表します。</span><span class="sxs-lookup"><span data-stu-id="5166f-119">Represents an element node.</span></span>|  
|<span data-ttu-id="5166f-120">Attr</span><span class="sxs-lookup"><span data-stu-id="5166f-120">Attr</span></span>|<xref:System.Xml.XmlAttribute>|<span data-ttu-id="5166f-121">要素の属性です。</span><span class="sxs-lookup"><span data-stu-id="5166f-121">Is an attribute of an element.</span></span>|  
|<span data-ttu-id="5166f-122">ProcessingInstruction</span><span class="sxs-lookup"><span data-stu-id="5166f-122">ProcessingInstruction</span></span>|<xref:System.Xml.XmlProcessingInstruction>|<span data-ttu-id="5166f-123">処理命令ノードです。</span><span class="sxs-lookup"><span data-stu-id="5166f-123">Is a processing instruction node.</span></span>|  
|<span data-ttu-id="5166f-124">コメント</span><span class="sxs-lookup"><span data-stu-id="5166f-124">Comment</span></span>|<xref:System.Xml.XmlComment>|<span data-ttu-id="5166f-125">コメント ノードです。</span><span class="sxs-lookup"><span data-stu-id="5166f-125">A comment node.</span></span>|  
|<span data-ttu-id="5166f-126">テキスト</span><span class="sxs-lookup"><span data-stu-id="5166f-126">Text</span></span>|<xref:System.Xml.XmlText>|<span data-ttu-id="5166f-127">要素または属性に含まれるテキストです。</span><span class="sxs-lookup"><span data-stu-id="5166f-127">Text belonging to an element or attribute.</span></span>|  
|<span data-ttu-id="5166f-128">CDATASection</span><span class="sxs-lookup"><span data-stu-id="5166f-128">CDATASection</span></span>|<xref:System.Xml.XmlCDataSection>|<span data-ttu-id="5166f-129">CDATA を表します。</span><span class="sxs-lookup"><span data-stu-id="5166f-129">Represents CDATA.</span></span>|  
|<span data-ttu-id="5166f-130">エンティティ</span><span class="sxs-lookup"><span data-stu-id="5166f-130">Entity</span></span>|<xref:System.Xml.XmlEntity>|<span data-ttu-id="5166f-131">内部ドキュメント型定義 (DTD) のサブセットまたは外部 DTD とパラメーター エンティティから取得され、XML ドキュメントに含まれている `<!ENTITY…>` 宣言を表します。</span><span class="sxs-lookup"><span data-stu-id="5166f-131">Represents the `<!ENTITY…>` declarations in an XML document, either from an internal document type definition (DTD) subset or from external DTDs and parameter entities.</span></span>|  
|<span data-ttu-id="5166f-132">Notation</span><span class="sxs-lookup"><span data-stu-id="5166f-132">Notation</span></span>|<xref:System.Xml.XmlNotation>|<span data-ttu-id="5166f-133">DTD で宣言された記法を表します。</span><span class="sxs-lookup"><span data-stu-id="5166f-133">Represents a notation declared in the DTD.</span></span>|  
  
 <span data-ttu-id="5166f-134">属性 (*attr*) は、W3C DOM Level 1 のセクション 1.2「Fundamental Interfaces」ではノードとして記載されていますが、どの要素ノードの子とも見なされません。</span><span class="sxs-lookup"><span data-stu-id="5166f-134">Even though an attribute (*attr*) is listed in the W3C DOM Level 1 section 1.2 Fundamental Interfaces as a node, it is not considered a child of any element node.</span></span>  
  
 <span data-ttu-id="5166f-135">W3C では定義されていない追加のノード型を次の表に示します。ただし、これらのノード型は **XmlNodeType** 列挙値としてのみ Microsoft .NET Framework オブジェクト モデルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5166f-135">The following table shows additional node types not defined by the W3C, however they are available for use in the Microsoft .NET Framework object model as **XmlNodeType** enumerations.</span></span> <span data-ttu-id="5166f-136">そのため、これらのノード型に対応する DOM ノード型の列はありません。</span><span class="sxs-lookup"><span data-stu-id="5166f-136">Therefore, there is no matching DOM node type column for these node types.</span></span>  
  
|<span data-ttu-id="5166f-137">ノード型</span><span class="sxs-lookup"><span data-stu-id="5166f-137">Node type</span></span>|<span data-ttu-id="5166f-138">説明</span><span class="sxs-lookup"><span data-stu-id="5166f-138">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|<span data-ttu-id="5166f-139">宣言ノード `<?xml version="1.0"…>` を表します。</span><span class="sxs-lookup"><span data-stu-id="5166f-139">Represents the declaration node `<?xml version="1.0"…>`.</span></span>|  
|<xref:System.Xml.XmlSignificantWhitespace>|<span data-ttu-id="5166f-140">有意の空白を表します。これは混合コンテンツの空白です。</span><span class="sxs-lookup"><span data-stu-id="5166f-140">Represents significant white space, which is white space in mixed content.</span></span>|  
|<xref:System.Xml.XmlWhitespace>|<span data-ttu-id="5166f-141">要素コンテンツ内の空白を表します。</span><span class="sxs-lookup"><span data-stu-id="5166f-141">Represents the white space in the content of an element.</span></span>|  
|<span data-ttu-id="5166f-142">EndElement</span><span class="sxs-lookup"><span data-stu-id="5166f-142">EndElement</span></span>|<span data-ttu-id="5166f-143">**XmlReader** が要素の末尾に達したときに返されます。</span><span class="sxs-lookup"><span data-stu-id="5166f-143">Returned when **XmlReader** gets to the end of an element.</span></span><br /><br /> <span data-ttu-id="5166f-144">XML サンプル: **\</item>**</span><span class="sxs-lookup"><span data-stu-id="5166f-144">Example XML: **\</item>**</span></span><br /><br /> <span data-ttu-id="5166f-145">詳細については、「<xref:System.Xml.XmlNodeType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5166f-145">For more information, see <xref:System.Xml.XmlNodeType>.</span></span>|  
|<span data-ttu-id="5166f-146">EndEntity</span><span class="sxs-lookup"><span data-stu-id="5166f-146">EndEntity</span></span>|<span data-ttu-id="5166f-147"><xref:System.Xml.XmlReader.ResolveEntity%2A> を呼び出した後、置換するエンティティの末尾に **XmlReader** が達したときに返されます。</span><span class="sxs-lookup"><span data-stu-id="5166f-147">Returned when **XmlReader** gets to the end of the entity replacement as a result of a call to <xref:System.Xml.XmlReader.ResolveEntity%2A>.</span></span> <span data-ttu-id="5166f-148">詳細については、「<xref:System.Xml.XmlNodeType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5166f-148">For more information, see <xref:System.Xml.XmlNodeType>.</span></span>|  
  
 <span data-ttu-id="5166f-149">XML を読み込み、case 構成体を使用してノード型を判定し、ノードとその内容についての情報を出力するコード サンプルについては、「<xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5166f-149">To view a code example that reads in XML and uses a case construct on the node types to print information about the node and its contents, see <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.</span></span>  
  
 <span data-ttu-id="5166f-150">ノード型のオブジェクト階層構造とそれぞれに対応するオブジェクト名の詳細については、「[XML ドキュメント オブジェクト モデル (DOM) の階層構造](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5166f-150">For more information on the object hierarchy of the node types and their equivalent object name, see [XML Document Object Model (DOM) Hierarchy](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md).</span></span> <span data-ttu-id="5166f-151">ノード ツリーに作成されるオブジェクトの詳細については、「[オブジェクト階層の XML データへのマップ](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5166f-151">For more information on the objects created in the node tree, see [Mapping the Object Hierarchy to XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5166f-152">参照</span><span class="sxs-lookup"><span data-stu-id="5166f-152">See Also</span></span>  
 [<span data-ttu-id="5166f-153">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="5166f-153">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
