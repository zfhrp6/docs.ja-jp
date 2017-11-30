---
title: "XslCompiledTransform クラスへの入力"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 97d636583393ab856a9c17af4c974c53fbde5767
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a><span data-ttu-id="d4766-102">XslCompiledTransform クラスへの入力</span><span class="sxs-lookup"><span data-stu-id="d4766-102">Inputs to the XslCompiledTransform Class</span></span>
<span data-ttu-id="d4766-103"><xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドには、<xref:System.Xml.XPath.IXPathNavigable> インターフェイスを実装するオブジェクト、ソース ドキュメントを読み取る <xref:System.Xml.XmlReader> オブジェクト、文字列 URI という 3 種類のソース ドキュメントを入力できます。</span><span class="sxs-lookup"><span data-stu-id="d4766-103">The <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method accepts three input types for the source document: an object that implements the <xref:System.Xml.XPath.IXPathNavigable> interface, an <xref:System.Xml.XmlReader> object that reads the source document, or a string URI.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4766-104"><xref:System.Xml.Xsl.XslCompiledTransform> クラスは既定で空白を維持します。</span><span class="sxs-lookup"><span data-stu-id="d4766-104">The <xref:System.Xml.Xsl.XslCompiledTransform> class preserves white space by default.</span></span> <span data-ttu-id="d4766-105">このことは、W3C XSLT 1.0 勧告 (セクション 3.4、http://www.w3.org/TR/xslt.html#strip) のセクション 3.4 に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="d4766-105">This is in accordance with section 3.4 of the W3C XSLT 1.0 recommendation (section 3.4, http://www.w3.org/TR/xslt.html#strip).</span></span>  
  
## <a name="ixpathnavigable-interface"></a><span data-ttu-id="d4766-106">IXPathNavigable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4766-106">IXPathNavigable Interface</span></span>  
 <span data-ttu-id="d4766-107"><xref:System.Xml.XPath.IXPathNavigable> インターフェイスは、<xref:System.Xml.XmlNode> および <xref:System.Xml.XPath.XPathDocument> クラスに実装されています。</span><span class="sxs-lookup"><span data-stu-id="d4766-107">The <xref:System.Xml.XPath.IXPathNavigable> interface is implemented in the <xref:System.Xml.XmlNode> and <xref:System.Xml.XPath.XPathDocument> classes.</span></span> <span data-ttu-id="d4766-108">これらのクラスは XML データのメモリ内のキャッシュを表します。</span><span class="sxs-lookup"><span data-stu-id="d4766-108">These classes represent an in-memory cache of XML data.</span></span>  
  
-   <span data-ttu-id="d4766-109"><xref:System.Xml.XmlNode> クラスは W3C ドキュメント オブジェクト モデル (DOM) を基礎とし、編集機能も含んでいます。</span><span class="sxs-lookup"><span data-stu-id="d4766-109">The <xref:System.Xml.XmlNode> class is based on the W3C Document Object Model (DOM) and includes editing capabilities.</span></span>  
  
-   <span data-ttu-id="d4766-110"><xref:System.Xml.XPath.XPathDocument> クラスは、XPath データ モデルに基づいた読み取り専用のデータ ストアです。</span><span class="sxs-lookup"><span data-stu-id="d4766-110">The <xref:System.Xml.XPath.XPathDocument> class is a read-only data store based on the XPath data model.</span></span> <span data-ttu-id="d4766-111"><xref:System.Xml.XPath.XPathDocument> は、XSLT 処理に推奨されるクラスです。</span><span class="sxs-lookup"><span data-stu-id="d4766-111"><xref:System.Xml.XPath.XPathDocument> is the recommended class for XSLT processing.</span></span> <span data-ttu-id="d4766-112">これは、<xref:System.Xml.XmlNode> クラスと比較して、より高速なパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="d4766-112">It provides faster performance when compared to the <xref:System.Xml.XmlNode> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4766-113">変換はドキュメント全体に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="d4766-113">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="d4766-114">つまり、ドキュメント ルート ノード以外のノードを指定しても、変換処理では、読み込んだドキュメントのすべてのノードがアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="d4766-114">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="d4766-115">ノード フラグメントを変換するには、ノード フラグメントだけを含むオブジェクトを作成し、そのオブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="d4766-115">To transform a node fragment, you must create an object containing just the node fragment, and pass that object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="d4766-116">詳細については、次を参照してください。[する方法: ノード フラグメントを変換](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4766-116">For more information, see [How to: Transform a Node Fragment](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).</span></span>  
  
 <span data-ttu-id="d4766-117">次の例では、<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> メソッドにより、transform.xsl スタイル シートを使用して books.xml ファイルを books.html ファイルに変換しています。</span><span class="sxs-lookup"><span data-stu-id="d4766-117">The following example uses the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> method to transform the books.xml file to the books.html file using the transform.xsl style sheet.</span></span> <span data-ttu-id="d4766-118">このトピックの「books.xml と transform.xsl ファイルが見つかりません:[する方法: アセンブリを使用して XSLT 変換を実行](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4766-118">The books.xml and transform.xsl files can be found in this topic: [How to: Perform an XSLT Transformation by Using an Assembly](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).</span></span>  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a><span data-ttu-id="d4766-119">XmlReader オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d4766-119">XmlReader Object</span></span>  
 <span data-ttu-id="d4766-120"><xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドは、<xref:System.Xml.XmlReader> の現在のノードから、そのすべての子を通して読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d4766-120">The <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method loads from the current node of the <xref:System.Xml.XmlReader> through all its children.</span></span> <span data-ttu-id="d4766-121">これにより、ドキュメントの一部をコンテキスト ドキュメントとして使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d4766-121">This enables you to use a portion of a document as the context document.</span></span> <span data-ttu-id="d4766-122"><xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドから帰った後、<xref:System.Xml.XmlReader> は、コンテキスト ドキュメントの終了後の次のノード上に位置します。</span><span class="sxs-lookup"><span data-stu-id="d4766-122">After the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method returns, the <xref:System.Xml.XmlReader> is positioned on the next node after the end of the context document.</span></span> <span data-ttu-id="d4766-123">ドキュメントの末尾に到達すると、<xref:System.Xml.XmlReader> はファイルの末尾 (EOF) に位置します。</span><span class="sxs-lookup"><span data-stu-id="d4766-123">If the end of the document is reached, the <xref:System.Xml.XmlReader> is positioned at the end of file (EOF).</span></span>  
  
 <span data-ttu-id="d4766-124">次の例では、<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> メソッドにより、transform.xsl スタイル シートを使用して books.xml ファイルを books.html ファイルに変換しています。</span><span class="sxs-lookup"><span data-stu-id="d4766-124">The following example uses the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> method to transform the books.xml file to the books.html file using the transform.xsl style sheet.</span></span> <span data-ttu-id="d4766-125">このトピックの「books.xml と transform.xsl ファイルが見つかりません:[する方法: アセンブリを使用して XSLT 変換を実行](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4766-125">The books.xml and transform.xsl files can be found in this topic: [How to: Perform an XSLT Transformation by Using an Assembly](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).</span></span>  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a><span data-ttu-id="d4766-126">文字列 URI</span><span class="sxs-lookup"><span data-stu-id="d4766-126">String URI</span></span>  
 <span data-ttu-id="d4766-127">XSLT の入力としてソース ドキュメントの URI を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4766-127">You can also specify the source document URI as your XSLT input.</span></span> <span data-ttu-id="d4766-128">URI の解決には <xref:System.Xml.XmlResolver> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d4766-128">An <xref:System.Xml.XmlResolver> is used to resolve the URI.</span></span> <span data-ttu-id="d4766-129"><xref:System.Xml.XmlResolver> を <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡して、使用するリゾルバーを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="d4766-129">You can specify the <xref:System.Xml.XmlResolver> to use by passing it to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span> <span data-ttu-id="d4766-130"><xref:System.Xml.XmlResolver> が指定されていない場合、<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドは既定の <xref:System.Xml.XmlUrlResolver> を資格情報なしで使用します。</span><span class="sxs-lookup"><span data-stu-id="d4766-130">If an <xref:System.Xml.XmlResolver> is not specified, the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method uses a default <xref:System.Xml.XmlUrlResolver> with no credentials.</span></span>  
  
 <span data-ttu-id="d4766-131">次の例では、<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> メソッドにより、transform.xsl スタイル シートを使用して books.xml ファイルを books.html ファイルに変換しています。</span><span class="sxs-lookup"><span data-stu-id="d4766-131">The following example uses the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> method to transform the books.xml file to the books.html file using the transform.xsl style sheet.</span></span> <span data-ttu-id="d4766-132">このトピックの「books.xml と transform.xsl ファイルが見つかりません:[する方法: アセンブリを使用して XSLT 変換を実行](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4766-132">The books.xml and transform.xsl files can be found in this topic: [How to: Perform an XSLT Transformation by Using an Assembly](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).</span></span>  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 <span data-ttu-id="d4766-133">詳細については、次を参照してください。[を解決する外部のリソース中に XSLT 処理](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)です。</span><span class="sxs-lookup"><span data-stu-id="d4766-133">For more information, see [Resolving External Resources During XSLT Processing](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4766-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4766-134">See Also</span></span>  
 [<span data-ttu-id="d4766-135">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="d4766-135">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
