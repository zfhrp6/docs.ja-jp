---
title: XML ツリー (Visual Basic) への要素、属性、およびノードの追加
ms.date: 07/20/2015
ms.assetid: e243e694-c987-43aa-8b22-1e33dace582c
ms.openlocfilehash: 86d28f5974e30a9b7f1a1e830cd40c3cd916e8ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-visual-basic"></a><span data-ttu-id="a15bb-102">XML ツリー (Visual Basic) への要素、属性、およびノードの追加</span><span class="sxs-lookup"><span data-stu-id="a15bb-102">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="a15bb-103">コンテンツ (要素、属性、コメント、処理命令、テキスト、および CDATA) を既存の XML ツリーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="a15bb-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="a15bb-104">コンテンツを追加するためのメソッド</span><span class="sxs-lookup"><span data-stu-id="a15bb-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="a15bb-105">次のメソッドを使用すると、<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument> に子コンテンツを追加できます。</span><span class="sxs-lookup"><span data-stu-id="a15bb-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="a15bb-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="a15bb-106">Method</span></span>|<span data-ttu-id="a15bb-107">説明</span><span class="sxs-lookup"><span data-stu-id="a15bb-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="a15bb-108"><xref:System.Xml.Linq.XContainer> の子コンテンツの末尾にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="a15bb-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="a15bb-109"><xref:System.Xml.Linq.XContainer> の子コンテンツの冒頭にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="a15bb-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="a15bb-110">次のメソッドは、<xref:System.Xml.Linq.XNode> の兄弟ノードとしてコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="a15bb-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="a15bb-111">兄弟コンテンツの追加先となる最も一般的なノードは <xref:System.Xml.Linq.XElement> ですが、<xref:System.Xml.Linq.XText> や <xref:System.Xml.Linq.XComment> など別の種類のノードに、有効な兄弟コンテンツを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="a15bb-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="a15bb-112">メソッド</span><span class="sxs-lookup"><span data-stu-id="a15bb-112">Method</span></span>|<span data-ttu-id="a15bb-113">説明</span><span class="sxs-lookup"><span data-stu-id="a15bb-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="a15bb-114"><xref:System.Xml.Linq.XNode> の後にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="a15bb-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="a15bb-115"><xref:System.Xml.Linq.XNode> の前にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="a15bb-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a15bb-116">例</span><span class="sxs-lookup"><span data-stu-id="a15bb-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a15bb-117">説明</span><span class="sxs-lookup"><span data-stu-id="a15bb-117">Description</span></span>  
 <span data-ttu-id="a15bb-118">次の例では、2 つの XML ツリーを作成し、その 1 つを変更します。</span><span class="sxs-lookup"><span data-stu-id="a15bb-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a15bb-119">コード</span><span class="sxs-lookup"><span data-stu-id="a15bb-119">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="a15bb-120">コメント</span><span class="sxs-lookup"><span data-stu-id="a15bb-120">Comments</span></span>  
 <span data-ttu-id="a15bb-121">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a15bb-121">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a15bb-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a15bb-122">See Also</span></span>  
 [<span data-ttu-id="a15bb-123">XML ツリー (LINQ to XML) の変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a15bb-123">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
