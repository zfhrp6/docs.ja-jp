---
title: "XML ツリー (Visual Basic) への要素、属性、およびノードの追加 |Microsoft ドキュメント"
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
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f8ee26aef896a2f404e815823ade83e204270613
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a><span data-ttu-id="20117-102">XML ツリー (Visual Basic) への要素、属性、およびノードの追加</span><span class="sxs-lookup"><span data-stu-id="20117-102">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="20117-103">コンテンツ (要素、属性、コメント、処理命令、テキスト、および CDATA) を既存の XML ツリーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="20117-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="20117-104">コンテンツを追加するためのメソッド</span><span class="sxs-lookup"><span data-stu-id="20117-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="20117-105">次の方法では、子コンテンツを追加<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XDocument>::</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="20117-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="20117-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="20117-106">Method</span></span>|<span data-ttu-id="20117-107">説明</span><span class="sxs-lookup"><span data-stu-id="20117-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="20117-108"><xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XContainer.Add%2A></span><span class="sxs-lookup"><span data-stu-id="20117-108"><xref:System.Xml.Linq.XContainer.Add%2A></span></span>|<span data-ttu-id="20117-109"><xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer>の子コンテンツの末尾にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="20117-109">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="20117-110"><xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XContainer.AddFirst%2A></span><span class="sxs-lookup"><span data-stu-id="20117-110"><xref:System.Xml.Linq.XContainer.AddFirst%2A></span></span>|<span data-ttu-id="20117-111"><xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer>の子コンテンツの冒頭にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="20117-111">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="20117-112">次のメソッドは、 <xref:System.Xml.Linq.XNode>。</xref:System.Xml.Linq.XNode>の兄弟ノードとしてコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="20117-112">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="20117-113">兄弟コンテンツを追加する最も一般的なノードが<xref:System.Xml.Linq.XElement>有効な兄弟コンテンツ ノード<xref:System.Xml.Linq.XText>または<xref:System.Xml.Linq.XComment>.</xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XText>などの他の種類を追加できますが、</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="20117-113">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="20117-114">メソッド</span><span class="sxs-lookup"><span data-stu-id="20117-114">Method</span></span>|<span data-ttu-id="20117-115">説明</span><span class="sxs-lookup"><span data-stu-id="20117-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="20117-116"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span><span class="sxs-lookup"><span data-stu-id="20117-116"><xref:System.Xml.Linq.XNode.AddAfterSelf%2A></span></span>|<span data-ttu-id="20117-117"><xref:System.Xml.Linq.XNode>。</xref:System.Xml.Linq.XNode>後にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="20117-117">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<span data-ttu-id="20117-118"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span><span class="sxs-lookup"><span data-stu-id="20117-118"><xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></span></span>|<span data-ttu-id="20117-119"><xref:System.Xml.Linq.XNode>。</xref:System.Xml.Linq.XNode>する前にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="20117-119">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="20117-120">例</span><span class="sxs-lookup"><span data-stu-id="20117-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="20117-121">説明</span><span class="sxs-lookup"><span data-stu-id="20117-121">Description</span></span>  
 <span data-ttu-id="20117-122">次の例では、2 つの XML ツリーを作成し、その&1; つを変更します。</span><span class="sxs-lookup"><span data-stu-id="20117-122">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="20117-123">コード</span><span class="sxs-lookup"><span data-stu-id="20117-123">Code</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element1>1</Element1>  
        <Element2>2</Element2>  
        <Element3>3</Element3>  
        <Element4>4</Element4>  
        <Element5>5</Element5>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child1>1</Child1>  
        <Child2>2</Child2>  
        <Child3>3</Child3>  
        <Child4>4</Child4>  
        <Child5>5</Child5>  
    </Root>  
  
xmlTree.Add(<NewChild>new content</NewChild>)  
xmlTree.Add( _  
    From el In srcTree.Elements() _  
    Where CInt(el) > 3 _  
    Select el)  
  
' Even though Child9 does not exist in srcTree, the following statement  
' will not throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"))  
Console.WriteLine(xmlTree)  
  
```  
  
### <a name="comments"></a><span data-ttu-id="20117-124">コメント</span><span class="sxs-lookup"><span data-stu-id="20117-124">Comments</span></span>  
 <span data-ttu-id="20117-125">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="20117-125">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20117-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="20117-126">See Also</span></span>  
 [<span data-ttu-id="20117-127">XML ツリー (LINQ to XML) の変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20117-127">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
