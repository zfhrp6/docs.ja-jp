---
title: "XML ツリー (Visual Basic の場合) からの要素、属性、およびノードの削除 |Microsoft ドキュメント"
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
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8842858080ce1f27d997e6af61a8dd2301cdc2bc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="1752c-102">XML ツリー (Visual Basic の場合) からの要素、属性、およびノードの削除</span><span class="sxs-lookup"><span data-stu-id="1752c-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="1752c-103">要素、属性、およびその他の種類のノードを削除して、XML ツリーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="1752c-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="1752c-104">1 つの要素または&1; つの属性は XML ドキュメントから簡単に削除できます。</span><span class="sxs-lookup"><span data-stu-id="1752c-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="1752c-105">一方、要素または属性のコレクションを削除する場合は、まずコレクションをリストに具体化し、そのリストから要素または属性を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1752c-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="1752c-106">最良のアプローチが使用するには、<xref:System.Xml.Linq.Extensions.Remove%2A>拡張メソッドは、これはするが実行されます</xref:System.Xml.Linq.Extensions.Remove%2A>。</span><span class="sxs-lookup"><span data-stu-id="1752c-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="1752c-107">このような方法でコレクションの削除を実行する主な理由は、XML ツリーから取得するコレクションのほとんどが遅延実行を使用して生成されるからです。</span><span class="sxs-lookup"><span data-stu-id="1752c-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="1752c-108">最初にコレクションをリストに具体化せず、拡張メソッドも使用しない場合、特定の種類のバグが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1752c-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="1752c-109">詳細については、次を参照してください。[混在宣言型コードと命令型コードのバグ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="1752c-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="1752c-110">ノードおよび属性を XML ツリーから削除するメソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1752c-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="1752c-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="1752c-111">Method</span></span>|<span data-ttu-id="1752c-112">説明</span><span class="sxs-lookup"><span data-stu-id="1752c-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1752c-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1752c-113">[XAttribute.Remove](https://msdn.microsoft.com/library/system.xml.linq.xattribute.remove\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="1752c-114">削除、<xref:System.Xml.Linq.XAttribute>を親から</xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="1752c-114">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<span data-ttu-id="1752c-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="1752c-115">[XContainer.RemoveNodes](https://msdn.microsoft.com/library/system.xml.linq.xcontainer.removenodes\(v=vs.110\).aspx)</span></span>|<span data-ttu-id="1752c-116"><xref:System.Xml.Linq.XContainer>。</xref:System.Xml.Linq.XContainer>から子ノードを削除します。</span><span class="sxs-lookup"><span data-stu-id="1752c-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<span data-ttu-id="1752c-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1752c-117"><xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName></span></span>|<span data-ttu-id="1752c-118"><xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>からコンテンツおよび属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="1752c-118">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="1752c-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1752c-119"><xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName></span></span>|<span data-ttu-id="1752c-120"><xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>の属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="1752c-120">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<span data-ttu-id="1752c-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1752c-121"><xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="1752c-122">`null` を値に受け取ると、属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="1752c-122">If you pass `null` for value, then removes the attribute.</span></span>|  
|<span data-ttu-id="1752c-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1752c-123"><xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName></span></span>|<span data-ttu-id="1752c-124">`null` を値に受け取ると、子要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="1752c-124">If you pass `null` for value, then removes the child element.</span></span>|  
|<span data-ttu-id="1752c-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1752c-125"><xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="1752c-126">削除、<xref:System.Xml.Linq.XNode>を親から</xref:System.Xml.Linq.XNode>。</span><span class="sxs-lookup"><span data-stu-id="1752c-126">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<span data-ttu-id="1752c-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1752c-127"><xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=fullName></span></span>|<span data-ttu-id="1752c-128">ソース コレクション内のすべての属性または要素をその親要素から削除します。</span><span class="sxs-lookup"><span data-stu-id="1752c-128">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1752c-129">例</span><span class="sxs-lookup"><span data-stu-id="1752c-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1752c-130">説明</span><span class="sxs-lookup"><span data-stu-id="1752c-130">Description</span></span>  
 <span data-ttu-id="1752c-131">この例では、要素を削除する&3; つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1752c-131">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="1752c-132">まず、1 つの要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="1752c-132">First, it removes a single element.</span></span> <span data-ttu-id="1752c-133">次に、要素のコレクションの取得を具体化して、使用して、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>演算子、およびコレクションを削除します</xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="1752c-133">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> operator, and removes the collection.</span></span> <span data-ttu-id="1752c-134">最後に、要素のコレクションを取得し、削除を使用して、<xref:System.Xml.Linq.Extensions.Remove%2A>拡張メソッド</xref:System.Xml.Linq.Extensions.Remove%2A>。</span><span class="sxs-lookup"><span data-stu-id="1752c-134">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="1752c-135">詳細については、<xref:System.Linq.Enumerable.ToList%2A>演算子を参照してください[データ型を変換する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)</xref:System.Linq.Enumerable.ToList%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1752c-135">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="1752c-136">コード</span><span class="sxs-lookup"><span data-stu-id="1752c-136">Code</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
  
```  
  
### <a name="comments"></a><span data-ttu-id="1752c-137">コメント</span><span class="sxs-lookup"><span data-stu-id="1752c-137">Comments</span></span>  
 <span data-ttu-id="1752c-138">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1752c-138">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="1752c-139">最初の孫要素が `Child1` から削除されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="1752c-139">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="1752c-140">すべての孫要素が、`Child2` と `Child3` から削除されています。</span><span class="sxs-lookup"><span data-stu-id="1752c-140">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1752c-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="1752c-141">See Also</span></span>  
 [<span data-ttu-id="1752c-142">XML ツリー (LINQ to XML) の変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1752c-142">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
