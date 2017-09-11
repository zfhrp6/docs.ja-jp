---
title: "XElement オブジェクトと XDocument Objects2 の有効なコンテンツ |Microsoft ドキュメント"
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
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: ecdcd4c2c0ec61cf248c9e210d42abb750e0546b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="a8afa-102">XElement オブジェクトと XDocument オブジェクトの有効なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="a8afa-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="a8afa-103">ここでは、コンストラクターやメソッドに渡すことができる有効な引数について説明します。これらのコンストラクターやメソッドは、コンテンツを要素やドキュメントに追加するためのものです。</span><span class="sxs-lookup"><span data-stu-id="a8afa-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="a8afa-104">有効なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="a8afa-104">Valid Content</span></span>  
 <span data-ttu-id="a8afa-105">クエリは多くの場合、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Xml.Linq.XElement><xref:System.Collections.Generic.IEnumerable%601><xref:System.Xml.Linq.XAttribute>。</xref:System.Xml.Linq.XAttribute></xref:System.Collections.Generic.IEnumerable%601></xref:System.Xml.Linq.XElement></xref:System.Collections.Generic.IEnumerable%601>に評価されます。</span><span class="sxs-lookup"><span data-stu-id="a8afa-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="a8afa-106">コレクションを渡すことができます<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>オブジェクトを<xref:System.Xml.Linq.XElement>コンス トラクター</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="a8afa-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="a8afa-107">したがって、XML ツリーの設定に使用するメソッドとコンストラクターに対して、クエリの結果をコンテンツとして渡すと便利です。</span><span class="sxs-lookup"><span data-stu-id="a8afa-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="a8afa-108">単純コンテンツを追加するときに、さまざまな型をこのメソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a8afa-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="a8afa-109">有効な型は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a8afa-109">Valid types include the following:</span></span>  
  
-   <span data-ttu-id="a8afa-110"><xref:System.String></xref:System.String></span><span class="sxs-lookup"><span data-stu-id="a8afa-110"><xref:System.String></span></span>  
  
-   <span data-ttu-id="a8afa-111"><xref:System.Double></xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="a8afa-111"><xref:System.Double></span></span>  
  
-   <span data-ttu-id="a8afa-112"><xref:System.Single></xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="a8afa-112"><xref:System.Single></span></span>  
  
-   <span data-ttu-id="a8afa-113"><xref:System.Decimal></xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="a8afa-113"><xref:System.Decimal></span></span>  
  
-   <span data-ttu-id="a8afa-114"><xref:System.Boolean></xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="a8afa-114"><xref:System.Boolean></span></span>  
  
-   <span data-ttu-id="a8afa-115"><xref:System.DateTime></xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="a8afa-115"><xref:System.DateTime></span></span>  
  
-   <span data-ttu-id="a8afa-116"><xref:System.TimeSpan></xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="a8afa-116"><xref:System.TimeSpan></span></span>  
  
-   <span data-ttu-id="a8afa-117"><xref:System.DateTimeOffset></xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="a8afa-117"><xref:System.DateTimeOffset></span></span>  
  
-   <span data-ttu-id="a8afa-118">`Object.ToString` を実装する任意の型</span><span class="sxs-lookup"><span data-stu-id="a8afa-118">Any type that implements `Object.ToString`.</span></span>  
  
-   <span data-ttu-id="a8afa-119"><xref:System.Collections.Generic.IEnumerable%601>。</xref:System.Collections.Generic.IEnumerable%601>を実装する任意の型</span><span class="sxs-lookup"><span data-stu-id="a8afa-119">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="a8afa-120">複合コンテンツを追加するときは、次のような型をこのメソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a8afa-120">When adding complex content, various types can be passed to this method:</span></span>  
  
-   <span data-ttu-id="a8afa-121"><xref:System.Xml.Linq.XObject></xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="a8afa-121"><xref:System.Xml.Linq.XObject></span></span>  
  
-   <span data-ttu-id="a8afa-122"><xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="a8afa-122"><xref:System.Xml.Linq.XNode></span></span>  
  
-   <span data-ttu-id="a8afa-123"><xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="a8afa-123"><xref:System.Xml.Linq.XAttribute></span></span>  
  
-   <span data-ttu-id="a8afa-124">実装する任意の型<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="a8afa-124">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="a8afa-125">オブジェクトを実装する場合<xref:System.Collections.Generic.IEnumerable%601>、オブジェクトのコレクションが列挙され、コレクション内のすべての項目が追加されます</xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="a8afa-125">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="a8afa-126">コレクションに含まれる場合<xref:System.Xml.Linq.XNode>または<xref:System.Xml.Linq.XAttribute>オブジェクト、コレクション内の各アイテムは個別に追加されます</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XNode>。</span><span class="sxs-lookup"><span data-stu-id="a8afa-126">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="a8afa-127">コレクションにテキスト (またはテキストに変換されるオブジェクト) が含まれている場合、コレクション内のテキストが連結され、1 つのテキスト ノードとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="a8afa-127">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="a8afa-128">コンテンツが `null` の場合は、何も追加されません。</span><span class="sxs-lookup"><span data-stu-id="a8afa-128">If content is `null`, nothing is added.</span></span> <span data-ttu-id="a8afa-129">コレクションを渡すとき、コレクション内の項目は `null` にできます。</span><span class="sxs-lookup"><span data-stu-id="a8afa-129">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="a8afa-130">コレクション内の `null` 項目は、ツリーに影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="a8afa-130">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="a8afa-131">追加する属性の名前は、そのコンテナー要素内で一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="a8afa-131">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="a8afa-132">追加するときに<xref:System.Xml.Linq.XNode>または<xref:System.Xml.Linq.XAttribute>オブジェクトの場合、新しいコンテンツに親があるない場合、オブジェクトは単に、XML ツリーにアタッチします</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XNode>。</span><span class="sxs-lookup"><span data-stu-id="a8afa-132">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="a8afa-133">新しいコンテンツに既に親があり、別の XML ツリーの一部となっている場合は、新しいコンテンツが複製され、新しく複製されたコンテンツが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="a8afa-133">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="a8afa-134">ドキュメントの有効なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="a8afa-134">Valid Content for Documents</span></span>  
 <span data-ttu-id="a8afa-135">属性と単純コンテンツをドキュメントに追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="a8afa-135">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="a8afa-136"><xref:System.Xml.Linq.XDocument>。</xref:System.Xml.Linq.XDocument>を作成する必要がある多くのシナリオはありません。</span><span class="sxs-lookup"><span data-stu-id="a8afa-136">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="a8afa-137">代わりに、使用して XML ツリー作成通常、<xref:System.Xml.Linq.XElement>ルート ノードです</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="a8afa-137">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="a8afa-138">しない限り、ドキュメントを作成 (たとえば、最上位のレベルでは、処理命令とコメントを作成する必要があるまたはドキュメント型をサポートする必要がある) する特定の要件がある、方が容易に<xref:System.Xml.Linq.XElement>ルート ノードとして</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="a8afa-138">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="a8afa-139">ドキュメントの有効なコンテンツは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a8afa-139">Valid content for a document includes the following:</span></span>  
  
-   <span data-ttu-id="a8afa-140">0 または&1; 個<xref:System.Xml.Linq.XDocumentType>オブジェクト</xref:System.Xml.Linq.XDocumentType>。</span><span class="sxs-lookup"><span data-stu-id="a8afa-140">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="a8afa-141">ドキュメントの型は、要素の前に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8afa-141">The document types must come before the element.</span></span>  
  
-   <span data-ttu-id="a8afa-142">0 個または&1; 個の要素。</span><span class="sxs-lookup"><span data-stu-id="a8afa-142">Zero or one element.</span></span>  
  
-   <span data-ttu-id="a8afa-143">0 個以上のコメント。</span><span class="sxs-lookup"><span data-stu-id="a8afa-143">Zero or more comments.</span></span>  
  
-   <span data-ttu-id="a8afa-144">0 個以上の処理命令。</span><span class="sxs-lookup"><span data-stu-id="a8afa-144">Zero or more processing instructions.</span></span>  
  
-   <span data-ttu-id="a8afa-145">空白のみを含む、0 個以上のテキスト ノード。</span><span class="sxs-lookup"><span data-stu-id="a8afa-145">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="a8afa-146">コンテンツの追加が可能なコンストラクターと関数</span><span class="sxs-lookup"><span data-stu-id="a8afa-146">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="a8afa-147">次の方法では、子コンテンツへの追加<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>::</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>できます。</span><span class="sxs-lookup"><span data-stu-id="a8afa-147">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="a8afa-148">メソッド</span><span class="sxs-lookup"><span data-stu-id="a8afa-148">Method</span></span>|<span data-ttu-id="a8afa-149">説明</span><span class="sxs-lookup"><span data-stu-id="a8afa-149">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a8afa-150"><xref:System.Xml.Linq.XElement.%23ctor%2A></xref:System.Xml.Linq.XElement.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-150"><xref:System.Xml.Linq.XElement.%23ctor%2A></span></span>|<span data-ttu-id="a8afa-151"><xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>の構築します。</span><span class="sxs-lookup"><span data-stu-id="a8afa-151">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="a8afa-152"><xref:System.Xml.Linq.XDocument.%23ctor%2A></xref:System.Xml.Linq.XDocument.%23ctor%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-152"><xref:System.Xml.Linq.XDocument.%23ctor%2A></span></span>|<span data-ttu-id="a8afa-153"><xref:System.Xml.Linq.XDocument>。</xref:System.Xml.Linq.XDocument>の構築します。</span><span class="sxs-lookup"><span data-stu-id="a8afa-153">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<span data-ttu-id="a8afa-154"><xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XContainer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-154"><xref:System.Xml.Linq.XContainer.Add%2A></span></span>|<span data-ttu-id="a8afa-155"><xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>.</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>の子コンテンツの末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="a8afa-155">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<span data-ttu-id="a8afa-156"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-156"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span></span>|<span data-ttu-id="a8afa-157"><xref:System.Xml.Linq.XNode>。</xref:System.Xml.Linq.XNode>後にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="a8afa-157">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<span data-ttu-id="a8afa-158"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-158"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span></span>|<span data-ttu-id="a8afa-159"><xref:System.Xml.Linq.XNode>。</xref:System.Xml.Linq.XNode>する前にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="a8afa-159">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<span data-ttu-id="a8afa-160"><xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XContainer.AddFirst%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-160"><xref:System.Xml.Linq.XContainer.AddFirst%2A></span></span>|<span data-ttu-id="a8afa-161"><xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer>の子コンテンツの冒頭にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="a8afa-161">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="a8afa-162"><xref:System.Xml.Linq.XElement.ReplaceAll%2A></xref:System.Xml.Linq.XElement.ReplaceAll%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-162"><xref:System.Xml.Linq.XElement.ReplaceAll%2A></span></span>|<span data-ttu-id="a8afa-163"><xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>のすべてのコンテンツ (子ノードおよび属性) を置き換えます</span><span class="sxs-lookup"><span data-stu-id="a8afa-163">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="a8afa-164"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-164"><xref:System.Xml.Linq.XElement.ReplaceAttributes%2A></span></span>|<span data-ttu-id="a8afa-165"><xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>属性に置き換えられます</span><span class="sxs-lookup"><span data-stu-id="a8afa-165">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="a8afa-166"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-166"><xref:System.Xml.Linq.XContainer.ReplaceNodes%2A></span></span>|<span data-ttu-id="a8afa-167">子ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a8afa-167">Replaces the children nodes with new content.</span></span>|  
|<span data-ttu-id="a8afa-168"><xref:System.Xml.Linq.XNode.ReplaceWith%2A></xref:System.Xml.Linq.XNode.ReplaceWith%2A></span><span class="sxs-lookup"><span data-stu-id="a8afa-168"><xref:System.Xml.Linq.XNode.ReplaceWith%2A></span></span>|<span data-ttu-id="a8afa-169">ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a8afa-169">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8afa-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8afa-170">See Also</span></span>  
 [<span data-ttu-id="a8afa-171">XML ツリー (Visual Basic) の作成</span><span class="sxs-lookup"><span data-stu-id="a8afa-171">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
