---
title: XPathNavigator を使用した XML データの選択
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c937754f031420d90f89bf89563db17ddaaf3bbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572123"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="a8791-102">XPathNavigator を使用した XML データの選択</span><span class="sxs-lookup"><span data-stu-id="a8791-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="a8791-103"><xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクト内で XPath 式を使用してノード セットを選択するための一連のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a8791-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="a8791-104">選択した後、選択されたノード セットに対して反復して処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a8791-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="a8791-105">XPathNavigator の選択メソッド</span><span class="sxs-lookup"><span data-stu-id="a8791-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="a8791-106"><xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathDocument> オブジェクトまたは <xref:System.Xml.XmlDocument> オブジェクト内で XPath 式を使用してノード セットを選択するための一連のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a8791-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="a8791-107"><xref:System.Xml.XPath.XPathNavigator> クラスは、祖先、子、および子孫のノードを、XPath 式を使用するよりも高速に選択できる最適化された一連のメソッドも提供します。</span><span class="sxs-lookup"><span data-stu-id="a8791-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="a8791-108">選択されたノード セットは、<xref:System.Xml.XPath.XPathNodeIterator> オブジェクトまたは、選択されたノードが単一の場合は <xref:System.Xml.XPath.XPathNavigator> オブジェクトとして返されます。</span><span class="sxs-lookup"><span data-stu-id="a8791-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="a8791-109">XPath 式によるノードの選択</span><span class="sxs-lookup"><span data-stu-id="a8791-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="a8791-110">XPath 式を使用して 1 つのノード セットを選択するには、次のいずれかの選択メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8791-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="a8791-111">呼び出されると、これらのメソッドは <xref:System.Xml.XPath.XPathNodeIterator> オブジェクト、または選択が単一ノードの場合は <xref:System.Xml.XPath.XPathNavigator> オブジェクトを使用して、自由に移動できる 1 つのノード セットを返します。</span><span class="sxs-lookup"><span data-stu-id="a8791-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="a8791-112"><xref:System.Xml.XPath.XPathNodeIterator> オブジェクトを使用して移動しても、その作成に使用された <xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置に影響ありません。</span><span class="sxs-lookup"><span data-stu-id="a8791-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="a8791-113"><xref:System.Xml.XPath.XPathNavigator> メソッドから返された <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> オブジェクトは、返された単一ノード上に位置し、この場合もその作成に使用された <xref:System.Xml.XPath.XPathNavigator> オブジェクトの位置には影響しません。</span><span class="sxs-lookup"><span data-stu-id="a8791-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="a8791-114">次の例は、<xref:System.Xml.XPath.XPathNavigator> オブジェクトからの <xref:System.Xml.XPath.XPathDocument> オブジェクトの作成、<xref:System.Xml.XPath.XPathNavigator.Select%2A> メソッドを使用した <xref:System.Xml.XPath.XPathDocument> オブジェクト内のノードの選択、および <xref:System.Xml.XPath.XPathNodeIterator> オブジェクトを使用した選択ノード上の繰り返し処理について示しています。</span><span class="sxs-lookup"><span data-stu-id="a8791-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 <span data-ttu-id="a8791-115">この例は、`books.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="a8791-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="a8791-116">最適化された選択メソッド</span><span class="sxs-lookup"><span data-stu-id="a8791-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="a8791-117"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A>、および <xref:System.Xml.XPath.XPathNavigator> メソッドは、子、子孫、および祖先のノードにアクセスする一般的な XPath 式に相当します。</span><span class="sxs-lookup"><span data-stu-id="a8791-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="a8791-118">これらのメソッドのパフォーマンスは最適化されており、対応する XPath 式よりも高速です。</span><span class="sxs-lookup"><span data-stu-id="a8791-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="a8791-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>、<xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>、および <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> メソッドは、<xref:System.Xml.XPath.XPathNodeType> 値または選択するノードのローカル名と名前空間 URI を基にして祖先、子、および子孫のノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8791-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="a8791-120">選択された祖先、子、および子孫のノードは <xref:System.Xml.XPath.XPathNodeIterator> オブジェクトとして返されます。</span><span class="sxs-lookup"><span data-stu-id="a8791-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8791-121">参照</span><span class="sxs-lookup"><span data-stu-id="a8791-121">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="a8791-122">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="a8791-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="a8791-123">XPathNavigator による XPath 式の評価</span><span class="sxs-lookup"><span data-stu-id="a8791-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="a8791-124">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="a8791-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="a8791-125">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="a8791-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="a8791-126">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="a8791-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="a8791-127">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="a8791-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
