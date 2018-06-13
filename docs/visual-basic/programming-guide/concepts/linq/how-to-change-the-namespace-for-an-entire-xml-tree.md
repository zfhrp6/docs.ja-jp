---
title: '方法: Namespace、全体 XML ツリーを変更 (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 1837324b-5cb5-4fa8-95b9-3071efa0f913
ms.openlocfilehash: 1ef5ae9a2a8c4e69687809c117451d70dbfe211b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642988"
---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-visual-basic"></a><span data-ttu-id="5198a-102">方法: Namespace、全体 XML ツリーを変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5198a-102">How to: Change the Namespace for an Entire XML Tree (Visual Basic)</span></span>
<span data-ttu-id="5198a-103">要素または属性の名前空間をプログラムで変更しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5198a-103">You sometimes have to programmatically change the namespace for an element or an attribute.</span></span> <span data-ttu-id="5198a-104">LINQ to XML では、この操作を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5198a-104">LINQ to XML makes this easy.</span></span> <span data-ttu-id="5198a-105"><xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="5198a-105">The <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=nameWithType> property can be set.</span></span> <span data-ttu-id="5198a-106"><xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> プロパティは設定できませんが、簡単に属性を <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> にコピーし、既存の属性を削除して、目的の新しい名前空間に含まれる新しい属性を追加できます。</span><span class="sxs-lookup"><span data-stu-id="5198a-106">The <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=nameWithType> property cannot be set, but you can easily copy the attributes into a <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, remove the existing attributes, and then add new attributes that are in the new desired namespace.</span></span>  
  
 <span data-ttu-id="5198a-107">詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の操作](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)です。</span><span class="sxs-lookup"><span data-stu-id="5198a-107">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5198a-108">例</span><span class="sxs-lookup"><span data-stu-id="5198a-108">Example</span></span>  
 <span data-ttu-id="5198a-109">次のコードは、名前空間に含まれない 2 つの XML ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5198a-109">The following code creates two XML trees in no namespace.</span></span> <span data-ttu-id="5198a-110">次に、各ツリーの名前空間を変更して、1 つのツリーに結合します。</span><span class="sxs-lookup"><span data-stu-id="5198a-110">It then changes the namespace of each of the trees, and combines them into a single tree.</span></span>  
  
```vb  
Dim tree1 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim tree2 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim ad As XNamespace = "http://www.adatum.com"  
' change the namespace of every element and attribute in the first tree  
For Each el As XElement In tree1.DescendantsAndSelf  
    el.Name = aw.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' change the namespace of every element and attribute in the second tree  
For Each el As XElement In tree2.DescendantsAndSelf()  
    el.Name = ad.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' add attribute namespaces so that the tree will be serialized with  
' the aw and ad namespace prefixes  
tree1.Add( _  
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _  
)  
tree2.Add( _  
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _  
)  
' create a new composite tree  
Dim root As XElement = _  
    <Root>  
        <%= tree1 %>  
        <%= tree2 %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="5198a-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="5198a-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5198a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5198a-112">See Also</span></span>  
 [<span data-ttu-id="5198a-113">XML ツリー (LINQ to XML) の変更 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5198a-113">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
