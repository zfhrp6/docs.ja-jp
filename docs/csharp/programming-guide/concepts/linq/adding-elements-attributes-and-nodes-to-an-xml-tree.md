---
title: XML ツリーへの要素、属性、およびノードの追加
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: 2996b4f24b421e7a818381817e598804f9199d38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="9667c-102">XML ツリーへの要素、属性、およびノードの追加</span><span class="sxs-lookup"><span data-stu-id="9667c-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="9667c-103">コンテンツ (要素、属性、コメント、処理命令、テキスト、および CDATA) を既存の XML ツリーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="9667c-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="9667c-104">コンテンツを追加するためのメソッド</span><span class="sxs-lookup"><span data-stu-id="9667c-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="9667c-105">次のメソッドを使用すると、<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument> に子コンテンツを追加できます。</span><span class="sxs-lookup"><span data-stu-id="9667c-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="9667c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9667c-106">Method</span></span>|<span data-ttu-id="9667c-107">説明</span><span class="sxs-lookup"><span data-stu-id="9667c-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="9667c-108"><xref:System.Xml.Linq.XContainer> の子コンテンツの末尾にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="9667c-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="9667c-109"><xref:System.Xml.Linq.XContainer> の子コンテンツの冒頭にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="9667c-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="9667c-110">次のメソッドは、<xref:System.Xml.Linq.XNode> の兄弟ノードとしてコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="9667c-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="9667c-111">兄弟コンテンツの追加先となる最も一般的なノードは <xref:System.Xml.Linq.XElement> ですが、<xref:System.Xml.Linq.XText> や <xref:System.Xml.Linq.XComment> など別の種類のノードに、有効な兄弟コンテンツを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="9667c-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="9667c-112">メソッド</span><span class="sxs-lookup"><span data-stu-id="9667c-112">Method</span></span>|<span data-ttu-id="9667c-113">説明</span><span class="sxs-lookup"><span data-stu-id="9667c-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="9667c-114"><xref:System.Xml.Linq.XNode> の後にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="9667c-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="9667c-115"><xref:System.Xml.Linq.XNode> の前にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="9667c-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9667c-116">例</span><span class="sxs-lookup"><span data-stu-id="9667c-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="9667c-117">説明</span><span class="sxs-lookup"><span data-stu-id="9667c-117">Description</span></span>  
 <span data-ttu-id="9667c-118">次の例では、2 つの XML ツリーを作成し、その 1 つを変更します。</span><span class="sxs-lookup"><span data-stu-id="9667c-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="9667c-119">コード</span><span class="sxs-lookup"><span data-stu-id="9667c-119">Code</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",   
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a><span data-ttu-id="9667c-120">コメント</span><span class="sxs-lookup"><span data-stu-id="9667c-120">Comments</span></span>  
 <span data-ttu-id="9667c-121">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9667c-121">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9667c-122">参照</span><span class="sxs-lookup"><span data-stu-id="9667c-122">See Also</span></span>  
 [<span data-ttu-id="9667c-123">XML ツリーの変更 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9667c-123">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
