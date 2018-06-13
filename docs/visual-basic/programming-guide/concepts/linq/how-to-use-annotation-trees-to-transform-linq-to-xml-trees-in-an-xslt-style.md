---
title: '方法: 注釈を使用して、LINQ to XML ツリーを XSLT スタイル (Visual Basic) を変換するには'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: c19d290e5b7acdf2702e24383a176ed06c9c7a1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650258"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a><span data-ttu-id="c8aa7-102">方法: 注釈を使用して、LINQ to XML ツリーを XSLT スタイル (Visual Basic) を変換するには</span><span class="sxs-lookup"><span data-stu-id="c8aa7-102">How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)</span></span>
<span data-ttu-id="c8aa7-103">注釈を使用することで、XML ツリーの変換が容易になります。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-103">Annotations can be used to facilitate transforms of an XML tree.</span></span>  
  
 <span data-ttu-id="c8aa7-104">XML ドキュメントには、"ドキュメント中心で混合コンテンツを含んでいる" ものがあります。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-104">Some XML documents are "document centric with mixed content."</span></span> <span data-ttu-id="c8aa7-105">このようなドキュメントでは、必ずしも要素の子ノードの構造を把握する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-105">With such documents, you don't necessarily know the shape of child nodes of an element.</span></span> <span data-ttu-id="c8aa7-106">たとえば、テキストを含んでいるノードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-106">For instance, a node that contains text may look like this:</span></span>  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 <span data-ttu-id="c8aa7-107">どのテキスト ノードにも、任意の数の `<b>` と `<i>` が子要素として存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-107">For any given text node, there may be any number of child `<b>` and `<i>` elements.</span></span> <span data-ttu-id="c8aa7-108">その他の状況の数まで、この方法: さまざまな通常の段落、箇条書きの段落、ビットマップなどの子要素を含めることができるページなどです。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-108">This approach extends to a number of other situations: such as, pages that can contain a variety of child elements, such as regular paragraphs, bulleted paragraphs, and bitmaps.</span></span> <span data-ttu-id="c8aa7-109">テーブルのセルには、テキスト、ドロップダウン リスト、またはビットマップが含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-109">Cells in a table may contain text, drop down lists, or bitmaps.</span></span> <span data-ttu-id="c8aa7-110">ドキュメント中心の XML の主要な特性の 1 つは、特定の要素がどの子要素を持つかがわからない点です。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-110">One of the primary characteristics of document centric XML is that you do not know which child element any particular element will have.</span></span>  
  
 <span data-ttu-id="c8aa7-111">ツリー内の要素を変換するとき、その要素の子について詳しく理解している必要がない場合は、注釈を使用するこの方法が効果的です。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-111">If you want to transform elements in a tree where you don't necessarily know much about the children of the elements that you want to transform, then this approach that uses annotations is an effective approach.</span></span>  
  
 <span data-ttu-id="c8aa7-112">この方法の概要は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-112">The summary of the approach is:</span></span>  
  
-   <span data-ttu-id="c8aa7-113">最初に、ツリー内の要素に置換要素を使用して注釈を付けます。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-113">First, annotate elements in the tree with a replacement element.</span></span>  
  
-   <span data-ttu-id="c8aa7-114">2 番目に、ツリー全体を反復処理して、各要素をその注釈で置換する新しいツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-114">Second, iterate through the entire tree, creating a new tree where you replace each element with its annotation.</span></span> <span data-ttu-id="c8aa7-115">ここで示す例では、`XForm` という関数で新しいツリーの反復処理と作成を実装しています。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-115">This example implements the iteration and creation of the new tree in a function named `XForm`.</span></span>  
  
 <span data-ttu-id="c8aa7-116">この方法の詳細な構成は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-116">In detail, the approach consists of:</span></span>  
  
-   <span data-ttu-id="c8aa7-117">構造を変換する一連の要素を返す 1 つ以上の LINQ to XML クエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-117">Execute one or more LINQ to XML queries that return the set of elements that you want to transform from one shape to another.</span></span> <span data-ttu-id="c8aa7-118">クエリ内の要素ごとに、新しい <xref:System.Xml.Linq.XElement> オブジェクトをその要素に対する注釈として追加します。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-118">For each element in the query, add a new <xref:System.Xml.Linq.XElement> object as an annotation to the element.</span></span> <span data-ttu-id="c8aa7-119">変換後の新しいツリーでは、注釈付きの要素がこの新しい要素で置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-119">This new element will replace the annotated element in the new, transformed tree.</span></span> <span data-ttu-id="c8aa7-120">例で示すように、このコードは簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-120">This is simple code to write, as demonstrated by the example.</span></span>  
  
-   <span data-ttu-id="c8aa7-121">注釈として追加される新しい要素に新しい子ノードを含めることで、目的の構造を持つサブツリーを形成できます。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-121">The new element that is added as an annotation can contain new child nodes; it can form a sub-tree with any desired shape.</span></span>  
  
-   <span data-ttu-id="c8aa7-122">特別な規則として、この目的で作成された別の名前空間 (この例では `http://www.microsoft.com/LinqToXmlTransform/2007` という名前空間) に新しい要素の子ノードが含まれている場合、その子ノードは新しいツリーにコピーされません。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-122">There is a special rule: If a child node of the new element is in a different namespace, a namespace that is made up for this purpose (in this example, the namespace is `http://www.microsoft.com/LinqToXmlTransform/2007`), then that child element is not copied to the new tree.</span></span> <span data-ttu-id="c8aa7-123">代わりに、名前空間が上記の特別な名前空間で、かつ要素のローカル名が `ApplyTransforms` である場合は、ソース ツリー内の要素の子ノードが反復処理され、新しいツリーにコピーされます (例外として、注釈付きの子要素自体はここで示す規則に従って変換されます)。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-123">Instead, if the namespace is the above mentioned special namespace, and the local name of the element is `ApplyTransforms`, then the child nodes of the element in the source tree are iterated, and copied to the new tree (with the exception that annotated child elements are themselves transformed according to these rules).</span></span>  
  
-   <span data-ttu-id="c8aa7-124">これは、XSL での変換の仕様にある程度似ています。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-124">This is somewhat analogous to the specification of transforms in XSL.</span></span> <span data-ttu-id="c8aa7-125">一連のノードを選択するクエリは、テンプレートの XPath 式に似ています。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-125">The query that selects a set of nodes is analogous to the XPath expression for a template.</span></span> <span data-ttu-id="c8aa7-126">注釈として保存される新しい <xref:System.Xml.Linq.XElement> を作成するコードは、XSL のシーケンス コンストラクターに似ています。また、`ApplyTransforms` 要素は、XSL の `xsl:apply-templates` 要素と機能的に似ています。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-126">The code to create the new <xref:System.Xml.Linq.XElement> that is saved as an annotation is analogous to the sequence constructor in XSL, and the `ApplyTransforms` element is analogous in function to the `xsl:apply-templates` element in XSL.</span></span>  
  
-   <span data-ttu-id="c8aa7-127">この方法の利点の 1 つは、クエリを作成するときに、常に未変更のソース ツリーに対してクエリを記述する点です。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-127">One advantage to taking this approach - as you formulate queries, you are always writing queries on the unmodified source tree.</span></span> <span data-ttu-id="c8aa7-128">ツリーに対する変更が記述中のクエリに与える影響を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-128">You need not worry about how modifications to the tree affect the queries that you are writing.</span></span>  
  
## <a name="transforming-a-tree"></a><span data-ttu-id="c8aa7-129">ツリーの変換</span><span class="sxs-lookup"><span data-stu-id="c8aa7-129">Transforming a Tree</span></span>  
 <span data-ttu-id="c8aa7-130">最初の例では、`Paragraph` ノードの名前をすべて `para` に変更します。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-130">This first example renames all `Paragraph` nodes to `para`.</span></span>  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
                <Paragraph>More text.</Paragraph>  
            </Root>  
  
        ' Replace Paragraph with p.  
        For Each el In root...<Paragraph>  
            ' same idea as xsl:apply-templates  
            el.AddAnnotation( _  
                <para>  
                    <<%= at %>></>  
                </para>)  
        Next  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newRoot As XElement = XForm(root)  
        Console.WriteLine(newRoot)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="c8aa7-131">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-131">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a><span data-ttu-id="c8aa7-132">より複雑な変換</span><span class="sxs-lookup"><span data-stu-id="c8aa7-132">A More Complicated Transform</span></span>  
 <span data-ttu-id="c8aa7-133">次の例では、ツリーに対してクエリを実行し、`Data` 要素の平均と合計を計算して、それらを新しい要素としてツリーに追加します。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-133">The following example queries the tree and calculates the average and sum of the `Data` elements, and adds them as new elements to the tree.</span></span>  
  
```vb  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    Sub Main()  
        Dim data As XElement = _  
            <Root>  
                <Data>20</Data>  
                <Data>10</Data>  
                <Data>3</Data>  
            </Root>  
  
        ' While adding annotations, you can query the source tree all you want,  
        ' as the tree is not mutated while annotating.  
        data.AddAnnotation( _  
            <Root>  
                <<%= at %>/>  
                <Average>  
                    <%= _  
                        String.Format("{0:F4}", _  
                        data.Elements("Data") _  
                        .Select(Function(z) CDec(z)).Average()) _  
                    %>  
                </Average>  
                <Sum>  
                    <%= _  
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _  
                    %>  
                </Sum>  
            </Root> _  
        )  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(data)  
        Console.WriteLine(vbNewLine)  
  
        ' The XForm function, shown later in this topic, accomplishes the transform  
        Dim newData As XElement = XForm(data)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newData)  
    End Sub  
End Module   
```  
  
 <span data-ttu-id="c8aa7-134">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-134">This example produces the following output:</span></span>  
  
```  
Before Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
</Root>  
  
After Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
  <Average>11.0000</Average>  
  <Sum>33</Sum>  
</Root>  
```  
  
## <a name="effecting-the-transform"></a><span data-ttu-id="c8aa7-135">変換の実施</span><span class="sxs-lookup"><span data-stu-id="c8aa7-135">Effecting the Transform</span></span>  
 <span data-ttu-id="c8aa7-136">小さな関数 `XForm` によって、元の注釈付きツリーから変換された新しいツリーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-136">A small function, `XForm`, creates a new transformed tree from the original, annotated tree.</span></span>  
  
-   <span data-ttu-id="c8aa7-137">この関数の擬似コードはかなり単純です。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-137">The pseudo code for the function is quite simple:</span></span>  
  
```  
The function takes an XElement as an argument and returns an XElement.   
If an element has an XElement annotation, then  
    Return a new XElement  
        The name of the new XElement is the annotation element's name.  
        All attributes are copied from the annotation to the new node.  
        All child nodes are copied from the annotation, with the  
            exception that the special node xf:ApplyTransforms is  
            recognized, and the source element's child nodes are  
            iterated. If the source child node is not an XElement, it  
            is copied to the new tree. If the source child is an  
            XElement, then it is transformed by calling this function  
            recursively.  
If an element is not annotated  
    Return a new XElement  
        The name of the new XElement is the source element's name  
        All attributes are copied from the source element to the  
            destination's element.  
        All child nodes are copied from the source element.  
        If the source child node is not an XElement, it is copied to  
            the new tree. If the source child is an XElement, then it  
            is transformed by calling this function recursively.  
```  
  
 <span data-ttu-id="c8aa7-138">この関数の実装を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-138">Following is the implementation of this function:</span></span>  
  
```vb  
' Build a transformed XML tree per the annotations.  
Function XForm(ByVal source As XElement) As XElement  
    If source.Annotation(Of XElement)() IsNot Nothing Then  
        Dim anno As XElement = source.Annotation(Of XElement)()  
        Return _  
            <<%= anno.Name.ToString() %>>  
                <%= anno.Attributes() %>  
                <%= anno.Nodes().Select(Function(n As XNode) _  
                    GetSubNodes(n, source)) %>  
            </>  
    Else  
        Return _  
            <<%= source.Name %>>  
                <%= source.Attributes() %>  
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
            </>  
    End If  
End Function  
  
Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
    Dim annoEl As XElement = TryCast(n, XElement)  
    If annoEl IsNot Nothing Then  
        If annoEl.Name = at Then  
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
        End If  
    End If  
    Return n  
End Function  
  
Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
    Dim e2 As XElement = TryCast(n2, XElement)  
    If e2 Is Nothing Then  
        Return n2  
    Else  
        Return XForm(e2)  
    End If  
End Function  
```  
  
## <a name="complete-example"></a><span data-ttu-id="c8aa7-139">コード例全体</span><span class="sxs-lookup"><span data-stu-id="c8aa7-139">Complete Example</span></span>  
 <span data-ttu-id="c8aa7-140">次に示すのは、`XForm` 関数を含んだ完全なサンプル コードです。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-140">The following code is a complete example that includes the `XForm` function.</span></span> <span data-ttu-id="c8aa7-141">ここには、この種の変換の一般的な使用方法がいくつか示されています。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-141">It includes a few of the typical uses of this type of transform:</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Linq  
Imports System.Text  
Imports System.Xml  
Imports System.Xml.Linq  
  
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">  
  
Module Module1  
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"  
  
    ' Build a transformed XML tree per the annotations.  
    Function XForm(ByVal source As XElement) As XElement  
        If source.Annotation(Of XElement)() IsNot Nothing Then  
            Dim anno As XElement = source.Annotation(Of XElement)()  
            Return _  
                <<%= anno.Name.ToString() %>>  
                    <%= anno.Attributes() %>  
                    <%= anno.Nodes().Select(Function(n As XNode) _  
                        GetSubNodes(n, source)) %>  
                </>  
        Else  
            Return _  
                <<%= source.Name %>>  
                    <%= source.Attributes() %>  
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>  
                </>  
        End If  
    End Function  
  
    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object  
        Dim annoEl As XElement = TryCast(n, XElement)  
        If annoEl IsNot Nothing Then  
            If annoEl.Name = at Then  
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))  
            End If  
        End If  
        Return n  
    End Function  
  
    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode  
        Dim e2 As XElement = TryCast(n2, XElement)  
        If e2 Is Nothing Then  
            Return n2  
        Else  
            Return XForm(e2)  
        End If  
    End Function  
  
    Sub Main()  
        Dim root As XElement = _  
<Root Att1='123'>  
    <!--A comment-->  
    <Child>1</Child>  
    <Child>2</Child>  
    <Other>  
        <GC>3</GC>  
        <GC>4</GC>  
    </Other>  
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
    <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
        ' Each of the following serves the same semantic purpose as  
        ' XSLT templates and sequence constructors.  
  
        ' Replace Child with NewChild.  
        For Each el In root.<Child>  
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)  
        Next  
  
        ' Replace first GC with GrandChild, add an attribute.  
        For Each el In root...<GC>.Take(1)  
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)  
        Next  
  
        ' Replace Other with NewOther, add new child elements around original content.  
        For Each el In root.<Other>  
            el.AddAnnotation( _  
                <NewOther>  
                    <MyNewChild>1</MyNewChild>  
                    <<%= at %>></>  
                    <ChildThatComesAfter/>  
                </NewOther>)  
        Next  
  
        ' Change name of element that has mixed content.  
        root...<SomeMixedContent>(0).AddAnnotation( _  
                <MixedContent><<%= at %>></></MixedContent>)  
  
        ' Replace <b> with <Bold>.  
        For Each el In root...<b>  
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)  
        Next  
  
        ' Replace <i> with <Italic>.  
        For Each el In root...<i>  
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)  
        Next  
  
        Console.WriteLine("Before Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(root)  
        Console.WriteLine(vbNewLine)  
        Dim newRoot As XElement = XForm(root)  
  
        Console.WriteLine("After Transform")  
        Console.WriteLine("----------------")  
        Console.WriteLine(newRoot)  
    End Sub  
End Module   
```  
  
 <span data-ttu-id="c8aa7-142">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c8aa7-142">This example produces the following output:</span></span>  
  
```  
Before Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <Child>1</Child>  
  <Child>2</Child>  
  <Other>  
    <GC>3</GC>  
    <GC>4</GC>  
  </Other>  
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
After Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <NewChild>1</NewChild>  
  <NewChild>2</NewChild>  
  <NewOther>  
    <MyNewChild>1</MyNewChild>  
    <GrandChild ANewAttribute="999">3</GrandChild>  
    <GC>4</GC>  
    <ChildThatComesAfter />  
  </NewOther>  
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8aa7-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8aa7-143">See Also</span></span>  
 [<span data-ttu-id="c8aa7-144">高度な LINQ to XML プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8aa7-144">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
